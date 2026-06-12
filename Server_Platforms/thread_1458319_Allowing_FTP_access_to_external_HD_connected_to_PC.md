---
title: "Allowing FTP access to external HD connected to PC"
date: 2010-04-19
forum: Server Platforms
---

### Post by evanl81 on 2010-04-19
Hi,

Apologies if this has already been addressed. I searched but couldn't find an answer.

I have proftpd setup on my Aspire Revo (which I'm using as an HTPC) so that I can download files to my mac when I feel like watching in bed or whatever. I recently purchased a 1TB WD Elements to store my media. I have proftpd setup so that I can access every file on the computer. However, when I try to gain access to the Elements HD, I get an FTP error from Cyberduck that says:

/media/Elements: no such file or directory

Note that I have not formatted the drive or anything - just set it up straight out of the box. My media is loaded on to it, and XBMC reads the files fine. Is there a way I can enable the hard drive (or the OS) to share these files over FTP, or is this not possible?

I'm sort of a Linux dummy/noob, so simple explanations would be appreciated.

Thanks.

---

### Post by nexes128 on 2010-04-19
What version of ubuntu are you running?

Have you checked to make sure that /media/Elements exists, normally when externals get mounted its done by its id, unless you have manual specified it in the fstab (Have you? if so what does your fstab look like)

---

### Post by nexes128 on 2010-04-19
You may also want to look at the permissions on the mounted folder by doing "ls -la /media" and making sure the ftp user has read access at least

---

### Post by evanl81 on 2010-04-20
I'm running 9.10. The directory does exist - when I open the WD drive from the desktop, it's location is /media/Elements. When I access the FTP, this path exists, but when I try to open Elements I get the error messsage.

I tried the ls -la command for media/Elements. This is what I got:

user@HTPC:~$ ls -la /media/Elements
total 9
drwx------ 1 user user 4096 2010-04-19 13:30 .
drwxr-xr-x 4 root    root    4096 2010-04-19 20:21 ..
drwx------ 1 user user    0 2010-01-20 22:18 autorun
-rwxrwxrwx 1 user user   36 2002-10-16 22:56 autorun.inf
drwx------ 1 user user    0 2010-01-20 22:18 System Volume Information
drwx------ 1 user user    0 2010-04-19 13:39 Video

Not that the user in this example is not my ftp user. Does this mean that user has no permissions on the volume? If so, how do I add it?

I have not touched fstab.

---

