---
title: "Dynamic Headless Virtual Machines"
date: 2012-09-07
forum: Server Platforms
---

### Post by generic41209 on 2012-09-07
HI All,
I have been running around this idea for a while. I would like to create a lightweight virtual workstation that is customized for specific purposes. I would like my server to start a headless virtual machine on a new unoccupied display for each request.

I think this could be easily enough script-able, if I can find how to listen for a VNC request on an unoccupied display, or better yet to forward whatever display was used.

It would be nice to be able to map a display to a port so that VNC clients on light-weight devices (such as Android) could connect to the headless machine.

---

### Post by generic41209 on 2012-09-08
I have not fully digested these pages yet, but could this be what I am looking for?:

[http://www.stuartellis.eu/articles/vnc-on-linux/#on-demand](http://www.stuartellis.eu/articles/vnc-on-linux/#on-demand)

[http://www.ibm.com/developerworks/linux/library/os-multiuserloginsvnc/index.html](http://www.ibm.com/developerworks/linux/library/os-multiuserloginsvnc/index.html)

---

### Post by sandyd on 2012-09-08
Try proxmox.
It has everything that you are looking for out of the box.

---

### Post by generic41209 on 2012-09-09
Looks proprietary... Also, a quick browse through the website does not explain much of its intended purpose. I will did deeper and give it a trial run though, thanks!

---

### Post by lincoln32 on 2012-09-09
proxmox has a console mode that could be used but it is intended to be a barebones Virtual machine host (mutible servers running on one physical machine) I think you want more of a thin client and pxe server or also read up on LDAP(transfers settings and documents to client) or eyeOS (computer in a webpage)):P

---

### Post by sandyd on 2012-09-09
> **generic41209 said:**
> Looks proprietary... Also, a quick browse through the website does not explain much of its intended purpose. I will did deeper and give it a trial run though, thanks!

Proxmox is open source.
The virtualizers (KVM and OPENVZ) are open source as well.

---

