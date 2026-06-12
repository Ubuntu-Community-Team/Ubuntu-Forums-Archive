---
title: "How to VMWare Server 2.0 on Ubuntu 8.10"
date: 2008-11-07
forum: Virtualisation
---

### Post by bodhi.zazen on 2008-11-07
[CENTER][FONT=Times New Roman][SIZE=6]Install VMWare Server 2.0 in Ubuntu 8.10[/SIZE][/FONT][/CENTER]
[FONT=Times New Roman]
[CENTER][[IMG]http://tbn0.google.com/images?q=tbn:SalBlZhJj2MeFM:http://www.daniel15.com/blog/wp-content/uploads/2006/09/vmware-2.jpg[/IMG]]("http://www.daniel15.com/blog/wp-content/uploads/2006/09/vmware-2.jpg")
<click image for larger view>[/CENTER]

[SIZE=4]Introduction[/SIZE]

Server 2 installs easily and without any major difficulties. I find it has less features then 1.0.7 (I could not find an option to boot a physical partition for example).

_Advantages_:
[list][*]Nice web interface (yes, I know there is a web interface for 1.0.x).
[*]Easy to install, no patches necessary.[/list]

_Disadvantages_:
[list][*]For some reason it seems slower, more bloated.
[*]Less features.[/list]


[size=4]Installation[/size]

OK, enough, tell us how to install it already :)

[list=number][*]Prep.
```
sudo apt-get install build-essential linux-headers-`uname -r`
```


[*]Download : [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)
[list][*]Be sure to download the appropriate arch for your host (32 vs 64 bit).
[*]Do not forget to get a serial number[/list]

* Personally I save this to ~/src/vmware , you will need to adapt this how-to if you save it elsewhere (ie ~/Desktop).


[*]Extract.

```
cd ~/src/vmware
tar xzvf VMware-server-2*
```


[*]Install.
```
cd vmware-server-distrib
sudo ./vmware-install.pl
```

Unless you know what you are doing, select the defaults.

When you get to the question:

> The current administrative user for VMware Server  is ''.  Would you like to
specify a different administrator? [no]

**[color=blue]Enter "yes" and specify a non-root user. You will log into the web server with this user (using the same password to log onto Ubuntu).[/color]**


[*]Last you will need to configure your keyboard.

Using any editor **make a file** ~/.vmware/config

[indent]The directory ~/.vmware *should* exist, but the "config" file does not.[/indent]

Add the following text (from the VMWare forums): 

```
xkeymap.nokeycodeMap = TRUE 
```

[COLOR="DarkRed"]**WARNING**: The [FONT="Courier New"]'xkeymap.nokeycodeMap = true'[/FONT] configuration breaks the Unity feature on VMWare Workstation! Use the alternate solution below.[/COLOR]

[indent]Old solution (I left this in the event the "new" configuration does not work, **you do not need to do this if the above solution works**).
[indent]```
xkeymap.keycode.108 = 0x138 # Alt_R
 xkeymap.keycode.106 = 0x135 # KP_Divide
 xkeymap.keycode.104 = 0x11c # KP_Enter
 xkeymap.keycode.111 = 0x148 # Up
 xkeymap.keycode.116 = 0x150 # Down
 xkeymap.keycode.113 = 0x14b # Left
 xkeymap.keycode.114 = 0x14d # Right
 xkeymap.keycode.105 = 0x11d # Control_R
 xkeymap.keycode.118 = 0x152 # Insert
 xkeymap.keycode.119 = 0x153 # Delete
 xkeymap.keycode.110 = 0x147 # Home
 xkeymap.keycode.115 = 0x14f # End
 xkeymap.keycode.112 = 0x149 # Prior
 xkeymap.keycode.117 = 0x151 # Next
 xkeymap.keycode.78 = 0x46 # Scroll_Lock
 xkeymap.keycode.127 = 0x100 # Pause
 xkeymap.keycode.133 = 0x15b # Meta_L
 xkeymap.keycode.134 = 0x15c # Meta_R
 xkeymap.keycode.135 = 0x15d # Menu
```

[Thanks nthrbldyblg](http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html)[/Indent][/indent][/list]

[size=4]Run VMWare[/size]

