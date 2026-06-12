---
title: "Dual boot Ubuntu Studio 10.10 / 11.04 won't boot"
date: 2011-03-12
forum: Ubuntu Studio
---

### Post by Chtfn on 2011-03-12
Hi there. I wanted to help out reporting bugs with an Ubuntu alpha for the first time, so I installed Ubuntu Studio 11.04 Alpha 3 on the side of Ubuntu Studio 10.10. But now, none of them will boot. I'm on a Dell Studio Hybrid. Here is what happens with each choice I chose in Grub's list :

[B]2.6.38-5-generic (that's alpha 3)
[/B]
 
 Purple screen, then nothing (screen goes to sleep). I can turn the computer off by pushing the hardware button.
 With recovery mode : a stream of commands, then nothing (screen goes to sleep). Pushing the hardware button doesn't turn the computer off, but the combination « Alt Gr + Syst + B » reboots.  
 


All the rest are different versions of the kerne**l in 10.10 :**

 **2.6.35-27-generic (on /dev/sda1) :**
 

 Normal mode : stays on blinking underscore.
 

 With recovery mode : gets to the recovery mode menu.
 
[LIST]
[*]If I chose « resume normal     boot », it asks my login and password, says « welcome to     Ubuntu », tells me that there's 14 security updates. Stays in     command lines. After updating those, when I boot this version back     to the normal mode, it takes me to the login screen, with oldschool     appearance, and tells me that the gnome energy management default     settings weren't installed well, and that I should contact my admin.     Loging in always takes me back to the same login screen after a few     seconds.
[*]If I chose « dpkg » to     fix broken packages, it doesn't find any.
[*]If I chose to update GRUB, nothing     happens, back to menu.
[*]If I chose « clean »     to free some space, it doesn't do anything, same menu.
[*]If I chose « failsafeX »,     it doesn't boot, it takes me back to the recovery mode menu.
[/LIST]
 

 **2.6.35-25-generic (on /dev/sda1) :**
 

 Ubuntu studio loading screen, then empty black screen where I can write stuff, but no effect.
 Recovery mode : usual menu like above, no effect.
 

 **2.6.35-22-generic (on /dev/sda1) :**
 

 Stops booting with this :
 

 ```
Fsck de util-linux-ng 2.17.2
 /dev/sda1 : propre, 258834/8814592 fichiers, 34602528/35239975 blocs
 * Sarting AppArmor profiles                Skipping profile in /etc/apparmor.d/disable : usr.bin.firefox
                         [ OK ]
 * Setting sensors limits            [ OK ]
 Starting distributed audio encoder : distmp3host
```
 



 What should I do ? I would like to report this as a bug, but I don't know how, because il doesn't seem possible to report a bug without being in a session! How can I report a boot bug??

---

### Post by West201 on 2011-03-14
I have to the same problem. I just upgraded to 11.04 an hour ago, and I can't even start.. It stops where it displays all the content Ubuntu is loading.. Please Help

---

### Post by amantonas on 2011-03-19
Same thing happened to me :/.

---

### Post by Pablo_F on 2011-03-20
I would try booting from a recovery CD such as Rescatux. Then I would reinstall to the MBR the grub in Ubuntu 10.10.

Cheers, Pablo

---

### Post by Chtfn on 2011-03-22
Thanks for your answer, Pablo. I didn't try this, but here is what I did:
I installed Ubuntu Studio 10.04 LTS on a new partition, and now I can use this version. The other versions are still in Grub, but I still can't use them, it's exactly the same problem. At least I could recover my stuff on the other partitions via 10.04.
Does this help you guys understand the problem? How should I file that kind of bug?

---

### Post by ailo.at on 2011-03-22
This happened to me when installing Ubuntu Studio 11.04 from usb stick, that I made using unetbootin.

(This is for those who tries to boot, but nothing happens and the screen goes to sleep.)

The reason for not being able to boot is because ubuntustudio-desktop was not installed.
In recovery mode, drop into root shell with networking and do:

apt-get install ubuntustudio-desktop

Chtfn, did you install from DVD? What did you use?

Also, I don't know why 10.10 would be affected.

---

### Post by pHerretpHunk on 2011-08-12
I have the same problem, so I tried the recommended solution of booting into recovery mode, but when I executed "apt-get ubuntustudio-desktop" I got an unmet dependencies error, and the following errors were returned:

Depends: gnome-applets but it is not going to be installed
Depends: gnome-control-center but it is not going to be installed
Depends: gnome-media but it is not going to be installed
Depends: gnome-panel but it is not going to be installed
Depends: gnome-session but it is not going to be installed
Depends: network-manager-gnome but it is not going to be installed
Depends: pulseaudio-esound-compat but it is not going to be installed
Recommends: padevchooser but it is not going to be installed
Recommends: pamon but it is not going to be installed
Recommends: paprefs but it is not going to be installed
Recommends: pavucontrol but it is not going to be installed
Recommends: pavumeter but it is not going to be installed
Recommends: pulseaudio-module-bluetooth but it is not going to be installed
Recommends: pulseaudio-module-gconf but it is not going to be installed
Recommends: pulseaudio-module-x11 but it is not going to be installed

Sorry, I don't know how to give an actual screen capture, so I wrote it all down and typed it in manually. Can anyone help me with this?

---

### Post by jejeman on 2011-08-13
Do you have internet access in that root console?

---

### Post by pHerretpHunk on 2011-08-13
Yes I do. I watched it go through all the update motions with no problems.

---

### Post by pHerretpHunk on 2011-08-13
By the way, what is up with it taking way more of my hard drive than I said it could? I have a 120gb HD and I told Ubuntu it could have 60, but now Windows only has 40. What gives? Is there any way I can re-size it and give Windows half the drive or am I screwed?

---

### Post by jejeman on 2011-08-13
Give us the output form command
```
sudo parted -l
```

---

### Post by pHerretpHunk on 2011-08-13
Is that a letter l or a number 1? And I can do this from the recovery command line?

---

### Post by jejeman on 2011-08-13
It is a small L. 
And yes you can use it in recovery command line, it is a command. ;)
I forgot that you are using just a CLI, so you can do it like this
```
sudo parted -l > partitions.txt
```and later copy here the contents of the generate txt file.
First try command wihout ">" part, to see if you need to answer a question. Sometimes it has questions. Than do with ">" part, so you don't need to write it down on paper. It is a big output.

