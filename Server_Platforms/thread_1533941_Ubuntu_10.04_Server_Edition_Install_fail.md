---
title: "Ubuntu 10.04 Server Edition Install fail"
date: 2010-07-18
forum: Server Platforms
---

### Post by MAFoElffen on 2010-07-18
I tried installing Ubuntu LTS 10.04 Server Edition 64 bit on one of my drives today...

The install completed fine until it went to reboot.  Then it faills while initializing the graphics.  It tries (a purple flash on the screen) then goes to a text based dump on the monitor.

Ubuntu LTS 10.04 Desktop Edition run great on this machine.  I'm wondering if the Server Edition confused by multiple instances of a video card?  This computer is SLI bridged:

```
ASUS A8N32-SLI Deluxe Gaming Edition
AMD 64 FX-60
4GB PC3200 Performance Gaming RAM
Two XFX GeForce 6800GT Ultra SLI bridged video cards
1TB SATA drive
250GB SATA drive
500GB IDE drive
```Is the xorg or whatever video subsystem that the server edition uses different than Desktop Edition?

---

### Post by MAFoElffen on 2010-07-19
If you've been following me in other posts, this is a multi-boot machine. It has Win7 64bit and Ubuntu LTS 10.04 Desktop 64bit on the 1TB, Windows Vista 64bit and OpenSolaris on the 250GB and trying to Install Ubuntu LTS 10.04 Server Edition 64bit on the 500GB along side a swap partition and a data partition.

* On the install process, I have the SATA drives unmounted.

This computer is my dev platform. Someone wants me to develop a website for them using a Joomla CMS as a prototype template.

The reason I mentioned "xorg" is that back in January-February, I ran into some upstream xorg problems between OpenSolaris and Solaris 10.  OpenSolaris had updated their xorg version, That upstream change lost their compatibitlity with multiple instances of the same video card (where SLI technology "is"). That's when I had to go to a dev version of OpenSolaris- that went to an even newer version of xorg, that fixed that problem.

Is the graphical logo/login screen in Ubuntu in the server edition after the init of xorg?
If so, is the xorg of the Server Edition different than the Desktop Edition?

---

### Post by howefield on 2010-07-19
What does the "text based dump" say ?

---

### Post by arrrghhh on 2010-07-19
Uhm... Xorg or "X" is not included in the server edition - it's a text-based only distro.  The whole purple splash screen is new - called landscape.  I think it's ridiculous that they included it on a text-only console, but to each their own I guess.

---

### Post by MAFoElffen on 2010-07-19
> **arrrghhh said:**
> Uhm... Xorg or "X" is not included in the server edition - it's a text-based only distro.  The whole purple splash screen is new - called landscape.  I think it's ridiculous that they included it on a text-only console, but to each their own I guess.
Then I guess the problem is not there. Thanks.

---

### Post by arrrghhh on 2010-07-19
> **MAFoElffen said:**
> Then I guess the problem is not there. Thanks.

No worries.  The server edition is meant to be optimized for simply running services - IE as little overhead as possible (so no room for a GUI!)

If you **need** a GUI, then run ubuntu-desktop.  All of the same services can be setup on the desktop version, the only real difference is the desktop version includes a lot of packages (like OpenOffice, etc).

Some people do run the server edition with gnome-core, but to me that seems silly.  It has been done, however and I feel I must mention it lest this post be considered biased :P

---

### Post by MAFoElffen on 2010-07-19
> **howefield said:**
> What does the "text based dump" say ?
Basically that there is cache corruption.  It's a whole screen full of detailed info and I wish I could have copied it into a text file, but the computer was locked up.  I guess I could have hand written it, but it would have taken a long time.

I first installed packages while doing the first install... Then removed "all" the packages to see if it was the basic server system- It is.

Does this server OS have boot logging that would tell me where is locked out?  ...Some file than I can look at and post here from one of my other OS'es?  (Otherwise I'll hand copy)

---

### Post by ingeva on 2010-07-20
> **arrrghhh said:**
> Some people do run the server edition with gnome-core, but to me that seems silly.  It has been done, however and I feel I must mention it lest this post be considered biased :P
Just a comment.
I always use the server version because it's quicker to install, and if some time has passed after the issue, you don't need to install all the desktop updates; you get the latest version at once. All you need is an apt-get, and the latest version is installed the first time.
I think it's a good idea to use the server version if you need any of the services it provides.

---

### Post by arrrghhh on 2010-07-20
> **ingeva said:**
> I think it's a good idea to use the server version if you need any of the services it provides.

Server edition does NOT provide any additional services above and beyond the desktop edition.  Granted, it does make installing a LAMP stack easier... but it's not by any means hard install a LAMP stack on the desktop version.

So I'm not sure what you mean... Like I said, the server edition doesn't provide any special services.  It's just been stripped to run lean and mean (no X, OpenOffice, Gimp, etc...)

---

### Post by MAFoElffen on 2010-07-23
> **arrrghhh said:**
> Uhm... Xorg or "X" is not included in the server edition - it's a text-based only distro. The whole purple splash screen is new - called landscape. I think it's ridiculous that they included it on a text-only console, but to each their own I guess.
 I discovered something this morning. I was having problems after a "Distrution Upgrade of the Desktop Edition.  During that Upgrade, my system no longer booted Ubuntu (another thread, still as yet ongoing. I could not boot any 10.04 version of Ubuntu, even from the LiveCD.
 
During that process I removed one of my SLI cards.  Now the LiveCD and the previously installed Server Edition boots up fine.
 
...Even though you said this was a "text-based only distro". Ubuntu LiveCD and the Server Edition DOES seem to have problems with multiple instances of a video card- SLI bridged cards included.
 
I gueuss, at least in my instance, this is either a BUG or a limitation.  Although in Server's. Graphics is not really an asset... and the Server Edition doesn't take advantage of multi-GPU processing (such as CUDA).
 
In either instance it is a FAIL situation that I think should be noted currently as system compatibility goes.

---

### Post by arrrghhh on 2010-07-23
Hrm... I don't think a single server would have an SLI video card setup.  Mine doesn't, there's no point.  The on-board Intel GPU is more than enough, considering I don't have the server hooked up to a monitor.

With that said, the server does still need _something_ to put video out to, and if that's your only video out...

It's a shame that you're having issues with it, but basically nobody in their right mind would be installing the server ed on a rig like yours ;)

---

### Post by MAFoElffen on 2010-07-23
> **arrrghhh said:**
> It's a shame that you're having issues with it, but basically nobody in their right mind would be installing the server ed on a rig like yours ;)
You're right. mine is a development and testing platform.  I do know many who think gaming PC's make good server platforms, but it wouldn't be "my" choice as a deicated server. LOL.  Thanks for your help!

---

