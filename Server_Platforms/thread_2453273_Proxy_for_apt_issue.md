---
title: "Proxy for apt issue"
date: 2020-11-06
forum: Server Platforms
---

### Post by telamont on 2020-11-06
I am trying to configure a server running on 18.04 in our DMZ to use a proxy we have setup that is used for the package manager on our systems (normally yum which is 99% of our systems). This proxy is only available on 443, I get the following error when I try to update:
Could not handshake: An unexpected TLS packet was received. [IP: x.x.x.x443]

I have the proxy settings for apt configured as follows:
Acquire::http::Proxy "https://proxy.example.com:443";
Acquire::https::Proxy "https://proxy.example.com:443";
Acquire::https::Verify-Peer "false";
Acquire::https::Verify-Host "false";

I have tried only having the https config, changing all urls in souce.list to https but it always gives the same issue.

To be clear, I have never had an issue doing this with our RHEL servers so I can confirm the proxy is functional.

---

### Post by slickymaster on 2020-11-06
Thread moved to **Server Platforms** for a better fit

---

