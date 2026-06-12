---
title: "Multiple Ubuntu Server users need access to shared files on a Windows domain"
date: 2013-06-24
forum: Server Platforms
---

### Post by CQIT on 2013-06-24
Sorry for the crazy title, but that's the best way I can explain my problem. I've looked all over the internet and on Ask Ubuntu, but have yet to find a solution that works.

My work runs a Windows domain where most of our users keep their personal files. We do a lot of heavy computation, and sometimes the programs we need are only available, or work better or faster, on Linux. So, earlier this year we acquired a heavy-duty computing machine that runs Ubuntu Server. Naturally, since our users have their files on the Windows share, we wanted to mount some of its shared folders on this new machine. We set up a cifs mount in fstab, and that almost worked: try as we might, we haven't been able to change the permissions for any of the files or folders in the share to anything but 755. 

What we need to be able to do is allow a group of our users to read and write stuff to the share from the Linux machine, but it seems like we can't do this with CIFS. Would NTFS-3G work better with its user-mapping features? Would some other alternative work best? I can provide more information about the setup if necessary.

Thanks for your help!

---

### Post by 3L33T on 2013-06-24
The easiest solution is to create 2 samba shares of the same windows folder:

1. Name one samba share "docdata" and give it read only permission in Samba.   Mount this share name in the windows desktop users who need read only access to this share.

2.  Name the second share "docdata-rw" and give it read and write permission in Samba.  Mount this share name in the windows desktop users who need the read-write access to the share.

Do not broadcast the share names of both Samba shares.

---

### Post by koenn on 2013-06-24
> **CQIT said:**
> We set up a cifs mount in fstab, and that almost worked: try as we might, we haven't been able to change the permissions for any of the files or folders in the share to anything but 755. 

Usually this is done the other way around, where a linux server serves files to windows clients. I'm not aware of any ready to use recepes for the situation you describe.

The root of your issue is that you're dealing with the NTFS ACL of the WIndows filesystem that you share  (+ maybe Windows "share permissions" on top of it).  I'm asuming you use NTFS, not FAT. 
There are several possible issues with that :
- the standard linux (unix) file modes (ugo rwx  or numbers like 750 or 640) don't translate to NTFS ACL; therefore "setting permissions" from the linux side is next to impossible
- when you mount with -t cifs, you do so under a specific user account known on the windows side. This account may or may not have the required privileges to change NTFS ACL

you could install posix acl on your linux server and see if the commands this provides (eg setacl) can be used to manipulate the NTFS ACL. NTFS ACL and POSIX ACL are pretty similar, so this might get you closer to a solution. 

Then you have to consider the whole user account side of the problem : you have linux accounts on one side, windows accounts on the other side, and 1 windows account that mounts the share. I'm guessing this means your linux accounts access the shared files with the privileges of the 'mounting' account, so you may need to set the NTFS ACL privileges of that account on the shared files in such a way that your linux accounts can use these files the way you intend them to. Maybe you have to elaborate on  why this, in the current setup, is not a satisfactory solution. 

I don't know NTFS-3G so I can't tell if it's going to be any help. I expect not : unless you physically attach the windows disk to the linux server, you're dealing with CIFS (a windows share), not NTFS (a windows disk).

---

### Post by SeijiSensei on 2013-06-25
Have you looked into software like [Power Broker](http://download1.beyondtrust.com/Technical-Support/Downloads/PowerBroker-Identity-Services-Open-Edition/?Pass=True) (formerly likewise-open)  that let you join a Linux server to a Windows domain?  Maybe that would help.

Even though the download page says the release is for the 2.4/2.6 kernels, the Debian/Ubuntu version installed cleanly on this 13.04 machine with kernel 3.8.  I haven't tried it out, though.

---