---

### Post by pHerretpHunk on 2011-08-13
Unless there is a quick and easy way for me to save the output and easily find it when I boot back into Windows, I'm going to have to write it down. I'm sure the solution is something blazingly obvious to everyone but me, but I'm a total n00b. Feel free to laugh at me, just not to my face, okay? ;-)

---

### Post by jejeman on 2011-08-13
As I said the output will be saved in partitions.txt file in the working directory. Than copy the file to win partition or usb.

---

### Post by pHerretpHunk on 2011-08-13
That sounds suspiciously easy. Watch me fail. ;-) Anyway, I won't be trying anything for a few hours yet, on account of someone else here needs to get online and do something productive. I'll let you know how things work out later. Thanks.

---

### Post by pHerretpHunk on 2011-08-14
Okay, so tried what you suggested, jejeman, but it tells me command not found for parted. Now that I have rebooted into Windows and am replying, it occurs to me that I could have  typed "sudo gparted -l" but now I don't want to reboot again. I think I'd best just scrap the Ubuntu (I have never had a successful install or properly working one over the years) and just go back to Mint. That always works like a charm. But I want the rest of my drive back.

---

### Post by pHerretpHunk on 2011-08-15
Okay, I managed to get my whole disk back using Partition Wizard, a free version of what used to be Partition Magic. It was fast, easy, and painless. Also it was graphical, a big help to a n00b like me. I may give Ubuntu Studio or another Ubuntu a try again, but this time I'm putting it on my Mint drive.

---

### Post by eligwd on 2011-09-27
I been trying to get 2 HDD's and ubuntu 11.04 64 bit and UStudio 11.04 to install and boot but???
I think the 64 bit is the problem?
Probably need to use only 32 bit for both of them?
I am now removing one hdd and just gonna try to get them to dual boot from one hdd???

---

### Post by jejeman on 2011-09-28
If youre cpu isn't 64bit, than use 32bit. Otherwise it doesn't metter.

---

