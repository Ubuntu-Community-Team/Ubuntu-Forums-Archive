---
title: "Multiple OS - formatting"
date: 2013-05-04
forum: Ubuntu, Linux and OS Chat
---

### Post by knowitnothing on 2013-05-04
Less than 6 months ago I was installing Panda Security. After installation I was asked to restart. I did, and at desktop, only the background image was there. No taskbar, no icons. nothing. It also disabled chrome. After a lot of googling I reset the computer to factory settings, and everything got fine.
Two weeks later I installed Ubuntu, recommended by a hacker book (yes I was researching on that stuff).
Also recommended by that book was Backtrack. I installed it, but now it is being very inconvenient having to wait for the pc to run grub so I can select Windows 7.
I want to format C: once again. Will it erase every OS and grub in this computer? (That is my objective).[FONT=arial]&#8203;[/FONT]






Thank you.

---

### Post by codingman on 2013-05-04
Yes. There are certain tools that will run for hours that will COMPLETELY remove everything on the disk. However, a quick format will take less time, but people hacking into your system can use certain tools to access old information.

---

### Post by knowitnothing on 2013-05-04
thank you. i will now format.

---

### Post by codingman on 2013-05-04
Your welcome! Remember to mark this thread as solved using the thread tools in the top right corner of the screen.

---

### Post by mastablasta on 2013-05-06
> **knowitnothing said:**
> I want to format C: once again. Will it erase every OS and grub in this computer? (That is my objective).[FONT=arial]&#8203;[/FONT]
.

if Ubutnu or backtrack is not on C:\ (and probably it is not unless you used wubi) then the formating of C:\ will not erase it. it will only erase windows (because you will only format that partition of the disk). to delete it all use the linux live disk and then use gparted. delete all of the partitions. now both OS will be removed.

btw you can set the grub (bootloader) to have windows first that way you do not have to select windows but it will boot windows by default. you can also reduce the selection time for example to one or two seconds. that way you can still select linux if you need and system won't linger for too long on grub.

otherwise grub can be accessed by holding left shift immediatelly after boot.

also as i know backtrack is now named differently - Kali Linux. it's based of debian (testing?) and as i know is usually ran in virtualbox. but feel free to install it.

---

