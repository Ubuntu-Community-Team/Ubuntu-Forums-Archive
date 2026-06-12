---
title: "Awesome trick"
date: 2010-05-14
forum: Server Platforms
---

### Post by fang0654 on 2010-05-14
I just discovered something today so fundamental, and so awesome, that it is going to make many things much much easier for administering my systems.  Most of the old hats probably already know this, and it could be that I am the only linux sysadmin in existence that never heard of this.  If that is the case, please shake your head sadly and continue past this post.

I've never known about SSH X Forwarding, how simple it was, or how useful.  For those like me not in the know, it is very simply, a means of running some GUI related program on a remote server in your own instance of X Windows.  Scenario where this makes things much much easier:

I have a lot of virtual machines spread out all over the United States, and use VirtualBox as my hyper visor.  For day to day administration, I am pretty fluent with VBoxManage (VirtualBox's excellent command line utility).  When creating a new VM though, VBoxManage is a pain, especially as more and more features are added.  What takes three clicks in VirtualBox's New Machine Wizard takes about 10 commands on the command line.  

I set up a new hyper visor today.  To set up a new VM, I ssh'd into it with the following:

```

ssh -X -C user@remotehost

```

Then, on the remote host:

```

user@remotehost:~$ VirtualBox

```

And just like that, I have VirtualBox's GUI wizard up on my screen.  It then took me 20 seconds to set up a new VM.

As I said earlier, I imagine most of you already know this, but hopefully anyone else that somehow managed to miss it for years like myself, this comes in handy!

One little Caveat: On an 8.04 system, I had to do a quick apt-get install xauth before this would work.  On 10.04, xauth is already installed.

---

### Post by NeddyDownUnder on 2010-05-17
Thanks. I have been using ssh to forward ports regularly to my mac from my ubuntu server and I knew you could forward X11, I just didn't know how... Now I do. 

Cheers.

---

