---
title: "Ubuntu - Apache2 - FTP - hosting web sites for people"
date: 2007-01-30
forum: Server Platforms
---

### Post by JimTDI on 2007-01-30
After running Ubuntu with Gnome for awhile (and LOVING it!!) - I've now also installed Ubuntu server on a test box, with the intention of replacing my old SuSE box - which now hosts a few web sites for friends and family, as well as an FTP server so users can update their web sites remotely.

I've figured out VSFTPD, and for the most part Apache2, (I'm running Apache 1 on the SuSE box so it's a little different the Ubuntu way...).

Anyways, obviously, I want my users to be able to update their web sites via FTP, so I'm wondering... do I want to have my users virtual host document root in Apache to be their /home/user directories (I'm worried about Spiders reading their shell history, etc from their home directories, although I can delete those files once I create the users since they're all remote) or... is it preferrable in Ubuntu Server to place each users web site in /var/www and then map their home directories to var/www/theirsite, and then CHROOTing them there, in VSFTPD??

Also - what permissions should I grant to each of their directories, so Apache2 can serve their web pages correctly?

If you have ideas, or experience with a setup like this, I would appreciate you sharing your experience!!

Thanks!

---

### Post by Brazen on 2007-01-30
I would suggest just installing some sort of hosting software, like zPanel.

---

### Post by JimTDI on 2007-01-30
> **Brazen said:**
> I would suggest just installing some sort of hosting software, like zPanel.

Thank you - I'll take a look at zPanel (I did a little already) but it needs MySQL and PHP, and I was not intending to install either (I do have PostgreSQL), but for now I don't have a need for PHP (maybe zPanel is enough of a need!)  ;-)

Appreciate your input!

---

### Post by JimTDI on 2007-01-31
Does anyone else have any ideas on this subject that might help me out?

Thank you!

---

