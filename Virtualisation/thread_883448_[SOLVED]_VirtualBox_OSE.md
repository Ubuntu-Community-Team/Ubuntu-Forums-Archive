---
title: "[SOLVED] VirtualBox OSE"
date: 2008-08-08
forum: Virtualisation
---

### Post by cowboyup6983 on 2008-08-08
I install VirtualBox about a week ago, and i finally tried to install Windows XP via virtual machine. i got a an error message right after completely everything and actually booting for the first time.

its says:

virtualbox kernel driver not installed. 

VBox status code:-1908 (VERR_VM_DRIVER_NOT_INSTALLED).

does anyone have any suggestions?

the verison of VirtualBox OSE i have installed is: 1.5.6_OSE

---

### Post by DagMan on 2008-08-08
you just need to install virtualbox-ose-modules
there's a differant package for the various differant kernels so it would be virtualbox-ose-modules-generic for example, or perhaps virtualbox-ose-modules-`uname -r` would work.

---

### Post by cowboyup6983 on 2008-08-08
> **DagMan said:**
> you just need to install virtualbox-ose-modules
there's a differant package for the various differant kernels so it would be virtualbox-ose-modules-generic for example, or perhaps virtualbox-ose-modules-`uname -r` would work.

can anyone be more specific.. i dont understand.

---

### Post by jocko on 2008-08-08
More specific? Not sure if that's possible. I'll just repeat what the last poster said:

Install the package virtualbox-ose-modules-XXX matching your kernel. Either find it in synaptic, or use this command in a terminal:
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```

---

### Post by davidw89 on 2008-08-09
How do i find my kernel number?

---

### Post by jocko on 2008-08-09
```
uname -r
``` will give you the kernel number.

---

### Post by overdrank on 2008-08-09
Moved to  Virtualization :)

---

### Post by davidw89 on 2008-08-09
> **jocko said:**
> More specific? Not sure if that's possible. I'll just repeat what the last poster said:

Install the package virtualbox-ose-modules-XXX matching your kernel. Either find it in synaptic, or use this command in a terminal:
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```

Your instruction is kinda unclear

I have found my kernel number: 2.6.24-19-generic

So what do i do?

I have type this:
sudo apt-get install virtualbox-ose-modules-`uname -r`

or is it:

sudo apt-get install virtualbox-ose-modules-`2.6.24-19-generic`

??

But it hasn't fixed my problem

---

### Post by jocko on 2008-08-09
> **davidw89 said:**
> Your instruction is kinda unclear

I have found my kernel number: 2.6.24-19-generic

So what do i do?

I have type this:
sudo apt-get install virtualbox-ose-modules-`uname -r`

or is it:

sudo apt-get install virtualbox-ose-modules-`2.6.24-19-generic`

??

But it hasn't fixed my problem

Unclear? How? I told you to run a very specific command in a terminal, how could that be unclear?
Did ```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```tell you anything? Did it install anything? Did it give you any error? Or did it tell you it was already installed?
Just to clearify: If you type or copy paste the command:```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```_exactly_ as it's written here into a terminal, press enter and enter your password when you are asked to, it will install the correct version for your kernel. The "`uname -r`" part or the command will take care of that.

Another command that you may need to run in order to get the proper permissions to run virtualbox is this:
```
sudo adduser $USER vboxusers
```Just copy the command from the code box, paste it in a terminal and press enter (you don't need to change anything, having "$USER" there will automatically use your username).
Then log out of gnome and log in again.

---

### Post by davidw89 on 2008-08-10
Nope no errors

> david@david-desktop:~$ sudo apt-get install virtualbox-ose-modules-`uname -r`
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  avant-window-navigator-data
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  virtualbox-ose-modules-2.6.24-20-generic
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 327kB of archives.
After this operation, 918kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe virtualbox-ose-modules-2.6.24-20-generic 24.0.5 [327kB]
Fetched 327kB in 2s (115kB/s)                                    
Selecting previously deselected package virtualbox-ose-modules-2.6.24-20-generic.
(Reading database ... 149456 files and directories currently installed.)
Unpacking virtualbox-ose-modules-2.6.24-20-generic (from .../virtualbox-ose-modules-2.6.24-20-generic_24.0.5_i386.deb) ...
Setting up virtualbox-ose-modules-2.6.24-20-generic (24.0.5) ...

david@david-desktop:~$ sudo adduser $USER vboxusers
The user `david' is already a member of `vboxusers'.
david@david-desktop:~$ 


---

### Post by davidw89 on 2008-08-10
I have added some pictures to say thanks ; )
Funny thing is that i will be using this to run off utorrent
lol

