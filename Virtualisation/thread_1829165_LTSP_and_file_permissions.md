---
title: "LTSP and file permissions"
date: 2011-08-20
forum: Virtualisation
---

### Post by BRRFOC on 2011-08-20
Running LTSP 10.10 on KVM, with ~/.profile permissions set umask 003, some applications (gedit, touch) will create files in data folders with 664 permissions, which is desired for shared folders. However, OpenOffice, Firefox, and saving Thunderbird attachments to shared folders results in file permissions set at 644. Have tried using chmod g+s for parent folders and this does not seem to affect the result. Also tried changing umask settings 003 in /opt/ltsp/i386/etc/profile, and OpenOffice saved files still save with permissions 644.

Any recommendations?

---

### Post by BRRFOC on 2011-08-21
Well, I don't know whether this is truly a solution since I have not completed testing but found this post which seemed to achieve the desired results, at least with OpenOffice:

[http://ubuntuforums.org/showthread.php?t=711066](http://ubuntuforums.org/showthread.php?t=711066)

---

