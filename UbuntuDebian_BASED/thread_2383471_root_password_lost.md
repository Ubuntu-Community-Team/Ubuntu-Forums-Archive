---
title: "root password lost"
date: 2018-01-25
forum: Ubuntu/Debian BASED
---

### Post by christon74 on 2018-01-25
Good evening fellow Ubunters):P (time here is 6:38 pm). I have successfully installed Zorin (which I have heard is not an official flavour of Ubuntu) alongside Windows 7. The problem is I really do not remember being asked to set a password during the install process. I know this reads crazy, but I think that Zorin created a password of its own and is now asking me to simply guess it. I have tried all the passwords I am currently using on different web sites, and each time, the authentication failed. I have tried hard to reset a new password, and this has failed too. I would be extremely sorry to have no other option left than deleting the partition and have to re-charge Windows 7 (I have already made a back-up to a high capacity USB disk, using Macrium Reflect). 
Is there a way to "blanck" or erase a partition WITHOUT deleting it? If yes, then I could install Ubuntu, or any other Linux destro.

Hardware: Fujistu-Siemens Esprimo 5731 E Star 5.0
Motherboard:  Fujitsu D 3024 -A1
Processor: dual core Intel E 7500  (2933 Mhz)
BIOS: Phoenix
Graphics board: Intel Q43/Q45

A zillion thanks in advance to anybody for any easy tip that saves me from deleting the partition and doing a fresh install.

---

### Post by wildmanne39 on 2018-01-25
*Thread moved to **Ubuntu/Debian BASED, a more appropriate forum**.*

---

### Post by yetimon_64 on 2018-01-26
Firstly I will note I do not use, nor ever have used, Zorin but have just done a bit of searching on Google and reading of Zorin forums/questions etc after reading this thread.

As Zorin is based on Ubuntu I would suspect if you did not set a root password on installation that the root account will be locked, just like in Ubuntu. That is there is NO root password to be used.

Did you set a password for your user account during installation?

If you did set a user password then to do any administrative tasks or commands you would need to use sudo with any root commands and your user password just like you would do in Ubuntu.

I have read on some Zorin forums the recommendation not to set a root password and to use sudo for root privileges. If you really wish to set a root password, or for that matter relock the root account after doing so and changing your mind, read the first green link in my signature and you will find the info you want there. 

This site will generally not give instructions for such actions and no support would likely be possible here if you run into troubles from doing so. As an Ubuntu support site this forum follows the Canonical security policy/proceedure of using a locked root account.

Read the RootSudo documentation link in my sig fully and carefully and it may be of help to you. Regards, yeti.

---

### Post by christon74 on 2018-01-26
Good evening Yetimon:)
 No, no, no, I did not set any password, I have absolutely no recollection of ever setting a password. But, each time I try downloading any software, or try any command on a terminal window, I get a password prompt.  I am no psychic and I cannot guess the password which Zorin has set of its own accord.  The "Root shell" method simply does not work since "The system does not have  bin/bash"

Let me just copy/paste what I have put to "Ask-Ubuntu" :
24th Jan 2018_ 8:10 pm_ I have just tried this method: 1_Reboot your system 2- Highlight your image and press E to edit 3- Find the line with "linux" and append rw init =/bin/bash at the end of that line. 4-Press Ctrl X to boot Type in passwd Set your passwd and restart your PC.
  Now here are a few lines on the screen which caught my attention: "bash: cannot set terminal process group (-1) inappropriate ioctl for d"
"bash: no job control in this shell"
"Kernel panic! _ not synching: attempted to kill init!"

---

