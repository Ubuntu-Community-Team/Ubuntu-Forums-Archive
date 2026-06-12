---
title: "[SOLVED] Ubuntu Server 8.10 on a Dell Poweredge 2600"
date: 2008-11-13
forum: Server Platforms
---

### Post by dulbirakan on 2008-11-13
Hi, 

I just installed 8.10 server edition on a poweredge 2600 and I cannot boot. The machine has 3x34 gb disks forming up a RAID 5 72 gb logical drive. Installation and everything goes fine except the booting...

Previously there was FC4 installed on the machine and it was booting fine...

What I got as an error message was:

```
[8.450015] io2: iop0: Get status timeout.
Gave up waiting for root device. Common problems.

-Boot args...
.
.
.
.
Alert! /dev/disk/by-uid/08af.........fb56 does not exist. Droping to a shell

Busy box........
.
.
(initramfs) [ 38.460014] io2: iop0: IOP reset timeout.
[38.460067] io2: iop0: could not activate the controler.
[68.470013] io2: iop0: IOP reset timeout.
```

I tried changing the raid controler to mass storage and did a reinstall, I even did a LVM install. Still the same problem...

I am giving the error messages for Mass Storage below:

```
Gave up waiting for the root device. Common problems

-Boot args...
.
.
.
.
Alert! /dev/mapper/***-root does not exist. Droping to a shell

Busy box........
.
.

(initframs)  [40.795786] sd 4:2:0:0: [sda] asking for cache data failed
[40.795848] sd 4:2:0:0: [sda] Assuming drive cache: write through
[40 796379] sd 4:2:0:0: [sda] Asking for cache data failed
[40.796441] sd 4:2:0:0: [sda] Assuming drive cache: write through

```

---

### Post by dulbirakan on 2008-11-15
No replies?

---

### Post by iponeverything on 2008-11-15
try updating the Perc firmware.

---

### Post by madtom1999 on 2008-11-16
This seems to be a common problem with 8.10 - I have it on 3 machines I have upgraded from 8.0.4.
Some say the solution is to edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel. Which has worked for me but makes the boot time ridiculous. I guess you can reduce the 90 until it stops working and step back ...

---

### Post by dulbirakan on 2008-11-18
Thank you guys, I will try them tommorow and report back. :)

---

### Post by mike010 on 2008-11-18
does any of the groupware software work from linux to windows?
i am looking for a open source software something like ms exchange
or at least close to it.

---

### Post by dulbirakan on 2008-11-19
I tried adding bootdelay=90 to the kernel line and it worked. I previously tried with 60 which did not work.

About the PERC update, I think that might be the permanent solution to this problem but I currently do not have any floppy disks...

---

### Post by Lars Noodén on 2008-11-22
> **mike010 said:**
> does any of the groupware software work from linux to windows?
i am looking for a open source software something like ms exchange
or at least close to it.

For a drop-in replacement for MS Exchange, look at:
[INDENT][http://www.damnvulnerablelinux.org/](http://www.damnvulnerablelinux.org/)[/INDENT]

;)

If you're looking for a working mail server alone, then check:

simta
[INDENT]    [http://rsug.itd.umich.edu/software/simta/](http://rsug.itd.umich.edu/software/simta/)[/INDENT]
Dovecot
[INDENT]    [http://www.dovecot.org/](http://www.dovecot.org/)[/INDENT]
Postfix
[INDENT]    [http://www.postfix.org/](http://www.postfix.org/)[/INDENT]
Exim
[INDENT]    [http://www.exim.org/](http://www.exim.org/)[/INDENT]
Sendmail
[INDENT]    [http://www.sendmail.org/](http://www.sendmail.org/)[/INDENT]


If you are looking for integrated Scheduling/PIM/Mail, try starting with these:

    Kolab
[INDENT]        [http://www.kolab.org/](http://www.kolab.org/)[/INDENT]

    Citadel
[INDENT]        [http://www.citadel.org/](http://www.citadel.org/)[/INDENT]

    Zimbra

[INDENT]        [http://www.zimbra.com/](http://www.zimbra.com/)[/INDENT]

---

### Post by AdriaanseJP on 2009-01-20
> **dulbirakan said:**
> I tried adding bootdelay=90 to the kernel line and it worked. I previously tried with 60 which did not work.

About the PERC update, I think that might be the permanent solution to this problem but I currently do not have any floppy disks...

Would you mind elaborating the steps to do this? I'm having the exact same issues, I updated to the latest firmware Dell has on their site with no luck.

I tried editing directly in GRUB, which wouldn't save changes, then modifying menu.lst with a rescue disk; somehow I suspect I'm missing some critical :KS

Thanks!

---

### Post by y@w on 2009-01-20
> **mike010 said:**
> does any of the groupware software work from linux to windows?
i am looking for a open source software something like ms exchange
or at least close to it.

Check out Zimbra. The web GUI is a very similar experience to Outlook but is much better. It's what Yahoo! mail uses for its frontend (since Yahoo! now owns Zimbra).

---

