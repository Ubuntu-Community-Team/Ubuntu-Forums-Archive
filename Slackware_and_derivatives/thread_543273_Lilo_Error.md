---
title: "Lilo Error"
date: 2007-09-04
forum: Slackware and derivatives
---

### Post by ry4n on 2007-09-04
Hello, I have an old laptop and i installed slackware 12 on it today. But when i got to installing LILO on it, it gave me this error. I treid to install it on the MBR but i guess not luck right? what should i do. This laptop does not have a floppy and it can not boot from USB. So i think i need to edit the lilo.conf but how? what should i do? 



"sorry, but the install lilo has retuned an error, so lilo has not been installed. you'll have to use a boot disk to start you machine instead. it is still posible to get illo working by editing the /etc/lilo.conf and reinstalling lilo manually. see lilo man page and documentaion in /user/doc/lilo/ for help. "

---

### Post by ry4n on 2007-09-05
is there no one that can help?

I thought that this would be an easy for you slack guru's 

I hope that someone can help me becaues i can't even boot my laptop unless someone helps me. 

:confused::confused::confused::confused:

---

### Post by Bachstelze on 2007-09-05
Is it Slackware-only or a multi-boot ?

---

### Post by ry4n on 2007-09-05
just slack, 


it says that it can't install on the MBR? who knows (i know that i don't)

I can install vector (which has LILO) but slack is having problems with the MBR

---

### Post by Bachstelze on 2007-09-05
Can't help you much, I'm afraid, I always install GRUB on my Slacks. Maybe try doing that ?

---

### Post by ry4n on 2007-09-05
could i use the ubuntu alt cd on that?

---

### Post by Bachstelze on 2007-09-05
GRUB is in Slack's /extra packages, or you can use your Ubuntu Live CD. I guess it's possible with an Alt CD too, but I don't know how.

---

### Post by ry4n on 2007-09-05
ok, well thank you anyway.

---

### Post by saulgoode on 2007-09-06
It is possible that your laptop has some system utility software installed on the harddrive which is write-protected.

Have you tried installing LILO to the partition rather than the MBR? In 'lilo.conf' you would need to change the line

***boot=/dev/hda***

to 

***boot=/dev/hda1***

If that does not work, perhaps you could provide some more information about your laptop.

---

### Post by ry4n on 2007-09-06
i had windows 2000 on it for a while and that is when the laptop would not let me put slack on it. So i am sure that is what is probaly write protected.

But now the laptop won't let me put windows nor slack on it. 
so i put Vector on it instead and it works fine.

---

### Post by wilsonsamm on 2007-09-23
Salck has some problems with installing the bootloader.
See my observations at this thread for more info
[http://www.linuxquestions.org/questions/showthread.php?t=473682&highlight=lilo+slack](http://www.linuxquestions.org/questions/showthread.php?t=473682&highlight=lilo+slack)

---