### Post by oldos2er on 2018-01-26
Why not use [Zorin's forums]("https://zoringroup.com/forum/viewforum.php?f=3")?

---

### Post by yetimon_64 on 2018-01-26
> **oldos2er said:**
> Why not use [Zorin's forums]("https://zoringroup.com/forum/viewforum.php?f=3")?

@ OP, my response was a bit a of a "stab in the dark" not having used Zorin myself.  oldos2er's reply may be a better option for you in this case. You are more likely to find your answers on a specialist site for Zorin. 

Good luck with your problem, regards, yeti.

---

### Post by christon74 on 2018-01-28
Good morning Oldos and Yetimon . Yes, I am subcribed to Zorin forums.  I have already received answers from  Swarfendor437 who seems to be the chief moderator. He has asked me if I installed Zorin with "autologin" (I do not know what that is). Anyway, at the moment, I am still going round in circles and I fear the only solution in sight is completely erasing the HD, do a fresh install of Windows 7 and install another Ubuntu system, but not Zorin:!:

---

### Post by oldos2er on 2018-01-28
Autologin allows your user to login automatically without having to type a password to do so. If you're positive you didn't set a user password during installation, it could mean there's a bug in the Zorin installer; might be why the mod on their forums wanted to know.

---

### Post by christon74 on 2018-01-30
5 days! During 5 days, I have unsuccessfully tried to solve the problem. I have taken down the password on a sheet of paper, prior to installing Zorin. I have tried installing nearly all the existing linux distros and I am still stuck with this unsolvable authentication problem. Swarfendor (Zorin forum) has tried as hard he could to help me, to no avail. I have tried installing Ubuntu (and other distros, like I have said) from USB sticks and from DVDs. Swarfendor says there might be something amiss with my partitions. I posted a screenshot of my disks. But what could it be? I did a checkdisk this morning and everything is OK, disks are clean. I have even tried tonight, to install Ubuntu using Oracle virtual machine. Same problem. My password is still not recognized. I have tried every trick or manipulation used to reset my password, and failed every time.

---

### Post by yancek on 2018-01-30
Zorin, like the other major Ubuntu distributions, does not use root by default and does absolutely require you to create at least one user with a password during the installation.  That user has administrative/root privileges when using sudo.  Neither Zorin, Ubuntu or any of it's derivatives has a 'secret' password that someone has to guess.  The only password is the one created by the person installing the system.  This is my experience having installed Zorin (multiple times) and used it.

---

### Post by christon74 on 2018-01-31
Good morning Yancek:-|_ Have you read my posts, do you really understand what I am saying? During the install, I DID set a password at some point, I confirmed it, I put it down on a sheet of paper (just in case). And after rebooting, the moment I tried downloading thunderbird (or any other software), I got a password prompt, I typed the selfsame password I had set, and the authentication failed ](*,). So, please try explaining to me like I was a 6 years old, why the authentication systematically fails?#-o By the way, I have uninstalled Zorin and have installed Ubuntu 16.04 instead, and I still have this authentication problem. Oh! And I have also tried the "rw init=/bin/bash" a thousand times at least. Please scroll up a bit and read what I posted 4 days ago. Have a good day.

---

### Post by lisati on 2018-01-31
Please forgive me if I'm stating the obvious, but (a) when using "sudo" the password does not show on the screen when you're typing it, and (b) passwords are case sensitive, for example, *password* is interpreted differently to *PASSWORD*

---

### Post by christon74 on 2018-01-31
Good morning Yancek. I do not know why the quick reply I posted a few minutes has vanished into thin air. But have you carefully read the message I posted 9 hours ago?
 By the way, I have completely uninstalled Zorin and put Ubuntu 16.04 instead. During this Ubuntu install yesterday night, I DID set a password and prior to the install, I took care of taking it down on a sheet of paper. The insall completed without any problem. Now, after rebooting and loading Ubuntu, the first time I tried downloading Thunderbird (or any other software) from the Ubuntu software center, I got a password prompt, type the password I had set and got the same message: authentication failure.
OK. reboot_ recovery mode_ edit_  append the line with "rw init=/bin/bash" CtrlX log on to Ubuntu, Software center, insall thunderbird_ password prompt
"shortcn" (my password) _ authentication failed
when I tried editing, I got these lines:
bash: cannot set terminal process group (-1)
Inappropriate ioctl for d
bash: no job control in this shell

Apologies accepted unreservedly. I'm sorry if my messages are slightly terse, but I feel very very frustrated. Yes, I know passwords are case sensitive, and that I why I always use the lower case when I set up a Ubuntu password.
Don't know how relevant this can be, but on rebooting I sometimes get this § on the display:

[Minimal BASH line editing is supported. For the first word, TAB lists possible command completions. Anywhere else, TAB lists the possible completions of a  device/filename.]
grub>

Anyway, thanks again for all help and advice. I wonder if one day I will be able to make full use of Ubuntu 16.04 like I once was able to, not so long ago.

---

### Post by mc4man on 2018-01-31
Try a new install of Ubuntu, during the install set your password to 1
Then see what happens after install with something like sudo apt update, when prompted for password it's just 1 (so no need to write down, remember  or anything really ..

---

### Post by christon74 on 2018-02-01
Good evenu mc4man:)
This evening I completely wiped E (partition), I formatted it, using MiniTool Partition wizard. I then reinsalled Ubuntu using Oracle virtual machine. Typed 1 as a password, just like you have suggested. After completion of the install, I rebooted, tried again to download Thunderbird, got the passwd prompt and guess what? Authentication failed again. :confused:

