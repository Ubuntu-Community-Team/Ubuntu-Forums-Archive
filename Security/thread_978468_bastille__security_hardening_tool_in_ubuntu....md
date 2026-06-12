---
title: "bastille : security hardening tool in ubuntu..."
date: 2008-11-11
forum: Security
---

### Post by etdsbastar on 2008-11-11
Hello friends,

I have recently installed bastille, a security hardening tool from synaptic. But after setting all the configurations according to my suite, bastille is showing some error messages. 

Can anyone help me in curing or rectification of these errors...

> 
{Tue Nov 11 15:01:25 2008} Failed to place /psad as /usr/sbin/psad
{Tue Nov 11 15:01:25 2008} Failed to place /psadwatchd as /usr/sbin/psadwatchd
{Tue Nov 11 15:01:25 2008} Failed to place /kmsgsd as /usr/sbin/kmsgsd
{Tue Nov 11 15:01:25 2008} Failed to place /diskmond as /usr/sbin/diskmond
{Tue Nov 11 15:01:25 2008} #ERROR: chmod: File /usr/sbin/diskmond doesn't exist!
{Tue Nov 11 15:01:25 2008} Failed to place /psad-init as /etc/rc.d/init.d/psad
{Tue Nov 11 15:01:25 2008} #ERROR: chmod: File /etc/rc.d/init.d/psad doesn't exist!
{Tue Nov 11 15:01:25 2008} Failed to place /whois as /usr/bin/whois.psad
{Tue Nov 11 15:01:27 2008} #ERROR: chmod: File /usr/bin/g++ doesn't exist!
{Tue Nov 11 15:01:27 2008} ERROR:   Unable to delete Bastille lock file: /var/lock/bastille/bastille-lock
{Tue Nov 11 15:05:35 2008} ERROR:   A fatal error has occurred. Not all of the questions
         that pertain to this system have been answered.  Rerun
         the interactive portion of bastille on this system.
         MODULE.QUESTION=FilePermissions.suidprint
{Tue Nov 11 15:16:40 2008} Failed to place /psad as /usr/sbin/psad
{Tue Nov 11 15:16:41 2008} Failed to place /psadwatchd as /usr/sbin/psadwatchd
{Tue Nov 11 15:16:41 2008} Failed to place /kmsgsd as /usr/sbin/kmsgsd
{Tue Nov 11 15:16:41 2008} Failed to place /diskmond as /usr/sbin/diskmond
{Tue Nov 11 15:16:41 2008} #ERROR: chmod: File /usr/sbin/diskmond doesn't exist!
{Tue Nov 11 15:16:41 2008} Failed to place /psad-init as /etc/rc.d/init.d/psad
{Tue Nov 11 15:16:41 2008} #ERROR: chmod: File /etc/rc.d/init.d/psad doesn't exist!
{Tue Nov 11 15:16:41 2008} Failed to place /whois as /usr/bin/whois.psad
{Tue Nov 11 15:16:43 2008} #ERROR: chmod: File /usr/bin/g++ doesn't exist!
{Tue Nov 11 15:16:43 2008} ERROR:   Unable to delete Bastille lock file: /var/lock/bastille/bastille-lock
{Tue Nov 11 15:19:00 2008} Failed to place /psad as /usr/sbin/psad
{Tue Nov 11 15:19:00 2008} Failed to place /psadwatchd as /usr/sbin/psadwatchd
{Tue Nov 11 15:19:00 2008} Failed to place /kmsgsd as /usr/sbin/kmsgsd
{Tue Nov 11 15:19:00 2008} Failed to place /diskmond as /usr/sbin/diskmond
{Tue Nov 11 15:19:00 2008} #ERROR: chmod: File /usr/sbin/diskmond doesn't exist!
{Tue Nov 11 15:19:00 2008} Failed to place /psad-init as /etc/rc.d/init.d/psad
{Tue Nov 11 15:19:00 2008} #ERROR: chmod: File /etc/rc.d/init.d/psad doesn't exist!
{Tue Nov 11 15:19:00 2008} Failed to place /whois as /usr/bin/whois.psad
{Tue Nov 11 15:19:03 2008} #ERROR: chmod: File /usr/bin/g++ doesn't exist!
{Tue Nov 11 15:19:03 2008} ERROR:   Unable to delete Bastille lock file: /var/lock/bastille/bastille-lock
{Tue Nov 11 15:24:03 2008} #ERROR: chmod: File /usr/bin/g++ doesn't exist!
{Tue Nov 11 15:24:03 2008} ERROR:   Unable to delete Bastille lock file: /var/lock/bastille/bastille-lock


