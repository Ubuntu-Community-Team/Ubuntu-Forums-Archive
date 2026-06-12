---
title: "Still not quite able to install VMware Server"
date: 2009-03-16
forum: Virtualisation
---

### Post by JerryI on 2009-03-16
I am getting closer to installing VMware 1.0.6 in Hardy, but I have encountered the following hiccup.  I would appreciate enlightenment re. what to do next.  How do I obtain and install the VMware VmPerl Scripting API (whatever that is)?  Thanks in advance for any help.

---------------------------------------------------------------------
Unable to compile the VMware VmPerl Scripting API.

********
The VMware VmPerl Scripting API was not installed.  Errors encountered during 
compilation and installation of the module can be found here: 
/tmp/vmware-config0

You will not be able to use the "vmware-cmd" program.

Errors can be found in the log file: 
'/tmp/vmware-config0/control-only/make.log'
********

Unable to get the last modification timestamp of the destination file 
/etc/vmware/ssl/rui.key.  Execution aborted

---

### Post by yeats on 2009-03-16
Hi - have you considered VirtualBox?  I have found it to be much more straightforward and would probably be a better option (unless your goal is a VMWare server to be used by other network clients).  If you're trying to use other OS's on one machine, VirtualBox is the way to go IMHO.

Info here:

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by JerryI on 2009-03-16
Thanks. I will consider Virtualbox if I cannot get VMware to run within the next few days.  Sofar, I have found Ubuntu and everything associated with it to be extremely difficult to negotiate, but I guess that is just part of the learning curve.  Meanwhile, I hope someone will suggest how to continue on my present path with VMware.

---

### Post by Slancher on 2009-03-16
Here's a tutorial I found  [http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04](http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04)

Try to stick with linux for a while.  Once you know your way around a little better I think you will love it.

---

### Post by JerryI on 2009-03-16
Thanks, but I don't think running the same install tutorial again will help.  I think I will hit the same snag.  I would appreciate assistance from anyone who might be able to tell me how to install the VMPerl Scripting API.  Meanwhile I'll keep trollng for a solution, and if I don't come up with one in a day or so, I'll pursue the VirtualBox approach, which has already led me to my first snag in that path.

Sofar, my Ubuntu adventure has been a lot tougher than I imagined it would be.  I can't even get a valid installation of Adobe whatever to allow me to look at a Youtube tutorial.

---

### Post by yeats on 2009-03-16
```

Errors can be found in the log file:
'/tmp/vmware-config0/control-only/make.log'
```

Can you open this file and paste the content here?

> Sofar, my Ubuntu adventure has been a lot tougher than I imagined it would be. I can't even get a valid installation of Adobe whatever to allow me to look at a Youtube tutorial.

Are you running 64-bit Ubuntu?  If so there are workarounds to get flash working ....

Stay with it.  You can get good help here on the forums if you're clear and persistent.  I *completely* understand your frustration though :-).

---

### Post by JerryI on 2009-03-16
I'm not intentionally running 64-bit Ubuntu, but who knows?  Tell me how to find the answer and I'll post the results.  I really do appreciate the helpfulness of the Ubuntu community.

Here's what I'm working on now.  The associated download looks like it will take 30 minutes or so.  Very interesting post.  Reminds me of some of the errors I've seen in Vista.

-----------------------------------------------------------

The error message is very misleading and suggests there is a perl problem. This is however not true!!!! - I solved this by installing the libssl-dev code and the running the VMware install again.

To install libssl-dev enter the following

sudo apt-get install libssl-dev

The download can take a while on 1mb broadband so go make a cup of coffee and by the time you have done this the problem should be gone.

--------

Another problem I had with VMWare and 64bit Ubuntu was that the 32bit compatibility libraries are not installed by default. While VMWare is happy to run in 64bit it still needs these libraries. Again the error message for this one is misleading claiming that the vmware-ping cannot be found or executed and that no subnets can be automatically probed for.

Fix it with this:-

sudo apt-get install ia32-libs*

---

### Post by yeats on 2009-03-16
> I'm not intentionally running 64-bit Ubuntu, but who knows? Tell me how to find the answer and I'll post the results. I really do appreciate the helpfulness of the Ubuntu community.

do this at the terminal:

```
uname --all
```

and post back the result...

---

### Post by JerryI on 2009-03-16
jerry@downstairs:~$ uname --all
Linux downstairs 2.6.24-23-generic #1 SMP Thu Nov 27 18:13:46 UTC 2008 x86_64 GNU/Linux
jerry@downstairs:~$ 

That's what I'm running.  Is it 64 bit?  If so, what kind of problems will that create?

I installed the stuff mentioned in the previous post and am happy to report that vmware is supposedly installed.  I have not run it yet.  I had to reboot the computer after installing all the libs and rerunning the VMware install.  I still have not figured out why my invidia dual-monitor thing hasn't worked yet or why I can't get Adobe to do its thing, but I am progressing.  Thanks again for lots of help.  I'll keep posting elementary questions until I either get this thing running or decide to forget it and go back to the Vista devil.

---

### Post by yeats on 2009-03-16
> That's what I'm running. Is it 64 bit? If so, what kind of problems will that create?

64 bit has a little more trouble with flash (not sure what the issues are).  You might Google "64-bit Ubuntu Flash" or somesuch to see guides to work around this.

Good luck.

---

