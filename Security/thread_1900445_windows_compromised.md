---
title: "windows compromised"
date: 2011-12-26
forum: Security
---

### Post by Max_Max on 2011-12-26
I am planing to use the xubuntu desktop-CD to scan my old windows based hard disk content for malware and create an iso image of it.

In the general forum I've been told that there are siutable Linux programs to do so. Is that even possible? - Scanning a windows system with a Linux Anti-Malware program. If thats so what pgrogams could  I use?

Dounload links would be great! :) 

Thanks for the help, and excuse my lack of knowledge.

---

### Post by BC59 on 2011-12-26
The link is about to clean a Windows machine through an Ubuntu live CD but you can improvise:
[http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/](http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/)

---

### Post by Max_Max on 2011-12-27
Hi,i downloaded avast to a flash drive. What do i Have to type into the terminal to install it from there? 

(In the how to geek tutorial they only exlplain how its done from the cd download folder)   

Flash drive runs under sdb. I typed in dev/sdb1 to see the content respectively the name of the avast file but it says: "no  permission" Proberbly completly wrong anyway...


Thanks again, for the help.

---

### Post by routed on 2011-12-27
You can scan they filesystem, but I don't think it will catch stuff in the windows registry. The /dev/sdb1 is more of a pseudo file. When the USB is mounted it will be under /media.

---

### Post by jramshu on 2011-12-27
Why not just run Malwarebytes in Windows, it's free and effective. You can also run it from a usb.

---

### Post by Ms. Daisy on 2011-12-27
A very similar question was posed in another thread, here was a good answer:
[http://ubuntuforums.org/showpost.php?p=11559566&postcount=22](http://ubuntuforums.org/showpost.php?p=11559566&postcount=22)

---

### Post by Max_Max on 2011-12-28
> **jramshu said:**
> Why not just run Malwarebytes in Windows, it's free and effective. You can also run it from a usb.

Unfortunately i can't boot from my hard disk. Windows system data is corrupted.

> **Ms. Daisy said:**
> A very similar question was posed in another thread, here was a good answer:
[http://ubuntuforums.org/showpost.php?p=11559566&postcount=22](http://ubuntuforums.org/showpost.php?p=11559566&postcount=22)

I already gave kaspersky a try. -works REALLY slow (my old hardware i guess). But nice one Daisy.

I 'll stick to xubuntu for know...

---