I believe somebody put a spell on my PC! An hour ago, I logged on to Ubuntu (recovery mode), scrolled to the prompt shell:
Give root password for maintenance
(or type control-D to continue):
I typed my password
root@christophe-destop:~#  (????????) authentication success!
passwd
Enter new UNIX password: *******
Retype new UNIX password: *******
password updated successfully
root@christophe-desktop:~# sync
root@christophe-desktop~# reboot -f

I have not yet tried again to log back on to Ubuntu. 
To be continued......

No, no, no. Despite the "password updated successfully", I still cannot authenticate on a terminal window. If I log off and try to log back on, my password is still not recognized.
At some point Swarfendor437 hinted at my partitions, saying that something might be wrong with them. How should I know?
Ubuntu should be located on volume E. I have wiped the partition (MiniTool partition wizard), I have formatted it. I have deleted it. Ubuntu is still present. 
I have got to the root (more than once, recovery mode) I have changed the password successfully. Reboot, log back on to ubuntu_ open a terminal window type sudo su. Authentication still fails again, and again, and again. Never before have I so wistfully wished I had a light bulb moment.....
I have an operating system of which I cannot make full use, I cannot uninstall it. I am glad I have kept Windows 7.
It's either me or my PC who need a head shrinker. 
Now, how can you pinpoint the linux files on your hard disk? How do you know which partition is allocated to Ubuntu?  I'm asking because, if I'm not mistaken, Windows and Linux will not share the same partition, or do they? Like I've said, on my system, "E" was the partition allocated to Ubuntu. Deleting the volume, wiping it, formatting it, none of these operations have suppressed it. It's still present, and I can log on to it. But still cannot authenticate!!!!!!!!!

---

### Post by yetimon_64 on 2018-02-02
> **christon74 said:**
> Good evenu mc4man:)
This evening I completely wiped **E (partition)**, I formatted it, using MiniTool Partition wizard. I then reinsalled Ubuntu using Oracle virtual machine....Just one more "stab in the dark" style question from me, going on that that wording (bolded) and the tone of this thread in general regarding authentication. [B]

Question:[/B]  Are you trying to install Zorin or Ubuntu (Linux distros) onto a windows formatted partition? If so, I would point out windows partitions do NOT support linux ownership/permissions requirements and as such authentication will fail consistently.

Honestly, I don't know if it is even possible to install a linux disto onto a windows partition (I've never tried such an action), but if it is possible then I would expect any authentication attempts to fail as a result of the lack of support for linux permissions on windows formatted partitions (NTFS or FAT). Ensure when you install that you format the linux partitions as **ext4** (If you are not doing so already) and try again.

