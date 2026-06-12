---
title: "rsync from ubuntu to windows server 2k3"
date: 2009-05-17
forum: Server Platforms
---

### Post by shadowpr on 2009-05-17
I've been trying to get rsync to work for the past 2 days. I originally had an external drive connected to my linux computer. I used rsync to copy my personal drive to the external. No problems there. 

I have since made a windows server 2003 computer. I connected the external backup drive to that. I now want to use rsync to copy all my personal files to that.

My personal files are on a second hard drive. For now, i'm just trying to get a test file or two to transfer over to a test folder on a second drive on the windows 2003 computer.

This is what I type in the terminal:> rsync -vprtWO  --ignore-errors --delete --force --delete-excluded  --stats --log-file=testlog /media/Personal/ username:userpassword@192.168.1.100:share

I've tried without userpassword, and still no go.

I know I could just mount the share folder and then use rsync that way (I tested it, and it works great) but I rather not mount it if I don't have to.

I also tried to install cwRsyncServer on server 2003, but had no effect. I'm probably not configuring it right.

Feel like I'm in over my head.

Any help or hints as to what I'm doing wrong would be greatly appreciated.

Thanks.

---

### Post by jesuspresley on 2009-05-17
Why don't you mount the share first? I did so to give rsync easy access to the Windows files - and the sync ran totally smooth. 

If you stick to do it the other way: Try to become a member of the Windows domain /workgroup first with Kerberos, Winbind and a "net ads join -U [email]Administrator@COMPUTER.DOMAIN[/email]" command....

Sorry I think I can't help you any further

---

### Post by HermanAB on 2009-05-18
If you don't want to mount shares, then install Cygwin and SSH Server, then do rsync over SSH with 'rsync -e ssh ...'.

---

### Post by koenn on 2009-05-18
> **HermanAB said:**
> If you don't want to mount shares, then install Cygwin and SSH Server, then do rsync over SSH with 'rsync -e ssh ...'.

or run DeltaCopy on the W2k3 server

---

### Post by shadowpr on 2009-05-18
Is Cygwin and SSH Server or DeltaCopy that much different from cwRsyncServer? 

If so, should I just delete cwRsyncServer and go with either deltacopy or cygwin?

Do I need ssh since this is a home lan?

And I plan on adding some windows computers to this mix later. They will also have to send backup files to the win server 2k3 computer.

(sorry for being a pain. this is the first time I can't find a simple enough tutorial online.)

Oh yeah, what about using the rsync daemon? Someone else mentioned that was good, and might help.

---

### Post by koenn on 2009-05-18
I only know DeltaCopy, and I know it works, and isn't hard to set up.

How to backup or copy between Win2k3 and XP is a Windows problem, isn't it.

Rsync daemon is just a different way of using rsync. Any which way, you're always going to need something on the Windows side that can deal with rsync, since it's not native to Windows.

---

### Post by shadowpr on 2009-05-20
Thanks everyone.

I actually got it to work with cwrsync. I edited the rsyncd.conf file which is located in c:\program files\ICW\

[HTML][doctest]
path = /cygdrive/c/doctest
read only = false
transfer logging = yes
[/HTML]

and then edited my rsync command with: 

[HTML]rsync -vprtWO --ignore-errors --delete --force --delete-excluded --stats --log-file=testlog /source/documents rsync://192.168.1.206/doctest[/HTML] 

This seems to work well. Had to open the port for it as well.

Only problem this gives me is no support for spanish characters. Trying to figure that one out now.

---

### Post by fungiscience on 2011-02-02
shadowpr : Can you explain how you setup cwrsync server on your windows machine. I tried basicaly the same steps with windows firewall off and I get "Connection refused on port 22" from ubuntu shell. I wan't to use rsync over shh from Ubuntu server machine to windows for an automated backup system with BackupPC software running on Ubuntu server.


PC1: Windows 7 64 bits with cwrsync and cwrsyncserver (v4.05)

PC2: Ubuntu server 10.10


I modified the rsyncd.conf to add a share.

I'm using the following command to copy my ssh_key to windows machine:

```

rsync -e ssh /pathto/sshkey username@windowsip::modulename

```

I also tried the version you proposed :

```

rsync -e ssh /pathto/sshkey rsync:://windowsip/modulename

```

Any hints?

---

