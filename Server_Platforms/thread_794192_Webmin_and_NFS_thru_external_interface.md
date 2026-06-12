---
title: "Webmin and NFS thru external interface"
date: 2008-05-14
forum: Server Platforms
---

### Post by xris_xcess on 2008-05-14
HI:

I work in a school, were I have set up an Ubuntu 8.04 Server. It "serves" NFS shares, DNS caching and NAT/firewalling. To help me out with the setup and admin I installed the latest webmin.

Everything has worked out quite well for now, but my phisical network setup is causing me some headaches. Basically I have a Private network inside a private network !?. Something Like:

(INTERNET)
|
(ISP's ROUTER)
|
(Switch)----(office)
|
|
(Ubuntu Server)---(switch)---(Lab).

I am trying to allow access to the NFS shares and Webmin from the office side, but have had no success in setting up my iptables correctly. Since I'm using masquerading to route/nat the labs computers to the internet, I´ve been trying to set up some sort of 1:1 Nat to allow access but with no success.

Has anyone had any experience setting it up thru webmin? Should I just forget webming and start writting my own iptables?

Thanks.

---

