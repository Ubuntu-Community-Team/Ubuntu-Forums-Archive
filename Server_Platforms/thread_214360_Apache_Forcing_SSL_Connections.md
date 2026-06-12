---
title: "Apache Forcing SSL Connections"
date: 2006-07-12
forum: Server Platforms
---

### Post by terigox on 2006-07-12
Hi everyone, I'm new to the way debian/ubuntu configs it's Apache, so I'm hoping this is an easy question :)

I have my Ubuntu 6.06 server running, serving up a couple virtual hosts. Right now I am running it off of a secondary port, 8080. Basically, I want the option to be able to access the page via https, or http. I have enabled the SSL Mod using things like:
```
    SSLEngine on
    SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire
    SSLCertificateFile /etc/ssl/certs/server.crt
    SSLCertificateKeyFile /etc/ssl/private/server.key

```

But when I go to the non-ssl page, it is forcing me to use SSL.
> Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.
[https://mydomain:8080](https://mydomain:8080)

Is it doing this because I am using a specific port? Is there a way to allow both types of traffic over the same port? Port 443 is currently being forwarded to another server for handling. I hope someone can provide some insight on this :)

Thanks!! :)

---

