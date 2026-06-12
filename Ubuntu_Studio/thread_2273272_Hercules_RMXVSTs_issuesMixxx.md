---
title: "Hercules RMX/VSTs issues/Mixxx"
date: 2015-04-11
forum: Ubuntu Studio
---

### Post by gogor67 on 2015-04-11
Hi,

Before telling you about the issues that brought me to post here, it might be important to tell you guys about my configuration.

So, ten days ago, I decided that I'd try to install Windows 8.1, Ubuntu and Kali Linux on my hard drive. After many issues I had to reinstall Windows fort the 10th time, but when the installer reached 90%, a message appeared, saying that local options could not be installed. I tried many times to fix it but after hours of research I ended up finding that this error could only be fixed by changing the hard drive.
I then installed Ubuntu 14.04 without any issue ( it is my only OS now ). After discovering that Ubuntu Studio existed, I installed all the packages from this distribution, which is why I post here now. 
In the end, the issues I have might be caused by my corrupted hard drive. I don't think they are, but if no one could help me, I would definitely think this is the reason why nothing works as expected.

By the way, my Hercules RMX controller doesn't work at all. I' ve downloaded the driver package many times but when I plug it to my powered usb hub, all the other usb things that are plugged to my computer get disconnected, and  the RMX doesn't stop going on and off. It has been recognized once, for a couple of seconds ( lsusb showed me the controller ) but it soon stoppped working again. It is not broken, I have used it on an other computer.
Now, for Mixxx : Mixxx doesn't stop crashing. Firstly, I just cannot launch it by clicking on the icon, because it doesn't do anything ; I have to launch it with a command line. Secondly, it doesn't make any sound, no matter how I set the output in the settings. And finally, it randomly crashes when I try change the settings ( yeah, it's really screwed up :lolflag: ).

And here comes the most important issue : I cannot use my windows VSTs because I cannot get lash and other softwares like this to be installed properly ; as I cannot find the ladish package with apt-get for example, I've spent several hours trying to compile it. I've fixed an insane lot of error messages, but I don't understand this last message, and I'm pretty sure THIS can be fixed ( I'm not so sure about the other issues, unfortunately :/ ) :
[ATTACH=CONFIG]261231[/ATTACH]
The configure process doesn't recognize my locale.h library, although it IS installed. I' ve even displayed where the process looks for the locale.h thing, and looked directlty for it in the the directory ; locale.h is where it should be. But I'm convinced there's a way to fix it, probably because of all the other problems I've fixed before this one came up :p

Anyways, I' m sorry to post such a long message, but I think all these problems are closely related. Maybe I've messed up the installation or something. Thanks for reading, and hopefully, trying to help me ):P

---

