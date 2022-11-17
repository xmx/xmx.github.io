### 如何生成 swagger 接口文档

[swagger OAS 标准](https://swagger.io/specification/) 只是一个与编程语言无关的接口文档规范。

一些基于 swagger 的接口文档生成工具，比如：Java 语言的 [SpringFox](https://github.com/springfox/springfox)，Go 语言下的 [swaggo](https://github.com/swaggo/swag)。这些工具都会对代码产生入侵。不论通过是注解、注释还是go tag。（注释虽然不算代码，但是 swaggo 注释方式也十分影响代码的整体观感）。对于一个代码洁癖的人来说，简直不能忍。

我目前的做法是使用 [Stoplight Studio](https://github.com/stoplightio/studio) 编写 sawgger 文档(json 或 yaml 格式都可)。UI 显示只需要一个 [简单的 HTML 页面](https://github.com/swagger-api/swagger-ui/blob/master/docs/usage/installation.md#unpkg) 即可(UI 可以使用官方的 SwaggerUI，也可以换成 Redoc)：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta
    name="description"
    content="SwaggerUI"
  />
  <title>SwaggerUI</title>
  <link rel="stylesheet" href="https://unpkg.com/swagger-ui-dist@4.5.0/swagger-ui.css" />
</head>
<body>
<div id="swagger-ui"></div>
<script src="https://unpkg.com/swagger-ui-dist@4.5.0/swagger-ui-bundle.js" crossorigin></script>
<script>
  window.onload = () => {
    window.ui = SwaggerUIBundle({
      url: 'openapi.json', // 此处换成自己的地址 YAML 或 JSON
      dom_id: '#swagger-ui',
    });
  };
</script>
</body>
</html>
```

### Swagger UI

![swagger-image.png](https://static.golangjob.cn/221117/3a6a013ad12826418a24581c6de2c1e4.png)

### Redoc UI

![2022-11-17T14:31:09,863334099+08:00.png](https://static.golangjob.cn/221117/9a5bac1a95f55fbfef00ccd5f42ee5a9.png)
