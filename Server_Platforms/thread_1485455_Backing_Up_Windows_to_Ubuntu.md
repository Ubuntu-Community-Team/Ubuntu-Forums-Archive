---
title: "Backing Up Windows to Ubuntu"
date: 2010-05-16
forum: Server Platforms
---

### Post by dadepfan on 2010-05-16
Hi everyone!

I have been hassling with this for several days now.  I have 64-bit Ubuntu Server 10.04 running on an Acer Aspire EasyStore H340.  I have windows 7 running on a 64-bit desktop pc and on a laptop.  I mainly wanted to use the Ubuntu server for a file server, so I installed Samba and created three shares.  These do show up in Windows explorer, and I can read and write to them.  My windows applications seem to be able to see the shares and open & save files.

My next step was to try and set up a backup of the Windows 7 pc to the Ubuntu server.  Windows integrated backup sees the shares and sub-directories within the shares, and the initial part of the backup seems to run OK, but when it tries to save an image of the 'C:" drive it works for a long time and then ends with an error (cannot complete backup).

So, I looked for some free backup programs to try, but these do not allow me to select the shares as a destination (invalid destination).  The dialogue sees the drives I have mapped the shares to in Windows, but does not show any sub-directories, and selecting the mapped drive letter does not take as a destination.  If I try to browse down through "Network" in the destination dialogue, it selects "Network," but does not expand it or accept it as a destination.

So, I partitioned, formatted as ext3, and mounted my 2nd 1TB SATA drive on the  server, and mounted it as "storage."  I set this up as share in Samba and gave everyone read-write access, but still no luck selecting it for a backup destination.  After some Googling, I downloaded and installed Ext2Fsd-0.48 (a windows 'driver' for Ext2/Ext3).  This installed correctly, but when I open the program, neither "Network," the shares, or the mapped drives show up anywhere.

Also, is there any problem with using the same user name on the Windows desktop and on the Ubuntu server?  On the network, aren't these treated as two different users, with the host name pre-pended??

I must be missing something - any suggestions??

Thanks,
Dave

---

### Post by BobVila on 2010-05-17
The Ext2Fsd isn't necessary for connecting to a samba share. I'd remove it and see if samba starts working as it was before.

Have you tried running the backup on either of the windows boxes and storing the resulting file on the local machine? If that succeeds, try copying the backup file to the Ubuntu server. If all that works, you can set up a pretty simple script to copy your local backup file to the server and schedule it in windows.

---

### Post by koenn on 2010-05-17
Windows can now also mount shares to a local folder (think: mount point) in stead of mapping them to drive letters or using unc paths. It's called a '(NTFS) symbolic link'. [http://en.wikipedia.org/wiki/NTFS_symbolic_link](http://en.wikipedia.org/wiki/NTFS_symbolic_link)

According to Microsoft, this is transparent to local apps, so any backup program on your windows machine should be able to backup to that mount point->to the share, without being aware of the SMB stuff underneath.

---

### Post by wkulecz on 2010-05-20
What version of Windows 7 do you have?

I think you need Professional or Ultimate for network based backups to work.

--wally.

---

