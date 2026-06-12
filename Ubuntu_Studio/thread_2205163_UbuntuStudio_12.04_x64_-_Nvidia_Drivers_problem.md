---
title: "UbuntuStudio 12.04 x64 - Nvidia Drivers problem"
date: 2014-02-12
forum: Ubuntu Studio
---

### Post by sam28 on 2014-02-12
Hi!
I'm a new user of ubuntustudio on laptop Acer Aspire 4520G with SSD Crucial M4 128G.

Please help - after install system i can see in "NVIDIA X Server Settings" version of drivers is 173.14.39.
Once i try to update Nvidia Drivers trough "Additional Drivers" - after restart i can't login (after login my laptop is freeze).

So question is:
- i should update Nvidia drivers or no?
- if it better to update - which versions of Nvidia drivers i should install?

Big thanx.

p.s. Regards from Ukraine.:)

---

### Post by jejeman on 2014-02-12
Give us
```
lspci -knn | grep VGA -A 5
```

---

### Post by sam28 on 2014-03-03
Sorry for late reply:

unclesam@unclesam-Aspire-4520G:~$ lspci -knn | grep VGA -A 5
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation G86M [GeForce 8400M G] [10de:0428] (rev a1)
	Subsystem: Acer Incorporated [ALI] Device [1025:0121]
	Kernel driver in use: nvidia
	Kernel modules: nvidia_173, nouveau, nvidiafb
07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Quanta Microsystems, Inc Device [1a32:0105]

---

### Post by jejeman on 2014-03-03
You have Nvidia 8400M card, it works with the nvidia-current driver, and that is the one you should use.

Purge the nvidia_173 driver, instal the nvidia-current

```
sudo apt-get purge nvidia-173
sudo apt-get install nvidia-current
```

---

### Post by sam28 on 2014-03-04
> **jejeman said:**
> You have Nvidia 8400M card, it works with the nvidia-current driver, and that is the one you should use.

Purge the nvidia_173 driver, instal the nvidia-current

```
sudo apt-get purge nvidia-173
sudo apt-get install nvidia-current
```
Dosent work = on login screen after i enter user & pass - freeze.
Now i 'm just fully reinstall system. :(

p.s. If i install Ubuntu 12.04 - same problem with video drivers - works only, if after installing system i don't touch any update for vide drivers.:(

---

### Post by jejeman on 2014-03-05
Well, then use the nouveau driver. If you don't need 3D support there is no need to install proprietary driver.

---

