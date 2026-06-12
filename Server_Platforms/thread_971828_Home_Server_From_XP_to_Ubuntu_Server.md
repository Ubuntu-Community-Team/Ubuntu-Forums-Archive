---
title: "Home Server: From XP to Ubuntu Server"
date: 2008-11-05
forum: Server Platforms
---

### Post by jason442 on 2008-11-05
Hi all,

I want to migrate from XP to ubuntu on my home server. I've installed ubuntu on a test machine to learn and make sure I can get everything going. One area that I am confused on is file systems. I tried to setup file sharing on my test machine - trying to share a NTFS drive with samaba. I am using webmin to configure samba and it only allows me to share directories in the linux file system.

My current server is as follows: (not the test machine)
OS: Windows XP
HD 1: 500 gb - OS/misc
HD 2: 750 gb - shared drive - music, pics, software, etc etc
HD 3: 750 gb - backup

If I want to migrate to ubuntu, does this mean I have to convert all my Hard drives from NTFS to ext3?

my clients are all windows based PCs

thanks
Jason

---

### Post by HermanAB on 2008-11-05
Samba can share any kind of file system.

Read the Official Howto: [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by lykwydchykyn on 2008-11-05
Ubuntu can handle NTFS, though ideally you'd want to use something like ext3.  If you have the space to juggle around your files so that you can reformat, I'd recommend it.  If not, you can still operate, though you may have some tricky issues with the way permissions are handled and so forth.

---

### Post by jason442 on 2008-11-05
Thanks for the responses.

So if convert to ext3, will my windows machines be able access the ext3 shares?

---

### Post by lykwydchykyn on 2008-11-05
Yes; once they're shared from a server, the local filesystem is (mostly) irrelevant.  The remote machines don't have to know or care what the actual filesystem is.

---

### Post by jason442 on 2008-11-05
Sweet, thanks. Bye Bye Windows!

---

