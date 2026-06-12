---
title: "[SOLVED] VMware server 2 64bit install help."
date: 2008-10-29
forum: Virtualisation
---

### Post by dmizer on 2008-10-29
I keep getting the following error:
```
Your kernel was built with "gcc" version "4.2.3", while you are trying to use
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and
VMware Server may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler
"/usr/bin/gcc" version "4.2.4" anyway? [no]
```

I've tried resetting the CC variable according to this thread: [http://www.linuxquestions.org/questions/linux-software-2/export-ccusrbingcc-4.1-614342/](http://www.linuxquestions.org/questions/linux-software-2/export-ccusrbingcc-4.1-614342/)

gcc --version gets this:
```
gcc (GCC) 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

I'm missing something pretty basic. Most of the searching I've done has provided very little in the way of progress. I've even tried forcing the install anyway, but the install was broken.

Thanks

---

### Post by colinlr on 2008-10-29
What base os are you using to install vm server2 onto
I have used ubuntu server 8.04 64 bit and had no such issues.

---

### Post by dmizer on 2008-10-29
Thank you for your reply,

My host system is Xubuntu Hardy 64bit.

---

### Post by dmizer on 2008-10-29
Okay, I believe I have it installed correctly now. I still have a huge problem. I cannot get the web interface to start.

```
$ sudo /etc/init.d/vmware restart
Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
[B]   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed[/B]
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family:                           done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   VM communication interface socket family:                           done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   VMware Server Authentication Daemon (background)                    done
   Shared Memory Available                                             done
Starting VMware management services:
   VMware Server Host Agent (background)                               done
**   VMware Virtual Infrastructure Web Access**
Starting VMware autostart virtual machines:
   Virtual machines                                                   failed

```
Now what?

---

### Post by colinlr on 2008-10-29
This may sound stupid but it your apache server configured and up and running?

---

### Post by dmizer on 2008-10-29
> **colinlr said:**
> This may sound stupid but it your apache server configured and up and running?

Not stupid at all. I have no Apache server on the host machine. I read that the Vmware Server had its own html server, and nothing about system requirements indicated that I should have an active web server on the host. None of the howto's (including the one [at the top of this page](http://ubuntuforums.org/showthread.php?t=779934)) indicate anything about having an active web server either.

The [release notes](http://www.vmware.com/support/server2/doc/releasenotes_vmserver2.html) on vmware's site indicate possible conflicts with Apache:
> ... stop IIS's default Web site or any other Web site running on these ports. On Linux, shut down Apache or any other application using these ports and make sure they are not configured to restart automatically.

Have I misread? If so, do I have to install Apache, or would LightTPD be acceptable?

---

### Post by dmizer on 2008-10-30
I have gotten nowhere with this. I have zero access to vmware's web or console interface. I can restart all the vmware services but nothing seems to be happening. I've tried installing both LightTPD, and Apache2, but neither make any improvement. I don't even know where to start troubleshooting this.

For most people,
```
sudo /etc/init.d/vmware-mgmt restart
```
seems to fix the problem, but I'm left high and dry.

---

### Post by gerryg001 on 2008-10-30
Ouch. I know that happened to me, after the last ubuntu kernel update. I do not have apache running here, but latest Hardy-64 and vmware server. Couldn't find the problem quickly and, best I can recall, rebuilding and reinstalling vmware a 2nd time made the issue go away. Been working okay now for several weeks.

---

### Post by dfreer on 2008-10-30
> **dmizer said:**
> I keep getting the following error:
```
Your kernel was built with "gcc" version "4.2.3", while you are trying to use
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and
VMware Server may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler
"/usr/bin/gcc" version "4.2.4" anyway?
```


This is a common problem for me trying to install the official NVIDIA drivers. This how I normally solve it:
(1). Make sure you have the version you need of GCC installed, so gcc-4.2.3 I think.
(2). I believe you need to be root to install vmware-server, so make sure you run the following as root:
```
export CC='gcc-4.2.3'
```
You can test to make sure it worked like so:
```
echo $CC
```

Hmmm... it appears like you can only install gcc-4.2, and you can't specify whether you want to install gcc-4.2.3 or gcc-4.2.4... You could give recompiling your kernel a try, if you use your existing kernel .config you shouldn't have to change anything, just recompile.

Not sure why your web interface isn't working, note at the bottom of the output you posted it shows the web interface supposedly starting.

---

### Post by dmizer on 2008-10-31
I knew this had to be something rediculously simple. So simple in fact, I never found it. I ended up simply reinstalling Ubuntu on the guest, and the install went without a hitch.

I did not have to change the gcc variable. I just answered yes to the question when it asked me, "Do you want to go with compiler "/usr/bin/gcc" version "4.2.4" anyway?" Everything seems to be working fine now. Had a few hangups with learning the new interface, but otherwise everything works.

Web interface is super slow though.

Anyway, marking this one as solved, even though it was a decidedly Windows style fix.

---

### Post by sgla1 on 2008-12-31
> **dmizer said:**
> Not stupid at all. I have no Apache server on the host machine. I read that the Vmware Server had its own html server, and nothing about system requirements indicated that I should have an active web server on the host. None of the howto's (including the one [at the top of this page](http://ubuntuforums.org/showthread.php?t=779934)) indicate anything about having an active web server either.

The [release notes](http://www.vmware.com/support/server2/doc/releasenotes_vmserver2.html) on vmware's site indicate possible conflicts with Apache:


Have I misread? If so, do I have to install Apache, or would LightTPD be acceptable?

You are right about vmware server 2 including it's own web server: it's tomcat installed at: 
/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16

Once vmware is running if you run 
```
ps -ef | grep [v]mware
``` you will see it.

Tomcat for vmware runs on ports 8222 and 8333, so it "shouldn't" conflict with apache.

---

