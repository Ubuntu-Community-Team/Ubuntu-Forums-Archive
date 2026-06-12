---
title: "Cannot update remote Vista files"
date: 2010-01-20
forum: Security
---

### Post by JLahm on 2010-01-20
I am trying to access files on a laptop (running Windows 7) from an Ubuntu desktop running 9.10. I can view the Windows 7 files just fine. Listing their permissions from an Ubuntu terminal shows them to be read/write by everyone. But, I am unable to update any of the files from Ubuntu. 

I mount the files using the command:
mount -t cifs //richard-pc/C -o username=***,password=***,dir_mode=0777,fi
le_mod=0777 /mnt/windows7c

The permissions on the Windows 7 files on the laptop are set to Full Control by Everyone. 

Any ideas would be appreciated! Many thanks.  ---Jim

---

### Post by adam814 on 2010-01-20
In my experience useful network shares seem to be the most common thing blocked by the Windows Firewall.

Make sure you have sharing enabled in the "Network and Sharing Center" for starters.  Then I'd try using the IP of the machine instead of the computer name in case your WINS isn't resolving correctly.

---

### Post by JLahm on 2010-01-20
adam814: Thanks for the ideas. Unfortunately, I had the same thoughts. The firewall allows smb through (and I've also tried turning it off), the directories are being shared, and I've tried connecting connecting with the IP address. 

As I noted, I can see all of the shared directories and files just fine from Ubuntu once they've been mounted. Doing an "ls -l" shows all files owned by root with -rwxrwxrwx permissions. But, I cannot update any of them on Windows 7.

Very frustrating...

---Jim

---

### Post by cariboo on 2010-01-20
I know you are setting the read/write permissions to 777 with your mount command, but, did you check that the mount point is actually being set to 777? Are the permissions set recursively, in other words are all the directories set to world read/write?

---

### Post by JLahm on 2010-01-20
Unfortunately yes, I had made sure that all of the directories were set to 777.

---

### Post by adam814 on 2010-01-20
So what actually happens when you try to write to the Windows share?  Does it fail silently (might still log it somewhere) or give an error message?

---

### Post by JLahm on 2010-01-20
Sorry - good question - should have included that. When I access it from the command line I get: -bash: filename: Permission denied

Jim

---

### Post by cprofitt on 2010-01-20
In Windows the share permission are not the final arbiter of what happens.

If you gave full control to everyone of the share... but the NTFS rights -- the security tab -- still has right limited then the rights will be limited.

The way it works is that NTFS can take rights away from share permissions, but not add to them... and shares can not add to NTFS right either... so you have to set both up.


[IMG]http://performit.co.uk/network/images/2000_network-share-permissons.jpg[/IMG]

[IMG]http://www.novell.com/coolsolutions/img/17829-16.jpg[/IMG]

---

### Post by JLahm on 2010-01-21
That worked! I didn't realize the sharing permissions had been set incorrectly. Fixing those permissions allowed everything to work.

Many thanks! I really appreciate everyone's help.

Jim

---

### Post by cprofitt on 2010-01-21
> **JLahm said:**
> That worked! I didn't realize the sharing permissions had been set incorrectly. Fixing those permissions allowed everything to work.

Many thanks! I really appreciate everyone's help.

Jim


Glad to help; who knew my Windows skills would come in handy on the Ubuntu forums.

It would help other if you can mark the thread solved now.

---