[[IMG]http://img355.imageshack.us/img355/2941/screenshotes8.png[/IMG]](http://imageshack.us)
[[IMG]http://img355.imageshack.us/img355/2941/screenshotes8.67f8a1f415.jpg[/IMG]](http://g.imageshack.us/g.php?h=355&i=screenshotes8.png)

Ok working now but Windows XP has no internet??

---

### Post by davidw89 on 2008-08-10
First impression:

Internet not working, if anyone knows how to get it working please post. Host computer is connected WIRED. Also there is no sound!!

Why can i not access the host's hard drive/network.

How do i go to full screen mode (so i an leave it on one of the workstation)

Should i use VMWare and follow that tutorial instead?

---

### Post by cowboyup6983 on 2008-08-22
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}



what does this mean? i cant believe all the trouble i am having installing this application. my god its been a nightmare, windows was so easier! can someone please help.

thanks in advance

---

### Post by cowboyup6983 on 2008-08-22
under user settings i do have my name unlocked! and under group settings for vboxusers and group members there is a check next to my name


so i dont know what else i can do

---

### Post by penguins01 on 2008-08-22
Hi.

So I have this problem too, however, when I type in the termial the line of code used to see the kernal number I get this:

E: Couldn't find package virualbox-ose-modules-uname - r

However, I do have virtual box installed, its worked well for many months, and whenever I got this error VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED)., I could usually fix it by uninstalling and reinstalling virtual box. 

Yet, now that doesn't even work.

Thanks for any possible help.

---

### Post by cowboyup6983 on 2008-08-25
okay i reinstall ubuntu, can someone tell me the correct way to install VirtualBox OSE. I want to be able to run Windows XP Home Edition inside Ubuntu so I can do all my stuff for school. Classes start next week and I want to have my PC completely ready. 

last time i install VirtualBox OSE i got an error message

virtualbox kernel driver not installed.

VBox status code:-1908 (VERR_VM_DRIVER_NOT_INSTALLED).


last time i installed the virtualbox-ose-modules under synaptic package manager, and it installed like 10 other boot options under GRUB

 the  installed something that made me have like over to boot options under the GRUB bootloader

---

### Post by cowboyup6983 on 2008-08-25
i used this site to install VirtualBox

[https://help.ubuntu.com/community/VirtualBox#Open%20Source%20Edition%20on%20Ubuntu%208.04%20(Hardy](https://help.ubuntu.com/community/VirtualBox#Open%20Source%20Edition%20on%20Ubuntu%208.04%20(Hardy))

and ran the command under the terminal, and i got an error:

eldin@dual-core:~$ sudo apt-get install virtualbox-ose virtualbox-ose-source virtualbox-ose-modules-generic
[sudo] password for eldin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages
eldin@dual-core:~$


should i have downloaded something first before running this command?

---

### Post by HemiGTX on 2008-08-26
I had alot of problems with vbox-ose myself, so what i did was go [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

choose the appropriate platform, download the .deb package and install that ay, all should work just fine afterwords.

---

### Post by Tom--d on 2008-08-26
You need to make yourself to the group of vboxusers as well.

Go to:
System > Admin > Users and Groups > Manage Groups > vboxusers > Check 'david' and log out and log in.

Next one is to install the kernel modules for Virtualbox.
I see your on -19 kernel.
Thats simple.
```
sudo apt-get install virtualbox-ose-guest-modules-2.6.24-19-generic
sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic
```

That should do it.

---

### Post by cowboyup6983 on 2008-08-26
> **HemiGTX said:**
> I had alot of problems with vbox-ose myself, so what i did was go [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

choose the appropriate platform, download the .deb package and install that ay, all should work just fine afterwords.

i did this last night, download appropriate version and ran the deb file, then i went into system>admin>user and groups>

click on my name and hit unlock, put in password, then manager groups, and then went down to vboxusers and double click it open and then put in a check mark next to my name, i then rebooted my PC and then under applications and system tools VirtualBox icon was there. 

i was able to install XP without any problems, for thanks everyone, im so happy i got this fixed in time for school next week. thanks again!

---

### Post by Tearstone on 2008-09-10
> **jocko said:**
> More specific? Not sure if that's possible. I'll just repeat what the last poster said:

Install the package virtualbox-ose-modules-XXX matching your kernel. Either find it in synaptic, or use this command in a terminal:
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```

Thank you, that worked great.

---

