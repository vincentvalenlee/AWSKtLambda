## 欢迎使用AWSKtLambda

本项目主要针对AWS Lambda提供一些常用工具库

### 工具特性

 - 提供AWS_Proxy集成模式的封装
 - 提供kotlin方式的路由处理handler
 eg. 
 AWSProxy {
   get("/user") { ctx ->
      ctx.response("hellow word");
   }
   
   post("/member/:id") { ctx->
      ctx.params("id)
      ctx.json(model)
   }
 }
 - 兼容JAX-RS规范，使用注解定义路由处理
eg.
@Path("/library")
public class Library {
   @GET
   @Path("/books")
   public String getBooks() {...}

   @GET
   @Path("/book/{isbn}")
   public String getBook(@PathParam("isbn") String id) {
      // search my database and get a string representation and return it
   }

   @PUT
   @Path("/book/{isbn}")
   public void addBook(@PathParam("isbn") String id, @QueryParam("name") String name) {...}
   
   @DELETE
   @Path("/book/{id}")
   public void removeBook(@PathParam("id") String id {...}
}
- 支持Lambda @Heart心跳保持，避免AWS Lambda 冷启动
- 支持AWS @KeepAlive(resource = {db, sns, iot, sqs}) 资源链接的保持
- 后续版本引入camel，使用kotlin DSL方式调用AWS 各种资源
- 后续版本引入vertx，支持lambda内部事件点，并提供各类符合vertx的工具库
- 后续版本支持kts脚本加载（从AWS S3或DynamoDB中）