### Post by sam28 on 2014-03-05
[Here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1033263") i read this "[COLOR=#333333][FONT=Ubuntu Mono]Version 173 of the Nvidia seems to be less troublesome. ... but no quick and total freezing, like with Nvidia current.[/FONT][/COLOR]".
Please help.:(

---

### Post by sam28 on 2014-03-05
> **jejeman said:**
> Well, then use the nouveau driver. If you don't need 3D support there is no need to install proprietary driver.
304 drivers will not work on my laptop?

---

### Post by luctor on 2014-03-05
there's a problem with the 8300 and 8400 card
Newer (304) drivers are NOT working, use the 173 legacy drivers or nouveau
It's a card problem, not an ubuntu or linux problem. I can't even update the windows drivers on my pc

---

### Post by jejeman on 2014-03-05
I didn't know about that specific problem with 8400m. Then you are better off with nouveau.

---

### Post by sam28 on 2014-03-05
Sad .:(
As is see here [http://www.geforce.co.uk/drivers](http://www.geforce.co.uk/drivers) they still developin new drivers, but we can try on our own risk.
I'm tired from reinstalling system all the time after got some problems with drivers testing ...

---

### Post by sam28 on 2014-03-05
Here [http://ubuntuforums.org/showthread.php?t=2191611&highlight=nvidia+8400m](http://ubuntuforums.org/showthread.php?t=2191611&highlight=nvidia+8400m) Nvidia GeForce 8400M GS works with 313 driver. How i possible?

---

### Post by sam28 on 2014-04-26
Looks that we have [solution]("http://ubuntuforums.org/showthread.php?t=2189839&highlight=years+%28literally%21%29+waiting%2C+users+nVidia+GeForce+8400m+%28and+G86M+family%29+celebrate.+issue+fixed+nvidia-331+drivers.+better%2C+corruption+bug+GPU+nouveau+found+fixed+Kernel+3.14%2C+nouveau+binary+blobs+working+finally.+I%27ve+tested+released+Ubuntu+14.04+64-bits+%28ships+kernel+3.13+updated+3.14.1%29.+Cheers%21%26quot%3B%26quot%3B"). But not yet tested by me. Hope will do it soon.:)

---

### Post by luctor on 2014-04-28
> **sam28 said:**
> Looks that we have [solution]("http://ubuntuforums.org/showthread.php?t=2189839&highlight=years+%28literally%21%29+waiting%2C+users+nVidia+GeForce+8400m+%28and+G86M+family%29+celebrate.+issue+fixed+nvidia-331+drivers.+better%2C+corruption+bug+GPU+nouveau+found+fixed+Kernel+3.14%2C+nouveau+binary+blobs+working+finally.+I%27ve+tested+released+Ubuntu+14.04+64-bits+%28ships+kernel+3.13+updated+3.14.1%29.+Cheers%21%26quot%3B%26quot%3B"). But not yet tested by me. Hope will do it soon.:)

Installed the nvidia-331 drivers in lubuntu 14.04 , they work great, so far ! :-)
I've done the following to test the driver:

[LIST]a quick game of Urban Terror[/LIST]
[list]run compton as a screen compositor[/list]
[list]run Synthesia in wine, cause that used to give me screen flickering with the 173 drivers[/list]

so far no issues, very excited :-) 

thanks, sam28 for the tip!

---

### Post by sam28 on 2014-04-30
> **luctor said:**
> Installed the nvidia-331 drivers in lubuntu 14.04 , they work great, so far ! :-)
I've done the following to test the driver:

[LIST]
[*]a quick game of Urban Terror
[/LIST]

[LIST]
[*]run compton as a screen compositor
[/LIST]

[LIST]
[*]run Synthesia in wine, cause that used to give me screen flickering with the 173 drivers
[/LIST]

so far no issues, very excited :-) 

thanks, sam28 for the tip!
U r welcome, hehe.;)

U installed NVIDIA-Linux-x86_64-331.67.run or nouveau?

Please, can u write us step by step process of installing nvidia drivers?
Btw - which model of laptop/pc u have and nvidia graphic card model?

---

### Post by jejeman on 2014-04-30
There are 331.38 in repository, just install form there.

---

### Post by luctor on 2014-05-01
> **sam28 said:**
> U r welcome, hehe.;)

U installed NVIDIA-Linux-x86_64-331.67.run or nouveau?

Please, can u write us step by step process of installing nvidia drivers?
Btw - which model of laptop/pc u have and nvidia graphic card model?

nVidia GeForce8300 GS (128MB DDR2 PCI-Express x16 (DVI/VGA) )Dell Inspiron 531

open terminal 
```

sudo apt-get install nvidia-331

```

after that reboot

piece of cake

---

