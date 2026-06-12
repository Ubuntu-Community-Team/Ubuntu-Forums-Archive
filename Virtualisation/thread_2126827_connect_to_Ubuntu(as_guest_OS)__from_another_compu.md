---
title: "connect to Ubuntu(as guest OS)  from another computer"
date: 2013-03-18
forum: Virtualisation
---

### Post by virtualetk on 2013-03-18
I've recently used VirtualBox to install Ubuntu 12.04 as guest OS. My primary OS is Windows 7.
Now what I want to do is, while being on another computer to connect to my  guest OS which runs a server-client application that I programmed. When I run on Ubuntu the server I can't connect to it from  another computer. But when server runs on any other computer, the client programm that runs on the Ubuntu guest OS can connect to it and successfully send and receive messages from the server.


Why does this happen? How to fix it?

PS. I traced the client.c and it seems that connect() returns -1

---

### Post by sanderj on 2013-03-18
It's because the guest OS is behind NAT (=default network setting in VirtualBox).

In the Virtualbox settings of the guest OS, go to Network, and change to Bridged or to Internal (experiment which one works).

HTH

---

