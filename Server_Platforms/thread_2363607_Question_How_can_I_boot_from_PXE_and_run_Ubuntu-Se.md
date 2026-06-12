---
title: "Question: How can I boot from PXE and run Ubuntu-Server in RAM?"
date: 2017-06-12
forum: Server Platforms
---

### Post by expremo2 on 2017-06-12
Hi guys

Ok so here's a pretty specific question. 

Here's what I want to do:

I have a PXE server (running ubuntu-server). I want multiple clients to boot a ubuntu-server OS from the PXE and run it from the RAM (no USB, HDD, etc).

Also I want to customize said ubuntu-server to have the nvidia drivers integrated.

I searched for hours and found "debirf". I got it to work (it boots via pxe) however I cannot customize it with the nvidia drivers.

Does anyone have an idea?

Feedback is much appreciated!

Thank you guys in advance!

Remo

---

### Post by Tadaen_Sylvermane on 2017-06-12
If I was you I would look into the LTSP project. I use it at home to pxe boot my media centers around the house. Makes things simple. You can add whatever packages to the chroot with little fuss as needed. Why Ubuntu server though? Wouldn't a desktop solution make more sense?

---

### Post by Tadaen_Sylvermane on 2017-06-12
Not letting me edit. If you are pxe booting ubuntu server to split services to different machines maybe containers may be more suitable. LXD is wonderful, is how I run my minecraft servers.

---

### Post by expremo2 on 2017-06-13
> **Tadaen_Sylvermane said:**
> Not letting me edit. If you are pxe booting ubuntu server to split services to different machines maybe containers may be more suitable. LXD is wonderful, is how I run my minecraft servers.

basically what I need it for is crypto mining. I want my miners to boot via PXE without having to think about harddrives or USB sticks from which the system runs. Also it's way easier to manage in case I want to edit the configuration of the OS. I'll just edit it once and reboot all my miners. That's what I need it for in a nutshell.

I'll check  out LXD, maybe someone knows anything else?

Thanks guys!

EDIT: LTSP looks great however I don't really need the clients (in my case the miners) to connect to the server or anything. I just want them to boot up and connect to the network. Is that possible with LTSP?

---

### Post by Tadaen_Sylvermane on 2017-06-13
Yes you can do what you want with ltsp. Pretty easy to configure. Using a pxe boot image is a great idea for miners I think, never crossed my mind. For mining lxd containers wouldn't help because everything would be on the same hardware.[http://www.havetheknowhow.com/Configure-the-server/Install-LTSP.html](http://www.havetheknowhow.com/Configure-the-server/Install-LTSP.html) should get you started. You would also need to figure out the lts.conf for each client so that they run different users and different processes. Shouldn't be to hard.

---

### Post by faddat on 2017-11-05
@expremo2

You ever get anywhere with this?  LTSP work out for you? 

Did you happen to hit network block device (NBD) errors?

That's where I am stuck right now.

---

