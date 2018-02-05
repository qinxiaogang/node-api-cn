
<!--introduced_in=v0.10.0-->

> 稳定性: 2 - 稳定的

<!-- name=dgram -->

`dgram`模块提供了 UDP 数据包 socket 的实现。

```js
const dgram = require('dgram');
const server = dgram.createSocket('udp4');

server.on('error', (err) => {
  console.log(`服务器异常：\n${err.stack}`);
  server.close();
});

server.on('message', (msg, rinfo) => {
  console.log(`服务器收到：${msg} 来自 ${rinfo.address}:${rinfo.port}`);
});

server.on('listening', () => {
  const address = server.address();
  console.log(`服务器监听 ${address.address}:${address.port}`);
});

server.bind(41234);
// 服务器监听 0.0.0.0:41234
```

------------------------------------------------------------------------------------------------------------
// 测试程序
const dgram = require('dgram');
const client = dgram.createSocket('udp4');
client.on('close',() => {
        console.log('socket close');
});
 
client.send(`这是一个测试信息`,41234,'127.0.0.1');
