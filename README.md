### NKC proxy go
golang实现的可配置的反向代理服务器

## usage
```bash
go run main.go path/to/config.json
```

## example
配置文件示例
```json
{
  "ports": {
    "httpPort": 80,
    "httpsPort": 443
  },
  "timeout": 10000,
  "servers": [
    {
      "name": "故园怀旧",
      "type": "forward",
      "hostname": [
        "127.0.0.1",
        "localhost"
      ],
      "https": true,
      "httpTarget": [
        "http://127.0.0.1:9000",
        "http://127.0.0.1:9001",
        "http://127.0.0.1:9002"
      ],
      "wsTarget": [
        "http://localhost:2170",
        "http://localhost:2171",
        "http://localhost:2172"
      ],
      "SSL": {
        "cert": "/cert/www.kechuang.org.crt",
        "key": "/cert/www.kechuang.org.key"
      }
    },
    {
      "name": "故园怀旧 重定向",
      "type": "redirect",
      "hostname": [
        "a.test"
      ],
      "https": false,
      "httpTarget": [
        "https://www.kechuang.org",
        "https://www.bilibili.com",
        "https://www.baidu.com"
      ]
    }
  ],
  "noResponsePage": "/html/503.html",
  "SSL": {
    "cert": "/cert/default.crt",
    "key": "/cert/default.key"
  },
  "concurrentLimit": 0
}
```
