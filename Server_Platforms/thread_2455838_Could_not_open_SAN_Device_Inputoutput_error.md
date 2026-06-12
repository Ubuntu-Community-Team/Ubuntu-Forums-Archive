---
title: "Could not open SAN Device: Input/output error"
date: 2020-12-28
forum: Server Platforms
---

### Post by windows7ge on 2020-12-28
Hello, I setup Ubuntu Server 20.04.1 LTS with the iSCSI tgt package. I can connect to the iSCSI targets just fine using open-iscsi from client machines when in a booted OS but I'm trying to setup iPXE Network Boot and for whatever reason iPXE doesn't like it.

I tried using a different OS (TrueNAS CORE) using their iSCSI client and that worked perfectly. I can install and boot an OS and everything which tells me the issue lies with Ubuntu Server/tgt.

My research has led me to believe it's an issue with permissions but I have no idea what settings I need to change for iPXE to not have issues with the iSCSI LUN.

I've been trying to find a debug or verbose command so I can see what the server is doing when iPXE tries to connect but no dice.

iPXE itself did provide a resource that is meant to explain the error but I have no idea what this means or how to fix it: [http://ipxe.org/1d704039](http://ipxe.org/1d704039)

All suggestions are appreciated.

---

