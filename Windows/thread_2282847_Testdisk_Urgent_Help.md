---
title: "Testdisk Urgent Help"
date: 2015-06-17
forum: Windows
---

### Post by AlJourgensen on 2015-06-17
[COLOR=#323232][FONT=verdana]Hello community[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]i need urgent help here, i have a usb sony vaio 2.0, 2TB exfat, and i don´t know why, it´s been a headache to solve this, because all information regarding that kind of error, the CHS and LBA conflict, or is a mess to understand, or is incomplete, and i need someone that can tell me step by step please, how can i solve this problem to get my pen back[/FONT][/COLOR]


[COLOR=#323232][FONT=verdana]i have "None" partition table type has been detected[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]i click on "Intel" option[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]"analyse"[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]and get the[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]Warning: Bad starting head (CHS and LBA don't match)[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]Only one partition must be bootable[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]Space conflict between the following two partitions[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]4* Xenix Bad Block[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]1* Xenix bad block[/FONT][/COLOR]


[COLOR=#323232][FONT=verdana]i choose the intel option, and the result was the first photo[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]Now, i have made another analysis, and the result of this one, was different from that first photo (see 2nd photo attached).[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]Made another one and now i have only 2 options, and one of them is (create partition pressing in "A"), but i don´t know what to choose from here, because it asks me for the "Geometry, Head, Type, Sectors", and i don´t know nothing about this, i read all the articles related to this, but none has been conclusive, or none says me what to put under this configuration.[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]as a last resort i can do another analysis, and see where that log file goes and posted here, if that photo, and my description doesn't help you.[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]Thank you very much in advance, and if you can tell me something, that would be a great help.



[/FONT][/COLOR]

---

### Post by slickymaster on 2015-06-17
Hi AlJourgensen, welcome to the forums.

I'm moving your thread to the **Hardware** sub-forum, which is the proper venue for it and where, luckily, you'll have a better chances to get help for your problem.

---

### Post by AlJourgensen on 2015-06-17
Thank you very much my friend and sorry for my mistake

---

### Post by dino99 on 2015-06-17
some explanations and help: [http://superuser.com/questions/872318/corrupted-hdd-lost-partitions-shrunken-drive-damaged-boot-sectors-chs-and-lb](http://superuser.com/questions/872318/corrupted-hdd-lost-partitions-shrunken-drive-damaged-boot-sectors-chs-and-lb)

---

### Post by AlJourgensen on 2015-06-17
hello my friend and thank you for your answer 

i´m newbie with this, and i don´t know how to work in linux environment, i already tried but i don´t understand anything about it

[COLOR=#323232][FONT=verdana]the thing is that when i plug in the pen, it is recognized has a exFAT primary partition, but when i try to format, windows doesn´t let me, i tried all kind of programs to format the pen, but i didn't have success with no one.[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]so i tried testdisk, and i´m stuck in this problem, because i´m newbie with the program, and i already tried to look for an anwser, but no one reply to those threads that i found.[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]that´s why i need help

[/FONT][/COLOR][COLOR=#323232][FONT=verdana]Also when i try verifying the disk with the tool from windows, from bad sectors or corrupted, it says that have none and everything is ok[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]i just can´t understand what is happening[/FONT][/COLOR]

---

### Post by howefield on 2015-06-17
Are you using Ubuntu ?

---

### Post by AlJourgensen on 2015-06-17
no, i don´t understand the program my friend

---

### Post by slickymaster on 2015-06-17
I think what howefield asked is with which operating system are you running TestDisk?

---

### Post by AlJourgensen on 2015-06-17
thank you for your answer, with win 8.1 my friend

---

### Post by slickymaster on 2015-06-17
Have a look at this tutorial: [http://selfsolve.net/software/testdisk_pbr.html](http://selfsolve.net/software/testdisk_pbr.html)

---

### Post by AlJourgensen on 2015-06-17
i already read this post my friend thank you again, but the thing is, that those options don´t show up, the only options that are shown are "Create partition" and another one that i cannot recall wright now.
When i click create partition, appears some things that i don´t understand like "geometry", "Head", "Type", "Sectors", and here is where i get stuck, because i don´t know the wright values to input, and i can´t pass from this menu.

here are some screenshots of what appears when i press to create a partition

---

### Post by AlJourgensen on 2015-06-18
i don´t know if this helps, but first i was trying to format the pen to NTFS system, then everything i posted start happening 


thank you for your attention.

---

