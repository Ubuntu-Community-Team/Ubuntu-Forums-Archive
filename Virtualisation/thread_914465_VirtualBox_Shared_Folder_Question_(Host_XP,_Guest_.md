---
title: "VirtualBox Shared Folder Question (Host: XP, Guest: Ubuntu)"
date: 2008-09-08
forum: Virtualisation
---

### Post by Kamek on 2008-09-08
I have a shared folder set up in VirtualBox to transfer files between my XP host and my Ubuntu guest. Under ubuntu, the command to mount my shared folder is:

```
sudo mount -t vboxsf "VirtualBox Share" /media/share
```

I'd like to set this up in /etc/fstab so that I can have the shared folder mounted on boot, but I can't figure out how to set it up properly.

I tried this, but got "line 11 in /etc/fstab is bad" when I tried mount -a:

```
"VirtualBox Share" /media/share vboxsf rw 0 0
```

Thanks in advance to anyone who can help.

---

### Post by HermanAB on 2008-09-09
Rather than fighting with shared folders, I use SSH, SFTP or FTP with Filezilla.  This seems to be far less trouble.

Install the Filezilla FTP server on your Windows host and you are in business.

---

### Post by gkbhat on 2008-10-28
> **HermanAB said:**
> Rather than fighting with shared folders, I use SSH, SFTP or FTP with Filezilla.  This seems to be far less trouble.

Install the Filezilla FTP server on your Windows host and you are in business.
I have set up fiezilla in winxp host and it works will with the client in xp.
I set up filezilla cleint  in ubuntu in virtual box and gave 127.0.0.1 as address and 21 as port and username, password. It gives error cannot connect to server. Can you please help in setting up ftp file tranfer?
Bhat

---

### Post by Greyed on 2008-10-28
> **Kamek said:**
> ```
"VirtualBox Share" /media/share vboxsf rw 0 0
```Thanks in advance to anyone who can help.

The space in the name is probably killing it.  Mine works fine with no space.

```

C_DRIVE         /mnt/C          vboxsf  rw,uid=1000     0       0

```

---

### Post by Lutshow on 2010-07-09
Using a transfer protocol such as FTP et al. implies duplicating the involved files in order to use them. Shared folders offer the advantage to actually share file (or I am wrong ?)

---

### Post by JustinR on 2010-07-09
To my understanding if there are spaces in a devices/objects name there needs to be a special slash.

So instead of:

"VirtualBox Share" /media/share vboxsf rw 0 0"

do this:

""VirtualBox\ Share" /media/share vboxsf rw 0 0"

In newer versions of VirtualBox it doesn't allow you to put spaces in Shared Folders names. So when you share a folder, eg. called "My Documents" you have to put something such as an underscore instead of a space like "My_Documents" or no space at all before it can be accepted as a shared folder.

---

### Post by hytek on 2010-11-17
Sometimes my shared folder doesn't like to mount, so I just created a shell script inside the folder I mount the shared folder to. If I see the shell script, I know the mount isn't mounted. Then I just run the shell script and all is good again.

I have tried a few ways to use pmount so gksu wasn't needed, but pmount I don't think likes vboxsf for as an option...

```
#!/bin/bash

if [ "`mount | grep /path/to/folder`" == "" ]
        then
                 gksu "mount -t vboxsf sharedFolderName /path/to/folder"
fi

exit 0

```

You can even put this in your bash script to check at logon, or even in a crontab to check periodically...

---

