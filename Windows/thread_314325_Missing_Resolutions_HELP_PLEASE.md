---
title: "Missing Resolutions HELP PLEASE"
date: 2006-12-07
forum: Windows
---

### Post by Mutley01 on 2006-12-07
Hello,

I had a spill accident with my Laptop. After cleaning it it started normally, with only one problem: my normal 1280x800 resolution has been missing. All I have now is 800x600 and 1024x768. What to do to get it back? Inside, there doesn't seem to be any damage on the motherboard.

I have HP DV4170us laptop with Intel 915 GM Graphic Card. 

Any suggestions? I read something about Dapper Repositories here but I'm not an expert and I don't think it's for Windows anyway???:???: Even if it was, I don't know what to do...

When responding please explain all step by step so I know (amateur) how to folow. Many thanks in advance.

---

### Post by bscbrit on 2006-12-07
The first thing to do is to open a Terminal or command line. (Applications -> Accessories -> Terminal).  Then you are going to need use 'root' privileges to change the system configuration.  To do this you will need to log on as the first user that you created when you installed the software; many systems only have a single user and this is probably the user that you are logged onto now. Type the following on the command line:

sudo dpkg-reconfigure xserver-xorg

It will ask you for your password, give it your usual password (or the password for the first user installed if you have changed user to do this.)

It will lead you through a very basic screen reconfiguration wizard.  Accept defaults where you do not know the answer.  At one stage it will ask you what resolutions you want to use for your display.  Highlight the missing resolutions in turn and then press the 'Spacebar' to set a star next to the resolutions that you want.

When you have followed all the instructions and the reconfiguration has completed, I suggest that you log out and log back in again to restart the X server (that's the software that is driving your display).  You should now have all the resolutions that you selected available.

Good luck.

---

### Post by Mutley01 on 2006-12-07
I have go to Command Prompt

C:\Documents and settings\Mutley>sudo dpkg-reconfigure xserver-xorg

It says "sudo" is not recognized as an internal or external comand...

what am I doing wrong?

---

### Post by KiwiNZ on 2006-12-07
errr are you running Ubuntu or Windows?

---

### Post by Mutley01 on 2006-12-08
I'm running Windows XP Pro

---

### Post by KiwiNZ on 2006-12-08
HP have a very good restore facility on their Laptops that allow for a destructive or non destructive restore. In addition to the Windows roll back.
 
First up try Windows restore to a restore point before you incident.
 
If that doesnt work re install the graphics drivers. If you have the disks if not I would suggest you try a non destructive restore. This will restore your laptop but retain your data.

---

