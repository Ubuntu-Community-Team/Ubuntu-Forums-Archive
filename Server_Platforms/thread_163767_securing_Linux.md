---
title: "securing Linux"
date: 2006-04-21
forum: Server Platforms
---

### Post by ice60 on 2006-04-21
hi, i just found this about securing Linux, i haven't really been through it yet, but i'm going to go through it bit by bit :mrgreen: 

i don't know about shadow passwords, i'll have to look it up. but, i'm going put this in **/etc/hosts.deny**
```
 ALL: ALL
```
i don't use remote logins so i'll leave it at that. is that OK to do?

i'm going to go through 7 in a bit, is it OK to comment out all those services? thanks.
[http://www.linux-sxs.org/security/scheck.html](http://www.linux-sxs.org/security/scheck.html)

---

### Post by ice60 on 2006-04-21
BTW, i found it on this site
[http://www.linux-sxs.org/](http://www.linux-sxs.org/)
click on security in the column and there's some other stuff there too.:cool:

---

### Post by h3llfyr3 on 2006-04-23
That only helps if you ae using external services such as ssh and then have entries in hosts.allow .
If someone whacks your server with some exploit they can still get a reverse bind shell . At least that's my experience of it.

---

### Post by LordHunter317 on 2006-04-23
There's no such thing as a 'reverse bind shell' so I don't have the slighest idea what you're talking about.

Not every service uses TCP wrappers so doing that won't make your box secure.  Apache doesn't use it, for example.  Most FTP servers don't.  

You need to explain what you're running and who needs to access it, then we can describe how to secure it.

---

### Post by ice60 on 2006-04-25
hi, when i went through 7 at [this](http://www.linux-sxs.org/security/scheck.html) link it says this -
> In [color=blue]/etc/inetd.conf[/color], comment out all services you don't use regularly. Each service is a potential security risk. but, when i open /etc/inetd.conf there's nothing there :confused: does that mean Ubuntu is hardened already? or do i have to comment out these things somewhere else? 

i don't use remote logins, so i want to disable anything which is running and is only needed for that purpose. can you explain what i should do? thanks.

---

### Post by ice60 on 2006-04-25
btw, i am using a standalone desktop. i just want to disable as much as possible to start off, then see if i can harden any needed services.

when i have disabled/uninstalled un-needed things should i use something like [Bastille](http://www.bastille-linux.org/)? what about trip-wire? what else is there? thanks.

---

### Post by auroraborealis on 2006-04-25
Hey check out the CERT VTE library. You can't access the labs, but there's other good stuff on there. Search Linux and it should come up with a bunch of things (Securing Linux Systems Demo might be of interest). If you want the lab documents though, I can get em to you...

[https://www.vte.cert.org/vtelibrary.html](https://www.vte.cert.org/vtelibrary.html)

---

### Post by ice60 on 2006-05-05
[QUOTE=auroraborealis]Hey check out the CERT VTE library. You can't access the labs, but there's other good stuff on there. Search Linux and it should come up with a bunch of things (Securing Linux Systems Demo might be of interest). If you want the lab documents though, I can get em to you...

[https://www.vte.cert.org/vtelibrary.html](https://www.vte.cert.org/vtelibrary.html)[/QUOTE]
thanks, aurora. 

**[color=red]EDIT[/color] I'M NOT DOING THIS NOW (below), APT NEEDS TO EXECUTE STUFF IN /tmp**
i want to do this next
> [b]Mount /tmp as noexec
[/b]Many exploits and script kiddies rely on downloading scripts to /tmp and executing them, by mounting /tmp as noexec, scripts located in /tmp will not be executable, effectively disabling exploits that rely on /tmp, and stumping many script kiddies, here is the /tmp config line from my /etc/fstab:
/dev/hda5 /tmp ext2 noatime,noexec 0 0

my fstab looks like this
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda5 	/media/windows2 ntfs 	umask=0222
```
can i use the "Mount /tmp as noexec"? or do things need it to work for a desktop user and i should leave it?

---

### Post by ice60 on 2006-05-05
i've added these two lines to /etc/security/limits.conf to help warn/stop of Fork Bombs. they limit a user to 150 processes and warn you when you get to 100.
@users soft nproc 100
@users hard nproc 150

---

### Post by ice60 on 2006-05-06
i'm thinking of installing libsafe from synaptic.
> Protection against buffer overflow vulnerabilities
Libsafe is a library that works with any pre-compiled executable and can be
used transparently. Libsafe intercepts calls to functions known to be
vulnerable.  Libsafe uses a substitute version of the function that
implements the same functionality, but makes sure any buffer overflows are
contained within the current stack frame.
has anyone installed it? thanks.

i just found out there's "No maintainer for libsafe"
[http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=libsafe](http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=libsafe)
i found this too
> Just install the package and say Yes to have the library preloaded globally. Be careful, however, since this might break software (notably, programs linked with the **old libc5**), so make sure to read the reported bug reports first and test the most critical programs in your system first with the libsafe wrapper program.
i don't use any version of libc5 so maybe it's OK to use ??? can anyone help me?

---

