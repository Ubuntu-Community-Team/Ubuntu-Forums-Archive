---
title: "VMWARE-Error unable to add virtual machine"
date: 2007-12-05
forum: Virtualisation
---

### Post by masai489 on 2007-12-05
Hello all. I have been dual booting and wanted to stop that. I used Vmware converter to make my xp side a virtual machine and put it on my larger usb drive. Install of vmserver went fine but when I start it up and navigate to the machine I have I get this window..


Unable to add virtual machine "/media/disk/Section-2/Section-2.vmx" to the inventory: Configuration file was created by a VMware product with more features than this version.

Anyone know what this means? I don't want to reinstall when i have a working xp setup. Thanks for any help you guys can give.

:guitar:

---

### Post by speed145a on 2007-12-05
what version of vmware are you using to run the virtual machine?

i believe that in order to get around this features problem you will need vmplayer 2.0.x

player 2.0 has a lot more features than the previous versions (including usb suport) and the only real difference is that you can't CREATE new virtual machines with the player.
since you already have the virtual machine created and you are just looking to run it now i would install vmplayer 2.0

---

### Post by masai489 on 2007-12-05
Speed, thanks so much. I've been lurking around some other sites and saw that this might be my problem also. I'm going to try your solution. I'll be back..as Ahnold said..thanks. :)

---

### Post by masai489 on 2007-12-05
I downloaded the vmplayer, extracted it...but now can't run it. I tried to sudo command sudo ./vmware-install.pl and it tells me the command not found. But those are the directions I found to install. Any suggestions? Thanks

---

### Post by gb64 on 2007-12-05
Did you cd into the vmware-player-distrib directory, then type the command?
[B]cd vmware-player-distrib
   sudo ./vmware-install.pl[/B]

---

### Post by masai489 on 2007-12-05
I did do that. I was also told to run the vmware any-any update. Even after doing that, I try to run the player andit says vmplayer isn't installed, though I thought I did that. But neither method worked. Oh yea, I didn't get that directory. I untared the vmplayer file..cd to the directory and only saw usr and etc. thanks :)

---

### Post by masai489 on 2007-12-05
I think I see what I did wrong. I believe I downloaded the wrong package. I should have gotten the tar and not the rpm. I'm downloading the tar now and will see what happens from there. BRB

---

### Post by gb64 on 2007-12-05
If you get the latest player version, and you have the regular kernel, it may install without using the any-any package.

---

### Post by masai489 on 2007-12-05
Thanks for all the help you guys. I've been at this for two days now and it wins. I'm just going to have to do a fresh install and try my best to setup everything as it is on my dual boot. Thanks again.

---

### Post by speed145a on 2007-12-05
don't give up buddy!!

i worked on getting mine working for over 2 weeks and now it is so awesome!

we can help guide you through any other steps you need

just let us know where you are at and we can get you through

---

### Post by sahi on 2009-07-22
I used vm converter to convert my laptop to a virtual machine. I saved the vm image in my c drive. I created it with vm server 2.x . Trying to open it in VM server console 1.0.6. I see this error message : "Configuration file was created by a VMware product with more features than this version" Any help would be great.

---

### Post by Cheesemill on 2009-07-23
When you run VMware Converter you get an option to specify the VM hardware version.
Make sure you select a version that is low enough to be compatible with whatever host solution you are using (Server 2.0, ESX, Player, etc..).

---

