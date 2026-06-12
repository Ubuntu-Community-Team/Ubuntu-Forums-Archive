---
title: "Personal Server Help!"
date: 2009-01-27
forum: Server Platforms
---

### Post by Matsuri on 2009-01-27
Hello all,

I have an extra box and I'm looking to make a personal server for my dorm. The intended operations that this server needs to be able to do in both Ubuntu and MS XP/Vista is:

1. File Storage
2. Media streaming
   - Music to laptops and Desktops
   - Videos to TV
3. Print Server
   - For laptops and desktop computers... wirelessly :P

I have a small idea of where to start but not totally. Should I use the Server edition of Ubuntu or use the Desktop edition? Any other specific programs to use for what I need it to be able to do? I understand that I'll need SAMBA and CUPS for Windows based printing. What is available for Media streaming? What is the best way to setup file storage, preferably with user accounts. (Multiple people in my dorm). The box will be hooked up to my wireless router on the network.

The box I'm using is a little stretched for RAM (256mb) and I'm looking into increasing that.

Processor: 2.0ghz
Ram: 256mb
Plenty of Hard drive space
Video: ATI Radeon x850 Pro

All (constructive) comments appreciated!

Thanks,
Matsuri

---

### Post by Coreigh on 2009-01-27
Server will give you the best performance given your hardware, but you'll need to be comfortable with the command line. Everything but the video to a TV is pretty basic file server stuff Samba for the Windows clients and NFS for the linux (NFS just works better and is native to Linux clients) I know that Mythbuntu can drive a TV and run headless, but I have never gotten it to work. I didn't try to hard though either.

If you really want to avoid the command line you can install a window manager on the server version, or just use the desktop version and add packages as needed, but in either case I would add a lot more RAM. 

Adding RAM just can't hurt you anyway, you will never say 'wow I added too much RAM.'

---

### Post by Matsuri on 2009-01-27
I'm pretty comfy in the command line so it does not bother me. However, my other dorm mate will be helping me run this server and maintaining it. He however, is no so experienced. Any low end window managers?

I have utterly no experience with the server edition. Is it pretty much install the software, configure SAMBA, CUPS, NFS, and anything else and it works? Anything special I have to do in order to get everything working with each other? Other than obviously fighting the evil empire ( MicroSoft ) to configure it properly.

Much appreciated!
Matsuri

---

### Post by tomwerner470 on 2009-01-27
Fluxbox and IceWM are both lightweight window managers, however, what tools do you think you would need in a graphical environment that you couldn't use on the command line? I personlly have installed icewm on a server that needed a GUI to be able to run WINE apps and it is perfect just for that.

Both are available in the repos, if you intend to install this on a Server edition install, you may also need to pull in the base X11 server as I am not sure whether fluxbox/icewm will pull it automatically...

Good luck..

---

### Post by Matsuri on 2009-01-27
Well, I'm fine doing everything via command line. However, my roommate will be helping me is pretty much a noob with unix based systems. I just need a windows manager that will allow him to basically maintain everything / help work on the server. I might be asking to much out of a window manager but hey, I can dream right?

---

### Post by tomwerner470 on 2009-01-27
you may be dreaming - it depends on what you are expecting the ui to do :-)

---

### Post by cariboo on 2009-01-28
Instead of installing a desktop, you could install [webmin]("http://webmin.com/"), it is a web based server administration suite. It uses far less resources then a desktop would.

Jim

---

### Post by Matsuri on 2009-01-28
I was actually looking into using Webmin. Since when does Ubuntu 8.04 Server edition not include a full fledged terminal but busybox or whatever it is called?

Did I managed to set this up wrong? Any tutorials on the forums here or external sites? Noob on servers :P

thanks!

---

### Post by tomwerner470 on 2009-01-28
Bash is the default shell you get with Ubuntu Server, if you are getting a busybox shell then something may of gone wrong at boot and dropped you into a busybox shell to try and fix the problem.

+1 for webmin it does make config alot easier and is realtively easy to install.

---

### Post by Matsuri on 2009-01-28
K, installed this at like midnight so I don't think I was awake enough to notice the error staring me in the face. Haven't done much of a search on it but here is the error I get on startup:

```
29.568137 ata1.01: status: {DRDY ERR }
29.568189 ata1.01: error: {ICRC ABRT}
Check root = bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/995bb6e4-0e8a-425c-835b-fbb3c86f515f does not exist. Dropping to a shell!
```

And then busybox :)

Any suggestions? This is also a brand new install. I installed last night and started it up for the first time and got this. No errors during the install process. Popped in the rescue disk to try and explore the problem. My system was installed on sda1. Home directory on sdb5. Rescue disk cannot mount sda1 for whatever reason.

---

### Post by tomwerner470 on 2009-01-28
The first two lines look like a disk initialisation error. I have seen issues with booting with this error when the settings were incorrect in the bios for AHCI support (assuming you are using SATA drives). 

I would also double check the cables etc.

What spec is the machine and what was it running before (if anything)?

---

### Post by Matsuri on 2009-01-28
Read the first post for the system specs.

The system previously ran Ubuntu Edgy Eft. I've tried reinstalling the server software and always get the same error. What in the boot bios would I need to check to make sure everything is setup properly?

