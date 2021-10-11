


client
{
  "policy": null,
  "log": {
    "access": "/dev/stdout",
    "error": "/dev/stderr",
    "loglevel": "warning"
  },
  "inbounds": [
    {
      "tag": "proxy",
      "port": 1080,
      "listen": "0.0.0.0",
      "protocol": "http",
      "sniffing": {
        "enabled": true,
        "destOverride": [
          "http",
          "tls"
        ]
      },
      "settings": {
        "auth": "noauth",
        "udp": true,
        "ip": null,
        "address": null,
        "clients": null
      },
      "streamSettings": null
    }
  ],
  "outbounds": [
    {
      "tag": "proxy",
      "protocol": "vmess",
      "settings": {
        "vnext": [
          {
            "address": "hk-tx-v2ray-01.zuhaohao.com",
            "port": 443,
            "users": [
              {
                "id": "2a9577ef-a6b5-4c35-bb31-e74ad905f814",
                "alterId": 233,
                "email": "t@t.tt",
                "security": "auto"
              }
            ]
          }
        ],
        "servers": null,
        "response": null
      },
      "streamSettings": {
        "network": "ws",
        "security": "tls",
        "tlsSettings": {
          "allowInsecure": true,
          "serverName": "hk-tx-v2ray-01.zuhaohao.com"
        },
        "tcpSettings": null,
        "kcpSettings": null,
        "wsSettings": {
          "connectionReuse": true,
          "path": "/",
          "headers": {
            "Host": "hk-tx-v2ray-01.zuhaohao.com"
          }
        },
        "httpSettings": null,
        "quicSettings": null
      },
      "mux": {
        "enabled": true
      }
    },
    {
      "tag": "direct",
      "protocol": "freedom",
      "settings": {
        "vnext": null,
        "servers": null,
        "response": null
      },
      "streamSettings": null,
      "mux": null
    },
    {
      "tag": "block",
      "protocol": "blackhole",
      "settings": {
        "vnext": null,
        "servers": null,
        "response": {
          "type": "http"
        }
      },
      "streamSettings": null,
      "mux": null
    }
  ],
  "stats": null,
  "api": null,
  "dns": null,
  "routing": {
    "domainStrategy": "IPIfNonMatch",
    "rules": [
      {
        "type": "field",
        "port": null,
        "inboundTag": "api",
        "outboundTag": "api",
        "ip": null,
        "domain": null
      },
      {
        "type": "field",
        "port": null,
        "inboundTag": null,
        "outboundTag": "direct",
        "ip": [
          "geoip:private"
        ],
        "domain": null
      },
      {
        "type": "field",
        "port": null,
        "inboundTag": null,
        "outboundTag": "direct",
        "ip": [
          "geoip:cn"
        ],
        "domain": null
      },
      {
        "type": "field",
        "port": null,
        "inboundTag": null,
        "outboundTag": "direct",
        "ip": null,
        "domain": [
          "geosite:cn"
        ]
      }
    ]
  }
}

