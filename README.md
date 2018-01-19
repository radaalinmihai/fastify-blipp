Inspired by [blipp](https://github.com/danielb2/blipp) hapijs plugin which prints your routes.

## install
```
npm i fastify-blipp
```

## usage
```javascript
const fastify = require('fastify')()

fastify.register(require('fastify-blipp'));

fastify.get("/hello/:username", async (req, reply) => ({
  greeting: `Hello, ${req.params.username}`
}));
fastify.get("/hello/:username/CAPS", async (req, reply) => ({
  greeting: `Hello, ${req.params.username.toUpperCase()}`
}));
fastify.post("/hello", async (req, reply) => ({
  greeting: `Hello, ${req.body.username}`
}));
fastify.get(
  "/example/at/:hour(^\\\\d{2})h:minute(^\\\\d{2})m",
  (req, reply) => ({
    hour: req.params.hour,
    minute: req.params.minute
  })
);

const start = async () => {
    try {
        await fastify.listen(3000);

        fastify.blipp();

        console.log(`server listening on ${fastify.server.address().port}`);
    } catch (err) {
        console.error(err);
        process.exit(1)
    }
}

start();
```

## result

![image](var/images/output_example.png)

