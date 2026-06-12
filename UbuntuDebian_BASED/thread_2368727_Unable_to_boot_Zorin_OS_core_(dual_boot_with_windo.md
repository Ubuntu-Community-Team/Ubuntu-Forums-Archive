---
title: "Unable to boot Zorin OS core (dual boot with windows 10)"
date: 2017-08-14
forum: Ubuntu/Debian BASED
---

### Post by manmm on 2017-08-14
Hi, I have installed Linux before without problems but this is the first time I do it with dual boot. 
I installed Zorin OS in a new partition succesfully, Windows 10 is in the bigger partition and I can access W10.

[B]Problems I have: 

[/B]
[LIST]
[*]Zorin OS partition doesnt appear neither in the bios boot list or the windows default booter.
[*]Grub doesnt start when initiating, neither shift, space or escape works. It goes straight to windows 10 unless I press F12 to start the default booter.
[/LIST]
     
[B]Things I have done so far:

[/B]
[LIST]
[*]Reinstalled Zorin OS once.
[*]I went to Ubuntu live session("[COLOR=#111111][FONT=Ubuntu]Try Ubuntu option" where you install it) and[/FONT][/COLOR] installed Boot-repair to fix Grub with "[COLOR=#111111][FONT=Ubuntu]Recommended Repair". [/FONT][/COLOR]
[*][COLOR=#111111][FONT=Ubuntu]I also used the command "[/FONT][/COLOR][COLOR=#000000][FONT=Arial]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi" on windows as it was recommended by the text file of boot-repair. It said that it was run succesfully but it didnt fix it[/FONT][/COLOR].
[/LIST]



[B]Posts I have used:
[/B]
[https://askubuntu.com/questions/327676/dual-boot-menu-with-ubuntu-and-windows-8-not-showing-up](https://askubuntu.com/questions/327676/dual-boot-menu-with-ubuntu-and-windows-8-not-showing-up)
[https://askubuntu.com/questions/256879/dual-boot-menu-not-showing-after-installation-of-ubuntu-12-04](https://askubuntu.com/questions/256879/dual-boot-menu-not-showing-after-installation-of-ubuntu-12-04)
[https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time](https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time)

[B]None of the above posts solved my problems.
[/B]                                        
You can see the report of boot-repair here: [https://drive.google.com/file/d/0B7rqSksSsvDBM09xWVZxd1pxalE/](https://drive.google.com/file/d/0B7rqSksSsvDBM09xWVZxd1pxalE/)

Thanks for your help.

---

### Post by manmm on 2017-08-14
I fixed it with [https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

Close the thread.

---

### Post by vasa1 on 2017-08-14
Glad you got it sorted and thanks for marking the thread [SOLVED]. We don't close threads here unless something goes wrong or the thread is inactive for more than a year in which case it is automatically closed.

---

