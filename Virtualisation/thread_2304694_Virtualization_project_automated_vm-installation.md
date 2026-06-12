---
title: "Virtualization project: automated vm-installation"
date: 2015-11-29
forum: Virtualisation
---

### Post by flopsgotya on 2015-11-29
Hello ubuntuforums 
I am new here! I hope to find what i need, and also hope to give back to his community. 


So: Me and my friend have plans to setup some service where people test their program on a vm for max 5 min, and after that the vm will be removed and a new one will be created. We have no idea what software to use, but we'd prefer to use linux, as i have quite a lot of experience with it. 


So this is what we want:  
Users will have to upload their program to a website, the program will be executed, and after max 5 minutes the vm needs to be replaced.  


The service will be hosted on a dedicated server. If there is anyone who can help, that would be great. We can pay for help, if that is required, because it needs to work flawless. If we get this to work, i will write a tutorial and share it here, so people can learn from this. 


Thanks in advance, 
flops 


ps. if this is the wrong place to post this thread, i'm sorry!

---

### Post by TheFu on 2015-11-29
vagrant with docker/lxc containers and a few bash scripts to put it all together. If you want to be fancy, you can setup a web front end using a CI tool. End-users like that stuff.

---

### Post by flopsgotya on 2015-12-02
> **TheFu said:**
> vagrant with docker/lxc containers and a few bash scripts to put it all together. If you want to be fancy, you can setup a web front end using a CI tool. End-users like that stuff.
Thx TheFu for your reply! 
Do you mind if i ask you some more questions over time? i'll need some assistance :)

flops

---

