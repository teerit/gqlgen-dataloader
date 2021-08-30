# GqlGen graphql server with dataloader

This repo demonstrates a simple [GqlGen](https://gqlgen.com/) graphql server using the [graph-gophers/dataloader](https://github.com/graph-gophers/dataloader). This service is based on the GqlGen "Todo" sample app, and the dataloader middleware is inspired by [vektah/dataloaden](https://github.com/vektah/dataloaden). Unlike vekta/dataloaden, this dataloader does not rely on code generation.

### Project Structure
```sh
.
├── gqlgen.yml # GqlGen configuration
├── graph
│   ├── dataloader # implements the user dataloader
│   ├── generated # GqlGen generated files
│   ├── model # defines User and Todo model structs
│   ├── resolver # implements the graphql queries/mutations
│   └── storage # mock datastore for use in dataloader
├── schema.graphqls # graphql schema definition
└── server.go # runnable server
```


### Build & run the app
```sh
# run the app
go run ./server.go

# run GqlGen (to generate new resolvers & models)
go generate ./...
```

*NOTE:* there are [issues](https://github.com/99designs/gqlgen/issues/800) running the GqlGen generator if you have vendored dependencies. The easiest workaround is to delete the `vendor/` folder when you generate.
