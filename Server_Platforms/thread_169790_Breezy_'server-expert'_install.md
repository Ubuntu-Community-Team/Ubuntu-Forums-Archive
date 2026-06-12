---
title: "Breezy 'server-expert' install"
date: 2006-05-03
forum: Server Platforms
---

### Post by ttwt on 2006-05-03
Hi,

just had a problem installing i386 breezy with 'server-expert' option.  I wanted a bare minimum system wo went through the steps but didn't do the "copy remaining packages to hard disk" bit.  After the 'finish installation' step, the server reboots and I followed the dialogue to create a new user.  Then the server goes on to the installing packages step and just hangs.  Logging in to VC2 shows that apt-get is hogging 100% of the CPU.

If I boot with the CD available, it starts installing everything, i.e. a desktop machine not a server.

If I just do a server install rather than a server-expert install it runs to completion, though it does copy a load of stuff across that I don't want and appears to leave it uninstalled.

I have googles, STFW'd, RTFM'd, RTFW, been to bugzilla but can find no information on how to continue from this point.

Anybody any ideas on how to install a more minimalist system than a straightforward 'server' install ?

TTFN

---

### Post by ttwt on 2006-05-04
Answering my own questions here - I downloaded and installed ubuntu-6.06-beta2-install-i386.iso and went through the server expert route on that.

This works fine and doesn't copy anything unless you tell it to.

If you "select and install software" though, it will copy all the packages and then start building a desktop.

---

### Post by breezyfox on 2006-05-05
[QUOTE=ttwt] I downloaded and installed ubuntu-6.06-beta2-install-i386.iso and went through the server expert route on that.

This works fine and doesn't copy anything unless you tell it to.

If you "select and install software" though, it will copy all the packages and then start building a desktop.[/QUOTE]
hi ttwt
i would appreciate if you could tell me how you are able to install server -expert from live cd you downloaded. I could not find any way to install the minimum software.
I have only one option just install icon on desktop and when you install through this it installs bundles of softwares which really i don't want. i am running 400MZ and want to use it as server (just for learning purpose first)
can you please give me bit more details so i can also install.

thanks

bz

---