>  It's either me or my PC who need a head shrinker. 
If I am off the mark with this question, please consider this suggestion as a "sanity check" style quesion/suggestion :). Cheers, yeti.

---

### Post by christon74 on 2018-02-02
Aaaaah. OK. Indeed, yes, E is FAT 32 formatted. I thought that was a possible format for Linux systems. Thanks, I think I will try again, this time formatting Linux partitions as ext4 and see if I the authentication is successful this time. 
Thanks again. ;)

Good, logging on to Zorin works on an Oracle VM. That's one thing. Now trying to install it with Pendrive Linux does not work either. When I press F12, choose the USB drive, my PC beeps twice, I cannot choose the install, with only the trial version in surbrilliance, and the next second I get a black screen, nothing else happening.

Question: I have bout this Fujitsu-Siemens Esperio second hand at a cheap price from "PlusdePC.com" with Windows 7 already installed on it. Do sometimes manufacturers or vendors "do something" which precludes the installation of other OS?

---

### Post by christon74 on 2018-02-03
Hello again Yetimon and Mc4man:) 
I have here a small laptop (hp nc 4200) that runs Ubuntu. Is it possible to export the whole system, first copy it to a large capacity USB stick and then write it to my Fujistsu Esprimo desktop? On second thoughts, I'd rather not. I have read a page (Ask) and the whole procedure looks far too complicated for a dummy like misself.

---

### Post by christon74 on 2018-02-04
Good evening Yancek, Oldos, Yetimon....
No Linux distribution will ever install on this PC I'm afraid. I have even tried Yumi (pendrive) and what happens is when I choose the linux distribution the PC gives a loud beep (well,it gives just one beep, yes) and no matter which option I choose (try, install, etc..) I get a perfectly black screen. Now I have an external hard disk which I use only for storing music, videos and other documents. One partition is free space. Could I use this Western Digital (My Book) and install a linux distribution to it? What I fear though, is that this might completely mess up all the data already saved to this disk? And what is more, Swarfendor says external drive are not really linux friendly. Oh, and there is something else I do not know about this external hdd: does it have MBR?
Any ideas about a Linux install on external hard disks?

05th Feb 2018
Last night I tried again to install Zorin, Peppermint, Ubuntu and always got the same black screen after pressing Enter.  I searched the web for any answers and I found a page (JournalXtra) and this caught my attention: 

The Ubuntu graphical installer is poor at detecting and setting up  old graphics cards and monitors. It is a strange and frustrating problem  because once Ubuntu is installed it detects and configures them  effortlessly. The installation issue shows itself through symptoms which  include any of the following:
 
[LIST=1]
[*]A perpetually blank screen that prevents any set-up questions from being answered 
[*]A continuously moving animated gif that suggests &#8220;*something amazing is about to happen*&#8220;; which it is &#8211; the computer is about to get a boot from its frustrated user! 
[*]An error message that reads 1: "vesamenu C32:attempted DOS system call 2: boot
   vesamenu.c32: attempted DOS system call boot:

  [TABLE="class: crayon-table"]
[TR="class: crayon-row"]
[TD="class: crayon-nums"]


[/TD]
[TD="class: crayon-code"][/TD]
[/TR]
[/TABLE] 
[/LIST]

I get 1, yes, and then it's either a blue screen with a "No signal" square randomly wandering the monitor, or a black screen. But 3, no, never. I never saw this message on my screen.

Oh dear, oh dear! Finally installed Ubuntu 16.04 successfully, password authentication OK. It was the now famous trick with F6 and select "nomodeset". Now, there is another problem. I thought I had chosen the right partition to install Ubuntu, but I boobed and completely wiped out Windows 7! I want to reinstall it. And that is quite another matter.  Anyway, I think I am marking this thread as "Solved". Again, thank you all so very much guys, for all the time and trouble.=d>

---

