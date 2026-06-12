---
title: "mkisofs problems??"
date: 2011-04-25
forum: Server Platforms
---

### Post by lazerz on 2011-04-25
Im using mkisofs to make the final iso image of my ubuntu em using this guide as an help and em on the last step
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

if i don't use (.) at the end of stmnt i get 
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Missing pathspec.
Usage: genisoimage [options] -o file directory ...


if i do then
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Uh oh, I cant find the boot image 'boot/grub/stage2_eltorito' 

I don't know what to do? im already behind schedule no-one is really helping me over here...please let me know how can i work around this ....

---

### Post by matt_symes on 2011-04-25
Hi

Have a look at remastersys instead. Although i have not used it, i believe it allows you to create an installable image from your hard drive.

Kind regards

---

### Post by schily on 2011-04-29
> **lazerz said:**
> Im using mkisofs to make the final iso image of my ubuntu em using this guide as an help and em on the last step
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

if i don't use (.) at the end of stmnt i get 
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Missing pathspec.
Usage: genisoimage [options] -o file directory ...

if i do then
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Uh oh, I cant find the boot image 'boot/grub/stage2_eltorito' 

I don't know what to do? im already behind schedule no-one is really helping me over here...please let me know how can i work around this ....

Please note that genisoimage is an unmaintained and buggy variant made from a 7 year old original mkisofs.

Also note, that the  instructions you are following may be wrong.

I would guess that reading the  recent man page:

[http://cdrecord.berlios.de/private/man/cdrecord/mkisofs.8.html](http://cdrecord.berlios.de/private/man/cdrecord/mkisofs.8.html)

may help you with your problems. 

It may also help to install recent original software. For a binary package look e.g. for the packages from Brandon Snider as the error messages from mkisofs of course have been enhanced over the past 7 years...

---

