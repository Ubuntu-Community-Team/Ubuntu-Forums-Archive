---
title: "Can't connect client to server on ubuntu 12.04 vps on port 9620"
date: 2013-04-21
forum: Server Platforms
---

### Post by hypokill on 2013-04-21
Hello!
I've been having an headache about this for 4 days. I just can't understand it. I have a vps set up with LXDE and VNC remote desktop. I'm using wine to run a server program. I can also run a program on the vps and connect to the server using internet static ip. I can connect to the server externally through my browser on my home computer by puting ipaddress:9620. Using a web based port checker it says the port is open! I cannot for my life connect through the same program that connects on the vps on my home computer. I've looked into iptables and everything. I can't find anything that works. Please Help!!

Edit: Thought i would add some more information. i'm using lxde-core not full. Is there any settings automatically blocking incoming connections? I can connect through VPN and SSH. This is a post from the minecraft forums for CentOS. This i one post that really sounds the same.

 [http://www.minecraftforum.net/topic/165033-vps-linux-centos-manually-port-forwarding-solved/page__st__20](http://www.minecraftforum.net/topic/165033-vps-linux-centos-manually-port-forwarding-solved/page__st__20)

The end post explains how he fixed it. though ubuntu iptables doesn't use a config file... from what i know. Im very new to this, any suggestions or anything would be much appreciated!

---

### Post by hypokill on 2013-04-21
Please anyone got any clue?

---

### Post by wildmanne39 on 2013-04-21
*Thread moved to **Server Platforms**.*

---

### Post by hypokill on 2013-04-21
Sorry, i posted this on my phone and for some reason didn't see the other more suitable sections. I realized when i got on my laptop but couldn't figure out how to more it. Cheers

---

### Post by wildmanne39 on 2013-04-21
Nothing to be sorry for. 

Hopefully you can get the help you need in this section.

---

### Post by hypokill on 2013-04-21
Here's hoping too! I'm just going round and round in circles with this. I'm just all out of ideas. Thanks again

---

### Post by hypokill on 2013-04-22
I moved to Debian 6 and xFCE and now it's working!

---

