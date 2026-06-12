---
title: "setting up chrooted sftp user (and failing at it)"
date: 2012-02-27
forum: Server Platforms
---

### Post by P3t3r on 2012-02-27
I'm trying to give a user sftp access to only a single folder in the /var/www folder, sort of similar to public hosting.

I followed the guide on [http://shapeshed.com/chroot_sftp_users_on_ubuntu_intrepid/]("http://shapeshed.com/chroot_sftp_users_on_ubuntu_intrepid/") but it seems it doesn't work, or at least it's outdated. When the user tries to connect, he gets an error that SFTP doesn't work as no bash thing could be found.

Any clues what could be wrong? Chmod & chown are set correctly as in the link.

---

### Post by P3t3r on 2012-04-24
Two months and no reply... is there something wrong with my post? Should I add more detailed info (and which) or is this just a wrong forum or is it a stupid question alltogether?

---

### Post by matt_symes on 2012-04-24
Hi

The exact bash error message would help for a start, i'm sure. 

You can also bump once every 24 hours if you like. 2 months is a long time for a bump.

I may have a go at this myself. If i can get it working, i will report back. If not, then maybe some one else will see this and help you out.

Kind regards

---

### Post by P3t3r on 2012-04-24
> **matt_symes said:**
> Hi

The exact bash error message would help for a start, i'm sure. 

You can also bump once every 24 hours if you like. 2 months is a long time for a bump.

I may have a go at this myself. If i can get it working, i will report back. If not, then maybe some one else will see this and help you out.

Kind regards
The exact message would depend on the FTP client, no? I remember different FTP clients worded the error differently.

(but then again it's been 2 months)

In any case the problem seems to be that due to the chrooted environment, the ftp client can't get into bash anymore. But I have no idea how to deal with that.

---

### Post by kevinthecomputerguy on 2012-04-24
This may help

[http://woodel.com/domore/sftp/woodel_sftp.pdf](http://woodel.com/domore/sftp/woodel_sftp.pdf)

-KevinTheComputerGuy

---