### Post by sam28 on 2014-05-02
No need sudo apt-get purge nvidia and then [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install nvidia-331 ?[/FONT][/COLOR]

---

### Post by jejeman on 2014-05-02
Do you already have nvidia driver installed? Which one?

---

### Post by sam28 on 2014-05-03
> **jejeman said:**
> Do you already have nvidia driver installed? Which one?
Yes, nvidia 173 nouveau.

---

### Post by jejeman on 2014-05-03
I've read whole thread to refresh my memory.
Yes, you can purge it, purge both the dirver and nvidia X server settings.
After that install 331.
Remember 331 is only available in 14.04.

---

### Post by sam28 on 2014-05-03
> **jejeman said:**
> I've read whole thread to refresh my memory.
Yes, you can purge it, purge both the dirver and nvidia X server settings.
After that install 331.
Remember 331 is only available in 14.04.

[COLOR=#0000cd]Remember 331 is only available in 14.04[/COLOR] -- nouveau or official nvidia? Are you sure about 14.04? Why that drivers dont work on 12.04?

So, as i understand - i should:
[LIST=1]
[*]Erase UbuntuStudio 12.04 from my laptop by installing UbuntuStudio 14.04
[*]remove nvidia 173 nouveau (as i know its default drivers for my graphick card, that comes with ubuntu)  
[LIST]
[*]sudo nvidia-settings --uninstall
[*]sudo apt-get remove --purge nvidia* [COLOR=#ff0000]<- here should be [/COLOR][COLOR=#0000cd]nvidia[/COLOR][COLOR=#ff0000] or[/COLOR][COLOR=#0000cd] nvidia*[/COLOR][COLOR=#ff0000] ?[/COLOR]

[*]sudo apt-get remove --purge xserver-xorg-video-nouveau xserver-xorg-video-nv
[/LIST]

[*]&#8203;install nvidia 331
[LIST]
[*]&#8203;sudo apt-get install nvidia-331
[/LIST]
[/LIST]


&#8203;Everything correct?

p.s. Big thanx for attention.:)

---

### Post by luctor on 2014-05-04
If I'm not mistaken, ubuntu doesn't install restricted drivers by default so there's no need to purge nvidia drivers.

---

### Post by sam28 on 2014-05-04
> **luctor said:**
> If I'm not mistaken, ubuntu doesn't install restricted drivers by default so there's no need to purge nvidia drivers.
Are you sure that i need to install ubuntustudio 14.04 instead current ubuntustudio 12.04 for installing official 331 by 
[LIST]
[*]&#8203;sudo apt-get install nvidia-331
[/LIST]
?

---

### Post by jejeman on 2014-05-04
I don't understand why are you always keep joining together number 173 and nouveau?
173 is version of Nvidia driver, nouveau is FLOSS driver for nvidia cards. You need to remove 173 if you want to install 331, if it is installed, but leave nouveau alone.
If we say 331 or any other number it is proprietary Nvidia driver, not a free driver nouveau. Number is always associated with proprietary driver.

You can't simply run "&#8203;sudo apt-get install nvidia-331" for 12.04, there is no such package on 12.04. Look for it your self.

I guess you can install 331 on 12.04 if you make that package, hope to be compatible with X server version, or if you can find it in PPAs or similar. I wouldn't recommend using .run package from nvidia website.

---

### Post by sam28 on 2014-05-04
> **jejeman said:**
> I don't understand why are you always keep joining together number 173 and nouveau?
173 is version of Nvidia driver, nouveau is FLOSS driver for nvidia cards. You need to remove 173 if you want to install 331, if it is installed, but leave nouveau alone.
If we say 331 or any other number it is proprietary Nvidia driver, not a free driver nouveau. Number is always associated with proprietary driver.

You can't simply run "&#8203;sudo apt-get install nvidia-331" for 12.04, there is no such package on 12.04. Look for it your self.

I guess you can install 331 on 12.04 if you make that package, hope to be compatible with X server version, or if you can find it in PPAs or similar. I wouldn't recommend using .run package from nvidia website.
I am new ubuntu user, so a lot of things i need to learn (with community help;)).

What you mean "[COLOR=#0000ff]if you make that package[/COLOR]"? I dont know how to create some packages - i know how to'install from ppa trough [COLOR=#0000ff]sudo apt-get install[/COLOR] etc.:)

I have clean installed ubuntustudio 12.04 with nvidia 173 drivers.
Now i want to install nvidia 331 drivers, but i don't know how to check compatible with X server version?!
I worry if i will run simply [COLOR=#0000ff]&#8203;sudo apt-get install nvidia-331 [/COLOR][COLOR=#000000]after restart and login [/COLOR][COLOR=#0000ff]i [/COLOR][COLOR=#000000]will got screen freeze and need to reinstall whole system again.:(
Whats why i keep asking for help, bcos i need to understand clearly everything.
In advance big thanx for everyone, who answering!:)[/COLOR]

---

### Post by jejeman on 2014-05-05
The easiest thing for you to do is to cut small slice off the HDD, install 14.04 and see how will that work for you. If it is all good, you can switch to it from 12.04.
All the rest is at least few weeks of learning, exploring and working.

---

### Post by luctor on 2014-05-06
For me, 14.04 is working very good. So I recommend installing a fresh 14.04 and after that, installing nvidia-331.
Don't be alarmed if after installing the nvidia drivers the plymouth startup-screen looks like crap.
On my pc I first get a blinking white cursor on a black background, after that a blue blackground with white "LUBUNTU" text and white dots.
When the desktop is loaded everything works fine.

---

### Post by sam28 on 2014-05-09
Test No1:
- sudo apt-get install nvidia-331
- reboot

Dosen't work - in Nvidia X Server Settings still i see "NVIDIA Driver Version 173.14.39" :(

But [COLOR=#000000][FONT=Ubuntu Mono]lspci -knn | grep VGA -A 5[/FONT][/COLOR][FONT=Ubuntu Mono]:
[/FONT][COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR][IMG]http://cs620327.vk.me/v620327057/49ad/o0lRccCOQAA.jpg[/IMG]

How i should force laptop use Kernel moude 331 instead 173?
Now thinking which steps i should do in test No2 ...
Any suggestions?

---

### Post by jejeman on 2014-05-09
First, I need to correct my self, actually there is 331 package in 12.04. 

Which nvidia settings package you have installed?

One suggestion: Don't use picture to show text from terminal, just copy it.

Module 331 is active. You should purge the 173 module.

---

### Post by sam28 on 2014-05-09
> **jejeman said:**
> First, I need to correct my self, actually there is 331 package in 12.04. 
[QUOTE=jejeman;13019117]Which nvidia settings package you have installed?
I use this in terminal [COLOR=#000000]sudo apt-get install nvidia-331[/COLOR]

> **jejeman said:**
> One suggestion: Don't use picture to show text from terminal, just copy it.
Ok.

> **jejeman said:**
> Module 331 is active. You should purge the 173 module.
Purge by [COLOR=#0000cd]purge nvidia-173[/COLOR] ?

---

### Post by jejeman on 2014-05-09
Yes, purge the 173 package.

There is two packets one for settings, and one  for driver.
Just give
```
dpkg -l | grep nvidia
```

---

### Post by sam28 on 2014-05-10
sudo apt-get purge nvidia-173 - afte this reboot, abter password and my screen freeze. Thats it. Again reinstalling system:(

---

### Post by sam28 on 2014-05-10
Problem solved - clean install UbuntuStudio 14.04 x64, settings -> Software Updater -> Settings -> Additional Drivers -> Select "Using NVIDIA binary driver - version 331.38 from nvidia-331 (proprietary, tested)".
Looks good.:)
Now ready to test Steam and Play On Linux.

---

### Post by sam28 on 2014-05-10
Problem solved - clean install UbuntuStudio 14.04 x64, settings -> Software Updater -> Settings -> Additional Drivers -> Select "Using NVIDIA binary driver - version 331.38 from nvidia-331 (proprietary, tested)".
Looks good.:)
Now ready to test Steam and Play On Linux.

---

### Post by barjea on 2014-06-04
Nvidia drivers problem or Crucial M4 firmware ?
I had similar issue with my Crucial M4 SSD. It would freeze after one hour of uptime.
I had to update M4 firmware to 070H see :
[http://en.kioskea.net/faq/29514-crucial-m4-how-to-remove-the-5200-hours-bug](http://en.kioskea.net/faq/29514-crucial-m4-how-to-remove-the-5200-hours-bug)

How to do it :
[COLOR=#333333][FONT=UbuntuRegular]Upoad crucial-m4-070h-07-00.iso file, create a bootable USB key using UNetbootin and follow instructions.[/FONT][/COLOR]

---

### Post by sam28 on 2014-06-17
Yes, Crucial M4.

Will try to update firmware of my SSD.

---

