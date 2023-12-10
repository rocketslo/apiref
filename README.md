# RocketSLO Public gRPC API Reference

[RocketSLO](https://rocketslo.com) is a quality management solution for distributed software architectures.

This repository contain proto files that you can use to connect to RocketSLO public gRPC API. Review API reference at https://apiref.rocketslo.com.

Learn more about RocketSLO at https://docs.rocketslo.com.


## Examples

We are going to make a call to [rct.api.TenantService#GetInfo](https://apiref.rocketslo.com/rct.api#service-rct.api.TenantService-GetInfo) method.

### Prerequisites

* Create bot and generate API token in RocketSLO portal.

### Make a request with gRPCurl utility

* Install `grpcurl` from https://github.com/fullstorydev/grpcurl.
* Install `protoc` utility as described in https://grpc.io/docs/protoc-installation/.
* Export bot's API token into environment variable `API_TOKEN`.
* Generate protoset file as described in https://github.com/fullstorydev/grpcurl#protoset-files

```
protoc --proto_path=proto \
    --descriptor_set_out=rocketslo.protoset \
    --include_imports \
    proto/grpcapi/*.proto
```

* Make a call

```
grpcurl -protoset rocketslo.protoset \
    -expand-headers -H "RctApiToken: ${API_TOKEN}" \
    rocketslo-grpcapi-nmw7h5srja-uw.a.run.app:443 \
    rct.api.TenantService/GetInfo
```