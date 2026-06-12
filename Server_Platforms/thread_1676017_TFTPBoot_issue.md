---
title: "TFTPBoot issue"
date: 2011-01-26
forum: Server Platforms
---

### Post by dmb-barnes on 2011-01-26
Good afternoon everyone,

**First, I must state that I am new to Ubuntu but I've jumped in with both feet in trying to learn to use it.  I've changed my work computer to Ubuntu as well as my netbook that use when I travel. [plus a boxee PC I have at home...]


I have a Ubunutu 10.10 64 bit server that started out a 9.?? server.  The main purpose of this server is to run Clonezilla for drive imaging.  Later I did server updates that did something with TFTP. - not sure what but I did receive a TFTP open timeout error.

About a month later I started getting messages that / had only 1.3 gigs free.  I was able to do some clean up of orphaned files which helped this.  However, I updated the server to 10.10 yesterday and I started receiving the message again.  This time I looked into a little bit more and found that clonezilla creates nodes in the TFTPboot area for each computer that connects to it for imaging.

Ok.. all of the above to ask what I hope is a simple question...
Clonezilla uses DRBL.  Is there a config file or setting someone that I can change that will allow me to either reinstall TFTP or move the TFTPBoot directory to a different path?

I have a data partition that has plenty of space.   

Thank you... I will try to answer any question(s) you might ask...

dmb

---

### Post by koenn on 2011-01-26
your tftp probably comes from the clonezilla server / DRBL so you might find a tftp or clozilla or rdbl conf in /etc or /etc/defaults

this might help to find it
```
find /etc -name *tftp*
```

or this
```
grep -lr 'tftp'  /etc
```

far easier, probably, is to mount that extra disk you have to /tftpboot
to do so, add a suitable statement to /etc/fstab, and run 'mount -a'

homework: find a way to delete or move the current content of /tftpboot, because it will be unreacheable if you permanently mount an other disk/partition.filesystem there. Also, if that data partition is already being used, you need an alternative solution for those files as well.

---

### Post by dmb-barnes on 2011-01-26
Thank you Koenn,

The data partition is being used.  I guess my solution is tainted more from windows than I thought.  I thought it would be enough to tell DRBL or clonezilla that the TFTPboot folder is in another location.

I might be able to mount another HD to this machine but I do not know if 1. there is enough room inside or if 2. the SATA raid card will allow a HD off of the motherboard.  This is a reload HP ML110 file server.

I will try to find files with TFTP in them.

As for what is in that location... I don't need it.  Once I try to reload DRBL it recreates the nodes for the IP range I setup.

Thanks

Mike

---

### Post by koenn on 2011-01-26
> **dmb-barnes said:**
> 
The data partition is being used.  I guess my solution is tainted more from windows than I thought.  I thought it would be enough to tell DRBL or clonezilla that the TFTPboot folder is in another location.
well, yes, but you do that by editing its config file. You're problem is you don't know what tftp you're running, so we're kinda guessing at what the relevant config file might be.

---

### Post by dmb-barnes on 2011-01-27
Is there a way to tell which type? I know that when I tried to configure DRBL yesterday it was asking for more space to create the nodes inside the TFTPBoot folder.  Beyond that I guess I'm clueless...

Here are the results of the two commands you gave me...

/etc/default/tftpd-hpa
/etc/default/tftpd-hpa.old
/etc/group-
/etc/group
/etc/passwd
/etc/services
grep: /etc/dictionaries-common/words: No such file or directory
/etc/shadow
/etc/bash_completion.d/qemu
/etc/gshadow-
/etc/inetd.conf
grep: /etc/blkid.tab: No such file or directory
/etc/exports
/etc/gshadow
/etc/exports.drblsave
grep: /etc/apparmor.d/disable/usr.bin.firefox-3.5: No such file or directory
/etc/init/tftpd-hpa.conf
grep: /etc/alternatives/ex.it.1.gz: No such file or directory
grep: /etc/alternatives/usplash-artwork.so: No such file or directory
grep: /etc/alternatives/vi.fr.1.gz: No such file or directory
grep: /etc/alternatives/ex.ru.1.gz: No such file or directory
grep: /etc/alternatives/vi.it.1.gz: No such file or directory
grep: /etc/alternatives/view.pl.1.gz: No such file or directory
grep: /etc/alternatives/view.it.1.gz: No such file or directory
grep: /etc/alternatives/vi.ru.1.gz: No such file or directory
grep: /etc/alternatives/view.fr.1.gz: No such file or directory
grep: /etc/alternatives/ex.pl.1.gz: No such file or directory
grep: /etc/alternatives/vi.pl.1.gz: No such file or directory
grep: /etc/alternatives/view.ru.1.gz: No such file or directory
grep: /etc/alternatives/ex.fr.1.gz: No such file or directory
/etc/shadow-
/etc/passwd-
]0;root@otnubuntusvr: ~root@otnubuntusvr:~# find /etc -name *tftp*
/etc/default/tftpd-hpa
/etc/default/tftpd-hpa.old
/etc/init.d/tftpd-hpa
/etc/init.d/tftpd-hpa.dpkg-bak
/etc/init/tftpd-hpa.conf

Thank you

Mike

---

### Post by koenn on 2011-01-27
if the tftp server is started by inetd, you may just need to change the tftp line in /etc/inetd.conf (modify or append  -s /path/to/alternate/tftpboot

if not, look in
/etc/default/tftpd-hpa
/etc/init/tftpd-hpa.conf
or maybe /etc/exports.drblsave


in any case, make sure the new dir exists and has the same permissions as the old /tftpboot

---

