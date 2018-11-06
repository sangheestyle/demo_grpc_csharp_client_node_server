# Node.js server and C# client on gRPC

This is a simple example for explaining Node.js server and C# client on gRPC. For more, please check [grpc](https://goo.gl/HgFx14).

## Steps to run

Let's execute Node.js server part at first:

```
cd node
npm i
node greeter_server.js
```

Now, server is ready.

Let's execute C# client part:

```
cd csharp/Greeter
dotnet build
dotnet run -p GreeterClient
```

If you can see the `Greeting: Hello you` on our console, it's done.

## How to generate code from proto

Code for gRPC can be generated from proto.

For Node.js, you can use two different ways. [Dynamic and Static](https://grpc.io/docs/tutorials/basic/node.html#example-code-and-setup). In this example, we use dynamic. So, you don't need to do anything for it.

But you should execute code generation command for generating code for C#. Assume we use mac then execute the following:

```
cd csharp
/Users/kimsan/.nuget/packages/grpc.tools/1.16.0/tools/macosx_x64/protoc -I ../../protos --csharp_out Greeter ../../protos/helloworld.proto --grpc_out Greeter --plugin=protoc-gen-grpc=/Users/kimsan/.nuget/packages/grpc.tools/1.16.0/tools/macosx_x64/grpc_csharp_plugin
```

The most important part from above command is the path. You have to use absolute path like `/Users/kimsan` instead of `~`. Otherwise, `protoc` throws error message. Plesae check [the issue](https://github.com/protocolbuffers/protobuf/issues/791). So, please keep in mind that.

