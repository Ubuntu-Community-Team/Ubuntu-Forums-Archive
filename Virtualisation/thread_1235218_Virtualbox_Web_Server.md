---
title: "Virtualbox Web Server"
date: 2009-08-08
forum: Virtualisation
---

### Post by open_coder on 2009-08-08
I set up an ubuntu web server in a VirtualBox. I need to install joomla to this web server, but I don't know of a way to make the server accessible on my host machine. I tried to just use the ip address in my browser but it didn't work. 

So my question is, how to set up Virtual box to have guest machines accessible as a network connection from the host machine? 

Thanks in advance,

Alex

---

### Post by jocampo on 2009-08-08
> **open_coder said:**
> I set up an ubuntu web server in a VirtualBox. I need to install joomla to this web server, but I don't know of a way to make the server accessible on my host machine. I tried to just use the ip address in my browser but it didn't work. 

So my question is, how to set up Virtual box to have guest machines accessible as a network connection from the host machine? 

Thanks in advance,

Alex

Please use Bridged network option, instead of Nat. It will give a real private IP to your VM but still, you will have connection to "outside" world. With Bridged, your VM NIC will act like a different network card which can communicate and exchange packets with your host.

---

### Post by open_coder on 2009-08-08
Thanks.

---

### Post by slooksterpsv on 2009-08-09
That's actually how I'm using Ubuntu server to try out Web Applications (and creations of my own). If you're serious about having your own dedicated server, you can get a low-end machine for $200 which will do everything you need, if not more.

---

### Post by ruru on 2009-11-01
> Please use Bridged network option, instead of Nat

Many thanks! I just spent all morning trying to work this out before I got lucky and found this post. I've now changed the settings for the VirtualBox guest (the server), and all works as it should.

---

### Post by chinaski on 2010-06-10
> **jocampo said:**
> Please use Bridged network option, instead of Nat
thanks a lot mate ;)

---

### Post by dsr3 on 2011-01-09
Late to the game, but thanks for the post! This would've driven me nuts.

---

### Post by khughitt on 2011-02-09
Hmm. I tried setting up a bridged network interface, but only loopback shows up on ifconfig. Any ideas what I could be missing?

---

### Post by khughitt on 2011-02-11
Still no luck. I've tried host networking, and also bridged. Here is my setup:

Host: Ubuntu 10.04 desktop
Guest: Ubuntu 10.10 server
Network: Wireless

Any suggestions? I've read a lot of discussions where people were able to get it working, but I have had no such luck.

---

### Post by slooksterpsv on 2011-02-11
> **pwnedd said:**
> Still no luck. I've tried host networking, and also bridged. Here is my setup:

Host: Ubuntu 10.04 desktop
Guest: Ubuntu 10.10 server
Network: Wireless

Any suggestions? I've read a lot of discussions where people were able to get it working, but I have had no such luck.

A new thread would be better, but here's what we need to check:

1. Make sure you have these two packages installed on your host system (install in terminal like so): 
```

gksudo apt-get install dkms build-essential

```
2. After those are installed run (in terminal): 
```

gksudo /etc/init.d/vboxdrv setup

```

Reboot.
Startup the VM and see if it gives you like an eth1 or that for the vbox ethernet adapter. Let me know if that works.

---

### Post by khughitt on 2011-02-13
Hi slooksterpsv,

Thanks for the suggestion. Still no luck though. I'll start a new threads on the question.

Best,

---

### Post by slooksterpsv on 2011-02-14
> **pwnedd said:**
> Hi slooksterpsv,

Thanks for the suggestion. Still no luck though. I'll start a new threads on the question.

Best,

Sorry it's taken me so long to get back to you, I've been sick the past few days so I haven't been online.

You can go in and change what type of Ethernet Adapter it uses, I believe by default it's 
AMD PCNet FAST III (Am79C973, the default);

I would try one of the Intel ones and see if that makes a difference.

---

### Post by khughitt on 2011-02-14
Hi slooksterpsv,

No problem! Thanks for taking the time to reply. I did try out all of the different interfaces before, but that didn't work either. I took your suggestion and started a new discussion thread at: [http://ubuntuforums.org/showthread.php?t=1686970](http://ubuntuforums.org/showthread.php?t=1686970).

Best,

---