I'm not going to flash the bios as I don't feel like bricking my extra box.

Edit: Just installed Ubuntu Edgy Eft Server Edition on the box and it configures and boots perfectly fine. Bugs in the 8.04 server edition?

Edit: Installed Edgy Eft and upgraded to Feisty Fawn 8.10... same problem.

---

### Post by tomwerner470 on 2009-01-29
Are the system's hard disk(s) Sata based?

---

### Post by Matsuri on 2009-01-29
I don't remember. Its been a while since I've had this thing apart. Any quick way of telling, other than pulling the drives and looking at them?

:P Screw Drivers are of scarce nature in college...

---

### Post by redroad55 on 2009-01-29
Hi here's my 2 cents .. Install the "alternate install" cd for 8.04 desktop giving your assistant some time to get used to linux .. then one step at a time add what you need to desktop in the way of server environment .. I suggest 8.04 simply because it is an LTS kernel (long term support) supported for 5 years .. you don't want to spend all this time overcoming the learning curve here only to relearn the ins and outs of a new kernel in one year .. Max out your ram , 256 mb although adequate is certainly not optimal , buy some used memory off ebay ( ram is one of the few computer parts you can buy used and be sure 99% of the time to be functional ) .. As far as the suggestion to update the Bios , there are certain times when this is necessary .. You are right to be cautious about this however in order to go forward it may be the only choice .. Before you choose this route prepare by reading what is required to do the update .. 
you might find these links helpful
[[URL="http://tldp.org/LDP/sag/html/index.html"]https://help.ubuntu.com/8.04/serverguide/C/index.html]("https://help.ubuntu.com/8.04/serverguide/C/index.html")[/URL]
[http://tldp.org/LDP/sag/html/index.html]("http://tldp.org/LDP/sag/html/index.html") 
Remember this the more imfo you can give in your posts the more help you will receive .. Post back and let us know how you are coming ..
Best to you..

---

### Post by element_G on 2009-01-29
I used to have this problem (dropping to busybox on boot after a clean no-problems install from livecd).

The fix I found was to insert ' all_generic_ide ' into your boot options from GRUB

To do this, when you see grub:

select your desired kernel 
press  e  (to edit the menu entry)
scroll to the line that says kernel 
e again  (to edit the line)
at the very end of the line type ' all_generic_ide '
press enter 
press b to boot this kernel

also here are some links for I recently used to set up my home server
General How-To: [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/)
Setting a Static IP: [http://ubuntuforums.org/showpost.php?p=6226922&postcount=9](http://ubuntuforums.org/showpost.php?p=6226922&postcount=9)
How to mount a Samba share at boot: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) 
Stream anything with VLC: [http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/](http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/)
Very detailed info on SSH: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
Ubuntu help for VNC: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by tomwerner470 on 2009-01-29
Sounds like good advice redroad, it will be interesting whether the desktop boots ok, as the kernels are so similar between the two distros.

Regarding the bios thing, I may have mislead you there, I didn't mean to reflash your bios - I have never dared do that in my life! Assuming the machine has sata disks, there will be a setting for the SATA disk controller, with options normally like; ide compat, raid and (pure) ahci. When I had the same errors on my ubuntu desktop, it was because the setting was set to ide compatiability, not ahci.

Looking at element_g's post, that may well work aswell, however, I seem to recall the reason why ide compat didn't work on my machine was because the generic_ide driver has issues with my rather dodgy dell motherboard :-) 

Certainly give both a try, ubuntu won't bluesceen on you just because you decided to change the mode of the disk!

---

### Post by Matsuri on 2009-01-29
Redroad, the point is not to reinstall a Desktop software on this machine. Would rather learn the ins and outs of running a server. I'm ok with a learning curve, I like computers. I appreciate the advice though.

The problem is fixed! The `all_generic_ide' crap is what caused it. I had this problem on a desktop version of Ubuntu a while ago... surprised that they haven't fixed that bug in the software.

Anyone else have this problem, do as element_g said to get into your server. Then once booted, login and type:

```

cd /boot/grub
sudo nano menu.lst

```

Once there, scroll down past all the ## comments and the section with the title: "Ubuntu 8.04.02, Kernel 2.6.24-23-server"

 Edit the kernel line and remove the 'quiet splash'. Simply replace it with 'all_generic_ide'

Once done, press ctr+o and hit enter. Then press crt+x to exit.

---

### Post by tomwerner470 on 2009-01-29
Aswell as what mastsuri said, it is best to also make amendments to the line beginning:
```
# kopt=
```

for example
```
# kopt=root=UUID=8edb92fb-7e25-46b3-9264-0dccb8c3b94d ro [COLOR="Red"]**all_generic_ide**[/COLOR]

```

So that the setting is preserved after a kernel upgrade.

---

### Post by redroad55 on 2009-01-29
I'm glad you got it.. My suggestion for the desktop was more for your assistant not you so much ,, you said "my roommate will be helping me is pretty much a noob with unix based systems" .. I just wouldn't want to spend all the time building a data base and put it in the hands of someone else without giving then all the help I could ..It's great that you posted your solution so others can benefit .. Good on you ..Just one last thing to do show element_g some respect by roasting his beans and mark the thread as solved .. Best to you

---