```
sudo /etc/init.d/vmware start|stop|status|restart
```

Open a browse and enter :

```
localhost:8222
```

If you prefer https (you will be redirected automatically to https if you are connecting remotely):

```
localhost:8333
```

Enter your user name and password.

The only caveat is you will need to install a plug in in Firefox (or *gasp* IE) to view the guests on the VMWare console.

**[color=blue]If you wish to access the machines over the Internet you must forward ports 902, 8222, and 8333.**[/color][/font]

---

### Post by rkrishnam_can01 on 2008-11-14
Thanks bodhi.zazen. This post helped me.

---

### Post by handband2 on 2008-11-14
bodhi.zazen thanks.  You beat me too it :)

I would also like to share a script I run to backup my virtual machines.  This script is pieced together from all the other scripts floating around on the web.

---

### Post by bodhi.zazen on 2008-11-14
You are most welcome, glad it worked for you.

---

### Post by dcstar on 2008-11-15
> **bodhi.zazen said:**
> 
.......
Server 2 installs easily and without any major difficulties. I find it has less features then 1.0.7 (I could not find an option to boot a physical partition for example).
.......
_Disadvantages_:
[list][*]For some reason it seems slower, more bloated.
[*]Less features.[/list]
.....
And for anyone that finds 2.0 an unreliable, slow P.O.S. and made the mistake of "upgrading" their VMs before deciding to ditch it, you can actually fix your VMs so they will again run in 1.0.7.

It is just a matter of editing a couple of config files (.vmx and also the .vmdk, if you have it) and making the following lines the value of 4:

```
virtualHW.version = "4"
ddb.virtualHWVersion = "4"
```

---

### Post by handband2 on 2008-11-15
Having problems with permissions of a VM ([COLOR="Red"]error[/COLOR]:  **RuntimeFault: Database temporarily unavailable or has network problems.** )?  I found this on the VMware forums:

- Stop vmware management
```
sudo /etc/init.d/vmware-mgmt stop
```
- Edit vmware management
```
sudo vim /etc/vmware/hostd/authorization.xml
```
- Edit the line that talks about
```
<NextAceId>11</NextAceId>
```
- Incrament it past the current "root" or administrator account you have. So it now reads
```
<NextAceId>12</NextAceId>
```
or to be safe (for many users)
```
<NextAceId>20</NextAceId>
```
- Delete
```
<NextRoleId>11</NextRoleId>
```
- Start vmware management
```
sudo /etc/init.d/vmware-mgmt start
```
-Re-login to VMware Infrastructure Web Access

I hope this will help!

