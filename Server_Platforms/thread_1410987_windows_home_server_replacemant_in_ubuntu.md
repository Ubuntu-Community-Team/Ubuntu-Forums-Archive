---
title: "windows home server replacemant in ubuntu"
date: 2010-02-19
forum: Server Platforms
---

### Post by jmore9 on 2010-02-19
Hello!

Anyone know of a simple replacement for windows home server based on ubuntu 9.10 ?  Really need a simple solution as i am not to network savy.

---

### Post by doas777 on 2010-02-19
well, even on windows, you do need to be at least somewhat network savvy to set up a server. 

the real question is, what services do you want on the server? they are the tricky part.

---

### Post by jmore9 on 2010-02-19
No internet just want to hook up a windows machine and a ubuntu machine to it to share files and keep projects on.  I plan on using a router to connect the three together once i have a server installed.  I tries windows server 2003 but it was to hard to get to work.  I figured maybe somekind of samba server running off ubuntu 9.10 ?

---

### Post by lykwydchykyn on 2010-02-19
> **jmore9 said:**
> No internet just want to hook up a windows machine and a ubuntu machine to it to share files and keep projects on.  I plan on using a router to connect the three together once i have a server installed.  I tries windows server 2003 but it was to hard to get to work.  I figured maybe somekind of samba server running off ubuntu 9.10 ?

Samba's usually the best solution when dealing with Windows workstations.

If you're not very network/command-line savvy, I'd recommend just setting up a regular ubuntu workstation, and maybe install something like [webmin](www.webmin.com).

Honestly, though, I can't think of anything that won't require at least a bit of knowledge investment on your part, so be prepared to do a bit of reading and troubleshooting.

---

### Post by ezacon on 2010-02-19
simple answere: ebox
[http://www.ebox-platform.com/](http://www.ebox-platform.com/)

---

### Post by KnottyMars on 2010-02-19
> **lykwydchykyn said:**
> Samba's usually the best solution when dealing with Windows workstations.

If you're not very network/command-line savvy, I'd recommend just setting up a regular ubuntu workstation, and maybe install something like [webmin](www.webmin.org).

Honestly, though, I can't think of anything that won't require at least a bit of knowledge investment on your part, so be prepared to do a bit of reading and troubleshooting.

i agree, use a desktop version unless you want to get into command line stuff. Although since all you need is network storage, once you set a server up, you can just put the PC in a closet with power and a network connection and it will be set. 
Samba is pretty simple to install and use

---

### Post by hubtech on 2010-02-19
An interesting question. I'd like to help clarify the question somewhat as the responses thus far have suggested that ppl aren't fully grasping what you're looking for. Windows Home Server ([http://www.microsoft.com/windows/products/winfamily/windowshomeserver/default.mspx](http://www.microsoft.com/windows/products/winfamily/windowshomeserver/default.mspx)) provides very specific services. eBox seems a bit of overkill as a replacement for it.
 
I don't believe that Samba alone could fulfill the same services. It would take more than an insignificant amount of "network savvy" to setup a system to fully mimic a replacement to this sort of device. From a simplicity standpoint, you may be best of buying the real thing.
 
Having said that, and acknowledging that I do not have an intimate knowledge of how these "Home Servers" work, it sounds to me as though they are rather exposed to the internet. Without a more significant amount of network savvy, I would be reticent to use or recommend such a device. And I agree with lykwydchykyn that either way will require a knowledge investment on your part (assuming you want to protect your data privacy).
 
... Allen
 
EDIT: Link to "technical home networking" doc ([http://download.microsoft.com/download/d/6/6/d66fdc35-519b-4768-8c68-06804fb61bf7/Windows%20Home%20Server%20Technical%20%20Brief%20-%20Home%20Networking.docx]("http://download.microsoft.com/download/d/6/6/d66fdc35-519b-4768-8c68-06804fb61bf7/Windows%20Home%20Server%20Technical%20%20Brief%20-%20Home%20Networking.docx"))

---

### Post by rturner on 2010-02-19
As others have said, you need to know what services you want to run similar to windows home server.  I set up a home media server on an old machine using ubuntu server 9.10, but it would probably be easier for you installing it as desktop.  For a media server, the easiest one I've ever used is MediaTomb.  You can stream music, videos and games with it (I've only got it working with music at this point).  You can install it on the server or desktop version.  For basic file serving, samba works fine.

[https://help.ubuntu.com/community/MediaTomb](https://help.ubuntu.com/community/MediaTomb)

---

### Post by laytek on 2010-02-19
A server is used to enhance productivity. Setting up any server takes a plan (services desired), and some knowledge to execute the plan. Based on your stated use of the server, may I suggest an external USB hard drive and a religious backup plan. Quick, simple, productive, and meets the needs you have stated so far.

I am not trying to be cute. Computers and servers can take away far more than they give if you overkill.

LayTek

---

### Post by CharlesA on 2010-02-19
> **laytek said:**
> A server is used to enhance productivity. Setting up any server takes a plan (services desired), and some knowledge to execute the plan. Based on your stated use of the server, may I suggest an external USB hard drive and a religious backup plan. Quick, simple, productive, and meets the needs you have stated so far.

I am not trying to be cute. Computers and servers can take away far more than they give if you overkill.

LayTek
This.

As it has already been said, figure out what you want to be using. What does WHS do that you want to replace it with Ubuntu?

---