---

### Post by persistentstubborn on 2008-11-11
> **etdsbastar said:**
> ...
Can anyone help me in curing or rectification of these errors...

It's been a while when I used to use bastille for the last time, but from the messages it seems you haven't configured it properly. There are questions you are supposed to answer in interactive mode when setting bastille up.

BTW, bastille, harden and other hardening tools do make sense when installed on a clean system, immediately after a clean install and during configuration of the system. If installed subsequently, on a possibly already compromised box, they can make false feeling of security.

---

### Post by koenn on 2008-11-11
> **etdsbastar said:**
> Hello friends,

I have recently installed bastille, a security hardening tool from synaptic. But after setting all the configurations according to my suite, bastille is showing some error messages. 

Can anyone help me in curing or rectification of these errors...

Looks like the bastille script can't execute what it wants to, probably due to a lack of permissions.
Did you run it as root / with sudo ?

---

### Post by etdsbastar on 2008-11-11
> **koenn said:**
> Looks like the bastille script can't execute what it wants to, probably due to a lack of permissions.
Did you run it as root / with sudo ?

Ya,,, I ran it with sudo but the same problem occured.

Even I tried:** bastille -b** with root.

the same problem occured.

---

### Post by koenn on 2008-11-11
hm, most of those files the log complains about don't even exist on my pc (some do, but I may have installed them separately).
Looks as if bastille wants to do things that won't work on a default ubuntu system, or you made a bad choice somewhere in the configuration run ...

---

### Post by etdsbastar on 2008-11-15
can i have another choice of solution.... please

---

### Post by cariboo on 2008-11-15
Did you run:

```
/usr/sbin/InteractiveBastille -c
```

This will walk you through setting up Bastille.

From Synaptic:

> If run in the (recommended) Interactive mode, Bastille
educates the administrator during the hardening process:
in each step of the process, extensive descriptions are
given of what security issues are involved. Each step is
optional. If run in the quicker Automated mode, Bastille
hardens the system according the profile chosen.

Jim

---

### Post by bodhi.zazen on 2008-11-15
Not to be rude (don't take this the wrong way please) , but why are you installing something like bastille without reading the documentation ?

I highly advise against this course of action if you do not know what you are doing.

[https://help.ubuntu.com/community/BastilleLinux](https://help.ubuntu.com/community/BastilleLinux)

---

### Post by etdsbastar on 2008-11-18
> **bodhi.zazen said:**
> Not to be rude (don't take this the wrong way please) , but why are you installing something like bastille without reading the documentation ?

I highly advise against this course of action if you do not know what you are doing.

[https://help.ubuntu.com/community/BastilleLinux](https://help.ubuntu.com/community/BastilleLinux)

Dear, then what should I do to harden the security of my system.

Is there any other option. Please specify.

---

### Post by bodhi.zazen on 2008-11-18
> **etdsbastar said:**
> Dear, then what should I do to harden the security of my system.

Is there any other option. Please specify.

Security is an active process, there is no substitution for reading and education.

The "problem" with bastille, IMO, is that it will make changes to your system that may be difficult to undo. IMO you therefore need very much read and understand the installation and configuration. Even more so if you are getting error messages.

There are many many many ways to harden your system, see the stickies on the top of these forums, including the thread on snort and OSSEC. These may not be for you, and if not there are many other options.

See also : [http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

---

### Post by etdsbastar on 2008-11-20
Thanks for the posts.

Thank you very much to all of you friends for helping me.

---

### Post by erwall on 2008-11-23
> **etdsbastar said:**
> Dear, then what should I do to harden the security of my system.

Is there any other option. Please specify.

If you really want to learn how to harden a machine, do it by hand.  Fill out the following and follow the directions in the corresponding pdf.

[http://www.cisecurity.org/sub_form.html](http://www.cisecurity.org/sub_form.html)

---

### Post by docfx on 2008-12-14
I can't get Bastille to actually complete the process. I'm trying to harden Ubuntu 8.04.1 on a gutted OSX-server w/LVM before I start porting client domains from an old RH webserver.

I'm getting:
```
ERROR: System is not running a stable Debian GNU/Linux version. Setting to 4
```

any thoughts?

---