Source:  [http://communities.vmware.com/message/1070373](http://communities.vmware.com/message/1070373)

---

### Post by remy06 on 2008-11-16
Hi bodhi.zazen,

Thanks.Your post helps and managed to fix the keyboard issue.

However,during installation i got the vsock warning.I have a thread here:
[http://ubuntuforums.org/showthread.php?t=975084]("http://ubuntuforums.org/showthread.php?t=975084")

I'm able to complete the installation though,but am wondering if there is any solution for this?

Have also tried the following links and patch but the issue persist:
[http://kramfs.com/2008/07/13/vmware-server-2-unable-to-build-the-vsock-module/]("http://kramfs.com/2008/07/13/vmware-server-2-unable-to-build-the-vsock-module/")
[http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627]("http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627")

---

### Post by bodhi.zazen on 2008-11-16
That is a good question, and no I do not know of a fix.

I read the section that said :

> The VM communication interface socket family is used in conjunction with the VM communication interface to provide a new communication path among guests and host.  The rest of this software provided by **VMware Server is designed to work independently of this feature.**

*Emphasis added by me. I guess I do not use the vsock.

---

### Post by remy06 on 2008-11-16
Hi,

Yup i understood that it is an independent feature and it allows you to access the vmware console?(correct me if im wrong)

Since I've followed your guide without using the patch,I can access my VM via the shortcuts.Perhaps can do without that feature as mentioned.Just curious about getting it to work.

Thanks again for the nice guide.:)

---

### Post by io5150 on 2008-11-17
Last you will need to configure your keyboard.

Using any editor make a file ~/.vmware/config

    The directory ~/.vmware *should* exist, but the "config" file does not.


I have searched throughout the root for the /.vmware directory and can't find it.  I am new to Linux, though and might be missing something (I have inacted the show hidden files).

Thanks
io

---

### Post by bodhi.zazen on 2008-11-17
> **io5150 said:**
> Last you will need to configure your keyboard.

Using any editor make a file ~/.vmware/config

    The directory ~/.vmware *should* exist, but the "config" file does not.


I have searched throughout the root for the /.vmware directory and can't find it.  I am new to Linux, though and might be missing something (I have inacted the show hidden files).

Thanks
io

~ is short hand for your home directory, or /home/username where "username" = your log in name.

---

### Post by thierrybo on 2008-11-17
> **bodhi.zazen said:**
> 

_Disadvantages_:
[list][*]For some reason it seems slower, more bloated.
[

By the way I didn't noticed speed differences running wirtual machines. Do you speak about web interface speed (yes this one is a lot slower than the console) or virtual machines speed?

---

### Post by bodhi.zazen on 2008-11-17
> **thierrybo said:**
> By the way I didn't noticed speed differences running wirtual machines. Do you speak about web interface speed (yes this one is a lot slower than the console) or virtual machines speed?

Both, although the speed of the web interface is most annoying ;).

As you might imagine, I have a "test installation" of 8.10 where I installed and tested all three and, at least on that box, there is a noticeable difference in performance (of the guests) between server 1.0.x and 2.x (it is a 64 bit CPU with enough RAM).

---

### Post by OisinT on 2008-12-01
i'm running into a bit of trouble here

```
oisint@OisinT1:~$ sudo /etc/init.d/vmware start|stop|status|restart
stop: missing job name
Try `stop --help' for more information.
status: missing job name
Try `status --help' for more information.
sudo: /etc/init.d/vmware: command not found
bash: restart: command not found

```

---

### Post by bodhi.zazen on 2008-12-01
> **OisinT said:**
> i'm running into a bit of trouble here

```
oisint@OisinT1:~$ sudo /etc/init.d/vmware start|stop|status|restart
stop: missing job name
Try `stop --help' for more information.
status: missing job name
Try `status --help' for more information.
sudo: /etc/init.d/vmware: command not found
bash: restart: command not found

```

What are you wanting to do ?

The syntax is :

sudo /etc/inti.d/vmware start
sudo /etc/inti.d/vmware stop
sudo /etc/inti.d/vmware restart
sudo /etc/inti.d/vmware status

---

### Post by handband2 on 2008-12-02
There seems to be problems when installing vmware with the new gcc.  If you get the following warning:

```
Your kernel was built with "gcc" version "4.2.3", while you are trying to use
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and
VMware Server may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler
"/usr/bin/gcc" version "4.2.4" anyway? [no]
```

Answer with **Yes**

---

### Post by bodhi.zazen on 2008-12-02
Or set your gcc version ...

[http://ubuntuforums.org/showthread.php?t=65638](http://ubuntuforums.org/showthread.php?t=65638)

---

### Post by ericvw on 2008-12-08
How do you allow multiple users to authenticate and use the UI interface?  I am sure it has to do something with the authorization.xml file, but I can't seem to figure it out.

---

### Post by Hellaxe on 2008-12-10
I have one issue: the keybord doesn't writ all signs like \ or |.
These keys are desable.
Do you know why?
Portuguese keyboard here.
Thanks

---

### Post by bodhi.zazen on 2008-12-10
> **Hellaxe said:**
> I have one issue: the keybord doesn't writ all signs like \ or |.
These keys are desable.
Do you know why?
Portuguese keyboard here.
Thanks

Did you follow the instructions in the first post of this how to?

If so, what did you add to ~/.vmware/config ?

---

### Post by Hellaxe on 2008-12-13
> **bodhi.zazen said:**
> Did you follow the instructions in the first post of this how to?

If so, what did you add to ~/.vmware/config ?

I did exactly as is in the How To:
```
xkeymap.nokeycodeMap = TRUE
```

Only today I had time to check this out.

---

### Post by williec4 on 2008-12-15
Last you will need to configure your keyboard.

Using any editor make a file ~/.vmware/config

The directory ~/.vmware *should* exist, but the "config" file does not.

How do I make a file like this. Please show me step by step.

---

### Post by bodhi.zazen on 2008-12-15
From the command line :

```
gedit ~/.vmware/config
```

Make your edit, save the file.

You can use any editor (vim, nano, emacs, kate ....).

You can make an empty file with touch

```
touch ~/.vmware/config
```

Then naviagate to ~/.vmware (with nautilus) and open the file.

---

### Post by thierrybo on 2008-12-15
I read reports that the "old" solution is better because it does not break the Unity feature. The best place seems to be /etc/vmware/config, not ~/.vmware/config


> **bodhi.zazen said:**
> 

[*]Last you will need to configure your keyboard.

Using any editor **make a file** ~/.vmware/config

[indent]The directory ~/.vmware *should* exist, but the "config" file does not.[/indent]

Add the following text (from the VMWare forums): 

```
xkeymap.nokeycodeMap = TRUE 
```

[COLOR="DarkRed"]**WARNING**: The [FONT="Courier New"]'xkeymap.nokeycodeMap = true'[/FONT] configuration breaks the Unity feature on VMWare Workstation! Use the alternate solution below.[/COLOR]

[indent]Old solution (I left this in the event the "new" configuration does not work, **you do not need to do this if the above solution works**).


---

### Post by williec4 on 2008-12-15
I read reports that the "old" solution is better because it does not break the Unity feature. The best place seems to be /etc/vmware/config, not ~/.vmware/config

Can I do it from any directory or I have to move to some specific folder?

---

### Post by thierrybo on 2008-12-16
> **williec4 said:**
> I read reports that the "old" solution is better because it does not break the Unity feature. The best place seems to be /etc/vmware/config, not ~/.vmware/config

Can I do it from any directory or I have to move to some specific folder?

:-k sorry, don't understand exactly how your question is related to my previous post.

---

### Post by gtdaqua on 2008-12-20
> **bodhi.zazen said:**
> 

[*]Last you will need to configure your keyboard.

Using any editor **make a file** ~/.vmware/config

[indent]The directory ~/.vmware *should* exist, but the "config" file does not.[/indent]

Add the following text (from the VMWare forums): 

```
xkeymap.nokeycodeMap = TRUE 
```


Thanks for this hack. Really need this.

---

### Post by ready2go on 2008-12-22
Hi all,
I am running VMWare Server 2.0 build 122589 on Ubuntu 8.1 64-bit, on an Intel Q6600. VMWare server had been running for some time, then I had an error which stopped all VMs from completing start-up. The error was "Failed to initialize monitor device." I checked around forums and with Google, came to suspect it was because I had KVM libraries installed. I uninstalled KVM, restarted, and the VMs ran.

Recently the VMs all stopped running again with the same error. I don't believe I installed anything 'interesting'. I checked that KVM is not installed, and that Xen is not installed. There is very little information from VMWare corp on how to troubleshoot. I have found a /var/log/vmware/hostd-5.log which collects entries as the VMs start and fail.

There is an entry in this log that says: " on <machine name> in ha-datacenter: The virtualization capability of your processor is already in use. Disable any other running hypervisors before running VMware Server."

I am fairly new to Linux, and am not sure how to confirm what, if any, other virtualization technologies are running.

---

### Post by ready2go on 2008-12-23
> **ready2go said:**
> 
There is an entry in this log that says: " on <machine name> in ha-datacenter: The virtualization capability of your processor is already in use. Disable any other running hypervisors before running VMware Server."

I am fairly new to Linux, and am not sure how to confirm what, if any, other virtualization technologies are running.

Fixed it myself by installing sysv-rc-conf and using it to disable kvm in all run-levels. Surely this can be checked by the VMWare Server install scripts:confused:

---

### Post by mahasmb on 2008-12-23
Umm... can I not run this in a browser? Is there another way to it? I mean when I install Windows XP into it I don't want to be running Windows XP in a browser...

Also, I keep on getting this error whenever I power on the virtual machine:

```
"Power On Virtual Machine" failed to complete

If these problems persist, please contact your system administrator.
DetailsA general system error occurred: Cannot connect to the virtual machine
```

Edit: Nevermind. VMWare has been so very very very tedious to install and set up and I can't even get it to work properly. So I tried VirtualBox... which was honestly a breeze. Why isn't VMWare that easy to install and setup? Plus, my VirtualBox actually works. I've already got Windows XP installed.

So I just have one question. How do I do a complete removal?

---

### Post by handband2 on 2008-12-24
mahasmb,

To remove vmware from your system run the following:
```

sudo /usr/bin/vmware-uninstall

```

---

### Post by mahasmb on 2008-12-28
Thank you.

---

### Post by uomolinux on 2009-01-07
> **handband2 said:**
> bodhi.zazen thanks.  You beat me too it :)

I would also like to share a script I run to backup my virtual machines.  This script is pieced together from all the other scripts floating around on the web.

Hi all!
Could you please tell me how do you use your scripts to backup your machines?
Thank you!

---

### Post by handband2 on 2009-01-07
> **uomolinux said:**
> Hi all!
Could you please tell me how do you use your scripts to backup your machines?
Thank you!
Download the scripts:
```

wget http://handband.net/projects/vmware-scripts.tar.gz

```
Extract the scripts:
```

tar -zxvf vmware-scripts.tar.gz

```
Open up the script to modify
```

gedit vmware-backup.sh

```
**[SIZE="2"]Modify[/SIZE]**
[COLOR="Red"]USER=USERNAME
PASS=PASSWORD
BACKUPDEST=/backup/vmware
DAYS_TO_KEEP_TAR=1[/COLOR]
[INDENT]Notes:
- **USER** and **PASS** has to be the same as the one created when installing VMware Server 2.
- Make sure **BACKUPDEST** goes to an actual location recognized by your computer and has enough space to create the backup.
- **DAYS_TO_KEEP_TAR** is exactly what it says.
- Save changes to file.[/INDENT]

Make the script executable:
```

chmod +x vmware-backup.sh

```
Run the script as sudo or root:
```

sudo ./vmware-backup.sh

```

-----

If you want it to run at scheduled times then insert something like the following in the sudo's crontab:
```

sudo crontab -e

```
```

0 2 * * * /bin/bash [COLOR="Red"]/home/username/vmware-backup.sh[/COLOR] > [COLOR="Red"]/home/username/vmware.log[/COLOR] 2>&1

```

*** Change items in red to the correct locations!**

This will run the script at 2 am everyday and create a log file.

The log file isn't necessary but can be important!  

It is also possible to have the log file emailed (which I can write up a howto if you want?).

---

### Post by uomolinux on 2009-01-09
thank you vary much handband2. I will try your scripts as soon as possible!
Now I have another BIG problem:(
I cannot connect (pass) usb devices to my linux VMs:
- I insert my usb drive, I select the device from whithin the server web interface, but my VMs doesn't see it.
The VM is SMEsever 7.4 (centos based).
The same VM running in a windows version of vmware server 2, works like a charm.
If I connect the device to a windows VM, (on ubuntu vmware server host) works!
This is very strange!!!:confused:

When I plug the pendrive into the server this message appears many times:

[12314123.12341234] sd 7:0:0:0: [sdc] Assuming drive cache: write throug

Have you an idea???

---

### Post by vgrisham on 2009-01-18
Bodhizazen, 

Thanks for this thread. I am now running Windows 7 32 in a VM on Intrepid 64.

---

### Post by dodghz on 2009-01-19
Hi handband2
Just wanted to say thanks. After much searching round the net, comparisons & much deliberation, I used your script to backup the VMs on my headless server here. :KS Clean design & some really nice coding. My script wouldn't have even have come close

Cheers

---

### Post by Jeremiah478 on 2009-01-31
Thanks for the guide, it worked great!

---

### Post by RealG187 on 2009-02-09
I think I will use this since the older one doesn't work in 8.10....

---

### Post by RealG187 on 2009-02-09
I didn't add a user, what can I do, is there a way I can add one after installing?

---

### Post by handband2 on 2009-02-10
> **RealG187 said:**
> I didn't add a user, what can I do, is there a way I can add one after installing?

I think the best thing to do would be to reconfigure your vmware settings:
```
sudo /usr/bin/vmware-config.pl
```

Just in case you need to add more users:
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)
[http://ubuntuforums.org/showpost.php?p=6184638&postcount=6](http://ubuntuforums.org/showpost.php?p=6184638&postcount=6)

---

### Post by RealG187 on 2009-02-12
It runs really bad (like choppy) and the arrow keys don't work (down does the same thing as super)

EDIT: I thin I found  fix
[http://blogs.unbolt.net/index.php/brinley/?blog=5&title=vmware-server-2-0-breaks-keyboard-mappin-10&disp=single&more=1&c=1&tb=1&pb=1](http://blogs.unbolt.net/index.php/brinley/?blog=5&title=vmware-server-2-0-breaks-keyboard-mappin-10&disp=single&more=1&c=1&tb=1&pb=1)

---

### Post by RealG187 on 2009-02-20
How do I connect USB devices? The USB controller says auto connect enabled but I don't see my device.

UPDATE: [http://communities.vmware.com/thread/172689](http://communities.vmware.com/thread/172689)

> I added to /etc/fstab

# USB for VmWare sessions
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
Found the solution, I think I remember I had to do the same thing in 8.04 and 1.0.6

My USB Devices shows up as well as a device called "Chicony CNF7047" what is that?

---

### Post by RealG187 on 2009-02-27
I get a problem when I try to add a new hard drive, it says "Datastore not found"

---

### Post by fishdeamon on 2009-03-16
Im trying to install vw server 2 but i get this message during installation.

```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.27-11-generic/include

The directory of kernel headers (version 2.6.27.10) does not match your running
kernel (version 2.6.27-11-generic).  Even if the module were to compile 
successfully, it would not load into the running kernel.
```

```
~$ uname -r
2.6.27-11-generic
```

Anyone know how to sort this out?

---

### Post by handband2 on 2009-03-16
Update your kernel headers:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Then re-install or update VMware-server:
```
sudo /usr/bin/vmware-config.pl
```

---

### Post by fishdeamon on 2009-03-17
> **handband2 said:**
> Update your kernel headers:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Then re-install or update VMware-server:
```
sudo /usr/bin/vmware-config.pl
```

I have the right headers already, there is just something wrong with them 
```

sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.27-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
```

---

### Post by handband2 on 2009-03-17
It looks like you need to upgrade your system.  Try the following:
```

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get autoremove

```

---

### Post by fishdeamon on 2009-03-17
> **handband2 said:**
> It looks like you need to upgrade your system.  Try the following:
```

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get autoremove

```

It downloaded the new mediacodecs, but nothing else. I tried to reboot and install again but still get same error.

I installed the system from the alternative installtion CD(not the live cd) about 1 week ago.

---

### Post by handband2 on 2009-03-17
Try to install the headers for kernel 2.6.27-11-generic through Synaptic Package Manager.  Check to see if Synaptic Package Manager is checking the backports repository.

Or go download them from here:  
[http://packages.ubuntu.com/intrepid-updates/base/](http://packages.ubuntu.com/intrepid-updates/base/)
[http://packages.ubuntu.com/intrepid-updates/base/linux-headers-lbm-2.6.27-11-generic](http://packages.ubuntu.com/intrepid-updates/base/linux-headers-lbm-2.6.27-11-generic)

---

### Post by fishdeamon on 2009-03-17
> **handband2 said:**
> Try to install the headers for kernel 2.6.27-11-generic through Synaptic Package Manager.  Check to see if Synaptic Package Manager is checking the backports repository.

Or go download them from here:  
[http://packages.ubuntu.com/intrepid-updates/base/](http://packages.ubuntu.com/intrepid-updates/base/)
[http://packages.ubuntu.com/intrepid-updates/base/linux-headers-lbm-2.6.27-11-generic](http://packages.ubuntu.com/intrepid-updates/base/linux-headers-lbm-2.6.27-11-generic)

It worked now. What i did was to enable the proposed repository and that gave me a new kernel.
The vmware installation also detected the path to my headers automatically.

---

### Post by RealG187 on 2009-03-19
Can someone please help me here?:

[http://ubuntuforums.org/showthread.php?t=1094814](http://ubuntuforums.org/showthread.php?t=1094814)

I am having trouble with backing up my VMs due to permissions...

---

### Post by handband2 on 2009-03-19
What is the output of the folder when you run the following:
```

sudo ls -lha

```

Also, you might want to check to see if your hard drive is failing.  

I had an issue in the past that I couldn't backup one section of my VM.  Using [SpinRite]("http://www.grc.com/spinrite.htm") on the disk fixed the drive so I could backup it up to another location.

---

### Post by RealG187 on 2009-03-19
What does ls -lha do?

I don't think it'sa failing drive, everything works fine, just not the VM, I can change the permissons and back up, but then when I try to add a VM it says datastore not found when I try to add a hard drive image,or if I do add one when I run the VM Windows Setup says it cannot find a hard drive installed on my system (not sure about Linux setup)

---

### Post by handband2 on 2009-03-20
RealG187,

The following site should help you out and answer anymore questions you have about VMware Server 2:
[http://www.virtuatopia.com/index.php/VMware_Server_2.0_Essentials](http://www.virtuatopia.com/index.php/VMware_Server_2.0_Essentials)

---

### Post by RealG187 on 2009-03-20
It's not a VMWare problem, it's a Linux Permissions problem

---

### Post by handband2 on 2009-03-21
Try giving VMware folder and the contents the same permission as your VMware administrator account.

```

sudo chown -Rv YourVMwareAdminAccount:YourVMwareAdminAccount /ToYourVMwareLocation

```

Also make sure all the files are at least read and writeable.  The .vmx file needs to read, writeable, and executable.  All the rest just need to be read and writeable.

.vmx file - **rwxr-xr-x**
.log files - **rw-r--r--**
rest of files - **rw-------**

---

### Post by RealG187 on 2009-03-23
My VMWare admin is mpg and the location is /home/mpg/VMWware for this datastore...

---

### Post by slyman1973 on 2009-03-27
One thing I have noticed is that the ~/.vmware folder does not exist until you create a virtual machine, then you can go in and create the config file with the parameters listed earlier.

---

### Post by RealG187 on 2009-03-27
What parameters?

---

### Post by theDaveTheRave on 2009-06-11
Hello all (and particularly to bodhi.zazen).

I've been installing vmware server 2 on my system, running the herron.
```

uname -r 
2.6.24-24-server

```

when I run the pearl install script
```

sudo /usr/bin/vmware-config.pl

```

everything all seems to be going swimmingly, but then I get to this message
```



None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```

So I guess the location of the header files is incorrect for the server version of Hardy?

I'm going to have a quick hunt to see if I can find them, and report back if I can find them or not....

If not does anyone know where they are off hand!?

David.

____________Edit 1______ I'm expecting some more!

ok a quick trawl on the forums shows up this [thread]("http://ubuntuforums.org/showthread.php?t=200156")

Basically I have had to do this command to get the kernel headers
```

apt-cache search `uname -r` | grep headers | awk '{print $1}' | sudo xargs apt-get install -y

```

I'm not sure if this following symlink is required, but I'm going to include it just in case, however I think it may be a requirement if you are just installing the VMware viewer?? not sure though...

```
sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux
```

which all seems more hopefull, so I start the vmware server

```

$ sudo /etc/init.d/vmware start
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed

```

which seem reasonable, as I don't intend to access the internet with the VM, but when I open firefox I still can't acces the web interface?

I've also noticed that I haven't been asked for a username and password during the installation?

any ideas...

David

---

### Post by handband2 on 2009-06-11
theDaveTheRave,

Remember, everytime the kernel gets updated you have to install the new headers.

Try the following:
```

sudo apt-get install build-essential linux-headers-`uname -r`

```
Then
```

sudo /usr/bin/vmware-config.pl

```

---

### Post by theDaveTheRave on 2009-06-11
> **handband2 said:**
> 
Try the following:
```

sudo apt-get install build-essential linux-headers-`uname -r`

```

which is what I think my code did... just in a round about sort of way to make sure that I collected the correct ones..., I just copied and pasted it in from the other thread that I found.


Then
```

sudo /usr/bin/vmware-config.pl

```

which I did...so well spotted... stupidly I forgot to mention it ](*,)

question is, why haven't I been asked for a password at all? so how do I add one post intalation??

and is that why I can't access from the web interface?


David

---

### Post by handband2 on 2009-06-11
The password is set when configuring VMware.  It should be at the end when configuring VMware.
```

sudo /usr/bin/vmware-config.pl

```

---

### Post by theDaveTheRave on 2009-06-16
Sorry I've been a bit quiet over the weekend.....

I've never been asked for a password.... or maybe when I first installed I was and it is picking up the original one that I set.

I've de-installed and re-installed so many times I can't remember what the password is now anyway !  but surely removing the vmWare would remove the passwords also?

I really want to get this working, so any help is hugely appreciated.

what files should I look into for incorrect settings that are stopping the server from working correctly (and the fact I don't have a web interface).

thanks in advance.

David

---

### Post by handband2 on 2009-06-16
theDaveTheRave,

This might answer your question:
> Next is the designation of a user to act as the administrator of the VMware Server environment. When prompted, enter 'y' to configure a different administrator and provide the name of the user to be given administrative access to the VMware Server system. This user's name and system password will subsequently be used to gain access to the management console.

Source:  [http://www.virtuatopia.com/index.php/Installing_VMware_Server_2.0_on_Linux_Systems](http://www.virtuatopia.com/index.php/Installing_VMware_Server_2.0_on_Linux_Systems)

the default user is root but if you want to change it to another user on the system the enter 'y' to add a different administrator.

---

### Post by theDaveTheRave on 2009-06-17
Hello all.

These are all great and helpfull replies... however they don't exactly fit my situation :(

I am unable to get logged into the browser interface of the VMware Server.

I don't know if this is due to an error in my installation, as I can't remember having been asked for an admin password.

However, I can confirm that when I navigate to the required "web page"
```

localhost:8333

```
in firefox, the page doesn't load, I don't get asked for a password or anything at all!

I don't even get an error message.... again not that I can remember - I can't get into the terminal for the moment, so I'm not going to be able to test for a day or so!

My question is this.

The install seemed to go OK, but no requests for an admin password. I did get a message saying "do you wish to use previous settings" with regard to networking etc, to which I responded yes (as I've only ever used the default settings).

If I remove the Vmware server why are these setting retained? how can I remove them manually as I suspect that this may be where I am getting problems?

thanks in advance...

David.

---

### Post by handband2 on 2009-06-17
theDaveTheRave,

I think you need to read my last post again.  You will not be asked for a password.  If you don't configure a different administrator it will use "root" as the main.  I recommend not using root for security reasons.

Here are couple howto's for reference:
[http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-8.10](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-8.10)
[http://howtoforge.org/how-to-install-vmware-server-2-on-ubuntu-9.04](http://howtoforge.org/how-to-install-vmware-server-2-on-ubuntu-9.04)
[http://planetvm.net/blog/?p=330#more-330](http://planetvm.net/blog/?p=330#more-330)

---

### Post by theDaveTheRave on 2009-06-17
handband2

Oh Ok, I'll check it out.

I just remember setting this up on a windows terminal and I remember being  asked for a login name / password ?

I guess it must have been for something else?

David

---

### Post by fsando on 2009-07-02
I use Ubuntu 8.10
I have used vmware server 2 for several months without problems but saw some problems yesterday.

I'm running 
```
Ubuntu 8.10, kernel 2.6.27-14-generic
```
Have also tried to go back doing a full reinstall with patch and all with
```
Ubuntu 8.10, kernel 2.6.27-7-generic
```


I continue to get the following error
```
"Power On Virtual Machine" failed to complete
If these problems persist, please contact your system administrator.
Details
Failed to initialize monitor device. 
```

I have done uninstall, reinstall applied the patch etc. to no avail.

This happens with any of the virtual machines regardless of guest OS

I've spent the last 8 hours trying to find a solution - it has popped up regularly during recent years - only found one old post that seem to imply that someone actually solved it but no solution posted.

Is there a solution to this.

EDIT:

Found the solution by accident:
Tried to install vmware player instead but it complained about kvm being present - I uninstalled kvm and everything went back to normal.

So why did kvm suddently show up? 
Well, I found an article about creating custom VMs with a python script
python-vm-builder
which pulled in kvm

Still vmware server never complained about anything.

---

