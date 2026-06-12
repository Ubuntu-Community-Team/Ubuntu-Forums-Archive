---
title: "Share and connect to external HD"
date: 2015-07-06
forum: Server Platforms
---

### Post by Steve_Cline on 2015-07-06
I have an external HD with NFTS file system connected to a desktop running 14.04.  I would like to share it within my home network to access files from other computers, both Ubuntu and Windows.  What is the best procedure for setting this up and what factors should I consider?

---

### Post by TheFu on 2015-07-06
Sharing with Windows usually means "samba" - install that - there are hundreds of "how-to" guides. The trick with NTFS is getting the mount permissions connect on the Linux side.  CIFS is the protocol.

Sharing over the internet is best done with sftp - install openssh-server and setup remote ssh access. You get sftp automatically. It is secure.  WinSCP is a windows client and every networked OS has a good sftp client available.  You can use sftp on the LAN if you like as well. It is much easier to setup than Samba almost always.

---

### Post by Steve_Cline on 2015-08-05
It has been a while since your reply.  I made a few failed attempts but was finally able to make some progress on this in between other projects.  Thanks for the guidance.

I have hit a wall though.  I followed the steps in this documentation: [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

I was able to successfully set up the "share" in the "smb.conf" file and it worked when accessing it with a Windows client.

Now I would like to do the same with an external hard drive.  I followed the procedures and put this text in the "smb.conf" file:

[extsmall]
    comment = Ubuntu File Server Share
    path = /media/steve/extsmall
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

When I try to access it from the Windows client I get: "You do not have permission to access \\MEDIA\extsmall.  Contact your network administrator to request access."

I have set permissions in nautilus to make sure they are the same for both "share" and "extsmall".

Any suggestions?

Thanks again.

---

### Post by TheFu on 2015-08-05
Check the permissions on /media/steve

---

### Post by Steve_Cline on 2015-08-06
That fixed it after a little trial and error.  It also fixed my problem with PLEX not recognizing the media on that HD.  Thanks for the help.

I have one last issue to resolve, if it is possible.  I have another 2TB HD that I would also like to serve in this manner.  When I set up the "extsmall" HD I reformatted it to Ext4 because it was empty anyway.  The larger HD is NFTS and I do not want to reformat it because there are a lot of files to move.  It will not allow me to change permissions even when I gain root access to nautilus.  Is this just a product of the file structure or can this on also be added to the server?

---

### Post by TheFu on 2015-08-06
It is a by-product of using NTFS.  The only way to control permissions for NTFS partitions is at mount time. After that, it is too late. Further, you don't get detailed control over the file/directory permissions. 1 setting for files. 1 setting for directories.  

It really will make your life easier if you can migrate to a POSIX standard file system (that means pretty much ANY file system that works with Linux/Unix permissions).

BTW - letting an automatic mount handle plex areas is a terrible idea.  I don't allow anything under /media - that area is where random stuff gets mounted - which is sorta dangerous.  Mount file systems where you want them - specifically - not where they are automatically placed.  Since you have to change the mount options anyway, this is the time to fix that too.

---

### Post by Steve_Cline on 2015-08-08
When you say, 

[COLOR=#000000]"BTW - letting an automatic mount handle plex areas is a terrible idea. I don't allow anything under /media - that area is where random stuff gets mounted - which is sorta dangerous. Mount file systems where you want them - specifically - not where they are automatically placed. Since you have to change the mount options anyway, this is the time to fix that too."[/COLOR]

I assume you are referring to the External HD that I have working.  If so, can you point me to a guide to work on this process?

---

### Post by TheFu on 2015-08-09
Google found this: [https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux](https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux) - seems overly complicated to me, but has some plex specific things. If you've already loaded the Plex DB with files in the current location, those will need to be cleaned up if the mount location is moved.  Basically, just rescan the library.  BTW, I've run plex for about 18 months and Xbmc for many years and worked as a Unix admin in the 1990s.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) is the ubuntu version. I strongly disagree with mounting anything under /media or using any GUI editor with sudo - that is dangerous. Always use **sudoedit** when you need to edit a file that your userid doesn't have write permissions for already. sudoedit is SAFE.  

You will need the uid/gid options on the NTFS mount to keep plex happy.  Add your userid to the plex group and make plex user and group be the group for the mount options.

It really is easier if you dump NTFS for ext4 or any other Linux file system. Then normal, expected, Unix permissions rule. No surprises.

OTOH, it is your system, not mine. Do what works best in your situation.

---

### Post by Morbius1 on 2015-08-09
> **TheFu said:**
> Google found this: [https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux](https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux) - seems overly complicated to me, but has some plex specific things. 
More of an FYI but that little HowTo suggests using the "permissions" option in fstab for the NTFS partition. What that does is bypass the normal NTFS mounting in Linux and allows setting ownership and permissions at the file level. If this is an NTFS partition in an all Linux system that's fine I suppose ( but you're making an NTFS partition act like an ext4 partition without any of ext4's benefits ). But if this is an NTFS partition in a dual boot with Windows then it's just a wee bit more complicated than this.

You will need to create what is basically a user mapping lookup table to let both OS's know that this user with this uid in Linux is the same as this user with this sid in WIndows otherwise any file added in Linux will appear as a foreign user in Windows and any file added in Windows will appear as root in Linux.

All in all it's a complicated convoluted mess and not something I personally would ever do again. Ever.

---

