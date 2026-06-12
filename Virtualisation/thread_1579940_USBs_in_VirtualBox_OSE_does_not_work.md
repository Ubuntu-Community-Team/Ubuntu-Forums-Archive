---
title: "USBs in VirtualBox OSE does not work"
date: 2010-09-22
forum: Virtualisation
---

### Post by Perica911 on 2010-09-22
Hello,

I am running Windows XP under VirtualBox OSE and I can not use USB there. Whan I pluggin an usb storage stick it only apeers in ubuntu, but not in Windows. Could anyone help me with this?

I have to mention that my usb mouse works fine in both systems. When I pluggin the mouse it is detected in Ubuntu and Windows and I can use it.

Another problem is the sound in Windows under this VirtualBox OSE. On the VirtualBox OSE first window it say I have no sound drivers so I can understand why it does not work, but I installed drivers in Windows and it still says null audio driver. Do I have to check a box or choose the sound card somewhere? 

All this made me buy an USB sound card, actually just an USD mic and headphones socket. It works good in ubuntu, but only for the music and sounds, under System>Preferences>Sound I have changed all the sound devices to this USD sound card, did the test and everything works good. But than I ran Skype(Beta) 2.1.0.81 and it is still using the old devices, so my laptop speakers and the laptops mic.

I would be really grateful if someone could help me with this:)

kind regards and viva la Linux, Peter

---

### Post by wilee-nilee on 2010-09-22
You need the puel version for USB support. Also add yourself to virtualbox in users-groups in the admin menu. Then in the setting with the OS off usb then the plus sign and add the usb.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Perica911 on 2010-09-23
hello,

first thank for this fast replay:)

ok I am not that much of a Linux pro, I am using it only for 6 months now and only for programing and scientific computing and the comp runs smoother of course:)

Could you be more specific with your answer? I need a puel (or did you mean duel) version of USB support, so I need another version of VirtualBox, or just some USD support protocol? Than about adding myself in user-groups, I think I can manage to do that, but it would be faster if you tell me how:) and than the last thing... in my VirtualBox settings for my guest I can not find this + for adding filters for USB and I am running VirtualBox OSE 
2.1.4

again thank you for you help, I really appreciate it

Peter

---

### Post by wilee-nilee on 2010-09-23
> **Perica911 said:**
> hello,

first thank for this fast replay:)

ok I am not that much of a Linux pro, I am using it only for 6 months now and only for programing and scientific computing and the comp runs smoother of course:)

Could you be more specific with your answer? I need a puel (or did you mean duel) version of USB support, so I need another version of VirtualBox, or just some USD support protocol? Than about adding myself in user-groups, I think I can manage to do that, but it would be faster if you tell me how:) and than the last thing... in my VirtualBox settings for my guest I can not find this + for adding filters for USB and I am running VirtualBox OSE 
2.1.4

again thank you for you help, I really appreciate it

Peter

No problem, puel is a license, kind of miss leading. What you can do is just remove the version you have, and install the one in the link you may have to add the original XP;Back, it will still be there. You just have make a new machine and in the install portion point it at the vdi file in the .virtual-hard disc folder. The .virtual folder is hidden hit ctrl+h to see hidden files in home.

The download is a deb, gdebi should open if you click on the download file it's a nice gui. Look for anything missing. Make sure the plain Ubuntu dkms is installed synaptic.

Ask any questions if you need to and if you want to be extra sure; just copy that vdi file to someplace, just to be safe, it is the bootable XP OS in Vbox as it is when you shut it down. If you have any extra snap shots you, that is an area I'm not sure off, I never save that way just the vdi.

User groups is in the menu..system-admin-users and groups open it hit manage groups then scroll to vboxusers and tick your name on and close.
[ATTACH]170303[/ATTACH]

Hey, I'm no pro, just hanging out.;)

---

### Post by Perica911 on 2010-09-23
Again this is  very helpful:) thaks

ok so in the in the first section, you are telling me I need a newer version of VirtualBox, and then I install the vid file?

ok if I tell the the whole story, I am an exchange student and need to communicate with my family home. But the sound does not work in linux for me because Toshibas laptops are known to have problems with sound cards. So I bought an USB sound card socket. If I can get USB working in Windows I can use USB sound card there and I hope skype will work there:) but the problem is I dont have the original XP cd here, so this might be a problem if I need to instal XP all over again. Can I just make a new machine and just use the data from my existing hoste XP? or the date will be lost when I install the new machine?

thanks again, Peter

---

### Post by wilee-nilee on 2010-09-23
Read what I posted carefully the VDI is where I said in the hidden Vbox folder I mention. 

It is not that you need a newer version these two versions are slightly different. They will look the same but the net downloaded one will let a usb connection happen. Whether or not you can use something other then a thumb or HD is speculation.

Take a look at the manual, we are not communicating, very well. I gave very straight information, and how to get to it in the computer, **you have to do some of the work here.** ;) I mean this in the nicest way possible.


So here is are some screen shots leading to the VDI the VDI is the installed XP in your virtual machine. There are other files in the VBox folder as well but the VDI is the OS. So open home and if the hidden files are not showing, hit ctlr+h this will make the first picture, .virtualbox seen.
[ATTACH]170355[/ATTACH][ATTACH]170356[/ATTACH][ATTACH]170357[/ATTACH]

---

### Post by Perica911 on 2010-09-24
> **wilee-nilee said:**
> 
It is not that you need a newer version these two versions are slightly different. They will look the same but the net downloaded one will let a usb connection happen. Whether or not you can use something other then a thumb or HD is speculation.
[ATTACH]170355[/ATTACH][ATTACH]170356[/ATTACH][ATTACH]170357[/ATTACH]

again, many thanks for all your help...

sorry but I must say your instructions are not so straight forward:P you do not refer to a certin think. I have found the vid file ofcourse, but from your instroctions I can not understand what I have to instal. that is why I want to make sure what I am doing.

so I apologize, but I think I do not understand the working of VirtualBox. But I have a clue:) So if I save this .vid file on a save spot, get a new VirtualBox and move this .vid to the same directoy of the new VirtualBox... /home/peter/.VirtualBox/HardDisks

I know I have to do a part of my of, but again I want to make sure what I am doing so that I will not mess ou the sysem:)

I hope we are on the same page now:)

thank you, Peter

---

### Post by wilee-nilee on 2010-09-24
**Making a copy of the vdi is just extra insurance**. When you remove the vitualbox-ose the program is removed but not the XP setup. The XP setup is the vdi file, right click on the vdi then properties and you will see how big it is.

When you start the new installed machine you will not see XP. But it is still in the computer, so you make a new machine like you did when you installed originally, and use the prebuilt vdi in it. You will know what to do, just follow the instructions for building a new machine to run your XP that is still in the same place. 

You can hardly mess this up if you don't remove anything but the Vbox installed now; from synaptic then install the download.

If your nervous about building the new machine practice in the vbox now with a live linux cd so you will see the process again.

I don't know how to make this any easier, good luck.

---

### Post by Perica911 on 2010-09-24
ok now I know exactly waht to do:)

the first paragraph said it all:)

now I just need to get XP install cd and I can do the thing

thank you veay much for all you help again:)

Peter

---

