---
title: "Port Forwarding and Putty Problem"
date: 2010-06-01
forum: Server Platforms
---

### Post by QuackPot10 on 2010-06-01
Hi,

I've made an ubuntu server with some webpages with a url. I'm trying to get it to work in my windows brower by using putty. But I'm getting problem trying to get the portforwarding to work. Below is the code I'm using in command prompt when in the program files > Oracle > VirtuaBox directory.

"

VBoxManage setextradata Ubuntu Server Site VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/Protocol  TCP VBoxManage setextradata Ubuntu Server Site
VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/GuestPort 22 VBoxManage setextradata Ubuntu Server Site VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/HostPort  22
"

The name of my ubuntu file is "Ubuntu Server Site". 

When I load up Putty and type in my ip address (I take it it has to be my ubuntu server ip or my windows ip? as I have two when I run ip config) and select port 22 I either get a "connection refused" or a "connection timeout" message.

Can anyone help?

---

