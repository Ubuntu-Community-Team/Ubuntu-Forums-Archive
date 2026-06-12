---
title: "Installing Ubuntu Server without cd or usb?"
date: 2009-10-19
forum: Server Platforms
---

### Post by codescompiling on 2009-10-19
Ok, I am currently working as an assistant IT at my school and am currently attempting to install Ubuntu server 9.04 to an old server the school is not currently using. It's a Compaq Proliant DL360 G1. 

I cannot use the cd drive since it requires a smartstart cd that has been lost (I downloaded the .iso [v 5.5] and it doesn't start up) in order to boot from an installation cd. I also cannot use usb since it has no usb ports! I can log into it and I found out that an old IT manager here installed Fedora core 4 to this server. The problem is that it doesn't have the drivers for the cd drive. 

I was wondering, is it possible to mount ubuntu's .iso from command line and then install it to another partition? I also need to know how to create a partition from a command line since this old version of fedora doesn't have any GUI partition managers. 

Any help is greatly appreciated!

---

### Post by t3r0 on 2009-10-19
take the hd out from the server and put it in a desktop (or other server) box and install ubuntu there. Then just put the hd back to the old server and hope it boots :) 

- Tero

---

### Post by prshah on 2009-10-19
> **codescompiling said:**
> 
I was wondering, is it possible to mount ubuntu's .iso from command line and then install it to another partition? 

> **t3r0 said:**
> take the hd out from the server and put it in a desktop (or other server) box and install ubuntu there.

That's a suggestion that will work. Alternate suggestions can be had from the Community Documentation on [Installation without a CD]("https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD"). Also a little below that are suggestions to install from Local Net, etc.

---

