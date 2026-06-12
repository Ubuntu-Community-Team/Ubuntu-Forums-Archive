---
title: "How to create live CD for browing protected material"
date: 2011-02-16
forum: Security
---

### Post by sundaune on 2011-02-16
Hello, fare easy on a newcomer please :)

I have a project where I have some material (pictures, movie clips etc.) that I want to distribute on CDs. The receiving part should be able to boot this CD and browse the material, preferably through some kiosk mode locked-down Firefox. My challenge is that nobody should be able to copy the material that is on the CD.

I have thought out the following:

- Bootable CD with internet, USB and harddrive support disabled. 
- XAMPP runs local web server, presents material on local webpage (localhost)

Now, nobody should be able to just pop the CD into another machine allready running and browse it. So I want the file system to be encrypted, but of course automagically unencrypted upon booting.

Any ideas how this can be accomplished?

Hopeful regards,
Håkon M.E. Sundaune
Oslo, Norway

---

### Post by psrdotcom on 2011-09-15
Please see this thread. It may help you

[http://ubuntuforums.org/showthread.php?t=1765472&highlight=firefox+kiosk](http://ubuntuforums.org/showthread.php?t=1765472&highlight=firefox+kiosk)

---

