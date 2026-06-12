---
title: "HowTo: Windows (XP) on Ubuntu with VMWare Server"
date: 2006-05-27
forum: Tutorials
---

### Post by Peturrr on 2006-05-27
[SIZE=4][B]Update!
[/B]Vmware Server is now in the repositories. (7.10, also 7.04)
See the updated instructions below.
[B]
Introduction[/B]
[/SIZE]Are you too having problems with software that is only available on Windows and not on Linux? Are you still Dual Booting to solve this problem? After this HowTo you will never need to dual-boot again for your windows only software, like Adobe CS!

[SIZE=4][B]Info 
[/B][/SIZE]** That sounds great, but how?**
Did you ever heard about Virtual Machines? There is software available that can run Windows XP or any other Operating System inside your main Operating System. This means that you can run Windows XP in Ubuntu without the need to Reboot/Dual Boot. 

** That sounds slow...**
It is indeed a little slower, but really: a little. Personally I am very willing to sacrifice that little speed in order to avoid Dual Booting.
[B]
What else can I do with it?[/B]
Run seperate Operating Systems for Online Banking and other things that you want to secure. Try out new Ubuntu Versions without Dual Booting, Try out other Linux Distro's etc. 

** What can I not do with it?**
You will not be able to use hardware that doesn't work on Ubuntu. This is very important to understand!
The Virtual Machine runs on top of Ubuntu, so it can only acces Ubuntu detected devices. It is a virtual machine with virtual hardware. 

Also don't expect to be gaming on a Virtual Machine at this moment. Heavy Videocard 3d things are just not supported right now. So for gaming it's unfortunately a no go. For everything else, just try it out!

[SIZE=4]**Requirements**[/SIZE][LIST]
[*]Ubuntu Edgy, Dapper or Breezy or later.
[*]A Windows (XP) Installation CD & Key
[*]Internet Connection (+- 100 Megabyte file download)[/LIST][SIZE=4]**Procedure Gutsy & Feisty**[/SIZE] 

Because VMWare Server is now in the repo's, installation is much easier.[LIST]
[*]Make sure you have enabled the "partner" repository.[LIST]
[*]```
sudo gedit /etc/apt/sources.list
```
[*]Make sure the lines below are not commented out with a #. Save the file.(**replace gutsy with feisty if necessary!**) ```
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
```[/LIST] 
[*]Install VMWare Server[LIST]
[*]```
sudo apt-get update && sudo apt-get install vmware-server
```[/LIST] 
[*]Get your **serial** at [COLOR=YellowGreen][http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)
[/COLOR][/LIST][LIST]
[*]Now skip to the section "**Installation of Windows XP**"[/LIST][SIZE=4]**Procedure Edgy and earlier versions**[/SIZE]
First we need to install a few dependencies:

In a terminal type
```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
``` This will install all needed dependencies (atleast I hope so ;) )

Breezy users will also need to install gcc-3.4. 
```
sudo apt-get install gcc-3.4
```We are now ready to download VMWare Server.[LIST]
[*]Go to [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
[*]On the menu on the right click: Download VMWare Server
[*]Click on the appropriate Download Now button.
[*]Register as new user, do give a valid email adres, since you will be receiving the registration key by email.
[*]Select the VMWare Server beta (for Linux)
[*]Accept the EULA
[*]Download VMware Server for Linux. (first mentioned, binary (.tar.gz) )[/LIST]The Installation[LIST]
[*]Open the downloaded file with the archive manager.
[*]Extract it to somewhere, I will use /tmp here.
[*] Startup the terminal and go to the extracted files 
```
cd /tmp * replace with your download directory*
cd vmware-server-distrib
```[LIST]
[*][LIST]
[*]**Breezy users only.** Execute ```
export CC=/usr/bin/gcc-3.4
```[/LIST] [/LIST] 
[*]Execute the installation script 
```
sudo ./vmware-install.pl
```
[*]You can accept all defaults, only thing you might want to alter is the directory where the Virtual Machines are stored. I have mine set to /home/username/vmware . But offcourse, just accept the settings you want to.
[*]You will be prompted for your key during the installation. You will find the key in your email inbox
[*]If everything went allright, the installation will finish without any problems[/LIST]We can now test if it worked by starting the VMWare server console[LIST]
[*]Via the menu Applications => System Tools => Vmware Server Console
[*] If everything is allright, the server console program will show up.
[*]If it didn't, start the terminal and execute ```
vmware
```This will display the errors, post them here and hopefully we can solve them.[/LIST][SIZE=4]**Installation of Windows XP**[/SIZE]
Next thing we want to do is Install Windows (XP) !

First we need a virtual machine[LIST]
[*] Insert your Windows (XP) CD into your CDROM drive
[*] Open the VMware Server Console
[*] select 'Create a new virtual machine'
[*] => Next => Next => Select Windows Xp (or whatever Windows versions you want to install  )
[*]=> Next => Enter a name and select a location for the Virtual Machine File (It contains the virtual harddisk, so it needs quite some space, min 2 GB, but I would recommend 8+ GB )
[*] => Next => Select Network type. I am using NAT, but choose whatever fits you ( or your mood  )
[*]=> Next => Choose the size for the Virtual Disk and set other preferences
[*] => Next => Finish[/LIST]Now we can start the newly made virtual machine and the install of Windows![LIST]
[*] Start the virtual machine
[*] Hopefully it detects your Windows install CD and will start the installation! If it won't boot from the CD, stop the virtual machine and check/change the preferences for the virtual machine regarding the CD drive
[*] Enjoy the installation and the freedom to use Ubuntu while installing :D[/LIST][SIZE=4][B]
Tips

[/B][/SIZE] You will definately want to install the VMWare tools, when windows has been installed. This will **speed up your Windows responsiveness **[LIST]
[*] Make sure your Windows Virtual Machine is Running and visable/selected. (Not in FullScreen)
[*] Go to the VM menu (on the top in the VM Server Console)
[*]Select Install VMWare Tools. 
This will start a installation wizard in your WIndows Environment. Just install the stuff and you will have better mouse and system responsiveness.[/LIST]CTRL + ALT will **release the mousecursor **from the virtual machine
CTRL + ALT in FullScreen mode will get you **out of the FullScreen**.

You can Suspend a running virtual machine. this way it will start very fast the next time you need it.

To have **sound support**, add a sound device in the virtual machine settings.

**Enjoy!**

See Attached screenshots from my windows XP Installation and the succes of it.

Please no discussions about Windows versus Linux in this Thread.


[B][SIZE=4]Common Problems & Solutions[/SIZE]
[/B][LIST]
[*]No Serial Number Received[/LIST][INDENT][INDENT]You can view your serial numbers at: [http://www.vmware.com/vmwarestore/newstore/serial_number_login.jsp](http://www.vmware.com/vmwarestore/newstore/serial_number_login.jsp)[/INDENT][/INDENT][LIST]
[*]After a kernel upgrade VMWare won't start because it *** has not been (correctly) configured for the running kernel***[/LIST][INDENT][INDENT]execute ```
sudo /usr/bin/vmware-config.pl
```[/INDENT][/INDENT][LIST]
[*]vmware-config.pl fails to find the right kernel headers. **It cannot find /usr/src/kernel/include** and won't proceed to install.[/LIST][INDENT][INDENT]You have a updated kernel, but not the updated kernel headers. 
You can install them by executing ```
sudo apt-get install linux-headers-`uname -r`
``` Now you can succesfully run ```
sudo /usr/bin/vmware-config.pl
```[/INDENT][/INDENT][LIST]
[*]You don't want to install the kernel headers manually each time there is an update.[/LIST][INDENT][INDENT]There is a package called linux-headers-*** that automatically installs the latest kernelheaders, so you don't need to install them manually each time.

There are 4 flavours of this package: 386, 686, k7, server.

If you don't know wich one you need, execute ```
uname -r
``` It will give you something like 2.6.15-26-**k7** or 2.6.15-26-**686**

Now you know the right flavour, install it by ```
sudo apt-get install linux-headers-*****
``` Replace the *** with 386, 686, k7 or server.
    
[/INDENT][/INDENT][LIST]
[*]**Uninstallation failed** and reinstall won't work  
====
A previous installation of VMware software has been detected.
 The previous installation was made by the tar installer (version 3).
 Keeping the tar3 installer database format.
 Error: **Unable to execute "/usr/bin/vmware/vmware-uninstall.pl.**
 Failure
    ** Execution aborted.**
====[/LIST][INDENT][INDENT]Look for the /etc/vmware directory and either move it to a different location or remove it altogether. ```
sudo rm -R /etc/vmware
``` [/INDENT][/INDENT][B]
 [SIZE=4][SIZE=4]Note
[/SIZE][/SIZE][/B]According to Flip314: > VMWare has stated that VMWare Server will be a free product, just like VMWare player. [B]

[SIZE=4][SIZE=4] Credits
[/SIZE] [/SIZE][/B] Used some information from a blogpost by James Wilford and a comment placed there by 'mips' ([http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu](http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu) )
Thanks to Remusus for the linux-headers-'uname -r '  command.
Thanks to firetux for the GCC-3.4 info
Thanks to Nick Couchman from the VMWare forum for the uninstallation problems workaround.

---

### Post by Nomearod on 2006-05-27
Excelent how-to. I heard about VMWare in the past but I thought it was very dificult to install.

For exemple, my wireless card works in windows, so this means that I can use my wireless network in Ubuntu with this? 

Can I install progrms in windows, shutdown the PC, turn on Ubuntu and VMWare and use that programs?

Sorry the n00b questions :rolleyes:

---

### Post by marianoi on 2006-05-27
great guide,

just let me add one thing. If you have the same problem I had with VMWare not starting. You can go to the terminal and type vmware hit enter and see if it claims about "libgcc.s.s0.1" and  "libpng12.so.0" not being recognized. If so, just do the following:

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/

and

sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

For some reason I had problem installing a virtual machine if I ran "vmware" so I always do:

sudo vmware

to run it as a super user (correct me if this is not a good policy please)

Hope this was useful

Cheers

Mariano

---

### Post by Peturrr on 2006-05-27
Thanks for your comments and appreciation.

@nomearod
You won't be able to acces the programs you have already installed on your windows. The virtual windows machine will be a **new** windows install, that only is accesible with VMware software. You cannot boot it directly. you **won't** be able to use your internet in windows if it's not installed in Ubuntu. Also a scanner or other hardware will not run, since it is running above Ubuntu. You will still need to reboot to a real windows for that. Sorry. 
==update== This appears to be not true. It is possible to boot an existing windows installation. This is not covered (yet) in the HOWTO

@marianoi 
Running VMWare as super user doesn't seem be a good practice to me. But If that's the only way for you to start the stuff... So be it.

---

### Post by flip314 on 2006-05-27
[QUOTE=Peturrr]**Note**
Since this is free bèta software, It could be the case that in a few months it will not be free available anymore. In That case, you can always use the free VMWare player to acces your Virtual Machine. 
I wil try to find out if they intend to allow you using the beta software for free.[/QUOTE]

VMWare has stated that VMWare Server will be a free product, just like VMWare player.  They seem to be focussed on selling VMWare Workstation, and want to use Player and Server to get people hooked while competing with other products like VirtualPC.

---

### Post by marianoi on 2006-05-27
It says something about not being able to modify a file (do not remember which one). So I tried with sudo vmware and it started. Now it is working fine

Cheers

---

### Post by mlind on 2006-05-27
Very nice guide, thanks!

I've been keen for some time to try VMWare on Ubuntu, but didn't have nerve to do
it yet.

I guess it's out of question to use already installed XP on VMWare ?

---

### Post by Peturrr on 2006-05-27
[QUOTE=mlind]
I guess it's out of question to use already installed XP on VMWare ?[/QUOTE]

I guess it is for now. It would be very hard to accomplish, but who knows, someday...

---

### Post by flip314 on 2006-05-27
[QUOTE=mlind]I guess it's out of question to use already installed XP on VMWare ?[/QUOTE]

Is [this]("http://macrolinz.com/macrolinz/index.php/2006/01/09/physcial-to-virtual/") what you mean?  I haven't tried it, but it sounds cool.

Has anyone tried the experimental D3D accelleration (possibly only available in VMWare Workstation)?  I'm gonna give it a shot once I get my ati driver issues resolved ](*,)

---

### Post by Nomearod on 2006-05-27
[QUOTE=Peturrr]Thanks for your comments and appreciation.

@nomearod
You won't be able to acces the programs you have already installed on your windows. The virtual windows machine will be a **new** windows install, that only is accesible with VMware software. You cannot boot it directly. you **won't** be able to use your internet in windows if it's not installed in Ubuntu. Also a scanner or other hardware will not run, since it is running above Ubuntu. You will still need to reboot to a real windows for that. Sorry.

[/QUOTE]

For exemple:
- I install Windows XP in Ubuntu with VMWare. Then install in my virtual XP some programs and drives. Can I use then everytime I want ? ( Under ubuntu and with VMWare )

---

### Post by Peturrr on 2006-05-27
> I install Windows XP in Ubuntu with VMWare. Then install in my virtual XP some programs and drives. Can I use then everytime I want ? ( Under ubuntu and with VMWare )
Yes, you can use them everytime you want. You only have to start the virtual windows with the VMware server console. And your windows boots automatically with all the software and documents you have installed, put in it.

---

### Post by Peturrr on 2006-05-27
[QUOTE=flip314]
Has anyone tried the experimental D3D accelleration (possibly only available in VMWare Workstation)?  I'm gonna give it a shot once I get my ati driver issues resolved ](*,)[/QUOTE]

I enabled it according to the guide here: [http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling.html)

DirectX 9 gave indeed: direct3d support enabled (!)
But unfortunately it crashed immediately when I wanted to try the Direct3d test.
It also gave me irritating black area's that didn't got refreshed. But it does look promising.

---

### Post by LsrLine on 2006-05-27
How do I get past this part?

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.
```

---

### Post by Peturrr on 2006-05-27
[QUOTE=LsrLine]How do I get past this part?

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.
```[/QUOTE]

It looks like  the linux-kernel-headers are not installed. 
As mentioned in the howto:
Try to execute:
```
sudo apt-get install linux-headers-2.6.15-23-686 *don't forget to change the 2.6.15-23-686 with the uname -r results *
```
Does it say that it is indeed installed? Hope this helps you.

---

### Post by remusus on 2006-05-27
To avoid any confusion with the linux-headers install, just do this:

```
sudo apt-get install linux-headers-`uname -r`
```

And it will look up the uname in the same command.

.....

Am I the only one that can't get the registration at VMware to work *at all*?

---

### Post by cowmix on 2006-05-27
Don't forget to turn off debug mode so things run A LOT faster:

[http://www.phunsites.ch/wp/2006/03/17/howto-disable-debugging-mode-on-vmware-server-beta/](http://www.phunsites.ch/wp/2006/03/17/howto-disable-debugging-mode-on-vmware-server-beta/)

---

### Post by mdurham on 2006-05-27
If you want a really easy way to create vmx machines for VmPlayer just go to [/http://www.easyvmx.com/]("/http://www.easyvmx.com/")  It's great.

---

### Post by stargazer on 2006-05-28
[QUOTE=marianoi]great guide,

just let me add one thing. If you have the same problem I had with VMWare not starting. You can go to the terminal and type vmware hit enter and see if it claims about "libgcc.s.s0.1" and  "libpng12.so.0" not being recognized. If so, just do the following:

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/

and

sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

For some reason I had problem installing a virtual machine if I ran "vmware" so I always do:

sudo vmware

to run it as a super user (correct me if this is not a good policy please)

Hope this was useful

Cheers

Mariano[/QUOTE]

I had the same problem. You need to change the ownership of the .vmware directory. I just did:

sudo chown -R yourusername:yourusername .vmware

---

### Post by flip314 on 2006-05-28
[QUOTE=Peturrr]I enabled it according to the guide here: [http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling.html)

DirectX 9 gave indeed: direct3d support enabled (!)
But unfortunately it crashed immediately when I wanted to try the Direct3d test.
It also gave me irritating black area's that didn't got refreshed. But it does look promising.[/QUOTE]

I tried it out and it crashes when VMWare tries to resize my resolution when I go to fullscreen.  When I run it windowed, it crashes if I run the D3D test under DXDiag. :( 

Pretty impressive crashes too, they take down my system entirely.  I can't even ctrl+alt+backspace or ctrl+alt+f1 to get around it

---

### Post by Nomearod on 2006-05-28
Why do I need to regist before download VMWare? :-k  Is there any free program like this one?

---

### Post by eokorie on 2006-05-28
You need to do that so they can send you a serial number.

---

### Post by Nomearod on 2006-05-28
[QUOTE=eokorie]You need to do that so they can send you a serial number.[/QUOTE]



But it requires a organization name :-?

---

### Post by eokorie on 2006-05-28
I believe that is just standard for those who plan to pay for support or plan to download the trial versions of paid products but just type in anything.  I entered the name of my website and it went through.

---

### Post by eentonig on 2006-05-28
Help! :mrgreen:

Complaining about GCC 3.4. But I figure it's installed anyway?

> rfonteyn@RFONTE-FCS:~/Programs/VMware/vmware-server-distrib$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
rfonteyn@RFONTE-FCS:~/Programs/VMware/vmware-server-distrib$ apt-cache policy gcc-3.4
gcc-3.4:
  Installed: 3.4.6-1ubuntu2
  Candidate: 3.4.6-1ubuntu2
  Version table:
 *** 3.4.6-1ubuntu2 0
        500 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/main Packages
        100 /var/lib/dpkg/status
rfonteyn@RFONTE-FCS:~/Programs/VMware/vmware-server-distrib$


---

### Post by ortsanfang on 2006-05-28
@ eentonig

As far as I understand the internal secrets of Linux, Dapper uses gcc-4.0. So, before running the installation script, I needed to use the following command (in the terminal):

export CC=/usr/bin/gcc-4.0 

If you're working with Breezy, try this:

export CC=/usr/bin/gcc-3.4

Make this sense? Does that help? I can't say - I only know it worked on my machine.

---

### Post by eentonig on 2006-05-28
I'm on Dapper. And yeah, stupid me. I had the same issue with another soft I installed as well. 

Should have known this one. retrying as we, hum,  *speak*.

---

### Post by eentonig on 2006-05-28
ortsanfang, 
Nope, no good.
Still got the same errors.

> rfonteyn@RFONTE-FCS:~/Programs/VMware/vmware-server-distrib$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)


---

### Post by ortsanfang on 2006-05-28
eentonig, I followed this instruction: [VMware Server Beta on Ubuntu]("http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu")

Maybe you need to create the mentioned (see first comment) symbolic link - although I didn't need to create it.

---

### Post by eentonig on 2006-05-28
Nope, doesn't help. link already existed. 
It's gonna be someting stupid and simple. I just wish I could figure it out.

---

### Post by ortsanfang on 2006-05-28
I'm not sure, but do you get the messages when starting vmware (or during the installtion)? What about the installation? Did it finish successfully? Any errors? Do you have a vmware log in the /temp directory?

I just want to figure out when the first time in the hole process you went into trouble?

---

### Post by eokorie on 2006-05-28
I have always used this to install VMware Server and its worked every single time:

```

sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4 xinetd xserver-xorg libxt6 libxrender1 libxtst6 libxi6 libdb2 openssl libssl-dev mc htop ssh

```

Once all the libraries have been installed, all I do is start the VMware installer.

Hope this helps....

---

### Post by paul cooke on 2006-05-28
[QUOTE=mdurham]If you want a really easy way to create vmx machines for VmPlayer just go to [/http://www.easyvmx.com/]("/http://www.easyvmx.com/")  It's great.[/QUOTE]

borked link... takes you here [http://www.microsoft.com/](http://www.microsoft.com/) prolly cos Microsoft have bought up the "http" domain and parked a redirect link there to take people to microsoft.com... devious beggars

what you want is [www.easyvmx.com](www.easyvmx.com)

---

### Post by eentonig on 2006-05-28
Well, 

As you can see from the output, It's after launching vmware. The install works just fine without any errors.

I'll give it another try with the packages from eokorie's post. Allthough a bunch of them seem useluss ballast to me.

---

### Post by firetux on 2006-05-28
eentonig, have a look at [this]("http://www.ubuntuforums.org/showthread.php?t=157011") thread.

---

### Post by marianoi on 2006-05-28
rfonteyn@RFONTE-FCS:~/Programs/VMware/vmware-server-distrib$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
rfonteyn@RFONTE-FCS:~/Programs/VMware/vmware-server-distrib$ apt-cache policy gcc-3.4
gcc-3.4:
Installed: 3.4.6-1ubuntu2
Candidate: 3.4.6-1ubuntu2
Version table:
*** 3.4.6-1ubuntu2 0
500 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/main Packages
100 /var/lib/dpkg/status
rfonteyn@RFONTE-FCS:~/Programs/VMware/vmware-server-distrib$

[B]Hello,

I had that problem and posted the solution here. It is in the 1st page!

Cheers

Hope that works for you too[/B]

---

### Post by firetux on 2006-05-28
[QUOTE=marianoi]rfonteyn@RFONTE-FCS:~/Programs/VMware/vmware-server-distrib$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
rfonteyn@RFONTE-FCS:~/Programs/VMware/vmware-server-distrib$ apt-cache policy gcc-3.4
gcc-3.4:
Installed: 3.4.6-1ubuntu2
Candidate: 3.4.6-1ubuntu2
Version table:
*** 3.4.6-1ubuntu2 0
500 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/main Packages
100 /var/lib/dpkg/status
rfonteyn@RFONTE-FCS:~/Programs/VMware/vmware-server-distrib$

[B]Hello,

I had that problem and posted the solution here. It is in the 1st page!

Cheers

Hope that works for you too[/B][/QUOTE]


Yeah, but that involves running vmware with root, wich is not a good idea.
The link in my first post has a better solution.

---

### Post by paul cooke on 2006-05-28
[QUOTE=Peturrr][...]

We are now ready to download VMWare Server.
[LIST]
[*]Go to [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
[*]On the menu on the right click: Download VMWare Server
[*]Click on the appropriate Download Now button.
[*]Register as new user, do give a valid email adres, since you will be receiving the registration key by email.
[*]Select the VMWare Server beta (for Linux)
[*]Accept the EULA
[*]Download VMware Server for Linux. (first mentioned, binary (.tar.gz) )
[/LIST][/QUOTE]

what happens after the beta period finishes? cos it's not obvious from the email I got with my serial numbers:

|Use the serial number(s) provided below to install and run multiple copies of VMware Server during the beta period:

will vmware server remain free of cost?

---

### Post by Nomearod on 2006-05-28
[QUOTE=paul cooke]what happens after the beta period finishes? cos it's not obvious from the email I got with my serial numbers:

|Use the serial number(s) provided below to install and run multiple copies of VMware Server during the beta period:

will vmware server remain free of cost?[/QUOTE]


That's what I'd like to know... 

What did you put in the "company" field? ](*,)

---

### Post by firetux on 2006-05-28
[QUOTE=paul cooke]what happens after the beta period finishes? cos it's not obvious from the email I got with my serial numbers:

|Use the serial number(s) provided below to install and run multiple copies of VMware Server during the beta period:

will vmware server remain free of cost?[/QUOTE]

It stays free, anyway it says so in the [FAQ]("http://www.vmware.com/products/server/faqs.html").

---

### Post by sYs^ on 2006-05-28
I have no sound, only the speaker beeps, I have NForce 2 integrated soundcard, any ideas? Btw great guide everything else if working fine!

EDIT: Problem solved, I didn't add manualy a Sound Device. :p

---

### Post by jrobinson5 on 2006-05-28
Tried to follow the steps on breezy. It didn't work, tried to run the installation script again, same error. Here's what I cut and pasted from Terminal. (see attached.)

---

### Post by Video Toaster on 2006-05-28
[QUOTE=paul cooke]borked link... takes you here [http://www.microsoft.com/](http://www.microsoft.com/) prolly cos Microsoft have bought up the "http" domain and parked a redirect link there to take people to microsoft.com... devious beggars

what you want is [www.easyvmx.com](www.easyvmx.com)[/QUOTE]
Nah... I just tried that link in MSIE and it just says "Cannot Find Server".  Firefox redirects to Microsoft's web page by itself.

---

### Post by firetux on 2006-05-28
[QUOTE=jrobinson5]Tried to follow the steps on breezy. It didn't work, tried to run the installation script again, same error. Here's what I cut and pasted from Terminal. (see attached.)[/QUOTE]

Why did you press "n"? Doing this terminates the install.
Just press "y", and go on. There's nothing wrong with compiling, it needs to be compiled because vmware doen't support ubuntu as an host-os.

EDIT: sorry I didn't read the whole thing.Anyway.

Just makee sure you have gcc3.4 installed and do ```
export CC=/usr/bin/gcc-3.4
``` before you execute the command.

---

### Post by paul cooke on 2006-05-28
[QUOTE=Nomearod]That's what I'd like to know... 

What did you put in the "company" field? ](*,)[/QUOTE]

erm... my own company name... I have a sideline business that involves fixing borked ms-windows boxes... quite profitable... I only do referrals.

You know you can put n/a in that field...

[OT aside here. Please DO NOT reply to this]

If they let me, they end up with an Ubuntu dual boot setup with Ubuntu for browsing and ms-windows for their other stuff. Otherwise, I leave them with a Knoppix cd and show them how to browse the web with it (saving data to USB key drives  (setup as a persistent home)) and do Gaim for IM etc.. I have had some call backs to install Linux properly after they've had a play with Knoppix. I've even had people call me back and let me know they've gone off and installed Linux themselves.

---

### Post by Peturrr on 2006-05-28
[QUOTE=jrobinson5]Tried to follow the steps on breezy. It didn't work, tried to run the installation script again, same error. Here's what I cut and pasted from Terminal. (see attached.)[/QUOTE]
The log says it cannot compile because the wrong gcc is used. This is easily solved.
**for breezy users**
You will need to enter this first before starting the install script:
```
export CC=/usr/bin/gcc-3.4
```
Also make sure that gcc-3.4  is indeed installed
```
sudo apt-get install gcc-3.4
```

---

### Post by marianoi on 2006-05-28
Hi I just got the answer for not running VMWare as root...:-D 

after copying the libgcc and libpng files as I explained in the first page do the following:

sudo chmod 777 /home/"your home directory"/.vmware/preferences

It works for me now I just type in the terminal:

"vmware"

And vmware starts

Cheers

Mariano

---

### Post by John Jones on 2006-05-28
Excellent post!

Very clear and it all worked first time.

All I have to do now is work out how to connect to the internet some time in the next 30 days so I can activate XP.

You are definitely a :KS .

John Jones :-D

---

### Post by dicecca112 on 2006-05-28
I followed your guide but it failed.  All I get is this 

A previous installation of VMware software has been detected.

Failure

Execution aborted.

dicecca@dicecca-desktop:~/Desktop/vmware-server-distrib$


This is a 2 day old install of dapper.  I believe i have everything I need installed

---

### Post by flip314 on 2006-05-28
[QUOTE=dicecca112]I followed your guide but it failed.  All I get is this 

A previous installation of VMware software has been detected.

Failure

Execution aborted.

dicecca@dicecca-desktop:~/Desktop/vmware-server-distrib$


This is a 2 day old install of dapper.  I believe i have everything I need installed[/QUOTE]

Do you have another VMWare product installed?  You can't have VMPlayer and VMServer on the same machine.  I don't know about workstation.

If you want to clean out any other products you can run /usr/bin/vmware-uninstall.pl.

If the errors are caused by a failed previous installation attempt, I don't know if that script will be there/work, but you can try anyway.

---

### Post by rafaelsdmf on 2006-05-28
Hey man! excelent post! This is my first post and I'm kind of newbie to all this but i'ts nice to see this community. It's great to be part of this.

Ok here's my problem: The installation went Ok, the only thing that bothers me is that I have to run the program from the directory itself because I go "vmware" in the console and nothing happens. It says that there is no such command. 

Anyway, I start the program and make the virtual machine and try to install Win Me, and it seems that I don't have the keyboard available.

Any clue on this?

PS: sorry about my english... I'm working on that too :)
[I]
edit:[/I] I'ts ok now!!!just have to click on the screen of the virtual machine. I'ts installing right now and I'll keep you informed.

Long Live Rock 'n Roll!!!

---

### Post by dicecca112 on 2006-05-28
got it to work.  I had to reinstall Ubuntu anyway, and installed the newest RC, and I have it up and working thanks for the guide

---

### Post by rafaelsdmf on 2006-05-29
Works perfect !!! Just one question: Is it safe to surf the 'net? :-k

---

### Post by eentonig on 2006-05-29
[QUOTE=firetux]eentonig, have a look at [this]("http://www.ubuntuforums.org/showthread.php?t=157011") thread.[/QUOTE]

Works like a charm, Thanks!

---

### Post by Video Toaster on 2006-05-29
[QUOTE=rafaelsdmf]Works perfect !!! Just one question: Is it safe to surf the 'net? :-k[/QUOTE]
Mostly.  :D  Just make sure you run Microsoft Update in the virtual machine each month to make sure you're up-to-date (or turn on Automatic Updates, if you wish).  Using Firefox instead of IE in the virtual machine would also be a good idea.

---

### Post by ampop on 2006-05-29
With this help, finnally I installed the VMware workstation.
Thank you very much.

Just one question. I just give 2GB to the virtual win XP. It's possible give more, or I must reinstall the virtual Win XP?

Thank you.

---

### Post by centered effect on 2006-05-29
Is it possible to uninstall VMware?

EDIT - yes it is

```
sudo vmware-uninstall.pl
``` 
I need a working keyboard.. my damn F8 key doesnt want to work....


NEW EDIT - Damn logitech keyboards, they have F-lock keys to use the function keys, plus I had to redo vmware anyway cause I put the Virtual Machines in /var/lib

Thanks for this how to!!!

---

### Post by Grog140 on 2006-05-29
I get 

Details: Failed to execute child process "vmware" (No such file or directory)

When trying to launch from Applications menue and get a "command not found when I do "vmware" from terminal.

I don't know where to begin tyring to figure this one out.

---

### Post by Symbios on 2006-05-30
Great guide. Everything worked great, except for one little problem, (something about GCC_3.4 not being found) but [marianoi's post]("http://www.ubuntuforums.org/showpost.php?p=1058964&postcount=3") quickly fixed that.

EDIT: Just found another little problem, when I try to go into full screen mode, I get this message: 

"Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.

Failed to switch to full screen SVGA mode."

What exactly is it tellling me to do here?

---

### Post by evand on 2006-05-30
maybe a stupid question -

how do you set it up so you have a shared folder/drive between a vmware windows xp (guest) install and your ubuntu (host) system?

the howto worked like a charm, but for this to be useful i'll need a way to transfer files.... probably really easy answer, but it's late...

---

### Post by jontxo on 2006-05-30
to share files from vmware windows with linux you only have to set up shared folders on windows. Then from nautilus go to archive -> connect with server.

to share folders from linux with vmware windows  you have to right click on a folder and select share folder with smb. In general configuration of the files shared with windows select the name you want for you computer but for the workgroup put MSHOME, and select not to use a wins server.
then you have to add an user to samba, with the command: 
sudo smbpasswd -a user_name
After that in windows go to net folders and there you will see on the microsoft windows net the workgroup of the folders you have shared.

---

### Post by evand on 2006-05-30
thanks, that did it.

also, thanks to everyone. great thread. i think i finally solved my "i still need windows for AutoCAD" problem....

---

### Post by fingal12 on 2006-05-30
Hi, how do I uninstall it? 

Thanks

---

### Post by Peturrr on 2006-05-30
[QUOTE=fingal12]Hi, how do I uninstall it? 

Thanks[/QUOTE]
The answer was posted a few posts above you.
In the same directory you ran the instal script, run : sudo vmware-uninstall.pl

---

### Post by fingal12 on 2006-05-30
Thanks for your answer
i tried that, nothing happend.

---

### Post by lulin on 2006-05-30
Following the instructions I get this when trying to start vmware:
> roger@lulin:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Using log file /tmp/vmware-roger/ui-8316.log
Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Stopp and _Stopp
Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Vor and _Vor
Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Informationen and Informationen
*** glibc detected *** free(): invalid pointer: 0x09302b78 ***

---

### Post by bluenova on 2006-05-30
Worked perfectly, thanks! (But installed xubuntu RC instead of windoze :D)

---

### Post by evand on 2006-05-30
out of curiosity, is it possible to run mac osx (for intel chip) as a virtual machine? i'm thinking about buying a macbook later this year, it'd be nice to check out the OS first, to be sure I don't want a (cheaper) pc....

---

### Post by lime4x4 on 2006-05-31
i'm having the same problem here with installing vmserver on a 4 day old install of ubuntu/dapper and i don't have vmplayer installed
john@ubuntu:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

i also don't have a vm folder in /usr/bin

---

### Post by Grog140 on 2006-05-31
Has anyone seriously tested the performance you get with this? Or is it not even worth doing the requires a great deal of resources?

(Looking for a better alternative to Windows for World of Warcraft. Wine seems sluggish. I am thinking this isn't going to do the trick...)

---

### Post by Mr. Picklesworth on 2006-05-31
Awesome...
Thanks for the tutorial!

I'm going to show this off to my anti-OperatingSytems brother (he routinely despises Linux, Mac OS and Windows... sometimes at the same time)... ASAP!
He'll either be trembling with anger at having to look at Windoze and Linux in the same frame, or amazed by this application. (Yes, I realize it's possible from any OS, but it's only fun in Ubuntu).

---

### Post by Peturrr on 2006-06-01
[QUOTE=Grog140]Has anyone seriously tested the performance you get with this? Or is it not even worth doing the requires a great deal of resources?

(Looking for a better alternative to Windows for World of Warcraft. Wine seems sluggish. I am thinking this isn't going to do the trick...)[/QUOTE]

I don't think it's ready for gaming. At least not the server version. They are working on integrating Direct Rendering in the VMWare Workstation, so you have really almost the same 3d power in your Virtual machine as in your native environment.

---

### Post by Rackerz on 2006-06-02
darren@darren:~$ cd ~/Desktop
darren@darren:~/Desktop$ cd vmware-server-distrib
darren@darren:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
Password:
A previous installation of VMware software has been detected.

Failure

Execution aborted.

darren@darren:~/Desktop/vmware-server-distrib$

What the hell? I haven't even got vmware installed.

---

### Post by chinaski on 2006-06-02
thanks a lot Peturrr this howto worked perfectly for me! ;)

---

### Post by goahead on 2006-06-02
Sweet guide, perfect for a linux newbie like me..

Now i can remove my orginal xp installation and skip the dual boot thingy..

---

### Post by Whimar on 2006-06-03
Is there any way to get a file i save in my VMware session out into linux?

Basically i want to create documents in my windows VM then carry them across onto my dapper installation.

Thanks!

---

### Post by Rackerz on 2006-06-03
Ok no problems now, thanks it installed perfectly!

---

### Post by chinaski on 2006-06-03
[QUOTE=Whimar]Is there any way to get a file i save in my VMware session out into linux?

Basically i want to create documents in my windows VM then carry them across onto my dapper installation.

Thanks![/QUOTE]
hello, for me simple copy&paste works

---

### Post by Whimar on 2006-06-03
[QUOTE=chinaski]hello, for me simple copy&paste works[/QUOTE]

Mhmm not working for me sadly, also is there any way to get a 1920x1200 resolution for the windows graphics driver.  Its got pretty much every res except that one

---

### Post by Hellaxe on 2006-06-03
Try with the windows network and copy it to dapper

---

### Post by kassetra on 2006-06-03
[quote=Whimar]Is there any way to get a file i save in my VMware session out into linux?

Basically i want to create documents in my windows VM then carry them across onto my dapper installation.

Thanks![/quote]

In my version, under Virtual Machine Setting -> Options, I setup "shared folders" and then setup which folders I wanted my VMWare session to have access to.

Then, it's simply in the network on windows.

---

### Post by mervg on 2006-06-03
This post removed due to author's finally getting things right.:-#

However, when I completed the installation ov VMWare, and entered 'vmware' in the terminal, I got:
   
         *vmware: command not found*

Any thoughts, anyone?

---

### Post by bigken on 2006-06-04
Thanks for the how to  worked a treat  loaded winxp will also be trying win 2000
& win 98se :D

---

### Post by cjm5229 on 2006-06-04
Worked great to set up, but I have 3 issues I can't seem to get. My Windows guest will not recognize my USB ports, so no printer, no  Ipod, no thumbdrive. and I can't transfer files between Ubuntu and Windows, Copy and Paste doesn't work, and I can't get  networking to work.  There is no place in VM  to set shares,  and  Connecting to server in ubuntu doesn't show vmware. Leaves me no way to move documents between systems, Strangely I can access my Wifes computer (Ubuntu) and My Youngest son's Computer (PCLinux) and even my Oldest son's computer (WinXP), from guest Win, just can't get to my own. 3rd problem is no sound. I'm going through vmware's docs to see if I can find solutions,  I used to have WinXP in vmpayer on Breezy and things worked well so I might try setting that one up later. I see VMplayer in Repo's, so that can be installed through apt-get.

---

### Post by Whimar on 2006-06-04
[QUOTE=cjm5229]Worked great to set up, but I have 3 issues I can't seem to get. My Windows guest will not recognize my USB ports, so no printer, no  Ipod, no thumbdrive. and I can't transfer files between Ubuntu and Windows, Copy and Paste doesn't work, and I can't get  networking to work.  There is no place in VM  to set shares,  and  Connecting to server in ubuntu doesn't show vmware. Leaves me no way to move documents between systems, Strangely I can access my Wifes computer (Ubuntu) and My Youngest son's Computer (PCLinux) and even my Oldest son's computer (WinXP), from guest Win, just can't get to my own. 3rd problem is no sound. I'm going through vmware's docs to see if I can find solutions,  I used to have WinXP in vmpayer on Breezy and things worked well so I might try setting that one up later. I see VMplayer in Repo's, so that can be installed through apt-get.[/QUOTE]#

What type of ethernet device did you set up? Bridged or vpn?  I'm having the same issues. I can access all my network shares on either operating system, except for the shares on the host and vm system.

Also what benefits are there of Player over server?

And does anyone know how to set the resolution to 1920x1200?

Thanks!

---

### Post by cjm5229 on 2006-06-04
[quote=Whimar]#

What type of ethernet device did you set up? Bridged or vpn?  I'm having the same issues. I can access all my network shares on either operating system, except for the shares on the host and vm system.

Also what benefits are there of Player over server?

And does anyone know how to set the resolution to 1920x1200?

Thanks![/quote]
Bridged.

I don't know if there are any benifits, I haven't used it for quite a while. I do seem to recall it was easy to enable sound, just click a button. and USB support worked. I'm not sure I was able to move files without using my USB Thumb Drive though.

---

### Post by cjm5229 on 2006-06-04
Well, the Player is easy to install, Applications>Add/Remove>VMware Player, check box, click apply,  go to [www.easyvmx.com]("http://www.easyvmx.com"), create your vmx file, follow the tutorial,  (4 steps,all easy) install Windows and it's up and running. USB ports work , and sound can be enabled with a click. Only have Windows half installed yet so don't know about file sharing, but I can use my thumbdrive to transfer files if necessary.
:D

I now have Player up and running w/ WinXP installed. I looked through my settings and I don't see any screen resolutions for 1920x1200 either. There is a 1920x1440, My guess would be Either Windows doesn't support it, or the Install disks we are using don't support it. I think with player at least, just use one that comes close since it is only using part of the screen anyway.

---

### Post by mervg on 2006-06-04
Anyone able to point me to the solution for this:  after the successful (it said) install, when I try to run VMware Server Console, I get "failed to execute child process 'vmware' No such file or directory". I have the files in / in a vmware directory.

---

### Post by spockrock on 2006-06-04
I had also had the following problem;
```

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

```

and as fire tuxpointed out this fixed it
```

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/

```

thanks for the how to.

---

### Post by Peturrr on 2006-06-04
Hey guys,

Thanks for all the positive feedback.
I will look into the problems people are facing in this thread and hope to respond with the solutions I find tomorrow.

---

### Post by GhandiBurger on 2006-06-04
Will Windows games work on it? and how much slower will they be?

---

### Post by Omission on 2006-06-04
OK everything installed fine, and I wacked in my Windows CD and the DOS Style installer all kicked in, selecting my partition etc and it started to copy files. After so long the screen simply goes blank, despite the HDD and CDROM icons still flashing.

I did a screen capture and low and behold the windows XP installation is there in the screen capture.. just not appearing on my screen in real time. Pressing ENTER lets me interact sucessfully with the installation ( Subsequent Screen Captures prove this). Its just not Displaying.

I'm running XGL and Compiz with an ATI card and I Imagine this is my problem, I'm just confused to why the DOS Style installation would appear but then go blank when the Graphical installer kicks in... anyone got any ideas?:-k

Edit: To add to the irony i've just installed VMware Player and loaded the virtual machine created by VMW Server and it actually works. Seems strange how it displays with the player but not within the server app.

---

### Post by mervg on 2006-06-05
Here is some additional info re: vmware command/directory not found. Don't know if this will help. 
Merv

 [Error msg I get is - after the successful (it said) install, when I try to run VMware Server Console, I get "failed to execute child process 'vmware' No such file or directory".



Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up bcm43xx-fwcutter (20060108-6build1) ...

Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Sq322 on 2006-06-05
[QUOTE=Peturrr]Thanks for your comments and appreciation.

@nomearod
You won't be able to acces the programs you have already installed on your windows. The virtual windows machine will be a **new** windows install, that only is accesible with VMware software. You cannot boot it directly. you **won't** be able to use your internet in windows if it's not installed in Ubuntu. Also a scanner or other hardware will not run, since it is running above Ubuntu. You will still need to reboot to a real windows for that. Sorry.
[/QUOTE]

@Peturrr...sorry to rehash...just to clarify. this will NOT allow me to access programs installed in a current windows ?
Is there anything that will allow for that ??

---

### Post by Peturrr on 2006-06-05
[QUOTE=Sq322]@Peturrr...sorry to rehash...just to clarify. this will NOT allow me to access programs installed in a current windows ?
Is there anything that will allow for that ??[/QUOTE]
This will indeed NOT allow you to acces programs installed in a current windows. It allows you to install a completely clean windows, that can be used without rebooting your pc.

 I don't know of any software that can do that, but maybe you should have a look at the vmware site. I guess they will offer such software (but offcourse that will cost you $$ )

---

### Post by Sq322 on 2006-06-05
[QUOTE=Peturrr]This will indeed NOT allow you to acces programs installed in a current windows. It allows you to install a completely clean windows, that can be used without rebooting your pc.

 I don't know of any software that can do that, but maybe you should have a look at the vmware site. I guess they will offer such software (but offcourse that will cost you $$ )[/QUOTE]
thx for the info, it seems that there is a way to use the vmware workstation to do this but it involves configuring a dual boot computer for use ...
ARGH !!
reinstalling my programs presents a time consuming nightmare for me :(

---

### Post by irv on 2006-06-05
Following this How To I get to the point of executing the install scrip and I get:

irv@ubuntu:~/DownLoads/vmware/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

Which is telling me I have a previous installed VMware, but I am not sure how to remove it?
I don't remember installing it. I did install VMware player from the package manager, but completely remove it before starting this install. Where do I go from here?

---

### Post by Anonimoes on 2006-06-05
This is a great howto! The only problem I am having is that the virtual machine doesn't want to power up, I get the error message:

Unable to change virtual machine power state: The process exited with an error:
End of error message.

I didn't install windows xp yet so the machine is completely empty. Of course I tried different cd-rom drives, etc. Does anyone have an idea about how to get past this?

---

### Post by irv on 2006-06-05
I couldn't get it installed on my fast machine so I install it on my 800Mhz with 300+ MB RAM, but windows took forever to load and it ran way to slow so I removed it. I want to uninstall VMware from two machines, and I tried sudo vmware-uninstall.pl, and it goes through the motions, but it dosen't seem to uninstall it.
Has anyone got any idea how to get it off my systems?
Thanks.

---

### Post by evand on 2006-06-05
(in win xp on vmware server on dapper)

anyone have any tips on how to -

1 - get an ipod working (w/ itunes)? ubuntu and VMWare Server both recognise the ipod, and I can "check" it under the usb devices menu. It shows up in winxp as a generic "USB Mass Storage Device."  No luck with it so far. It'd be nice to have itunes. nothing in linux is quite "there" yet (gtkpod is workable but dissappointing, and rhythmbox would be awesome, if you could actually transfer files)


2 - tweak the graphics speed? nvidea card, and I don't need any 3D games, but it would be nice to speed up AutoCAD, Photoshop, and Sketchup, which are really what i need this for right now.

still kind of frustrating because from powered off, to boot into ubuntu and load winxp in vmware is *quicker* than i've ever had winxp boot up natively, and to not have to deal with spyware and assorted windows annoyances is a dream, but the slight lag in graphics rendering is ](*,)

---

### Post by bluevoodoo1 on 2006-06-05
[QUOTE=irv]Following this How To I get to the point of executing the install scrip and I get:

irv@ubuntu:~/DownLoads/vmware/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

Which is telling me I have a previous installed VMware, but I am not sure how to remove it?
I don't remember installing it. I did install VMware player from the package manager, but completely remove it before starting this install. Where do I go from here?[/QUOTE]


Does anyone have any ideas how to remedy this?

---

### Post by poyner on 2006-06-06
[QUOTE=bluevoodoo1]Does anyone have any ideas how to remedy this?[/QUOTE]
yes I also had this problem. the problem was a directory that was left on the computer after the uninstall. I can't remember exactly but I think it might have been /etc/vmware Once I removed this directory (and the single file within it called 'locations' ) the install continued file. Try this

sudo rm -r /etc/vmware

---

### Post by dorts on 2006-06-06
Follow this tutorial. Work great!! Including the Internet. Now, is there a way to transfer data from the Xp in VMware to my ubuntu? Because I use photoshop in the XP. (I find GIMP hard to use and lacking some features.)

---

### Post by givré on 2006-06-06
What is the difference in performence between vmplayer and vmware server?

---

### Post by givré on 2006-06-06
[QUOTE=dorts]Follow this tutorial. Work great!! Including the Internet. Now, is there a way to transfer data from the Xp in VMware to my ubuntu? Because I use photoshop in the XP. (I find GIMP hard to use and lacking some features.)[/QUOTE]
You will have to share them via samba

---

### Post by Sq322 on 2006-06-06
givre...does that mean via samba i can use vmware to access programs on my existing XP install?

---

### Post by givré on 2006-06-06
[QUOTE=Sq322]givre...does that mean via samba i can use vmware to access programs on my existing XP install?[/QUOTE]
Yeh sq322, what a surprise, you are everywhere :cool: 
I guess you could be able to run some apps (never try it), but remember that you are limited by a 10Mb transfer (vmware virtuallize a real network card), so i guess it will not work well for a majority of apps (you can run at least notpad or paint :rolleyes: ).

---

### Post by Sq322 on 2006-06-06
[QUOTE=givré]Yeh sq322, what a surprise, you are everywhere :cool: 
I guess you could be able to run some apps (never try it), but remember that you are limited by a 10Mb transfer (vmware virtuallize a real network card), so i guess it will not work well for a majority of apps (you can run at least notpad or paint :rolleyes: ).[/QUOTE]

almost as many places as you are :wink: \
Thx again for the 411

---

### Post by tmastran on 2006-06-06
I've installed everything but when I run vmware I can not create a virtual machine. The only option in the GUI is to "Connect to a host". Most all other VMWare Server Console GUI options are greyed out. I tried running "vmware" as root but this did not do anything.

Any ideas what to look for?

I'm running the latest Ubuntu. I have no problem with other applications or compiling/installing in general.

---

### Post by dorts on 2006-06-06
Can anyone help me with samba? How do you share files with my vmware Xp and ubuntu?

---

### Post by crouton on 2006-06-06
givré: VMWare server is more full-featured, VMPlayer is intended for demos and self-contained images.

tmastran - VMServer requires that you 'connect' to the Server management console.  You can choose to connect to 'localhost' using your normal username and password.

dorts - There are various threads about Samba, that will work for your XP virtual machine.  It will need an IP address obviously, so make sure that the virtual machine has a network card 'installed'.

If you select the VMXNet driver, you should be able to 'set up' a 1Gbps network card.  The added benefit of having virtual machines on the same host machine is that the host machine's network card is never actually utilized - file transfers and such actually occur at FSB speeds.  The limiting factor will be the speed of the host machine HD, as it will be saturated transferring files long before the network card throughput is saturated.

---

### Post by Fedcer on 2006-06-06
Thanks, great how-to! it worked perfectly here !

---

### Post by bigken on 2006-06-06
[QUOTE=tmastran]I've installed everything but when I run vmware I can not create a virtual machine. The only option in the GUI is to "Connect to a host". Most all other VMWare Server Console GUI options are greyed out. I tried running "vmware" as root but this did not do anything.

Any ideas what to look for?

I'm running the latest Ubuntu. I have no problem with other applications or compiling/installing in general.[/QUOTE]

So connect to the host then create your VM the host is ubuntu :wink:

---

### Post by tmastran on 2006-06-06
[QUOTE=
tmastran - VMServer requires that you 'connect' to the Server management console.  You can choose to connect to 'localhost' using your normal username and password.
[/QUOTE]

Thanks! And thanks to the author for a great tutorial.

---

### Post by aktiwers on 2006-06-06
Thanks for the guide, worked out great.

Wow.. its running as windows would normally! I was expecting lags and slowdowns, but it runs like a dream! 

Anyone tested Games through this?

---

### Post by rgcrowley on 2006-06-06
[QUOTE=Peturrr]Thanks for your comments and appreciation.

@nomearod
You won't be able to acces the programs you have already installed on your windows. The virtual windows machine will be a **new** windows install, that only is accesible with VMware software. You cannot boot it directly. you **won't** be able to use your internet in windows if it's not installed in Ubuntu. Also a scanner or other hardware will not run, since it is running above Ubuntu. You will still need to reboot to a real windows for that. Sorry.

@marianoi 
Running VMWare as super user doesn't seem be a good practice to me. But If that's the only way for you to start the stuff... So be it.[/QUOTE]

I've used both a Visioneer XP100 scanner and a Fujitsu Scansnap with vmware and they both worked ok.  My experience is that vmware worked great except for having to shut down printing from linux in order to print from vmware.  

Win4lin works fine for printing from both linux and windows at the same time but does not work with the usb scanners.  It is also a bit slower than vmware.  But both get the job done for me.

---

### Post by frozen chosen on 2006-06-06
Problem : could not open/dev/vmnet8:no such file or directory,vitual device ethernet0 will start disconnected
 This is what I get when i start xp in VM Ubuntu Dapper, I also installed windows Me and get the same error .
 Newbie in over head  please throw rope. And Thank You in advance Frozen.

---

### Post by bluevoodoo1 on 2006-06-06
[QUOTE=poyner]yes I also had this problem. the problem was a directory that was left on the computer after the uninstall. I can't remember exactly but I think it might have been /etc/vmware Once I removed this directory (and the single file within it called 'locations' ) the install continued file. Try this

sudo rm -r /etc/vmware[/QUOTE]


Thank you, that did it!

---

### Post by Anonimoes on 2006-06-07
[QUOTE=Anonimoes]This is a great howto! The only problem I am having is that the virtual machine doesn't want to power up, I get the error message:

Unable to change virtual machine power state: The process exited with an error:
End of error message.

I didn't install windows xp yet so the machine is completely empty. Of course I tried different cd-rom drives, etc. Does anyone have an idea about how to get past this?[/QUOTE]

Anyone?

---

### Post by OneSeventeen on 2006-06-07
Awsome!

I have dual monitors and the left monitor has XP running nearly full screen (full screen blocks out the ability to move the mouse to this screen)

If there is a way to run it at full screen on one monitor while still allowing me to move my mouse to the other, please let me know, otherwise this is still really awsome!

Also, I accepted all defaults.  When I tried to add it to /home/oneseventeen/vmware it said "vmware" could not be found...
So going with the defaults makes things insanely easy.

**EDIT**: I can't seem to get USB devices to show up...  is there any way to share files between the VM and Ubuntu?

---

### Post by mervg on 2006-06-07
I cleaned up the files from the first failed attempt to install vmware-server, started again, and everything went fine until this. I am new enough at Linux (Ubuntu) to not understand what is needed. /tmp/vmware-config0 exisits with /vmnet-only in it, and if the 'includeCheck.h' should be there - it isn't. So, how would it be created and is there anything I can/should do?

Sure would like to get this running.

[U]make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
[B]Warning: could not open /tmp/vmware-config0/vmnet-only/includeCheck.h: Invalid argument
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".[/B][/U]

Execution aborted.

---

### Post by pepijn on 2006-06-08
[QUOTE=Peturrr]

**Requirements**[LIST]
[*]Ubuntu Dapper or Breezy
[*]A Windows XP Installation CD & Key
[*]Internet Connection (+- 100 Megabyte file download)
[*]**i386 pc!!!! (amd/intel)**[/LIST]
[/QUOTE]

thank's for the howto, worked great on my pc.

Now this might be something everyone else knows, but I didn't.  where i tested all installing ubuntu + vmware server on my pc, I tried to do the same on my   powerbook G4. It took me the whole day to get the HFS+ partition resized & ubuntu properly installed (yes, newbee) to find out that vmware server doesn't support the G4 processor. So Ubuntu-ppc users, don't be fooled... ](*,) 

> 
Before running VMware Server for the first time, you need to configure it by
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this
program to invoke the command for you now? [yes]

Your processor does not support the ^cpuid instruction. VMware Server will not
run on this system.

Your /proc/cpuinfo is:

processor          : 0
cpu                    : 7410, altivec supported
temperature     : 56-58 C (uncalibrated)
clock                  : 500.000000MHz
revision               : 0.3 (pvr 800c 1103)
bogomips            : 49.79
timebase              : 24966218
machine              : PowerBook3,2
motherboard       : PowerBook3,2 MacRISC2 MacRISC Power Macintosh
detected as             : 71 (PowerBook Titanium)
pmac flags             : 0000001b
L2 cache               : 1024K unified
pmac-generation   : NewWorld
Execution aborted.


---

### Post by shuttleworthwannabe on 2006-06-08
Ok Noob here so please bear with me.

1. My Ubuntu partition hda7 is about 7.51GB (4.47GB free). I have both root and home on this. The rest of my hdd has (hda1=WinXP, hda5=FAT32, hda6=MEPIS 6, hda8=SWAP, hda9=Kubuntu 6.06). During the VMWare installation, I want to put the Virtual XP on hda7 home directory.

Q's:
- What instructions should i type to VMware where to place the new XP: hda7/root/home/user/winxp [I will have to create a folder in home called winxp]??
- Is this space enough (4.51GB) for basic XP install? Then, I will be installing in this Virtual XP: Office2003 (1G), EndNote (50MB), SAS Statistical Software (700MB), SUN JRE 1.4 (180MB), SPSS statistical software (700MB), others (smaller programs)
- Now how would be installing all these programs in the Virtual XP? Do I just follow the same procedures as if I were in XP???
- Once the virtual XP is set up within Ubuntu, and I have launched the VMware window and selected WinXP OS, how does it know it has to boot up? IS this a stupid question? I am assuming that once in VMWare, XP feels and looks like the original XP??? right?

Thanks I am about to give it a try...wish me luck...! Oh, but first I have to track the stupid XP key ..is it on the OEM dics or should I just flip my laptop and check underneath it???

Many thanks, Peturr this is very helpful Regards,
swb

---

### Post by shuttleworthwannabe on 2006-06-08
Great stuff. I just installed VMW and XP on to my hda7 (I allocated 2G only for starters). The basic install took 1.99G. All went effortlessly.
 
Just 1 problem. I used the OEM supplied XP CD, and was not asked about the CD key. But the annoying thing is that it keeps pestering me to Activate and when I plugin the key it does not recognize it all. Any way to overcome this.
 
I do not have sound: I am assuming we have to install the drivers?? or will it not recognize that?? Do I have to configure thi sin VMWare to tell it what audio devices to check??
 
 
I am wrting this thro IE6..yes, I know. But now I can have my Stats packaes running in Linux and do not have to boot!
 
Thanks,
swb

---

### Post by AModlin on 2006-06-08
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)

This is when I run "vmware"  I have GCC 3.4 and 4.0 installed could that be the problem?

---

### Post by AModlin on 2006-06-08
Tried to reinstall and getting this error:

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.15-23-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
/usr/src/linux-headers-2.6.15-23-386/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.15-23-386/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
make[2]: gcc: Command not found
/tmp/vmware-config4/vmmon-only/Makefile:89: *** Inappropriate build environment: you wanted to use gcc version 4.0.3 while kernel attempts to use gcc version .
/tmp/vmware-config4/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc with symbolic link to /usr/bin/gcc-4.0.  Stop.
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

No idea why I'm getting it though.

---

### Post by darknuala on 2006-06-08
Is it possible to use your cd burner in this?  I installed Nero 6, but it only shows a virtual device.  And is sound possible?

---

### Post by shuttleworthwannabe on 2006-06-09
[quote=shuttleworthwannabe]Great stuff. I just installed VMW and XP on to my hda7 (I allocated 2G only for starters). The basic install took 1.99G. All went effortlessly.
 
Just 1 problem. I used the OEM supplied XP CD, and was not asked about the CD key. But the annoying thing is that it keeps pestering me to Activate and when I plugin the key it does not recognize it all. Any way to overcome this.
 
I do not have sound: I am assuming we have to install the drivers?? or will it not recognize that?? Do I have to configure thi sin VMWare to tell it what audio devices to check??
 
 
I am wrting this thro IE6..yes, I know. But now I can have my Stats packaes running in Linux and do not have to boot!
 
Thanks,
swb[/quote] 
Ok, hi there.
2 issues:

1. How do I get the Activation process bypassed. I have OEM cd. CD key from the COA back of laptop is not accepted. I ecen tried Telephone, but the sweet lady, told me that the installation ID was not valid.
2. Get sound going. Currently, no sound at all. Device not detected. EDIT: I got this working by goign into vm settings and adding sound card. works fine , though a bit poor sound.

---

### Post by blokus2006 on 2006-06-09
I get and error message when i try to install vmware. I am using a G4 Processor in a Mac Mini. the error message is:

Your processor does not support the ^cpuid instruction. VMware Server will not
run on this system.

Your /proc/cpuinfo is:

processor       : 0
cpu             : 7447A, altivec supported
clock           : 1333.333328MHz
revision        : 0.5 (pvr 8003 0105)
bogomips        : 82.94
timebase        : 41600571
machine         : PowerMac10,2
motherboard     : PowerMac10,2 MacRISC3 Power Macintosh
detected as     : 287 (Unknown Intrepid-based)
pmac flags      : 00000000
L2 cache        : 512K unified
pmac-generation : NewWorld
Execution aborted.



What should i do?

---

### Post by shuttleworthwannabe on 2006-06-09
[quote=darknuala]Is it possible to use your cd burner in this?  I installed Nero 6, but it only shows a virtual device.  And is sound possible?[/quote] 
Sound: check my post below [your post], and above as sq322 puts it below.. ;-)

---

### Post by Sq322 on 2006-06-09
[QUOTE=shuttleworthwannabe]Sound: check my post below[/QUOTE]
U mean your post above :D 

sorry its Friday..couldnt resist

---

### Post by Kure on 2006-06-09
I am not quite sure about Linux, but I just _successfully_ booted running Windows XP in vmware (I mean while running one OS I booted from physical disk partition the _same_ OS+version+apps+everything in vmware).

To do so, while selecting the disc you want to use, do not select “Create new virtual disk” or “Use an existing disk”, but select “Use a physical disk”.

Select the drive you want, preferably the whole partition. I have Grub, therefore it is not possible for me to tell whether the original Microsoft installer would boot.

No excuses for not using Linux now, because this should remove the installation hassle.

---

### Post by Sq322 on 2006-06-09
[QUOTE=Kure]I am not quite sure about Linux, but I just _successfully_ booted running Windows XP in vmware (I mean while running one OS I booted from physical disk partition the _same_ OS+version+apps+everything in vmware).

To do so, while selecting the disc you want to use, do not select &#8220;Create new virtual disk&#8221; or &#8220;Use an existing disk&#8221;, but select &#8220;Use a physical disk&#8221;.

Select the drive you want, preferably the whole partition. I have Grub, therefore it is not possible for me to tell whether the original Microsoft installer would boot.

No excuses for not using Linux now, because this should remove the installation hassle.[/QUOTE]
In short, this means i could boot from my existing C: drive on the partition that windows is installed?Thus keeping my data in tact and not have to start on a fresh VMWare OS installation
If this is for real Im Done!..No more windows ever....
Which VMWare product did you use.

---

### Post by Kure on 2006-06-09
[QUOTE=Sq322]In short, this means i could boot from my existing C: drive on the partition that windows is installed?Thus keeping my data in tact and not have to start on a fresh VMWare OS installation
If this is for real Im Done!..No more windows ever....
Which VMWare product did you use.[/QUOTE]

I had Vmware workstation demo under my XP, right now I am installing Vmware server in Ubuntu... should be done in less than 30 minutes (if something like gcc versions doesn't screw up).

And yes, this means you should be able to run your "old version" with all apps. However, I am still not sure what bootloader you need to do so - I have Grub on MBR.

---

### Post by Kure on 2006-06-09
OK, it BOOTS CORRECTLY.

I am using

[LIST]
Ubuntu Dapper Drake 6.06 LTS[/LIST]
[LIST]2.6.15-23-k7 kernel[/LIST]
[LIST]gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)[/LIST]
[LIST]vmware server 1.0.0 build-24927[/LIST]
[LIST]Grub in MBR[/LIST]
[LIST]Windows XP[/LIST]


... and it works - I haven't tested any real applications yet nor know I how it would affect the Windows installation - at least it may ruin it and you may not be able to boot back to bare windows again because of huge amounts of generic drivers installed by vmware.

---

### Post by Kure on 2006-06-09
VMware tools installation works.

Sometimes while one OS uses the harddisk on "low level" e.g. Windows installing drivers to IDE can block the second OS from working (Aptitute).

---

### Post by Kure on 2006-06-09
... even sound + **video** playback works

---

### Post by nero2150 on 2006-06-09
How do I add guest mode to etc/X11/XF86Config 
If not xorg.conf for ubuntu am i right. #-o  
What do you need to put in the section screen /subsection display  :confused:

---

### Post by shuttleworthwannabe on 2006-06-09
[quote=Kure]OK, it BOOTS CORRECTLY.
 
I am using
[LIST]
[*]
Ubuntu Dapper Drake 6.06 LTS[/LIST][LIST]
[*]2.6.15-23-k7 kernel[/LIST][LIST]
[*]gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)[/LIST][LIST]
[*]vmware server 1.0.0 build-24927[/LIST][LIST]
[*]Grub in MBR[/LIST][LIST]
[*]Windows XP[/LIST] 
 
... and it works - I haven't tested any real applications yet nor know I how it would affect the Windows installation - at least it may ruin it and you may not be able to boot back to bare windows again because of huge amounts of generic drivers installed by vmware.[/quote]
 
I tried vmware to boot native WinXp on /dev/hda1. It picks up the GRUB menu, and I can choose WInXP, but the boot process halts unexpectedly. I tried twice, then gave up (lest I get my system hosed)..Th e goo d thing is that I can boot safely into my WINXP.
 
I also tried a WINXP i had on a previous laptop hdd (that is now sitting in a USB casing). It does not recognize the /dev/sda for some reason.
 
But I by mistake had a USB memory stick in one of the USB port, and vmware picked tha up thinkling that there was an OS to boot. but obviously did not as this is a data USB stick.
 
Interesting

---

### Post by gharz on 2006-06-11
i've been looking for the previous posts who experience the same problem with mine...

A previous installation of VMware software has been detected.

Failure

Execution aborted.

but i don't see any answer how to fix it.

initially, i installed vmware-player from synaptic until i found this forum. i removed vmware-player again from synaptic (complete removal) but i'm still getting the same message.

hope you could help me. i don't want to re-install my ubuntu because of this error message. i want my ubuntu to be the default OS on my laptop. windows is too bloated.

please help.

---

### Post by gharz on 2006-06-11
guys,

i was able to install vmware.

i didn't see the previous post... it was just a simple rm -r /etc/vmware that made my day.

enjoy!

---

### Post by Sq322 on 2006-06-11
[QUOTE=Kure]OK, it BOOTS CORRECTLY.

I am using

[LIST]
Ubuntu Dapper Drake 6.06 LTS[/LIST]
[LIST]2.6.15-23-k7 kernel[/LIST]
[LIST]gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)[/LIST]
[LIST]vmware server 1.0.0 build-24927[/LIST]
[LIST]Grub in MBR[/LIST]
[LIST]Windows XP[/LIST]


... and it works - I haven't tested any real applications yet nor know I how it would affect the Windows installation - at least it may ruin it and you may not be able to boot back to bare windows again because of huge amounts of generic drivers installed by vmware.[/QUOTE]
First of all this is very good news for me at least
2 questions, 
1)did you get a chance to try and boot direct to windows from startup to see if it caused any ill effects on the windows install.
2) is there any reason that you would not be able to map to a network directory under VMWare while running windows ?

---

### Post by kloshar on 2006-06-11
When I want to power on my Windows 98 virtual OS, it says the error: No bootable CD, floppy or hard disk was detected. I wonder how, if I can boot from CD rom normally and run Windows 98 from startup boot. :confused: :confused: :confused:  Maybe the problem is that windows are very old and I should use win Xp. :confused: :confused:

---

### Post by djsroknrol on 2006-06-11
Thanks...I've learned alot and was just about to wipe my MS partition, when I had a foul up and had to reinstall VMware server...

I'd be really cautious about loading anything important on it untill this "beta period" stuff is sorted out...do they hope to continue providing this as a "free" product AFTER the expiration date in Help>About ?

---

### Post by skinner on 2006-06-11
Hi... ive installed vmware succesfully, and tried it... working perfect... but i have  a question about this program. i have windows XP installed in another partition before deleting it and using vmware for the programs i need in windows... i would like to know if it is possible to run the installation of windows xp i have allready installed in another partition with VMWARE... i meen... if its posible to run the OS i have installed in the partition... no creating and installing an OS with vmware. Thanx

---

### Post by stairwayoflight on 2006-06-11
hi,

i have an emachines pc, that came with a "system restore disk" containing the os and some other crap. at one point i tried to reinstall windows, but on boot it would not install it. i got a console mode, and poked around, found a disk image and a prog by symantec, 'ghost' or something like that. i'm pretty sure it formatted my drive to put windowz on it.

i'd love to play around with vmware--qemu does it too right. maybe even dual boot again for games.. anyways i don't want to lost my ubuntu installation. i'd rather run it in a virtual machine anyways, screw the games, nothings secure anyways. i think in a vm it can't access my ext3 filesystem right?

---

### Post by xxrealmsxx on 2006-06-12
I get this error when I try to install windows:

see attached.

---

### Post by Sq322 on 2006-06-12
[QUOTE=skinner]Hi... ive installed vmware succesfully, and tried it... working perfect... but i have  a question about this program. i have windows XP installed in another partition before deleting it and using vmware for the programs i need in windows... i would like to know if it is possible to run the installation of windows xp i have allready installed in another partition with VMWARE... i meen... if its posible to run the OS i have installed in the partition... no creating and installing an OS with vmware. Thanx[/QUOTE]
Scroll back a few pages to where KURE speaks about having done this

---

### Post by mms on 2006-06-12
it worked for me, except that my application -> system tools -> vmware link doesn't work. I get this error: Failed to execute child process "vmware" (No such file or directory)

I can start from the vmware file in Home/vmware, though.  Does anyone know how I can fix that link?

---

### Post by xxrealmsxx on 2006-06-12
Is it possible to install Windows Xp off of a .iso on the harddrive? I mounted a winxp cd and it does not recognize it.

---

### Post by Billquinn1 on 2006-06-13
This guy has a guide useing Vista beta and pulls it from the iso.

[http://ubuntuforums.org/showthread.php?t=192328&highlight=vista+vmware](http://ubuntuforums.org/showthread.php?t=192328&highlight=vista+vmware)

Bill

---

### Post by xxrealmsxx on 2006-06-13
[QUOTE=Billquinn1]This guy has a guide useing Vista beta and pulls it from the iso.

[http://ubuntuforums.org/showthread.php?t=192328&highlight=vista+vmware](http://ubuntuforums.org/showthread.php?t=192328&highlight=vista+vmware)

Bill[/QUOTE]


It worked, thanks!

---

### Post by John Jones on 2006-06-13
I tried this HOWTO a few weeks ago, and it worked perfectly.

Then my system started behaving oddly and I re-installed from scratch. I've just spent a frustrating hour trying to re-download VMWare Server, and I just end up going round in circles; i.e. click on "First Time Download", log in, click on VMWare Server and end up back on the page with "First Time Download". Am I missing something? Or have VMWare just re-vamped their website?

Can somebody help, please?

Cheers,

John Jones ](*,)

---

### Post by drdnl on 2006-06-13
Guy above me, cookies? 

Just wanted to say thanks alot! One of the last few ties to Windows have succesfully been cut (Office and Mediamonkey), all that is left is gaming....

Again, thnx alot for a great howto
Regards
D

---

### Post by InDenial on 2006-06-13
Hi all,

I just installed Ubuntu 6.06 TLS and vmware in which I installed Windows XP.

I have one serious issue regarding my setup.

I have an MSI Mega Book s270 laptop. The resolution of the screen is 1280 * 800 in the host operating system.

first thing I would like to know: Is it possible to let Windows XP within VM detect that I have an LCD screen?.. (Right now the refreshrate is set to 85 Hz, which should be 60) The reason it is set to 85 Hz is because Windows XP sees a default monitor which I can not change.

Second thing I hope someone can help me with is: How do I make it so that I can use the resolution 1280 * 800. I tried changing some settings in the preferences file but this had not effect.  I also changed:

pref.placement.top to 0
pref.placement.right to 1280
pref.placement.bottom to 800

I also tried changing some settings regaring the autoadjustment of the vmware screen to the host screen. This too did not work.

Thanks in advance

[SIZE="5"]SOLVED MY PROBLEM:[/SIZE]
This seemed to be a XGL/Compiz problem. But I made it work and for the people that visit this thread for installing vmware on ubuntu using XGL/Compiz this is what I did:

I got it working. right now I have in front of me (actually to the left of me) a laptop running ubuntu 6.06 LTS 32 bit running XGL/COmpiz Vmware with an XP guest running in FULLSCREEN on a 1280 * 800 
resolution.

I can not exactly say which changes made it work right now, since I tried a lot of different things. I suggest trying one at a time.

**Setup**

Ubuntu 6.06 TLS
VMware server 1.0.0
Windows XP home
XGL/Compiz

ATI Radeon Express 200M
running the fglrx-driver (latest)

**VMware settings**

Edit | Preferenes | Display
Autofit window true
AutoFit guest true

**Changes I made**

**_.vmare/preferences file_**

Besides the changes mentioned earlier in the post about the placements I changed:
```

pref.autoFitFullScreen = "FitHostToGuest"
```
to
```

pref.autoFitFullScreen = "FitGuestToHost"
```
I am not sure where I got this idea from but this had as a result that pressing the Full Screen button did not give an error anymore and went fullscreen. The problem now was that the desktop of Windows XP did not extend all the way to the sides of the screen. So if before pressing the full screen button the desktop had a resolution of 800 * 600 it would have the same resolution after pressing fullscreen.

**_/etc/X11/xorg.conf_**

I think this is what did the trick. I remembered from another thread about installing the ATI drivers that there was something in there about setting the LVDS. [HOW TO: ATI Drivers v0.2 (Revised)]("http://www.ubuntuforums.org/showthread.php?t=24557&pp=10"). I added the following line since I have a laptop:

```

Option		"MonitorLayout"	"LVDS, STV"
```

---

### Post by Dilligaf on 2006-06-13
Can windows in vmware write to ntfs partitions???
Can I boot my Windows install partition if it's ntfs??
Has anyone tried or an I the guinea pig??

Mike

---

### Post by ShiftyPowers on 2006-06-14
this HOWTO was fantastic, works like a charm, no more rebooting in order to simply use Excel.  THANKS!

---

### Post by kloshar on 2006-06-14
Hi!

First of all, thank you for this excellent howto.

Secondly, I have a problem. :D When I press "Power on", virtual machine doesn't start my Windows XP, but automatically boot the cd and starts windows Xp installation. :confused: How to convience it to get automatically into Windows?

Thanx, 
Peter

---

### Post by kloshar on 2006-06-14
I have installed Windows before Linux so I want to skip that installation progress and go directly to Windows.

---

### Post by Ve33iE on 2006-06-14
Hey guys 
i just asking if there is any way for making windows xp find the nvidia drivers because its using the VGA driver for windows and its a bit laggy some times ?

Sorry if i sound like a noob only installed this like few hours ago :P hehe

---

### Post by RedBowers on 2006-06-14
Excellent how to! Had VMware up and running in no time. Thanks Peturrr

---

### Post by InDenial on 2006-06-14
[QUOTE=Ve33iE]Hey guys 
i just asking if there is any way for making windows xp find the nvidia drivers because its using the VGA driver for windows and its a bit laggy some times ?

Sorry if i sound like a noob only installed this like few hours ago :P hehe[/QUOTE]

Not possible. Vmware uses the vmware drivers. Did you install vmware tools ?

---

### Post by kloshar on 2006-06-14
One question more ... 

I've installed Windows XP (formated previous version during installation) and used it normally. But how the things go on boot? Are there any problems as if I installed windows XP normally? I'm now really afraid of turning off computer, because I had so many problems with partitions lately. :D

---

### Post by kloshar on 2006-06-15
I've upgraded the kernel and now vmware shows an error:

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

I do the /usr/bin/vmware-config.pl command, but it stops at:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

Could you advice me what to do? My kernel is  2.6.16.20.

---

### Post by kloshar on 2006-06-15
Please, I really need this. :-(

---

### Post by kloshar on 2006-06-15
OK, I found out the solution. I suppose it has already been told, but it doesn't metter.

**How to configure VMware after upgrading Kernel**

1. Conditions:
sudo apt-get install buld-essential (GCC& so on)

2. You have to know the version of kernel:
uname -r 

3. apt-cache search linux-headers

4. sudo apt-get install linux-headers-(your kernel version)

5. /usr/bin/vmware-config.pl


Bye!

---

### Post by pdwalpole on 2006-06-15
What an excellent howto -- thank you so much. I followed the instructions closely and installed the VMWare server and Windows XP without a hitch. I have dual-booted into Windows for a couple of reference tools that I enjoy and could not get to work under Wine -- the complete New Yorker magazine on DVD and the OED version 3.1 on cdrom, and both work just fine under VMWare. I am one very happy (and grateful) camper.

---

### Post by mr_static on 2006-06-16
Another way to turn off debugging/logging to improve performance in VMware Server beta, from the same blogger referenced in a previous post in this thread.

Not sure how much difference it makes, but there it is.

[http://www.phunsites.ch/wp/2006/05/14/another-way-to-disable-debugging-in-vmware-server-beta/](http://www.phunsites.ch/wp/2006/05/14/another-way-to-disable-debugging-in-vmware-server-beta/)

And thanks for the howto, very useful :)

---

### Post by kloshar on 2006-06-16
How to exchange files between linux and windows as virtual os? Is it hard to get files from windows?

---

### Post by steveneddy on 2006-06-18
**Nevermind**I read the man pages for VMware. It was easy. Please forgive this premature post. -SE

[QUOTE=Peturrr]

To have sound support, add a sound device in the virtual machine settings.

[/QUOTE]

OK - Could you tell me where I go to get sound while on my VM? I have Win2K running successfully on my Dapper and it seems pretty good. It is actually very acceptable, especially after ther VMware Tools installation. But I would like to have sound. 

Thanks in advance - SE

**I was gonna add a screen shot, but it is on the Ubuntu Home folder - silly me**(it does look very nice)

**I am posting from VMware and Win2k, actually**

---

### Post by bigken on 2006-06-18
In vmwae go to inventory right click guest OS and select settings the select add
this will give options to add sound usb ect ;)

---

### Post by E-Jey on 2006-06-18
How could I exchange data between my virtual machine and my host OS. I've installed VMware tools and when I drag and drop files in to my virtual machine I get this error: 

Unable to open: Virtual machine "/home/erik/Desktop/file.extension" is not in the inventory. 

How could I solve this?

---

### Post by renwklo on 2006-06-18
This feature currently only support Windows host to Windows client, that means you cannot drag and drop your file to the virtual machine if one of your host or client is not Windows.

To solve this, you can use Samba or FTP to share files between your host and client.:D

---

### Post by Se[BBB]e on 2006-06-18
The installation doesnt work. It says "command not found" when I type "vmware". The menu entry says the same. The installation was successful, though.

---

### Post by Somenoob on 2006-06-18
Great "how to", I am daily constantly switching operating systems due to games.

---

### Post by DAaaMan64 on 2006-06-18
What is the secret to getting usb to work?  I have it activated along with sound, but I get nothing, I have tried all my ports... Is there something else I can test?

EDIT; I just read the instructions :p, you go to VM -> Removable Devices -> Select the device.  The vmware will connect it for you! Awesome!

---

### Post by Se[BBB]e on 2006-06-19
[QUOTE='Se[BBB]e']The installation doesnt work. It says "command not found" when I type "vmware". The menu entry says the same. The installation was successful, though.[/QUOTE]
I solved my own problem so Ill post the solution if anyone wants to hear... Writing wmware wont work, and neither will the menu entry. But when I go to the place where I told vmware to install (/home/sebbe/vmware) and click vmware, it starts.

---

### Post by toLa` on 2006-06-19
VMWare is an awesome program -- I learnt the basics of Linux in a virtual machine using VMWare Workstation running in Windows.

With help from your guide I managed to get VMWare Workstation installed under Ubuntu using the new Kernel (I was getting stuck at the vmmon compiler missing, specify a location for a C compiler), and your guide (installing the dependencies / gc) seemed to do the job!

Thanks!

---

### Post by kloshar on 2006-06-19
Hello! I have a problem here.

I've opened VMware as root (thought to change some settings) and now vmware server shows error when I want to open it as normal user: 

Unable to add virtual machine "/home/xxx/vmware/Windows XP Professional/Windows XP Professional.vmx" to the inventory: No permission to perform this operation

What to do?

Edit: SInce I opened wmvare as root, I don't have Windows in the Invetory anymore. When I want to add it, it shows me error listed up.

---

### Post by Somenoob on 2006-06-19
How fast is it? fast enough for playing games on it?

---

### Post by DAaaMan64 on 2006-06-19
[QUOTE=Somenoob]How fast is it? fast enough for playing games on it?[/QUOTE]

Hopefully I will be the last person to have to say this in this thread.

[SIZE="7"]IT'S FAST BUT NOT FAST ENOUGH TO PLAY GAMES ON[/SIZE]

---

### Post by aterlecki on 2006-06-19
I'm suprised nobody has mentioned installing the VMWare Management Interface on the server yet. For Dapper it is not smooth sailing and, in fact, I think there is a bug in the code so that the local Apache web server which is installed will not start on Dapper after a reboot.

Here are the additional steps I took to get it working:

1. The MUI needs an older libdb library (libdb.so.3) which isn't installed by default. This can be obtained by installing the libdb2 package:

sudo apt-get install libdb2

2. After a reboot the VMWare MUI Apache instance will not load properly. This is because it does not have the appropriate permissions to create the files it needs under /var/run/vmware/httpd. When it tries to create these files it needs first to create the /var/run/vmware/httpd directory but the default user and group that Apache runs under is www-data and nogroup and therefore lack the permissions to create this directory. As a workaround I added the following two lines to the top of the /etc/init.d/httpd.vmware script:

mkdir -p /var/run/vmware/httpd
chown www-data.nogroup /var/run/vmware/httpd

After these changes everything came up rosy!

Hope this helps someone.

Tony.

---

### Post by OneSeventeen on 2006-06-20
After updating my kernel, VMWare server stopped working.
In #ubuntu, the user "NoUse" mentioned running vmware-config.pl.

When running that, I got:```
The path "/usr/src/linux/include" is not an existing directory.
```

Then I realized I need to rerun one of the original commands from the first post:```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
```

It told me xinetd and build-essential were already up-to-date but would download linux-headers-2.6.15-25_2.6.15-25.43 and linux-headers-2.6.15-25-386_2.6.15-25.43 and install them.

Then, I reran vmware-config.pl (accepting all the defaults, as I did when I first installed the server) and all is well!

So, in summary, if you upgrade your kernel, be sure to open a terminal and:```
sudo apt-get install linux-headers-`uname -r`
sudo vmware-config.pl
```
Then vmware should be up and running as usual! :D

---

### Post by rekahsoft on 2006-06-20
I am having this problem (it is because i attempted to install vmware before without success). How do i fix this?
```
collin@RekahSoft:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.
```
btw: i have unistalled all vmware packages with synaptics ;)

---

### Post by sess420 on 2006-06-20
A previous installation of VMware software has been detected.

Failure

Execution aborted.


I uninstalled vmware player and vmware kernels and restarted but it still will not let me install the server. Any clues or guesses would be helpful

---

### Post by sess420 on 2006-06-20
never mind vmaware folder was still in etc ------solved it

---

### Post by Trocisp on 2006-06-20
I accidentaly put 20 gb instead of 10gb, is there anyway to uninstall it?

I feel like a turd... :(

---

### Post by jpepin on 2006-06-20
For those of you that are curious...

As Kure said a few pages back it is entirely possible, and more convenient for some, to use vmware to boot an existing windows installation (as in a dual boot system) as a vm.  I've been doing this for quite some time with vmware workstation.  I haven't tried it with vmware server, but I don't see why it shouldn't work.  

BUT..in order to prevent screwing up your windows install, you have to create a new hardware profile in windows that you use solely for vmware.  That way, if you boot directly into your windows installation natively, your drivers, settings, etc, won't be screwed up.  

I could spell it all out for you, but it'd probably be better to go straight to the source:

[http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html](http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html)

:mrgreen:

---

### Post by dorts on 2006-06-20
I need help. My VMware Server was working well. But it now does not open. So I followed the instructions on the first page again. Now it still does not open. I tried vmware in terminal and it gave me this:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to alloc client: Cannot open file "/home/dorts/.vmware/preferences": Permission denied.



VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/dorts/.vmware/preferences": Permission denied.

A log file is available in "/tmp/vmware-dorts/ui-10255.log".  Please request support and include the contents of the log file.
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.

---

### Post by delar0cha on 2006-06-21
hi.. newb here :)
i've installed win xp through vmware on drapper
and when i try to activate my ethernet on windows
i get this error from vm:

Could not open /dev/vmnet0: No such file or directory
Failed to connect virtual device Ethernet0.

i've tried bridged,NAT,host only-
but they all give me the same error as above but with a different #
after 'vmnet'

somebody help me~~~~~~

---

### Post by pellgarlic on 2006-06-22
[QUOTE=E-Jey]How could I exchange data between my virtual machine and my host OS. I've installed VMware tools and when I drag and drop files in to my virtual machine I get this error: 

Unable to open: Virtual machine "/home/erik/Desktop/file.extension" is not in the inventory. 

How could I solve this?[/QUOTE]


it seems that the most commonly suggested solution to sharing files between the "host" and the "virtual" machines, is to set up a network share, using samba or seomthing, but that seems a bit complicated to me - if you have a usb drive, it is easily detected by the virtual machine, and "disconnecting" it from the virtual machine makes it accessible in ubuntu, without having to unplug it. 

it seems to me that this is the easiest way to share files between ubuntu and the virtual machine, although having a decent sized usb drive would be paramount for large files - i have a 60gb external drive, and a 1gb flash drive, both of which work fine using this method.

---

### Post by pillypoon on 2006-06-22
Thanks for all the great info so far from this thread.. I am so looking forward to never having to dual boot again.. 

I am running into a problem because i have a w2k oem dell specific cd.  when i try to install it in vmware the installation halts and tells me i need to be using a dell machine.  (Iam using a dell machine but i guess the install cd is not able to see past vmware?) is there a way to force the w2k install cd to install inside vmware.   any help would be greatly appreciated. 

Also,  I tried using my copy of XP and it installs perfectly but it tells me i need to buy a new serial code..  can you believe that crap ?   a copy of xp that I bought wont let me install it into my system  . whats up with that?   i know that it is suppose to be installed on one machine only but does that count if it is the same machine inside VMware?  

So i guess if somebody can tell me how to activate my bought copy of XP without calling the big brother that would be great.. 

The whole activation scheme is what made me turn to Linux in the first place about 4 years ago..  good work Bill!!!  

thanks pilly

---

### Post by 43moon on 2006-06-22
pillypoon, when you finish the install are you allowing it to register online?  That is the default option in XP, so if you change it and don't register it, that may resolve the issue.  Just a guess though...

---

### Post by pillypoon on 2006-06-22
[QUOTE=43moon]pillypoon, when you finish the install are you allowing it to register online?  That is the default option in XP, so if you change it and don't register it, that may resolve the issue.  Just a guess though...[/QUOTE]

I selected "dont register and just activate"..  I have reinstalled XP on my machine so many times.. Sometimes it goes through and sometimes i need to call and get a new activation code..  what a great way to treat a paying customer.  i am so sick of it.. I am not going to touch Vista with a 10 foot pole!!   I am sure the final Vista activation code is even worse.

---

### Post by matrooswolf on 2006-06-22
[QUOTE=delar0cha]hi.. newb here :)
i've installed win xp through vmware on drapper
and when i try to activate my ethernet on windows
i get this error from vm:

Could not open /dev/vmnet0: No such file or directory
Failed to connect virtual device Ethernet0.

i've tried bridged,NAT,host only-
but they all give me the same error as above but with a different #
after 'vmnet'

somebody help me~~~~~~[/QUOTE]
I don't know if this would be any help to you, but during the installation vmware proposed eth0 as standard option, but it was eth1, (that was the only thing I changed in the standard options ...)

Just my 2 (euro)cents

---

### Post by pellgarlic on 2006-06-22
[Deleted by poster]

---

### Post by InDenial on 2006-06-22
[QUOTE=pillypoon]Thanks for all the great info so far from this thread.. I am so looking forward to never having to dual boot again.. 

I am running into a problem because i have a w2k oem dell specific cd.  when i try to install it in vmware the installation halts and tells me i need to be using a dell machine.  (Iam using a dell machine but i guess the install cd is not able to see past vmware?) is there a way to force the w2k install cd to install inside vmware.   any help would be greatly appreciated. 

Also,  I tried using my copy of XP and it installs perfectly but it tells me i need to buy a new serial code..  can you believe that crap ?   a copy of xp that I bought wont let me install it into my system  . whats up with that?   i know that it is suppose to be installed on one machine only but does that count if it is the same machine inside VMware?  

So i guess if somebody can tell me how to activate my bought copy of XP without calling the big brother that would be great.. 

The whole activation scheme is what made me turn to Linux in the first place about 4 years ago..  good work Bill!!!  

thanks pilly[/QUOTE]

The problem is, that once you activate it on a computer it will remember the hardware which is IN your computer. So in the theory if you are upgrading your computer with a lot of new hardware.. you would have to activate it again because they think you are installing it on another computer. In your case the whole computer changed because you are installing it within vmware. 

Just call them and tell them you bought a new computer and let them reset it. Or just say you bought it for testing purposes and that your hardware is changing a lot or just say you are installing it within vmware because you have to run a program which you did not find a linux substitute for yet... :P

Hmmm I wonder if vmware's hardware id's will change if you create a new virtual machine.

---

### Post by pillypoon on 2006-06-22
[QUOTE=InDenial]The problem is, that once you activate it on a computer it will remember the hardware which is IN your computer. So in the theory if you are upgrading your computer with a lot of new hardware.. you would have to activate it again because they think you are installing it on another computer. In your case the whole computer changed because you are installing it within vmware. 

Just call them and tell them you bought a new computer and let them reset it. Or just say you bought it for testing purposes and that your hardware is changing a lot or just say you are installing it within vmware because you have to run a program which you did not find a linux substitute for yet... :P

Hmmm I wonder if vmware's hardware id's will change if you create a new virtual machine.[/QUOTE]


I just hate the fact I need to call Bill so I can reactivate my purchased windows.. Microsft has probably lost thousands of users becasue of it and the numbers are still growing.  I wonder if i told them that i am installing it in VMware is that considered a different system?  I already have xp instaled as dual boot , so is having 2 windows on the same machine against the eula? :-#

---

### Post by InDenial on 2006-06-22
[QUOTE=pillypoon]I just hate the fact I need to call Bill so I can reactivate my purchased windows.. Microsft has probably lost thousands of users becasue of it and the numbers are still growing.  I wonder if i told them that i am installing it in VMware is that considered a different system?  I already have xp instaled as dual boot , so is having 2 windows on the same machine against the eula? :-#[/QUOTE]

first I want to say that I am not really fond of Microsoft. The things you have to do to make something work and the unportability of a bought operating system.

That said.. I do not find it strange that a company is doing things like that. You would probably do the same thing. If a burgaler breaks into your house you are going to make sure next time it will be harder for a burgaler to break in.. right?

MS is taking it a little too far though but as long they have the biggest share of the market they do not care what the result of those actions is.

But this is highly off-topic. so lets leave it at that...

---

### Post by Somenoob on 2006-06-22
I heard it has problems with detecting USB devices,

had any problems with that?

---

### Post by pellgarlic on 2006-06-23
[QUOTE=InDenial]The problem is, that once you activate it on a computer it will remember the hardware which is IN your computer. So in the theory if you are upgrading your computer with a lot of new hardware.. you would have to activate it again because they think you are installing it on another computer. In your case the whole computer changed because you are installing it within vmware. 

Just call them and tell them you bought a new computer and let them reset it. Or just say you bought it for testing purposes and that your hardware is changing a lot or just say you are installing it within vmware because you have to run a program which you did not find a linux substitute for yet... :P

Hmmm I wonder if vmware's hardware id's will change if you create a new virtual machine.[/QUOTE]

i'm pretty sure this doesn't apply to installing windows in vmware - it only applies to an already existing installation of windows, where you want to change the hardware. 

the problem pillypoon has with his "dell" cd is that it is restricted for use only to install on a "dell" pc. it has nothing to do with "changed hardware" - that is a different issue. i'm sure the cd would work on other "dell" pcs with different hardware configurations.

installing windows in vmware involves a clean install, so windows does't know anything about "previous" hardware. 

as far as creating a new virtual machine goes, as long as the virtual devices selected are the same, there will be no problem - with physical systems, you can substitute the hardware for another part of the same make and model, without effect. it is only if you switch from an nvidia card to an ati card, or from an asus motherboard to a gigabyte motherboard (for examples) that it is an issue.

---

### Post by InDenial on 2006-06-23
[QUOTE=pellgarlic]i'm pretty sure this doesn't apply to installing windows in vmware - it only applies to an already existing installation of windows, where you want to change the hardware.
[/quote]

As far as I know, when you validate a copy of windows XP it keeps a certain file in your windows/system32 directory which contains your hardware. This file is checked against a database at Microsoft whenever you want to do windows update. So I do agree that this applies to changing hardware when the system is already installed, but I am very positive that it applies to the situation where you first installed it on another machine and then reinstall windows in vmware since the hardware changes dramaticly. In this case you would have to re-validate your copy.

[QUOTE=pellgarlic]
the problem pillypoon has with his "dell" cd is that it is restricted for use only to install on a "dell" pc. it has nothing to do with "changed hardware" - that is a different issue. i'm sure the cd would work on other "dell" pcs with different hardware configurations.
[/quote]

I do not agree with that. The thing is that windows XP delivered Together with a pc is pre-validated at the company who deliveres the pc's. This means that it MIGHT work if you use the copy on almost exactly the same pc, but it will fail on a pc with a different configuration. Besides most of the time you just get a recovery cd which won't work on different hardware. 

[QUOTE=pellgarlic]
installing windows in vmware involves a clean install, so windows does't know anything about "previous" hardware. 

as far as creating a new virtual machine goes, as long as the virtual devices selected are the same, there will be no problem - with physical systems, you can substitute the hardware for another part of the same make and model, without effect. it is only if you switch from an nvidia card to an ati card, or from an asus motherboard to a gigabyte motherboard (for examples) that it is an issue.[/QUOTE]

This only goes IF you validate your copy of windows when running in vmware.  Once validated you are stuck with the hardware you got unless you let them reset the validation.

---

### Post by ewonk on 2006-06-23
This HOWTO worked seamlessly for me. I'm running on a dapper xubuntu and followed every step in the howto.

I'm on a Toshiba Satellite A15-127 laptop. Running the ubuntu 4.0.3 desktop under kernal 2.6.15-23-386 with gcc version 4.0.3 - oh I guess my gcc was different, however, I did install the 3.0 version of it. Maybe I have both or it got updated somehow?

Anyways, the toy is working and here's a screener.

[[IMG]http://static.flickr.com/54/173473281_a8c0ac5b1b.jpg[/IMG]](http://static.flickr.com/54/173473281_a8c0ac5b1b_o.jpg)

---

### Post by tokez on 2006-06-23
**I AM USING UBUNTU DAPPER 6 WITH XGL AND COMPIZ INSTALLED AND ACTIVE**

i followed the howto are far as possible.

when i run 'vmware' i get this 
```

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

so i follow the directions and it stops at this

```

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

```

after selecting yes, i get this error output
```

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-25-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.15-25-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
/tmp/vmware-config4/vmmon-only/Makefile:89: *** Inappropriate build environment: you wanted to use gcc version 4.0.3 while kernel attempts to use gcc version 3.4.6.
/tmp/vmware-config4/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc -m32 with symbolic link to /usr/bin/gcc-4.0.  Stop.
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

thanks in advance.

---

### Post by slider on 2006-06-24
tokez-

Reading the error message it looks like you have the wrong version of gcc installed. You need to install gcc-4.0

apt-get install gcc-4.0

Chances are doing that and then rerunning the install will work. If not set the  environment variable CC to point to the gcc-4.0 binary before starting the build (man env)

---

### Post by slider on 2006-06-24
I followed this tutorial and it worked great for me. Thanks a ton. I took it a step farther and followed the information [ here]("http://macrolinz.com/macrolinz/index.php/2006/01/09/physcial-to-virtual/") to back up my old XP install using ntbackup.exe and restore it as a client OS in vmware. Works like a charm. About the only time I have to jump over to XP is to use Photoshop and for browser testing.

If you try it, make sure to follow the link above and read the comments. There are a couple gotchas that are real timewasters.

---

### Post by tokez on 2006-06-24
I read thru 'man env' and figured to type the command ..

env CC=/usr/bin/gcc-4.0

this does not solve my problem ... i even attempted to run 'env CC=/usr/bin/gcc-4.0 /usr/bin/vmware-config.pl'

as you can probably see i am clueless :P please direct me in the right direction to forcing gcc to use 4.0
(apt-get install gcc-4.0 returns gcc-4.0 is newest version)

---

### Post by andylei on 2006-06-24
i'm on dapper, and when I executed the install script heres what happened:




================


Installing the content of the package.

In which directory do you want to install the binary files?
[/home/Andy/vmware]

The path "/home/Andy/vmware" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/home/Andy/sbin]

The path "/home/Andy/sbin" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the library files?
[/home/Andy/lib/vmware]

The path "/home/Andy/lib/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]


In which directory do you want to install the manual files?
[/home/Andy/man]
The path "/home/Andy/man" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the documentation files?
[/home/Andy/doc/vmware]

The path "/home/Andy/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

===============



anyone know what went wrong?

---

### Post by bobc on 2006-06-24
I am on Breezy and it workd nicely for me :p Thanks!!

---

### Post by slider on 2006-06-25
Tokes-

Not sure why it would ignore CC. Only other suggestion is to link /usr/bin/gcc to /usr/bin/gcc-4.0

ln -s /usr/bin/gcc-4.0 /usr/bin/gcc

Make sure to remember where gcc points to first so you can reset it afterward

ls -als /usr/bin/gcc*

---

### Post by kopolee11 on 2006-06-25
[QUOTE=andylei]i'm on dapper, and when I executed the install script heres what happened:




================


Installing the content of the package.

In which directory do you want to install the binary files?
[/home/Andy/vmware]

The path "/home/Andy/vmware" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/home/Andy/sbin]

The path "/home/Andy/sbin" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the library files?
[/home/Andy/lib/vmware]

The path "/home/Andy/lib/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]


In which directory do you want to install the manual files?
[/home/Andy/man]
The path "/home/Andy/man" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the documentation files?
[/home/Andy/doc/vmware]

The path "/home/Andy/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

===============



anyone know what went wrong?[/QUOTE]

The same thing happened to me, and to tell the truth I have no idea what happened. However, I was able to install vmware by going back to the vmware directory and running 
```
sudo ./vmware-install.sh
```

For some reason it didn't show the error the second time, and instead it simply skiped that step. You just then continue with the installation, all the way up to the installation key. 

I know this isn't the most official answer, but try again, and see if it works.

---

### Post by Twizz on 2006-06-25
I have the same problem as andylei.  I cant seem to get it to work.

---

### Post by pellgarlic on 2006-06-26
@InDenial - think we've crossed wires here - i'm not actually disagreeing with you as such - i just envisage people using vmware in a different way that you do, i think.

[QUOTE=InDenial]As far as I know, when you validate a copy of windows XP it keeps a certain file in your windows/system32 directory which contains your hardware. This file is checked against a database at Microsoft whenever you want to do windows update. So I do agree that this applies to changing hardware when the system is already installed, but I am very positive that it applies to the situation where you first installed it on another machine and then reinstall windows in vmware since the hardware changes dramaticly. In this case you would have to re-validate your copy.[/QUOTE]

to be pedantic :) it's not "re-validating a copy", since it's not a copy - it's a completely separate installation, unless an existing windows installation is "ported" into vmware, as i know is possible. but a new installation will need validation separately from the first installation - not because of hardware changes, but because it's a new installation. (the file which stores the list of hardware in the first installation has nothing to do with any separate installation, unless you actively copied it over to the new installation, which wouldn't work unless the hardware was exactly the same).

[QUOTE=InDenial]I do not agree with that. The thing is that windows XP delivered Together with a pc is pre-validated at the company who deliveres the pc's. This means that it MIGHT work if you use the copy on almost exactly the same pc, but it will fail on a pc with a different configuration. Besides most of the time you just get a recovery cd which won't work on different hardware. [/QUOTE]

yep - i think you're right there, and i was wrong.

[QUOTE=InDenial]This only goes IF you validate your copy of windows when running in vmware.  Once validated you are stuck with the hardware you got unless you let them reset the validation.[/QUOTE]

agreed. however, i expect that most people would do it this way, as opposed to the "import an existing windows installation" way, in which case the "changed hardware" issue would kick in. once you create a "virtual machine", i think it is unlikely that you would want to change the hardware configuration, and as far as i know, there isn't much choice for things like sound card, display adapter etc in vmware anyway.

(p.s. sorry for late reply - no broadband at home :( do this all at work.)

---

### Post by m23 on 2006-06-26
I'm not sure if this has been addressed yet; there are way to many pages to read through.

Upon default installation of VMWare server, port 902 is opened up. 
```
userid@host:~$ cat /etc/xinetd.d/vmware-authd
# default: on
# description: The VMware remote access authentification daemon
service vmware-authd
{
    disable         = no
    port            = 902
    socket_type     = stream
    protocol        = tcp
    wait            = no
    user            = root
    server          = /usr/sbin/vmware-authd
    type            = unlisted
}

```

If you're using vmserver locally, there isn't a need for this to be open.

To clos it, simply change ```
disable         = no
``` 
To```
disable         = yes
``` 

Then run
```
userid@host:~$ sudo /etc/init.d/xinetd restart 
```

Maybe the thread's author could add this to his guide.

---

### Post by InDenial on 2006-06-26
[QUOTE=pellgarlic]@InDenial - think we've crossed wires here - i'm not actually disagreeing with you as such - i just envisage people using vmware in a different way that you do, i think.



to be pedantic :) it's not "re-validating a copy", since it's not a copy - it's a completely separate installation, unless an existing windows installation is "ported" into vmware, as i know is possible. but a new installation will need validation separately from the first installation - not because of hardware changes, but because it's a new installation. (the file which stores the list of hardware in the first installation has nothing to do with any separate installation, unless you actively copied it over to the new installation, which wouldn't work unless the hardware was exactly the same).



yep - i think you're right there, and i was wrong.



agreed. however, i expect that most people would do it this way, as opposed to the "import an existing windows installation" way, in which case the "changed hardware" issue would kick in. once you create a "virtual machine", i think it is unlikely that you would want to change the hardware configuration, and as far as i know, there isn't much choice for things like sound card, display adapter etc in vmware anyway.

(p.s. sorry for late reply - no broadband at home :( do this all at work.)[/QUOTE]

Crossed wires indeed.... ;) We are talking about the same...  case closed....

---

### Post by tokez on 2006-06-26
[QUOTE=slider]Tokes-

Not sure why it would ignore CC. Only other suggestion is to link /usr/bin/gcc to /usr/bin/gcc-4.0

ln -s /usr/bin/gcc-4.0 /usr/bin/gcc

Make sure to remember where gcc points to first so you can reset it afterward

ls -als /usr/bin/gcc*[/QUOTE]

i should have checked the links first :P thank you slider this took care of it. gcc was linked to 3.4 :/

easy solution :P thanks a ton

---

### Post by Don_DiZzLe on 2006-06-28
Whats the difference 'tween VMware Server and Workstation and can I use this howto for Workstation instead of Server?

---

### Post by tiddlygoose on 2006-06-28
I don't know about you but I could not get VMWare workstation running on Ubuntu. I was able to get the VMWare server running following the above instructions. Does it matter since they are giving it away?

---

### Post by Don_DiZzLe on 2006-06-28
Nope not really, just curious though

---

### Post by fade510 on 2006-06-28
this code in the beginning is wrong
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
there should be no space between uname and -r
it should be
sudo apt-get install linux-headers-`uname-r` build-essential xinetd

---

### Post by Somatik on 2006-06-28
[QUOTE=aterlecki]I'm suprised nobody has mentioned installing the VMWare Management Interface on the server yet. For Dapper it is not smooth sailing and, in fact, I think there is a bug in the code so that the local Apache web server which is installed will not start on Dapper after a reboot.

Here are the additional steps I took to get it working:

1. The MUI needs an older libdb library (libdb.so.3) which isn't installed by default. This can be obtained by installing the libdb2 package:

sudo apt-get install libdb2

2. After a reboot the VMWare MUI Apache instance will not load properly. This is because it does not have the appropriate permissions to create the files it needs under /var/run/vmware/httpd. When it tries to create these files it needs first to create the /var/run/vmware/httpd directory but the default user and group that Apache runs under is www-data and nogroup and therefore lack the permissions to create this directory. As a workaround I added the following two lines to the top of the /etc/init.d/httpd.vmware script:

mkdir -p /var/run/vmware/httpd
chown www-data.nogroup /var/run/vmware/httpd

After these changes everything came up rosy!

Hope this helps someone.

Tony.[/QUOTE]

do you by any chance know how to make a normal (not root) user administrator for the server? i can't configure the server options without setting the root password

---

### Post by Endwin on 2006-06-28
I was able to install the server on a machine where I keep my files, and on my laptop I installed the vmware-server-console. I can connect up fine, create the machine, but when I turn it on I get 

Error during launch: 11, The process exited with an error:
End of error message

When I check the /var/log/vmware/serverd.log I see...

Jun 28 19:07:08: app| SP: Retrieved username: endwin
Jun 28 19:07:11: app| Adding to list of running vms: /var/lib/vmware/machines/Windows 2000 Professional/Windows 2000 Professional.vmx
Jun 28 19:07:11: app| Attempting to launch vmx : /var/lib/vmware/machines/Windows 2000 Professional/Windows 2000 Professional.vmx
Jun 28 19:07:11: app| Error during launch: 11, The process exited with an error:
Jun 28 19:07:11: app| End of error message
Jun 28 19:07:11: app| VmsdVmStatePendingCmdFailed: cmd status is already set
Jun 28 19:39:46: app| Attempting to launch vmx : /var/lib/vmware/machines/Windows 2000 Professional/Windows 2000 Professional.vmx
Jun 28 19:39:46: app| Error during launch: 11, The process exited with an error:
Jun 28 19:39:46: app| End of error message
Jun 28 19:39:46: app| VmsdVmStatePendingCmdFailed: cmd status is already set
Jun 28 19:39:50: app| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
Jun 28 19:39:50: app| SP: Deleting user session: 0 username: endwin
Jun 28 19:40:08: app| New connection on socket server-vmdb from host 192.168.0.3 (ip address: 192.168.0.3) , user: endwin
Jun 28 19:40:08: app| SP: New user session for user: endwin, pos: 0
Jun 28 19:40:08: app| The vm-list file has changed! Reloading the list of registered vms
Jun 28 19:40:10: app| SP: Retrieved username: endwin
Jun 28 19:40:15: app| Attempting to launch vmx : /var/lib/vmware/machines/Windows 2000 Professional/Windows 2000 Professional.vmx
Jun 28 19:40:15: app| Error during launch: 11, The process exited with an error:
Jun 28 19:40:15: app| End of error message
Jun 28 19:40:15: app| VmsdVmStatePendingCmdFailed: cmd status is already set
Jun 28 19:40:25: app| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
Jun 28 19:40:25: app| SP: Deleting user session: 0 username: endwin

Any idea on what needs to me modified/installed/whatever?

---

### Post by nudaz on 2006-06-28
Trying to install vmware server on ubuntu 6.06 server, getting error about liX11.so.6 and invalid serial number.

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
Please enter your 20-character serial number.

- typed in serial number -

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
The serial number xxxxx is invalid.

Please enter your 20-chararcter serial number.

- repeat ad infinitum

Also, during install/configure got:

libX11.so.6 => not found
libXtst.so.6 => not found
libXext.so.6 => not found
libXt.so.6 => not found
libICE.so.6 => not found
libXrender.so.1 => not found

Any help would be appreciated, cheers

---

### Post by machia on 2006-06-29
I got the vmware to work and I can boot to my Windows partition.Thanks for that mate :)
One thing I noticed was that I had Jagged Alliance 2 installed on in windows and it seems to work through vmware. It works smooth as well. It might be that it works through Wine as well but I dont know. My verision is the latest v.1.13 which has lots of cool updates :D

[IMG]http://80.221.36.254/~machia/kuvat/vmware_running_JA2.png[/IMG]

---

### Post by Endwin on 2006-06-29
[QUOTE=nudaz]Trying to install vmware server on ubuntu 6.06 server, getting error about liX11.so.6 and invalid serial number.

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
Please enter your 20-character serial number.

- typed in serial number -

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
The serial number xxxxx is invalid.

Please enter your 20-chararcter serial number.

- repeat ad infinitum

Also, during install/configure got:

libX11.so.6 => not found
libXtst.so.6 => not found
libXext.so.6 => not found
libXt.so.6 => not found
libICE.so.6 => not found
libXrender.so.1 => not found

Any help would be appreciated, cheers[/QUOTE]

I had the same problem aparently it validates the key through some X11 library if you install libx11-dev and/or libx11-6 it should work.

---

### Post by 655321 on 2006-06-29
I'm very new to Linux and today I installed Ubuntu 6.06 Dapper Drake on a couple of machines.  These are fresh installs with no modifications.  When trying to install VMWare I got error messages on both machines:

> Setup is unable to find the "make" program on your machine.  Please make sure it is installed.  Do you want to specify the location of this program by hand? 

I've got some books on the way, and I'll keep browsing the forums here.  Any quick advice on where to obtain & install the make program, or any other essential tweaks is greatly appreciated.

---

### Post by genzo on 2006-06-29
sounds like you need to install gcc.. look in the first post

---

### Post by pellgarlic on 2006-06-29
actually, it's "build-essential" that's missing (it contains various programs necessary for compiling software, including "make") - you can install this from the dapper installation cd - 

just put it in the cd drive, and wait until a message pops up saying "an ubuntu cd has been detected. you can now start the package manager". now, click the button that says "start package manager", and synaptic will open. 

now click on the "search" button, and type "build-essential". click the square icon at the left of the name of the package, then select the "mark for installation" option. now click the "apply" button at the top.

synaptic will install "build-essential" from the dapper cd, then you can "close" the window (once it says that "changes have been applied").

now try installing vmware again. you should be good to go.

---

### Post by 655321 on 2006-06-29
[QUOTE=pellgarlic]actually, it's "build-essential" that's missing (it contains various programs necessary for compiling software, including "make") - you can install this from the dapper installation cd - 
[/QUOTE]

Thanks for your help!  I think this is exactly what I need.  Today is my first day with Linux and I'm looking forward to learning more about it.

---

### Post by pellgarlic on 2006-06-29
hope you have fun :)

if it ever stops being fun, come here and ask for help - there are a lot of smart dudes around here who can help out.

---

### Post by Riona on 2006-07-01
Followed your howto and am having trouble.
At the last step I get an error message
The path "/home/xxxxx/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

I've tried reinstalling gtk and starting the process over. Any ideas on how to get past this error? Thanks.

---

### Post by abregenzer on 2006-07-01
> Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.


I was able to get around this by doing:

mkdir vmware-vix/bin

---

### Post by WaWeeT on 2006-07-02
hey....i didn't recived any mail from vmware!   
and i am now in front of tape the serial number!   
how can i get the serial???
can someone paste his serial here???

---

### Post by WaWeeT on 2006-07-02
aha...i found this in vmware's forum:

he serial numbers issued to you are available in your VMware Store account under:

VMware.com > Your Account > Account Home > Serial Number History

These are the same serial numbers that are emailed to you.

---

### Post by Cris987 on 2006-07-04
[QUOTE=dorts]Can anyone help me with samba? How do you share files with my vmware Xp and ubuntu?[/QUOTE]

Install Samba. Go into "vmware xp" and declare shared folders/drives by right clicking -> sharing and security -> click on blue link in the "network sharing" box -> check box that says "share this folder"   or something like that.  Now go back to Ubuntu -> places -> network server and find your vmware xp computer.

good luck

---

### Post by Cris987 on 2006-07-05
Two problems are buggin me inside my "vmware xp":

1. I can't get my sound device to work. It seems like if I'm using my sound card in Ubuntu (amarok?), vmware won't allow it to work inside the virtual machine as well. Anyway to fix that?

2. I was installing Mvp Baseball 2005 on vmware XP , and it told me to switch CDs, so I did. But the installer would not proceed after that. It seemed like it would not detect the new CD or something. What's wrong?

---

### Post by tzulberti on 2006-07-05
Thanks cris987 y was looking for that tip. This How-to worked perfect in my ubuntu drapper.

---

### Post by qrm on 2006-07-06
hi,

I allocated 8 Gigabytes of space from my HDD to my XP install but somehow i succeeded to mess the XP install up. Is there a way to regain the space? Ive deleted the virtual machine from /var/lib/vmware folder but it doesnt seem to work

---

### Post by SteveHoffmanUK on 2006-07-06
This is an excellent Howto, and the VM seems to be just what I need. It installed flawlessly and it is working as it should.

HOWEVER, I can't seem to get file sharing working. I followed Chris's instructions and installed Samba, then went into my XP vm and modified my C Drive to share it with others on the network. Then I returned to Ubuntu Places>Network Servers> Windows Network > MShome >Steve-Desktop but nothing shows as a shared file.

Chri987 (or anyone else): Any suggestions on how to correct this?

Many thanks

---

### Post by PhrankDaChickenGeek on 2006-07-07
SCORE! Got widescreen working. I can now use Windows XP in fullscreen at 1920x1200

Followed this:

[http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1003](http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1003)

Make sure to do step #9, otherwise it might not work.

---

### Post by acejones on 2006-07-07
Trying to install VMware Server, but i'm getting the following error when running
```
sudo ./vmware-install.pl
```:
```
A previous installation of VMware software has been detected.

Failure

Execution aborted.
```
I had previously installed VMware Player, but I uninstalled it viy Synaptic.  Any help getting past this would be great.

---

### Post by halfthelaw on 2006-07-07
Is there any way (whether with VMWare or otherwise) to boot a pre-existing Windows install?

---

### Post by TheMono on 2006-07-08
Question - Is it safe to use an external Hard Drive as the place for your virtual PC install?

---

### Post by jan on 2006-07-08
Woow,

Windows XP on Ubuntu is just cool! :mrgreen:

---

### Post by rhipwell on 2006-07-08
Thanks for the guide, works great!

---

### Post by mwolfe on 2006-07-08
I don't understand how to install this.. I downloaded vmware VMware-server-1.0.0-27828.tar.gz
for linux and when i extract the file there IS a vmware-server-distrib directory, however there is no install script inside of this directory. I've looked through all the directories that were extracted and none of them included an install script (however i found an uninstall script)

Any idea what i did wrong?

[EDIT]Alright i know what i did wrong now, i was extracting it on a fat32 drive.. the install script was a symbolic link and for some reason symoblic links don't work on fat32 drives.. not sure why though
[/EDIT]

---

### Post by kpkeerthi on 2006-07-08
Installation fails for me... BSOD... any clue why?

---

### Post by Shampyon on 2006-07-08
This is a pretty cool guide. I'm in the middle of the install as I type. I have a question, though.
I accidentally made a VM Windows partition for XP, but I made a mistake.

I should have done:
#  select 'Create a new virtual machine'
# => Next => Next => Select Windows Xp

But I actually did
#  select 'Create a new virtual machine'
# => Next => Next => Select Windows 2000

I didn't notice until I tried to install XP on it and it told me it had the wrong boot strap (or something). How would I go about deleting it?

---

### Post by jISh on 2006-07-09
You can just right click the virtual machine in the inventory window on the left side, and click Delete from hard disk.

---

### Post by Shampyon on 2006-07-09
I have one little problem with that - I removed it from the inventory. I should have said that in my post :oops: 

I'm also wondering how I'd go about giving the VM XP access to my files, or to copy over files into it, so I can use it to play DRM'd wmv's. I still haven't been able to get the sound working, either...

---

### Post by mwolfe on 2006-07-09
sound is pretty easy to get working. Open up your xp server console, but don't power it on. You should see a button that says edit virtual machine. Click that, and then click the add button under the options tab and add your audio device. I chose auto and it worked fine.

---

### Post by Shampyon on 2006-07-09
That ooption had been auto-selected already.
I tried changing it from Auto Select to the only device it seemd to recognise, /dev/dsp. Still nothing. Would I have to install the XP-based sound drivers from the disc that came with my card into th VM XP? Or should it already work by virtue of it being already set in Ubuntu?

I seem to be having problems left and right (though, admittedly, it's more than likely due to my love of tinkering with settings I don't fully understand).

---

### Post by krazykirk on 2006-07-09
Wow! It works great! Great guide btw!

But i'm having 1 problem!

I press the "full screen" button, and i get a error!

```
Unable to find an appropiate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.
```

I think it means Xorg.conf in the same directory, but i have no idea to "add the guest mode."

I'm going to restart X now to see how that goes!

I'll post results here.

---

### Post by krazykirk on 2006-07-09
nope! Restarted X and got the same error.

Any ideas anyone?

I found the right area in the display subsection of the screen section, but i have no idea how to set the guest mode.

---

### Post by BlackMambo on 2006-07-09
While carrying out the instructions in the first post of this topic, I got this:
```

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.
```
:confused:

FIXED :)

---

### Post by BlackMambo on 2006-07-09
Well I installed VM Ware but when I click on the menu item, as the first post describes, I get a 

[B][COLOR="Red"]Could not launch menu item

Details: Failed to execute child process "vmware" (No such file or directory)[/COLOR][/B]

Anyone know what could be the problem?

---

### Post by mekas2024 on 2006-07-09
Hello , first of all this its a greeat how-to, i have everything working fine, but.. my only problem its the sound, i add the device in the vmware machine settings, but when i power on the virtual machine it says this warning message>

Failed to open sound device /dev/dsp: Device or resource busy
Virtual device sound will start disconnected.

I think that its because ubuntu its using it ! 

Any Ideaas???

Thanks and i hope someone help mee!

Regards

MeKaS

---

### Post by mwolfe on 2006-07-09
I'm not sure if you can fix that. I think i read someone else had that problem. Luckily i have 2 sound cards and the vm uses the one that ubuntu isnt using so i just switch the cable or listen to headphones in windows.

---

### Post by Shampyon on 2006-07-09
I couldn't get any sound from my VM XP. I tried using the AutoSelect option, and the /dev/dsp. Neither worked, so I opened nautilus and navigated to /dev/dsp. I noticed that there was also a dsp1. I went back into VMWare, added a 1 (one) to the /dev/dsp option (/dev/dsp1), and now sound is working.

Hope that helps someone else.

---

### Post by krazykirk on 2006-07-09
@ People who have audio problems:

I had the same problem, and I was playing my music at the time, so I tried closing Rythmbox and all the other programs that would use the sound device, and it fixed it!

---

### Post by Sq322 on 2006-07-10
Great how to: got this puppy installed in no time.
One problem
I tried to use the custom option and "use physical disk" to tell vmware to use my existing Windows install as was suggested way back in the pages of this thread.
I got an error.
"unable to access, you do not have sufficient permissions"
Any ideas ?

---

### Post by Hellaxe on 2006-07-11
> **mekas2024 said:**
> Hello , first of all this its a greeat how-to, i have everything working fine, but.. my only problem its the sound, i add the device in the vmware machine settings, but when i power on the virtual machine it says this warning message>

Failed to open sound device /dev/dsp: Device or resource busy
Virtual device sound will start disconnected.

Same problem here on my Thinkpad R51. It's an Intel chip sound.

---

### Post by DA_uf on 2006-07-11
Since
> Upon default installation of VMWare server, port 902 is opened up.
Why can't I connect from Windows XP VMware Server console to my Ubuntu VMware Server?  I saw when this default port was selected during the install.  I can use the local VMware Server console, but not the remote one.

From the remote Windows XP VMware Server console, I get...
There was a problem connecting:
Cannot connect to host xxx.xxx.xxx.xxx: No connection could be made because the target machine actively refused it.

EDIT:
Between the recent Ubuntu updates and restarts, and a few Windows XP restarts, it is actually working now.

---

### Post by oocce on 2006-07-11
Hi!
This is a sort of all-a-round question but I tought this thread would be nice place to put it ;)

I would like to have this vmware and Win Xp to be opened each time ubuntu starts. Want to get rid of the connection to Local host and after that must change tab to Win Xp... I use Gnome+Xgl/Compiz and it would nice to have this vmware to opened (in my case) to 3th workspace! Full screen doesent work because it says something about /etc/X11/XF86Config and guest mode, but if I got this thing workin, I would like vmware open in full screen. 

What is THE command I'm looking for? :)

---

### Post by Shampyon on 2006-07-11
I just got an annoying little problem.
I updated Ubuntu last night, kernel and all.
This morning, I can't start VMWare. I click the licnk in the Applications menu, and a little entry appears on the task bar saying "starting vmware". Then it just disappears, doesn't start up.

Edit: I typed "vmware" into the terminal, it gave me some instructions, and now I'm stuck at this point:
> Me@MyComputer:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

Me@MyComputer:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
The path "/usr/src/linux/include" is not an existing directory.


---

### Post by zhoux on 2006-07-11
> **Shampyon said:**
> I just got an annoying little problem.
I updated Ubuntu last night, kernel and all.
This morning, I can't start VMWare. I click the licnk in the Applications menu, and a little entry appears on the task bar saying "starting vmware". Then it just disappears, doesn't start up.

 it is because of the kernel updates, apparently, vmware server is only specific to previous kernel header, i read somewhere on other threads that you have to recompile vmware...i'll see if i can find the link later.

However, i have a question of my own, i upgraded my kernel this morning, and then i tried to install vmware server via this guide. However, because of the new kernel, i can't install, so i quit half-way through...so how do i delete/clean everything that i had already installed? is there an uninstall script?

EDIT: Shampyon, i had the exactly same problem, could anyone point the solution out to both (and many more people out there) of us?

---

### Post by scottd23 on 2006-07-12
Im using server and i  ran this -

sudo apt-get install linux-headers-`uname -r` build-essential xinetd

then ran the vmware-config.pl  

and it worked.

---

### Post by disturbd on 2006-07-12
I'm getting this one. I've tried everything on the boards. Nothing seems to work. I keep getting this same error. I even tried reinstalling and changing from VMware server to VMware Player. Neither of them work and both give same error.

> Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-26-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config5/vmmon-only'
make -C /lib/modules/2.6.15-26-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
/tmp/vmware-config5/vmmon-only/Makefile:89: *** Inappropriate build environment: you wanted to use gcc version 4.0.3 while kernel attempts to use gcc version 3.4.6.
/tmp/vmware-config5/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc -m32 with symbolic link to /usr/bin/gcc-4.0.  Stop.
make[1]: *** [_module_/tmp/vmware-config5/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config5/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


---

### Post by Shampyon on 2006-07-12
> **scottd23 said:**
> Im using server and i  ran this -

sudo apt-get install linux-headers-`uname -r` build-essential xinetd

then ran the vmware-config.pl  

and it worked.

The result for me:

> The configuration of VMware Server 1.0.0 build-27828 for Linux for this running kernel completed successfully.


Thanks!

---

### Post by geetarista on 2006-07-12
> **Sq322 said:**
> Great how to: got this puppy installed in no time.
One problem
I tried to use the custom option and "use physical disk" to tell vmware to use my existing Windows install as was suggested way back in the pages of this thread.
I got an error.
"unable to access, you do not have sufficient permissions"
Any ideas ?

I am having the same problem as well and I can't figure it out!  ](*,) 

I've heard of others who do this successfully.  Can anyone help?

---

### Post by Peturrr on 2006-07-12
> **disturbd said:**
> I'm getting this one. I've tried everything on the boards. Nothing seems to work. I keep getting this same error. I even tried reinstalling and changing from VMware server to VMware Player. Neither of them work and both give same error.
It gives you an error about GCC. You are using GCC version 3.4 but you'll need the GCC 4, since it looks like you are on Dapper.
You probably did the export export CC=/usr/bin/gcc-3.4, but that's only for breezy users.

Try restarting and installing without this export command. If that fails, enter ```
export CC=/usr/bin/gcc-4
``` and then it should work.

---

### Post by Peturrr on 2006-07-12
**Problem**
After a kernel upgrade VMWare won't start because it * has not been (correctly) configured for the running kernel*
[INDENT]**Solution**
execute ```
sudo /usr/bin/vmware-config.pl
``` 

[/INDENT]**Problem**
vmware-config.pl fails to find the right kernel headers. It cannot find /usr/src/kernel/include and won't proceed to install.
[INDENT]**Solution**
You have a updated kernel, but not the updated kernel headers. 
You can install them by executing ```
sudo apt-get install linux-headers-`uname -r`
``` Now you can succesfully run ```
sudo /usr/bin/vmware-config.pl
``` 
[/INDENT][B]
Problem[/B]
You don't want to install the kernel headers manually each time there is an update.
[INDENT]**Solution**
There is a package called linux-headers-*** that automatically installs the latest kernelheaders, so you don't need to install them manually each time.

There are 4 flavours of this package: 386, 686, k7, server.

If you don't know wich one you need, execute ```
uname -r
``` It will give you something like 2.6.15-26-**k7** or 2.6.15-26-**686**

Now you know the right flavour, install it by ```
sudo apt-get install linux-headers-*****
``` Replace the *** with 386, 686, k7 or server.[/INDENT]

---

### Post by Peturrr on 2006-07-12
> **Sq322 said:**
> Great how to: got this puppy installed in no time.
One problem
I tried to use the custom option and "use physical disk" to tell vmware to use my existing Windows install as was suggested way back in the pages of this thread.
I got an error.
"unable to access, you do not have sufficient permissions"
Any ideas ?
Although it is definately not save, you could try to execute from a terminal in gnome ```
sudo vmware
``` It will run with more priviliges, but should definately not be used day to day. It is however a good way to find out where the privilige problems come from.

---

### Post by Shampyon on 2006-07-12
I'm all set up now, thanks to the help from this thread.
I can network with the virtual XP, so I can use the win-only Super video encoder to make all my vids Linux-friendly.

Thanks for all the help!

---

### Post by Sq322 on 2006-07-12
> **Peturrr said:**
> Although it is definately not save, you could try to execute from a terminal in gnome ```
sudo vmware
``` It will run with more priviliges, but should definately not be used day to day. It is however a good way to find out where the privilige problems come from.

i was thinking that but was very afraid to do so...i will give it a whirl 
thx

---

### Post by qrm on 2006-07-12
i just got it installed and got rid of the libcairo errors so that it satrts flawlessly. But when I try to connect it tells me:

The local VMware Server is not installed, or is not currently running.
Make sure that the server is properly installed and try again.

any suggestions?

---

### Post by BlackMambo on 2006-07-12
I got XP installed on VM Ware. After the install, I suspended it and rebooted. Ubuntu then prompted me to install some automatic software updates, so I did that... after rebooting, I can't retrieve my VM Ware install.

If I click on Applications/System Tools/VM Ware Server Console, it sppears to start it, then it dies out after a short while.

Where are the virtual images kept? (I installed on my /home/username/vmware directory but there's nothing obvious in there) How can I load up VM Ware again so as to use the virtual machine I suspended earlier?

Thanks!

---

### Post by dino2006 on 2006-07-12
I have a problem connection from windows using the console to the ubuntu server 6.06 (64 bit) running vmware server. I get the following error in windows "vmware-authd socket error 10013.

I have vmware server running on another box which runs fedora 3, and have no problems connecting to it. 

I can telnet to vmware-authd on the ubuntu machine from windows. I checked the logs on the ubuntu machine and couldn't find anythink related to this problem.

---

### Post by SteveHoffmanUK on 2006-07-12
USB DEVICES NOT RECOGNIZED

Excellent HOWTO. Installed WindowsXP, powered up the machine, but it didn't recognize two USB storage devices: an external HDD (Freecom FHD2-Pro) and a 512Kb memory stick (Buffalo clip drive). Both of these are recognised by my Ubuntu 6.06. I tried the VMWare Console, clicked on VM and tried to install these, but under USB, it just says "Empty".

Can anyone suggest how to get these to work in VMWare? Without one of them usable in Windows, there's no point in having VMWare. I need only one Windows program, a WYSIWYG web authoring program (WebStudio). I've got to be able to write its output onto the USB device so that I can upload it using Ubuntu. At the moment there is no way to commmunicate between my virtual XP machine and my Ubuntu one.

---

### Post by ricnmar on 2006-07-12
The Official 1.0 version has been released!

No more beta!

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

ricnmar

---

### Post by samuelkarush on 2006-07-13
I have had great luck with VMserver, file sharing, performance, etc. 
 I set it up with only a 3g hard drive. I can add more hard drives, but they aren't recongnized by the guest OS (Winxp).
 
can I get more memory into the guest OS without reinstalling?

sam

---

### Post by scottd23 on 2006-07-13
so how do you upgrade from 1.0.0 build-27828 to new non beta version without breaking everything again..

---

### Post by Peturrr on 2006-07-13
> **scottd23 said:**
> so how do you upgrade from 1.0.0 build-27828 to new non beta version without breaking everything again..
I'm installing it right now, so we'll know it soon :)

==

You can just download the 1.0 version, and install it exactly the way you installed the beta version. It automatically uninstalls the previous version while keeping your virtual machines. Then it installs the new version and you are up and running.
Don't forget to install the new VMWare Tools.

---

### Post by mwolfe on 2006-07-13
I downloaded and installed the new version, works perfect, no problems.

Before you install make sure you kill all vmware running programs or the install will fail (don't worry it fails pretty much immediately)

to kill vm apps type
ps aux | grep vm
then manually kill all the programs that come up related to vmware.. should be obvious.. 

sudo killall [vmappname here]

---

### Post by pcolamar on 2006-07-13
I screwed up my old installation (that btw never worked !) and now when I try again from scratch I get :

----------------------
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware/vmware-uninstall.pl.

Failure

Execution aborted.
----------------------

actually the "/usr/bin/vmware" does not exists on my disk.

How can I start from scratch ?

Thanks

---

### Post by Peturrr on 2006-07-13
=> pcolomar 
I suggest you post your question on the vmware server forum from vmware itself since they are much more likely to know the answer.
[http://www.vmware.com/community/thread.jspa?threadID=48107&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=48107&tstart=0)

---

### Post by qdvubun on 2006-07-13
help  I'm stuck on this part
#  Insert your Windows (XP) CD into your CDROM drive
# Open the VMware Server Console
# select 'Create a new virtual machine'

where is create a new virtual machine option? it only popup as an open virtual machine dialog.

---

### Post by pcolamar on 2006-07-13
> **Peturrr said:**
> => pcolomar 
I suggest you post your question on the vmware server forum from vmware itself since they are much more likely to know the answer.
[http://www.vmware.com/community/thread.jspa?threadID=48107&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=48107&tstart=0)

And right you were !!
I report for who may be concerned the answer from nick.couchman from the vmware forum that solved the problem 
--------------nick.couchman --------
Look for the /etc/vmware directory and either move it to a different location or remove it altogether. 
----------------

---

### Post by BlackMambo on 2006-07-13
upg to latest version :eek:

---

### Post by qdvubun on 2006-07-13
oops I" posted in the wrong section,

I just finish install the vmware and made a new virtual machine windows xp follow the direction in the how to. When I click on power on this virtual device this appear:

unable to change virtual machine power state: could not execute /usr/lib/vmware/bin/vmware.vmx

I tried all the different setting in the CD Rom section but no help.
the windows xp is aldready in the drive.

---

### Post by MystaMax on 2006-07-13
> **krazykirk said:**
> Wow! It works great! Great guide btw!

But i'm having 1 problem!

I press the "full screen" button, and i get a error!

```
Unable to find an appropiate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.
``` 
I think it means Xorg.conf in the same directory, but i have no idea to "add the guest mode."

I'm going to restart X now to see how that goes!

I'll post results here.

I'm having the same problem:

[I]Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.

Failed to switch to full screen SVGA mode.

[/I]I'm not exactly sure what vmware wants me to do. I attempted to browse that directory it specified, but there is no such XF86Config folder (or file for that matter). 

I think it wants me to edit my xorg.conf file, but I'm not sure what or where i'm suppose to insert/edit the file.  I am attempting to go full screen on a monitor w/ a resolution of 1280x1024. On windows, if you go full screen, it'll just place Any advice? Thanks.

---

### Post by mekas2024 on 2006-07-13
> **mekas2024 said:**
> Hello , first of all this its a greeat how-to, i have everything working fine, but.. my only problem its the sound, i add the device in the vmware machine settings, but when i power on the virtual machine it says this warning message>

Failed to open sound device /dev/dsp: Device or resource busy
Virtual device sound will start disconnected.

I think that its because ubuntu its using it ! 

Any Ideaas???

Thanks and i hope someone help mee!

Regards

MeKaS
Hello people, after look for a while on the net and not get an answare of how to make work my sound on VWware running windows xp pro, well i found how to make it and will work 4 everyone!! :D 

you just need to kill the esd process... u can kill it from a terminal :twisted:  with:
sudo killall esd or from system monitor ending the process called esd.

After this u can initialize ur vmachine and will work fine, then when u want sound on ubuntu again u need to disconect the sound device from the virtua machine u can do this from the menu:

VM -> Removable Devices -> Sound Adapter -> Disconect

after doing that u gotta re initialize the esd process in ubuntu, u can do this by ALT+F2 and then writte esd 
 
Sound a little bit complicated :???:  ,  but its :-D  not and also its the only way that i found to do it :p .

Well... anyway i recomend to dont use sound on the host OS because this its a waist of resources!! u dont need sound for the little things that u do in Windooozz

Well C yaa later people

Viva Mexxxico!!! :mrgreen: 

Regards

MeKaS

---

### Post by Peturrr on 2006-07-14
> **MystaMax said:**
> I'm having the same problem:

[I]Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.

Failed to switch to full screen SVGA mode.

[/I]I'm not exactly sure what vmware wants me to do. I attempted to browse that directory it specified, but there is no such XF86Config folder (or file for that matter). 

I think it wants me to edit my xorg.conf file, but I'm not sure what or where i'm suppose to insert/edit the file. I am attempting to go full screen on a monitor w/ a resolution of 1280x1024. On windows, if you go full screen, it'll just place Any advice? Thanks.

I also suggest that you post this on the vmware forum. It looks like they are very able to solve this problem! Please post the solution here if you get one.
[http://www.vmware.com/community/thread.jspa?threadID=48107&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=48107&tstart=0)

---

### Post by Peturrr on 2006-07-14
> **qdvubun said:**
> help  I'm stuck on this part
#  Insert your Windows (XP) CD into your CDROM drive
# Open the VMware Server Console
# select 'Create a new virtual machine'

where is create a new virtual machine option? it only popup as an open virtual machine dialog.
It should be available on the localhost tab. Or you should be able to open the File Menu ==> New ==> Virtual Machine

---

### Post by PPower on 2006-07-15
I need some help getting the sound set up. I enable a sound card and when I start up the guest I get this error (on the host, but the emulation carries on minus sound): Failed to open /dev/dsp. Device or Resource Busy

---

### Post by appis on 2006-07-15
I got my sound working with this help.
[http://www.vmware.com/community/thread.jspa?messageID=355454&#355454](http://www.vmware.com/community/thread.jspa?messageID=355454&#355454)

---

### Post by utnubu001 on 2006-07-15
is it possible that u can do it with an existing windows partition?

---

### Post by mekas2024 on 2006-07-15
> **PPower said:**
> I need some help getting the sound set up. I enable a sound card and when I start up the guest I get this error (on the host, but the emulation carries on minus sound): Failed to open /dev/dsp. Device or Resource Busy


Hey PPower...why dont u read my last post... thats gotta work for ur sound problem!!!!!:D

Take care

MeKaS

---

### Post by samuelkarush on 2006-07-16
I am getting this error during installation.
Not quite sure how to fix it.
any suggestions?
thanks,
sam


What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

***update***

Fixed it. I had installed the dependencies, but for some reason I had to reinstall them, and now it works.

---

### Post by Hellaxe on 2006-07-17
> **utnubu001 said:**
> is it possible that u can do it with an existing windows partition?

Yes. If you have a ghost (or whatever) image but first you have to create the virtual machine then you do the procedure just like in an real box.

---

### Post by Sq322 on 2006-07-17
VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/<username>/.vmware/preferences": Permission denied.



this is the error i get when trying to run it, when i click on the vmware icon to run it, it never opens. the only way I can force it is by running  it in terminal mode.
the only way i can run it is without error is via  'sudo'

---

### Post by Peturrr on 2006-07-17
Sq322

Don't know why it says so, but this should get you rid of the error
```

sudo chown *username.username* -R /home/*username*/.vmware

```

It gives you the permissions of the .vmware directory and all underlying files. Which is save, since all files in your homedirectory normally should be yours.

---

### Post by Sq322 on 2006-07-17
Thx Peturrr...I assume this does it permanently

---

### Post by SteveHoffmanUK on 2006-07-17
How do I uninstall VMware Server? I installed it following the instructions in this thread, that is, I used the apt-get command. It doesn't show up in either of my two GUI installers -- Autmatix or Synaptic --.

Can someone tell me how to get rid of all the stuff that got downloaded with my spt-get so that I get a nice clean uninstall?

Many thanks

---

### Post by oolunchbox on 2006-07-17
For the life of me I cannot seem to get my networking, Internet connection, and USB drives to work.  I've setup VMware server and installed XP just fine but I cannot get the 3 above mentioned items working.  My ethernet adapter says it cannot be started yet I have no problem with it in Kubuntu? anyone?

---

### Post by Eric_T on 2006-07-17
> **SteveHoffmanUK said:**
> How do I uninstall VMware Server? I installed it following the instructions in this thread, that is, I used the apt-get command. It doesn't show up in either of my two GUI installers -- Autmatix or Synaptic --.

Can someone tell me how to get rid of all the stuff that got downloaded with my spt-get so that I get a nice clean uninstall?

Many thanks

```
apt-get remove --purge packagename
```

---

### Post by Sq322 on 2006-07-17
Thx to you Peturrr, i am now up and running off of the existing windows install on my laptop
Last issue is the fact that when i boot into windows from vmware it asks about activating my copy of windows
...what gives?

One thing i also still cannot do is mount the existing install unless i run Sudo

---

### Post by gamerteck on 2006-07-17
Great tut! Installing XP as I write this.

The only thing I had to do was install the linux headers and I was all set with the rest.

---

### Post by SteveHoffmanUK on 2006-07-17
To Eric_T: 
thanks for the uninstall code; I really appreciate it.

to oolunchbox:
Join the club! I installed Vmware server according to this Howto. It seemed to be working fine when I installed XP, but it just won't "see" either of my two USB disks (small memory stick and an 80Gb external hdd). That means I have no very practical way of exchanging data with my Ubuntu system and is therefore completely useless to me.

No one has answered my request for help, so I have no choice but to uninstall it. Maybe you will have better luck.

---

### Post by SteveHoffmanUK on 2006-07-17
To Eric_t:

I tried your code and got this result:
```
steve@steve-desktop:~$ sudo apt-get remove --purge vmware
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vmware

```

Yet, when I type in "vmware", I get this:
```
steve@steve-desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
steve@steve-desktop:~$
```

But the next thing that happens is that my VM comes up! What's going on? What is the server package called if it's not "vmware"?

---

### Post by oolunchbox on 2006-07-17
I did discover how to use the USB devices, you have to start the virtual machine, then click the VM menu> removable devices> USB and set them up.  It took me a while to get my USB drive to show up in windows but it's finally working. I'm still having trouble with the networking.

---

### Post by SteveHoffmanUK on 2006-07-17
oolunch wrote:
> I did discover how to use the USB devices, you have to start the virtual machine, then click the VM menu> removable devices> USB and set them up.

Well I did all that, of course, but when I get to USB, it says "Empty", unlike the entries for my CD and floppy drives, which give the choice of "Disconnect" and "Edit". At that point I'm stuck because there's nothing to "set up" when it says "empty", unless I'm missing something obvious. It's a dead end.](*,)

ON EDIT:

Discovered the answer: I powered down my XP vm. Then clicked on VM > Settings > Hardware > Add, and I added a USB Controller. Then I powered up my Windows XP vm and did VM > Removable devices > USB and it shows my two discs plus my printer. So, I am definitely making progress, but I'm still not clear on what I have to do to configure these devices.

Presumably I have to install my printer using the manufacturer's disk. Also I guess I have to do the same with the 80Gb hard disk. But I didn't get any disk with the memory stick, so am not sure what I have to do for that.

Also, when I go to Windows Explorer, it does show Removable disk E: but when I click on it, it says I should insert a disk into it. Hmm. For further report. At least I shall not uninstall VMWare for the moment, although (see previous msg) it is likely I can't anyway. What fun.

---

### Post by nicbink on 2006-07-17
> **SteveHoffmanUK said:**
> oolunch wrote:


Well I did all that, of course, but when I get to USB, it says "Empty", unlike the entries for my CD and floppy drives, which give the choice of "Disconnect" and "Edit". At that point I'm stuck because there's nothing to "set up" when it says "empty", unless I'm missing something obvious. It's a dead end.](*,)

i didn't read the previous posts but did you edit the virtual machine settings and add USB controller? 

mine was empty until i did that then i was able to activate the usb devices. 

the downside is that right now VMServer will present the devices as USB 1.1 to the guest OS.  this is a problem when trying to use an IPod.

---

### Post by SteveHoffmanUK on 2006-07-17
Nicbink

See my edit -- just now I caught on to that and am now making progress, though not without problems. I don't have an IPod, I just have a couple of USB disk devices that I need to write to.

---

### Post by BKK on 2006-07-17
I think I have made a massive noob error while installing VMware server.

During the setup I changed the install directory to my home directory. Since I got errors I realised I should have left the default directory alone. I then ran nautilus as root and deleted all the files in my home directory associated with VMware. Now when I try to do a fresh install, VM wants to execute a file that I have deleted. Since I used root privelege the deleted files are not in my trash bin...

The error I get is "Unable to execute/dir/dir/vmware/vmware-uninstall.pl"
Failure
Execution Aborted

SO...Am I screwed ?

Thanks

---

### Post by nicbink on 2006-07-17
> **SteveHoffmanUK said:**
> Nicbink

See my edit -- just now I caught on to that and am now making progress, though not without problems. I don't have an IPod, I just have a couple of USB disk devices that I need to write to.

Check out the device manager in XP.  See if there are any cluesa as to why they're not connecting.

I just checked on my system and both my external drive and thumb drive were deteted and operational.  It did take my thumb drive a bit to work (it threw up some errors about not connecting/empty/etc) but after waiting a bit it recognized it.

you could also setup the Samba server to share those drives over the virtual network as long as they are accessable on linux.

---

### Post by nicbink on 2006-07-17
> **BKK said:**
> ...I try to do a fresh install, VM wants to execute a file that I have deleted. Since I used root privelege the deleted files are not in my trash bin...

The error I get is "Unable to execute/dir/dir/vmware/vmware-uninstall.pl"
Failure
Execution Aborted

my question is why is it complaining about executing vmware-uninstall when you're trying to install...

verify that you have removed all the vmware files by searching your machine for other files relating to VMWare

```
sudo updatedb
sudo locate vmware
```

then try reinstalling.  extract the tar file to a new dir then run the install script and choose the defaults for everything but where you want the actual virtual machine files to be installed.

---

### Post by manro on 2006-07-18
Hello to all! ... I just fished installing VMWare Server (thanks for the tuto) but I have no enough space in my hard drive for installing WinXP :( ... now ... I have another PC running Windows who have a big HD! ... my question ... is there a way to make some kind of mapping to a share folder on the other PC so I can use it to install the Vitual Machine on that share folder?

Thanks for everything! :-D

---

### Post by BKK on 2006-07-18
Thanks! That was the command I needed. I had a few files hiding in the /etc. It works perfectly now and installed flawlessly.

Peace

---

### Post by Eric_T on 2006-07-18
> **SteveHoffmanUK said:**
> To Eric_t:

I tried your code and got this result:
```
steve@steve-desktop:~$ sudo apt-get remove --purge vmware
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vmware

```

Yet, when I type in "vmware", I get this:
```
steve@steve-desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
steve@steve-desktop:~$
```

But the next thing that happens is that my VM comes up! What's going on? What is the server package called if it's not "vmware"?

Ah, sorry... that only works if you installed the package via apt-get as well...
Try the download script, in a terminal, run:
sudo /usr/bin/vmware-uninstall.pl

---

### Post by Megatog615 on 2006-07-18
```
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.15-26-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
/tmp/vmware-config0/vmmon-only/Makefile:89: *** Inappropriate build environment: you wanted to use gcc version 4.0.3 while kernel attempts to use gcc version 3.4.6.
/tmp/vmware-config0/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc -m32 with symbolic link to /usr/bin/gcc-4.0.  Stop.
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

This happens whenever I run the vmware-config.pl, and compile the module.

---

### Post by Peturrr on 2006-07-18
megatog615=> The error message complains about you using gcc 4 while the kernel is gcc 3.4. Or maybe the other way, it's not very clear.
If you are on breezy, make sure you execute ```
export CC=/usr/bin/gcc-3.4
``` before running the vmware config. If it still not works try ```
export CC=/usr/bin/gcc-4
``` Hope this is going to help you.

---

### Post by Megatog615 on 2006-07-18
I'm running Dapper. I get the same error after doing what you told me.

---

### Post by SteveHoffmanUK on 2006-07-18
Having sorted my USB problem in VMware server :) now I turn to trying to connect my wireless card to my home network. 

Host computer runs Ubuntu 6.06; connects via wlan0 using D-Link AirPlus DWL-520 wirless PCI adaptor to a DHCP network with WEP encryption. Using a Netgear DG834GT wireless router to access the Internet and provide the wireless network.

Guest system on VMWare is Windows XP Home. VMWare console 1.0.0 build-28343. I am trying to get my wireless connection working in XP but no success so far. Wireless is running happily in Ubuntu. My reading of other threads suggests that I may need to bridge my XP machine to my Ubuntu host, but, if that's true, I haven't a clue how to do that.

Can someone take me step-by-step through this process or else tell me what I do need to get my XP guest to have Internet access?

---

### Post by Oblong_Cheese on 2006-07-18
I'm having major issues with some kind of memory management bug within the vmware-dhcpd process. I can install VMWare and its dependencies fine, get VMWare server running fine, and I've even managed to install XP fine (with networking disabled), but once I enable the virtual networking components of the VMWare software (/etc/init.d/vmware start), all hell breaks loose. Not only does the virtual operating system (XP) crawl to a halt, so does the host operating system (Ubuntu Dapper 6.06), and the cause?

The vmware-dhcpd process is using approximately 900Mb of physical memory! I discovered this simply by starting the VMWare services as normal, then starting the Server Console, and watching the output of top in a terminal window.

Has anyone else experienced this problem? Anyone know of a way to fix it?

I think a nice workaround would be to disable the NAT networking functions and have the virtual machine's network adapter bridged to the host's network adapter, thus they are on the same network and the VMWare software needs not initialise any dhcp daemons.

*Edit*:

I have just reconfigured my VMWare to not use NAT and now I am running XP under VMWare without any noticable slowdown to my host OS, Ubuntu!

---

### Post by nicbink on 2006-07-19
> **SteveHoffmanUK said:**
> ...I may need to bridge my XP machine to my Ubuntu host, but, if that's true, I haven't a clue how to do that.

Can someone take me step-by-step through this process or else tell me what I do need to get my XP guest to have Internet access?

Your guest OS will not see the wireless/wired network device.  It will only see the VMWare Network Device.  

To change the network settings you'll need to edit the Virtual Machine settings in the VMWare Console.  (Edit settings button under start virtual machine)
In the setup you will see the Ethernet device and options to the right.
     Bridged - it will use your network card as a "bridge" to your router.  the IP address for the guest OS will be assigned like any other device on your network
     NAT - will use your host OS (ubuntu) as a router type device that the guest OS will sit behind and receive DHCP settings.
     Host-only - private network between host and guest

When I am connected to a network (with internet available) I use bridged but when Ii am at work and can't connect to a network I use Host-Only so I can connect to my samba share on the host OS.


If you setup bridged then you should be good to go.  Any configuring that you'll need to do will be on your GuestOS with that setting.

---

### Post by SteveHoffmanUK on 2006-07-19
Nicbink

Thanks very much for trying to help me sort out this problem.

I started my virtual machine and then edited the virtual machine settings by adding an ethernet device and made it bridged. This seems to be the only type of network device you can add, although, of course, it's not what I have. I don't have an ethernet device, I have a wireless one. So I do that, otherwise I have no network device and WinXP will complain about that if I try to set up a network.

However, when I then power up my guest (WinXP) system I get this warning message:
```
WARNING: Could not open /dev/vmnet1: No such file or directory
Virtual device Ethernet0 will start disconnected.
```

So I click on OK (no choice, really). XP then announces that it has detected a new network device installed and invites me to set up a network by running the network setup wizard. So I do that, and XP takes me to Network Connections, where it shows that I have set up a "Local Area Connection, a network cable is unplugged, VMware accelerated AMD PCNet adapter" 

Hmm. If I right-click on this I have several options: Disable, Bridge Connections, Create Shortcut, Rename, Properties. I'll try Bridge Connections. This produces this message:
```
To create a network bridge, you must select at least two network connections that are not being used by Internet Connection Sharing or the Internet Connection Firewall.
```

Oh yeh? So I click OK on this amazingly unenlightening message. The window disappears and so do the last remnants of my understanding.

So now in Windows I have a LAN connection with a cable unplugged, whatever that means. What I DON'T have is a wireless LAN, which is what I really want and what I have running in Ubuntu quite successfully. 

HELP!

---

### Post by nicbink on 2006-07-19
When you originally setup VMServer which network device did you select?

Example: I have wireless and wired which are eth1 and eth0 respectively.  When the vmware config (vmware-config.pl) ran I selected eth1 as the network device.

In the virtual machine settings when it says Ethernet it will mean which ever one you selected in the host config (wireless or wired).


If Windows complained about the cable being unplugged I would bet that you specified the wired connection in the setup.  Re-run vmware-config.pl and when prompted to change network settings click yes and choose the wireless device (probably going to be eth1 unless you specified otherwise)



Someone else may know how to enable both devices for the virtual machine...

---

### Post by SteveHoffmanUK on 2006-07-19
Nicbink wrote:
> If Windows complained about the cable being unplugged I would bet that you specified the wired connection in the setup. Re-run vmware-config.pl and when prompted to change network settings click yes and choose the wireless device (probably going to be eth1 unless you specified otherwise)

Brilliant, absolutely brilliant! Did as you said, and my connection now works. 

To be honest, when I ran the setup first time, I didn't really have a clue what all those questions were about, so I pretty much hit return to accept all the defaults. This time I chose wlan0, which somehow seemed the right choice to make, and it was.

I am not actually planning on using my wireless connection in XP very much, certainly not for Internet connection, but I needed it to authenticate my XP installation and also to register the other piece of Windows software that I can't find a good Linux equivalent for.

Now I'm in business, and thank you again for making it happen. \\:D/

---

### Post by mr. B on 2006-07-20
@Peturrr

Thanx! I installed VMware, works great!

no more rebooting :D

---

### Post by Sq322 on 2006-07-20
My lingering issue is with windows activation. my windows install thinks it needs to be  activated.....anyone figure out how to deal with this ?](*,)

---

### Post by landwomble on 2006-07-20
> **mlind said:**
> Very nice guide, thanks!

I've been keen for some time to try VMWare on Ubuntu, but didn't have nerve to do
it yet.

I guess it's out of question to use already installed XP on VMWare ?

No, you could use an existing install.  Ghost a copy of it to a file, then using ghost on the virtual PC import it.  you may have problems with a change in hardware, but it's doable...

---

### Post by Sq322 on 2006-07-20
I did this but am having a devil a time now. Windows is asking to activate and i have one day left before my entire windows install dies (or so it seems) unless someone can tell me otherwise how to do it

---

### Post by urusaiyatsu on 2006-07-20
> **SteveHoffmanUK said:**
> oolunch wrote:


Well I did all that, of course, but when I get to USB, it says "Empty", unlike the entries for my CD and floppy drives, which give the choice of "Disconnect" and "Edit". At that point I'm stuck because there's nothing to "set up" when it says "empty", unless I'm missing something obvious. It's a dead end.](*,)

ON EDIT:

Discovered the answer: I powered down my XP vm. Then clicked on VM > Settings > Hardware > Add, and I added a USB Controller. Then I powered up my Windows XP vm and did VM > Removable devices > USB and it shows my two discs plus my printer. So, I am definitely making progress, but I'm still not clear on what I have to do to configure these devices.

Presumably I have to install my printer using the manufacturer's disk. Also I guess I have to do the same with the 80Gb hard disk. But I didn't get any disk with the memory stick, so am not sure what I have to do for that.

Also, when I go to Windows Explorer, it does show Removable disk E: but when I click on it, it says I should insert a disk into it. Hmm. For further report. At least I shall not uninstall VMWare for the moment, although (see previous msg) it is likely I can't anyway. What fun.


Hi,

When I try this the 'Add', 'Remove' options are greyed out in the Settings > Hardware tab. USB works fine in Linux. How do I add the USB controllers in VMWare?

Thanks.

---

### Post by dr_mikeyboy on 2006-07-21
problem:

when trying to reconfigure vmware after kernel upgrade i get this error message:

```
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Workstation

Execution aborted.

mikeyboy@mikeyboy:~/VMware Workstation 5.5.1/vmware-distrib$  
```

now i really dont know what to do, even tried to reinstall, but got same error message. what to do? :-k

---

### Post by dr_mikeyboy on 2006-07-21
doesnt matter if i install server or workstation, it wont work since yesterday when i got a kernel headers upgrade.

everytime i try to reinstall i get this message:

```
Warning: could not find /tmp/vmware-config2/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config2/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config2/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config2/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config2/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config2/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

mikeyboy@mikeyboy:~/tmp/vmware-server-distrib$  
```

anyone else got this problem? what to do?

---

### Post by Swab on 2006-07-21
> **urusaiyatsu said:**
> Hi,

When I try this the 'Add', 'Remove' options are greyed out in the Settings > Hardware tab. USB works fine in Linux. How do I add the USB controllers in VMWare?

Thanks.

You need to stop the virtual machine first.

---

### Post by urusaiyatsu on 2006-07-21
> **Swab said:**
> You need to stop the virtual machine first.

Yeah, this is when the VM is stopped...?! I can't edit any of the hardware settings.

Edit: Sorry > it was only Paused! Thanks.

---

### Post by GreyGhost_NZ on 2006-07-22
Worked first time without any problems. Goodbye dual boot :D

---

### Post by seshomaru samma on 2006-07-23
I followed the instructions on the first post but when vmware console comes up - it is empty (look at the screenshot)
When I run it from the terminal this is what I get:
```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
GTK Accessibility Module initialized
*** glibc detected *** free(): invalid pointer: 0x0939bc78 ***

```


I dont know if it's related but I've been having problems with skype (unsolved yet) whenever I ran it I get a smilar error :
```
*** glibc detected *** free(): invalid pointer: 0x08a246a8 ***
Aborted
```
Someone said it might be realted to SCIM , I wonder if anybody managed to run VMware alongside SCIM?

---

### Post by petersjm on 2006-07-26
Excellent HowTo. Thanks a lot! My only problem now is that WinXP is saying my product key is invalid when I try to activate it. I've got a number to call which I'll do tomorrow. If they say it *is* invalid, I'll be straight on the phone to Dell! Grrr

---

### Post by Swab on 2006-07-26
> **petersjm said:**
> Excellent HowTo. Thanks a lot! My only problem now is that WinXP is saying my product key is invalid when I try to activate it. I've got a number to call which I'll do tomorrow. If they say it *is* invalid, I'll be straight on the phone to Dell! Grrr

Standard BS... just phone them and they'll sort it out.

---

### Post by Sq322 on 2006-07-26
@petersjm:Are you booting from an existing partition or from a newly created one ?

---

### Post by petersjm on 2006-07-26
> **Sq322 said:**
> @petersjm:Are you booting from an existing partition or from a newly created one ?

Newly created, through vmware. Does it make a difference?

To be honest, I wish I didn't have to use WinXP at all, but I need it for work - I need to use Quark and Photoshop. Other than that, I don't need it.

---

### Post by pollock.tar.gz on 2006-07-26
i tried to install vmware, i used all defaults, and i get this error:

```

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]
Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-26-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.15-26-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
/tmp/vmware-config1/vmmon-only/Makefile:89: *** Inappropriate build environment: you wanted to use gcc version 4.0.3 while kernel attempts to use gcc version 3.4.6.
/tmp/vmware-config1/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc -m32 with symbolic link to /usr/bin/gcc-4.0.  Stop.
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

any ideas?
thanks in advance, pollock

---

### Post by nicky.7 on 2006-07-27
I have no time to read all the entire thread. I can't install vmware-tools in ubuntu dapper. I know is a well known problem.
Do you know if someone has solved it? Thanks

---

### Post by Kuraboy on 2006-07-27
hi! thnx for a good how-to!:)

but how can I get access to the other HDD from inside the vmware WinXP?

---

### Post by pinklerose on 2006-07-27
After instal vmware, recently when I shutdown computer or restart I've this msg.:
```
[17204264.7000000] unregister_netdevice waiting for vmnet1 to become free. Usage count=1
```
This lines multiply many times on screen and computer don't turn off.
How to solve this problem?

*sorry for my weak english*

---

### Post by Sq322 on 2006-07-27
> **petersjm said:**
> Newly created, through vmware. Does it make a difference?

To be honest, I wish I didn't have to use WinXP at all, but I need it for work - I need to use Quark and Photoshop. Other than that, I don't need it.
I feel your pain and am in the same boat as far as  needing it  at work.
The diffrence in booting from a existing install is that usually makes the machine think your existing install needs activation..
Your problem should be rectified with a phone call

---

### Post by petersjm on 2006-07-27
@Sq322: Thanks. I called them this morning and got a new code from them to enter into the dialogue, which I'll do when I get home.

Now for another question: Can I open a virtual window in a virtual window (if you see what I mean)? If I run WinXP through vmware on my home PC, can I then run another virtual program inside that XP window to hook up to my work's desktop - with whatever package my company wants me to install; can't think what it's called...)

---

### Post by Sq322 on 2006-07-27
I think i get the jist , you should be able to use terminal services to connect to your work desktop from within the vmware console..i never tried it though..

---

### Post by petersjm on 2006-07-27
Thanks Sq322. Terminal services. That rings a bell. Cheers.

---

### Post by Sq322 on 2006-07-27
> **petersjm said:**
> Thanks Sq322. Terminal services. That rings a bell. Cheers.
Good luck!

---

### Post by bomanizer on 2006-07-27
> **PhrankDaChickenGeek said:**
> SCORE! Got widescreen working. I can now use Windows XP in fullscreen at 1920x1200

Followed this:

[http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1003](http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1003)

Make sure to do step #9, otherwise it might not work.

How, exactly? ..a bit confused here :rolleyes: 

Do I need to edit the registry values on my XP installation (guest), or some configuration on my VMWare installation...?

Thanks in advantage!

---

### Post by userundefine on 2006-07-27
Great howto, worked seamlessly.

One question for anyone, since I've never used this amazing program before.  Is there a way to move files in between your desktop and the virtual machine?

---

### Post by Peturrr on 2006-07-28
@pollock.tar.gz

The error message complains about you using gcc 4 while the kernel is gcc 3.4. Or maybe the other way, it's not very clear.
 If you are on breezy, make sure you execute       Code:
     [LEFT]```
export CC=/usr/bin/gcc-3.4
```[/LEFT]
   
  before running the vmware config. If it still not works try  ```
export CC=/usr/bin/gcc-4  
``` 
  Hope this is going to help you.

---

### Post by mcman42 on 2006-07-28
Error: Sound device busy (/dev/dsp). As a result no sound available.
Any solutions fo that?

---

### Post by mcman42 on 2006-07-28
Anyone?

---

### Post by from_beyond on 2006-07-28
edit:
Thanks to JONTXO for the help on file sharing . It works!
"to share files from vmware windows with linux you only have to set up shared folders on windows. Then from nautilus go to archive -> connect with server.

to share folders from linux with vmware windows you have to right click on a folder and select share folder with smb. In general configuration of the files shared with windows select the name you want for you computer but for the workgroup put MSHOME, and select not to use a wins server.
then you have to add an user to samba, with the command:
sudo smbpasswd -a user_name
After that in windows go to net folders and there you will see on the microsoft windows net the workgroup of the folders you have shared."

my screenshot of Drake and Vmware:
[http://users.lmi.net/subjazz/images/screenshot.png](http://users.lmi.net/subjazz/images/screenshot.png)

---

### Post by miikkee on 2006-07-28
So, I just read everything. I learned that it is possible to use an already installed windows with VNWARE. Wesh. Who wants to be the good Samaritain and explain it step by step... I'll love you forever... 

Miikkee

---

### Post by Kuraboy on 2006-07-29
> **from_beyond said:**
> 
Thanks to JONTXO for the help on file sharing . It works!
"to share files from vmware windows with linux you only have to set up shared folders on windows. Then from nautilus go to archive -> connect with server.

to share folders from linux with vmware windows you have to right click on a folder and select share folder with smb. In general configuration of the files shared with windows select the name you want for you computer but for the workgroup put MSHOME, and select not to use a wins server.
then you have to add an user to samba, with the command:
sudo smbpasswd -a user_name
After that in windows go to net folders and there you will see on the microsoft windows net the workgroup of the folders you have shared."

I cant share Linux with Windows, havnt tryed the other way yet...

I get a message when trying to view "View workgroup computers" 

'Workgroup is not accessible. You might not have permission to use this network resource. Contatct the admiistrator of this server to find out if you have access permissions.

The list of servers for this workgroup is not currently available'

thnx for nay help :)

---

### Post by petersjm on 2006-07-29
Just a question for anyone who can answer... WinXP through vmware doesn't seem to recognise any CD-Rs or CD-RWs I put in the drive. It still thinks there's a different CD in there... Any one got any suggestions?

**EDIT:** My bad. I powered the vm-window off and on again, and now it seems to be okay... Should have done that first! :D

---

### Post by Burgresso on 2006-07-29
A quick question b4 I decide to install or not: does this allow you to access files Ubuntu files with software the XP install? Could you browse with IE files on the Ubuntu system, and can you save from the XP install to ubuntu?

gracias

burgresso

- -- 

Edit: never mind, read a few posts back - I guess not...

---

### Post by pinklerose on 2006-07-30
Howto totally uninstall vmware also deleting config files?
Beagle found some vmware words in sharing system files after used uninstall script.

---

### Post by urusaiyatsu on 2006-07-30
Hi,

VMWare server was working fine up until recently. Now I run vmware and the window loads but stalls, I force quit the window, then vmware runs fine. I'm guessing a recent upgrade somewhere has caused this...? How do I solve?

Thanks.

---

### Post by lime4x4 on 2006-07-30
also which version should we download?? They no longer have a beta version

---

### Post by RajivNair on 2006-07-30
hi everyone,

i'm having a rather queer problem.im running Win XP in VMWare n i connect to internet through pppoe so i have used the ethernet connection in VMWare as NAT.but now im not able to connect to net nor browse my LAN thru DC++ unless i switch on my Virtual Machine n also i get an error about my sound device being busy n it isn't used by the Virtual Machine.the internet connection is solved if i keep my settings to bridged but it doesnt work with NAT.any help guys.

thnx in advance,
rajiv

---

### Post by rshel on 2006-07-31
Thanks for the easy to follow guide.  I have a problem, however.  As I'm going through the vmware installalation/creation of directories I get a message saying

"Unable to get the access rights of source file "./vmware-vix/bin".

and the operation aborts.  

I'm pathetically new, so please forgive me if the answer is obvious.

Cheers

---

### Post by rshel on 2006-07-31
Oh yes,

I am never asked for the serial number.

thanks

---

### Post by PingunZ on 2006-07-31
Nice guide, I use it for testing edgy.

---

### Post by orbital on 2006-08-01
Is it possible for me to use an already existing windows xp-install with vmware server? Right now I'm dual-booting and don't really want to re-install xp.

---

### Post by gwi on 2006-08-02
> **lime4x4 said:**
> also which version should we download?? They no longer have a beta version
Just download the 1.0 version, it's the only one there. Why do you want to use a beta version if you can have the 1.0?

---

### Post by gwi on 2006-08-02
> **nicky.7 said:**
> I have no time to read all the entire thread. I can't install vmware-tools in ubuntu dapper. I know is a well known problem.
Do you know if someone has solved it? Thanks
You have to install the vmware-tools in your virtual machine, not in Ubuntu (unless your virtual machine is running Ubuntu :D ).

Let's say you are running Windows XP in your virtual machine (vm).
1. Boot the vm;
2. In the vmware server console menu select VM;
3. Select Install VMWare tools;
4. If you have autrun enabled in your vm, the setup should start. If so, go to step 7;
5. In your vm browse to the CDROM drive. The VMWare tools setup should be mounted as a CDROM;
6. Run setup.exe;
7. Accept the default settings.

---

### Post by SteveHoffmanUK on 2006-08-02
Description of VMWare problem with WebStudio loading

VM Server Console
Version 1.0.0. build-28343
1.54 Ghz AMD Athlon desktop; 384 Kb memory
Host: Linux Ubuntu 6.06 (Dapper)
VM guest: Windows XP Home Edition SP2 128Kb memory

VMWare Server is generally working well hosting my XP system: XP connects to the Internet, accesses internal and external disks, shares files with Ubuntu host, drives my Canon printer, runs Windows apps without problems except for one. WebStudio (WS) 4.0 - web authoring software ( [http://www.webstudio.com](http://www.webstudio.com)) - works when run in Windows XP Home Edition native mode but often fails in VM.

WS provides true WYSIWYG web authoring by translating author-generated screen layouts into graphics and text objects and instructions for producing HTML, and stores all these as a project file which uses a proprietary format called .ows ("only Web Studio"). After starting WS, the user tells it which .ows project file to load. After loading a project, the author can then add, delete and change website pages and then can have WS generate web pages or a whole website for uploading. Although WS contains a webpage uploader, I never use it, but upload using a freestanding FTP uploader.

I am experiencing variable results with WMWare Server when I tell WS to load a project file. Of the 10 .ows project files I try to load, 5 load successfully and 5 fail to load. All 10 files load sucessfully when I run WS in XP native mode. Of the VM 5 failures, 4 fail with the standard XP message "Web Studio 4.0 SP1 has encountered a problem and needs to close. We are sorry for the inconvenience ...." You all know the rest of this message, I'm sure! The other failure to load first causes a Web Studio 4.0 pop-up window to appear with this message: "An error occurred while reading your Project file. an unnamed file contained an unexpected object." Click OK on that and then you get the standard XP message as above.

The obvious question is how do the projects that successfully load differ from those that fail? I wish I knew. Generally speaking, those that fail are the more complex projects, but failure is not just a function of size, as is clear from this table of projects sorted by size:
Proj1 1.7Mb loads
Proj2 2.8Mb loads
Proj3 4.4Mb fails to load
Proj4 13.4Mb fails to load
Proj5 15.7Mb fails to load
Proj6 22.6Mb loads
Proj7 28.5Mb fails to load
Proj8 48.3Mb fails to load
Proj9 64.0Mb loads
Proj10 97.8Mb loads

I am unable to identify any common feature of the projects that fail to load, at least there is no obvious common factor.

Question: are there any features or characteristics of files that might cause VMWare to behave differently in loading them from how XP would behave?

Thanks for any help or leads you can give. Any suggestions would be welcome on how I could test this further.

Note: I have submitted this message to the VMWare Server forum, but no one has replied.

---

### Post by gwi on 2006-08-02
> **Shampyon said:**
> This is a pretty cool guide. I'm in the middle of the install as I type. I have a question, though.
I accidentally made a VM Windows partition for XP, but I made a mistake.

I should have done:
#  select 'Create a new virtual machine'
# => Next => Next => Select Windows Xp

But I actually did
#  select 'Create a new virtual machine'
# => Next => Next => Select Windows 2000

I didn't notice until I tried to install XP on it and it told me it had the wrong boot strap (or something). How would I go about deleting it?
Maybe a bit late (I just discovered this thread). You can go to the virtual machine settings (while the vm is not powered on), and on the Options tab under General settings change the guest operating system selection. No need to delete or reinstal afaik.

---

### Post by gwi on 2006-08-02
> **Trocisp said:**
> I accidentaly put 20 gb instead of 10gb, is there anyway to uninstall it?

I feel like a turd... :(

Did you check the "Allocate disk space now" option? If not, leave things as they are. Your disk image file (*.vmdk) will only grow to the size needed. If you don't use more than 10GB, the vmdk will not be much bigger than that.

---

### Post by gwi on 2006-08-02
> **evand said:**
> (in win xp on vmware server on dapper)
2 - tweak the graphics speed? nvidea card, and I don't need any 3D games, but it would be nice to speed up AutoCAD, Photoshop, and Sketchup, which are really what i need this for right now.
Maybe a bit late (I just discovered this thread). VMWare is sumulating (or emulating?) a PC. That PC does not have an nVidia graphics card. You need to install the vmware-tools in your virtual machine. The vmware-tools contain (amongst others) a video driver and a mouse driver to speed things up.

---

### Post by Kuraboy on 2006-08-02
just a fast question will WMware Server runs faster on dual core?!

---

### Post by martinmaurer on 2006-08-02
hi,

I just published an installation guide for VMware Server V1.0 on Ubuntu 6.06 LTS.

Download: 
[http://www.proxmox.com/cms_proxmox/cms/front_content.php?client=1&lang=1&idcat=11](http://www.proxmox.com/cms_proxmox/cms/front_content.php?client=1&lang=1&idcat=11)

Regards,
Martin

---

### Post by Washington Irving on 2006-08-02
I followed the instructions and everything went fine except for the ethernet connection which I use to connect to the internet with and is fairly important for what I want to use VMware for. I have tried all the different options (nat and so on) but I get this error: > Could not open /dev/vmnet8: No such file or directory
Failed to connect virtual device Ethernet0. this varies slightly between the different options. Should I use "Custom: Specific virtual network" and set the device to it's path in linux? if so then how do I find out what that is? My ethernet connection is onboard and works perfectly in Ubuntu. I am running the 64-bit version.

---

### Post by Just4 on 2006-08-03
I'm having a problem, everything instaleld fine, but how can I get sound to work? I tried adding it but it only lists Autodetect or /dev/dsp - neither work, what do I have to enter in the field to get it to work?

---

### Post by Washington Irving on 2006-08-03
Ok, something really weird and quite disturbing has just happened. I installes VMware Tools as recommended in the HOWTO then I shut down my computer and went to bed. The next morning, I booted up Ubuntu and started VMware but all of he text is replaced with evil box things (screenshots attached)

---

### Post by 0p3r4 on 2006-08-03
Hello,

I've set up the vmware-server on a Ubuntu-driven laptop (Thinkpad R40) and most things seem to work fine. However, I've not been able to get the network to function correctly, the Internet is unreachable.

I've been trying all kinds of configurations in the network-configuration of the server console, and nothing seems to work, among other things i tried setting the "Network Connection" to "Custom" pointing to /dev/wmnet0 which should be mapped to /dev/eth0, my wired ethernet connection. And that didnt solve anything either. Then I found this forum-page and found i hadn't installed the xinetd-package as told in the how-to. Said and done, I installed it and to be safe I also ran the vmware-config.pl application again after doing this, in case something had to be reconfigured in order to work.

After all of this was done, I still can't get in touch with the DHCP-server (at the ISP, I'm not running my own DHCP-server) using "ipconfig /renew" under WinXP. I've tried pinging other machines I have running (including the host of the server) with no sucess. At the moment the NIC-configuration is set to "Bridged" in the settings for the vm.

The one thing I'm noticing that might show something is badly configured from my side is that the icon showing nic-activity (the icon sitting next to the hdd and dvd (when running the vm in windowed mode) is showing no activity at all, whereas the hdd- and dvd-icons are flashing as they should.)

Anyone have any ideas on what i might have done wrong? I would be really grateful for any tips i might get.

PS. I hope my english isn't too bad, and if I've been unclear on anything, please tell me. DS.

---

### Post by oocce on 2006-08-03
Server wasnt free? Vmware server tells in startup that it will expire in 3 days. Im confused!

---

### Post by jstueve on 2006-08-03
you need to register and get a serial number (it is free)

---

### Post by Washington Irving on 2006-08-03
If anyone's VMware has started to display weird characters like mine then I have found the soulution (well miasma did):
> It's caused by the recent update of ia32-libs-gtk. You can revert to version 16 via "Force version" in Synaptic.


I found that at [this thread]("http://www.ubuntuforums.org/showthread.php?t=228518").

---

### Post by OneSeventeen on 2006-08-03
Well, I tried to install vmware player to see if I could just buypass upgrading the server software to 1.0, but it kept giving me errors (after overwriting a lot of the config files).

Now I want to remove it, but I cannot.  Snyaptic acts as though everything went fine, then after I click "close" I get the following error:```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

No matter how often I run dpkg --configure -a I always get the same results.

now I've uninstalled vmware server, still get the same errors as above, and when I try to isntall the newer vmware server, it tells me that each file it is trying to copy already exists, do I want to overwrite?

I've been holding down the enter key for about 5 minutes, and it is getting very tiring...

Did the uninstall script do anything?  Or did it just remove some system links?

---

### Post by OneSeventeen on 2006-08-03
It just finished copying the files, ending on "Unable to stop services for VMware Server: Execution aborted"

After rebooting and running the vmware configuration script again, it is working just fine.

Now the only problem is I have a non-functioning vmware player that is sitting on my machine... if I uninstall it, I'd imagine it would delete a few config files among other things neccessary for the vmware server, if I leave it on, I still can't use it since 1. it didn't work properly to begin with, and 2. it uses the same location for config files and whatnot...

oh well, live and learn, I'm back to having windows on linux, so I can't comlain, hopefully my annoyance and rantings will help someone else that has similar problems.

---

### Post by bruenig on 2006-08-03
flawless, much much thanks, only unfortunate part about this was I spent 3 hours or so setting up the xp virtual machine because I couldn't get something to run in wine, then after setting up the virtual machine realized that I didn't do it properly and was then able to get it running in wine.

---

### Post by jstroot on 2006-08-03
Somone posted this same error earlier, but I did not see the solution.
```
Unable to add virtual machine "/home/jstroot/progs/vmware/Virtual_Machines/Windows XP Professional/Windows XP Professional.vmx" to the inventory: No permission to perform this operation
```

That is when I try to open the virtual machine I made. I made sure that everything in my home directory is owned by me. I changed some of the permission and such. Nothing helps.

Any ideas?

---

### Post by fjm03 on 2006-08-03
Dapper, as host, refuses to release its parallel port to a guest.

The bios on the box has the parallel port configured for ECP.

Dapper has both parport_pc and ppdev compiled into its kernel and they both show active.

The virtual XP machine running under VMware Server 3, can't gain access to Dapper's parallel port either using its default serarch path, /dev/parport0, or the Auto Detect setting.

LTP1 is working properly on the vXP machine but can't communicate with the physical port controlled by the host.

Dapper has a network printer configured using CUPS (IPP) emulation.

Any advice or help would be appreciated.

New to Linux and Ubuntu

---

### Post by oocce on 2006-08-04
> **jstueve said:**
> you need to register and get a serial number (it is free)

I have serial number, but it's kind of a beta serial? I have license time one month! What I have done wrong?

---

### Post by tiddlygoose on 2006-08-04
If you have the beta version then it will expire, mine did. Just download the 1.0 release version of VMWare Server, then get a new serial number and set it back up.

I am running Ubuntu 6.06 on a dual xeon 2.4 system with 1 GB of RAM and I run WindowsXP in vm and it's as fast as any XP machine I've ever run.

I LOVE my Ubuntu and VMWare combo!

---

### Post by oocce on 2006-08-04
> **tiddlygoose said:**
> If you have the beta version then it will expire, mine did. Just download the 1.0 release version of VMWare Server, then get a new serial number and set it back up.

I am running Ubuntu 6.06 on a dual xeon 2.4 system with 1 GB of RAM and I run WindowsXP in vm and it's as fast as any XP machine I've ever run.

I LOVE my Ubuntu and VMWare combo!

Thanks =)

---

### Post by neewby on 2006-08-05
VMWARE trying to connect eth0

I get error message for trying vmserver connect internet for virtual machine XP :

Could not open /dev/vmnet8: No such file or directory
Failed to connect virtual device Ethernet0.





How can I change for right directory to connect eth0???

---

### Post by lime4x4 on 2006-08-05
how do u upgrade the vmware tools?? I've updated to the latest version of server 1.0 went to install vmware tools in cause they were updated as well and when i try to update it tells me i have the following processes that are running

vmware tools service
vmwaretray
vmware user
windows explorer

so it won't update

Any ideas?

---

### Post by PokerFacePenguin on 2006-08-05
> **Washington Irving said:**
> I followed the instructions and everything went fine except for the ethernet connection which I use to connect to the internet with and is fairly important for what I want to use VMware for. I have tried all the different options (nat and so on) but I get this error:  this varies slightly between the different options. Should I use "Custom: Specific virtual network" and set the device to it's path in linux? if so then how do I find out what that is? My ethernet connection is onboard and works perfectly in Ubuntu. I am running the 64-bit version.

I was having a similiar problem, then I used a container from easyvmx.com and used their default ethernet choice.  Give it a shot.

---

### Post by AlanV on 2006-08-05
I am using Drake x64 and Vmware Server. Everything was working fine until the update of a couple of days ago. Using 2.6.15-26-amd64-generic I now have problems whenever I restart my computer.

Trying to run Vmware Server I get:

[B]vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.[/B]

Runninig the command I get:

[B]mhoward@ubuntu:~$ sudo /usr/bin/vmware-config.pl
Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.
[/B]

Once the services are manually stopped I run vmware-config.pl and it configs perfectly:

[B]The configuration of VMware Server 1.0.0 build-28343 for Linux for this running
kernel completed successfully.[/B]

Vmware Server runs fine as long as I do not reboot. If I do reboot\restart I need to go through the entire config setup again!

Any suggestions?

Thanks!

---

### Post by kpurcell on 2006-08-05
> **Just4 said:**
> I'm having a problem, everything instaleld fine, but how can I get sound to work? I tried adding it but it only lists Autodetect or /dev/dsp - neither work, what do I have to enter in the field to get it to work?

I had to do, at someone's suggestion, kill esd (i think it was) in terminal to get it to work.  I've sincer rebooted and it continues to work for me.

---

### Post by neewby on 2006-08-06
starting upvirtual machine i get the following error

Could not open /dev/vmnet8: No such file or directory
Failed to connect virtual device Ethernet0.

---

### Post by neewby on 2006-08-06
> **PokerFacePenguin said:**
> I was having a similiar problem, then I used a container from easyvmx.com and used their default ethernet choice.  Give it a shot.

A you indicating to remove VMserver

and installing vmplayer instead?

---

### Post by Don_DiZzLe on 2006-08-06
> If you have the beta version then it will expire, mine did. Just download the 1.0 release version of VMWare Server, then get a new serial number and set it back up.

I got me a a new key but I cant enter in VMware Server Console, it says I cant enter cuz Im not the administrator.

How do I enter the new key before vmware expires?

---

### Post by stairwayoflight on 2006-08-06
> **marianoi said:**
> 
For some reason I had problem installing a virtual machine if I ran "vmware" so I always do:

sudo vmware

to run it as a super user (correct me if this is not a good policy please)


Hmm.. what directory are the virtual machines being installed into? if i recall earlier in the howto, the author installs them into user's home directories. perhaps the directory you are using requires sudo while the home directory does not?

---

### Post by Jose Catre-Vandis on 2006-08-06
> **mekas2024 said:**
> Hello people, after look for a while on the net and not get an answare of how to make work my sound on VWware running windows xp pro, well i found how to make it and will work 4 everyone!! :D 

you just need to kill the esd process... u can kill it from a terminal :twisted:  with:
sudo killall esd or from system monitor ending the process called esd.

After this u can initialize ur vmachine and will work fine, then when u want sound on ubuntu again u need to disconect the sound device from the virtua machine u can do this from the menu:

VM -> Removable Devices -> Sound Adapter -> Disconect

after doing that u gotta re initialize the esd process in ubuntu, u can do this by ALT+F2 and then writte esd 
 
Sound a little bit complicated :???:  ,  but its :-D  not and also its the only way that i found to do it :p .

Well... anyway i recomend to dont use sound on the host OS because this its a waist of resources!! u dont need sound for the little things that u do in Windooozz

Well C yaa later people

Viva Mexxxico!!! :mrgreen: 

Regards

MeKaS


MeKaS - you are a star! Thanks for this tip. My Ubuntu sound continues to work even after *killall esd* 8)

---

### Post by AlanV on 2006-08-07
Solved my problem:

> I am using Drake x64 and Vmware Server. Everything was working fine until the update of a couple of days ago. Using 2.6.15-26-amd64-generic I now have problems whenever I restart my computer.

Going to Synaptic:Status:Not installed (residual config)

I found traces of a Vmware Player install I thought were gone. 

Deleting the traces eliminated my needing to reconfig each time I rebooted.

---

### Post by Jose Catre-Vandis on 2006-08-07
Here's a little script I wrote that helps to overcome two issues with vmware namely parallel port and sound. On my ubuntu 6.06 this sorts these two issues out, e.g. gives a vm access to the parallel port and enables sound. it will ask you for sudo password, but you have got used to that :-)

```
#!/bin/sh
foo=`gksudo -u root -k -m "enter your password for sudo command" /bin/echo "Do you have root access?"`
sudo rmmod lp
killall esd
vmware
```

Copy this code to a text file and name it vmready.sh or whatever.
Set as executable and then link to your VMware launcher and you are good to go :-)

Also something else that works - Wireless USB adapter in XP vm. Yes, after installing XP as a VM on Ubuntu, and using the bridged networking to access the net, I though I would try a usb wireless adapter. So I disabled the VM network "NIC", installed the drivers in Xp for the wusb nic, and lo and behold it connected up to a wireless network in my locale, giving me internet access via a different route, totally unconnected to my main system. Note: the wusb nic was in no way setup or autodetected by my Ubuntu host (uses prism2_usb).

---

### Post by UltraSonicSite on 2006-08-07
Hey I have a question. Could I install the laptop version of Windows XP on VMWARE?

---

### Post by starscalling on 2006-08-07
what the bloody blinking hell
none of the serial numbers work for the thing ~_________~



-============================-
so um
i went back to the page a number of times
and eventually the serial worked for some reason
ive no idea why ~_~
gawd i hope i dont get emails for all the times i signed up !___________!
installing windows now though :D


mm ok windows installed
very laggy :/
ive noticed that im having a hard time getting the usb bit to work... though i set it up as per this thread
anyone get itunes + ipod to work via vmware ?

---

### Post by rippon on 2006-08-09
Thanks a ton! Worked like a charm on a (nearly) fresh Drake installation. :D

Also, they now just give you the key on their site, right after you register. I haven't gotten an email from them yet :-$

---

### Post by grahams on 2006-08-09
Great guide, thanks.

I've installed XP but I've vmware crash my entire system (6.0.6 2.6.15-26-686) a few times now. Has anyone else had similar issues or know of a fix?

---

### Post by Jucato on 2006-08-09
I followed this guide and was able to successfully install and use VMWare Server. But now I want to remove it completely. I ran the vmware-uninstall.pl script and it says that VMWare Server was removed successfully. However, I can still find traces of vmware in my system, notably in /usr/bin and /usr/lib. So how do I completely remove all traces of vmware?

Thanks!

---

### Post by A.M.D on 2006-08-10
Thanks for thehow to.. 
I followed all the steps and now it comes up with the following error....

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

Please help..:(

---

### Post by blackmh on 2006-08-10
Help please, I'm getting this. I tried to link it but haven't succeed. TIA

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.15-26-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
/tmp/vmware-config4/vmmon-only/Makefile:89: *** Inappropriate build environment: you wanted to use gcc version 4.0.3 while kernel attempts to use gcc version 3.4.6.
/tmp/vmware-config4/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc -m32 with symbolic link to /usr/bin/gcc-4.0.  Stop.
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

---

### Post by Jose Catre-Vandis on 2006-08-10
> **A.M.D said:**
> Thanks for thehow to.. 
I followed all the steps and now it comes up with the following error....

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

Please help..:(


This is usually due to not having the right linux headers installed, although I did have one case where nothing I tried would fix the thing. Might need to check the uninstall thread and start again, but make sure your linux headers match your kernel.

---

### Post by rasjidw on 2006-08-11
> **Anonimoes said:**
> This is a great howto! The only problem I am having is that the virtual machine doesn't want to power up, I get the error message:

Unable to change virtual machine power state: The process exited with an error:
End of error message.

I didn't install windows xp yet so the machine is completely empty. Of course I tried different cd-rom drives, etc. Does anyone have an idea about how to get past this?

Had the same problem.  To get more information, enabled the 'advanced' option 'Run with debugging information'.  Turned out that ~/.vmware was owned by root instead of my normal user.  Once that was fixed, it all worked.

Cheers, Rasjid.

---

### Post by CuBone on 2006-08-11
I run vmware server on Ubuntu 6.06. On the virtual machine I installed Win XP pro. So far so good (Actually it works great). But now to the problem. I want to have direct acess to one of my HD partitions. I can share it on samba and access it that way but its terribly slow. So in the device settings I added the partition so that the vm could access it direct but when i power it on I  get this message ```

Cannot open the disk '/var/lib/vmware/Virtual Machines/Windows XP
Professional/Windows XP Professional-1.vmdk' or one of 
the snapshot disks it depends on.
Reason: Insufficient permission to access file.
```
and then it won't start. 

Does anyone now how I can change the permissions so I can access the partition?

---

### Post by WPAStrangla on 2006-08-11
When installing Windows XP I cant get it to Detect my Boot Disc, I tried many different options but I am still stumped here. Any ideas? ](*,)

---

### Post by Jose Catre-Vandis on 2006-08-11
> **WPAStrangla said:**
> When installing Windows XP I cant get it to Detect my Boot Disc, I tried many different options but I am still stumped here. Any ideas? ](*,)

Have you set the CD to boot first in the Vm's bios?

To do this:

Start the VM
Press F2 when you see the VMware screen (be quick)
You will get a bios screen.
Right arrow across to Boot
Select device using up and down arrows then + or - to change priority
Save Exit and reboot

Have you set up the default CDrom in the VM? Does it point to a physical CDrom or image on disc?

---

### Post by WPAStrangla on 2006-08-11
It Doesnt Seem to be working, here are a few screenshots maybe you can see what I am doing wrong.

[[IMG]http://delta.zshare.net/thumb/400413/thumb.png[/IMG]](http://www.zshare.net/image/screenshot3-png.html)

[[IMG]http://delta.zshare.net/thumb/400411/thumb.png[/IMG]](http://www.zshare.net/image/screenshot1-png.html) 
   [[IMG]http://delta.zshare.net/thumb/400412/thumb.png[/IMG]](http://www.zshare.net/image/screenshot2-png.html)

---

### Post by mitch.c on 2006-08-12
You may have tried this, but I had to turn on the Auto Detect and Legacy Emulation option for my CD-ROM to make it work correctly with VMServer. I noticed it's unchecked in one of your screenshots (screenshot-2.png)

Good Luck.

---

### Post by WPAStrangla on 2006-08-12
> **mitch.c said:**
> You may have tried this, but I had to turn on the Auto Detect and Legacy Emulation option for my CD-ROM to make it work correctly with VMServer. I noticed it's unchecked in one of your screenshots (screenshot-2.png)

Good Luck.

Just tried what you said and nothing. :-k

---

### Post by Pulshion on 2006-08-12
Is there a way to mount ntfs drive in vmware? or mount any drives?

---

### Post by dr.drake on 2006-08-12
hello, 
I just got vmware installed just fine with this guide, so the next step was to install windows. I pop in the CD, and nothing ....
I restart vmware and click "power on this virtual machine". and get this message:
> Bad parameter ide0:0.fileName: no file specified.
Failed to configure disk ide0:0.  The virtual machine cannot be powered on with an unconfigured disk.
so I go to "edit virtual machine settings" and right away get: > Unable to get information for disk (IDE 0:0)
Unable to open file "/media/windows/vmware/": The file specified is not a virtual disk.
so I guess it must be something with the Hard Disk setting, I click on the  Hard Disk, and notice that the Disc File box is empty...
if I click OK to exit the vmware settings screen, it gives me: > Unable to save virtual disk: Please specify the disk file.
so something is trying to tell me I should enter a Disc File, but I can't type anything into the box.
under Disk Information it says: "unable to get information for disk"

please help?

*******************************************

update: 

just for the sake of it, I tried to install a new virtual machine in the host folder ( /home/vmware ), but I really don't have enough space on my linux ext partition. and now it all works!!! it's installing windows..
but that means my whole disk is full now, and I can't even move the things to trash anymore.
if I try to change the host folder to the folder on the fat32 windows partition, it doesn't allow me to...
in my fstab I have the umask set to 000, I tried 007, but that locks more.
I can always just create files fine with the 000 settings but the install stalls here:
> In which directory do you want to keep your virtual machine files?
[/media/windows/vmware/virtual machines]
Unable to change the access rights of the file /media/windows/vmware/virtual
unable to **change** the permissions.... so it won't let me install in a fat partition, I'm really stuck now.

anything i can do about this?

*************************************************

update 2:

tried again in my home folder: 
In which directory do you want to keep your virtual machine files?
[/home/vmware/virtual machines]
but when opening vmware I chose the expert install, and somehow now it DID find the disk file, so everything is ok, vmware is installing XP as we speak (type/read I mean ;))

I'll leave this whole post in, in case other noobs like me run into the same problem.

eric.

---

### Post by Cris987 on 2006-08-12
I kno that some people have this same problem I do:

When vmware is opened, it freezes with a blank screen, then loads when the user kills it or executes a force quit. Is there any fix to this? 

Thanks.

---

### Post by madu on 2006-08-12
can somebody please elp me with this error:

[B]
Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.
[/B]

I get this at the installation. There is no /bin in the /vmware-vix directory.

Can somebody help me please..

Madu.

---

### Post by GadgetsGuy on 2006-08-13
ok I glanced thru all the posts in this thread, but I did not find a definitive answer to my question ...

I installed VMWare Server on a friend's machine running Dapper, and installed WinXP onto that .... I was really amazed at how well it operated, and basically removed any need for a dual booting system.

Now the question I have, is I would like to set my work system up to operate the same way - is it possible for me to mount my FAT32 C drive with my native XP OS on it, so that I can IMPORT the files and such that I need into the virtual machine, and then eventually delete the native XP partition once I have importeed all my needed files??

Has anybody had any luck with this, and is it possible, or do I have to back stuff up and reformat?

---

### Post by theratster on 2006-08-13
This may be stupid, as I am a newbie myself, but for the address of the CD-rom, insert in the CD, when it comes up on the desktop, right click it and find its actual address /dev/whatever or /mnt/whatever and use that address for the CD-ROM.

---

### Post by dr.drake on 2006-08-13
> **GadgetsGuy said:**
> ok I glanced thru all the posts in this thread, but I did not find a definitive answer to my question ...

I installed VMWare Server on a friend's machine running Dapper, and installed WinXP onto that .... I was really amazed at how well it operated, and basically removed any need for a dual booting system.

Now the question I have, is I would like to set my work system up to operate the same way - is it possible for me to mount my FAT32 C drive with my native XP OS on it, so that I can IMPORT the files and such that I need into the virtual machine, and then eventually delete the native XP partition once I have importeed all my needed files??

Has anybody had any luck with this, and is it possible, or do I have to back stuff up and reformat?

well, since I just installed vmware (see above), I tried to do the same.
what I did was set up samba and smbfs through synaptic, and set up a network like that.
I can now basically right click a file (in ubuntu) to make it shared. so you could do that with your mounted Windoze partition: just right click and share.
in VMware windows you then set up a network and you'll see that whole partition as a shared folder.
I used a guide from this forum, I'll look for it, and post a link here asap.

***************************

edit: ok, I used a bit of the first post here: [http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba)

then I installed smbfs as well

then went into system settings to activate,

then I tried right clicking a folder, but got an error message that was resolved through reading and following this:

> I had that same "Make sure that the Perl script 'fileshareset' is set suid root" error at one point. According to the package manager, /usr/bin/fileshareset is installed as part of the kdelibs-bin package. For whatever reason, when the file was installed, the proper permission (the SUID bit) was not set.

The SUID bit allows you to run a program in the security context of the owner of the file. So for example, since root owns that file, a normal user can run the program and it can do things that normally only root could do.

To set the SUID bit:

Code:

$ sudo chmod u+s /usr/bin/fileshareset


That should get your right click file sharing in working order. Once that is working, file sharing should be pretty easy.

then in VMware windows it's just as easy as going to your network places, and clicking the shared file to see.

good luck

---

### Post by cautious on 2006-08-13
[QUOTE=machia;1194897]I got the vmware to work and I can boot to my Windows partition.Thanks for that mate :)
One thing I noticed was that I had Jagged Alliance 2 installed on in windows and it seems to work through vmware. It works smooth as well. It might be that it works through Wine as well but I dont know. My verision is the latest v.1.13 which has lots of cool updates :D

Machia: Did you mean you can you can "switch" to Windoze under (linux) by way of VMWare Player?  You said "boot", but I wonder if you meant you can switch and run it in VMWare Player.

If, in fact, you can switch using VM player, could I get you to spell it out for me?  Your reply seems to be a quick statement of "No worries, mate".  I'd sure like to know how you did that.

Scottish joke:

Liam:  Di' ye see thon clever Yank, then, Aengus?
Aengus: No, Liam, I dinnae.
Liam:  Nar di' I, Aengus, nar di'd I.

---

### Post by Jose Catre-Vandis on 2006-08-13
> **WPAStrangla said:**
> It Doesnt Seem to be working, here are a few screenshots maybe you can see what I am doing wrong.

Why is your cdrom listed as /media/cdrom-1  ?  This seems an odd place to look for it.

Try Autodetect or /dev/hdc as your cdrom setting in VM

---

### Post by UltraSonicSite on 2006-08-13
> **UltraSonicSite said:**
> Hey I have a question. Could I install the laptop version of Windows XP on VMWARE?

Could I?

---

### Post by WPAStrangla on 2006-08-13
> **Jose Catre-Vandis said:**
> Why is your cdrom listed as /media/cdrom-1  ?  This seems an odd place to look for it.

Try Autodetect or /dev/hdc as your cdrom setting in VM

Thank You! I am now current Installing. \\:D/

---

### Post by M4LFUNCT10N on 2006-08-14
While formatting the drive during the XP install(NTFS Quick Format) the install locks up at 20%.  VMware doesn't lock up, I can turn off the virtual machine with no problems, but the XP install quits.  Same thing every time.  Is there something else that needs to be done?  I searched this post for "format", but nothing turned up.  44 pages is a bit much for me to read right now.  Can someone help?

---

### Post by moparfan90 on 2006-08-14
i get this error when im trying to configure vmware

```

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel?
[/lib/modules/2.6.15-26-amd64-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.15-26-amd64-generic/build/include/.. SUBDIRS=$PWD SRCRO OT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
/tmp/vmware-config0/vmmon-only/Makefile:89: *** Inappropriate build environment:  you wanted to use gcc version 4.0.3 while kernel attempts to use gcc version 3. 4.6.
/tmp/vmware-config0/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc with symbolic link to /usr/bin/gcc-4.0.  Stop.
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

what do i do to fix this?

---

### Post by M4LFUNCT10N on 2006-08-14
Just a shot in the dark.  Why don't you try:
```
sudo apt-get update gcc
```

Then run the installer again.  Looks like you're using an old version of gcc.

---

### Post by moparfan90 on 2006-08-14
thanks. now it works.

---

### Post by quad3d@work on 2006-08-14
> **InDenial said:**
> **Setup**

Ubuntu 6.06 TLS
VMware server 1.0.0
Windows XP home
** XGL/Compiz**

ATI Radeon Express 200M
running the fglrx-driver (latest)

**VMware settings**

Edit | Preferenes | Display
Autofit window true
AutoFit guest [COLOR=Red]**false**[/COLOR]

**Changes I made**

**_.vmare/preferences file_**

Besides the changes mentioned earlier in the post about the placements I changed:
```

pref.autoFitFullScreen = "FitHostToGuest"
``` to
```

pref.autoFitFullScreen = "FitGuestToHost"
```

Above is all I needed to get VMWare to work in Xgl/compiz fullscreen again. Running Ubuntu 6.06 32-bit on Pentium D 930 with NVIDIA 6800GT AGP.

---

### Post by stanna on 2006-08-15
that was rather painless to get working. thanks for the guide mate! :)

---

### Post by wazzup on 2006-08-16
I did had to do a

# sudo apt-get install libxtst 

to get libXtst.so.6, but that's just because I installed vmware-server on a machine without Xwindows (it's a server). Thanks for the howto, made installation a breeze. A colleague already had a sarge-image for a vmware client, so I was up and running within 15 minutes.

---

### Post by Lobox on 2006-08-16
hi 

i have problem after deleting folders with vmware
when i tray to install again i've got this
```
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/yaqb/vmvare/vmware-uninstall.pl.

Failure

Execution aborted.

yaqb@ubu:~/instalki/vmware/vmware-server-distrib$

```
howto fix this problem ?? 

sorry for may bad language

---

### Post by M4LFUNCT10N on 2006-08-16
Make sure the window/tab in VM ware for your previous OS is open, then click File-> Remove from Inventory.

---

### Post by Lobox on 2006-08-16
i have this error when i want to install again vmware server not the virtual OS

---

### Post by ntwrkguy on 2006-08-16
I have /dev/hda1 with Ubuntu on it, /dev/hda2 with swap, /dev/hda3 with NTFS Windows XP on it. Loaded up hda3 in VMWare, and when I start it, I get a ERROR 17 in GRUB. Any advice? Thanks!

---

### Post by misse- on 2006-08-16
I edit this since I found a good keyword for my search and fixed my error by apt-getting xlibs-dev.

Now, a question: Can vmware be runned without X? I mean why should X be needed for a daemon. From what I can understand from the howto you are bound to a graphical interface. I hope there is another way.

---

### Post by David TAkle on 2006-08-16
What happened to this issue ??
I've got basically the same problems and I cannot find any cures.
#1 problem: How can I move files between UBUNTU host and Win98 Guest ??  Seems to me this would be one of the main reasons for running a VM and there ought to be a way.

---

### Post by stanna on 2006-08-16
> #1 problem: How can I move files between UBUNTU host and Win98 Guest ?? Seems to me this would be one of the main reasons for running a VM and there ought to be a way.

i simply made a share folder in my ubuntu, and axs it via the network in the windowsXP i installed in vmware. pretty simple :) --hope this helps.

---

### Post by starscalling on 2006-08-16
it phails on grabbing usb port for cell phone
though i would like to know how to mount my ubuntu directories from it

---

### Post by David TAkle on 2006-08-17
> **stanna said:**
> i simply made a share folder in my ubuntu, and axs it via the network in the windowsXP i installed in vmware. pretty simple :) --hope this helps.

Just creates more questions....
1. How do I create a shared folder in ubuntu
2. How do I use the network (Win98) to access shared folders on the system?

---

### Post by bjornb on 2006-08-17
> **LsrLine said:**
> How do I get past this part?

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.
```

Hallo!

Did you manage to sort out this problem? I have the same one!

---

### Post by bjornb on 2006-08-17
Hallo

I've VERY recently begun using Ubuntu (I installed Dapper Drake two days ago!!), and want to install VMware server. I'm having trouble during the installation.

I think its to do with the installation of the linux-headers.

>sudo apt-get install linux-headers-`uname -r` build-essential xinetd
>Reading package lists... Done
>Building dependency tree... Done
>E: Couldn't find package linux-headers-2.6.15-21-386

help :-)

---

### Post by quyne on 2006-08-17
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.15-23-386/include

The directory of kernel headers (version 2.6.15-23-386) does not match your
running kernel (version 2.6.15-26-386).  Even if the module were to compile
successfully, it would not load into the running kernel.


Can anyone help me with this ? Thanks...

---

### Post by snakeloco on 2006-08-17
Hi.
Very nice article.

   One question bothers me, though.
   I have tried to install Windows XP professional on VMware workstation a few months ago in my Debian Sarge machine at home.
   It somehow worked strangely. Everything works okay on Windows, except that sometimes the virtual CPU seems to hang for some seconds and then get back to normal.
   The problem started to annoy me until i decided to give up on Windows XP and try Windows 2000 Professional.
   It works just fine, and is an acceptable option at home.
   Now I have recently upgraded my work machine to a dual dual-core AMD64 processor machine and decided to install Ubuntu Dapper on it.
   Ubuntu Dapper is working just fine, so i decided, well, the machine has awesome 8 gigabytes of RAM, so why not use Windows XP and Ubuntu Linux at the same time?
   I then followed a process almost identical to the one described in this article and got Windows XP installed successfully, and correctly inserted into my work's network.
   However, I get the same behaviour from Windows XP as my past attempt at home: it hangs once in a while, and at work I am usually more stressed out trying to squeeze my available time, so this CPU hanging is quite annoying.
   I haven't got the option to downgrade Windows XP to Windows 2000, so I ask:
   - has anyone had the same problem I'm describing?
   - may this have any relation to Debian, since Ubuntu's flesh is the same as Debian
   - am I doing anything wrong? 

   I am using VMware Server at work (version 1.0.1 build-29996)

   Thank you
   -- Fred

---

### Post by sefs on 2006-08-17
It looks like a new version of the server is out.  I would like to upgrade.

Is it as simple as folling the orginal install steps and just have it overwrite the old version?

Thanks.

---

### Post by M4LFUNCT10N on 2006-08-18
> **snakeloco said:**
> 
   I haven't got the option to downgrade Windows XP to Windows 2000.

Why do you see 2000 as a downgrade?  Do you even know the differences?  They are both based on the same kernel.  The only differences are in the GUI.  Security wise, capabilities... they are equal.  Performance wise... well, it depends on whether you used the XP or "Classic" gui.  I'd use 2000 and not look back.  

Wait... that's actually what I'm doing.  My XP Pro disc is fubar'd so I'm going with 2000 Pro.

---

### Post by xander848 on 2006-08-18
Ok i got a problem while installing this. I went through and did the installation. Everything went succesfully, but now when i type "vmware" in a terminal it says "vmware: command not found"

Any ideas what to do?

---

### Post by jpepin on 2006-08-19
try "sudo vmware"

I know that vmware is finicky about who is allowed to run it

---

### Post by Weav on 2006-08-19
My internet refuses to work in vmware regardless of many configurations I've tried.
Anyone know a way to get the internet working in vwmare windows when it works fine in ubunutu?
Thank you.

---

### Post by Quoth the raven on 2006-08-21
Hi, when I try and power on my virtual machine (Windows XP Professional, not actually installed it yet) I get the following error message:
Unable to change virtual machine power state: The process exited with an error:
End of error message.

Can anyone help? I tried running vmware as root but that didn't help.

---

### Post by toykilla on 2006-08-21
Is there a way to get the proper resolution ? I need 1650x1280 for widescreen. The closes I found after XP install is 1600x1200.

---

### Post by fakie_flip on 2006-08-21
Will using a windows xp virutal machine allow me to do all the things from inside of Linux that can normally only be done with windows xp only such as playing WMA music with DRM and using the wireless network cards that won't work in Linux and other hardware thats not supported in Linux? I guess this is the only way to run Internet Explorer 7 from Linux since Wine is not supporting it yet (it probably will, but not yet because IE7 is fairly new).

---

### Post by fakie_flip on 2006-08-21
Also, I have a few more questions. What about those windows games that seem impossible to get working in Linux? Will they run in VMware server with a xp virtual machine? I know that VMware could slow it down some, but VMware server is not an emulator. Programs are running natively somehow. I don't understand how its programmed and couldn't look at the source code, but I might with qumeu. VMware might play Windows games slow, but what if I have quad core dual Xeons and Opterons with 20 gigs of ram and a 512 megabyte video card and sata2 3 gigabyte per second hard drives, or a super computer with very high processing power? Could I get very many frames per second?

---

### Post by AndyCooll on 2006-08-21
As far as I'm aware using VMware works by "simulating" hardware.So the graphics card the XP image will "see" for instance isn't actually the one in your box but the one "built-in" to VMware servers own configuration. And that one is only bog-standard.

So ...although having a superfast machine will help VMware to run quick it still won't run games very well because you still don't have 3D quality and other whizzo graphics features.

I have an VMware XP image to play Football Manager and the game runs great, but this is because it is a number cruncher not a graphics intensive game

:cool:

---

### Post by AndyCooll on 2006-08-21
And in answer to your previous question ...yes you'll be able to do most of those things. In effect an XP VMware image works by running the operating system inside Linux. A bit like you can view a video within a window, so you can run XP within a window too, and like you can make a video fullscreen, so you can make your XP window fullscreen too. However, it's not just a picture, it's a window into a full-blown OS to the point that you'll need a Windows Key for it, it'll update using WGA etc etc.

:cool:

---

### Post by fakie_flip on 2006-08-22
> **Peturrr said:**
> 
[*]Execute the installation script 
```
sudo ./vmware-install.pl
```
[*]You can accept all defaults, only thing you might want to alter is the directory where the Virtual Machines are stored. I have mine set to /home/username/vmware . But offcourse, just accept the settings you want to.
[*]You will be prompted for your key during the installation. You will find the key in your email inbox
[*]If everything went allright, the installation will finish without any problems[/LIST]

Here is a quote from [https://wiki.ubuntu.com/VmwareServer](https://wiki.ubuntu.com/VmwareServer)
[HTML]The following are notes on successfully completing the installation.

    *

      When asked the following question by the installer, you must enter a different path:

      What is the location of the directory of C header files that match your running 
      kernel? [/usr/src/linux/include]

      Enter the path /usr/src/linux-headers-<version>/include, where <version> is the version number of your kernel, which you may have found earlier by typing uname -a into a Terminal. For example, if the uname -a command gives your kernel version as '2.6.15-25-686', type /usr/src/linux-headers-2.6.15-25-686/include and press Return.[/HTML]

If you don't see it, the directions at this howto and the directions at the  Ubuntu Wiki are not the same. What's correct? Shouldn't only one way work? It seems like this howto is working for many people, but the way on the wiki also worked for the author and maybe more people.

---

### Post by fakie_flip on 2006-08-22
After examining both directories, I found that both will work. The real location of the C header files is in the
/usr/src/linux-headers-2.6.15-26/include
and the location that the default path the vmware script uses contains symbolic links to the real location, so either one should work.

---

### Post by fakie_flip on 2006-08-22
Am I the only one getting this error? I followed the directions from this howto, so shouldn't other people be having the same problem that I am? How can this be fixed? I accepted all the default values.

```
Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Unable to compile the VMware VmPerl Scripting API.

********
The VMware VmPerl Scripting API was not installed.  Errors encountered during
compilation and installation of the module can be found here:
/tmp/vmware-config0

You will not be able to use the "vmware-cmd" program.

Errors can be found in the log file:
'/tmp/vmware-config0/control-only/make.log'
********

Hit enter to continue.

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files?
[/var/lib/vmware/Virtual Machines] /home/veronica/vmware

The path "/home/veronica/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:

```

Here is my contents of the make.log.

```
veronica@veronica-desktop:~$ cat /tmp/vmware-config0/control-only/make.log Checking if your kit is complete...
Looks good Writing Makefile for VMware::VmPerl
make: Entering directory `/tmp/vmware-config0/control-only' make: Warning: File `/usr/lib/perl/5.8/Config.pm' has modification time 9.2e+07 s in the future
Makefile out-of-date with respect to /usr/lib/perl/5.8/Config.pm /usr/lib/perl/5.8/CORE/config.h
Cleaning current config before rebuilding Makefile...
Checking if your kit is complete...
Warning: the following files are missing in your kit:
        vmcontrol.o
        vmcontrol64.o
Please inform the author.
Writing Makefile for VMware::VmPerl
==> Your Makefile has been rebuilt. <==
==> Please rerun the make command.  <==
make: *** [Makefile] Error 1
make: Leaving directory `/tmp/vmware-config0/control-only'
veronica@veronica-desktop:~$
```

From the make log I noticed this.

```
Warning: the following files are missing in your kit:
        vmcontrol.o
        vmcontrol64.o
Please inform the author.
```

I should not be missing any files. I did this to verify my download.

```
veronica@veronica-desktop:~/Desktop$ ls
VMware-server-1.0.1-29996.tar.gz      vmware-server-distrib
VMware-server-1.0.1-29996.tar.gz.md5
veronica@veronica-desktop:~/Desktop$ cat VMware-server-1.0.1-29996.tar.gz.md5
9846bff6c3c8af97d4e3ae2700f8dd3a  VMware-server-1.0.1-29996.tar.gz
veronica@veronica-desktop:~/Desktop$ md5sum -c VMware-server-1.0.1-29996.tar.gz.md5
VMware-server-1.0.1-29996.tar.gz: OK
veronica@veronica-desktop:~/Desktop$


```

I also tried using gcc-3.4 by installing it with apt-get and running this command.

```
export CC=/usr/bin/gcc-3.4
```

---

### Post by fakie_flip on 2006-08-22
Problem solved. After much research, I found that I should update my time and syncronize it with the ntp time servers on the internet. Looking in the errors gave let me know about that because I had a simliar problem when compiling something else in Linux. I hope this helps anyone having the same problem.

---

### Post by metalsam on 2006-08-22
I installed vmware following your guide (very useful!) and have two problems:
1. Vmware havent given me a serial number
2. Vmware starts a stack of background processes on boot, severely slowing down my computer so even the mouse laggs.

Which initrd do I need to change ?

---

### Post by wilberfan on 2006-08-23
Well, I'll be dipped--it actually *works*...!

It's taken the better part of 4 or 5 hours, and I don't have any sound yet...but pretty damn amazing, nonetheless!

This is only, like, my 2nd week playin' with Ubuntu...it's hard to believe I've got a virtual Windows machine on this thing!  (And, even more amazing, it's reasonably peppy, too!  My dual-boot Linux box is my 4 (5?) year-old DELL, Pentium IV, with only 512MB of RAM....)

=D>

[ And now the sound is working!   Hmmm...now what about that webcam...? ]

---

### Post by jamadagni on 2006-08-23
> **UltraSonicSite said:**
> Hey I have a question. Could I install the laptop version of Windows XP on VMWARE?
What do you mean, laptop version of Win XP? If you mean the one where Symantec Ghost restores a working Windows installation from an image, then no, you can't use that Win XP with this. You need the actuall Win XP installer disc.

---

### Post by Disastorm on 2006-08-23
does vmware work with 3d at all?  I have some games I wanted to play that are 3d but they arent like intense 3d they are cel shaded.  the first post said it doesnt work with heavy 3d whatever that means.

*edit*Nice HowTo, its the first howto ive been able to do on my first try without any errors.  Right now I'm downloading some 3d stuff to see how well they run on it.

*edit ok looks like 3d doesnt work at all or at least the games I tried gave me errors saying either unsupported video card or some directx errors.

---

### Post by jamadagni on 2006-08-24
> **kassetra said:**
> In my version, under Virtual Machine Setting -> Options, I setup "shared folders" and then setup which folders I wanted my VMWare session to have access to.

Then, it's simply in the network on windows.
Hello. I think you are using VMWare **WorkStation** on Linux. Is this true? Because I just downloaded and installed the latest VMWare Server on my Kubuntu Dapper and it does not have any Shared Folders setting.

---

### Post by jamadagni on 2006-08-24
> **chinaski said:**
> hello, for me simple copy&paste works
Please clarify that. When I do Ctrl+C on a file in Windows and Ctrl+V in a directory in Konqueror, I get "Please enter file name for clipboard content". How exactly are you able to copy&paste.

---

### Post by jamadagni on 2006-08-24
> **crouton said:**
> If you select the VMXNet driver, you should be able to 'set up' a 1Gbps network card.  The added benefit of having virtual machines on the same host machine is that the host machine's network card is never actually utilized - file transfers and such actually occur at FSB speeds.  The limiting factor will be the speed of the host machine HD, as it will be saturated transferring files long before the network card throughput is saturated.
How do I install the VMXNet driver?

---

### Post by jamadagni on 2006-08-24
> **darknuala said:**
> Is it possible to use your cd burner in this?  I installed Nero 6, but it only shows a virtual device.  And is sound possible?
Did you get your CD writer working? I have a DVD-RAM drive, but in the guest XP's Device Manager it only shows up as: 

NECVMWar VMWare IDE CDR

I have started [this thread]("http://www.vmware.com/community/thread.jspa?threadID=52770") at the VMWare forums.

---

### Post by cbeaudin on 2006-08-24
> **Jose Catre-Vandis said:**
> This is usually due to not having the right linux headers installed, although I did have one case where nothing I tried would fix the thing. Might need to check the uninstall thread and start again, but make sure your linux headers match your kernel.

I do not have the linux headers that match my kernel but if i try to install the correct headers by running "sudo apt-get install linux-headers-`uname -r`" i get the following error:

E: Couldn't find package linux-headers-2.6.15-26-amd64-generic

The linux header folders in /usr/src/ are "2.6.15-23" and "2.6.15-23-amd64-generic"

How do i fix this? Thank you in advance.

---

### Post by desiboston on 2006-08-24
I resolved this without any modification to xorg.conf but only the 1st 2 suggestions here. I have Dell 700m

---

### Post by alexandermimix on 2006-08-25
my fresh install of vmware only works if I start it as root "sudo vmware"

I have all my fat32 partitions added as 'persisting' and my windows NTFS partion as 'none parsisting' so that I wont kill my native XP installation. Anyway to make it so thta i dont need to run it as root?

---

### Post by Fíona on 2006-08-25
I have just installed kubuntu dapper and want to try out the vmware experience. I want to install windows 98se as virtual machine. However to install windows 98se I have to use 2 cd's, the original win98 and then the second edition upgrade (I don't have win98se on one cd). Do you think that this will cause problems with installation of the win 98se virtual machine?

---

### Post by alexandermimix on 2006-08-25
shouldnt cause any upsets that I can see. Think of you Virtual machine as being a computer inside a computer.

---

### Post by TooDamFast on 2006-08-25
great how to!  

windows is running great but i cant do a windows upadate?  

I get this 

[Error number: 0x80072EE2]
"The website has encountered a problem and cannot display the page you are trying to view. The options provided below might help you solve the problem. "


anyone have any ideas?
i would like to get it updated before i start installing apps.

---

### Post by docshawnc on 2006-08-25
I just installed an XP Professional VM - awesome!  Good-bye dual boot - thanks for the quide!

---

### Post by alexandermimix on 2006-08-26
stuff XP I just installed Mac OSX in mine :P

---

### Post by krowlands on 2006-08-26
I just followed the guide, and got this:

The path "/home/karl/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

karl@karl-desktop:/tmp/vmware-server-distrib$ 

any ideas?

---

### Post by Fíona on 2006-08-26
> **krowlands said:**
> I just followed the guide, and got this:

The path "/home/karl/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

karl@karl-desktop:/tmp/vmware-server-distrib$ 

any ideas?

I had the same error message and found the answer in the forums of vmware 
[www.vmware.com/community](www.vmware.com/community)
When you were asked where you wanted to install the binary files, you appear to have given your home directory /home/karl/  if I remember correctly you have to make that /home/karl/bin

Check out the vmware forum and good luck, there are possible more surprises in store!!

---

### Post by grizz_granlien on 2006-08-26
This VMware works great I think it runs good so far at first a little jerky but now it is awsom it works fine I bet you could run a game I will try later feel free to E-Mail I can tell you if it worked or you can try it your self...

---

### Post by chester on 2006-08-27
I just finished installing the vmware server, the installation couldn't have been easier, everything as far as i could tell went off without a hitch. however, when i try to open it from system tools it get:

Could not launch menu item

Details: Failed to execute child process "vmware" (No such file or directory)

any idea where i went wrong and how i can fix it,

thanks in advance

---

### Post by dqj_99 on 2006-08-27
Has anyone had any success in installing VMServer in Ubuntu 64-bit? I've tried but I cannot get past this message when I try to boot:

Will not boot:

Unable to change virtual machine power state: The process exited with an error:
/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libXrender.so.1: cannot open shared object file: No such file or directory
End of error message.

Please could someone publish some advice on getting VMWare Server working in 64-bit ubuntu.:(

---

### Post by Fíona on 2006-08-27
I managed to install vmware server on kubuntu 6.06 however I cannot launch it via K-system-Vmware server console.

I get the following error message, KDEinit could not launch vmware: could not find vmware executable.

I have also tried via the command line using sudo vmware, the reply is command not found.

I installed vmware to my home directory /home/fiona/vmware

total 28
drwxr-xr-x 2 root root 4096 2006-08-27 11:20 bin
drwxr-xr-x 3 root root 4096 2006-08-26 19:33 doc
drwxr-xr-x 3 root root 4096 2006-08-26 19:33 include
drwxr-xr-x 4 root root 4096 2006-08-27 11:27 lib
drwxr-xr-x 3 root root 4096 2006-08-26 19:33 man
drwxr-xr-x 2 root root 4096 2006-08-27 11:21 sbin
drwxr-xr-x 3 root root 4096 2006-08-26 19:33 share

Can anyone tell me what's going wrong?

---

### Post by _Graven on 2006-08-29
First I tried using archive manager to extract the files, and noticed the installation file was missing, so I went for the command line. 

If I run tar as normal user, then ALL files I'll say "cannot utime:operation not permitted". Weird... 

```
sudo tar -xf VMware-server-1.0.1-29996.tar.gz
```

I get...

```
tar: vmware-server-distrib/lib/perl5/man/man3/XML\:\:DOM.3.gz: Cannot open: Invalid argument
tar: vmware-server-distrib/lib/perl5/man/man3/XML\:\:Parser.3.gz: Cannot open: Invalid argument
tar: vmware-server-distrib/lib/perl5/man/man3/XML\:\:Parser\:\:Expat.3.gz: Cannot open: Invalid argument
tar: vmware-server-distrib/lib/perl5/man/man3/XML\:\:Sablotron.3.gz: Cannot open: Invalid argument
tar: vmware-server-distrib/lib/lib/libpam.so.0/libpam.so: Cannot create symlink to `libpam.so.0.81.2': Operation not permitted
tar: vmware-server-distrib/lib/lib/libpam.so.0/libpam.so.0: Cannot create symlink to `libpam.so.0.81.2': Operation not permitted
tar: vmware-server-distrib/lib/lib/libpam.so.0/libpam_misc.so: Cannot create symlink to `libpam_misc.so.0.81.2': Operation not permitted
tar: vmware-server-distrib/lib/lib/libpam.so.0/libpam_misc.so.0: Cannot create symlink to `libpam_misc.so.0.81.2': Operation not permitted
tar: vmware-server-distrib/lib/lib/libpam.so.0/libpamc.so: Cannot create symlink to `libpamc.so.0.81.0': Operation not permitted
tar: vmware-server-distrib/lib/lib/libpam.so.0/libpamc.so.0: Cannot create symlink to `libpamc.so.0.81.0': Operation not permitted
tar: vmware-server-distrib/lib/lib/libpam.so.0/security/pam_unix_acct.so: Cannot create symlink to `pam_unix.so': Operation not permitted
tar: vmware-server-distrib/lib/lib/libpam.so.0/security/pam_unix_auth.so: Cannot create symlink to `pam_unix.so': Operation not permitted
tar: vmware-server-distrib/lib/lib/libpam.so.0/security/pam_unix_passwd.so: Cannot create symlink to `pam_unix.so': Operation not permitted
tar: vmware-server-distrib/lib/lib/libpam.so.0/security/pam_unix_session.so: Cannot create symlink to `pam_unix.so': Operation not permitted
tar: vmware-server-distrib/vmware-vix/lib/libvmware-vix.so.0: Cannot create symlink to `libvmware-vix.so.0.0.0': Operation not permitted
tar: vmware-server-distrib/vmware-vix/lib/libvmware-vix.so: Cannot create symlink to `libvmware-vix.so.0': Operation not permitted
tar: vmware-server-distrib/vmware-install.pl: Cannot create symlink to `bin/vmware-uninstall.pl': Operation not permitted
tar: Error exit delayed from previous errors

```

I still get "operation not permitted" for some files, but with completely different error. Ok, so I guess this superuser is not that super. :twisted: What do you guys reckon? Should I recklessly disregard the invalid arguments, create the symlinks by hand and proceed?

PS: This is clearly an issue with tar, but since it came up while trying to follow the HOWTO, please bear with me if I seem a bit off topic..

---

### Post by CyberCr33p on 2006-08-30
Did someone try to play games using Windows under vmware? Does someone know if I can play lineage2 using vmware and Windows XP?

---

### Post by Mongoose on 2006-08-30
Actually, you can use many usb devices via Windows XP from VMWare.  I have a cheap scanner that doesn't work fully in Linux -- due to some of the features being in software.  I can connect the device via VMWare and use the XP USB driver from there.   I scan into an SMB share on my ubuntu box using GIMP 2.0 in XP under VMWare.   It's a good way to support crappy USB devices until they get a proper driver.

---

### Post by dentaku65 on 2006-08-31
I trying to load my XP Home partition (/dev/hda1) with vmWare but after the grub choice for XP in vmware I get a bsod screen (too quick to catch the screenshot) and the virtualization reload. I think something related to the HD or to the video card...

---

### Post by kaks on 2006-08-31
One question. I dont know if anyone has asked this before, but i was wondering can i use my current windows installation? I.e. installed on c:?


thanks

---

### Post by kendals on 2006-08-31
> **chester said:**
> I just finished installing the vmware server, the installation couldn't have been easier, everything as far as i could tell went off without a hitch. however, when i try to open it from system tools it get:

Could not launch menu item

Details: Failed to execute child process "vmware" (No such file or directory)

any idea where i went wrong and how i can fix it,

thanks in advance

I have that same problem. I tried to reinstall/uninstall, and now it's all buggered up. How do I do a clean uninstall then reinstall? I tried the uninstall pl script but it couldn't find it. I also tried deleting /etc/vmware, but it still had files on there when I tried to reinstall.

Now, it tries to start VMWare Server Console, then disappears and does nothing...any ideas on how to fix this up? I really need it :(

---

### Post by andrewlondonuk on 2006-08-31
Hi, i don't know if it has been covered in this guide (it's quite long and i don't fancy reading it all), but i installed vmware player the other day and had major problems with it.

As soon as the system would boot up the vmware player services were using all of my available ram and swap space.... is it meant to do this? 

I'd like to install vmware server so that i can get windows working inside my linux but i don't want to have the same problems i had with player.

Is player meant to be the same thing as server or does it have different uses?

---

### Post by kendals on 2006-08-31
I doubt it's meant to hog that much. How much RAM do you have? If at least 512mb, then something is wrong.

I can't even GET VMWare Server to uninstall, so I can reinstall it :(

---

### Post by dentaku65 on 2006-08-31
> **kaks said:**
> One question. I dont know if anyone has asked this before, but i was wondering can i use my current windows installation? I.e. installed on c:?

thanks

Yes you can, but yuo must aware of two important things:

1) when you see the grub menu in the virtulizator be very careful to do not load your linux prtition

2) You must set the disk geometry in grub and with kernel 2.6.x it is very hard to know what is the proper disk geometry, hdparm result is incorrect

There is a a guide for Gentoo, but you can find very helpful.

[http://yep.it/?pinmwj](http://yep.it/?pinmwj)

---

### Post by andrewlondonuk on 2006-09-01
> **kendals said:**
> I doubt it's meant to hog that much. How much RAM do you have? If at least 512mb, then something is wrong.

I can't even GET VMWare Server to uninstall, so I can reinstall it :(

I have 2gb of ram on this machine, it's a 2.6ghz athlon xp and the cpu is maxed out as soon as i log in with vmware player installed.

I uninstalled it and everything went back to normal. I don't want to install vmware server and have the same issues because from what i can tell it isn't as easy to get rid of.

Could somebody here tell me the difference between player and server?

Thanks
Andrew

---

### Post by kendals on 2006-09-01
Yeah, that's my problem too. I installed VMWare Server, it stuffed up, and now I can't uninstall and reinstall it cleanly :'(

---

### Post by tall-male on 2006-09-01
Running windows from an existing installtion turned out to be quite easy.
I have 2 different hard drives; /dev/hda is windows; /dev/hdb is Ubuntu. Mostly I run Ubuntu but for some stuff I need Windows. Most of the time I run the existing windows in VMWARE using the dedicated disk. It works perfectly:

- Start Windows dedicated and create a new hardware profile (called vmware of something)
- Start again dedicated, now with the vmware hardware profile. Replace the IDE-drivers with the Windows Standard IDE drivers. If you don't, windows won't start in Vmware.

In Linux in VMware, just use an existing disk instead of diskfiles.  (don't know about Windows and Ubuntu on 1 disk, should be about the same)

I'm working like this for about 3 moths now; it works perfectly. I'm using my old windows installation still

Good luck!

---

### Post by Skootle on 2006-09-02
> **andrewlondonuk said:**
> Hi, i don't know if it has been covered in this guide (it's quite long and i don't fancy reading it all), but i installed vmware player the other day and had major problems with it.

As soon as the system would boot up the vmware player services were using all of my available ram and swap space.... is it meant to do this? 

I'd like to install vmware server so that i can get windows working inside my linux but i don't want to have the same problems i had with player.

Is player meant to be the same thing as server or does it have different uses?

Yeah, that was happening to me as well. I also tried Workstation, but the exact same thing happened; once, I couldn't even start up Kubuntu and had to uninstall it via the recovery console.

When I installed the server edition (the one the HowTo tells you to download), I realised that "VMware-DHCP" (or something like that) was taking up around 85% of my 1024 MB or RAM. So I uninstalled (it took me a long time to type vmware-uninstall.pl :p ) and tried installing it again, but this time, when it automatically opened up vmware-config.pl and asked me about network information, I said "no", and that's it. :)

Seems to be working fine right now. I haven't finished setting up the virtual machine, but all seems to be going well. I'll keep you posted.

BTW, uninstallation of VMWare is pretty simple. Just *sudo ./vmware-uninstall.pl* and it'll take care of everything. :)

---

### Post by Skootle on 2006-09-02
OK, obviously if I do that (not configure network options), I don't have access to the internet via my Virtual Machine, yet if I *do* configure it, **vmnet-dhcpd** uses around 85% of my memory and makes it impossible for me to even use my computer (let alone a virtual machine).

Any ideas?

---

### Post by dentaku65 on 2006-09-06
> **tall-male said:**
> Running windows from an existing installtion turned out to be quite easy.
I have 2 different hard drives; /dev/hda is windows; /dev/hdb is Ubuntu. Mostly I run Ubuntu but for some stuff I need Windows. Most of the time I run the existing windows in VMWARE using the dedicated disk. It works perfectly:

- Start Windows dedicated and create a new hardware profile (called vmware of something)
- Start again dedicated, now with the vmware hardware profile. Replace the IDE-drivers with the Windows Standard IDE drivers. If you don't, windows won't start in Vmware.

In Linux in VMware, just use an existing disk instead of diskfiles.  (don't know about Windows and Ubuntu on 1 disk, should be about the same)

I'm working like this for about 3 moths now; it works perfectly. I'm using my old windows installation still

Good luck!

Can you explain what are exactly "Windows Standard IDE Drivers"?
I've tried to change the IDE driver(s) on XP partition (in the created vmware hardware profile) but I'm not able to find them...

TIA

---

### Post by dentaku65 on 2006-09-06
> **dentaku65 said:**
> Can you explain what are exactly "Windows Standard IDE Drivers"?
I've tried to change the IDE driver(s) on XP partition (in the created vmware hardware profile) but I'm not able to find them...

TIA

Never mind... I did it! :cool: 
Works perfect, the only thing was the waste of time re-registering my installed copy of XP :evil:

---

### Post by KageKeeper on 2006-09-06
Great HowTo. Worked perfectly.

Only problem is I have no sound in my XP on vmware. The option to add hardware is grayed out.

I have followed other's advice and did a sudo killall esd, but that does not help either.

Any other suggestions?

Thanks so much!

---

### Post by aetherane on 2006-09-07
Windows XP doesn't have my computer's screen resolution listed when I boot into it via vmware. How can I fix this?

---

### Post by dentaku65 on 2006-09-07
> **aetherane said:**
> Windows XP doesn't have my computer's screen resolution listed when I boot into it via vmware. How can I fix this?

Right click in the windows desktop and choose your screen resolution (i my case 1024x768 and was 800x600). Simple

---

### Post by acorn22 on 2006-09-08
Ok, I keep getting this error that it is looking for vmware already installed on my machine.

here is what I did
```
lowell@ubuntu:~/Desktop/vmware-mui-distrib$ sudo ./vmware*
Creating a new installer database using the tar3 format.

You must read and accept the End User License Agreement to continue.
Press enter to display it.




VMWARE MASTER END USER LICENSE AGREEMENT
...
...

Do you accept? (yes/no) yes

Thank you.

Installing the content of the package.

Setup is unable to find the "vmware" program on your machine. Please make sure
it is installed. Do you want to specify the location of this program by hand?
[yes] yes

What is the location of the "vmware" program on your
machine? /home/lowell/vmware

The answer "/home/lowell/vmware" is invalid. It must be the complete name of a
binary file.

What is the location of the "vmware" program on your
machine?  


``` 
What can I do?

EDIT: now I get this
```
lowell@ubuntu:~/Desktop/vmware-mui-distrib$ sudo ./vmware*
Password:
A previous installation of VMware software has been detected.

Failure

Execution aborted.

lowell@ubuntu:~/Desktop/vmware-mui-distrib$

``` 

and there is no folder named vmware in my etc folder. one folder named vmware-mui, tho


EDIT: This is my 100th post! :D

EDIT: I downloaded the wrong one! I got the mui (managing thingy) instead of the server.

EDIT: Ok, Now I'm getting this error.

```
The path "/home/lowell/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.
```

---

### Post by ramasdf123 on 2006-09-08
$ vmware
bash: vmware: command not found

---

### Post by jocheem67 on 2006-09-09
Yes:) 

Got XP up and running with vmware under dapper. Sound, usb, video all working perfectly. So a big thanks from here.

Some questiond though:

can I approach my ext3 ubuntu files and folders as well as my fat32 xp files and folders ( dual-boot ) in vmware--xp--ntfs???

The funny thing is that  I can mount my usb backup disk which is ntfs within vmware--xp.....
I am playing music, with a very old version of winamp ( 2.70 ) as we speak, and can swap files from my vmware installation to my usb-disk...
Is this a file-system matter????

---

### Post by Chew on 2006-09-09
Can somebody help a seriously new Linux user out?

I followed the guide step-by-step and was told it installed correctly.  When I go into applications to open it, I get an error.  It seems from searching this thread, the error has happened to other people, but I can't seem to see where the resolution is.  Here's the error:

> 
Details: Failed to execute child process "vmware" (No such file or directory)

When trying to launch from Applications menu and get a "command not found when I do "vmware" from terminal.

](*,)

---

### Post by s1gnAl on 2006-09-10
I am about to go nuts with this install. I have not been able to get it to work for whatever unknown reason. How can I completely remove every trace of vmware server so I can start over again? Is there a script or something to do this?

---

### Post by phattpuud on 2006-09-11
Hi.  I am trying to install Vmware Server.  I have followed the installation process, but I am getting an error.

In which directory do you want to install the documentation files?
[/home/money/doc/vmware]

The path "/home/money/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

What should I do?

Thanks for your help.

---

### Post by imwarren on 2006-09-11
I was about to post my problem, when i realised the previous post have the same problem as mine...

I also got this problem:
**Unable to get the access rights of source file "./vmware-vix/bin".**

I am a new ubuntu user, can an expert help both of us? Thanks in advance

anyway, my problem (showing all the prompts i got):

imwarren@Room:~$ cd /tmp
imwarren@Room:/tmp$ cd vmware-server-distrib
imwarren@Room:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

inetd: no process killed
Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Server 1.0.1 build-29996 for Linux completed
successfully. Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files?
[/home/imwarren/vmware]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/home/imwarren/sbin]

The path "/home/imwarren/sbin" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the library files?
[/home/imwarren/lib/vmware]

The path "/home/imwarren/lib/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the manual files?
[/home/imwarren/man]

The path "/home/imwarren/man" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the documentation files?
[/home/imwarren/doc/vmware]

The path "/home/imwarren/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

**Unable to get the access rights of source file "./vmware-vix/bin".**

Execution aborted.

---

### Post by siiib on 2006-09-11
> **ntwrkguy said:**
> I have /dev/hda1 with Ubuntu on it, /dev/hda2 with swap, /dev/hda3 with NTFS Windows XP on it. Loaded up hda3 in VMWare, and when I start it, I get a ERROR 17 in GRUB. Any advice? Thanks!

bit late i know.. catching up on thread.. :D 
i got rid of this by including all of the partitions in the selector.. seems like otherwise grub can't see some of its partition options and throws a wobbler..
thing is now i've got all kind of partition errors which i can't read cos it scrolls too fast:rolleyes:

---

### Post by siiib on 2006-09-11
> **dentaku65 said:**
> I trying to load my XP Home partition (/dev/hda1) with vmWare but after the grub choice for XP in vmware I get a bsod screen (too quick to catch the screenshot) and the virtualization reload. I think something related to the HD or to the video card...

me too.. any way of stalling it so that we can at least read it.. i have an acer with an auto repair partition thingy.. i was wondering if that was causing trouble..:-k

---

### Post by redDEADresolve on 2006-09-12
I got this error code any help???

Starting internet superserver: xinetd.

Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Fíona on 2006-09-13
To those having touble installing vmware server, specifically those installing to their home directories..
My experience is that it's easier for we beginner's to install not in the home directory, but follow the default locations. That way you don't have problems with faulty links or permissions. I too installed to my home directory; I did get it installed but then couldn't start vmware console up, kdeinit couldn't find the executable!
Installing to default locations cured this for me.

Good luck!

---

### Post by Teleboy on 2006-09-13
I've trawled this thread but can't see a reference to my problem - I have three additional users on my Ubuntu PC, all of whom require WinXP access via VMware server - they have no problem accessing the VMware application but do not have the permissions to access the *.vmx file - what's the best way to go about this?

(VM's in /var/lib/vmware/Virtual Machines)

Best Regards and thanks for the HowTo.

Teleboy

---

### Post by BLTicklemonster on 2006-09-14
I'm lost. It seems to me that when I was running vmware player once before, I set up the tools, but I can't find anything about vmware tools for the player. Is there a way to load the tools for the player?

---

### Post by NoTiG on 2006-09-14
Just a quick question... What performance can i expect for a decent cpu and 1.2 GB of ram? if debug mode is turned off or whatever and if everything is working... is it a huge resource drain on your computer?

---

### Post by tall-male on 2006-09-14
> **dentaku65 said:**
> Never mind... I did it! :cool: 
Works perfect, the only thing was the waste of time re-registering my installed copy of XP :evil:

Yep, I found out the re-registering the hard way myself. Until a week ago I used Windows 2000 which doesn't need this activation thing and it's easy to switch between "dedicated boot" (mainly used  for gaming) and VMware boot. (Some doesn't-work-on-Linux for-my-work-things)
Windows XP however is needs activation which is sticked to a hardware profile. If you change the hardware too much, you have to register again. (Guess what happens if you change your CPU from Pentium to Core 2 Duo ....)
VMware shows virtual hardware rather than the real hardware en blows your activation. As result: you have to activate again every time you switch between VMware and dedicated boot.
Activation seems to be limited to something like 20 times, so this is not a good option.
Solution:
- Make a choice whether to boot dedicated or under VMware.
- Spend lots of money on a cooperate or volume XP Licence which does't need activation.
- Stick to Windows 2000.

Anyone got an idea how to solve this activation and hardware problem? (Please: no "download this crack from xxx-rated.com...!)

---

### Post by tall-male on 2006-09-14
Running more safely

In my view, there is a security issue using VMware under Linux together with real hard disk instead of image file.
to be able to access the raw device, you need to be a member of the disk group. Without, you, VMware, cannot access the raw device.
Actually, that's not what you want. A normal user should NOT be a member of the disk group. Also; running VMware as root is also NOT a good idea. The issue can be solved easily however:

- Create a new user and new group. I used both vmware 
- Create a home directory for the user, you do need it
- Give the user a fake shell: /bin/false
- Don't give the user a password or simply disable it. (paaswd -d)
- The new user should be a member of primary group vmware en secondary groups disk (tha does the trick!) and audio (in case you want to use your soundcard)
- I use gksu --user vmware -l to start vmware. vmware will run as user vmware.

---

### Post by rcatman on 2006-09-14
Worked perfect! I now have Windows XP fully up and operational :) 

I ran a second terminal window incase i needed to install anything. I had to install the C header files ( sudo apt-get install build-essentials ) and download the linux header files. And all the default values were what I wanted. Now I'm going to install other linux distros and try em out! The possibilities are limitless! 

Btw, having XP in a nice "cage" on my desktop is a great feeling \\:D/

Thanks for the tutorial!

---

### Post by jamadagni on 2006-09-14
I don't have this currently installed, but have you tried the menus. I remember that I got it from there.

---

### Post by BLTicklemonster on 2006-09-14
> **jamadagni said:**
> I don't have this currently installed, but have you tried the menus. I remember that I got it from there.

The tools? I have looked and there's nothing like that, but there's something about upgrading to something. Thanks for the reply though.

---

### Post by jamadagni on 2006-09-14
BTW you are using VMWare server as instructed in this HOWTO, right? Or are you using VMWare Player for Linux? 'cos if it's the player, then I don't think it has VMWare tools. The server installation does have it.

---

### Post by darrenm on 2006-09-14
Don't know if this has been mentioned so far in the thread, sorry if it has but I don't have time to go all the way through ;)

A cool thing to do with running XP in vmware on linux is to enable remote desktop, SSH in remotely using putty to your linux box and tunnel port 3389 to the IP of XP in vmware. Then just connect rdesktop to localhost:3389 and it runs superbly quick even on modest hardware. You also dont get the keyboard/mouse grabbing weirdness of using the vmware server console to contend with.

---

### Post by BLTicklemonster on 2006-09-14
> **jamadagni said:**
> BTW you are using VMWare server as instructed in this HOWTO, right? Or are you using VMWare Player for Linux? 'cos if it's the player, then I don't think it has VMWare tools. The server installation does have it.

lmao, you mean I gotta do it again? I put player on, not server

---

### Post by dhmce on 2006-09-14
> **phattpuud said:**
> Hi.  I am trying to install Vmware Server.  I have followed the installation process, but I am getting an error.

In which directory do you want to install the documentation files?
[/home/money/doc/vmware]

The path "/home/money/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

What should I do?

Thanks for your help.

That is because the install the install script did not create a /bin directory in /vmware-vix.  Use the terminal to create one for yourself.  mkdir bin

---

### Post by BLTicklemonster on 2006-09-14
Alllllllrighty then, I just went and downloaded the vmware server for linux, first one mentioned, agreed to the eula, and never saw a place for where I was going to get any serial number, and haven't gotten one in email. I registered after I downloaded it. 

Now what? (Jiminy Crickets, I'm at it again. Who ordered a mountain, I got one molehill left over here!)

*edit:

Okay, I ran out of molehills, and just started the thing up and pressed help and enter serial number to see what would happen, and lo and behold, it had a place to register, and I got my serial number online, not in email. So I'm up and running now. Sweet, the tools installed from the internet. 

(don't like the window I'm in, but I suppose I can live with it :) aha, I see the full screen button now. I'll shut up now. G'day.

---

### Post by BLTicklemonster on 2006-09-15
Okay, I had vmware player, with my windowsxppro.vmx file, and installed vmwareserver, and it runs fine, but I only see my dvd, not my dvdrw. Can I manually edit my vmx file to add the dvdrw to it? At present, it's:

ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "atapi-cdrom"
ide1:0.autodetect = "TRUE"

 can I add an hd2:0 and ought I to call it something other than atapi-cdrom, or is that good enough?

and what about other hard drives, can I get them to show up also? 

Or would I be better off doing a fresh install from an xp disk, would that put things where they belong? I'd rather not do that.

*edit:

Okay, I installed and ran directx, and ran dxdiag and it worked fine, no problems. This is a lot faster than it was last year when I tried this. Installing winamp, then watching the movie I am Sam over shoutcast video was a treat. (does linux have anything to watch streaming video from shoutcast, he wonders.... have to check that one out. I love watching sean penn not acting, just being himself. ;) )
(that was mean)

Anyway, this is a lot better than a year ago!!! Now to get my other dvd to show up...


*edit:

Okay, I found where you add devices, and it worked fine. Can't run dvd decryptor or dvd shrink, though, so I'll stick with rebooting to xp. (I can't get anything linux has to offer to work for ripping dvds, even in wine, nothing will work)

---

### Post by SonWon on 2006-09-17
> **tall-male said:**
> Running more safely

In my view, there is a security issue using VMware under Linux together with real hard disk instead of image file.
to be able to access the raw device, you need to be a member of the disk group. Without, you, VMware, cannot access the raw device.
Actually, that's not what you want. A normal user should NOT be a member of the disk group. Also; running VMware as root is also NOT a good idea. The issue can be solved easily however:

- Create a new user and new group. I used both vmware 
- Create a home directory for the user, you do need it
- Give the user a fake shell: /bin/false
- Don't give the user a password or simply disable it. (paaswd -d)
- The new user should be a member of primary group vmware en secondary groups disk (tha does the trick!) and audio (in case you want to use your soundcard)
- I use gksu --user vmware -l to start vmware. vmware will run as user vmware.

When I run

```
gksu --user vmware -l vmware
```

I get

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
```

So after an Internet search I tried

```
xhost +vmware
```

And got

```
xhost:  bad hostname "vmware"
```

I used the gnome admin tool Users and Groups to setup the new user and then I ran

```
passwd -d vmware
```

I noticed once I got a password prompt but was told invalid password but I know I had the correct password?

I am a new Linux user and could use some help.

Thank you,

---

### Post by carrobarro on 2006-09-17
I installed VMware and installed windows vista on that. really cool i think. but just a question. where does the file goes? how do i get the stuff I do in VMware into ubuntu?

---

### Post by Giggity on 2006-09-18
It goes into the virtual hard drive, which is kinda like an ISO of a DVD, only a different format.  To get your data over, you need to setup a network drive of say, your /home/user/ folder using Samba ([instructions]("http://www.ubuntuforums.org/showthread.php?t=202605")), with read-write access and use that networked drive to save/move important files to.

---

### Post by carrobarro on 2006-09-18
okey thanks. I will try that

---

### Post by AllenJM on 2006-09-20
My fault :-& should have read the spec sheet on VMWare server. Thought this was the dream answer to using windows progs on a MAC iBook, you might want to put a little note at the beginning for dooobers like me. 

If your interested the result is below.:-({|= 

Great 'How to' though......


[I]Before running VMware Server for the first time, you need to configure it by
invoking the following command: "/home/allen/vmware/vmware-config.pl". Do you
want this program to invoke the command for you now? [yes]

Your processor does not support the ^cpuid instruction. VMware Server will not
run on this system.

Your /proc/cpuinfo is:

processor       : 0
cpu             : 7447A, altivec supported
clock           : 666.666000MHz
revision        : 0.2 (pvr 8003 0102)
bogomips        : 36.73
timebase        : 18432000
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
pmac-generation : NewWorld
Execution aborted.

allen@ubunMac:~/Download/VMWare/vmware$
[/I]

---

### Post by starscalling on 2006-09-20
my vmware install o:

nekostar@dapper-xp:~$ sudo apt-get install linux-headers-`uname -r` build-essent ial xinetd gcc-3.4
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
The following extra packages will be installed:
  cpp-3.4 gcc-3.4-base linux-headers-2.6.15-27
Suggested packages:
  gcc-3.4-doc libc6-dev-amd64 lib64gcc1
The following NEW packages will be installed:
  cpp-3.4 gcc-3.4 gcc-3.4-base linux-headers-2.6.15-27
  linux-headers-2.6.15-27-k7 xinetd
0 upgraded, 6 newly installed, 0 to remove and 2 not upgraded.
Need to get 10.2MB of archives.
After unpacking 88.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main gcc-3.4-base 3.4.6-1ubuntu2 [164k B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-27 2. 6.15-27.48 [6906kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main cpp-3.4 3.4.6-1ubuntu2 [1687kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main gcc-3.4 3.4.6-1ubuntu2 [494kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main xinetd 1:2.3.14-0ubuntu1 [131kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-27-k7  2.6.15-27.48 [855kB]
Fetched 10.2MB in 19s (528kB/s)
Selecting previously deselected package gcc-3.4-base.
(Reading database ... 115086 files and directories currently installed.)
Unpacking gcc-3.4-base (from .../gcc-3.4-base_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package cpp-3.4.
Unpacking cpp-3.4 (from .../cpp-3.4_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from .../gcc-3.4_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-27.
Unpacking linux-headers-2.6.15-27 (from .../linux-headers-2.6.15-27_2.6.15-27.48 _i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-27-k7.
Unpacking linux-headers-2.6.15-27-k7 (from .../linux-headers-2.6.15-27-k7_2.6.15 -27.48_i386.deb) ...
Selecting previously deselected package xinetd.
Unpacking xinetd (from .../xinetd_1%3a2.3.14-0ubuntu1_i386.deb) ...
Setting up gcc-3.4-base (3.4.6-1ubuntu2) ...
Setting up cpp-3.4 (3.4.6-1ubuntu2) ...
Setting up gcc-3.4 (3.4.6-1ubuntu2) ...
Setting up linux-headers-2.6.15-27 (2.6.15-27.48) ...

Setting up linux-headers-2.6.15-27-k7 (2.6.15-27.48) ...
Setting up xinetd (2.3.14-0ubuntu1) ...
Stopping internet superserver: xinetd.
Adding `diversion of /etc/init.d/inetd to /etc/init.d/inetd.real by xinetd'
Starting internet superserver: xinetd.

nekostar@dapper-xp:~/vmware-server-distrib$ sudo ./vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/usr/sbin]

In which directory do you want to install the library files?
[/usr/lib/vmware]

The path "/usr/lib/vmware" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the manual files?
[/usr/share/man]

In which directory do you want to install the documentation files?
[/usr/share/doc/vmware]

The path "/usr/share/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

The installation of VMware Server 1.0.0 build-28343 for Linux completed
successfully. You can decide to remove this software from your system at any
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Server for the first time, you need to configure it by
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this
program to invoke the command for you now? [yes]

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

You must read and accept the End User License Agreement to continue.
Press enter to display it.

VMWARE MASTER END USER LICENSE AGREEMENT

blah blah blahj
you gotta agree to this part ~_~


[email]VMware_server_distribution@vmware.com[/email] and we
will provide you with a copy of our
distribution agreement for your signature.





Do you accept? (yes/no) yes

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-27-k7/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.15-27-k7/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-k7'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-k7'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes] yes

Configuring a bridged network for vmnet0.

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes]

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.188.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.188.0.

Do you wish to configure another NAT network? (yes/no) [no]

Do you want to be able to use host-only networking in your virtual machines?
[yes]

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.105.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.105.0.

Do you wish to configure another host-only network? (yes/no) [no]

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.15-27-k7/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-k7'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-k7'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902]

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files?
[/var/lib/vmware/Virtual Machines] /home/nekostar/vmware/Virtual Machines

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  904K8-YAPF7-2DM1N-4JJ3N

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Server 1.0.0 build-28343 for Linux for this running
kernel completed successfully.

nekostar@dapper-xp:~/vmware-server-distrib$

---

### Post by starscalling on 2006-09-20
just an example of a sucessful install according to guide etc for the peeps on the irc chan etc :P

---

### Post by Zyzzyx on 2006-09-20
Set this up the other night, no problems. Great walkthrough.

Was also able to get Vista RC1 up and running in VMware as well.

---

### Post by paddyman1973 on 2006-09-21
Hi, I am getting the exact same error as posted. I have tried to find any answers to your question in the thread but can't see anything pertainent. What was the answer in the end?



> **Endwin said:**
> I was able to install the server on a machine where I keep my files, and on my laptop I installed the vmware-server-console. I can connect up fine, create the machine, but when I turn it on I get 

Error during launch: 11, The process exited with an error:
End of error message

When I check the /var/log/vmware/serverd.log I see...

Jun 28 19:07:08: app| SP: Retrieved username: endwin
Jun 28 19:07:11: app| Adding to list of running vms: /var/lib/vmware/machines/Windows 2000 Professional/Windows 2000 Professional.vmx
Jun 28 19:07:11: app| Attempting to launch vmx : /var/lib/vmware/machines/Windows 2000 Professional/Windows 2000 Professional.vmx
Jun 28 19:07:11: app| Error during launch: 11, The process exited with an error:
Jun 28 19:07:11: app| End of error message
Jun 28 19:07:11: app| VmsdVmStatePendingCmdFailed: cmd status is already set
Jun 28 19:39:46: app| Attempting to launch vmx : /var/lib/vmware/machines/Windows 2000 Professional/Windows 2000 Professional.vmx
Jun 28 19:39:46: app| Error during launch: 11, The process exited with an error:
Jun 28 19:39:46: app| End of error message
Jun 28 19:39:46: app| VmsdVmStatePendingCmdFailed: cmd status is already set
Jun 28 19:39:50: app| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
Jun 28 19:39:50: app| SP: Deleting user session: 0 username: endwin
Jun 28 19:40:08: app| New connection on socket server-vmdb from host 192.168.0.3 (ip address: 192.168.0.3) , user: endwin
Jun 28 19:40:08: app| SP: New user session for user: endwin, pos: 0
Jun 28 19:40:08: app| The vm-list file has changed! Reloading the list of registered vms
Jun 28 19:40:10: app| SP: Retrieved username: endwin
Jun 28 19:40:15: app| Attempting to launch vmx : /var/lib/vmware/machines/Windows 2000 Professional/Windows 2000 Professional.vmx
Jun 28 19:40:15: app| Error during launch: 11, The process exited with an error:
Jun 28 19:40:15: app| End of error message
Jun 28 19:40:15: app| VmsdVmStatePendingCmdFailed: cmd status is already set
Jun 28 19:40:25: app| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
Jun 28 19:40:25: app| SP: Deleting user session: 0 username: endwin

Any idea on what needs to me modified/installed/whatever?

---

### Post by tymek666 on 2006-09-24
Thanks a lot for this howto, works great!

---

### Post by Heideho on 2006-09-25
Hello

What a great HowTo and a truly fascinating read.  I have what I hope is a simple question for you learned souls to answer.  I am new to Ubuntu and Linux and trying to get my head around all this after a failed attempt to install Linux 2 years ago. 

I have a home network with the server currently running on Windows.  It performs duty as a file server for 4 users and connects to my 2 USB printers (both Canon - LBP-1120 and IP4000). I have scheduled backups that run regularly to 2 external USB hard drives.

I repartitioned the server and installed Ubuntu 6.06 as dual boot to see if I could replace Windows and I have been happy so far. Until (that is) I discovered my Canon laser was a WinPrinter and was troublesome to share in Linux. A friend suggested I try VMWare and that's how I stumbled onto this HowTo.

Before I jump in boots and all and try to fathom all of this new stuff can someone tell me:

*If I run Windows under VMWare will it let me share my printers across my Windows network? It looks like my file sharing needs are adequately met already and my backups can run Ok too. I just need to understand if there is a practical way to manage the printer shares.*

Thanks! :-k

---

### Post by Xecuter on 2006-09-25
I did something really stupid. I accidently deleted the wrong directory, the install directory. So VMWare wouldn't start, and I tried a reinstall:
```
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/sivert/vmware/vmware-uninstall.pl.

Failure

Execution aborted.

```

Is there a way to force an installation? Or remove the rest of the traces?? Please help!

---

### Post by iam_foo on 2006-09-25
just wanted to say ty.
i appreciate the howto.
the install went smooth as silk.

:twisted:

---

### Post by nzgreen on 2006-09-25
> **Heideho said:**
> 
*If I run Windows under VMWare will it let me share my printers across my Windows network? It looks like my file sharing needs are adequately met already and my backups can run Ok too. I just need to understand if there is a practical way to manage the printer shares.*

Thanks! :-k

Yes it will.  The only caveat is that you must use bridged networking for your Windows guest.  This will ensure that Windows is on the same subnet as your Ubuntu box (and presumably the clients that need to use the printer) and network browsing will work.

---

### Post by Heideho on 2006-09-25
> **nzgreen said:**
> Yes it will.  The only caveat is that you must use bridged networking for your Windows guest.  This will ensure that Windows is on the same subnet as your Ubuntu box (and presumably the clients that need to use the printer) and network browsing will work.

Thank you!:)

---

### Post by BLTicklemonster on 2006-09-26
I can't use my headset microphone in xp in vmware server. I have installed tools. The audio is really really low, but if I shout, it's barely audible on the other end. Creative labs. It works fine in gnome, dapper, though.

---

### Post by ekuliak on 2006-09-26
I updated my kernel a few days back when I was notified that an update was ready.  Unfortunately, now it seems I need to reconfigure vmware (it was working before the kernel update).  

However, this is the option I'm stuck on: 
```

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

```

What is the correct location of the C header files?  
I believe the kernel is 2.6.15-27

---

### Post by enopepsoo on 2006-09-26
I did not install XP, but thanks for the awesome How To.  VMWare server is working like a charm.

It even had to compile something, because I am on an AMD X2.  I guess it needed something extra!

---

### Post by qrm on 2006-09-27
im running edgy and got it installed just fine, but when I try to strat vmware via terminal or menu it just wont show up. Ideas?

---

### Post by nzgreen on 2006-09-27
> **ekuliak said:**
> I updated my kernel a few days back when I was notified that an update was ready.  Unfortunately, now it seems I need to reconfigure vmware (it was working before the kernel update).  

However, this is the option I'm stuck on: 
```

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

```

What is the correct location of the C header files?  
I believe the kernel is 2.6.15-27

Did you perform this step?
```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
```

That should install the headers for your running kernel (along with build-essential and xinetd).

---

### Post by Archville on 2006-09-27
I have exactly the same error. I've installed it on Edgy Eft but when i type "vmware" the console does not appear. There is just a "vmware" proccess using 99% cpu, but no error messages.

---

### Post by chameleon_789 on 2006-09-27
> **Archville said:**
> I have exactly the same error. I've installed it on Edgy Eft but when i type "vmware" the console does not appear. There is just a "vmware" proccess using 99% cpu, but no error messages.

> **qrm said:**
> im running edgy and got it installed just fine, but when I try to strat vmware via terminal or menu it just wont show up. Ideas?

Same here. Seems to install fine, although while it compiles it throws a couple of errors out :

```

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-10-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
**** builds other modules
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
**WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o**
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

```

```

/usr/share/applications/vmware-server.desktop: error: Categories values must be one of "Core", "Development", (etc)... (found "Application")

```

Can anyone confirm that those errors are happening when they compile as well..?

---

### Post by Darknezzdell on 2006-09-27
Hi, I had the same problem as everyone else, but I did manage to fix it. I'm a linux noob but I used the search in ubuntu looking for .h files. Then I just typed /usr/include knowing that the .h files in this folder wasn't the rigt ones.

I then got the message back, that the kernel version is 2.6.15- something else.

I then typed sudo apt-get install linux-headers-2.6.15-xxxxx

after this I had no problem with 
[I]
Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.[/I]

I'm now installiing windows xp under VMWARE. 

Sorry for my poor english, since danish is my primary language.

any questions about my workaround fix, just mail me.:-D :KS

---

### Post by qrm on 2006-09-27
could you please define your steps in a bit more prescision?

---

### Post by chameleon_789 on 2006-09-27
Ok, for you guys who can't run vmware server on edgy, I've done a bit of searching:
> problem is that you have libhal compiled against dbus 0.9, while dbus 0.6 is available on your system as well (libdbus-1.so.2 and libdbus-1.so.3). VMware loads libdbus-1.so.2 for itself, libhal loads libdbus-1.so.3 for itself, and then bad things happen as two libdbuses cannot coexist. If you'll uninstall package which provides libdbus-1.so.2, crashes will disappear.

There are two workarounds for the time being, either uninstall libdbus-1-2 with synaptic/apt-get, etc (as far as I can tell there aren't many programs which depend on it), or use this : 
```
LD_PRELOAD=/usr/lib/libdbus-1.so.3 vmware
```

Hope that helps... seems to be working fine for me now, even with the error messages in the compile :)

---

### Post by ekuliak on 2006-09-27
> **nzgreen said:**
> Did you perform this step?
```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
```

That should install the headers for your running kernel (along with build-essential and xinetd).

Thanks!  That did it!  :D

---

### Post by BLTicklemonster on 2006-09-28
> **Billquinn1 said:**
> This guy has a guide useing Vista beta and pulls it from the iso.

[http://ubuntuforums.org/showthread.php?t=192328&highlight=vista+vmware](http://ubuntuforums.org/showthread.php?t=192328&highlight=vista+vmware)

Bill

Sweet, thanks, I'm installing Edgy in VM right now. Going to test it out before I decide if it's ... I mean decide if I'M ready for it or not :)

---

### Post by dtmilano on 2006-09-28
You may also be interested in running only one Windows application, say Microsoft Internet Explorer.
Take a look at my [blog post]("http://dtmilano.blogspot.com/2006/09/running-microsoft-internet-explorer-on.html") where there's a screenshot and although the howto article is not finished you will find the idea and the tools needed to achieve it.
Any comments are gladly welcome.

---

### Post by Xecuter on 2006-09-29
I did something really stupid. I accidently deleted the wrong directory, the install directory. So VMWare wouldn't start, and I tried a reinstall:
```
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/sivert/vmware/vmware-uninstall.pl.

Failure

Execution aborted.

```

Is there a way to force an installation? Or remove the rest of the traces?? Please help!

---

### Post by BLTicklemonster on 2006-09-29
On a whim, if you can even do this, try ctrl alt del and see if you get to the "device manager", then look through your processes and see if you see vmware stuff running in the background, and kill them, then try it again. Probably not going to work, but I have noticed vmware stuff running in there when it was not supposed to be.

---

### Post by mitch.c on 2006-09-29
> **Xecuter said:**
> I did something really stupid. I accidently deleted the wrong directory, the install directory. So VMWare wouldn't start, and I tried a reinstall:
```
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/sivert/vmware/vmware-uninstall.pl.

Failure

Execution aborted.

```

Is there a way to force an installation? Or remove the rest of the traces?? Please help!

Been there...
```
rm -rf /etc/vmware/
```

---

### Post by Xecuter on 2006-09-29
Thank you! :D I could hug you, but I'm not going to. That's for the best! ;) :P

---

### Post by [Yatta] on 2006-09-30
> **chameleon_789 said:**
> Ok, for you guys who can't run vmware server on edgy, I've done a bit of searching:


There are two workarounds for the time being, either uninstall libdbus-1-2 with synaptic/apt-get, etc (as far as I can tell there aren't many programs which depend on it), or use this : 
```
LD_PRELOAD=/usr/lib/libdbus-1.so.3 vmware
```

Hope that helps... seems to be working fine for me now, even with the error messages in the compile :)

THANK YOU!!!!!!!!! that has worked for me.. i also upgraded to Edgy and for the life of me vmware just would not start!!! but that:
```
LD_PRELOAD=/usr/lib/libdbus-1.so.3 vmware
```
Worked...

---

### Post by Josh1 on 2006-09-30
Cool, thanks :).

---

### Post by nuub on 2006-09-30
very newby and trying to install vmware server. i've followed these instructions (thx) but the config asks me for the location of my make file. i know what the make file is and purpose but can't find it on my system and how to install it.

---

### Post by Muschl on 2006-10-01
Hi,

i would like to run my real Windows XP installation under Ubuntu VMWare Server.
With the help from the following sites you can configure your VMWare Server to boot into raw disks.

[http://forums.gentoo.org/viewtopic-t-246371-highlight-ntfs%20vmware.html](http://forums.gentoo.org/viewtopic-t-246371-highlight-ntfs%20vmware.html)
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

Now the Solution for No Keyboard and Mouse in VMWare.

1. Download the PE HWPnP Tool from Paraglider
[http://www.paraglidernc.com/plugins/HWPnP.cab](http://www.paraglidernc.com/plugins/HWPnP.cab)

2. Create the directory C:\fixvm\ on your Windows XP System Disk (C:\)
mkdir /media/hda1/fixvm

2. Extract the Files to the folder C:\fixvm\ on your Windows XP System Disk (C:\)
cabextract -d /media/hda1/fixVM HWPnP.cab
mkdir /tmp/iso
mount -t iso9660 /usr/lib/vmware/isoimages/windows.iso -o loop /tmp/iso
cp -r /tmp/iso/* /media/hda1/fixvm
echo FixVM Stage 1 start > /media/hda/fixvm/stage1.txt

3. create the C:\fixvm\fixvm.cmd file on your Windows System disk and inject the following content

echo Searching for FixVM Stage
if exist C:\fixvm\stage1.txt (
echo FixVM Stage 1 found
msiexec -i "C:\fixvm\VMware Tools.msi" ADDLOCAL=ALL /qn
del C:\fixvm\stage1.txt
echo Stage 1 finished successfully > C:\fixvm\stage2.txt
shutdown -r -f -t 30
)
if exist C:\fixvm\stage2.txt (
C:\fixVM\HWPnP.exe +all
del C:\fixvm\stage2.txt
echo.
echo Please check the function of your Mouse and Keyboard
echo.
pause
)
end

4. reboot into your real Windows

5. Change the following Registry Keys (start/run/regedit.exe)
\HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon
- AutoAdminLogon = 1
- AutoLogonCount = 5

(remember the Administrator must have a Password set)

(i think the next entrys are not needed, use it when you have problems)
- DefaultUser = *your USERNAME*
- DefaultUserName = *your USERNAME*
- DefaultPassword = *your Password*

6. Create fixvm.cmd shortcut in Startmenu/Programs/startup Folder (start/run/cmd)
ln -s C:\fixvm\fixvm.cmd "C:\Documents and Settings\All Users\Start Menu\Programs\Startup\fixvm"

7. configure Windows for automated driver installation (start/run/cmd)
sysdm.cpl
- on tab Hardware klick the Button DriverSigning and set it to Ignore

8. After all this steps reboot into the VMWare Server running OS and start the VMWare raw disk WindowsXP.

what the script do:
- system boot
- autologon
- auto installing VMWare Tools
- reboot
- autologon
- auto Plug and Play Hardware detection

tell me if you have problems with the script or the guidance...

---

### Post by godtvisken on 2006-10-01
Well, I tried going through the Windows XP installation, but it reports:

"Setup did not find any hard disk drives installed on your computer."

Here is a screenshot: [http://img218.imageshack.us/img218/1184/vmwarevd8.png](http://img218.imageshack.us/img218/1184/vmwarevd8.png)

What can I do to fix this?

---

### Post by 13east on 2006-10-01
i can't seem to be able to complete this installation. after i'm asked where  to save the documentation files, i get an error message saying 'Unable to get the access rights of source file "./vmware-vix/bin". Execution aborted.'  can someone please help?

---

### Post by godtvisken on 2006-10-01
> **13east said:**
> i can't seem to be able to complete this installation. after i'm asked where  to save the documentation files, i get an error message saying 'Unable to get the access rights of source file "./vmware-vix/bin". Execution aborted.'  can someone please help?

are you doing this as root?

---

### Post by 13east on 2006-10-01
> **godtvisken said:**
> are you doing this as root?

yea i am...

---

### Post by godtvisken on 2006-10-02
> **godtvisken said:**
> Well, I tried going through the Windows XP installation, but it reports:

"Setup did not find any hard disk drives installed on your computer."

Here is a screenshot: [http://img218.imageshack.us/img218/1184/vmwarevd8.png](http://img218.imageshack.us/img218/1184/vmwarevd8.png)

What can I do to fix this?

Any ideas? :confused:

I do have a virtual harddisk installed. At least I think I do. Would it matter if I only allocated 4.5 GB for the disk? Here you can see that I have a hard disk: [http://img208.imageshack.us/img208/7306/vmharddiskcx6.png](http://img208.imageshack.us/img208/7306/vmharddiskcx6.png)

Naturally I'm attempting the installation through the CD drive.

---

### Post by SkyNet2029 on 2006-10-05
Very nice how-to. Although I did not use it to install any bloatware..umm.. I mean xp. Anyway, this works fine with the image for FreeBSD 6.1 using the same info you posted (with Kubuntu 6.06 as Host OS). Again, Niiiiiiiiiiiiiiii-ce! :)

---

### Post by dolarsrg on 2006-10-05
Hi everyone. Thank you very much for this Howto!!

I've the same question than [http://www.ubuntuforums.org/showpost.php?p=1545824&postcount=548](http://www.ubuntuforums.org/showpost.php?p=1545824&postcount=548)

Is it possible to have the microphone working in WMWare Server?? It isn't in the hardware list to add to the virtual machine :( 

Thanks in advance ;)

---

### Post by galego on 2006-10-06
i cant figure out how to unlock the host so i can have NAT working. in XP i have limited connectivity. the NIC pings back but i have no DNS server or subnet mask. in the VMWare window it shows the host connection as locked. how can i unlock it?

---

### Post by daniel.r on 2006-10-07
> **darrenm said:**
> A cool thing to do with running XP in vmware on linux is to enable remote desktop, SSH in remotely using putty to your linux box and tunnel port 3389 to the IP of XP in vmware. Then just connect rdesktop to localhost:3389 and it runs superbly quick even on modest hardware. You also dont get the keyboard/mouse grabbing weirdness of using the vmware server console to contend with.

How can be achieved a such thing? I have successfully installed vmware-server, but I don't really know how to setup the virtual machine (network settings) and how to setup the ssh tunneling (including the configuration of my shorewall firewall).

Hope somebody can help me,

Daniel

---

### Post by darrenm on 2006-10-07
Replied to your email :)

---

### Post by dolarsrg on 2006-10-08
Then, there is nothing about the microphone?? :(

---

### Post by techstop on 2006-10-10
> **darrenm said:**
> Replied to your email :)

I would also like to know the answer to this, would you care to post the answer in the thread? :?:

---

### Post by the_maassk on 2006-10-15
I guess mine is a weird one! 

Sucessfully installed vmware-server but when I run **vmware** from the terminal, nothing happens! The only thing I get is:

GTK Accessibility Module initialized

No error messages...nothing! I even tried the vmware player - same result. I turned off Beryl and tried - nothing. 

Please HELP!!! ](*,)

---

### Post by daou on 2006-10-16
Great howto!

My new Ubuntu-Windows TwinView w/ Beryl hybrid:
[[IMG]http://img528.imageshack.us/img528/3917/screenshot2db1.th.png[/IMG]](http://img528.imageshack.us/my.php?image=screenshot2db1.png)

I had a little trouble with the networking and samba part, working now though. It's set up with a bridged connection at the moment but I'm a little concerned about the WinXP-Internet connection. Is there some way I can restrict its internet access, but still have access to samba on the host? 
Should I be worried about antivirus-firewall?

---

### Post by nwgray on 2006-10-19
Just installed vmware server on Edgy. The install went great but now when I try to run it, I get this in a term window:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

I have to kill the vmware process.

Any ideas?

---

### Post by darrenm on 2006-10-19
> **nwgray said:**
> Just installed vmware server on Edgy. The install went great but now when I try to run it, I get this in a term window:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

I have to kill the vmware process.

Any ideas?

Yep 

```
sudo apt-get remove libdbus-1-2
``` :)

---

### Post by nwgray on 2006-10-19
> **darrenm said:**
> Yep 

```
sudo apt-get remove libdbus-1-2
``` :)


That did the trick. Thx sooo much darren!:KS

---

### Post by daybreaker on 2006-10-19
Whenever I try to install VMWare, I get through a couple questions and then get this error:

```
The path "/home/daybreaker2/Programs/doc/vmware" does not exist currently. This
program is going to create it, including needed parent directories. Is this
what you want? [yes]

Unable to get the access rights of source file "./vmware-vix/bin".
```

---

### Post by BLTicklemonster on 2006-10-19
I have a strange problem, easy to fix, but the fact that it happens bugs me.

I don't shut down windows when I use it in VMWare, I just close VMWare. This leaves windows sitting there in sleep mode when I come back. Problem is, VMWare starts when I boot. No, it doesn't come up, but it's in the background, and I know it, because I keep hearing the windows startup sound shortly after I boot. Can I keep VMWare from starting in the background? I'd sort of like to keep my resource usage at a minimum.

---

### Post by skirkpatrick on 2006-10-20
You could tell VMWare to suspend before you close it.  It should stay suspended that way.

---

### Post by BLTicklemonster on 2006-10-20
VMWare would suspend XP, but when I would close VMWare, next time I'd boot, VMWare would still be running in the background. What I want to know is how to totally stop VMWare from running silently in the background until such time as I actually start it. 

I have stopped it in the boot menu as far as I can tell, but still, when I turn off my computer, I see it being stopped with all other devices as my machine shuts down.

---

### Post by darrenm on 2006-10-20
> **BLTicklemonster said:**
> VMWare would suspend XP, but when I would close VMWare, next time I'd boot, VMWare would still be running in the background. What I want to know is how to totally stop VMWare from running silently in the background until such time as I actually start it. 

I have stopped it in the boot menu as far as I can tell, but still, when I turn off my computer, I see it being stopped with all other devices as my machine shuts down.

You can tell vmware to start and shutdown any VM's at startup or boot time.

vmware as a service is installed into /etc/init.d then symlinked into the /etc/rc.N directories.

If you want vmware to not start Windows on boot time then just go into the options for that VM and choose to not have it start up.

The vmware service on its own doesnt take much resources and you won't notice it starting up and shutting down.

Of course if you do tell vmware not to shut down the VM operating system on system shutdown then it will just power it off leading to system corruption etc of the VM installed OS. This means you will have to start up/shut down manually or suspend to an image and resume from that.

---

### Post by daybreaker on 2006-10-27
> **daybreaker said:**
> Whenever I try to install VMWare, I get through a couple questions and then get this error:

```
The path "/home/daybreaker2/Programs/doc/vmware" does not exist currently. This
program is going to create it, including needed parent directories. Is this
what you want? [yes]

Unable to get the access rights of source file "./vmware-vix/bin".
```

Just a bump. Any ideas?

---

### Post by darrenm on 2006-10-27
Are you installing as root?

---

### Post by bobap1950 on 2006-10-27
I keep getting the following message:

A previous installation of VMware software has been detected.

Failure

Execution aborted.

I can't find any previous installation.  This really gets frustrating.

Bob

---

### Post by schport on 2006-10-28
Hi.  I am new and I have searched this forum and read many of the posts in this thread.  The solutions previously offered for problems that are similar to mine have not worked for my situation.

I have Edgy installed.  I installed vmware server successfully and it works great until I reboot Ubuntu.
When I reboot Ubuntu, I cannot start the vmware server console unless I re-run /usr/bin/vmware-config.pl 

This is the message that I get.
chad@chad-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

When I installed vmware server and ran /usr/bin/vmware-config.pl I followed the guide to the letter and accepted all the defaults except for the folder to store the virtual machines in.  I changed that folder to /home/chad/vmware

any ideas what I need to do to resolve this inconvenience?


It turns out that I was using the release candidate for Edgy.  After I reinstalled ubuntu using the final version of Edgy, I no longer have this problem.

---

### Post by jmwyatt on 2006-10-28
Identical problem here... Anyone out there have with an idea of how we might fix this? Tkanks.

---

### Post by techstop on 2006-10-28
Could this be the answer?

[http://ubuntuforums.org/showpost.php?p=1364485&postcount=413](http://ubuntuforums.org/showpost.php?p=1364485&postcount=413)

There are some answers to common problems in the very first post too;

[http://ubuntuforums.org/showpost.php?p=1058908&postcount=1](http://ubuntuforums.org/showpost.php?p=1058908&postcount=1)

---

### Post by doogy2004 on 2006-10-30
I'm trying to run VMWare Server on an Ubuntu CLI LAMP Server.  Does anyone know exactly what packages VMWare server depends on?

I'm trying to install VMWare server as clean as possible, I need to know what packages it needs to be completely functional.

Please respond in the following thread:
[http://www.ubuntuforums.org/showthread.php?t=279410](http://www.ubuntuforums.org/showthread.php?t=279410)

---

### Post by dr.lnx on 2006-10-30
hi, i have installed all those thing but when i run vmware it says:
```

root@rix:/usr/local/vmware-server-distrib# vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)


```
and it stops 
what could I do to make  it work?

---

### Post by daybreaker on 2006-10-30
> **darrenm said:**
> Are you installing as root?

Yep. Which is why I dont know why I'm getting a message about being unable to access that file.

---

### Post by doogy2004 on 2006-10-30
Does anyone know what packages VMWare server depends on? I want to be able to run VMware on a Command Line LAMP server.

Please respond in the following thread:
[http://www.ubuntuforums.org/showthread.php?t=279410](http://www.ubuntuforums.org/showthread.php?t=279410)

Thanks

---

### Post by techstop on 2006-10-31
please stop cross-posting! ](*,)

---

### Post by Juhwetus on 2006-11-02
Unable to get the access rights of source file "./vmware-vix/bin".

If I remember correctly I had no bin folder in vmware-vix folder so I created  one. So in vmware-vix just type mkdir bin. After that I got it to install. 

After installing I tried to start vmware from console by typing vmware and got this: vmware: command not found. I also wasn't able to start it through menus and got "failed to execute child process 'vmware' No such file or directory". This I solved by going to the vmware-directory which was specified during install-process and just typed in console ./vmware which got the program running.

I still didn't get it working perfectly because when starting vmware I got something like 
/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
 
This I solved by copying libpng12.so.0 from /usr/lib/libpng12.so.0 to ~/lib/vmware/lib/libpng12.so.0/libpng12.so.0

After those I got it working and it seems stable so far. tried it with xp pro. Hope this helps someone.

---

### Post by BLTicklemonster on 2006-11-02
> **techstop said:**
> please stop cross-posting! ](*,)

:-k 


So, if I have vmware on dapper, and dual boot with edgy, can I set up vmware server, then drag my virtual drive to edgy and use it? No links, but physically move the virtual drive's folder and use it? (copy and paste, actually) If so, then which is it? and is this basically what the cross dres- I mean poster was asking?

---

### Post by __InFeRnO__ on 2006-11-02
Does this work with Edgy?

Or is there any way I can get this working on Edgy?

---

### Post by BLTicklemonster on 2006-11-02
I intend to give it a shot this evening, I'll let you know :mrgreen:

---

### Post by techstop on 2006-11-02
> **__InFeRnO__ said:**
> Does this work with Edgy?

Or is there any way I can get this working on Edgy?

Working perfectly here! No change to the HOWTO, it's probably even easier as the kernel headers were already installed on my system.

> **BLTicklemonster said:**
> :-k 


So, if I have vmware on dapper, and dual boot with edgy, can I set up vmware server, then drag my virtual drive to edgy and use it? No links, but physically move the virtual drive's folder and use it? (copy and paste, actually) If so, then which is it? and is this basically what the cross dres- I mean poster was asking?

Cross-posting is posting the same question in multiple threads, which is what this person has done;

[http://ubuntuforums.org/showpost.php?p=1691792&postcount=599](http://ubuntuforums.org/showpost.php?p=1691792&postcount=599)

As to your question, yes, virtual hard drives are portable. You can move them and open them wherever you like. I created a WinXP guest OS in dapper, copied it to an SMB shared folder and then copied to a USB external hard drive. I take the external HDD to uni, and I get to run my own Windows installation at uni instead of their stupid SOE. I clean installed edgy, reinstalled Vmware server according to this HOWTO, copied the WinXP guest OS folder back from the SMB share, and it works perfectly. When you move the guest OS around, sometimes Vmware (server or player) prompts you to create a new identifer, but that's all there is to it.

---

### Post by gerrno on 2006-11-02
Thanks a 10000*n-times for this HowTo!! I tried to get the win progs to work with wine, but win just can't compare to VMware!!! Install's without a problem.

---

### Post by darrenm on 2006-11-02
May have been said somewhere else along this thread but I find it much better to enable remote desktop in XP in VMware then just run tsclient to remote desktop to it.

---

### Post by techstop on 2006-11-02
> **darrenm said:**
> May have been said somewhere else along this thread but I find it much better to enable remote desktop in XP in VMware then just run tsclient to remote desktop to it.

Yes, it has been mentioned, by you in fact. :-D However, when asked by someone how to do it, you weren't forthcoming with the information;

[http://ubuntuforums.org/showpost.php?p=1589451&postcount=577](http://ubuntuforums.org/showpost.php?p=1589451&postcount=577)
[http://ubuntuforums.org/showpost.php?p=1599780&postcount=580](http://ubuntuforums.org/showpost.php?p=1599780&postcount=580)

So, you would you like to share the knowledge? ;) 

And, what is the benefit of remote desktop when the guest os is already running in vmware anyway? Does it just let you access the windows os from multiple machines?

EDIT: The remote desktop in XP is fine, I'm interested in the SSH stuff.

---

### Post by BLTicklemonster on 2006-11-02
Installed easily enough, and I just opened xp from my dapper drive instead of copy and pasting. (because I don't have permission, of course, duh) ](*,)

---

### Post by lime4x4 on 2006-11-02
Just installed it on a fresh copy of edgy.The how to works great.My only problem is i can't connect to the internet.My edgy box is directly plugged into the cable modem which gets an ip addy. I guess i'll have to play with the vm settings

---

### Post by techstop on 2006-11-02
> **lime4x4 said:**
> Just installed it on a fresh copy of edgy.The how to works great.My only problem is i can't connect to the internet.My edgy box is directly plugged into the cable modem which gets an ip addy. I guess i'll have to play with the vm settings

Set your guest OS to use a bridged connection, that is the easiest...

---

### Post by lime4x4 on 2006-11-02
actually i set the vmware network to nat and that seems to be working.
Also is it possible to c the guest operating system's hard disk from edgy?

---

### Post by techstop on 2006-11-02
> **lime4x4 said:**
> actually i set the vmware network to nat and that seems to be working.
Also is it possible to c the guest operating system's hard disk from edgy?

See the host OS hard drive from the guest OS? Not AFAIK. Best bet is to set up a network share and access that from the guest.

---

### Post by headchange on 2006-11-03
thanks the headers dl of the edgy default kernel did the job, this and my nvidia card are the only probs i have had so far, thanks again

---

### Post by djroadrash on 2006-11-04
hola everyone
thanx to peturrr for a great howto, i had a couple of snags but other peoples reply's helped a lot, i had to put a couple of commands for vmware to finish installing, im not sure if the first or the second one helped but after i typed:```
mkdir vmware-vix/bin
 sudo ./vmware-install.sh

```
then i started the installation again
```
 sudo ./vmware-install.pl

```
the install did finish this time, the only other problem as other people seem to have is that i can't start vmware from the menu or from console no matter if i put sudo vmware or not, only from my home folder where the files are.

one thing i want to ask, and i think someone else was asking is, is it safe to surf the web, or do i need a virus protection software inside the virtual xp? other than than, a great guide and awesome support.
thanx peturrr and all the people that has helped with hints.
armando:)

---

### Post by skirkpatrick on 2006-11-04
For all intents and purposes, your virtual XP is no different than a normal XP.  Which means it can have all the same problems.

---

### Post by themunkee on 2006-11-07
Here's a quick update for Edgy using VMWare Player. It's mainly a rehash of bits I picked up from other posts, tied together. I tried this on an AMD64, but it should work for 32bits...

[SIZE="3"]**Procedure**[/SIZE]
* Load up Synaptic: System->Admin->Synaptic

* Install VMWare Player and QEMU (do a search).

* Create a new directory to store this machine in, and move there:
```
mkdir ~/VM/XP
```
```
cd ~/VM/XP
```

* Copy your XP CD. In terminal:
```
dd if=/dev/hdc of=WindowsXPPro.iso
```
where /dev/hdc is to location of the drive containing the CD. This will create an ISO called WindowsXPPro.iso

* Create a virtual drive:
```
qemu-img create -f vmdk WindowsXPPro.vmdk 10G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=10485760 kB
```
This will create a 10G drive. Adjust the 10G and 10485760 as required.

* Create our VMX file:
```
gedit WindowsXPPro.vmx
```

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "WindowsXPPro.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.fileType = "file"
floppy0.fileName = "cdboot1.img"
floppy0.startConnected = "FALSE"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
uuid.bios = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
ethernet0.generatedAddress = "00:0c:29:4c:23:7b"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "WindowsXPPro.vmss"
tools.remindInstall = "TRUE"
```

* Save, file as WindowsXPPro.vmx into the relevant folder.

* Start vmplayer from: Applications->System Tools->VM Player. Load WindowsXPPro.vmx and follow installation.

[SIZE="3"]**Note**[/SIZE]

* If you decide you want to boot some other file/folder as an ISO:
```
mkisofs -RJ -o /tmp/cd.iso /tmp/directory/
```
Where /tmp/cd.iso will be the output of the contents of /tmp/directory.

* You can then, if you haven't got Samba working, change the VMX file to boot the ISO as a CD by changing  WindowsXPPro.iso to cd.iso.

---

### Post by eagle63 on 2006-11-08
Hmmm, so I'm installing vmwareserver on Edgy and everything seems to be going fine until I hit this message:

"None of the pre-built vmmon modules for VMWare Server is suitable for your running kernel.  Do you want this program to try to build the vmmon module for your system(you need to have a C compiler installed on your system)?"

I guess I answer yes here??  Has anyone seen this before?  It makes me a little nervous because I haven't seen anyone else report this.  Thanks,

---

### Post by techstop on 2006-11-09
Yes, this is completely normal. Just answer yes.

---

### Post by doogy2004 on 2006-11-09
I installed VMware Server before I aquired a key, I have since registered and now have a serial number.  The problem is that when I attempt to enter my serial number using the GUI it gives me an error that I do not have sufficient privilages.

Running the GUI as root is not an option because I'm running VMware server remotely, and root is not enabled on the server, nor do I want to enable it for security reasons.

Where is the file that contains the serial, so that I can change the permissions to allow me to modify it.


Also, when using the MUI and I click the options link, it tells me that I do not have sufficient privilages.  Same question as above.

Where is the file that contains the settings, so that I can change the permissions to allow me to modify it.

Thanks in advance.

---

### Post by budman21901 on 2006-11-10
Thank you!  It took me a little time to get it working correctly since i only been using Linux for a few months.  I got it working perfectly now though.  I removed my dual boot, and i am all Linux now.  Now for a tutorial on using networking to get files back and forth would be great.  I am sure it has been posted.  I will do some searches later.  This is much appreciated on my end!      


[http://home.comcast.net/~budman21901/Screenshot-6.png](http://home.comcast.net/~budman21901/Screenshot-6.png)

---

### Post by OrganicPanda on 2006-11-10
I got this all up and working correctly but after I booted XP for the first time the sound (for the rest of my system, rhthymbox etc..) dropped and then after I closed vmware and rebooted I now have no sound atall, What could have caused this and how can I fix it?


EDIT: It seems asif I only get sound back once XP is booted up again??!?

Cheers,
Panda

---

### Post by outofnicks on 2006-11-10
Couple of quick questions, if I may:
Is 256 mb of RAM enough to run vmware and XP or 2000? I'm anxious to give this a try, but dont' want to wait until I can afford some additional RAM.

Second, how big is the download of Vmware Server? (the free version). I'm on dialup, and can move my box to a friend's DSL hookup down the road if necessary. Just nice to know ahead of time, and I can't find the info anywhere.
Thanks!

---

### Post by _duncan_ on 2006-11-11
If 256 mb is your total RAM, it's probably a bit low. I have 512 mb, vmware server allocates about 200 mb to running xp, and already I can feel some sluggishness.

vmware server download is about 100mb.

---

### Post by iceman504 on 2006-11-13
i just tried installing VMware server after installing VMware player and i keep getting A previous installation of VMware software has been detected. then the installation aborts.... I tried a complete removal of VMware player but i keep getting the same error.
Is there something else i need to uninstall?

---

### Post by yabbadabbadont on 2006-11-13
If you have removed vmware-player, then you might need to remove the /etc/vmware directory too.  I don't think that it gets removed automagically.

---

### Post by Aditz on 2006-11-13
I use Kubuntu now and I want to install VMWare. I have 1 GB RAM and 1 GB swap, but Kubuntu occupies about 700 MB. I wonder if I should use Ubuntu instead.

---

### Post by iceman504 on 2006-11-13
removing the etc/vmware directory did the trick thanks yabba

---

### Post by fabertawe on 2006-11-14
> **Aditz said:**
> I use Kubuntu now and I want to install VMWare. I have 1 GB RAM and 1 GB swap, but Kubuntu occupies about 700 MB. I wonder if I should use Ubuntu instead.

I'm using Ubuntu (Edgy) with Beryl, Swiftfox, nautilus file browser, a terminal, Thunderbird, Skype and GYachI running right now (plus various panel applets loaded) and I'm using 312Mb at this moment (0% swap used).

I run VMWare (XP) with 512Mb.

Paul

---

### Post by Aditz on 2006-11-14
I installed VMWare, it works, but it doesn't see other partitions, so it's useless for me. Please tell me how to uninstall.

---

### Post by skirkpatrick on 2006-11-14
VMWare can see your partitions, you just have to create a virtual drive and configure it to use a real drive.  Doing this allows you to create a virtual machine that runs a copy of Windows you've already installed.

---

### Post by n3rdism on 2006-11-16
Awesome how-to!
Good job!!

---

### Post by bionnaki on 2006-11-16
I was able to install vmware on edgy. But after reboot, it would not start up. when running vmware from the terminal I get the following error:

> vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


when I run sudo /usr/bin/vmware-config.pl I receive this error:

> sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.


I could not find how to solve this, so I decied to uninstall vmware in order to reinstall. I did sudo vmware-uninstall.pl as well as sudo rm -R /etc/vmware

When I try to reinstall I get this error:

> Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


I am lost. Anyone know how to fix this?

---

### Post by ixus_123 on 2006-11-16
Brilliant!  Thanks for this.

I'm just about to start studying Microsoft MCP's & this means I can install & run their operating systems without having to repartition my drive & more importantly, without quiting ubuntu which is fantastic as I like to have it running tasks so it's no good booted into Windows.

Got 2003 Server up & running (trial version) Now I just need to find XP Pro on their maze of a site - I don't think they offer it as trial.

Thanks so much.  Even without having to study it comes in handy to un Polar software for my heart rate monitor that wont run under wine.

This is just what I needed :)

---

### Post by qrm on 2006-11-16
if anyone has a p4 processor with HyperThreading enabled in bios try disabling it if you get some whacky errors while trying to power on the virtual machines

---

### Post by damcito on 2006-11-16
i've installed, its running ok, but, i cant get localhost to connect, it sucks all my ram and stay right there making "i dont know what" with cpu at 100% and memory at 100%+swap when i click on create a new virtual machine

after a long time, it comes back to where i started, ("button connect to a host" gets active again)

any ideas?


pd: sory for my poor english

---

### Post by darrenm on 2006-11-17
> **techstop said:**
> Yes, it has been mentioned, by you in fact. :-D However, when asked by someone how to do it, you weren't forthcoming with the information;

[http://ubuntuforums.org/showpost.php?p=1589451&postcount=577](http://ubuntuforums.org/showpost.php?p=1589451&postcount=577)
[http://ubuntuforums.org/showpost.php?p=1599780&postcount=580](http://ubuntuforums.org/showpost.php?p=1599780&postcount=580)

So, you would you like to share the knowledge? ;) 

And, what is the benefit of remote desktop when the guest os is already running in vmware anyway? Does it just let you access the windows os from multiple machines?

EDIT: The remote desktop in XP is fine, I'm interested in the SSH stuff.

Oops I'm really sorry, didnt spot those replies on this busy thread :)

I'll do it in proper detail tonight.

@damcito : sudo apt-get remove libdbus-1-2

---

### Post by darrenm on 2006-11-17
Ok some proper info:

Scenario : We are running Ubuntu Dapper/Edgy with an IP of 192.168.0.1
We install Windows XP Professional in VMWare server with bridged networking so it gets an IP of 192.168.0.2

Make sure you set up a user with a password otherwise RDP won't work.

Enable remote desktop by right clicking my computer and going to properties. Go to remote then tick Allow Users to connect remotely to this computer.

Then close VMWare console and open Applications, Internet, Terminal Server Client.

Connect to the IP address of Windows (192.168.0.2) in this case, you can adjust the preferences to your liking.

With RDP working you can then follow the seamless RDP howto:
[http://ubuntuforums.org/showthread.php?t=224212](http://ubuntuforums.org/showthread.php?t=224212)

Then you can run the Windows apps from vmware as if they are local Linux apps.

Next configure remote desktop over SSH:
install openssh-server
```
sudo apt-get install openssh-server
```
Port forward port 22 on your router to your Linux machine and get your outside IP address ([www.whatismyip.com](www.whatismyip.com)) 

Go to someone elses house and download putty [www.putty.nl](www.putty.nl)

Fill in the outside facing IP address of your Ubuntu box that you got from [www.whatismyip.com](www.whatismyip.com) in the putty window and then go to tunnels. Tick the 2 options at the top then put 3390 in the Source port and 192.168.0.2:3389 in the destination. This will forward port 3390 on your friends machine to port 3389 on the windows vmware machine via your Ubuntu box SSH.

Click open in Putty and log in. Then open Remote desktop (or rdesktop on Linux) and connect to localhost:3390 - voila, your Windows vmware machine forwarded over SSH.

Did I make that really confusing? I know this is basic for a lot of people but others have asked for the info.

---

### Post by nuclearj on 2006-11-18
Hey I intalled it and it works awesomely.  Thanks for the great guide!

---

### Post by dklearhos on 2006-11-19
i have a big problem after succesfully installing vmware using the instructions in 1st page.the system halted and had to reboot manual.after rebooting and logging in again the ram is used at 85%+ and have almost no virtual.i cannot even write in gedit!!!!What is going on?i had no problems at all during install....pls need help

---well today it stopped doing all these and i manage to uninstall vmware server.I installed vmware player and it was lot easier to install windows xp using a tutorial which i found in an another post!!

---

### Post by www-empty on 2006-11-21
Thanks for the guide/instructions. Finally got it to install after doing what [this guy]("http://www.vmware.com/community/message.jspa?messageID=451837#451837") did in his gentoo install. I would have liked to install the virtual machines to a FAT32 partition, but that didn't work.

My current problem:
VMware is not a recognized command in the terminal and when clicked from applications>System Tools menu, I get the error 
"Could not launch menu item
Failed to execute child process "vmware" (Permission denied)"

Any help?

---

### Post by dotsi on 2006-11-21
> **skirkpatrick said:**
> VMWare can see your partitions, you just have to **create a virtual drive and configure it to use a real drive**.  Doing this allows you to create a virtual machine that runs a copy of Windows you've already installed.

Could you specify how to exactly do those things?

---

### Post by BLTicklemonster on 2006-11-21
I suppose installing windows 2000 is about the same, right? I might just put it and 98 on VMW just for the heck of it. I wish vista was still a free try out download, I'd install that, too.

---

### Post by damcito on 2006-11-21
> **dklearhos said:**
> i have a big problem after succesfully installing vmware using the instructions in 1st page.the system halted and had to reboot manual.after rebooting and logging in again the ram is used at 85%+ and have almost no virtual.i cannot even write in gedit!!!!What is going on?i had no problems at all during install....pls need help



same problem, it doesnt work the command "sudo apt-get remove libdbus-1-2 "

its not installed

---

### Post by www-empty on 2006-11-21
Didn't work in Edubuntu with gnome, but works in a KDE session. Weird, though  the sound doesn't start/work. Weird. Can't have everything, I guess.

---

### Post by cesera on 2006-11-22
> **Peturrr said:**
> The Installation
[LIST]
[*]Open the downloaded file with the archive manager.
[*]Extract it to somewhere, I will use /tmp here.
[*] Startup the terminal and go to the extracted files 
```
cd /tmp * replace with your download directory*
cd vmware-server-distrib
```
[*]Execute the installation script 
```
sudo ./vmware-install.pl
```
[*]You can accept all defaults, only thing you might want to alter is the directory where the Virtual Machines are stored. I have mine set to /home/username/vmware . But offcourse, just accept the settings you want to.[/LIST]Ok, I did all this on a clean edgy install, but I get this error (with a little preceding text):


 ```
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902]

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

Unable to get the last modification timestamp of the destination file
/etc/vmware/ssl/rui.key.

Execution aborted.

```



The file /etc/vmware/ssl/rui.key does not exist, so I don't know what is happening here, anyone any ideas?

---

### Post by BiggoCharley on 2006-11-22
Tried to install VMware server and all seemed to be going ok downloaded the tar.gz file, unpacked it ok but when I tried to run the install script I got this message:

"root@ubuntu3:~/vmware-server-distrib# ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

root@ubuntu3:~/vmware-server-distrib#"

I had installed the VMware player with Synaptic and subsequently removed it, and that was and is the only VMware product that was ever installed on this system.

Any ideas would be appreciated.

---

### Post by cesera on 2006-11-23
> **cesera said:**
> Ok, I did all this on a clean edgy install, but I get this error:
 
 
 ```
Generating SSL Server Certificate
 
Unable to get the last modification timestamp of the destination file
/etc/vmware/ssl/rui.key.
 
Execution aborted.

```
 
 
 
The file /etc/vmware/ssl/rui.key does not exist, so I don't know what is happening here, anyone any ideas?
 
Tried touching the missing file, which got rid of the error, but then it would not accept the serial number. So after a bit more googling I finally realised I had to install ia32-libs, as that is no longer installed by default on edgy, maybe this could be added to the how-to.

---

### Post by skirkpatrick on 2006-11-24
> **dotsi said:**
> Could you specify how to exactly do those things?

Go into Edit Virtual Machine Settings.  Select your virtual hard drive.  Tell it to use a physical disk.  Then either select the appropriate hard drive or a single partition of a hard drive.  NOTE:  If you pick a previously installed partition of Windows and run it under a virtual machine, XP will see that all of your devices have changed and may cause problems.

You can also use this method with the virtual CD drive to point to an ISO image of a CD instead of using the actual CD drive.

---

### Post by BLTicklemonster on 2006-11-24
In the interest of just plain doing things the hard way, I am trying to install edgy in vmware in edgy. I opened vmware server and chose to create a new ubuntu device, and boot from the live cd and go to install and get to 15 percent installed and it hangs on me. Any ideas what I'm doing wrong? My intention is to upgrade edgy to feisty and test it from there.

---

### Post by dotsi on 2006-11-25
> **skirkpatrick said:**
> Go into Edit Virtual Machine Settings.  Select your virtual hard drive.  Tell it to use a physical disk.  Then either select the appropriate hard drive or a single partition of a hard drive.  NOTE:  If you pick a previously installed partition of Windows and run it under a virtual machine, XP will see that all of your devices have changed and may cause problems.

You can also use this method with the virtual CD drive to point to an ISO image of a CD instead of using the actual CD drive.

I've tried that, but for some reason I can't see any of the partitions on my physical disk. And when I try to use the whole disk, I get a "insufficient permissions" error. I have a dualboot system: on my /dev/sda (it's a SATA drive, is that a problem?) there's sda1 which is the actual Windows partition and sda5 that's the partition for music and pictures and stuff. They're both mounted with ntfs-3g and they show up and work nicely elsewhere in the Linux system. Then there's sda6, which is the Linux partition.

---

### Post by cesera on 2006-11-25
> **dotsi said:**
> I've tried that, but for some reason I can't see any of the partitions on my physical disk. And when I try to use the whole disk, I get a "insufficient permissions" error. I have a dualboot system: on my /dev/sda (it's a SATA drive, is that a problem?) there's sda1 which is the actual Windows partition and sda5 that's the partition for music and pictures and stuff. They're both mounted with ntfs-3g and they show up and work nicely elsewhere in the Linux system. Then there's sda6, which is the Linux partition.
 
Have you seen this: [http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition). I thought it might be helpful.

---

### Post by dotsi on 2006-11-26
> **cesera said:**
> Have you seen this: [http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition). I thought it might be helpful.

It sure is, thanks for the link. Although I managed to get the virtual machine to boot using the physical disk, I still can't get WinXP to start. As I (somewhat rudely) asked at the comment section of that page:

[QUOTE=dotsi]I also get stuck at the “chainloader +1” phase of the WinXP startup. I get no hardware profile selection dialog nor the startup screen.[/QUOTE]

---

### Post by ba5e on 2006-11-26
I am getting the following error:

> 
Could not launch menu item

Failed to execute child process "vmware" (Permission denied)

when launching from the menu, and:
> 
bash: /usr/bin/vmware: Permission denied

when launching from cmd line.

I have made all vmware files owned by my username in the home dir, is it safe to allow use to my user for /usr/bin/vmware and if so, what command should I use for this?

I have uninstalled & re-installed, and configured VMWare correctly.](*,)

---

### Post by BiggoCharley on 2006-11-26
I tried to install windows 98 as a virtual machine but the program can't find a bootable media so the setup woouldn;t complete.  I now want to remove all the windows 98 installation --is it a simple matter of going to my directory in which I have stored the virtual machine "windows98" and deleting all the files having to do with it or is there some other process to go through?:confused:

---

### Post by yabbadabbadont on 2006-11-27
> **BiggoCharley said:**
> I tried to install windows 98 as a virtual machine but the program can't find a bootable media so the setup woouldn;t complete.  I now want to remove all the windows 98 installation --is it a simple matter of going to my directory in which I have stored the virtual machine "windows98" and deleting all the files having to do with it or is there some other process to go through?:confused:

Yes, you just need to delete the VM files realted to your Win98 virtual machine.  However, to install Win98 without a bootable CD, you will need to create/obtain a Win98 boot floppy.  You should then be able to insert the floppy and install it as usual.

---

### Post by cesera on 2006-11-29
> **yabbadabbadont said:**
> to install Win98 without a bootable CD, you will need to create/obtain a Win98 boot floppy.  You should then be able to insert the floppy and install it as usual.If you haven't got one, you can download it from here: [http://www.bootdisk.com/](http://www.bootdisk.com/). Just point the floppy device of your virtual machine to the downloaded image, no need to create a floppy.

---

### Post by cesera on 2006-11-29
> **ba5e said:**
> I am getting the following error:```
bash: /usr/bin/vmware: Permission denied
```when launching from cmd line.
What are the permissions on /usr/bin/vmware?
My machine says:
-r-xr-xr-x 1 root root 4570 2006-11-23 13:46 /usr/bin/vmware

---

### Post by LucidTaZ on 2006-11-29
I just installed the VMWare Server according to this guide. Great guide, it's all explained nice and clean. After the installation I got the libpng12.so.0 error so I followed this post:

> **marianoi said:**
> great guide,

just let me add one thing. If you have the same problem I had with VMWare not starting. You can go to the terminal and type vmware hit enter and see if it claims about "libgcc.s.s0.1" and  "libpng12.so.0" not being recognized. If so, just do the following:

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/

and

sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

For some reason I had problem installing a virtual machine if I ran "vmware" so I always do:

sudo vmware

to run it as a super user (correct me if this is not a good policy please)

Hope this was useful

Cheers

Mariano

Now, when I try to start 'vmware' in the console, nothing happens. It doesn't return to the command line, it doesn't show any windows, nothing. When I try 'sudo vmware' I get the same results.

Could anyone help me out on this? :-k

---

### Post by ba5e on 2006-11-29
> **LucidTaZ said:**
> I just installed the VMWare Server according to this guide. Great guide, it's all explained nice and clean. After the installation I got the libpng12.so.0 error so I followed this post:



Now, when I try to start 'vmware' in the console, nothing happens. It doesn't return to the command line, it doesn't show any windows, nothing. When I try 'sudo vmware' I get the same results.

Could anyone help me out on this? :-k

Yeah, vmware only wants to run as root/sudo its very annoying because I do not like to run in that mode, but as previously stated, by cesera, its owned by root, infact everything in /usr/bin is. It is unsafe just to chown/chmod everything in that dir, So I think we need a new howto to show how we install VMWare to another drive, eg /opt/vmware (this we can safely change the permissions on)

If anyone else has a better idea, I would love to hear it!

---

### Post by schorsch on 2006-11-29
> **LucidTaZ said:**
> Now, when I try to start 'vmware' in the console, nothing happens. It doesn't return to the command line, it doesn't show any windows, nothing. When I try 'sudo vmware' I get the same results.

Could anyone help me out on this? :-k

I had this problem, too. Do you have both packages libdbus-1-2 and libdbus-1-3 installed? After the upgrade from Dapper to Edgy I had both of them and after deinstalling libdbus-1-2 vmware runs like a charm without changing any rights.

---

### Post by LucidTaZ on 2006-11-29
Thank you!! This did it. :)

---

### Post by syrleb on 2006-11-29
it tells me i have already installed vmware, and i havent, i have removed everything to do with vmware from my computer and i still get this error..... its really shitting me

---

### Post by syrleb on 2006-11-29
it tells me i have already installed vmware, and i havent, i have removed everything to do with vmware from my computer and i still get this error.....

---

### Post by syrleb on 2006-11-29
sorry for the multiple posts, my laptop does what it wants rather than what i want

---

### Post by schorsch on 2006-11-30
> **syrleb said:**
> it tells me i have already installed vmware, and i havent, i have removed everything to do with vmware from my computer and i still get this error.....
Are you sure you do not have the directory /etc/vmware ? If it still exists move it somewhere else and try again.

---

### Post by misteral on 2006-12-01
I'm on Kubuntu Dapper on an AMD64. I'd like to follow these instructions, but there is no  linux-headers-2.6.15-27-amd64-generic. Googling this package, it LOOKS like I should be able to apt-get this but it's not in any of my repositories.

Can I be mssing a repository? 
Thanks

---

### Post by bigjoe4265 on 2006-12-02
Hello all,

I have noticed on issue during vmnet module compilation, it throws up an warning shown below.

WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o

My guess is this has to do with bridging wireless adapters (static MAC addresses) and if you have none this can be safely ignored?

VMWare compiles the module successfully and seems to run ok otherwise.  Anyone else seen this and know what it is?

Thank you,

Bigjoe

---

### Post by saintj0n on 2006-12-02
When I go into VM->Settings, the ADD button is grayed out, along with everything on the right side of the screen. I tried typing sudo -s in a terminal window and switching back to the vmware screen but no change. I need to configure mt sound blaster Live card. Any ideas?

---

### Post by bodhi.zazen on 2006-12-03
Nice How-to 

This thread has been added to the UDSF wiki.

[VMWare_WindowsXP](http://doc.gwos.org/index.php/VMWare_WindowsXP)

If you do a major update to your how-to please send me a PM. Either I can teach you how to add to the wiki or I can try to maintain the wiki myself (as time allows), thank you.

Peace be with you,

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by nzgreen on 2006-12-03
> **misteral said:**
> I'm on Kubuntu Dapper on an AMD64. I'd like to follow these instructions, but there is no  linux-headers-2.6.15-27-amd64-generic. Googling this package, it LOOKS like I should be able to apt-get this but it's not in any of my repositories.

Can I be mssing a repository? 
Thanks

Nope, it's in main.  Try either linux-headers-amd64-generic, linux-headers-amd64-k8 or linux-headers-amd64-server.  apt-cache search linux-headers-amd64 to see what each is for.

---

### Post by Coldbird on 2006-12-04
Wow... this even worked on my 64bit Edgy... Congrats... well done Tutorial!

---

### Post by m.musashi on 2006-12-04
First, thanks. This is very cool. I've been wanting to do this but felt intimidated. The how-to is great. I now have XP running in Edgy. Too cool.

Now for a question...

I've tried scanning this thread and I'm sure the answer is here somewhere but I can't find it. I would like to make a copy of my XP install, say XP-1, and use XP-1 to install apps and such. When I manage to muck it up, I want to delete it and make a new copy of my original XP install. Essentially, I'd like to work on getting one install right and then not mess with it but mess with a copy. I don't want to install it from scratch a second time as that might cause problems with activation and it's much easier to copy the install anyway. However, when I try to just copy it, it doesn't work.

Can anyone help?

Thanks.

---

### Post by FattyCNS on 2006-12-05
> **m.musashi said:**
>  I would like to make a copy of my XP install, say XP-1, and use XP-1 to install apps and such. When I manage to muck it up, I want to delete it and make a new copy of my original XP install. 
Thanks.

VMWare has exactly the feature you are looking for. All you need to do is make a "snapshot" of your WindowsXP machine at a time when you're happy with it. You can then install as many programs as you like, destroy the registry, install viruses etc. Then when you have completely messed it up restore the machine back to the state it was in when you took the snapshot! There's a snapshot button on the top menu for your virtual machine.

---

### Post by britt-stinker on 2006-12-05
Hi all!
I have gotten the vmware installed. I can see the shared folders in vmwinxp but not in ubuntu. But I cant open any of them. it asks for password but nothing happens when i enter it. Any help?

---

### Post by m.musashi on 2006-12-05
> **FattyCNS said:**
> VMWare has exactly the feature you are looking for. All you need to do is make a "snapshot" of your WindowsXP machine at a time when you're happy with it. You can then install as many programs as you like, destroy the registry, install viruses etc. Then when you have completely messed it up restore the machine back to the state it was in when you took the snapshot! There's a snapshot button on the top menu for your virtual machine.

Thanks for the feedback. I see how that works and that is very cool. However, is it possible to copy the install to a new virtual machine as well? Maybe it's not all that different but it seems like it would be.

---

### Post by bigjoe4265 on 2006-12-06
> **m.musashi said:**
> Thanks for the feedback. I see how that works and that is very cool. However, is it possible to copy the install to a new virtual machine as well? Maybe it's not all that different but it seems like it would be.

Yes, copying the disk image file and config is possible.  If you accepted the  default location of your VM's during install you should be able to peek in that directory and back the files up, burn them onto CD, etc.  I like to create a base image of XP, load all the patches etc. then shutdown the guest VM and console and back up the directory containing that VM to CD.  Big time saver!

P.S.  VMWare has excellent documentation on their website and an excellent community forum

Bigjoe

---

### Post by FattyCNS on 2006-12-06
> **m.musashi said:**
> Maybe it's not all that different but it seems like it would be.

The snapshot feature will take your virtual machine back to the **exact** state it was when you took the snapshot. It is identical to moving back to a copy of the virtual machine backed up in the same state as the time the snapshot was taken. The only reason I can see to install a backup to a "new" virtual machine is if you wanted to keep a copy of the machine with, for example, certain software installed and then install a different set of software on another (identical) machine.

---

### Post by ThePants on 2006-12-06
not sure if this has been mentioned in these 60 pages, but this suggestion worked for me with installing vmware server on an edgy install upgraded from dapper in getting rid of this error (which is not the real problem: look at the logs in /tmp/vmware)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2) 

[http://tonywhitmore.co.uk/blog/2006/11/07/ubuntu-edgy-and-vmware-workstation-not-a-problem](http://tonywhitmore.co.uk/blog/2006/11/07/ubuntu-edgy-and-vmware-workstation-not-a-problem)

---

### Post by m.musashi on 2006-12-06
> **bigjoe4265 said:**
> Yes, copying the disk image file and config is possible.  If you accepted the  default location of your VM's during install you should be able to peek in that directory and back the files up, burn them onto CD, etc.  I like to create a base image of XP, load all the patches etc. then shutdown the guest VM and console and back up the directory containing that VM to CD.  Big time saver!

P.S.  VMWare has excellent documentation on their website and an excellent community forum

Bigjoe
Thank you. That is something I had not thought about.

> **FattyCNS said:**
> The snapshot feature will take your virtual machine back to the **exact** state it was when you took the snapshot. It is identical to moving back to a copy of the virtual machine backed up in the same state as the time the snapshot was taken. The only reason I can see to install a backup to a "new" virtual machine is if you wanted to keep a copy of the machine with, for example, certain software installed and then install a different set of software on another (identical) machine.
I guess I probably don't have a real good reason to want to make multiple copies since the snapshot will take me back to a good point. I was just thinking that it would be good to mess with one copy and keep one clean. The CD backup option seems closest to what I was thinking. I'll do that as well as the snapshot. If I mess up, I have the cd to fall back on.

Thanks for all the help.

---

### Post by j.bunce on 2006-12-07
Hi,
I followed the guide, installation completed without fault, however vmware typed in a terminal fails to work. No error message. Anyone else heard this?

Cheers,
jake

---

### Post by csk on 2006-12-08
this is a great guide!! thanks heaps

---

### Post by bvanaerde on 2006-12-08
I've used this guide, and I must say that everything works perfectly.

---

### Post by tajmox on 2006-12-08
Does anyone have a command or script to power on a virtual machine?

Right now it takes me 5 clicks to open the winxp machine and power it on.
5 Clicks is way too many for my poor fingers. :p 

Thanks!

---

### Post by yabbadabbadont on 2006-12-08
> **tajmox said:**
> Does anyone have a command or script to power on a virtual machine?

Right now it takes me 5 clicks to open the winxp machine and power it on.
5 Clicks is way too many for my poor fingers. :p 

Thanks!
If you start vmware from a terminal or the run dialog, I believe that you can supply the name of the .vmx file (include the path) for your desired VM as a parameter and it will be started automagically.

EDIT: found this by running "vmware --help"
```
Usage: /usr/lib/vmware/bin/vmware [OPTION ...] [--] [configuration file(s)]

where OPTIONS are:
       -v                Print program version
       -L                Display the list of registered stock IDs
       -x                Power on when a virtual machine is opened
       -X                Same as -x, also go to full screen mode
       -q                Close virtual machine at power off
       -s NAME=VALUE     Set variable NAME to VALUE
       -m                Automatically start in Quick Switch mode
 Remote connection:
       -l                Connect to the local host
       -h hostname       Host
       -P port           Port on host
       -u username       User name
       -w password       Password for remote connections


```

---

### Post by bigjoe4265 on 2006-12-08
> **tajmox said:**
> Does anyone have a command or script to power on a virtual machine?

Right now it takes me 5 clicks to open the winxp machine and power it on.
5 Clicks is way too many for my poor fingers. :p 

Thanks!

No need to do that, with your guest VM powered down there are power options in the guest VM configuration, set them so that your guest VM powers on automatically when your VMWare server service starts and when your host OS shuts down power down the guest VM gracefully.

Bigjoe

---

### Post by lime4x4 on 2006-12-09
everything is working good except i can't access any floppies.I can access the floppies in linux but not windows.I'm running edgy and using vmware to run xp pro.Everytime i'm in vmware xp and insert a floppy then go to my computer and double click the floppy drive i get an error about insert a floppy disk.

---

### Post by Kobussie on 2006-12-10
Hi!

Thanks for this excellent Howto: I installed W.98 inside Ubuntu without any problem! :D 
I wonder for how long VMware will give this software away for free??

---

### Post by VividHazE on 2006-12-13
I was a bit worried trying to set VMWare up but your instructions were so good I had to give it a try and it works! *scurrys off to remove windows partition with gparted. haha :)

---

### Post by David Valentine on 2006-12-14
I just have to add my thanks for this howto--this is seriously cool, and I look forward to this filling the gaps that wine can't (e.g., running zinio).  

I agree with the original poster that the virtual machine should go into the home folder--when I accepted the /var/lib/ default, the windows installer couldn't see my hard drive.

---

### Post by newpants2003 on 2006-12-15
thanx try it later.

---

### Post by blonder on 2006-12-15
I have some Problems with vmware,i hope someone can help me

> 
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: Fehler beim Bearbeiten von vmware-player (--configure):
 Unterprozess post-installation script gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)


uname -r say this: 2.6.17-10-generic

---

### Post by NZ-Wanderer on 2006-12-16
Well I upgraded to Edgy Kubuntu and suddenly my Vmware wouldn't work....

Reinstalled it, but it still didn't work when I tried to run it, so started reading this thread at page 1...

Got halfway into the 50's and found:

```
uninstall libdbus-1-2
```

Thank you very much, that worked perfectly, I uninstalled that file and now my VMware works great again..

My grateful thanks to everyone that has contributed to this massive thread... (and yes, I finished reading all 70 pages :-D  )

Maybe the Original poster might like to post a warning for Edgy users about this file stopping Vmware from working down in the first post under problems and solutions?

---

### Post by darrenm on 2006-12-16
> **blonder said:**
> I have some Problems with vmware,i hope someone can help me



uname -r say this: 2.6.17-10-generic

Just do what it says and you should be fine:

```
sudo /usr/bin/vmware-config.pl
```

---

### Post by m.musashi on 2006-12-17
Has anyone installed a non-unbuntu vm? I just installed sabayon in a virtual machine. It work fine but I cannot figure out how to intstall the vmware tools and without them it's rather jumpy and frustrating to use. Sudo doesn't work in sabayon the same way so I logged in as root and got it to run. The directions say to just accept the defaults but it kept asking the same question and the default was not accepted. I killed it and tried again and now it tells me there is a previous install of vmtools and aborts. It started the install but never finished.

Any thoughts?
Thanks.

---

### Post by a65bugman on 2006-12-18
For some reason VMWare will not load.  Yesterday I had installed and configures VMWare Server and successfully installed WinXP.  Everything was working fine since I updated the WinXP OS and even tried installing a few applications.  The issue came up today when I tried to start VMWare.  When typing vmware in the terminal it gives me the following error:

[B]vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.[/B]

That's fine and all but when I try to configure VMWare I get the following:

[B]Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.
[/B]

You'll notice that the Virtual Ethernet fails to stop and halts the configuration.  I have gone through this forum and have seen multiple posting for this issue.  Others have un-installed and re-installed but I still haven't seen anyone actually fix this issue.  Any takers?

---

### Post by a65bugman on 2006-12-18
Just an update...

It seems everytime I reboot the workstation I have to redo the install.  Any ideas on what is causing this?  This is an update to the post above.

---

### Post by sibrand on 2006-12-19
Please help me install vmware... I just get keeping those errors you see on the screenshot below. :( 

[[IMG]http://img521.imageshack.us/img521/2848/screenshotjc5.th.jpg[/IMG]](http://img521.imageshack.us/my.php?image=screenshotjc5.jpg)

---

### Post by bradsorensen on 2006-12-19
Does it matter if it vmware workstation or does it have to be server?
I have a purchased copy of workstation for unix and I was told it will work on linux.

---

### Post by arthursc on 2006-12-21
I have vmware server and xp vitual install on edgy,

My issue is that networking is not working at all. I have wireless laptop which works fine in edgy. But vmxp doesn't see any netowork even tho it's enabled.

also when I run vmware-config.pl i get 
colin@colin-laptop:~/vmware-server$ vmware-config.pl
bash: vmware-config.pl: command not found

even tho I can see the file.
colin@colin-laptop:~/vmware-server$ ls
vmnet-bridge   vmnet-sniffer  vmware-authtrusted  vmware-mount.pl
vmnet-dhcpd    vmrun          vmware-cmd          vmware-ping
vmnet-natd     vm-support     vmware-config.pl    vmware-uninstall.pl
vmnet-netifup  vmware         vmware-loop         vmware-vdiskmanager

any help would be great

thanks

---

### Post by schorsch on 2006-12-21
> **arthursc said:**
> 
also when I run vmware-config.pl i get 
colin@colin-laptop:~/vmware-server$ vmware-config.pl
bash: vmware-config.pl: command not found


try ```
./vmware-config.pl
``` in the same directory. If a command is not in your path the shell will not find it. With the preceding "./" you tell the shell to search for the command in your actual directory.

---

### Post by zetsumei on 2006-12-22
when i type the linux-headers..... it says cannot find package.

and vmware-config.pl asks for the dir of my C headers for my kernel, where arre they at?

---

### Post by iceman1234 on 2006-12-23
Many many many thx. Very good HOWTO.
cheers,

---

### Post by Obor on 2006-12-23
EDIT: Solved, just ran it again and it went through no problem.

When I run vmware-config.pl i get this error at the end.

```
Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

any clues as what the problem is? I'm running edgy with 2.6.17-10-generic kernel

---

### Post by sleepytom on 2006-12-24
When I try to start VMware the task bar adds a task that states "Starting VMware Server" which disappears after a few seconds, and the application never starts. For what it's worth, Sound Juicer CD Extractor does the same thing. Can you think of a way I can get this application going?

Thanks for your help.

---

### Post by lime4x4 on 2006-12-24
sleepytom

try running vmware from terminal so that u can see what error u are getting

applications->acc->terminal
then type vmware and hit return

---

### Post by mravljica on 2006-12-25
Hi!

I am trying to make vmware server run on my Edgy but no luck. I have done everything like it is told on page one. One thing I have noticed is one error during config - I have attached a complete screen dump of my config process.
Anyway, when I try to run vmware from the console it just hangs there - no errors displayed. 

Any idea how to solve this?

---

### Post by SurferJoe on 2006-12-25
VMWare works great.
Although I use Ubuntu for virtually all my needs , I still like the occasional small games eg from Popcap or Gamehouse , and these only run on Windows. Plus there are some really old games that run only on Win98 or earlier.
With VMware I have set up 2 virtual pcs - one for 98 the other for XP.
It is really impressive ( especially to my Windows using friends ) to see Ubuntu boot up and do my downloading etc and then I just can select XP to load and play a game etc while Linux is still doing its thing.
As for speed , apart from a bit of a slow down in file access across the "network" through shared folders , the programs all run at virtually usual speed , even with Linux running some tasks in the background.
It eliminates completely the need for multiple boot systems and is very quick to switch between O/S if needed at any time.
If I could find something almost the same as Visual Studio for C++ and Java development that I could install on Ubuntu , my life would be complete.

This O/S keeps getting better and better.

By the way , my PC setup for VMWare is :

Dual 2.8Ghz Xeon dual core CPUs
1GB Ram
2 of 300GB hdd
Quadro FX1000 video card - I used the Envy script to install the driver and this enables 3D gaming in Windows too.
Pioneer DVD Burner
Samsung DVD ROM

I figure I have a fair amount of grunt under the hood which probably makes everything run better with VMWare , but it is certainly usable and worth trying out.

---

### Post by beamo on 2006-12-26
For everyone having the problem where vmware server will not run after a reboot and starting vmware at the command line by typing "vmware" yeilds the following error message:

> vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

I found a solution here:

[http://www.debuntu.org/vmware-server-not-starting-after-reboot](http://www.debuntu.org/vmware-server-not-starting-after-reboot)

My vmware server works perfectly now.
Hope this helps ;)

---

### Post by mdbarton on 2006-12-27
I hadn't used VMWare server for some time, but now need to.  As usual, the kernel has been updated.  Got the latest headers, and do an ```
export CC=/usr/bin/gcc-3.4
```
Now when I run vmware-config.pl I get the following:
```
None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

[COLOR="Red"]**Using compiler "/usr/bin/gcc-3.4"**[/COLOR]. Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-27-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config7/vmmon-only'
make -C /lib/modules/2.6.15-27-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
/tmp/vmware-config7/vmmon-only/Makefile:89: *** Inappropriate build environment: [COLOR="Red"]you wanted to use gcc version 4.0.3 while kernel attempts to use gcc version 3.4.6.[/COLOR]
/tmp/vmware-config7/vmmon-only/Makefile:91: [COLOR="Red"]*** For proper build you'll have to replace gcc -m32 with symbolic link to /usr/bin/gcc-4.0.  Stop.[/COLOR]
make[1]: *** [_module_/tmp/vmware-config7/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config7/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Anyone know how to fix this?

---

### Post by MrMozza on 2006-12-27
I installed the vmware player package through Synaptic, then removed it again (not using a complete removal) - this seemed to cure the problems I got installing vmware. Not sure which dependency fixed it...

---

### Post by mdbarton on 2006-12-27
> **MrMozza said:**
> I installed the vmware player package through Synaptic, then removed it again (not using a complete removal) - this seemed to cure the problems I got installing vmware. Not sure which dependency fixed it...

I tried this and ended up having to re-install VMWare server.  Still had the same problem.  However I found that ```
vmware-config.pl -t
``` worked (try's to find modules that work).

---

### Post by Poison0985 on 2006-12-28
I have Ubuntu 6.10 installed, tried out this guide and followed the instructions as they were. I installed VMware Server without problems and then it ran the configuration script and everything went on fine until that point. It even told me "The configuration of VMware Server 1.0.1 build-29996 for Linux for this running kernel completed successfully."

Then I tried running it from the menus but got no response :-k , so I decided to run it from the terminal and it told me: "vmware is installed, but it has not been (correctly) configured for this system. To (re-)configure it, invoke the following command:/usr/bin/vmware-config.pl."

I invoked the command again and configure everything again but when trying to run VMware it still gives me the same message. :confused: 

I have tried multiple solutions I've read on the forum and in this thread but nothing has worked out. I even gave up for a while and tried VMware Player and it worked perfectly and managed to get Windows XP working but not as I wanted and with the features of Server.

Any help will be great. Thanks. :)

---

### Post by lime4x4 on 2006-12-28
how do u get vmware to see a regular dial up modem?? I have a modem install that works in dapper but when i try to add new hardware for a xp image i don't c the option to add the modem

---

### Post by _duncan_ on 2006-12-29
> how do u get vmware to see a regular dial up modem?? I have a modem install that works in dapper but when i try to add new hardware for a xp image i don't c the option to add the modem

It may be easier to just pass on dial-up connection using NAT networking from Ubuntu (host) to XP (guest).

With NAT networking enabled, vmware establishes some sort of LAN connection between the 2 OS. So what you do is dial-up in Ubuntu, fire-up the xp virtual machine with NAT enabled, and you will have internet connection in XP as well.

NAT networking is an option when you installed / configured vmware server. I think it followed the prompt about bridged networking.

---

### Post by cmichaelboyd on 2006-12-29
> **Poison0985 said:**
> I have Ubuntu 6.10 installed, tried out this guide and followed the instructions as they were. I installed VMware Server without problems and then it ran the configuration script and everything went on fine until that point. It even told me "The configuration of VMware Server 1.0.1 build-29996 for Linux for this running kernel completed successfully."

Then I tried running it from the menus but got no response :-k , so I decided to run it from the terminal and it told me: "vmware is installed, but it has not been (correctly) configured for this system. To (re-)configure it, invoke the following command:/usr/bin/vmware-config.pl."

I invoked the command again and configure everything again but when trying to run VMware it still gives me the same message. :confused: 

I have tried multiple solutions I've read on the forum and in this thread but nothing has worked out. I even gave up for a while and tried VMware Player and it worked perfectly and managed to get Windows XP working but not as I wanted and with the features of Server.

Any help will be great. Thanks. :)



I had the exact same problem, and I don't know if it's a real configuration problem or not, but if you go to the /etc/vmware directory and delete the "not_configured" file, and then try running it again, it starts with no complaints.

Good Luck,

Chris

---

### Post by chaplanger on 2006-12-29
In a terminal type
Code:

sudo apt-get install linux-headers-`uname -r` build-essential xinetd



As a newbie: what is meant by 'uname-r' (is this for the user's account name or is this to be typed exactly "as is"?

---

### Post by chaplanger on 2006-12-29
The VMware serve console will not show up.

When I open terminal and type in vmware, this is what I receive:
david@david-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

After doing the above I receive this:
david@david-desktop:~$ /usr/bin/vmware-config.pl.
bash: /usr/bin/vmware-config.pl.: No such file or directory
david@david-desktop:~$

I am a newbie and have no idea how to proceed (I did accept the defaults as the program was being set up)

---

### Post by Blixter on 2006-12-29
Most of you already know this but i want to write this anyway!

Those who want your USB (2.0) printer work with vmware. Download vmware 6 Beta :D Both my Canon pixma 5200 and Webcam working fine!

---

### Post by chaplanger on 2006-12-29
I saw from above:

I had the exact same problem, and I don't know if it's a real configuration problem or not, but if you go to the /etc/vmware directory and delete the "not_configured" file, and then try running it again, it starts with no complaints.


However when I go into the /etc/vmware directory (via Places>computer) I am not allowed to delete this file because I don't have permissions to change it or its parent folder.

Help!
](*,)

---

### Post by thenetduck on 2006-12-29
I keep running into this problem every time I try to install VMWare Server and don't know how to fix it. I get this.

```


Installing the VMware VmPerl Scripting API.

Unable to install the VMware VmPerl Scripting API.

********
The VMware VmPerl Scripting API was not installed.  Errors encountered during 
compilation and installation of the module can be found here: 
/tmp/vmware-config1

You will not be able to use the "vmware-cmd" program.

Errors can be found in the log file: 
'/tmp/vmware-config1/control-only/make.log'
********


```


How can I fix this? It won't install windows for some reason either. Thanks,
 The Net duck

---

### Post by MrMozza on 2006-12-30
I found that after installing vmware-player to get vmware server to install OK, server would not work after rebooting (despite uninstalling vmware-player). Seems some files were left behind from vmware-player, so...

sudo update-rc.d -f vmware-player remove

This removed some more files to do with vmware-player (networking on start-up) - which seemed to be interfering

---

### Post by ffi on 2006-12-30
Is there a way to run my current xp install in vmware?

---

### Post by Solver on 2006-12-30
Yes, but it's fairly complicated and you can screw your partitions up if you do something wrong. Might not work on some hardware setups, too.

If you feel like giving it a try, follow this tutorial:

[http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition)

---

### Post by ffi on 2006-12-30
Thanks:-D

---

### Post by s_h_a_d_o_w_s on 2006-12-30
dugster@dugster-desktop:~/vmware-server-distrib$ sudo ./vmware-install.pl
Password:
A previous installation of VMware software has been detected.

Failure

Execution aborted.

dugster@dugster-desktop:~/vmware-server-distrib$

[SIZE=6][B]
I tried vmware player but it's uninstalled, why is this happening?[/B][/SIZE]

---

### Post by cmichaelboyd on 2007-01-01
okay, so I've gotten everything configured and installed properly now, and it starts with no errors, but when I open the vmware console, the option to create a new virtual machine is greyed out.  Anyone know why this is happening and what I can do to fix it?

Thanks,

Chris

---

### Post by NZ-Wanderer on 2007-01-01
If you look up a few messages or go back a few pages, you will see the answer...

Basically, when you uninstall vmware player etc it does NOT uninstall everything.. - you have to go in and finish removing the junk that's left...

I'm no expert in these things, so don't know the commands myself, but I do remember seeing this question answered a lot in this thread, so finding the commands shouldn't be too hard :) :) 

> **s_h_a_d_o_w_s said:**
> dugster@dugster-desktop:~/vmware-server-distrib$ sudo ./vmware-install.pl
Password:
A previous installation of VMware software has been detected.
Failure
Execution aborted.
dugster@dugster-desktop:~/vmware-server-distrib$

I tried vmware player but it's uninstalled, why is this happening?[/B][/SIZE]

---

### Post by likerice on 2007-01-02
a big thanks to Peturrr for posting this fantastic HowTo.

i'm new to (x)ubuntu and was able to install vmware server with minimal hassle thanks to the clarity of your instructions. 

your tutorial can now officially be said to be "idiot proof". ;) 

thanks!

---

### Post by chaplanger on 2007-01-04
I have set up a virtual machine for WIN 2000.  However I cannot install the operating system.

The CD drive will not boot up for WIN 2000 for installation.  I have looked at the help article "Configuring a CD-ROM" and even with the suggested changes (changing CD-ROM from local to client), nothing occurs.  

This is the error message I receive:
-----------------------
No bootable CD, floppy or hard disk was detected.
To install an operating system, insert a bootable CD or floppy and restart the virtual machine by clicking the Reset button.
-----------------------

I am uploading a screen shot so you can see what I see directly.  (Being a noobie in Linux it saved the screenshot as .php -- I have no clue how this compresses the file -- so if the pic is too large, let me know & I won't do this again)

---

### Post by insane_alien on 2007-01-06
this is a great tutorial and probably does work for most people.

i got it installed no bother but it won't start. if i type 'vmware' into the console the only thing that happens is my processor usage jumps up to 100% and the temperature follows. i don't even get error codes in the terminal. i left this running for about 30 minutes still with nothing then i closed it since i waqs worried about the temperature on my processor (70*C)

EDIT: got it solved in IRC

LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware <-command to run if you have the same problem

---

### Post by Xera on 2007-01-06
Hoi, i'm trying to get my speedtouch 330 working in TinyXP, i've tried it on nas0 and eth0, but i just get this:
[http://img175.imageshack.us/img175/5642/s1ep2.png](http://img175.imageshack.us/img175/5642/s1ep2.png)
oh and btw, i used [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) to install the modem. any suggestions? ](*,)  :confused: 

Xera

---

### Post by raddik on 2007-01-07
> **MrMozza said:**
> I found that after installing vmware-player to get vmware server to install OK, server would not work after rebooting (despite uninstalling vmware-player). Seems some files were left behind from vmware-player, so...

sudo update-rc.d -f vmware-player remove

This removed some more files to do with vmware-player (networking on start-up) - which seemed to be interfering

Thanks for this tip! It has finally helped me after several days of searching for the right solution. I had previously installed and uninstalled vmware-player through Automatix. To get vmware-serverd and other services loading after reboot I also had to uninstall three other files left behind from vmware-player through synaptic and then run the vmware-config.pl again.

---

### Post by olieviya on 2007-01-08
Is there a guide as to how you may run an already existing "normal" installation of windows from within VMWare Server???

---

### Post by cesera on 2007-01-08
> **olieviya said:**
> Is there a guide as to how you may run an already existing "normal" installation of windows from within VMWare Server???
 
*[http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition)*

---

### Post by Peturrr on 2007-01-11
> **chaplanger said:**
> I have set up a virtual machine for WIN 2000.  However I cannot install the operating system.

The CD drive will not boot up for WIN 2000 for installation.  I have looked at the help article "Configuring a CD-ROM" and even with the suggested changes (changing CD-ROM from local to client), nothing occurs.  

This is the error message I receive:
-----------------------
No bootable CD, floppy or hard disk was detected.
To install an operating system, insert a bootable CD or floppy and restart the virtual machine by clicking the Reset button.
-----------------------

I am uploading a screen shot so you can see what I see directly.  (Being a noobie in Linux it saved the screenshot as .php -- I have no clue how this compresses the file -- so if the pic is too large, let me know & I won't do this again)
Click Power-Off. Then go to Summary and edit the properties of the virtual cd drive until it works. :)

---

### Post by elsebasbe on 2007-01-11
Thanks, works flawless.

---

### Post by Contrid on 2007-01-12
I can't boot into my existing Windows installation.
I'm not even sure how to do it. :(
Can someone tell me how?

---

### Post by Contrid on 2007-01-12
I managed to get it to work up until the Grub loader.
It gives me an [B]error 21

[/B]Both XP and grub is on the same partition/hard-drive.
Ubuntu is on another partition.
What should I do?

---

### Post by m.musashi on 2007-01-12
> **Contrid said:**
> I managed to get it to work up until the Grub loader.
It gives me an [B]error 21

[/B]Both XP and grub is on the same partition/hard-drive.
Ubuntu is on another partition.
What should I do?

Unless you have been trying to get vmware to boot your original xp install you would probably have better luck posting a new thread. It sounds more like a grub issue and it's unlikely anyone will find your request here.

---

### Post by unknownguy on 2007-01-12
When installing VMWare, I get an error message in Terminal. When it asks me where to install the documentation files, and I press enter for the default, I get this message: 
> Unable to get the access rights of source file "./vmware-vix/bin".
Execution aborted
How do I fix this problem?

---

### Post by m.musashi on 2007-01-12
Did you use sudo?
```
sudo ./vmware-install.pl
```
If you didn't that is probably the reason. If you did, then I'm afraid I don't know. It sounds like a permission issue though.

One more though. Is anything else trying to install at the same time?

---

### Post by unknownguy on 2007-01-12
> **m.musashi said:**
> Did you use sudo?
```
sudo ./vmware-install.pl
```
If you didn't that is probably the reason. If you did, then I'm afraid I don't know. It sounds like a permission issue though.

One more though. Is anything else trying to install at the same time?

I don't think so.  I've tried multiple times to install it, and the exact same error occurs.

---

### Post by Contrid on 2007-01-13
Hi there,

Everytime I reboot, Vmware stops working.
It gives me the following error :

```

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

Then...when I run that command stated above in the error, I get the following :

```

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

```

...and then I can't do anything.
What should I do to prevent this?

Thanks for any help available.

---

### Post by petersjm on 2007-01-13
I just installed VMWare server on Edgy but when I try to run it nothing happens. When starting it from the terminal, I get the following error. Does it mean anything to anyone? Is there a way round it? Thanks in advance :D 

```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
```

---

### Post by rhino_harley on 2007-01-13
petersjm did you ever work this out. i get the same error, and when i start my cpu always go to 100% and i never get the console. if i do an strace on the process it doesn't return anything at all.

---

### Post by petersjm on 2007-01-14
> **rhino_harley said:**
> petersjm did you ever work this out. i get the same error, and when i start my cpu always go to 100% and i never get the console. if i do an strace on the process it doesn't return anything at all.

Afraid not, rhino. I've had a look at both files the error mentions, but can't figure out how to "read" them, as gedit and nano can't do so. It seems the first file is missing a version number (?) that is required by the second file. But how to give it a version number is beyond me... Hopefully someone else can figure it out.

---

### Post by Deacon_X on 2007-01-14
I finally got throught the installation poroblem, but now when i try to start the vmware console to install windows i keep getting this error message  "Could not launch menu item

Details: Failed to execute child process "vmware" (No such file or directory)"  I don't know what went wrong.

---

### Post by rhino_harley on 2007-01-14
I finally worked out how to get the console started. I just run vmware like this:

LD_PRELOAD=/usr/lib/libdbus-1.so.3: vmware

Didn't help me much though as my windows partition won't boot due to some other problem now.

---

### Post by Bealer on 2007-01-16
Great How-To. Got mine all up and working.

One thing though. I can only see the set drives for the virtual machine (ie C:\ and the DVD-ROM). Is there any way of showing all my other drives (that are available to Ubuntu). 

These are actually all EXT3 drives/partitions, but I was hoping to use EXT2IFS within my virtual installation to see them. At current though I can't see anything apart from the C:\ in my Windows virtual machine.

-----

Edit, think I found what I'm looking for. Looks like I have to share the drives I want to see via Samba and map them in my Windows installation.

---

### Post by rhino_harley on 2007-01-16
Working at last. I hava a SATA drive, but for some reason windows sees it as an IDE drive, whereas linux sees it is a SATA drive. To fix this I had to manually edit my .vmdk file to:

ddb.adapterType = "ide"

and my .vmx file to sche all instances of scsi0 to ide0. Voila, windows is running. Only problem I have now is that I can't fullscreen windows at my full resolution (1920x1440), but I can live with that.

---

### Post by Alceal on 2007-01-17
I've got this problem:

> Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: se ingresa al directorio `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-10-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.17-10-386'
cp -f vmnet.ko ./../vmnet.o
make: se sale del directorio `/tmp/vmware-config0/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


---

### Post by icehammer on 2007-01-17
I did everything as shown in the guide above.. windows installed, and sound and all is working fine.. but i can't see my other drives!!! how am i supposed to install my software?? it only shows C:, D: [cd] ... what did i do wrong?? what to do now?

---

### Post by icehammer on 2007-01-17
i did ```
sudo -i
``` to make myself a root, then added a physical drive to the virtual drive.. it added, but when i power on (even as root), it says i don't have permissions.. why??

---

### Post by Thinh on 2007-01-18
Everyting seems to be working but the only thing is it runs really slow, it has been taking over 1 hours to install windows is this right and what is the good size for memory. I increased it to the maximum recommend and it seems to run slower now than the 256 which it was defaulted too.

i choose ntfs when i format the format does that have anything to do why it i so slow for me?
does this image act as a folder so if i want something to show up in windows just go in the folder and add a new folder?

---

### Post by techstop on 2007-01-18
> **Thinh said:**
> Everyting seems to be working but the only thing is it runs really slow, it has been taking over 1 hours to install windows is this right and what is the good size for memory. I increased it to the maximum recommend and it seems to run slower now than the 256 which it was defaulted too.

i choose ntfs when i format the format does that have anything to do why it i so slow for me?
does this image act as a folder so if i want something to show up in windows just go in the folder and add a new folder?

How much memory does your host OS have? You need to have enough to run both your host (Linux) and the guest (Windows). I have 1GB RAM and I've allocated 512MB to Windows guest OS. It's still a little sluggish. If you have anything less than 1GB I'd imagine that it would be very slow indeed. If you have allocated more than 512MB and you have 1GB of Linux memory, then there would be a lot of hard drive thrashing as virtual memory gets used. Is your hard drive activity light constantly on?

---

### Post by gvoima on 2007-01-19
Well I've got some problems too with it being slow, but if you're using a laptop or have frequency scaling there is slowdowns with that. It's a known problem and you should disable it.
But even that didn't help with me, on my home computer it runs beautifully, I have 1280megs of memory and allocate 512 to the VM. The same that I have on my home machine.

---

### Post by Thinh on 2007-01-19
I have 2g of ddr2 on my laptop I have a Dell precision M70. Windows seems to work fine but the maximazing and minimazing is very sluggish for some reason. Which is a better approach use the 2g divided partion or use the whole predetermine hd set. Also is there any performance gain if you can work it with sata instead of ata. I have sata on my machine but when i try to install it under sata windows doest recognize it even thought it does recognize it on a stand alone installation of windows. to be honest the only software my work required to use windows is ms access other than that i would have trash windows long time ago
i am trying to get away from dual booting.

---

### Post by depele on 2007-01-19
when I :
```
depele@Kubuntu:~$ vmware
```
I get 
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

I have been looking around but didn't find a lot 

thanks.

---

### Post by Enverex on 2007-01-19
Just incase anyone is still following this I have to recommend VirtualBox above VMWare, the performance is much better (really was supprised, I was expecting VB to be a bit slower).

---

### Post by Hanzerik on 2007-01-19
Don't know if it has been mentioned yet, but you can just use VMWare Player and qemu to install Windows on the same machine, without having to install and configure the VMWare Server package.

---

### Post by Doug11 on 2007-01-20
I keep getting this error when I try to do the config after a kernel upgrade,,


Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.19.1/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config9/vmmon-only'
make -C /lib/modules/2.6.19.1/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.19'
  CC [M]  /tmp/vmware-config9/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config9/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config9/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config9/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config9/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config9/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config9/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config9/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config9/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config9/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config9/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config9/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-2.6.19'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config9/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config9/vmnet-only'
make -C /lib/modules/2.6.19.1/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.19'
  CC [M]  /tmp/vmware-config9/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config9/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config9/vmnet-only/userif.o
/tmp/vmware-config9/vmnet-only/userif.c: In function ‘VNetCopyDatagramToUser’:
/tmp/vmware-config9/vmnet-only/userif.c:629: error: ‘CHECKSUM_HW’ undeclared (first use in this function)
/tmp/vmware-config9/vmnet-only/userif.c:629: error: (Each undeclared identifier is reported only once
/tmp/vmware-config9/vmnet-only/userif.c:629: error: for each function it appears in.)
make[2]: *** [/tmp/vmware-config9/vmnet-only/userif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config9/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config9/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.



Anyone know how I can get past this?

---

### Post by Doug11 on 2007-01-20
> **slider said:**
> Tokes-

Not sure why it would ignore CC. Only other suggestion is to link /usr/bin/gcc to /usr/bin/gcc-4.0

ln -s /usr/bin/gcc-4.0 /usr/bin/gcc

Make sure to remember where gcc points to first so you can reset it afterward

ls -als /usr/bin/gcc*


I found this reply to someone that was having a smiliar prob,,,I dont understand how to link these in the way they are talking about though. Can someone shed a little light/

---

### Post by YaseenKriel on 2007-01-21
[http://searchopensource.techtarget.com/tip/0,289483,sid39_gci1238129,00.html](http://searchopensource.techtarget.com/tip/0,289483,sid39_gci1238129,00.html)

found this interesting article on how to publish windows apps in linux. got most of the software install but when i use the command to publish I get the windows desktop and not the app.

---

### Post by Doug11 on 2007-01-21
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc-4.1". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.19.1/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config5/vmmon-only'
make -C /lib/modules/2.6.19.1/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.19'
  CC [M]  /tmp/vmware-config5/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config5/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config5/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config5/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config5/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config5/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-2.6.19'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config5/vmmon-only'
The module loads perfectly in the running kernel.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config5/vmnet-only'
make -C /lib/modules/2.6.19.1/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.19'
  CC [M]  /tmp/vmware-config5/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config5/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config5/vmnet-only/userif.o
/tmp/vmware-config5/vmnet-only/userif.c: In function ‘VNetCopyDatagramToUser’:
/tmp/vmware-config5/vmnet-only/userif.c:629: error: ‘CHECKSUM_HW’ undeclared (first use in this function)
/tmp/vmware-config5/vmnet-only/userif.c:629: error: (Each undeclared identifier is reported only once
/tmp/vmware-config5/vmnet-only/userif.c:629: error: for each function it appears in.)
make[2]: *** [/tmp/vmware-config5/vmnet-only/userif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config5/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config5/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.




OK,,alot of people say to use gcc-4,,,and this problem would be solved. Well, as you can see in the very first line that it is using gcc 4.1,,which is the one that compiled the kernel, and it's still giving me the same error. Even if I try to install vmware-player. Its the smae thing. I'm at a loss of what else to try. Any suggestions?

---

### Post by PartisanEntity on 2007-01-23
I just tried following the instructions to install vmware, however I had tried installing it through automatix2 some time ago (which didnt work) and now when I try to launch the install script

```
sudo ./vmware-install.pl
```

I get this error:
```

A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.
```

What files and folders do I need to delete to remove any instances of the previous installation attempt through automatix2?

Thanks in advance!

p.s. I did read through the forum that one should remove (uninstall) any old installation, I did deinstall the older vmware installation through automatix2 at the time, but it seems that certain parts of that installation still reside somewhere in the filesystem?

---

### Post by Bossieman on 2007-01-23
I get this error message as so many before me in this thread.

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

Suggestions to solve this? CPU goes up to 100% and nothing more happens.

---

### Post by yabbadabbadont on 2007-01-23
> **PartisanEntity said:**
> I just tried following the instructions to install vmware, however I had tried installing it through automatix2 some time ago (which didnt work) and now when I try to launch the install script

```
sudo ./vmware-install.pl
```

I get this error:
```

A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.
```

What files and folders do I need to delete to remove any instances of the previous installation attempt through automatix2?

Thanks in advance!

p.s. I did read through the forum that one should remove (uninstall) any old installation, I did deinstall the older vmware installation through automatix2 at the time, but it seems that certain parts of that installation still reside somewhere in the filesystem?

You probably need to remove the /etc/vmware directory.  It usually gets left behind for some reason.

---

### Post by DX 00 on 2007-01-23
Thanks for the great How-To BTW!

I got the VMWare server installed in Ubuntu 6.10 and the first time I run it it worked great. I was able to install WinXP with no problem. I then installed VMware Player through Automatix2 and it worked flawlessly. Then I restarted my machine :(.

After I restarted, the server wouldn't start anymore. When I run (all under root) vmware this is what I get.

```
root@APANB102:/tmp/vmware-server-distrib# vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

Then when I run vmware-config.pl I get:

```
root@APANB102:/tmp/vmware-server-distrib# vmware-config.pl 
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

```

I've tried killing the process but it will still be there:
```
root@APANB102:/tmp/vmware-server-distrib# ps
  PID TTY          TIME CMD
13203 pts/0    00:00:00 su
13204 pts/0    00:00:00 bash
13868 pts/0    00:00:01 vmware-serverd
14838 pts/0    00:00:00 du
16676 pts/0    00:00:00 ps
root@APANB102:/tmp/vmware-server-distrib# kill 13868
root@APANB102:/tmp/vmware-server-distrib# kill 13868
root@APANB102:/tmp/vmware-server-distrib# kill 13868
root@APANB102:/tmp/vmware-server-distrib# ps
  PID TTY          TIME CMD
13203 pts/0    00:00:00 su
13204 pts/0    00:00:00 bash
13868 pts/0    00:00:01 vmware-serverd
14838 pts/0    00:00:00 du
16686 pts/0    00:00:00 ps

```

I even tried stopping the service like this:
```
root@APANB102:/tmp/vmware-server-distrib# /etc/init.d/vmware stop
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
```

I've also tried running **vmware-uninstall.pl** and then reinstalling the server but I still get the same error. Anybody have an idea of how I can fix this or stop the server?

Thanks in advanced.

---

### Post by DX 00 on 2007-01-23
> **Contrid said:**
> Hi there,

Everytime I reboot, Vmware stops working.
It gives me the following error :

```

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

Then...when I run that command stated above in the error, I get the following :

```

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

```

...and then I can't do anything.
What should I do to prevent this?

Thanks for any help available.

Dude, if you find a solution let me know. I think this has to do with the VMware Playere installation. I read a hint in here.
[http://www.debuntu.org/vmware-server-not-starting-after-reboot]("http://www.debuntu.org/vmware-server-not-starting-after-reboot")

---

### Post by PartisanEntity on 2007-01-23
> **yabbadabbadont said:**
> You probably need to remove the /etc/vmware directory.  It usually gets left behind for some reason.

That was it! Thanks!

---

### Post by DX 00 on 2007-01-23
OK, I found the answer to the problem. The problem is the VMware-Player, I had to completely remove it and I had a hell of a time but here is what I did:
```
$apt-get autoremove vmware-player*
```
As soon as that finished, I uninstalled the VMware Server and reinstalled it and it worked again. Hopefully that will help someone!

> **DX 00 said:**
> Dude, if you find a solution let me know. I think this has to do with the VMware Playere installation. I read a hint in here.
[http://www.debuntu.org/vmware-server-not-starting-after-reboot]("http://www.debuntu.org/vmware-server-not-starting-after-reboot")

---

### Post by Doug11 on 2007-01-23
OK,,,after a week of probing and reading,,I finally found the answer. For all those who have compiled  to a 2.6.19 kernal and can't get vmware server back up and running, check out this thread,,,worked for me in 5 minutes

[http://www.ubuntuforums.org/showthread.php?t=334394](http://www.ubuntuforums.org/showthread.php?t=334394)

---

### Post by maqen on 2007-01-24
Is it possible do the prescripted vmware server install whitout x on my edgy server?

---

### Post by frogotronic on 2007-01-25
Just installed XP on VMWare server!  Thanks for the great HOWTO!

**Silly Question:**  Do I have to install McAfee AV on my XP/VMWare to avoid viruses and such (as if I was using a regular non-VMWare XP box)?

- CH

---

### Post by Contrid on 2007-01-25
> **cement_head said:**
> Just installed XP on VMWare server!  Thanks for the great HOWTO!

**Silly Question:**  Do I have to install McAfee AV on my XP/VMWare to avoid viruses and such (as if I was using a regular non-VMWare XP box)?

- CH

Hey...great question. I was wondering the same thing, but I was assuming that since it's running on top of Linux, using NAT provided by your Linux box for Internet connection, you should be safe. Not sure though...let's hear what people have to say.

---

### Post by yabbadabbadont on 2007-01-25
> **Contrid said:**
> Hey...great question. I was wondering the same thing, but I was assuming that since it's running on top of Linux, using NAT provided by your Linux box for Internet connection, you should be safe. Not sure though...let's hear what people have to say.

From what I've read when this topic has come up in the past, your windows vm can (and probably will) get infected.  Your host linux box would probably be safe, but every time the vm was run, the malware would be running too.  I think one of the proposed solutions, other than running AV software in the vm, was to setup the vm with snapshots.  You don't initially enable the networking when you install windows.  Then once everything is installed correctly, you enable host only networking.  This is so that windows will configure its networking settings correctly.  You then create a snapshot of this clean vm.  Then change the vmware settings so that the vm is rolled back to the snapshot every time you exit.  After that, you can enable NAT networking and access the internet as you like.  Anything that is done to the vm will be erased when the snapshot is restored on exit.  Of course this means that you can't save any new data or install any new programs or anything...

---

### Post by frogotronic on 2007-01-25
Crap!  That what I feared.

Well, that won't do at all.  I'm using VMware as a Windows solution on a production machine.  I've just installed McAfee VirusScan 8.0i (Enterprise Edition) in the vXP O/S and it seems to run fine.  I'll also put Windows Defender on for malware (not the best - but seems to catch most stuff).  I'm using the vXP O/S for only a few programmes (not really web based) that absolutely won't install with CrossOver Office 6.0.  And, because I have CXO installed - Windows binaries (*.exe) files will execute.

So, I feel safer with the virus scan - even though all the major problems are platform (MS) based.

- CH

---

### Post by _duncan_ on 2007-01-26
I never used CrossOver Office so I'm not sure about this. But if because of CrossOver your linux machine will now recognize .exe files, shouldn't you also install an antivirus on linux?

My understanding is that linux is relatively safe from .exe-based viruses because .exe don't run in linux. In this case however...

---

### Post by frogotronic on 2007-01-26
Hi,.

You're correct.  But, Linux network security is far better than the "open door" MS O/S's, so the chance of a virus targeting a Linux box is almost nill (this from our work IT guys).  It could happen, but unlikely.  I do have ClamAV installed on Ubuntu and I do use Firestarter as a firewall GUI.

Plus CXO ALWAYS asks before it executes a Windows Binary - something that *de facto* provides a layer of protection against self-executing files.  This "ask" policy might be inherent to Linux...

- CH

---

### Post by CameronCalver on 2007-01-26
Hey i did the how to but i get
```
cameron@ubuntu:/usr/bin$ cd /tmp
cameron@ubuntu:/tmp$ cd vmware-server-distrib
cameron@ubuntu:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

cameron@ubuntu:/tmp/vmware-server-distrib$ 

```


edic: fixed that problem by deleting /etc/vmware but now im getting 

```
 
cameron@ubuntu:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to alloc client: File "/etc/vmware/config" line 10: Syntax error.



VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: File "/etc/vmware/config" line 10: Syntax error.

A log file is available in "/tmp/vmware-cameron/ui-10123.log".  Please request support and include the contents of the log file.  
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.

```

---

### Post by hsalgado on 2007-01-28
Really nice guide.  I am dual booting and I would like to run in ubuntu what I need of windows... so I tried your guide... but...

when I try to run vmware I get the following message:

[I]vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.[/I]

When I do that it tell me:
[I]
Please re-run this program as the super user.[/I]

I don't have any idea what that means...

Thanks for any help!!!!!!!

---

### Post by kioftes on 2007-01-28
Hi guys!I use Edgy 64 and i recently updated to kernel 2.6.19.2. When i try to install vmware i get the following error


Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmnet-only'
make -C /usr/src/linux-headers-2.6.19.2/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.19.2'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
/tmp/vmware-config1/vmnet-only/userif.c: In function &#8216;VNetCopyDatagramToUser&#8217;:
/tmp/vmware-config1/vmnet-only/userif.c:629: error: &#8216;CHECKSUM_HW&#8217; undeclared (first use in this function)
/tmp/vmware-config1/vmnet-only/userif.c:629: error: (Each undeclared identifier is reported only once
/tmp/vmware-config1/vmnet-only/userif.c:629: error: for each function it appears in.)
make[2]: *** [/tmp/vmware-config1/vmnet-only/userif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.19.2'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


Any help would be much appreciated!!!

---

### Post by kioftes on 2007-01-28
I found the solution

[http://www.vmware.com/community/thread.jspa?threadID=69765&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=69765&tstart=0)

just change the name of the folder to match your kernel includes eg /usr/src/kernels/2.6.18-1.2849.fc6-i686/include/linux/config.h  to
/usr/src/linux-headers-`uname -r`/include/linux/config.h 

however, it seems now that i can't mount the cdrom....

root@Soula:~# mount -t iso9660 /dev/hdc  /media/cdrom0
mount: special device /dev/hdc does not exist

---

### Post by yabbadabbadont on 2007-01-28
> **hsalgado said:**
> Really nice guide.  I am dual booting and I would like to run in ubuntu what I need of windows... so I tried your guide... but...

when I try to run vmware I get the following message:

[I]vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.[/I]

When I do that it tell me:
[I]
Please re-run this program as the super user.[/I]

I don't have any idea what that means...

Thanks for any help!!!!!!!

It means you need to run the command using sudo.

sudo /usr/bin/vmware-config.pl

---

### Post by sudha48 on 2007-01-30
Hi
 i tried installing vmware
iam getting error message
"Unable to get the access rights of source file "./vmware-vix/bin. execution aborted "
when i did sudo ./vmware-install.pl

please help me.!!

---

### Post by nicklogan on 2007-01-30
Thanks for this HowTo - I've wanted to try VMWare for years. I got it working but am having one problem - when I suspend or quit  VMWare my Ubuntu desktop hangs and can't be accessed until I ctrl-alt-backspace to restart it.  I can use ctrl-alt-F1, etc. to go to another login screen or ctrl-alt-F7 to get back to the hung grey screen but can't get to the desktop.  Ctrl-alt-tab to get to another desktop window doesn't work. Please help - I'd love to be able to get in and out of AutoCad  without losing my desktop.
Apologies if this has already been covered, I searched this thread but couldn't read the whole thing.

---

### Post by sn0m on 2007-01-30
thanks for the guide, a great one.
I have installed it and created virtual machines named windows virtual machine 2000 and windows virtual machine 200 2 which are installed in /
The problem is that when i i tried to install win xp, i get the message that theres no hard disk in your system.

I have restarted it and now i got the message:
The master boot record (MBR) of this virtual machine's hard disk does not contain valid bootstrap code. It is likely that the MBR was corrupted by an incorrect guest operating system installation or some other reason.  The virtual machine cannot continue and will now power off. (For advanced users: the MBR is the last disk sector accessed by the virtual machine before the error.) Please consult our Web site at "http://www.vmware.com/info?id=18" for common troubleshooting help.

I also tried to delete the win virtual machines from / but got this message.

root@sn0m-laptop:/home/sn0m# cd /
root@sn0m-laptop:/# ls
bin    etc         lib         opt   srv  var
boot   home        lost+found  proc  sys  vmlinuz
cdrom  initrd      media       root  tmp  Windows 2000 Professional
dev    initrd.img  mnt         sbin  usr  Windows 2000 Professional 2
root@sn0m-laptop:/# rm Windows 2000 Professional
rm: cannot remove `Windows': No such file or directory
rm: cannot remove `2000': No such file or directory
rm: cannot remove `Professional': No such file or directory
root@sn0m-laptop:/# 

any help
thanks
Koli

---

### Post by positron on 2007-01-31
I installed vmware server on ubuntu edgy.  However, there is no command in my bin named "vmware."  I run vmware-server-console instead and it asks me to connect to host.  From what I understand I need to connect to localhost or ubuntu with the root password, but no matter what I type in it says "Unable to connect to the remote host"

What do I need to do/install?  I don't see how I could have gotten the wrong file, I downloaded the file from [http://www.vmware.com/download/server/]("http://www.vmware.com/download/server/") but I seem to be missing the vmware-server-distrib directory and ./vmware-install.pl script inside it.  I ran every install and config script I could find and it never asked me for my serial number.

Thanks.

EDIT: I downloaded this tar instead and it has the correct files. [http://download3.vmware.com/software/vmserver/VMware-server-1.0.1-29996.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.1-29996.tar.gz)

---

### Post by euthyfro on 2007-02-02
i got 2 the sudo ./vmware-install.pl step, & i got A previous installation of VMware software has been detected.

Failure

Execution aborted.

i thought it might have been cuz i had the vmwareplayer package installed so i removed it, got the same error, removed every vmware folder i could find tryed again & got the same thing.  is there some thing i've missed about vmware?

---

### Post by euthyfro on 2007-02-02
duh, the answer 2 that is posted everywhere, so i got past that got 2 the where u want doc. files part, got the "Unable to get the access rights of source file "./vmware-vix/bin" message, created the symbolic link that has been put forward as a fix 2 this & then got the same message.  i'm at my wit's end.:frown:

---

### Post by KeithO on 2007-02-03
i'm having the same error message as well.  i have a fresh edgy install.

---

### Post by schorsch on 2007-02-03
> **euthyfro said:**
> i got 2 the sudo ./vmware-install.pl step, & i got A previous installation of VMware software has been detected.

Failure

Execution aborted.

i thought it might have been cuz i had the vmwareplayer package installed so i removed it, got the same error, removed every vmware folder i could find tryed again & got the same thing.  is there some thing i've missed about vmware?

rm -rf /etc/vmware

---

### Post by MockY on 2007-02-03
I lost the ability to surf the internet after I installed VWserver. Everything else works fine. I installed Windows XP without issues. But the Internet problem remained. I could connect to the LAN easily but somehow the WAN part didn't work. I uninstalled and rebooted and I can now surf again. What did I wrong? I want VMware installed.

---

### Post by kegsy1 on 2007-02-03
Hi

After completing the install and then clicking on the VMWare Server Console icon under System Tools the console tries to load momentarily but nothing happens. I then opened a terminal session and typed...

vmware 

...as suggested in the instructions. The following paste came from the terminal session and I hope you might be able to help me to get this virtual machine working on my PC.

Regards
Kegsy

=========================================================

root@family:~# vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

root@family:~# /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
/usr/share/applications/vmware-console-uri-handler.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.17-10-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [no] 

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Would you prefer to modify your existing networking configuration using the 
wizard or the editor? (wizard/editor/help) [wizard] 

The following bridged networks have been defined:

. vmnet0 is bridged to ra0

Do you wish to configure another bridged network? (yes/no) [no] 

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

The NAT network is currently configured to use the private subnet 
172.16.120.0/255.255.255.0.  Do you want to keep these settings? [yes] 

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 172.16.120.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

The host-only network is currently configured to use the private subnet 
192.168.62.0/255.255.255.0.  Do you want to keep these settings? [yes] 

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.62.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

Do you want to enter a serial number now? (yes/no/help) [no] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed

The configuration of VMware Server 1.0.1 build-29996 for Linux for this running
kernel completed successfully.

root@family:~#

---

### Post by KeithO on 2007-02-04
> **schorsch said:**
> rm -rf /etc/vmware

that did the trick for me.  vmware installed seemlessly after that.  could you tell me what that command did exactly?

---

### Post by Norfolk 'n' Good on 2007-02-04
Hi,

I had VMware working fine the other day; such a dream to have Ubuntu with XP running flawlessly inside it. However, I recently reinstalled Ubuntu onto a new hard drive and tried to reinstall VMware, but I keep getting the following message when I try to launch it. It's the same copy of Ubuntu (Edgy 6.10 AMDX64). The only thing that's changed,apart from the hard drive, is a new monito

```

root@ubuntu64:/usr/bin# ./vmware /usr/bin/ldd: line 171: /lib/ld-linux.so.2: No such file or directory ldd: /lib/ld-linux.so.2 exited with unknown exit code (127) /usr/lib/vmware/lib/wrapper-gtk24.sh: line 142: /usr/lib/vmware/bin/vmware: No such file or directory /usr/bin/ldd: line 171: /lib/ld-linux.so.2: No such file or directory ldd: /lib/ld-linux.so.2 exited with unknown exit code (127) /usr/lib/vmware/lib/wrapper-gtk24.sh: line 142: /usr/lib/vmware/bin/vmware: No such file or directory root@ubuntu64:/usr/bin#

```

Any help would be much appreciated.

Thank you

---

### Post by yabbadabbadont on 2007-02-04
> **KeithO said:**
> that did the trick for me.  vmware installed seemlessly after that.  could you tell me what that command did exactly?

It removed the vmware configuration directory and all of it's contents...  :)

---

### Post by banditti on 2007-02-05
Probably a stupid question, but I need to F6 for a SATA driver during XP install.  I can't get the floppy to work.  It just shows a red x for the floppy under VMware.

thoughts?

---

### Post by R.J.R. on 2007-02-06
> **banditti said:**
> Probably a stupid question, but I need to F6 for a SATA driver during XP install.  I can't get the floppy to work.  It just shows a red x for the floppy under VMware.

thoughts?
You shouldnt need the SATA drivers for your XP Host. XP will recognize the drive you create in VMWare automatically.

---

### Post by computerjunkie on 2007-02-06
Hey wasup. I've been using dapperdrake for a couple months now and I tried installing vmplayer through synaptic. it hit errors saying the vmnet module wasnt installed blah blah blah. 

so I tried following the instructions in the first post. went great unti...

"Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted."

ARGH what? (I was logged in as root how the heck do I not have access rights to that file??)

I tried sudo first then when it said that I tried "su -" then running the installer and it gave the same error.


sorry if this question was asked already, I wasn't about to look through 80 pages lol.

thanks in advance.

---

### Post by Saubazi on 2007-02-07
I get following during configuration:

Manifying blib/man3/VMware::VmPerl::ConnectParams.3pm
make: Leaving directory `/tmp/vmware-config1/control-only'
make: Entering directory `/tmp/vmware-config1/control-only'
mkdir /usr/local/man: File exists at /usr/share/perl/5.8/ExtUtils/Install.pm line 112
make: *** [pure_site_install] Error 17
make: Leaving directory `/tmp/vmware-config1/control-only'

So wazzup?

---

### Post by dcav on 2007-02-07
> **schorsch said:**
> rm -rf /etc/vmware
this command not work for me because i have one file called locations in the folder that i don't have permission to delete. what can i do? Thanks

---

### Post by techstop on 2007-02-07
> **dcav said:**
> this command not work for me because i have one file called locations in the folder that i don't have permission to delete. what can i do? Thanks

Well then execute the command as a user who does have the permissions then...

```
**sudo** rm -rf /etc/vmware
```

---

### Post by dcav on 2007-02-07
:) Thanks, but i'm really new in ubuntu... i have only one week in that SO. Thanks it works ;)

---

### Post by techstop on 2007-02-07
> **dcav said:**
> :) Thanks, but i'm really new in ubuntu... i have only one week in that SO. Thanks it works ;)

No worries...

Have a read of this info about the sudo command. It is very powerful, and you can potentially get into a bit of trouble if you use it incorrectly;

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by woodmedic on 2007-02-08
I carefully followed all of the instructions to install vmware and it sucsessfully installed according to the terminal.  It shows up in my applications menu but when I click on the icon to run it, it just says....Failed to execute child process"vmware" (no such file or directory)

When I try to run it by typing vmware in the terminal, it say this.....bash: vmware: command not found.  

Any ideas how to fix this??

---

### Post by computerjunkie on 2007-02-09
so um does anyone one know why I am getting the error that I'm getting?? (first post on this page)

---

### Post by computerjunkie on 2007-02-09
nevermind guys i figured out whats wrong

there is actually a bug in the installer it calls for vmware-vix/bin but this doesn't exist in the tarball, but vmware-vix./bin does.

to get around this without editing the perl script to the firs question install the binaries to:

"/wherever/wherever/bin" (mine are in /home/chris/vmware/bin instead of /home/chris/vmware without the "/bin" you'll get the error I was getting.

---

### Post by zeroblitzt on 2007-02-09
This is a monster thread :shock: 

But its a great guide!

---

### Post by kaleman on 2007-02-09
> **Nomearod said:**
> Why do I need to regist before download VMWare? :-k  Is there any free program like this one?

You could try VirtualBox, see [http://www.ubuntuforums.org/showthread.php?t=340113&highlight=virtualbox](http://www.ubuntuforums.org/showthread.php?t=340113&highlight=virtualbox).

---

### Post by dberg on 2007-02-09
Will this HOWTO work with Vista as well, or would that be different?

Thanks

---

### Post by iammeagain on 2007-02-09
Thanx a ton! Just what i have been needin to install vmware, i had no idea where to start before. Awesomness!

---

### Post by iammeagain on 2007-02-09
> **dberg said:**
> Will this HOWTO work with Vista as well, or would that be different?

Thanks

i wouldnt know for sure, but i would think so. i think ill try it out.

---

### Post by iammeagain on 2007-02-10
> **iammeagain said:**
> i wouldnt know for sure, but i would think so. i think ill try it out.

The problem im havin is that Vista isnt able to see a hard drive to install too. Maybe installing XP then upgradin might work... Not sure, but got a big day tomorro so i aint stayin up late to find out.

im not having anyluck instally vista. It doesnt want to accept my product key, it accepts it on a real machine though.

---

### Post by gadget00 on 2007-02-10
Hi all. Im having problems installing windows with the vmware server.

VMWare installed fine, runs fine, creates the virtual machine in a fine way; even boots the windowsCD fine!

[SIZE="5"]***[COLOR="DarkRed"]But when I choose to do the drive format(NTFS, both regular or quick), it goes to the 0% screen, keeps there for a while, and then the virtual machine gets off by itself![/COLOR]***[/SIZE]

If I retry the installation, then tells me "operating system error" and never boots.

Also, all the programs running start having internal errors and crash. I knew it because each time i launch any app, the bug-report program launched, and then crashed too!

I dont understand why this is happening. I even switched the directory that keeps the virtual machine files, just in case it had any permission issues, but keeps on failing. It was supposed to be fine. I saw a guide here in the forums, and they didnt had problems. Im really out of ideas now. Hope for an answer ASAP.

[I]
**Also, I tried to use the recoveryCD that came with the laptop(Toshiba Satellite L10-S104) and that also gave an "Internal Memory Error" and didnt worked either. THe difference is that doing this didnt made the apps crash.[/I]
Edit/Delete Message

---

### Post by iammeagain on 2007-02-10
> **gadget00 said:**
> Hi all. Im having problems installing windows with the vmware server.

VMWare installed fine, runs fine, creates the virtual machine in a fine way; even boots the windowsCD fine!

[SIZE="5"]***[COLOR="DarkRed"]But when I choose to do the drive format(NTFS, both regular or quick), it goes to the 0% screen, keeps there for a while, and then the virtual machine gets off by itself![/COLOR]***[/SIZE]



I haven't had this problem but i run installs off of iso's instead of the actual cd, i figured it could read faster that way. I don't know if that may make a difference, but might as well give it a shot.

So just make an iso file of the cd and tell it to use that as the cd drive.

---

### Post by darklyndsea on 2007-02-10
Apologies if this has been asked already, but this is a rather long thread.  Is there any way for me to access the files already on my computer from within the virtual machine?  Also, how do I get sound to work?  I keep getting an error message which reads "Failed to open sound device /dev/dsp: Device or resource busy
Failed to connect virtual device sound."

---

### Post by raintheory on 2007-02-11
@darklyndsea:

if you set up samba shares in Ubuntu, you can access them from the virtual machine via network.

at least thats how I was able to do it...

as far as the sound, try disabling software sound mixing (ESD) under System/Preferences/Sound in Ubuntu, and see if that helps.

---

### Post by shareMenaPeace on 2007-02-12
This topic reveals howto get a key.
[http://www.vmware.com/community/ann.jspa?annID=203](http://www.vmware.com/community/ann.jspa?annID=203)

---

### Post by Neo40 on 2007-02-12
Hi,

Ok, I tried vmware-server and found it very interesting. However, I don't need it into mt HD anymore. So, how can I  *uninstall* it (vmware, windows98, partition I used to install, etc...)

Thanks

---

### Post by Bealer on 2007-02-13
There's an uninstall script you'll need to find. I think this is what you need to run from a terminal window:

```
sudo /usr/bin/vmware-uninstall.pl
```

---

### Post by cnc333 on 2007-02-13
> **woodmedic said:**
> I carefully followed all of the instructions to install vmware and it sucsessfully installed according to the terminal.  It shows up in my applications menu but when I click on the icon to run it, it just says....Failed to execute child process"vmware" (no such file or directory)

When I try to run it by typing vmware in the terminal, it say this.....bash: vmware: command not found.  

Any ideas how to fix this??



I have this exact same problem and this person was never answered, at least not on this thread.  Does any one know where we should start???

Thanks

---

### Post by mcrae on 2007-02-15
I get this error message after running
```
sudo ./vmware-install.pl
```



```
Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.
```

What could it be!?!

---

### Post by grabro on 2007-02-16
Hi

Is it possible to delete a virtual desktop? I create one but Win98 hung while installing and now it does not recognise the system disk as it has a partial system already installed. So I want to delete that virtual desktop and start again. Incidentally, can you explain(simply please)  where is this 8GB disk installed.

grabro

---

### Post by Repent on 2007-02-16
Ok this is what I get, what should I do? 

joe203@joe203-desktop:~$ sudo apt-get install linux-headers-`uname -r` build-essential xinetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
build-essential is already the newest version.
xinetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
joe203@joe203-desktop:~$ cd /tmp  replace with your download directory
joe203@joe203-desktop:/tmp$ cd vmware-server-distrib
joe203@joe203-desktop:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

joe203@joe203-desktop:/tmp/vmware-server-distrib$ 

> #  Insert your Windows (XP) CD into your CDROM drive
# Open the VMware Server Console
# select 'Create a new virtual machine'

Ok here's the deal there is no Create a new virtual machine on this player.

---

### Post by grabro on 2007-02-16
Hi

It's me again. I have just installd Vmware server with Win98SE on it hence the questions.

I have Win98Se on hda1 but cannot access it as I have 1.5gb of Ram and it doesn't like (will not boot). 

So, what I would like to do is copy all fo the hda1 over to the virtual win98. 

Can I do this? If so, how? 

grabro

---

### Post by Repent on 2007-02-16
Can someone please help ....PLEASE ](*,)

---

### Post by grabro on 2007-02-16
Hi Repent

I don't know whether I can help but here goes. If the Virtual Server loads and its for the first time you should be in a "window" within the server called localhost:localdomain. As far as I can remember within that "window " should be a couple of long(ish) buttons and I think one is "Power on"  As I recall the power on button allows the server to scan your system and eventually you should see what it has found e.g. HDD, CDROM, Memory, Ethernet etc. At this point you should also see a button for "Create virtual desktop". If this is pressed the server shold start to load Win XP from your CDROM. 

Can you say what you see when the server is loaded?

grabro

---

### Post by grabro on 2007-02-16
Hi

Regarding my first two question I have resolved the first and am trying to solve the second by using samba and file sharing. I have a problem however which is stopping me progressiing this option. At the moment the virtual server will not install the ethernet connection. It states it cannot find "/dev/vmnet8"  How do I resolve this?  Do I just create the file? it cannot be that easy as I am assuming that vmnet8 is a socket file.

I have now hit another problem. The server is stuck in full screen mode and Ctrl + Alt will not get me out. Any ideas?

grabro

---

### Post by Repent on 2007-02-16
Thanks grabro but the problem I'm having is the server wont install because it says " A previous installation of VMware software has been detected." I have VMware player installed but why would that matter?

Thanks
Repent.

---

### Post by yabbadabbadont on 2007-02-16
> **Repent said:**
> Thanks grabro but the problem I'm having is the server wont install because it says " A previous installation of VMware software has been detected." I have VMware player installed but why would that matter?

Thanks
Repent.

According to the vmware knowledgebase and forums, you cannot have both installed at the same time.  There is no reason to have vmware-player installed if you have vmware-server anyway.

---

### Post by Repent on 2007-02-17
But I deleted VMplayer and tried to install Vmserver and it still says the same thing . I deleted it from the Synaptic Package before I tried the last time but it still said I had Vmsoftware installed.

Is there a way to purge it from the system?

---

### Post by yabbadabbadont on 2007-02-17
> **Repent said:**
> But I deleted VMplayer and tried to install Vmserver and it still says the same thing . I deleted it from the Synaptic Package before I tried the last time but it still said I had Vmsoftware installed.

Is there a way to purge it from the system?

As has been repeated many times in this thread...  :D  you have to manually remove the /etc/vmware directory after you untinstall vmware.

---

### Post by praxis22 on 2007-02-17
Apologies if this has been answered before, I've yet to read all 84 pages, But...

I got vmware server running, and XP installed, on Edgy, but I upgraded to Fiesty (herd 4) last night, [Kernel 2.6.20-8] so I figured I'd have to rebuild the kernel module, but when I tried this:

```
sudo /usr/bin/vmware-config.pl
```

It went well until it died like this:

```
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-8-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-8-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-8-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

Which looks to me like a syntax error in the vmware include files, or possible incompatibility with kernel 2.6.20.8, anyone got any ideas, before I start digging?

---

### Post by Repent on 2007-02-17
Ok thanks but the problem is I'm new to linux and I have no idea how to manually remove the /etc/vmware directory . So any help as to how I can do this would really be nice.

Repent. ](*,)

---

### Post by praxis22 on 2007-02-17
OK, to remove a directory do the following:

sudo rm -rf /etc/vmware

type in your password when prompted and it will do the rest.

rm = remove/delete

-rf = recursive, forced, (delete everything below this point, and don't talk back) :)


Needless to say you have to be very careful about how you use that command as used in the wrong place it can wipe out your whole OS

---

### Post by praxis22 on 2007-02-17
Hi,

OK, To save anyone else the trouble, this is how you get vmware-server running again after the upgrade to Fiesty from Etch.

I found this page on the vmware forums: [http://www.vmware.com/community/message.jspa?messageID=538342#538342](http://www.vmware.com/community/message.jspa?messageID=538342#538342)

Which is essentially somebody with Fedora Core having the same problems. Looks like the Kernel has undergone a fair bit of pruning between 2.6.17 and 2.6.20 which means you end up with build errors if you try to build the module on a 2.6.20 Kernel.

So the nice people at vmware have come up with a patch [vmware-any-any-update108] which you can find here: [http://ftp.cvut.cz/vmware/vmware-any-any-update108.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update108.tar.gz)

I'm running VMware-server-1.0.1-29996 and this is what I did:

Extract the vmware server & patch tar balls, into /tmp

```
sudo /tmp/vmware-server-distrib/bin/vmware-uninstall.pl
sudo rm -rf /etc/vmware
sudo /tmp/vmware-server-distrib/vmware-install.pl

```
> Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this program to invoke the command for you now? [yes] **no**

```
sudo /tmp/vmware-any-any-update108/runme.pl
```
> Updating /usr/bin/vmware-config.pl ... now patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

> Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [no] **yes**

Then:
Compile, setup, serial, and you're finished.

My XP install was still intact and resumed without a problem. So uninstalling doesn't blank your active VM's or anything, though it may change your NAT numbers, etc. So be sure to check vmnet8 & vmnet1.

However, what it does do is remove the Icon from "Applications -> System Tools" so you'll need to create a new Icon, I put mine on the top panel, just "Add to Panel..." then click on "Custom Application Launcher" button, you'll find the program in /usr/bin/vmware and there is even a real Icon for the vmware-server, (near the bottom of the list) should you want the official "look & feel"

---

### Post by grabro on 2007-02-17
Hi

I have mentioned previously that I am stuck in full screen mode but I have since established  this is not the case. Windows 98 is not in full screen mode but the Server is. Win98 is a small screen in the centre of the screen surrounded by a large black area filing the rest of the screen. The tabs "localhost: localdomain" and "Windows" are the only items of the server I can access. 

I can power down windows but the only way to closed down the server is Ctrl+Alt+backspace which throws me out to my login prompt.

Any ideas how I can get back to a normal server?

grabro

---

### Post by Repent on 2007-02-17
Ok I did as you advised and this is what I got.


joe203@joe203-desktop:~$ sudo rm -rf /etc/vmware
joe203@joe203-desktop:~$ rm = remove/delete
rm: cannot remove `=': No such file or directory
rm: cannot remove `remove/delete': No such file or directory
joe203@joe203-desktop:~$ rm = remove/delete
rm: cannot remove `=': No such file or directory
rm: cannot remove `remove/delete': No such file or directory
joe203@joe203-desktop:~$ -rf = recursive, forced,
bash: -rf: command not found
joe203@joe203-desktop:~$ 

So what should I do now?

---

### Post by darrenm on 2007-02-17
Try installing again.

You were only meant to run the first command, the other lines were just explaining what it meant ;)

---

### Post by Repent on 2007-02-17
lol......OMG I should have looked at it better.

What a noob I am.

Thanks.

---

### Post by Repent on 2007-02-17
Ok just one last thing how do I get it to install Windows  from the CD rom and not the floppy disc?

Thanks for all your help.
Repent.

---

### Post by grabro on 2007-02-17
Repent

You have to go into the BIOS Setup and the machine boots. Its usually F2 or Esc. Press one of these and the machine boots and it will transfer you into the BIOS Setup. Go to the Boot Menu
and you will sees a list of the order of booting, obviously the floppy will be first. 

Scroll down using thearrow keys to the foppy and you can change this to the CDROm drive.

Pree ESC untill you exit and it should ask you to save your changes.

grabro

---

### Post by Repent on 2007-02-17
Thanks I reset the boot order, but for the life of me I can't remember changing it. Any way when I logged back on the Vmserver would not start so I typed vmware into the terminal and got this.

joe203@joe203-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

joe203@joe203-desktop:~$ /usr/bin/vmware-config.pl.
bash: /usr/bin/vmware-config.pl.: No such file or directory
joe203@joe203-desktop:~$ 

And I thought I was done.:confused:

---

### Post by Bobtheknight on 2007-02-17
Hey guys, I installed vmware and xp successfully via the howto.

However, when I try to enable sound support via vm settings, I find the "add" and "remove" bottons at the bottom greyed out.  I can't add sound device or USB drive.  I tried running the vmware as root via sudo vmware.  The same thing happened.

Any help?

---

### Post by Repent on 2007-02-17
Ok look I do indeed have that file, whats going on here?


[IMG]http://i16.tinypic.com/4csdaia.png[/IMG]

Thanks

---

### Post by m.musashi on 2007-02-17
I can't tell for sure but did you type the command with a period at the end?
> joe203@joe203-desktop:~$ /usr/bin/vmware-config.pl.
If so, try without the period.

Also, you might need to run that with sudo but I'm not 100% sure about that.

---

### Post by hfw on 2007-02-17
I am at a loss.  I installed both vmplayer and server last night.  The server seemed to be working.  I tried to run it today and it won't launch.  I tried to run the config, and it wouldn't config.  I ran the uninstall for the server, it said it worked.  I am trying to uninstall the player, and can't seem to get it to work.  I am doing it in Synaptic and get the following error:

E: vmware-player: subprocess pre-removal script returned error exit status 1

Any suggestions on how to get the player uninstalled and the server working.  Thanks.

BTW running Edgy...

hfw

---

### Post by cnc333 on 2007-02-18
> 
Originally Posted by woodmedic 
I carefully followed all of the instructions to install vmware and it sucsessfully installed according to the terminal. It shows up in my applications menu but when I click on the icon to run it, it just says....Failed to execute child process"vmware" (no such file or directory)

When I try to run it by typing vmware in the terminal, it say this.....bash: vmware: command not found.

Any ideas how to fix this??


I have this exact same problem and this person was never answered, at least not on this thread. Does any one know where we should start???

Thanks

---

### Post by Repent on 2007-02-18
Thank you m.musashi that worked, now that I have WindowsXp  loaded and running I noticed that my DVD player and my DVD-RW player have not been installed any ideas?

I would like to take this time to say Thank You to everyone that has helped me.:) 

Repent

---

### Post by m.musashi on 2007-02-18
Getting everything to work right can be a bit of a challenge. I haven't figured out yet how to access physical hard drives. CDs and such are not too bad.

Open your XP vm and instead of clicking power on, choose edit vm settings. On the left half of the window are your devices. If CD is there it may not be correctly configured. If not, choose add to add one (or two). I chose auto detect because that seems to work for me. You may need to play around to find the right settings for you.

---

### Post by Repent on 2007-02-18
Wow just tried to start up Windows and it's a no go, typed  sudo /usr/bin/vmware-config.pl and I got this.

joe203@joe203-desktop:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

I'm starting to think this just isn't meant to be .](*,)

---

### Post by hfw on 2007-02-18
I got the same unable to stop services when i tried to config as well. I am curious what the fix for that is.

hfw

---

### Post by hearty on 2007-02-19
Some how i have installed the Vmware server on my feisty ubuntu. Then I tested it with debian-stable as the guest OS; working well. 
But for Windows Xp I have the pain. XP setup is halting saying that "There is no hardisk attached to your computer". I tried with different versions of XP but the problem remained the same.

SOS

---

### Post by xreed88 on 2007-02-19
after i go through through the vmware setup i get this error



Unable to get the last modification timestamp of the destination file 
/etc/vmware/ssl/rui.key.

Excution aborted


anyone else have this problem?
thx in advance

---

### Post by Repent on 2007-02-19
So can anyone tell me why my Virtual Ethernet failed? Windows ran just fine yesterday I had no problems logging on to the Internet. 



joe203@joe203-desktop:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
Virtual machine monitor done
Bridged networking on /dev/vmnet0 done
DHCP server on /dev/vmnet1 done
Host-only networking on /dev/vmnet1 done
DHCP server on /dev/vmnet8 done
NAT service on /dev/vmnet8 done
Host-only networking on /dev/vmnet8 done
Virtual ethernet failed
Unable to stop services for VMware Server

Thanks.

---

### Post by Repent on 2007-02-19
Bump

---

### Post by evkefalas on 2007-02-20
i follow the instructions and after i run the install
i get
evan@evan-laptop:~/Desktop/tmp/vmware-server-distrib$ vmware
bash: vmware: command not found
evan@evan-laptop:~/Desktop/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

evan@evan-laptop:~/Desktop/tmp/vmware-server-distrib$

i ve tried to install nmplayer before from the synaptic pakg manager
but didnt use it and removed it normally
so it thinks i have a previous vmware installation there
any ideas how to solve this?

Many Thanks

---

### Post by Repent on 2007-02-20
evkefalas just type the following to purge your system of Vmware, then reinstall. 

sudo rm -rf /etc/vmware

type in your password when prompted and it will do the rest.


Needless to say you have to be very careful about how you use that command as used in the wrong place it can wipe out your whole OS


Thanks to praxis 22 for this code.

Repent

---

### Post by Repent on 2007-02-20
OK the guys from Vmware called me and said the reason  it says" Virtual ethernet failed
Unable to stop services for VMware Server" is because there server is having troubles.

But now can anyone tell me why I have to type  " sudo /usr/bin/vmware-config.pl " every time I want to run the Vm server?:(

---

### Post by Aggienator on 2007-02-23
> **Repent said:**
> OK the guys from Vmware called me and said the reason  it says" Virtual ethernet failed
Unable to stop services for VMware Server" is because there server is having troubles.

But now can anyone tell me why I have to type  " sudo /usr/bin/vmware-config.pl " every time I want to run the Vm server?:(

Is there a solution to this apart from uninstalling and reinstalling VMWare server? When I try to run VMWare server I get told to run the config.pl, but I can't because of the "unable to stop services" problem.

Cheers Aggie

---

### Post by m.musashi on 2007-02-23
> **Aggienator said:**
> Is there a solution to this apart from uninstalling and reinstalling VMWare server? When I try to run VMWare server I get told to run the config.pl, but I can't because of the "unable to stop services" problem.

Cheers Aggie

I don't know of any solution but vmware is easy to reinstall. It only takes maybe 5 minutes (if that). Just make sure you do it right. I have several problems but this is what worked for me.

To reinstall vmware, uninstall and remove the /etc/vmware folder

```
sudo /usr/bin/vmware-uninstall.pl
sudo rm -Rf /etc/vmware
```

Now, to avoid problems from any leftover install logs or files this next step is important. Until I figured this out I had problems every time I reinstalled.

Delete the entire /vmware-server-distrib/ folder from your /home (if that is where you put it). Re-extract the archive or just download a new copy. Then run the install as usual.

AFAIK, this does not affect any installed virtual machines. Mine are in a folder in /home and once I reinstalled I just opened like normal and no prob.

---

### Post by miltiad on 2007-02-23
I just installed the version 1.0.1-29996 of vmware-server-console.

The installation went well but I don't have vmware-server in my system menu. When I start it from the command vmware-server-console it show up like everything is ok.

When it ask me to connect to a host I enter localhost in Hostname and nothing in User name and Password -> Unable to connect to the remote host: Cannot connect to host localhost: connection refused.

Btw I didn't have to enter a key.

Any idea ?

---

### Post by m.musashi on 2007-02-23
> **miltiad said:**
> I just installed the version 1.0.1-29996 of vmware-server-console.

The installation went well but I don't have vmware-server in my system menu. When I start it from the command vmware-server-console it show up like everything is ok.

When it ask me to connect to a host I enter localhost in Hostname and nothing in User name and Password -> Unable to connect to the remote host: Cannot connect to host localhost: connection refused.

Btw I didn't have to enter a key.

Any idea ?

I'm not sure about everything but depending on how you set up networking you don't have to enter anything. Just select the radio button for localhost and click connect. You can add a item to the start menu manually. Just right click applications and choose edit menus. It's possible something didn't finish right since it never asked for a key and that could also explain why you don't have a menu icon or are having network problems. You could try to install it again. Watch the output closely as not all errors will cause the install to fail.

---

### Post by Zilulil on 2007-02-25
When i try to install VMWare it says ```
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)?
```
and when i say yes it fails to build vmm module... I have no idea what to do next.

---

### Post by m.musashi on 2007-02-25
> **Zilulil said:**
> When i try to install VMWare it says ```
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)?
```
and when i say yes it fails to build vmm module... I have no idea what to do next.

It looks like you do not have the needed packages for compiling. This line from the tutorial```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
``` should have installed what you need. Double check that these packages are installed (you can just do it again if they're installed nothing will change and if not they will be installed). After you do that you should be able to proceed with the install.

EDIT: I think that is for dapper and/or edgy users. I think it's different for others. Double check the first page of the tutorial.

---

### Post by Zilulil on 2007-02-25
ok i'm running fiesty... i'm going to reread the first page...and i already have the packages you listed installed

---

### Post by m.musashi on 2007-02-25
> **Zilulil said:**
> ok i'm running fiesty... i'm going to reread the first page...and i already have the packages you listed installed

I don't know if this work with feisty. It should but there could be some differences or unmet dependencies.

However, my understanding is that feisty is supposed to support hardware virtualization so vmware may not be what you want. I really know nothing about the hardware virtualization - just rumor - but it might be worth looking into. I plan to when feisty is released.

---

### Post by Zilulil on 2007-02-25
I'm trying to follow the Qemu howto in the wiki... but it seems to be borken...
Install the qemu, kernel-package, linux-source-version  and kqemu-source
```
cd /usr/src/linux
make-kpkg debian
make-kpkg modules_image
module-assistant prepare kqemu 
dpkg -i /usr/src/kqemu-modules-''version''.dpkg
```
the problem seems to come in because i dont' know what ''version'' he wants...

---

### Post by Zilulil on 2007-02-26
EDITED: well i fixed that problem...got another slightly smaller one and a big one... the small one is i can only start vmware with ```
LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware
```

EDITED: fixed that one

---

### Post by Repent on 2007-02-26
Can anyone tell me why I have to type " sudo /usr/bin/vmware-config.pl " every time I want to run the Vm server? Windows runs great afterwards but when I log off I will have to run config to get it to run again.

---

### Post by m.musashi on 2007-02-26
> **Zilulil said:**
> I'm trying to follow the Qemu howto in the wiki... but it seems to be borken...
Install the qemu, kernel-package, linux-source-version  and kqemu-source
```
cd /usr/src/linux
make-kpkg debian
make-kpkg modules_image
module-assistant prepare kqemu 
dpkg -i /usr/src/kqemu-modules-''version''.dpkg
```
the problem seems to come in because i dont' know what ''version'' he wants...

Are you trying to use vmware or kvm? If you want kvm (which is probably better if it works) check [this thread](http://ubuntuforums.org/showthread.php?t=350691). There is a link in the first post to a how to that may or may not be better than the one you are following.

---

### Post by khafra on 2007-02-27
I've been using XP under VMWare in Ubuntu 6.10 for a couple of months now.  I hadda ctrl+alt+backspace out of Gnome, which I've done before, because rdesktop made the session unresponsive to keyboard or mouse input.  But this time, VMWare won't start again.  

- I click it, "Starting VMWare Server Console" appears in the taskbar for a few seconds, but it disappears and I never see an application window
- According to ps axvw, there's no vmware-related tasks running after this (or before, or during)
- /var/log/vmware/vmware-serverd.log has no entries later than three days ago, the last time I successfully started vmware

The homework I need to do in my .NET IDE is due in four days :(

---

### Post by m.musashi on 2007-02-27
Try staring in a terminal and see what kind of errors, if any, you get. That might help pin it down.

---

### Post by khafra on 2007-02-28
Thanks, Miyamoto.  It told me vmware is installed, but has not been (correctly) configured for this system.  Does the graphical starter use a different configuration file than the command line?  If not, could the configuration file still be out there, and just lost somehow?  I don't get it, I didn't move anything around or delete anything--automatic ubuntu updates and data file downloads are the only changes I've made.

---

### Post by els on 2007-02-28
Worked great.  Thanks a lot.  This is way cool.

---

### Post by veloce on 2007-02-28
> **khafra said:**
> Thanks, Miyamoto.  It told me vmware is installed, but has not been (correctly) configured for this system.  Does the graphical starter use a different configuration file than the command line?  If not, could the configuration file still be out there, and just lost somehow?  I don't get it, I didn't move anything around or delete anything--automatic ubuntu updates and data file downloads are the only changes I've made.

Have you recently upgraded your kernel?  Sounds like you need to run vmware-config again.  This recompiles some stuff for your system.

---

### Post by m.musashi on 2007-02-28
> **khafra said:**
> Thanks, Miyamoto.  It told me vmware is installed, but has not been (correctly) configured for this system.  Does the graphical starter use a different configuration file than the command line?  If not, could the configuration file still be out there, and just lost somehow?  I don't get it, I didn't move anything around or delete anything--automatic ubuntu updates and data file downloads are the only changes I've made.

Starting with the menu or in a terminal should be the same. Did the terminal give any output? If so, can you post it? I suggested the terminal as it will usually give you some info about what might be causing it to not work. I had a permissions problem before and didn't know what it was until I used the terminal.

As veloce suggests it could be kernel issue too.

---

### Post by khafra on 2007-02-28
I got it--Veloce hit the nail on the head.  Ubuntu updated my kernel, so the vmmon installed using my old header files was no longer valid.  Wish the program woulda told me that instead of silently failing.

---

### Post by veloce on 2007-02-28
> **khafra said:**
> I got it--Veloce hit the nail on the head.  Ubuntu updated my kernel, so the vmmon installed using my old header files was no longer valid.  Wish the program woulda told me that instead of silently failing.

Yeah, I spent ages trying to track this one down. I'd just spent ages trying to get dual screens working and thought it was X causing the problem!

---

### Post by Vincent_Lin on 2007-03-01
Dear all,

I am mostly certain that this question has been asked before, but bear with me for being too lazy lookin it up.

I have xp running as guest in vmware server under 6.10.  Everything works (except skype, that's a well known problem), including sound, usb, networking, highresolution, ..). 

The problem is that I could not use audio device in xp when another program is using audio device outside vmware, say mplayer, with or without gnomes' esound enabled.  Message is something like audio device not availabe, or used by another program, something like that.

Does any one have a workaround?

Thank you very much.

Cheers,


Vincent Lin

---

### Post by praxis22 on 2007-03-01
```
The problem is that I could not use audio device in xp when another program is using audio device outside vmware,
```

I would have expected that to be honest, either that or you'll get a cacophony of two separate sets of sounds coming out of the same speakers. Though of the two options I would expect that only one application can exclusively use the audio output registers at one time to be the logical choice.

You can only really listen to one thing at a time anyway, failing that buy and configure a USB sound card, that way you have two sound cards, one for each OS.

---

### Post by littlewing0906 on 2007-03-01
> **krazykirk said:**
> Wow! It works great! Great guide btw!

But i'm having 1 problem!

I press the "full screen" button, and i get a error!

```
Unable to find an appropiate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.
```

I think it means Xorg.conf in the same directory, but i have no idea to "add the guest mode."

I'm going to restart X now to see how that goes!

I'll post results here.

After surfing the VMTN Discussion forums I found a thread, 
[http://www.vmware.com/community/thread.jspa?messageID=519426&#519426]("http://www.vmware.com/community/thread.jspa?messageID=519426&#519426")

i am currently running X at 1280x800; the guest OS is Windows XP. I turned off the guest OS, then opened and added to the *.vmx file these lines:
svga.maxWidth = "1280"
svga.maxHeight = "800" 
Then I started the guest OS up and changed the resolution in WindowsXP to 1280x800.
I was able to get full screen working!  By default, the vmx file is stored under /var/lib/vmware/VMWare Machines/.

---

### Post by caffienda on 2007-03-01
Wow, long thread!  My eyes are bleeding..
I'm having an install problem, and I saw many other users experiencing this throughout the thread, but they were all different. I apologize if this is a repeated question, but I didn't see an answer that fit my question.

I just installed 6.10 Server and am trying to now install VMware server. I am getting a error about 2/3's of the way through the install. Any idea on how to clear this up?

```


apt-get install libx11-6 libx11-dev libxtst6 xlibs-dev xinetd wget apt-get install 
  linux-headers-386 build-essential apt-get install gcc binutils-doc cpp-doc make manpages-dev 
  autoconf automake1.9 libtool flex bison gdb gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1 

tar xvfz VMware-server-*.tar.gz cd vmware-server-distrib sudo ./vmware-install.pl
```

This is the message I get pretty far into the install:
> 
None of the pre-built vmmon modules for the VMware server is suitable for your running kernel. Do you want this program to try to build the vmmon module for your system (you need to have a C compiler installed on your system)? [yes]

using compiler "usr/bin/gcc". Use environment Use enviornment variable CC to override.

[COLOR="Blue"]What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.[/COLOR]

The text in blue is what loops when I press enter here. I guess it is missing a C compiler or something?

I have the following directories in the /usr/src/ folder
linux
linux-headers-2.6.17-11
linux-headers-2.6.17-11-386
I've tried using all of these folders in the install, followed by the /include folder.
ex.  /usr/src/linux-headers-2.6.17-11/include          and this is what I get:
The directory of the kernel headers (version 2.6.17-11) does not match your running kernel (version 2.6.17-10-server).  Even if the module were to compile successfully, it would not load into the running kernel.

What do I do?

---

### Post by garren on 2007-03-02
I'm having two problems, one of which is similar to that which someone else posted.  I got VMWare-server running, and I intalled XP, after I power down my computer and turn it on again, when I run vmware-server-console, it gives me this error: 
> VMware Server Error:
VMware Server is installed, but it has not been (correctly) configured for your running kernel. To (re-)configure it, your system administrator must find and run "vmware-config.pl". For more information, please see the VMware Server documentation.
At the suggestion of the error box as well as the replies in this forum, I ran vmware-sonfig.pl again.  Doing so fixed the problem...until I turned off the computer and turned it back on again (to tell you the truth, I don't know if actually turning off the computer did it; I may have gotten the same error after turning vmware off and on again, but I'm not sure because I haven't tried it.  I can though if you guys really need me to) [*EDIT: I have now experimented with this; merely quiting the server console does not mess things up--it's only when I turn off my computer and restart it that I get the problem.  Every time I restart my computer, if I want to run VMware, I have to run vmware-config.pl*].  

Any ideas?  
[*EDIT: Answer found here: [http://ubuntuforums.org/showthread.php?t=288018]("http://ubuntuforums.org/showthread.php?t=288018").  Man, you forum guys are so smart!*]
[*EDIT (again): The answer above was mostly ok, except deleting the "not configured" file messed up my server.  So I ran "vmware" in the console, and it had me reconfigure something, and now it is working properly.*]

Second problem--I think this is because of the way I installed VMware.  To run it, I have to open a console and use sudo, I can't just open it from the menu.  What did I do wrong, and how should I make it so I can just open it from the menu?  

[*EDIT: I have now tried "sudo chown -R <my username> <whatever file I need to do this to>; and it worked.*]

Oh--by the way; this is VMware 1.0.2 build-39867 on Edgy (with kernel-2.6.17-11-generic) on a dell D400 laptop.

---

### Post by schorsch on 2007-03-02
Hi,
> **caffienda said:**
> 
I have the following directories in the /usr/src/ folder
linux
linux-headers-2.6.17-11
linux-headers-2.6.17-11-386
I've tried using all of these folders in the install, followed by the /include folder.
ex.  /usr/src/linux-headers-2.6.17-11/include          and this is what I get:
The directory of the kernel headers (version 2.6.17-11) does not match your running kernel (version 2.6.17-10-server).  Even if the module were to compile successfully, it would not load into the running kernel.

What do I do?

I guess, you have updated all packages as proposed by Ubuntu. But you did not not boot into the updated kernel 2.6.17-11-server, right? As long as you have not booted the updated kernel, the updated kernel-headers do not match the running kernel, So please either boot into the new kernel or downgrade the kernel headers to version 2.6.17-10-server.

---

### Post by caffienda on 2007-03-02
> **schorsch said:**
> Hi,


I guess, you have updated all packages as proposed by Ubuntu. But you did not not boot into the updated kernel 2.6.17-11-server, right? As long as you have not booted the updated kernel, the updated kernel-headers do not match the running kernel, So please either boot into the new kernel or downgrade the kernel headers to version 2.6.17-10-server.

Thanks for the response.  I tried rebooting and am still getting the same error:
> The directory of the kernel headers (version 2.6.17-11) does not match your running kernel (version 2.6.17-10-server). Even if the module were to compile successfully, it would not load into the running kernel.

I'm not sure how to downgrade my kernel or make it run the  2.6.17-11 version.  Suggestions?

---

### Post by PartisanEntity on 2007-03-02
I installed vmware server and win xp pro today. I am trying to get win xp to access the internet. When I try to enable NIC0 in Vmware Tools Properties but I get an error message that 

> Could not open /dev/vmnet8: No such file or directory
Failed to connect virtual device Ethernet0.

Now in edgy I am connected to wifi only through eth1.

Screenshots to follow:

---

### Post by ace_a1 on 2007-03-02
hello !!
i have ubuntu running as a host and xp home edition as a guest .. i got the vmware server working today .. finally !! thanks to the guide here !! but as i was looking through my windows i found out .. that i have no sound and no internet connection .. plus on my ubuntu i m connected to the internet via wifi and its the eth1 network connection .. so while configuring vmware server i used the eth1 for connection .. i dont know if tht is wht i should do .. plus i really need the sound thing working .. and yeah when i check the device manager on my computer (xp) all the drivers are installed .. but the funny thing is its using vmware drivers !! newayz i hope some one finds the solution !!

---

### Post by m.musashi on 2007-03-02
> **caffienda said:**
> I'm not sure how to downgrade my kernel or make it run the  2.6.17-11 version.  Suggestions?

I think you need to reconfigure vmware for the new kernel. Here are the instructions from the first page:
```
After a kernel upgrade VMWare won't start because it  has not been (correctly) configured for the running kernel

execute
[code]sudo /usr/bin/vmware-config.pl
```
[/code]

---

### Post by alteveer on 2007-03-02
> **marianoi said:**
> 
For some reason I had problem installing a virtual machine if I ran "vmware" so I always do:

sudo vmware

to run it as a super user (correct me if this is not a good policy please)
Mariano

i would say, as a general rule, give everything as little permission as is humanly possible, friend. i won't make this a soapbox, but viruses on windows are a great example of why.

when my server console wasn't starting up after i used **sudo** to put the serial number in (i forgot to during install), i ran vmware in a shell to see what the issue was:

```
Unable to alloc client: Cannot open file "/home/alteveer/.vmware/preferences": Permission denied.
```

... permissions! and this:

```
sudo chown -R <your username> ~/.vmware
```

should to the trick.

c

---

### Post by schorsch on 2007-03-03
> **caffienda said:**
> Thanks for the response.  I tried rebooting and am still getting the same error:


I'm not sure how to downgrade my kernel or make it run the  2.6.17-11 version.  Suggestions?

What is the output of the following comands:

```

uname -a
dpkg -l | grep kernel
cat /boot/grub/menu.lst

```

---

### Post by PartisanEntity on 2007-03-04
Could someone help me resolve [this issue]("http://ubuntuforums.org/showpost.php?p=2238088&postcount=889")? I would really appreciate it. I can't XP Pro to access the net in vmware because when I try to activate NIC0 I get an error message.

Could it be due to the fact that during the configuration I selected 'no' to set up betworking for the hosted OS? I did that because I had no idea what to enter in that section concerning pots etc..

---

### Post by m.musashi on 2007-03-04
That's probably the reason. You might want to reconfigure it (or just reinstall vmware it won't mess up the xp already installed) and this time just accept the defaults for networking.

---

### Post by caffienda on 2007-03-04
> **schorsch said:**
> What is the output of the following comands:

```

uname -a
dpkg -l | grep kernel
cat /boot/grub/menu.lst

```

```
uname -a:
```
> Linux TRex 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

```
dpkg -l | grep kernel
```
> ii  iptables                         1.3.5.0debian1-1ubuntu2                Linux kernel 2.4+ iptables administration to
ii  libdrm2                          2.0.2+git20060809-0ubuntu1             Userspace interface to kernel DRM services -
ii  linux-headers-2.6.17-10          2.6.17.1-10.34                         Header files related to Linux kernel version
ii  linux-headers-2.6.17-10-generic  2.6.17.1-10.34                         Linux kernel headers for version 2.6.17 on x
ii  linux-headers-2.6.17-11          2.6.17.1-11.35                         Header files related to Linux kernel version
ii  linux-headers-2.6.17-11-generic  2.6.17.1-11.35                         Linux kernel headers for version 2.6.17 on x
ii  linux-headers-generic            2.6.17.11                              Generic Linux kernel headers
ii  linux-image-2.6.17-10-generic    2.6.17.1-10.34                         Linux kernel image for version 2.6.17 on x86
ii  linux-image-2.6.17-11-generic    2.6.17.1-11.35                         Linux kernel image for version 2.6.17 on x86
ii  linux-image-generic              2.6.17.11                              Generic Linux kernel image
ii  module-init-tools                3.2.2-3ubuntu3                         tools for managing Linux kernel modules
ii  udev                             093-0ubuntu18.0edgy2                   rule-based device node and kernel event mana


```
cat /boot/grub/menu.lst
```
> # menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3fb2b0d1-7574-44e3-8d68-df68b3e2de5a ro
# kopt_2_6=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by PartisanEntity on 2007-03-04
> **m.musashi said:**
> That's probably the reason. You might want to reconfigure it (or just reinstall vmware it won't mess up the xp already installed) and this time just accept the defaults for networking.

Thanks for the info, reconfiguring and selecting networking defaults worked.

I just realised I have on sound in vmware xp pro, any tips on how to solve this? :)

---

### Post by m.musashi on 2007-03-04
> **PartisanEntity said:**
> Thanks for the info, reconfiguring and selecting networking defaults worked.

I just realised I have on sound in vmware xp pro, any tips on how to solve this? :)

No. I don't have sound either. I haven't bothered to try and fix it since I almost never use it. There might be something in this thread though. I kind of remember reading about it.

Anyway, glad you got it more or less working.

---

### Post by PartisanEntity on 2007-03-05
[I]Well I can live without sound in vmware too, don't really need it. But now network manager keeps crashing ever since I reconfigured vmware settings to allow networking. I**f I remove vmware will that undoe the offending settings?**

I use wifi as my main way of connecting to the internet, I don't have ethernet in this room. So since reconfiguring vmware, if I disable **network manager** I cannot re-enable it, and if I do try to do so it crashes edgy and I have to manually shutdown.

This is extremely annoying...[/I]

**_Update_**: I reconfigured vmware, this time I said 'no' to setting up networking, it undid the previous networking settings and upon testing network manager it no longer crashes if I disable it and I can once again re-enable it without problems. Has anyone else noticed this?

---

### Post by schorsch on 2007-03-05
Hola, caffienda

that is weird ..... :

"uname -a" tells you the version of the running kernel and this is "2.6.17-11-generic" .....
"dpkg -l | grep kernel" shows the installed packages regarding the kernel and the right header packages are installed ...
... and grub boots into the mentioned 2.6.17-11-generic kernel ....

so where does the reference to the 2.6.17-10-server kernel come from?

... but I am missing the kernel sources in the output of the "dpkg -l"  command

Could you please check the following commands:

```

cd /lib/modules
find . -name build

```

What is the content of the directory "/usr/src/linux" ?

Perhaps you should install the kernel sources for the running kernel and unpack them via

```

sudo apt-get install linux-source-2.6.17
cd /usr/src
sudo tar jxvf  linux-source-2.6.17.tar.bz2
sudo ln -s linux-source-2.6.17 linux

```

After this please try co configure vmware again ....

---

### Post by chinaski on 2007-03-05
> **chinaski said:**
> hello, for me simple copy&paste works
I quote myself to correct:

copy&paste from Ubuntu to XP virtual machine **do not work** (I'm sure it did the first time I installed it... and I was not drunk I swear :D ) but then I solved by sharing a folder in Ubuntu that I can browse from emulated XP.

It works fine :)

---

### Post by olieviya on 2007-03-06
Windows run from inside VMWare doesn't recognise my screen as being widescreen, what can i do?

---

### Post by PartisanEntity on 2007-03-06
> **olieviya said:**
> Windows run from inside VMWare doesn't recognise my screen as being widescreen, what can i do?

I had the same problem, I solved the issue using the method mentioned on [page 2 of this thread]("http://www.ubuntuforums.org/showthread.php?t=316381"). You have to edit the windows registry.

---

### Post by soffdarbau on 2007-03-07
Hi all, 

I installed VMware last night on my Ubuntu and run a fresh copy of XP through it.  All works well but the internet through XP is not working and yet it is fine through Ubuntu (as is everything else :) ).  How do I get the internet through VMware working on XP, all I really want it for is skype video calls to overseas ( i know about other VOIP's but it is the other side that are older and stuck in their ways...)

Thanks,

---

### Post by PartisanEntity on 2007-03-07
Do you get an error message when xp is loading in vmware? Something with the words vmnet# ? If yes, then you need to reconfigure vmware and this time select 'yes' when it asks about networking set up.

---

### Post by veloce on 2007-03-07
> **soffdarbau said:**
> Hi all, 

I installed VMware last night on my Ubuntu and run a fresh copy of XP through it.  All works well but the internet through XP is not working and yet it is fine through Ubuntu (as is everything else :) ).  How do I get the internet through VMware working on XP, all I really want it for is skype video calls to overseas ( i know about other VOIP's but it is the other side that are older and stuck in their ways...)

Thanks,

Isn't there a linux version of skype?

Otherwise, yeah, what he said - you need to setup virtual networking.  Bridged would be easiest for one vm.

---

### Post by bankie on 2007-03-07
The options under Hardware in the VM settings are grayed out. Any reason for this?

---

### Post by cknight725 on 2007-03-07
Something I ran across ...

I followed this HOWTO to get VMWare and XP running -- it works great!  However I was unable to get WindowsUpdate to run.  It would always error out with error 0x8007227 or something like that.  Basically it blamed proxy settings.

The fix was to set the Windows XP MTU setting to match that of the Ubuntu host machine.  In my case that was a size of 1492.
```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces\{SomeDamnInterfaceCode}]

"MTU"=dword:000005d4


```

---

### Post by nevertheless on 2007-03-08
I want to install windows xp and ubuntu on vmware but do I have to reinstall windows xp if its already on my computer or can I just put it on the vmware to boot with ubuntu. Also if I install this does ubuntu and windows xp start everytime together or will I have a choice with dual boot still.

---

### Post by markus77 on 2007-03-08
Hi everyone,
I installed today vmware-server to my ubuntu server and installation gone fine.
I can also make a new virtual machine and boot it up, but problems start when 
I try install windows xp on it. Keyboard is not detected because I can't press Enter to Install
or press ctrl-alt to escape from virtual machine. I use my server via nomachine nx-client is that the problem,if it's, is there any solutions for that.

thanks,
-markus

---

### Post by PartisanEntity on 2007-03-08
> **nevertheless said:**
> I want to install windows xp and ubuntu on vmware but do I have to reinstall windows xp if its already on my computer or can I just put it on the vmware to boot with ubuntu. Also if I install this does ubuntu and windows xp start everytime together or will I have a choice with dual boot still.

You need to install xp inside vmware, and no it does not dual boot. vmware is an application that you launch when you need it (inside ubuntu in this case). vmware is not to be mixed up with native installations of any OS.

---

### Post by Traiklin on 2007-03-08
ok this does not want to install at all for me.

I just copied and pasted everything quoted so it wouldn't mess up, it worked fine till

```
sudo ./vmware-install.pl
```

when I go to run that I get this error 

```
sudo: ./vmware-install.pl: command not found
```

I tried to use Automatrix & the repository but they both only had the player not the server, I try to just run the install.pl file in the terminal and the only thing that happens is the terminal comes up then closes right away.

I'm running whatever the latest VMWare server is & ubuntu 6.10.

---

### Post by PartisanEntity on 2007-03-08
Are you sure you are in the right folder? You need to navigate to the vmware folder you downloaded in order for that command to start the installer.

---

### Post by Traiklin on 2007-03-08
> **PartisanEntity said:**
> Are you sure you are in the right folder? You need to navigate to the vmware folder you downloaded in order for that command to start the installer.

yep, it's in the right folder, when I did just /tmp then when I tried to do ```
cd vmware-server-distrib
```
 it kept giving me an error that vmware-server-distrib couldn't be found, I renamed the folder and same error, then I tried just moving all the files to just the /tmp folder and I still got the error that it couldn't run the installer for some strange reason.

---

### Post by Jontydog on 2007-03-12
Great How to XP is up and running fine in VMware.  The only problem I have is my Skystar 2 PCI satellite card has not been found.  Is there a way to install it in or am I flogging a dead horse.  I wanted xp installed to use altdvb as I prefer this to mythtv or  vdr which are way too complicated for a linux n00b like myself.  I have tried altdvb in wine and it finds the card but won't register the needed drivers.  Any help gratefully received :)

---

### Post by Jontydog on 2007-03-12
Traiklin I know this may sound daft but when I tried to install vmware the first time I actually forgot to extract the files and it took me ages to find out where I had gone wrong. I extracted the folder to the desktop and then ran it from there.

---

### Post by nicklogan on 2007-03-13
> **mcrae said:**
> I get this error message after running
```
sudo ./vmware-install.pl
```



```
Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.
```

What could it be!?!

If you are installing any files to a directory which has been formatted as FAT32, put the option 'quiet' in the fstab line for that drive or partition. That solved the problem for me.
example:
UUID=45A6-A5E9  /media/Files    vfat     iocharset=utf8,umask=007,quiet,users,gid=100,uid=1000        0   0

---

### Post by veloce on 2007-03-13
> **Jontydog said:**
> Great How to XP is up and running fine in VMware.  The only problem I have is my Skystar 2 PCI satellite card has not been found.  Is there a way to install it in or am I flogging a dead horse.  I wanted xp installed to use altdvb as I prefer this to mythtv or  vdr which are way too complicated for a linux n00b like myself.  I have tried altdvb in wine and it finds the card but won't register the needed drivers.  Any help gratefully received :)

Definately dead horse on this one.  vms can only use hardware passed to them by the host os (in this case linux).  If linux doesn't have drivers for the card then it has no way of passing access on to the vm. Further, vmware only has options to pass certain types of hardware on, and I don't think tv cards are included.  And finally, vmware cannot run any 3d acceleration so tv is likely to be a non-starter.

---

### Post by akailum on 2007-03-15
that was greatly explained. It helped me a lot.
very much appreciated.
cheers
DA

---

### Post by dmeans08 on 2007-03-17
Hey Everyone,
I have been getting an error despite having installed vmware server successfully in the past.  

"vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl."

I have already tried reconfiguring twice, un-installing reinstalling, and reconfiguring. 
Anyways if anyone can help me I would greatly appreciate it.  
-Derek

---

### Post by dmeans08 on 2007-03-17
Hey Everyone,
I found a solution to my problem that I am sure is considered fairly obvious, I simply erased the not_configured file.
-Derek

---

### Post by fakie_flip on 2007-03-17
Here is a guide for anyone trying to install VMWare Server in the development version of Feisty.

[http://icanthack.com/?p=53](http://icanthack.com/?p=53)

---

### Post by Master Dwarf on 2007-03-17
I have VMServer installed on Edgy. It launches without a hitch. I create a machine in the default directory and /home/username/virtualmachines/

While trying to install Xp home it says windows cannot find my cd rom drive even though it originally booted (vm) from it. It happens after the xp EULA.  I started going through this monstrous thread and found nothing about this.  Granted I only checked 50 some pages, so maybe the solution is indeed here somewhere.  It's a regular NEC, IDE, DVD burner.  I even tried futzing with the CDRom settings in the VM to no avail.

---

### Post by johnbuck on 2007-03-18
I already have window XP and Ubuntu on different partitions and currently dual booting via GRUB. I like to boot with XP in Ubuntu. Can I use XP which already installed or do I need to reinstall XP under VMware?

---

### Post by mills on 2007-03-18
the installation of vmware server went well but when i tried to start it, no joy.

i typed vmware in terminal and got this error.

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

an imaginary pint for anyone who solves it:)

EDIT: solved it..... sudo apt-get remove libdbus-1-2 

credit to kevinG

---

### Post by praxis22 on 2007-03-19
> **johnbuck said:**
> I already have window XP and Ubuntu on different partitions and currently dual booting via GRUB. I like to boot with XP in Ubuntu. Can I use XP which already installed or do I need to reinstall XP under VMware?

Not as far as I know, I think you need to install XP into vmware from scratch. It's what I had to do.

---

### Post by gabng on 2007-03-19
> **johnbuck said:**
> I already have window XP and Ubuntu on different partitions and currently dual booting via GRUB. I like to boot with XP in Ubuntu. Can I use XP which already installed or do I need to reinstall XP under VMware?

> **praxis22 said:**
> Not as far as I know, I think you need to install XP into vmware from scratch. It's what I had to do.

Actually, it's possible to run the existing Windows install within Ubuntu through VMware server.
Check out this thread: [http://www.ubuntuforums.org/showthread.php?t=365057](http://www.ubuntuforums.org/showthread.php?t=365057)

---

### Post by praxis22 on 2007-03-19
I could be wrong here, but I suspect that what JohnBuck wants is to be able to use his currently installed version of XP under vmware. This, as far as I know, is not possible.

What the link you provided does, is give you a way to clone your existing install to a VM image. Essentially duplicating your entire XP install, meaning you require a lot more storage space. if your XP partition/disk is 20Gb, you need a 20Gb VM image. This VM, is then physically isolated from the real XP install.

So if you change your screen saver in the VM, the screensaver in the physical install of XP will remain unchanged.

Essentially you can take a copy, but you can't use the real thing. That is my understanding of the situation.

---

### Post by gabng on 2007-03-19
> **praxis22 said:**
> I could be wrong here, but I suspect that what JohnBuck wants is to be able to use his currently installed version of XP under vmware. This, as far as I know, is not possible.

What the link you provided does, is give you a way to clone your existing install to a VM image. Essentially duplicating your entire XP install, meaning you require a lot more storage space. if your XP partition/disk is 20Gb, you need a 20Gb VM image. This VM, is then physically isolated from the real XP install.

So if you change your screen saver in the VM, the screensaver in the physical install of XP will remain unchanged.

Essentially you can take a copy, but you can't use the real thing. That is my understanding of the situation.

Actually if you read the entire thread, I've confirmed I am able to run my existing Windows install in Ubuntu through VMware server, not cloning nor converting the physical partition to a VM or whatever, but actually running the Windows install as is, which lies in the NTFS partition in the same computer, which can be dual booted, anything changed through running the Windows through VMware will be reflected when you actually dual boot into Windows (I hope I'm clear enough on this).

---

### Post by praxis22 on 2007-03-19
Post in haste, repent at leisure :)

OK, I see what you mean, but that would mean installing VMtools into your native XP partition, not to mention having to chose which hardware profile to use each time you boot into XP, right?

I'm also presuming that certian apps which rely on the base hardware, like DX9 games, etc, Don't work under emulation, at least not with Server. I know Workstation is a lot better in this regard.

Since I've backed my data up, prior to re-installing, I may give it a try later, what NTFS stuff have you got installed?

---

### Post by gabng on 2007-03-19
:) I wasn't clear enough with my first post anyways.

You're right, I had to install VMtools in the native XP, but it doesn't affect anything when dual booted into XP if you have any concerns for that.  And yes, you'll need to choose the hardware profile when booting into XP, in both dual booting and booting in VMware.

I haven't tried running 3D apps when running the native XP in VMware, but I would think it's the same as running a guest XP in VMware, since it's emulated hardware, 3D support won't be too good, if there is any at all.

I used VMware server since it's free as opposed to workstation, so can't comment on workstation.  But I think I'll directly boot into XP anyways if I'm going to run any 3D or memory intensive programs.

What do you mean by NTFS stuff?  If you mean programs in Windows, just everything I had in XP before making it work in VMware.  If you mean programs in Linux to access NTFS partitions, I have ntfs-3g installed to read and write to NTFS partitions.

Few pieces of advice on running the native XP in vmware is be careful on booting that you don't boot into Ubuntu when you reach GRUB, I did that twice and was able to recover from it, but who knows if it will be recoverable next time.  Also, if you use ntfs-3g, make sure native XP shuts down gracefully in vmware else you'll need to directly boot into XP to scan your NTFS partitions before being able to mount them again in Ubuntu.  Just to be safe, I unmount all my NTFS paritions before running native XP in vmware to make sure they don't access the partitions at the same time.  I don't actually know if any problems will arise from that, but I don't want to be test lab mouse and risk my data. :popcorn:

---

### Post by praxis22 on 2007-03-19
Yes, I meant what are you using in Ubuntu to mount NTFS, I'm running the same so it should be OK. I don't mount my NTFS partitons in Ubuntu anyway. I'm not sure the write access is 100% reliable under all situations. I use a FAT32 common file system as go between. 

I'm guessing you can't suspend your XP install like you can with an image, right?

I don't dual boot, I'm running my systems on physically different disks, and GRUB refuses to load XP anyway. Though I suspect that it's probably less hassle to simply mirror XP to a VM and run that, less to lose if it all goes horribly wrong, I'm sure having to chose my profile each time would annoy me after a while anyway :)

---

### Post by gabng on 2007-03-19
If you're talking about pausing XP in VMware, it actually does work, as long as you don't need to mount ntfs partitions after you suspend it.  And I'm not sure about what will happen when you directly boot into XP after you pause it.

It's true it might be safer to convert XP into VM image, but it'll take up more space if you want to keep the native XP (not that storage space is expensive), but it'll be useful if you ever want to boot XP natively with any changes made when running in vmware being still there (not that I do it too often, since it's just used as a transition stage to linux for my family).

---

### Post by cesera on 2007-03-19
> **johnbuck said:**
> I already have window XP and Ubuntu on different partitions and currently dual booting via GRUB. I like to boot with XP in Ubuntu. Can I use XP which already installed or do I need to reinstall XP under VMware?
Check out this reply in this thread:


[http://www.ubuntuforums.org/showthread.php?p=1986129#post1986129](http://www.ubuntuforums.org/showthread.php?p=1986129#post1986129)

It is usually worth searching the forums carefully before asking questions.  ;-)

---

### Post by ryankhart on 2007-03-19
Will this also work for Suse 10.2?

---

### Post by Shampyon on 2007-03-19
As far as I know this guide, minus the Windows-specific portions, will work perfectly for installing pretty much any pc-based OS.

---

### Post by Shampyon on 2007-03-21
Damn, this is odd. I followed the intructions for accessing my actual XP pertition through VMWare Server. Once it gets to the stage where I'm supposed to fire it up for th efirst time, though, it fails, and I get this error:
> Cannot open the disk '/var/lib/vmware/Virtual Machines/WINXP/WINXP.vmdk' or one of the snapshot disks it depends on.
Reason: The partition table is invalid.
My hard drive is split into 5 partitions:
XP (NTFS)
Linux storage space 1 (reiserfs)
Linux storage space 2 (reiserfs)
Ubuntu Home partition (reiserfs)
Linux swap partition 

***Edit:*** I've been able to find only [one google result]("http://www.vmware.com/community/thread.jspa?messageID=513200&#513200") in English matching this problem. Apparently it has something to do with XP and Linux reading partition tables differently. The fix is far more drastic than I'd like. it recommends reinstalling Linux entirely after using XP to create the partitions. I've only just gotten Ubuntu working again, and I really don't want to go through downloading and installing all of those hundreds of MB worth of extras for the nth time.

Any advice?

---

### Post by Trenchbroom on 2007-03-23
Just want to say "thanks" for this thread.  With a bit of tinkering and some reading I've got it running and running well.

---

### Post by Shampyon on 2007-03-23
I managed to get it to start booting, but after the Windows Bootscreen starts there's some kind of error and it tries to restart. Stuck in a loop...

---

### Post by joco2 on 2007-03-30
have followed the instructions as stated but I keep getting this error in the terminal to run config again so i do but keep getting the same error. anyone know whats wrong here?



####@EvoLinux:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

####@EvoLinux:~$ sudo /usr/bin/vmware-config.pl
Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
/usr/share/applications/vmware-console-uri-handler.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.17-11-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.17-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [no] 

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Would you prefer to modify your existing networking configuration using the 
wizard or the editor? (wizard/editor/help) [wizard] 

The following bridged networks have been defined:

. vmnet0 is bridged to eth0
. vmnet2 is bridged to ath0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

The NAT network is currently configured to use the private subnet 
192.168.235.0/255.255.255.0.  Do you want to keep these settings? [yes] 

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.235.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

The host-only network is currently configured to use the private subnet 
192.168.2.0/255.255.255.0.  Do you want to keep these settings? [yes] 

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.2.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

Do you want to enter a serial number now? (yes/no/help) [no] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Bridged networking on /dev/vmnet2                                  failed
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Server 1.0.2 build-39867 for Linux for this running
kernel completed successfully.

####@EvoLinux:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

####@EvoLinux:~$

---

### Post by carloslosgrande on 2007-03-30
Hi, I followed this HowTo and everything ran like a breeze, well done Peturr.
A small matter has arisen - it seems the virtual XP cannot access usb drives? I checked the VMWare forums and its often said that ESX doesn't support USB but my VM menu shows a USB option under 'removable devices' but the 'connect/edit' filed shows as empty.
Does it mean that I actually can't use any USBs in virtual mode??
This is actually the reason I wanted to use this app.
Thanks.

---

### Post by Wofl on 2007-03-31
i followed the instructions, but i get an error when tring to start

it tells me to rerun the /usr/bin/vmware-config.pl

kernel headers is al fine, but it somehow cant bridge the network...

this is what i get after runing the configure script again
```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Server 1.0.2 build-39867 for Linux for this running
kernel completed successfully.

```

i told it to bridge network to my wifi connection (ath0)

---

### Post by Wofl on 2007-03-31
i followed the instructions, but i get an error when tring to start

it tells me to rerun the /usr/bin/vmware-config.pl

kernel headers is al fine, but it somehow cant bridge the network...

this is what i get after runing the configure script again
```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Server 1.0.2 build-39867 for Linux for this running
kernel completed successfully.

```

i told it to bridge network to my wifi connection (ath0)

*edit*

now got it working by entirely disabling the networking features...

---

### Post by phil90 on 2007-03-31
Hello

If I boot windows Xp in my ubuntu and my ubuntu is connected to Internet. Will Windowx Xp be able to use ubuntu internet if a software that require internet is working in windows???


Thanks

---

### Post by carloslosgrande on 2007-03-31
Hi Phil90, I have XP running in VM and access the net thru Ubuntu just fine.

---

### Post by neogenesis213 on 2007-04-01
I also have the same problem as Wofl. I also have the wifi connection (ath0). VMware only works when i disable the bridge. But I can't access the internet inside my guest XP. Does anyone have a solution?

---

### Post by dany_r50 on 2007-04-01
How can I do to share data between the server host (ubuntu edgy) and the virtual machine (windows xp); The vmware server doesn't have the shared folder option (as vmware workstation). Thank you

---

### Post by yabbadabbadont on 2007-04-02
> **neogenesis213 said:**
> I also have the same problem as Wofl. I also have the wifi connection (ath0). VMware only works when i disable the bridge. But I can't access the internet inside my guest XP. Does anyone have a solution?

I don't remember where I read it, it may have been on the vmware forums or knowledgebase, but the vmware products cannont be bridged to a wireless connection, only wired ones.  (unless they have changed things in the last couple of months)

---

### Post by rooihond on 2007-04-03
Hi Dany_r50, I just setup a Samba share on the Ubuntu host side, and then access it from XP. I had to do that because I cannot get the XP side to see any USB stuff, and probably will have problem with the pcmcia under XP as well. Still trawling the forums and net for info...


> **dany_r50 said:**
> How can I do to share data between the server host (ubuntu edgy) and the virtual machine (windows xp); The vmware server doesn't have the shared folder option (as vmware workstation). Thank you

---

### Post by Dr. Cox on 2007-04-03
Hi there,

i've just tried to install vmware server using this guide.  i had to abort it in between though.  to be able to do it again i thought, hey, better delete all the files the install script has already written. unfortunately also the vmware-uninstall.pl script.
when i try to run the installer now, he complains about the missing file and i don't seem to be able to get him to install.

what do i have to do?

cheers

---

### Post by nickd916 on 2007-04-03
I have a probnlem at 

sudo ./vmware-install.pl

It asks to type in your password after this.  The problem is after i put that in it wont let me type my password in.  Can anybody help me?

---

### Post by Shampyon on 2007-04-03
> **nickd916 said:**
> I have a probnlem at 

sudo ./vmware-install.pl

It asks to type in your password after this.  The problem is after i put that in it wont let me type my password in.  Can anybody help me?

Are you sure it's not letting you type it in? It won't come up with asterisks when you type it into the terminal, it just stays blank as though you've typed nothing. That way no-one can even see how many characters you have in your password.

Type it in, press enter and it should work. If it doesn't, you've got a problem one of the more experienced members will have to help you with.

Good luck!

---

### Post by Ijump2 on 2007-04-03
VMware Server Console help needed (Ubuntu & VMware noob)...

I'm running Dapper with the 2.6.15-28-k7 kernal.  VM Server (v1.0.2.39867) installation went well and no problems running the config.pl file (thanks to the HowTO) but when I try to connect to "Local Host" in Console I get an error message that the local server is not installed or not currently running.


Where do I go from here?

---

### Post by m.musashi on 2007-04-03
> **Dr. Cox said:**
> Hi there,

i've just tried to install vmware server using this guide.  i had to abort it in between though.  to be able to do it again i thought, hey, better delete all the files the install script has already written. unfortunately also the vmware-uninstall.pl script.
when i try to run the installer now, he complains about the missing file and i don't seem to be able to get him to install.

what do i have to do?

cheers

Did you solve this yet? If not, you should probably run the uninstall script first to clear everything else out. Since it's gone, you might try downloading the installer again. I think the script is one of the extracted files. If not, you might be able to run the install and have it created. Also,
```
sudo rm -Rf /etc/vmware
```
will delete what's left after running the uninstall.

---

### Post by Shampyon on 2007-04-04
For those of you having trouble getting your proper XP partition working through VMWare, this might help:
[http://www.vmware.com/community/message.jspa?messageID=288743](http://www.vmware.com/community/message.jspa?messageID=288743)

---

### Post by ububug on 2007-04-07
I have a problem running VMWare.  I get this message.

> 
$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/share/themes/Glider/gtk-2.0/gtkrc:29: error: unexpected character `@', expected string constant


Does anybody know how to fix this?

EDIT: Found a fix. [http://www.zoxx.net/notes/index.php/2006/12/30/33-vmware-server-console-libpng-error-on-debian-gnu-linux](http://www.zoxx.net/notes/index.php/2006/12/30/33-vmware-server-console-libpng-error-on-debian-gnu-linux)

---

### Post by sp200606 on 2007-04-08
I don't know if this thread is still alive... but thanks anyway.
Here is my story:
I've been trying for a while to have vmware work on my Ubuntu box, but I always get this towards the end of the setup process:

###################BEGIN####################
In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-14-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
###################END####################

I just can't make it work???
I'm running  2.6.20-14-generic

Thanks for any help.

Stéphane POGGI

---

### Post by hoomant on 2007-04-10
Hi everyone,
Can I run my _**existing **Ubuntu 6.10_ on my Windows XP?

Thanks
Hooman

---

### Post by mmcmonster on 2007-04-10
Okay.  I'm trying to get this to work with fiesty.  I got to the part where it tries to build the kernel module, and then no go.  I know I had this working on Dapper on another computer, no no dice here.  Any help would be appreciated:

```

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-14-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

---

### Post by mssever on 2007-04-10
> **hoomant said:**
> Hi everyone,
Can I run my _**existing **Ubuntu 6.10_ on my Windows XP?

Thanks
Hooman

I'm sure you can, but I don't know an easy way to do it. An advanced method might be the following (I haven't tested this command; it might need to be adjusted): ```
cd /
sudo tar -cjpvf /path/to/external/device/old_system.tar.bz2 --exclude /proc --exclude /sys --exclude /dev --exclude /media --exclude /mnt --exclude /tmp .
```Then, on the vm machine, do a ```
cd /
sudo tar -xjvf /path/to/old_system.tar.bz2
```**WARNING:** Doing this will destroy your hardware settings! You'll have to manually fis them. A safer method would be to exclude /etc when you make the tarball, but you wouldn't get other settings, either. So you might end up going through /etc file by file.

---

### Post by dynacrylic on 2007-04-10
Awesome guide! 

Thanks so much for taking the time to make this.  It helped me a lot. I don't think I would have been able to do this without it.

---

### Post by David Valentine on 2007-04-10
I just got the same error as mmcmonster on feisty.  Has anyone succeeded in installing vmware server for feisty?

---

### Post by Kingedgar on 2007-04-11
> **David Valentine said:**
> I just got the same error as mmcmonster on feisty.  Has anyone succeeded in installing vmware server for feisty?

I found some information in this thread...

[http://www.vmware.com/community/thread.jspa?threadID=71986&tstart=0]("http://www.vmware.com/community/thread.jspa?threadID=71986&tstart=0")

The any-any update is at 109 now, and there is a link in the thread to another thread that sheds some more light.

This got me further than the first error, however, I still have not been able to install it fully. If someone with fiesty follows the link I posted and gets it to work, please post back


-Jason

---

### Post by absol_of_doom on 2007-04-11
i am running feisty and vm ware works perfectly.  However, I only have Xubuntu and Fedora Core 6 in it, so if the errors are related to having windows, i wouldn't know.
Edit: sorry im running vbox, not vm ware...

---

### Post by seanleblanc on 2007-04-13
I'm running Edgy and trying to get this to work.

What is running vmware supposed to do? Running the application from the menu just exits, so I ran the command-line. Initially, I got the errors about libpng.so and copied in gcc.so and libpng.so libs into the vmware/lib dir.

Now, when I run vmware it just sits there. Nothing happens. I cannot ctrl-C out of it, either?

---

### Post by brownknight on 2007-04-14
> **bluevoodoo1 said:**
> Does anyone have any ideas how to remedy this?

Im having the same problem too. Dont know how to remove the prior install. I removed it via sudo apt-get remove and also went into synaptic to totally remove vmware-player. :confused:

---

### Post by brownknight on 2007-04-14
> **brownknight said:**
> Im having the same problem too. Dont know how to remove the prior install. I removed it via sudo apt-get remove and also went into synaptic to totally remove vmware-player. :confused:

Found the answer: sudo rm -r /etc/vmware
This folder was left after the uninstall. After removing it, installation went on without a problem.

---

### Post by brownknight on 2007-04-14
> **gharz said:**
> i've been looking for the previous posts who experience the same problem with mine...

A previous installation of VMware software has been detected.

Failure

Execution aborted.

but i don't see any answer how to fix it.

initially, i installed vmware-player from synaptic until i found this forum. i removed vmware-player again from synaptic (complete removal) but i'm still getting the same message.

hope you could help me. i don't want to re-install my ubuntu because of this error message. i want my ubuntu to be the default OS on my laptop. windows is too bloated.

please help.

Had the same problem. Did this below:
**sudo rm -r /etc/vmware**
This folder was left after the uninstall. After removing it, installation went on without a problem.

---

### Post by goodtimetribe on 2007-04-14
> **mlind said:**
> Very nice guide, thanks!

I've been keen for some time to try VMWare on Ubuntu, but didn't have nerve to do
it yet.

I guess it's out of question to use already installed XP on VMWare ?

I haven't read the entire thread, but there's the VMWare Convertor tool that will convert your existing XP Machine into a VMWare machine so that you can "take it with you" after you switch the machine to Ubuntu.

It's actually exactly perfect for what I believe you're looking for. I haven't tried it yet, but HowToForge has a howto on it. lemme know if you can't find the link. please post your experience here :)

---

### Post by kc5hwb on 2007-04-14
I followed these instructions on the first page of this thread and all went well until I went to create a Virtual Machine.  While creating my virtual disk the  machines freezes up around 30-35% and I have to do a hard shut down/reboot in order to get it back.  Any ideas on why this is happening?

---

### Post by bullgr on 2007-04-16
i installed vmware using this howto and works perfect!!!
heavy apps like photoshop, coreldraw are working smooth and with no slowing down even in full screen!!!
now i can say that i have finally run perfect winblows xp on my ubuntu box.

my pc is a intel core2duo 6300 with 2gb ram. the settings i gave in the vitual session is 512mb ram, two cpu's
(yes you can give two cpu's if you have a dual core cpu), allocated the disk image space (about 15gb) to
run faster the virtual session and finally install the vmware tools after the win xp installation.

with this options (and of course the intel core2duo cpu) winblows xp run in native speed and never slowing down!!!

the intel core2duo cpu is important because intel (and amd in the new 64 cpu's) are included in the cpu command's (sorry about my english)
some command's for vitualisation performance support.
and this performance support are using vmware to get this great native speed.

don't search anything else... if you want to run any (and i mean it, ANY) winblows app in ubuntu with
the native speed, vmware is what you need.

i try also wine, but forget the heavy apps like photoshop. wine is goot for winamp and some like lightweight
apps.

i also try win4lin (cost's about 60 euro's), the installation was ok but the performance are poor even i the
pure environment of winblows, even the mouse pointer was moving slow.
win4lin uses the kqemu emulator (closed alternative from qemu with better performance), it is a software
emulator and don't use any hardware performance issues (like intel core2duo cpu).

and last some notes:
-for your local network give the bridget option and not NAT.
give a ip from the winblows tcp/ip options to get it to the network.

-to share files install and setup samba in ubuntu with your prefered options.
and please take care that you must config iptables to allow samba go thru.
if you don't that, you can't see the ubuntu shares (this took me two hours to figure it out).

---

### Post by Shampyon on 2007-04-17
Here's an odd question for y'all.

You've heard of those [WIndows XP Portable]("http://www.tomshardware.com/2005/09/09/windows_in_your_pocket/") installations? The ones that are designed to run on a USB stick? Most are stripped down to be less that 200MB.

Is it possible to get one running in VMWare, either directly from the USB drive or (preferably) installed to the virtual disk?

---

### Post by drdnl on 2007-04-17
To those of you having issues in Feisty with the vmmon module (mcmonster? too lazy to go back and check)

download and run the "any-any" patch which can be found here: [http://knihovny.cvut.cz/ftp/pub/vmware/](http://knihovny.cvut.cz/ftp/pub/vmware/)

as of 17-04-2007 the direct link would be [http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update109.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update109.tar.gz)

Now your vmware will work perfectly fine. Well, it did for me (7.04 i386)

---

### Post by mmcmonster on 2007-04-17
Thanks for the help.  I'm still having problems, though. :-( :
```

$ sudo ./runme.pl 
Updating /usr/bin/vmware-config.pl ... now patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV321]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1522: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1523: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV3]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1522: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1523: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageGSX1]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1522: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1523: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV2]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1522: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1523: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM_V4(VMDriver*, Vcpuid) [with VMCrossPage = VMCrossPageV4]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMDriver*, Vcpuid)’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1522: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1523: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘void Task_Switch_V45(VMDriver*, Vcpuid)’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
The module loads perfectly in the running kernel.

mknod: `/dev/vmmon': File exists
Unable to create the character device /dev/vmmon with major number 10 and minor
number 165.

Execution aborted.

$ ls -l /dev/vmmon
ls: /dev/vmmon: No such file or directory
$ 
```

---

### Post by mmcmonster on 2007-04-17
I take my previous post back. :-) I ran the same command in the same window again, and the second time it worked. (*shrug*)

P.S. Works fine!  Thanks!

---

### Post by UltraM4n on 2007-04-17
Hi there. I just installed VMWare Server on Ubuntu version 6.10
Everything runs smooth on installation. But..when i go to run it, i see it starting in the little bar at the bottom of the screen, but it goes away and never comes back. So i check the process at it says its running :S
Can anybody help me?

---

### Post by m.musashi on 2007-04-17
Type "vmware" in a terminal and post the output. If it isn't starting that should show what the errors are.

---

### Post by UltraM4n on 2007-04-17
this is what came up
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

---

### Post by m.musashi on 2007-04-17
Well, now we know what may be causing the problem but I don't have a clue how to fix that. I was hoping for a permission problem or something easy.

Maybe wait and see if anyone else has any ideas.

Here is a thread that might help [http://ubuntuforums.org/showthread.php?t=408559](http://ubuntuforums.org/showthread.php?t=408559)

---

### Post by carloslosgrande on 2007-04-17
Hey BrownKnight, I was stuck at the same problem and that fixed it for me, Thanks! 

So I decided to add it to my 'howto' and right there in black n white was same thing. I'd be embarrassed but I'm getting used to it now.

---

### Post by carloslosgrande on 2007-04-17
I've got the same problem as McMonster and I ran the install and the fix install (ie the any-any file) twice both times I got the same error code
Finally tried one more time on each and voile! its all installed
thanks guys.

---

### Post by mmcmonster on 2007-04-18
> **UltraM4n said:**
> this is what came up
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

I'm not in front of my Ubuntu machine right now, but I think I get this warning when I run vmware from a terminal prompt, so it's not the cause of the hanging process.  Maybe you can `killall vmware` or something similar to make sure you aren't running any vmware processes (a reboot would also work) and then run it in a terminal to see what happens?

---

### Post by UltraM4n on 2007-04-18
Nevermind, thank god for ubuntus built in iso maker :D

---

### Post by arunsub on 2007-04-20
My webcam is not working. How do I make my webcam work?

Thanks.

---

### Post by diablo69er on 2007-04-25
OK--I am getting tired of this.  I have a FRESH install of Feisty and I was following the tutorial word for word, and I always get this error.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.


Is there ANY way to fix this?

---

### Post by diablo69er on 2007-04-25
> **diablo69er said:**
> OK--I am getting tired of this.  I have a FRESH install of Feisty and I was following the tutorial word for word, and I always get this error.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.


Is there ANY way to fix this?

Gheh--see this link to see how I fixed my own problem.

[http://www.go2linux.org/node/30](http://www.go2linux.org/node/30)

---

### Post by carloslosgrande on 2007-04-25
I finally got VMWare installed last week, thanks to the help here and using the 'vmware-any-any' fix.
Due to an overabundance of confidence I also tried the 'desktop effects' option and it made Feisty unworkable again. So another fresh install - this time of the latest release - and now vmware-any-any is giving me this error;

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config3/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

I've looked for cc1plus in synaptic but no go. Any ideas what it is and where I can find it?

I googled it and found some entries for in it debian forums and they talked of adding gcc-g++ the C+ compiler.
I've added this but no difference
Thanks.

---

### Post by drmbogo on 2007-04-27
> **diablo69er said:**
> Gheh--see this link to see how I fixed my own problem.

[http://www.go2linux.org/node/30](http://www.go2linux.org/node/30)

Thanks diablo69er! This worked!

All you need from that link is the link to the patch:
[http://jaws.go2linux.org/archivos/vmware-any-any-update109.tar.gz](http://jaws.go2linux.org/archivos/vmware-any-any-update109.tar.gz)

Extract, cd to extracted directory and:
sudo ./runme

it patches the vmware.config.pl file and runs it.
Lovely :))

---

### Post by cacharreo on 2007-04-28
Still doesn't work for me
 I run the script from [http://jaws.go2linux.org/archivos/vmware-any-any-update109.tar.gz](http://jaws.go2linux.org/archivos/vmware-any-any-update109.tar.gz)

I I still gets the next errors:

jaime@eliux:~/vmware-any-any-update109$ sudo ./runme.pl
Updating /usr/bin/vmware-config.pl ... already patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: se ingresa al directorio `/tmp/vmware-config5/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config5/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config5/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config5/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No existe el fichero ó directorio
make[2]: *** [/tmp/vmware-config5/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config5/vmmon-only] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: se sale del directorio `/tmp/vmware-config5/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


Some idea more? :confused: :confused: :confused:

---

### Post by veloce on 2007-04-28
Don't know if I can be much help as your error messages are in a language I don't understand.  It seems to be having difficulty creating a directory?  

One other thing to try is to upgrade vmware to version 1.0.2 - it may be a fixed bug.

---

### Post by nivosh on 2007-04-28
hello.
it is stated that virtual machine will not work with hardware that is not identified with ubuntu, but what about a printer that works just with windows driver but **is** identified by ubuntu?

i have USB lexmark X6170 that ubuntu recognize but without a proper linux driver.
will my printer work through the virtual machine?

thank

---

### Post by yabbadabbadont on 2007-04-28
> **nivosh said:**
> hello.
it is stated that virtual machine will not work with hardware that is not identified with ubuntu, but what about a printer that works just with windows driver but **is** identified by ubuntu?

i have USB lexmark X6170 that ubuntu recognize but without a proper linux driver.
will my printer work through the virtual machine?

thank

Good question.  I would guess that it would work.  Since Ubuntu can identify it, it means that there isn't a problem talking to it through the USB connection.  It is just that Ubuntu doesn't know how to "speak the printer's native language."  As long as the VM can talk to it over the USB bus, it should work.  I have a Canon photo printer that is in the same boat.  I'll have to setup a VM and see if I can print to it from inside the emulator.

---

### Post by carloslosgrande on 2007-04-28
Veloce, I get the same error message as Cacharreo and the error is 'gcc: error trying to exec 'cc1plus': execvp: (No existe el fichero ó directorio) _file or directory don't exist_

I actually had VMWare working on the version of Feisty prior to the official release. Then I played with 'desktop effects' and it killed everything so I reinstalled with the official release and now i can no longer get VMWare working. This cc1plus file seems to have been something to do with Debian from what I can see on google but I don't know where to get it from or, more importantly, why it seems to be no longer a part of Feisty?

---

### Post by Queen_Kira on 2007-04-28
thanks the guide ^^

---

### Post by veloce on 2007-04-29
> **carloslosgrande said:**
> Veloce, I get the same error message as Cacharreo and the error is 'gcc: error trying to exec 'cc1plus': execvp: (No existe el fichero ó directorio) _file or directory don't exist_

I actually had VMWare working on the version of Feisty prior to the official release. Then I played with 'desktop effects' and it killed everything so I reinstalled with the official release and now i can no longer get VMWare working. This cc1plus file seems to have been something to do with Debian from what I can see on google but I don't know where to get it from or, more importantly, why it seems to be no longer a part of Feisty?

I upgraded to Feisty from Edgy, used the "any to any" patch and config worked perfectly.  So maybe something is carrying over from Edgy.  

I found it in folder:

 /usr/lib/gcc/i486-linux-gnu/4.1.2

Don't know what package it would come in.

---

### Post by carloslosgrande on 2007-04-29
Yeah, I've got the 'any any' package and with the earlier Feisty i had to use it twice and the 'vmware-server' package twice, ie v-s, a-a, v-s, a-a, and then everything worked. I've tried this  more times than i can count now and it always has this error re cc1plus
I don't have any carryover from Edgy because I haven't had Edgy. I went from Dapper to Feisty.

---

### Post by veloce on 2007-04-30
> **carloslosgrande said:**
> Yeah, I've got the 'any any' package and with the earlier Feisty i had to use it twice and the 'vmware-server' package twice, ie v-s, a-a, v-s, a-a, and then everything worked. I've tried this  more times than i can count now and it always has this error re cc1plus
I don't have any carryover from Edgy because I haven't had Edgy. I went from Dapper to Feisty.

I think you need to (re) install the "build-essentials" package.  Saw this on a vmware list.

---

### Post by nivosh on 2007-05-01
> **yabbadabbadont said:**
> Good question.  I would guess that it would work.  Since Ubuntu can identify it, it means that there isn't a problem talking to it through the USB connection.  It is just that Ubuntu doesn't know how to "speak the printer's native language."  As long as the VM can talk to it over the USB bus, it should work.  I have a Canon photo printer that is in the same boat.  I'll have to setup a VM and see if I can print to it from inside the emulator.

I SUCCEDED!!! the lexmark X6170 printer now works under ubuntu from within the virtual windows machine.

this is great news for those with not working printers due to lack of linux driver!

and now for another quastion.
would someone please help me with the network and internet connection in vmware player.
i have one ethernet card in which i connect with cable. the internet is working fine in ubuntu.
how can i configure networking inorder to ba able to share folders with the host (ubuntu) and to be able to surf the net from the guest (windows XP)?
the network adaptor is on - nat and VMplayer sayes it's connected, but no internet and no networking available.
i installed samba and shared the folders i want.
what next?

---

### Post by veloce on 2007-05-01
> **nivosh said:**
> I SUCCEDED!!! the lexmark X6170 printer now works under ubuntu from within the virtual windows machine.

this is great news for those with not working printers due to lack of linux driver!

and now for another quastion.
would someone please help me with the network and internet connection in vmware player.
i have one ethernet card in which i connect with cable. the internet is working fine in ubuntu.
how can i configure networking inorder to ba able to share folders with the host (ubuntu) and to be able to surf the net from the guest (windows XP)?
the network adaptor is on - nat and VMplayer sayes it's connected, but no internet and no networking available.
i installed samba and shared the folders i want.
what next?

So your virtual windows machine is printing to an unsupported printer on the host?  Cool!  I must try this myself.

Networking: Some questions:
how are you connected to the internet? Is there a firewall somewhere?
how is your vm getting an IP address? 

If you have networking working between the vm and host (samba file sharing) then this should be simple.

---

### Post by nivosh on 2007-05-02
> **veloce said:**
> So your virtual windows machine is printing to an unsupported printer on the host?  Cool!  I must try this myself.

Networking: Some questions:
how are you connected to the internet? Is there a firewall somewhere?
how is your vm getting an IP address? 

If you have networking working between the vm and host (samba file sharing) then this should be simple.

yes, i was very pleased to find out that my printer is printing...

regarding the networking.
i am using cable as my internet provider. i have firewall on my guest system (win xp pro)
i have installed samba and shrad the folders in my host.
the virtual network in configured as NAT and is connected.
but there is no internet through the guest machine and i cant fined the shared folders in the guest.
maybe i should do reinstalation of vmplayer?

---

### Post by veloce on 2007-05-02
You might want to switch to vmware server.  It's now included in the feisty repository so should be an easy switch.

---

### Post by computerjunkie on 2007-05-02
My computer crashed and i just got it back so I reinstalled dapper and am now again trying to isntall vmware server, everything went fine, except after the install completed i tried to run it and it responded with "cannot launch menu item" Details: failed to execute child process "vmware" (no such file or directory)


Terminal output:

"chris@voyager:~$ sudo vmware
sudo: vmware: command not found
chris@voyager:~$ vmware
bash: vmware: command not found"


um help.

---

### Post by veloce on 2007-05-02
Did you run vmware- config ?

---

### Post by computerjunkie on 2007-05-02
chris@voyager:~$ vmware-config
bash: vmware-config: command not found

After the installer finished it said everything was successful. what happened?

---

### Post by veloce on 2007-05-02
Try

```
sudo /usr/bin/vmware-config.pl
```

---

### Post by computerjunkie on 2007-05-03
chris@voyager:~$ sudo /usr/bin/vmware-config.pl
Password:
sudo: /usr/bin/vmware-config.pl: command not found

i'm really confused. The installer said everything went fine, and an icon appears for vmware server in the applications>>system tools menu, and I know where I installed the files (/home/chris/vmware) but none of these commands are working.

---

### Post by Jad on 2007-05-03
installation went fine but File -> New -> Virtual machine is disabled, any idea?

---

### Post by Tarquin on 2007-05-04
Thanks for the walkthrough, but I cannot get mine to install. I alsways get this message:

> Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

I have made sure I have access to that folder & the files in it, but nothing seems to work.
Now I am pretty much a n00b when it comes to Linux in general, I only know what a friend has been telling me over the last couple of weeks, so I guess it could be something stupid!

Many thanks in advance for any help though.

Tarq

---

### Post by computerjunkie on 2007-05-06
I really need help with this. You guys think I shoudl try to reinstall vmware accepting all of the defualt options? Some things I really want to use I cant get to work in a natural linux environment. maybe reinstalling will work, idk.

---

### Post by computerjunkie on 2007-05-06
well I tried reinstalling and accepted all default options 

--start output--
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                         done
   Bridged networking on /dev/vmnet0                             done
   Host-only networking on /dev/vmnet1 (background)       done
   Host-only networking on /dev/vmnet8 (background)        done
   NAT service on /dev/vmnet8                                        done

The configuration of VMware Server 1.0.3 build-44356 for Linux for this running
kernel completed successfully.
--end output--

But it gives me the same errors. what in the world is going on!?

---

### Post by Ashex on 2007-05-07
If you are having trouble getting vmware server installed, you will need to install the vmware-anyany109 patch, which you can get here:
[http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

extract it and run the update script runme.pl, then run the vmware-config script and you should be fine.

If you still have trouble, reinstall vmware by doing a sudo apt-get dpkg --purge vmware-server
Then manually delete the directory /etc/vmware, then install vmware-server again. But when it gets to the step where it asks if you want to run the configuration script, say no and apply the patch.

---

### Post by drmbogo on 2007-05-07
> If you are having trouble getting vmware server installed, you will need to install the vmware-anyany109 patch, which you can get here:
[http://ftp.cvut.cz/vmware/vmware-any...date109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any...date109.tar.gz)


Just a note:
I wasn't able toget the file from the above location (server timed out; busy, I imagine:))
I found it here:
[http://jaws.go2linux.org/archivos/vmware-any-any-update109.tar.gz](http://jaws.go2linux.org/archivos/vmware-any-any-update109.tar.gz)

---

### Post by computerjunkie on 2007-05-07
Why does this keep saying command not found!!!!! ARG....

--start--
name@domain:~$ vmware
bash: vmware: command not found
name@domain:~$ sudo vmware
sudo: vmware: command not found
name@domain:~$ bash -l
name@domain:~$ vmware
bash: vmware: command not found
name@domain:~$ sudo vmware
sudo: vmware: command not found
--end--

Alright I'll try the purge thing, thanks for the help.

--start--
name@domain:~$ sudo apt-get --purge vmware-server
E: Invalid operation vmware-server
--end--

---

### Post by veloce on 2007-05-08
> **computerjunkie said:**
> Why does this keep saying command not found!!!!! ARG....

--start--
name@domain:~$ vmware
bash: vmware: command not found
name@domain:~$ sudo vmware
sudo: vmware: command not found
name@domain:~$ bash -l
name@domain:~$ vmware
bash: vmware: command not found
name@domain:~$ sudo vmware
sudo: vmware: command not found
--end--

Alright I'll try the purge thing, thanks for the help.

--start--
name@domain:~$ sudo apt-get --purge vmware-server
E: Invalid operation vmware-server
--end--

I can't figure out what's going on with your system.  It looks like you only have the vmware services installed, not the graphical console.   

Let's go back to the start.
1. From the vmware site, get a serial number.
2. From the vmware site, download the package: VMware-server-1.0.3[etc] .tar.gz 
3. Unpack the package to, say, a directory on the desktop
4. Change to the directory you created and run the installer
5. Use synaptic package manager to upgrade the kernels for Feisty.

VMware services will be started automatically.  To run the console, a menu item should be under Applications-System Tools (though mine got lost when I upgraded to Feisty). So I. as you were doing, start from the console or a short cut.

So, is there anything in there that doesn't sound familiar?

---

### Post by el_poderoso on 2007-05-11
I set it up NAT, tried bridged connections, direct connections to my DSL, but no luck. Gimme a clue?

---

### Post by mlind on 2007-05-11
hiya, thanks for the nice howto!

You might add to the tips section that Feisty users (and ppl with newer kernels) need to use the "vmware-anyany109 patch" to complete the installation. x64 users may also need **ia32-libs** package installed (at least I did) to complete private network setup part.

---

### Post by aspen on 2007-05-18
hi, 

this howto works fine on my girlfriend`s pc with dapper drake. And there are no Problems at all.
i get connections from the vm-client to the host system and to any other pc in our network (samba, ftp, http, ssh ...)

I`m on Feisty and i have some problems to get a connection from the vm-client to the host system.
i followed this howto and it worked out of the box,
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

but i`m not able to establish a connection to the host system, either via samba or ssh.
the vmware-server logfile looks ok, no errors or something like that.

does anybody has a similar problem or such strange behavier?

the clients are working in bridged mode and are able to connect to the internet or stuff like that, but is not able to get a connection to the vmware.server.

thx
aspen

---

### Post by TabletGuy on 2007-05-18
The easiest way to install VMserver these days is with the version in the Canonical commercial repository.

Instructions are here:
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")

---

### Post by veloce on 2007-05-18
> **aspen said:**
> hi, 

this howto works fine on my girlfriend`s pc with dapper drake. And there are no Problems at all.
i get connections from the vm-client to the host system and to any other pc in our network (samba, ftp, http, ssh ...)

I`m on Feisty and i have some problems to get a connection from the vm-client to the host system.
i followed this howto and it worked out of the box,
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

but i`m not able to establish a connection to the host system, either via samba or ssh.
the vmware-server logfile looks ok, no errors or something like that.

does anybody has a similar problem or such strange behavier?

the clients are working in bridged mode and are able to connect to the internet or stuff like that, but is not able to get a connection to the vmware.server.

thx
aspen

When you install from the repositories, it sets up three virtual networks:
bridged
nat
host only

If you want your vms to talk to your host, then they should have a virtual network card connected to the host only network.  

If you want them to talk to both the host and other machines on the network, and your network has a dhcp server, then you can connect the vms to the nat network.

If you only want your vm to access machines other than the host, then use bridged.

(I have a virtual firewall connected to the bridged and host only network, and my other vms connected to the host only network.)

---

### Post by aspen on 2007-05-19
hiho, 

thx 4 the quick reply veloce!

i got it working now, 
i switched the vm client which is hosted on my ubuntut 7.04 to NAT networking and it worked.
now i`m able to connect to the host system via smb, ftp or ssh without having any trouble.
but therefor i have some issue to get connections to other hosts on the network. internet is working fine, but browsing the network is tricky. if i now want to map a networkshared to the vm hosted on my ubuntu 7.04 i have to write down the "FQDN" of the host.

for exampel:
my girlfriends pc (dapper drake)... she just boots her vm client in bridged mode and has every service available provided from our network.

if i boot my vm clients, they are working in NAT mode, i`m able to surf the web, able to connect to the host system, but if i want to map a shared i have to type e.g. \\marla\clarkconnect.lan\shared
 and not as my girlfriend just \\marla\shared.

i also had to manual add the dns from our network as a second dns entry in my vm-clients to reach services on other mashines in our network.


anyway, i`m glad now that i got it working with your help, even it`s not the same way as it was on dapper drake.


update:
i added the dns-suffix and wins from our netweork to the  vm client, and now everything seems to work as it was before on dapper, except that my mashine is working in nat mode than in bridged mode :)

thx again
aspen

---

### Post by dbulante on 2007-06-01
My vmware did not run properly.  Instead, it gave me the following error messages.  Please help.

shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

---

### Post by veloce on 2007-06-02
what version of ubuntu, and vmware server are you running?  

how did you install vmware?  did you get any errors there?

---

### Post by doublehard on 2007-06-06
ARGGGGG THIS IS DRIVING ME MAD!!!!!!

I stumbled across this thread and thought it look fantastic so i'd give it a go. Downloaded and ran the script etc but couldn't get the install to work, it got about halfway through then returned an error. So I had a bit of a dig around and found that VMware is available on the Synaptic manager, so I thought that would be the best way to go. Selected the install, and it finds the previous attempt and tells me to uninstall it or 'purge' it. But as i've not managed to install it fully it looks like I can't uninstall it!!!

example:

andy@Our-PC:~$ sudo apt-get remove --purge vmware-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vmware-server is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andy@Our-PC:~$ 

I've tried the uninstall

andy@Our-PC:~/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/andy/vmware/vmware-uninstall.pl.

Failure

Execution aborted.

andy@Our-PC:~/vmware-server-distrib$ 



Any ideas?

---

### Post by mitch.c on 2007-06-06
My install/uninstall problems have always been solved by:
```
$ sudo rm -rf /etc/vmware
```
YMMV

Good luck

---

### Post by doublehard on 2007-06-06
Thanks, i've sorted it now. I searched for vmware and removed all references that I could find then wen into synaptic to install vmware server. I've just finished installing windows and it looks pretty good.

I'm having another problem now, all my media is on my external hard drive, I've installed windows onto the same external hard drive in a partition. How do I get windows to see the files I've got on the same hard drive in a different partition?

---

### Post by veloce on 2007-06-07
> **doublehard said:**
> Thanks, i've sorted it now. I searched for vmware and removed all references that I could find then wen into synaptic to install vmware server. I've just finished installing windows and it looks pretty good.

I'm having another problem now, all my media is on my external hard drive, I've installed windows onto the same external hard drive in a partition. How do I get windows to see the files I've got on the same hard drive in a different partition?

Be VERY careful here.  You must never have the host and vm directly accessing the same hard disk! 

The best way to share information between them is to use the host only virtual network and samba.

---

### Post by eaudet on 2007-06-07
> **Peturrr said:**
> Are you too having problems with software that is only available on Windows and not on Linux? Are you still Dual Booting to solve this problem? After this HowTo you will never need to dual-boot again for your windows only software, like Adobe CS!


[SIZE=4]**Info[SIZE=6][SIZE=3][SIZE=2][/SIZE][/SIZE][/SIZE] **[/SIZE] That sounds great, but how?
Did you ever heard about Virtual Machines? There is software available that can run Windows XP or any other Operating System inside your main Operating System. This means that you can run Windows XP in Ubuntu without the need to Reboot/Dual Boot. 

That sounds slow...
It is indeed a little slower, but really: a little. Personally I am very willing to sacrifice that little speed in order to avoid Dual Booting.

What else can I do with it?
Run seperate Operating Systems for Online Banking and other things that you want to secure. Try out new Ubuntu Versions without Dual Booting, Try out other Linux Distro's etc. 

What can I **not** do with it?
You will not be able to use hardware that doesn't work on Ubuntu. This is very important to understand!
The Virtual Machine runs on top of Ubuntu, so it can only acces Ubuntu detected devices. It is a virtual machine with virtual hardware. 

Also don't expect to be gaming on a Virtual Machine at this moment. Heavy Videocard 3d things are just not supported right now. So for gaming it's unfortunately a no go. For everything else, just try it out!


[SIZE=4]**Requirements**[/SIZE][LIST]
[*]Ubuntu Edgy, Dapper or Breezy
[*]A Windows (XP) Installation CD & Key
[*]Internet Connection (+- 100 Megabyte file download)[/LIST][SIZE=4][B]
Procedure[/B][/SIZE] 
First we need to install a few dependencies:

In a terminal type
```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
``` This will install all needed dependencies (atleast I hope so ;) )

Breezy users will also need to install gcc-3.4. 
```
sudo apt-get install gcc-3.4
```We are now ready to download VMWare Server.[LIST]
[*]Go to [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
[*]On the menu on the right click: Download VMWare Server
[*]Click on the appropriate Download Now button.
[*]Register as new user, do give a valid email adres, since you will be receiving the registration key by email.
[*]Select the VMWare Server beta (for Linux)
[*]Accept the EULA
[*]Download VMware Server for Linux. (first mentioned, binary (.tar.gz) )[/LIST]The Installation[LIST]
[*]Open the downloaded file with the archive manager.
[*]Extract it to somewhere, I will use /tmp here.
[*] Startup the terminal and go to the extracted files 
```
cd /tmp * replace with your download directory*
cd vmware-server-distrib
```[LIST]
[*][LIST]
[*]**Breezy users only.** Execute ```
export CC=/usr/bin/gcc-3.4
```[/LIST] [/LIST] 
[*]Execute the installation script 
```
sudo ./vmware-install.pl
```
[*]You can accept all defaults, only thing you might want to alter is the directory where the Virtual Machines are stored. I have mine set to /home/username/vmware . But offcourse, just accept the settings you want to.
[*]You will be prompted for your key during the installation. You will find the key in your email inbox
[*]If everything went allright, the installation will finish without any problems[/LIST]We can now test if it worked by starting the VMWare server console[LIST]
[*]Via the menu Applications => System Tools => Vmware Server Console
[*] If everything is allright, the server console program will show up.
[*]If it didn't, start the terminal and execute ```
vmware
```This will display the errors, post them here and hopefully we can solve them.[/LIST]Next thing we want to do is Install Windows (XP) !

First we need a virtual machine[LIST]
[*] Insert your Windows (XP) CD into your CDROM drive
[*] Open the VMware Server Console
[*] select 'Create a new virtual machine'
[*] => Next => Next => Select Windows Xp (or whatever Windows versions you want to install  )
[*]=> Next => Enter a name and select a location for the Virtual Machine File (It contains the virtual harddisk, so it needs quite some space, min 2 GB, but I would recommend 8+ GB )
[*] => Next => Select Network type. I am using NAT, but choose whatever fits you ( or your mood  )
[*]=> Next => Choose the size for the Virtual Disk and set other preferences
[*] => Next => Finish[/LIST]Now we can start the newly made virtual machine and the install of Windows![LIST]
[*] Start the virtual machine
[*] Hopefully it detects your Windows install CD and will start the installation! If it won't boot from the CD, stop the virtual machine and check/change the preferences for the virtual machine regarding the CD drive
[*] Enjoy the installation and the freedom to use Ubuntu while installing :D[/LIST][SIZE=4][B]
Tips

[/B][/SIZE] You will definately want to install the VMWare tools, when windows has been installed. This will **speed up your Windows responsiveness **[LIST]
[*] Make sure your Windows Virtual Machine is Running and visable/selected. (Not in FullScreen)
[*] Go to the VM menu (on the top in the VM Server Console)
[*]Select Install VMWare Tools. 
This will start a installation wizard in your WIndows Environment. Just install the stuff and you will have better mouse and system responsiveness.[/LIST]CTRL + ALT will **release the mousecursor **from the virtual machine
CTRL + ALT in FullScreen mode will get you **out of the FullScreen**.

You can Suspend a running virtual machine. this way it will start very fast the next time you need it.

To have **sound support**, add a sound device in the virtual machine settings.

**Enjoy!**

See Attached screenshots from my windows XP Installation and the succes of it.

Please no discussions about Windows versus Linux in this Thread.


[B][SIZE=4]Common Problems & Solutions[/SIZE]
[/B][LIST]
[*]No Serial Number Received[/LIST][INDENT][INDENT]You can view your serial numbers at: [http://www.vmware.com/vmwarestore/newstore/serial_number_login.jsp](http://www.vmware.com/vmwarestore/newstore/serial_number_login.jsp)[/INDENT][/INDENT][LIST]
[*]After a kernel upgrade VMWare won't start because it *** has not been (correctly) configured for the running kernel***[/LIST][INDENT][INDENT]execute ```
sudo /usr/bin/vmware-config.pl
```[/INDENT][/INDENT][LIST]
[*]vmware-config.pl fails to find the right kernel headers. **It cannot find /usr/src/kernel/include** and won't proceed to install.[/LIST][INDENT][INDENT]You have a updated kernel, but not the updated kernel headers. 
You can install them by executing ```
sudo apt-get install linux-headers-`uname -r`
``` Now you can succesfully run ```
sudo /usr/bin/vmware-config.pl
```[/INDENT][/INDENT][LIST]
[*]You don't want to install the kernel headers manually each time there is an update.[/LIST][INDENT][INDENT]There is a package called linux-headers-*** that automatically installs the latest kernelheaders, so you don't need to install them manually each time.

There are 4 flavours of this package: 386, 686, k7, server.

If you don't know wich one you need, execute ```
uname -r
``` It will give you something like 2.6.15-26-**k7** or 2.6.15-26-**686**

Now you know the right flavour, install it by ```
sudo apt-get install linux-headers-*****
``` Replace the *** with 386, 686, k7 or server.
    
[/INDENT][/INDENT][LIST]
[*]**Uninstallation failed** and reinstall won't work  
====
A previous installation of VMware software has been detected.
 The previous installation was made by the tar installer (version 3).
 Keeping the tar3 installer database format.
 Error: **Unable to execute "/usr/bin/vmware/vmware-uninstall.pl.**
 Failure
    ** Execution aborted.**
====[/LIST][INDENT][INDENT]Look for the /etc/vmware directory and either move it to a different location or remove it altogether. ```
sudo rm -R /etc/vmware
``` [/INDENT][/INDENT][B]
 [SIZE=4][SIZE=4]Note
[/SIZE][/SIZE][/B]According to Flip314: [B]

[SIZE=4][SIZE=4] Credits
[/SIZE] [/SIZE][/B] Used some information from a blogpost by James Wilford and a comment placed there by 'mips' ([http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu](http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu) )
Thanks to Remusus for the linux-headers-'uname -r '  command.
Thanks to firetux for the GCC-3.4 info
Thanks to Nick Couchman from the VMWare forum for the uninstallation problems workaround.

:KS

Thank you for spending the time to write all this.

Cheers!

---

### Post by mrynit on 2007-06-10
are these instructions still valid with feisty fawn? if so maybe the OP could say that it is b/c its over a year old and im not sure if it is still use able

---

### Post by veloce on 2007-06-10
> **mrynit said:**
> are these instructions still valid with feisty fawn? if so maybe the OP could say that it is b/c its over a year old and im not sure if it is still use able

Still usable but is not necessarily the best method of installing vmware server under Feisty.  VMware server is now in the commercial repository and this is, arguably, the best way.  From my notes:

> VMWare Server is now in the commercial repository for Feisty.  Had to add the commercial repo. to the file /etc/apt/sources.list:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

Full howto:
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)


---

### Post by mrynit on 2007-06-10
i followed the instructions but windows says it cannot find any hard drives to install on.

---

### Post by veloce on 2007-06-11
> **mrynit said:**
> i followed the instructions but windows says it cannot find any hard drives to install on.

> First we need a virtual machine

    * Insert your Windows (XP) CD into your CDROM drive
    * Open the VMware Server Console
    * select 'Create a new virtual machine'
    * => Next => Next => Select Windows Xp (or whatever Windows versions you want to install )
    * => Next => Enter a name and select a location for the Virtual Machine File (It contains the virtual harddisk, so it needs quite some space, min 2 GB, but I would recommend 8+ GB )
    * => Next => Select Network type. I am using NAT, but choose whatever fits you ( or your mood )
    * => Next => Choose the size for the Virtual Disk and set other preferences
    * => Next => Finish

You must have made a mistake creating the virtual hard drive in this section. In vmware server console, with the vm off, check that your vm has an appropriate sized hard drive.

---

### Post by superFerra on 2007-06-11
Hi everybody,
i'd like to ask you few questions about VMware server and windoes XP:

I'm running an Fiesty Fawn (great system), i've installed vmware server from commercial repositories, installed Windows XP pro without any big issue (yes i'm luky till now).
Installed correcly VMWare Tools then:

1- Is it possible to customize desktop available resolutions? 
I've forced into Windows XP vmware image something like svga.maxHeigth ="720"  because my mointor native resolution is 1280x720 but every time Windows boot desktop resolution is switched down to 1040x478 (or simethig like that) then i've to go to display setting and set back 1280x720.
Is there a way to force 1280x720 only?

2- I'd like to allow my virtualized windows to access a physical NTFS partition. To achieve this i had to add my user to "disk" group.
-Is it dangerous to allow windows and ubuntu access to a partition togheter? Will it result into a data loss? (Yes my HOST os Ubuntu is mounting R/W that NTFS partition too)
-I read that it's not secure to add a user to disk group. Is there a workaround?

3- Is there a way to completerly stop VMWare server service? Running "sudo /etc/init.d/vmware-server stop" seems to not stop it completely.

Thanks In Advance

---

### Post by Stefaan on 2007-06-11
Hi,

Can sb help me pls?

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:80:
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by Merk42 on 2007-06-11
Well I made a big mistake and closed the terminal before it was done installing, I thought I made a mistake so I figured I'd close it and retype ./vmware install.pl   unfortunately when I do:

```
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

Unable to find the answer INITSCRIPTSDIR in the installer database 
(/etc/vmware/locations). You may want to re-install VMware Server.

Execution aborted.

Failure

Execution aborted.

```

---

### Post by veloce on 2007-06-11
> **superFerra said:**
> Hi everybody,
i'd like to ask you few questions about VMware server and windoes XP:

I'm running an Fiesty Fawn (great system), i've installed vmware server from commercial repositories, installed Windows XP pro without any big issue (yes i'm luky till now).
Installed correcly VMWare Tools then:

1- Is it possible to customize desktop available resolutions? 
I've forced into Windows XP vmware image something like svga.maxHeigth ="720"  because my mointor native resolution is 1280x720 but every time Windows boot desktop resolution is switched down to 1040x478 (or simethig like that) then i've to go to display setting and set back 1280x720.
Is there a way to force 1280x720 only?

2- I'd like to allow my virtualized windows to access a physical NTFS partition. To achieve this i had to add my user to "disk" group.
-Is it dangerous to allow windows and ubuntu access to a partition togheter? Will it result into a data loss? (Yes my HOST os Ubuntu is mounting R/W that NTFS partition too)
-I read that it's not secure to add a user to disk group. Is there a workaround?

3- Is there a way to completerly stop VMWare server service? Running "sudo /etc/init.d/vmware-server stop" seems to not stop it completely.

Thanks In Advance

1. Resolutions: you might like to try using rdp to access your vms.  gnome rdp allows you to specify the resolution you would like - I used it to be just a bit smaller than my screen to allow for the window frame. Over the host only virtual network it is fast.

2. YES it is dangerous.  VMWare has big warnings about it.  Better to set up a samba share under ubuntu and allow the vm access over the host only virtual network.

3. I don't think so, but if you are not using it ubuntu will swap it out to disk so there's no performance penalty.

---

### Post by veloce on 2007-06-11
> **Stefaan said:**
> Hi,

Can sb help me pls?

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:80:
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Either:

[LIST=1]
[*]uninstall vmware server and install from the commercial repository. search: vmware commercial repository
[*]download and install the any-any patch. search: vmware patch
[/LIST]

---

### Post by superFerra on 2007-06-12
@veloce: Many thanks!!

2: Yes it's dangerous!! I did a simple test and tried to access the partition concurrently and it messed up everything. I think i'll move to a samba share solution.

Is there a tutorial that explain how to tweak vmx files? 

Cia'

---

### Post by eentonig on 2007-06-14
> **veloce said:**
> Either:

[LIST=1]
[*]uninstall vmware server and install from the commercial repository. search: vmware commercial repository
[*]download and install the any-any patch. search: vmware patch
[/LIST]

any idea where to find this patch?

---

### Post by yabbadabbadont on 2007-06-15
> **eentonig said:**
> any idea where to find this patch?

[http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

---

### Post by demonbro on 2007-06-19
when to go to install xp, it says no bootable disc in drive.  ANyone know how to fix this?

erik

---

### Post by nylecoj813 on 2007-06-19
Thanks for the guide. I figured I'd post here my issue before creating a new post. I have vmware successfully installed, and XP as a guest OS. However, I still cannot access the internet in XP through Vmware :( 

I am running on a laptop with wireless that works fine in Feisty. I am using the "host-only" setting, as this is the only setting that XP actually said was connected (the others stated limited or no connectivity). However, I cannot get to any web pages (cannot find server error)

Can anyone help me in solving this? I specified eth1 in the configuration because that is my wireless card, so it should be looking to the right card. It is possible I may just not be understanding how to configure this correctly.

Thanks in advance!

---

### Post by Merk42 on 2007-06-19
So...am I just screwed in my case?  Is that half-installation just going to sit there until I reinstall Ubuntu?

---

### Post by geezerone on 2007-06-20
@nylecoj813 - type "ifconfig" in terminal to see your I/Fs and understand that the top one will be the one you should be using. I used 'Bridged' connection. Make sure the IP/DNS settings are correct in VMware XP.

---

### Post by nylecoj813 on 2007-06-20
> **geezerone said:**
> @nylecoj813 - type "ifconfig" in terminal to see your I/Fs and understand that the top one will be the one you should be using. I used 'Bridged' connection. Make sure the IP/DNS settings are correct in VMware XP.

Ok..I won't be able to work on this for awhile (at work)...I spent quite awhile last night looking at the results of ifconfig and checking things in XP and trying different settings in vmware... can you possibly explain why I'd be using the "top one", which is eth0 (right?) if my wireless is at eth1? Or am I not following what you're saying? >_< 

Anyways...I'll be working on it more tonight and I'll post my ifconfig output if I can't get anywhere. Thanks!

---

### Post by nylecoj813 on 2007-06-20
Problem solved! Reconfigured using eth0 and NAT and I am browsing the net in XP on Vmware :) Thanks!

---

### Post by geezerone on 2007-06-22
Glad to help! :D

---

### Post by tdn on 2007-06-22
I have tried following this HOWTO. 
The installer/configure fails.
I have pasted the contents of my terminal here:
[http://thomasdamgaard.dk/paste/P627.html](http://thomasdamgaard.dk/paste/P627.html)

What went wrong? 
How do I fix it?
Can it be because I have a newer version of gcc?

---

### Post by nylecoj813 on 2007-06-22
> **tdn said:**
> I have tried following this HOWTO. 
The installer/configure fails.
I have pasted the contents of my terminal here:
[http://thomasdamgaard.dk/paste/P627.html](http://thomasdamgaard.dk/paste/P627.html)

What went wrong? 
How do I fix it?
Can it be because I have a newer version of gcc?

You need to apply a patch for the vmmon module. Here it is: 
[http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

Download and extract the tar and run the .pl file in the folder (forget the name). Then go back and rerun vmware-install.pl

Hope that helps!

---

### Post by tdn on 2007-06-22
> **nylecoj813 said:**
> You need to apply a patch for the vmmon module. Here it is: 
[http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

Download and extract the tar and run the .pl file in the folder (forget the name). Then go back and rerun vmware-install.pl

Hope that helps!


Where should I extract the tarball to?
From where should I run the .pl-file in it?

Is my current install broken now? Do I have to reinstall?

---

### Post by nylecoj813 on 2007-06-22
> **tdn said:**
> Where should I extract the tarball to?
From where should I run the .pl-file in it?

Is my current install broken now? Do I have to reinstall?

I extracted the tarball to the same place as I extracted the vmware tarball (home folder for me ) and ran the .pl (it's called runme or something IIRC?) from inside the patch folder . Your current install isn't really broken, you just haven't finished it yet. That's why you should re run the vmware-install.pl after running the patch pl. 

I came across the same exact issue and did this, and I have a working Vmware :) If this isn't clear and you want a more step-by-step instruction I can do that, just let me know!

---

### Post by jdbaok on 2007-06-24
ok - you said to post errors:

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

jdbaok@ubie:~/tmp/vmware-server-distrib$ 


jb

---

### Post by T0MA on 2007-06-25
hi everyone,
i need a little help with vmware-server 1.0.3. The problem is that when I try to power up a windows xp virtual machine I created with vmware-server 1.0.3 (the windows version of it) a black screen appears for a couple of seconds and then it quits and goes back to the console (ergo nothing happens). When I try to create a new virtual machine to install it from scratch the same thing happens, no error message, nothing...

any idea whats going on in here? I already reinstalled it but that didn't help..

UPDATE: ok, i realized it doesn't boot up because the vm image is on the NTFS partition, although it is read/write able... any idea how can I make it work on the NTFS partition?

---

### Post by Xanatos Craven on 2007-06-29
> **T0MA said:**
> hi everyone,
i need a little help with vmware-server 1.0.3. The problem is that when I try to power up a windows xp virtual machine I created with vmware-server 1.0.3 (the windows version of it) a black screen appears for a couple of seconds and then it quits and goes back to the console (ergo nothing happens). When I try to create a new virtual machine to install it from scratch the same thing happens, no error message, nothing...

any idea whats going on in here? I already reinstalled it but that didn't help..

UPDATE: ok, i realized it doesn't boot up because the vm image is on the NTFS partition, although it is read/write able... any idea how can I make it work on the NTFS partition?
Hm. I'm guessing I have the same problem you're having then. +2?

---

### Post by hotani on 2007-06-30
> **jdbaok said:**
> ok - you said to post errors:
**Unable to build the vmmon module.**

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

jdbaok@ubie:~/tmp/vmware-server-distrib$ 


jb

The process on [this page](http://www.debuntu.org/how-to-vmware-server-workstation-under-ubuntu-feisty) will fix that problem. Then you will need to run the installer again.

---

### Post by veloce on 2007-06-30
> **T0MA said:**
> hi everyone,
i need a little help with vmware-server 1.0.3. The problem is that when I try to power up a windows xp virtual machine I created with vmware-server 1.0.3 (the windows version of it) a black screen appears for a couple of seconds and then it quits and goes back to the console (ergo nothing happens). When I try to create a new virtual machine to install it from scratch the same thing happens, no error message, nothing...

any idea whats going on in here? I already reinstalled it but that didn't help..

UPDATE: ok, i realized it doesn't boot up because the vm image is on the NTFS partition, although it is read/write able... any idea how can I make it work on the NTFS partition?

This is likely to be a permissions issue.  NTFS might just be a really bad idea.  Try sudo chmod 777 
on all the files in the virtual machine directory.

To debug, you need to start your vm in console mode (ie not full screen) with debugging on (its one of the options for the vm).  Otherwise you get no error messages.

---

### Post by veloce on 2007-06-30
> **hotani said:**
> The process on [this page](http://www.debuntu.org/how-to-vmware-server-workstation-under-ubuntu-feisty) will fix that problem. Then you will need to run the installer again.

Or you could use the vmware server in the commercial repository that already has the modules built. (There are instructions on the forum here somewhere - do a search.)

---

### Post by hotani on 2007-06-30
Thanks, that's better than hacking some buried file.

Here is the line that needs to be added to the sources:
```

deb http://archive.canonical.com/ubuntu feisty-commercial main

```

---

### Post by Xanatos Craven on 2007-07-02
I have a problem specifically with the Ubuntu vmware-server package.

Right at the end of the install, when it's starting up the vmware service, it hangs right after that and never finishes the install. This has never happened to me with the .tar.gz file on vmware's site.

Is there any way to get around this?

---

### Post by Sciamano on 2007-07-04
Has anyone been able to make printers work in VMWare under Feisty?
They used to work with Edgy, but since I upgraded to Feisty they won't work anymore. I used the "port 631" trick before, but it looks like it does not work anymore.
Any suggestion? Thanks

---

### Post by fabertawe on 2007-07-05
> **Sciamano said:**
> Has anyone been able to make printers work in VMWare under Feisty?
They used to work with Edgy, but since I upgraded to Feisty they won't work anymore. I used the "port 631" trick before, but it looks like it does not work anymore.
Any suggestion? Thanks

I don't have any suggestion I'm afraid but my USB HP Deskjet 5150 works fine. I have to run it from Windows if I want to use "photo" quality printing as this setting from Ubuntu results in an oversized printout (wrong DPI). I too upgraded from Edgy to Feisty.

---

### Post by leetj on 2007-07-07
ok i went through the set up  and it asked for an absoulute path to extract the binaries ,i tried home/lee and it said this is relative path ,so i closed the terminal   ,now when i come to repeat the install procedure it says this:

sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to find the binary installation directory (answer BINDIR)
       in the installer database file "/etc/vmware/locations".

Failure

Execution aborted.

lee@lee-laptop:~/vmware-server-distrib




i am totally new to linux and any help would be greatly welcome
thanx for future responses 
lee

---

### Post by leetj on 2007-07-07
hi
i followed the setup above and it asked me for an absolute path to extract the binaries, i tried home/lee   but it says this is a relative path ,so i closed the terminal and tried to repeat the install procedure and got this error info:

lee@lee-laptop:~$ cd vmware-server-distrib
lee@lee-laptop:~/vmware-server-distrib$ sudo ./vmware-install.pl
Password:
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to find the binary installation directory (answer BINDIR)
       in the installer database file "/etc/vmware/locations".

Failure

Execution aborted.

lee@lee-laptop:~/vmware-server-distrib$ 



i am completely new to linux  and any help would be greatly welcome
thanx for any future response
lee

---

### Post by americanmetal07 on 2007-07-07
Im currently dual-booting Ubuntu 7.04 and XP, can I still use Vmware to do this? Or do I have to completely reinstall XP?

---

### Post by Tintinnabulation on 2007-07-09
@americanmetal07

Yes you can run your existing.  Use vm converter to create a xp vm or just use the physical xp installation.
See here:
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")
and here:
[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/]("http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/")

---

### Post by ElemonGW on 2007-07-10
You shouldn't have closed the terminal. Now you must uninstall it. If the problem continues run
```
sudo rm -rf /etc/vmware
```
in terminal.

---

### Post by americanmetal07 on 2007-07-11
> **Tintinnabulation said:**
> @americanmetal07

Yes you can run your existing.  Use vm converter to create a xp vm or just use the physical xp installation.
See here:
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")
and here:
[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/]("http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/")

THANKS!:lolflag:

---

### Post by luap56 on 2007-07-12
hi got vmware installed on ubuntu but every time i try and run it i get 

root@Duncan:~# vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

root@Duncan:~# 

now i do what it says but same thing i went through this link to to get it working with Ubuntu bits
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)
but i get the same thing over and over i enter my key it sayed done but no????

i have done so much 

so any help  :confused:

---

### Post by superFerra on 2007-07-16
Hi all,
Is there a way to run a script before and after booting a virtual host?

I configured my windows guest to use partition but i want to umount that partition automatically before running win and i want it remounted as windows powers off....
Is it possible ???
thanks

@luap56: Do you configure it correctly?? i mean have verified the paths that you confirmed/submitted to config.pl script ?? 
Why running as root ??

---

### Post by pacman_0020 on 2007-07-18
> **Xanatos Craven said:**
> 
[QUOTE=T0MA;2912516]hi everyone,
i need a little help with vmware-server 1.0.3. The problem is that when I try to power up a windows xp virtual machine I created with vmware-server 1.0.3 (the windows version of it) a black screen appears for a couple of seconds and then it quits and goes back to the console (ergo nothing happens). When I try to create a new virtual machine to install it from scratch the same thing happens, no error message, nothing...

any idea whats going on in here? I already reinstalled it but that didn't help..

UPDATE: ok, i realized it doesn't boot up because the vm image is on the NTFS partition, although it is read/write able... any idea how can I make it work on the NTFS partition?


Hm. I'm guessing I have the same problem you're having then. +2? [/QUOTE]

Ok ... So,  I'm also having the same problem with VMWARE ... but on Dapper LTS

After some research, found that this is a problem with mmap on NTFS ... refer to the discussion here ...
[http://www.vmware.com/community/thread.jspa?messageID=687525](http://www.vmware.com/community/thread.jspa?messageID=687525)

On searching for mmap problems with NTFS-3G, I got the following discussion which says the problem is with FUSE ! (not supporting shared writeable mmaps)  :
[http://forum.ntfs-3g.org/viewtopic.php?p=1677&sid=6d4f0474eed9495d890215440acfa98d](http://forum.ntfs-3g.org/viewtopic.php?p=1677&sid=6d4f0474eed9495d890215440acfa98d)

And last, I also got this link, which says that FUSE also has been enhanced to support shared writeable mmaps :
[http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/173](http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/173)

AAAAAAAAAAAAUUUUUUUUUUUUUUGHHHHHHHHHHHHH !!! :mad::mad:

Of course, it still does not work for me ... and I can't convert the partition to ext2/3 for now...

Anybody who has made it work on NTFS, please help !!

Regards,
Pacman

---

### Post by superFerra on 2007-07-20
...me too
First i tried to put vmware images on an NTFS drive without success. I had to switch to ext3 fs...

Any idea about running a script before and after powering up/down a VM ??

TIA

---

### Post by Jumbalaspi on 2007-07-27
Hi, i've just installed VMware server and i tried setting up a Winxp virtual machine on my kubuntu. Everything went fine, xp is working, i've got internet connection, i can surf the web, client pings my host machine and vice-versa but i can't set up a ftp connection. I can connect to my host machine's ftp (proftpd) from other pcs in my LAN but when i try connecting from my xp client (iexplorer and filezilla) it says that login timed out. Then i tried setting up an ftp server on xp (filezilla server) and i had the same error connecting from my host. I don't know what to do, everything is ok (ping, ip, internet connection, windows firewall disabled...) but it doesn't seem to work... what do you think i should try to do?

Host: Linux kubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
Client: Windows XP Professional Corporate
VMware version: 1.0.3 build-44356

---

### Post by the8thstar on 2007-07-29
Hello,

I'm using VMWare Player to use XP within Ubuntu. Everything works well except for the sound. There's none. My current soundcard is listed as HDA Intel under Ubuntu. What should I put in the config file so that VMWare/Windows XP finds it and uses it???

Thanks!

---

### Post by superFerra on 2007-07-30
@Jumbalaspi: you can try to switch you ethernet card from "nat" to "bridged"
 You have to open your .VMX file and look for:
```

ethernet0.connectionType = "nat"

```
and change it to
```

ethernet0.connectionType = "bridged"

```
...

@the8thstar: Did you added the sound card device to your image?

---

### Post by the8thstar on 2007-07-30
I don't understand what you mean. How do I add it? All that's listed is "sb16" in the config file of the VMWare Player for virtual sound.

My device is Audio an Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02).

---

### Post by Jumbalaspi on 2007-07-31
> **superFerra said:**
> @Jumbalaspi: you can try to switch you ethernet card from "nat" to "bridged"
 You have to open your .VMX file and look for:
```

ethernet0.connectionType = "nat"

```
and change it to
```

ethernet0.connectionType = "bridged"

```
...


thanks but i found that is an issue related to my ethernet card... i solved downloading and installing vmware player 2.0

---

### Post by dimitars on 2007-08-12
can i install vmware on already instaled windows. I don't want to install windows aggain.

---

### Post by dimitars on 2007-08-12
how can i install vmware if i don't wnt to install windows aggain. I have installed windows before installing vmware. CAN I

---

### Post by cesera on 2007-08-12
> **dimitars said:**
> how can i install vmware if i don't wnt to install windows aggain. I have installed windows before installing vmware. CAN I
 
 
Presuming you have a dual-boot machine and want to run vmware under ubuntu, this might be of help:
*[http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition)*

---

### Post by Fenix on 2007-08-13
```
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Anyone have any ideas?

---

### Post by adnanali on 2007-08-14
I was following the given instructions and encountered the following error:


Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

Can anyone help me out with this?

- Adnan

---

### Post by usc911 on 2007-08-14
heya guys,

i too got the error:

Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


any ideas on what to do?

thanks

---

### Post by wolrab49 on 2007-08-15
OK, I followed the procedure and I eventually ended up with this message:-

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? 

As I don't have a C compiler I answer No and it bombs me out, any ideas?

---

### Post by sjason2007 on 2007-08-15
I have done everything right but when i try to install windows it says that the cd i have in the drive is either not a windows cd or it can not read it. I have to copies of XP one mine one my brothers and neither of them work, both discs are clean. Can someone help me out?

---

### Post by mssever on 2007-08-15
> **wolrab49 said:**
> OK, I followed the procedure and I eventually ended up with this message:-

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? 

As I don't have a C compiler I answer No and it bombs me out, any ideas?
Install a C compiler. ```
sudo aptitude install build-essential
```You can uninstall build-essential and everything it drags in after completing the vmware install if you don't want it hanging around: ```
sudo aptitude purge build-essential
```

---

### Post by GregMcn on 2007-08-15
Excellent tutorial.As a newbie it was a big feat to enable me to install vmware.I now have XP running on Fiesty.(for those who had a little trouble there is a patch for Fiesty owners see [http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html](http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html)).

Im amazed at how quick it runs .Better then on a dedicated Xp mchine.

Well done guys

---

### Post by wolrab49 on 2007-08-16
> **mssever said:**
> Install a C compiler. ```
sudo aptitude install build-essential
```You can uninstall build-essential and everything it drags in after completing the vmware install if you don't want it hanging around: ```
sudo aptitude purge build-essential
```

Thanks for that information. I looked around further and it seems my problem is due to the fact that I'm using Feisty. I've added the commercial repository and I've just installed the VMware server using the package manager. I'm half way through installing XP now. I'll let you know how it goes.

---

### Post by friend_kami on 2007-08-16
yes yes it works. only problem is that im using ableton live with windows, and thats the **only** program i use windows for.

now, ive got two soundcards, one for midi only, and one for audio, dont ask me why. with xp, it just works. with ubuntu/xp vm, it doesnt.

that is, i get audio through a virtual (emulated) dx audio driver, and as you can understand this is far from optimal when using it as a daw.

10ms latency **tops**, more then that is just unacceptable for live perfomance/recording/jamming.

now, if anyone has some info on this specific problem and/or knows a place to go for troubleshooting/hacking, please please **please** do let me know.

ive been trying to make this work properly for ages now, still refuses to work. -.-

cant install drivers for my audiophile 24/96 card, because it wont find it, since ubuntu is using it, and since its a VM, with no support for real hardware (so it seems like). sigh.

ive tried them all, except parallels.

i know that someone is working on getting live to work with wine, but hasnt gotten the audio engine up and running yet, if someone knows how to do this i would love you long time if you tell me how.

the installer just quits with a memory allocation, and hey im a linux noob so i dont know enough to hack it either >.<.

---

### Post by JessXe on 2007-08-23
> **adnanali said:**
> I was following the given instructions and encountered the following error:


Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

Can anyone help me out with this?

- Adnan

I had the same exact problem.  Does anyone have a solution?

~JessXe

---

### Post by zairulazwan on 2007-08-23
I Have two hard disk one using windows xp and the other one ubuntu feisty. currently dual booting. Can I use VMWare without reinstalling windows so it can just detect the other hard drive (windows xp) ?

---

### Post by senor_smile on 2007-08-24
I'm running the configuration. On the screen that says:

In which directory do you want to keep your virtual machine files?

I have put:

/media/hda2/vmware

which is a folder on my second partition(since the partition ubuntu is in isn't that big)

I then get the following error:

Unable to change the access rights of the file /media/hda2/vmware.
Execution aborted.  

I tried it again with a different folder, this time creating the folder first to no avail.

Help

---

### Post by stinger30au on 2007-08-24
after oyu have the vmware xp running can you "drag n drop" data from the xp to linux machine and vise versa?

---

### Post by apiccirilli on 2007-08-25
> **Fenix said:**
> ```
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Anyone have any ideas?

I'm getting this same error too, running Feisty x86_64.  Anyone with some insight?

---

### Post by R0B071CxN1NJ4 on 2007-08-26
You can install an existing operating system but only if it is on another hard disk. it will not read from the same hard disk. So you cannot have a dual boot and a vmware of the same os.

---

### Post by jlmartinjr on 2007-08-27
I am trying to do this and when I installed VMware I recieved and error message,  now from Add/remove Applications or going to the system>admin>Synaptic package manager I get an error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Then if I go to terminal and attempt to run this it says that I must have superuser 

requested operation requires superuser priviledges

I did get XP to load onto my machine using Virtual box before the dpkg problem

I can run XP get to the internet but it has an odd IP address and is not able to see my windows network machines.

---

### Post by DemoN3x on 2007-08-27
> **jlmartinjr said:**
> I am trying to do this and when I installed VMware I recieved and error message,  now from Add/remove Applications or going to the system>admin>Synaptic package manager I get an error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Then if I go to terminal and attempt to run this it says that I must have superuser 

requested operation requires superuser priviledges

I did get XP to load onto my machine using Virtual box before the dpkg problem

I can run XP get to the internet but it has an odd IP address and is not able to see my windows network machines.

```
sudo dpkg --configure -a
```

---

### Post by orko3001 on 2007-08-31
> There is software available that can run Windows XP or any other Operating System inside your main Operating System.

Hi, thanks for this how to. What about Mac OSX? Can I have that as well?

Cheers

---

### Post by SteveHoffmanUK on 2007-08-31
Help!

My Vmware Server has stopped running. I click on the icon in the panel and nothing happens.

I am on Dapper and have been running Windows XP Home in my virtual machine;  it has worked fine until now. I just updated my system, and I noticed that the update included an update of Linux kernel. Could this have caused my problem?

What do I do? Can I just reinstall? I don't want to lose my Windows files.

---

### Post by HermanAB on 2007-08-31
Yup, VMware modifies the Linux kernel.  So if you upgrade the kernel, then you have to re-install VMware.  The moral of the story is - don't fix it if it ain't broke!  If Linux works properly, leave it alone, since an update can then only make things worse, not better.

---

### Post by -SpaZ on 2007-08-31
> **stinger30au said:**
> after oyu have the vmware xp running can you "drag n drop" data from the xp to linux machine and vise versa?

I am pretty sure you can, but if you can't, you should be able to just go into the file system and drop it in your home folder.

---

### Post by SteveHoffmanUK on 2007-08-31
HermanAB:

If I reinstall VMWare Server, do I have to reinstall XP? Do I lose all my XP files?

---

### Post by azray on 2007-08-31
I was wondering if this howto applies to Feisty?

---

### Post by tact on 2007-08-31
after a linux kernel update you do need to recompile VMWare server.  just run the 
/usr/bin/vmware-config.pl  script again.

No you dont lose all your VM's or settings or data.  It just recompiles using the new linux headers and all is sweet again.

---

### Post by davebrazier on 2007-09-02
Hey all,

Cheers for the article.  Really detailed and thorough.  Thanks.  However, I'm having a slight problem.  I'm getting this feedback in the terminal ...

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] // N.B. I pressed [ENTER] here

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-lowlatency/build/include] // N.B. I pressed [ENTER] here

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config6/vmmon-only'
make -C /lib/modules/2.6.20-16-lowlatency/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-lowlatency'
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config6/vmmon-only/linux/driver.c:80:
/tmp/vmware-config6/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config6/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config6/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config6/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config6/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-lowlatency'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config6/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

--------------

Any ideas what I should do?  If it makes a difference, I'm currently logged in as root.

Thanks so much, Dave.

---

### Post by Alex Broadbent on 2007-09-02
I have exactly the same problem and would also appreciate some help!

Thanks,
Alex

---

### Post by Alex Broadbent on 2007-09-02
OK Dave, I found the answer (thanks to a link provided by Greg Mcn, 2 weeks ago, this thread page 109).

Feisty needs a patch. Full instructions are here. They are working for me right now (I'm not through yet though...)

[http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html](http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html)

Good luck,
Alex

---

### Post by Alex Broadbent on 2007-09-02
OK, back again... I was going along well following the instructions at the link in my previous post but then I got the following errors.

```
Please specify a port for remote console connections to use [902] 

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

Unable to get the last modification timestamp of the destination file 
/etc/vmware/ssl/rui.key.

Execution aborted.
```


Why can't it get this timestamp? Any help much appreciated!
Thanks,
Alex

---

### Post by Alex Broadbent on 2007-09-05
Anyone?...

---

### Post by warlockninja on 2007-09-07
Hi,

I am not sure if this question has been asked yet but if it has can someone kindly post the link....

Anyway...........This is an awesome howto and I have my Xp virtual machine up and running..

I am curious though, is there a way to access a separate hard disk that is on the host side from within the virtual machine side? How would I make that other host disk appear as a drive in Windows XP virtual machine?

Any help on this would be most excellent.

Thanks in advance.

---

### Post by philven on 2007-09-07
Maybe this is an even dumber question:  I have a dual boot system with Win XP and Kubuntu Feisty.  Can VMWare allow me to access XP while booted to Kubuntu?  The reason I ask is I sometimes have a need to access a Windows prog but don't want to have log out of Kubuntu and boot into XP.  I don't want to have to re-install everything in VM.  Am I just stupid or is it possible?

---

### Post by Alex Broadbent on 2007-09-10
From what I understand, the Windows you have on a VM and the Windows you have on another boot partition are totally separate things. That's what it says near the top of the original howto. So I'm guessing the answer to the previous question is no. However, I haven't had any responses to my own questions yet so I don't yet have VM up and running! (Nudge nudge anyone?)

---

### Post by Alex Broadbent on 2007-09-10
...but in case I misread your question - yes, if you have VMWare, you can boot windows without logging out of linux. It runs "on top" of linux. - It's just a different instance of windows from whatever other ones you might have on your other partitions.

---

### Post by BLTicklemonster on 2007-09-10
Running Gutsy, and went to the vmware site, downloaded it, tried to install it, ran into problems, went and found this:

> If you have still problem with building kernel modules, or if VMware application refuses to run complaining that your kernel is too new, it is time to download this patch. You can find latest version of patch at [http://platan.vc.cvut.cz/ftp/pub/vmware](http://platan.vc.cvut.cz/ftp/pub/vmware) , or at its mirror [ftp://ftp.cvut.cz/vmware](ftp://ftp.cvut.cz/vmware)

After downloading unpack file into some directory, enter that directory and run "./runme.pl". After doing that run "vmware-config.pl", or, if you installed update on system which is supported by your product (though I do not understand why you installed product in this case) "vmware-config.pl -compile". Note that while original modules from VMware do not need C++ compiler, my updates need it, and won't build without - it is price I had to pay to get support for all these products from one source.

did it, and it worked.

Had to change the nic to nat (paddy wack, give the dog a bone, of course), though to get internet.

---

### Post by increduloushulk on 2007-09-11
> **Alex Broadbent said:**
> 
```
Unable to get the last modification timestamp of the destination file 
/etc/vmware/ssl/rui.key.
```


Why can't it get this timestamp? Any help much appreciated!
Thanks,
Alex

Alex, my first thoughts were to suggest verifying that the file exists, and then poking it to see if that'll generate a timestamp.  You might also check out cesare's post earlier in the thread on fixing the same issue with edgy.  Apparently, ia32-libs was missing.[  Here's the link.]("http://ubuntuforums.org/showthread.php?p=1795616&highlight=timestamp#post1795616")  

I was having the same problem you and Dave were having, so I hope the instructions you linked to will solve it for me, and I'm glad to have a heads-up about this timestamp issue.

---

### Post by yang2iu on 2007-09-12
> **Tarquin said:**
> Thanks for the walkthrough, but I cannot get mine to install. I alsways get this message:



I have made sure I have access to that folder & the files in it, but nothing seems to work.
Now I am pretty much a n00b when it comes to Linux in general, I only know what a friend has been telling me over the last couple of weeks, so I guess it could be something stupid!

Many thanks in advance for any help though.

Tarq


I got the same message... =/

Any idea?

---

### Post by il-luzhin on 2007-09-15
Uninstall help please?

I found a vmware-uninstall.pl file in /home/luzhin/vmware-server-distrib/bin and it didn't work so I used adept.  Foolish in retrospect.

Is there an easy way to remove the files vmware has placed in every nook and cranny of my machine now that the software is uninstalled?

Thnx

---

### Post by dimas869 on 2007-09-29
Is there any way to switch the hardware (microphone, speakers, camera, etc) from the main platform (Ubuntu Feisty) to Windows on VMWare Server?
:roll:

---

### Post by BLTicklemonster on 2007-09-29
Just install the (windows) drivers in windows in vmware. That ought to work fine.


I am running gutsy beta, and just downloaded and installed vmware server (from their site) and it installed with no problems whatsoever. Didn't have to patch it or anything.

---

### Post by DJ_Peng on 2007-09-30
I got VWare installed on Gusty with no problem, but when I try to set yup a virtual machine using the Windows installation I have for dual booting it complains that the partition table has changed since the snapshot was taken. I did change that partitions since I originally installed VMWare in Feisty, but I've done a reinstall of Feisty so I'm not sure why it's seeing an old snapshot. Is there some way to force a new snapshot so I can get the virtual machine set up? It keeps saying to remove the drive from the virtual machine and re-add it but that doesn't get rid of the error message.

---

### Post by pedro_sland on 2007-09-30
In response to BLTicklemonster:
the file to download is [vmware-any-any-update113.tar.gz]("http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update113.tar.gz") :)

---

### Post by BLTicklemonster on 2007-09-30
> **pedro_sland said:**
> In response to BLTicklemonster:
the file to download is [vmware-any-any-update113.tar.gz]("http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update113.tar.gz") :)

Thanks, but with the Gutsy Beta, I didn't have to patch a thing. I just installed vmware and it worked just fine. (I already had that particular patch saved on my storage drive, btw :) )

---

### Post by dimas869 on 2007-09-30
> **BLTicklemonster said:**
> Thanks, but with the Gutsy Beta, I didn't have to patch a thing. I just installed vmware and it worked just fine. (I already had that particular patch saved on my storage drive, btw :) )

hello monster, well no i got no sound and aether find the camera after installing the the windows driver!
any idea?:confused:

---

### Post by NZ-Wanderer on 2007-09-30
Thanks guys, I been contenplating upgrading to Gutsy but was a little worried I wouldn't be able to install VMware server, but since you guys have done it I will give it a go as well :) :)

---

### Post by bmartin on 2007-10-02
1. Install Ubuntu
2. Install VMware server.
3. Kernel spinlock message on boot.
4. Profit??

But seriously, I can't boot my computer anymore. When I did have VMware installed, I just got a blank screen when starting the VM. The VM didn't boot from the CD and didn't display an error; it was simply blank.

I've been trying to mount my partitions from the Feisty Live CD, but it simply locks up at the Ubuntu desktop after loading... I've left it for 20 minutes and nothing happends. So I grabbed a Gutsy CD, and after modifying my xorg.conf file to use fglrx and running sudo /etc/init.d/gdm restart, my X server loads properly. However, it won't let me mount my hda3 partition as root; it doesn't overwrite the Live CD's file system, so I can't use apt to grab a different kernel so as to solve this problem.

So I rebooted with the same Live CD and mounted the partitions elsewhere, then copied the kernel image and modules from the Live CD to my computer, modified GRUB so it'd know about the new kernel, and rebooted. I think I'm good to go now, but I won't be trying VMware again anytime soon.

---

### Post by frickea86 on 2007-10-06
```
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

Hey guys,  noob here.  I tried searching for this error without much luck.  I am having this error when installing Vmware.  Anyone seen this before and what should i do?

---

### Post by Osmo on 2007-10-06
When I go to the VM-ware-site I cannot download the Binary (.tar.gz) - file. When I click on it to download it, nothing happens (except hours of loading the page without any result). I can download all the other files (but I don't need them of course).

Can somebody help me?

---

### Post by bodhi.zazen on 2007-10-06
> **Osmo said:**
> When I go to the VM-ware-site I cannot download the Binary (.tar.gz) - file. When I click on it to download it, nothing happens (except hours of loading the page without any result). I can download all the other files (but I don't need them of course).

Can somebody help me?

Do you have java blocked (noscript) ?

---

### Post by Osmo on 2007-10-06
It worked and i have downloaded the file now but when i try to install with the code "sudo ./vmware-install.pl" I get this :


```
filip@Pc-Boven:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

inetd: no process killed
The removal of VMware Server 1.0.4 build-56528 for Linux completed 
successfully. Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr] /usr

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] /etc

What is the directory that contains the init scripts? [/etc] /etc

The file /etc/vmware that this program was about to install already exists. 
Overwrite? [yes] yes

Unable to copy the source file ./installer/services.sh to the destination file 
/etc/vmware.

Execution aborted.
```


What fault did I make?

---

### Post by bandoba on 2007-10-10
Folks,

I have VMware workstation and I executed following line in Terminal 
vmware -x <path of .vmx file>

This opens the VMX file and also starts the VM. But looks like somehow this is tied with current logged on user's session. As soon as I logout, this virtual machine stops running. 

Does anybody know how can I make sure the VM will keep on running even if I logout? I would actually like to run the VM by connecting over SSH. Is that possible?

Thanks.

---

### Post by apu95 on 2007-10-10
Any idea how I can increase performance in this? It's really terrible...I allocated 512 ram and 4gb of HD space for it, and even before I install the OS, its sluggish. When it booted off the CD, it seemed to get 'stuck' while it loaded the installation. This repeats itself throughout the usage of the VM. It just seems to hang at random intervals, and then it kicks back and starts working again. Any idea why this might happen?

---

### Post by d_xtremw on 2007-10-13
apu95 i think it might be your processor thats messing up

my question is how doe u transfer files back and forth across the host OS and the  guest OS. i really need to know.
thanks in advance

---

### Post by bmartin on 2007-10-13
> **d_xtremw said:**
> my question is how doe u transfer files back and forth across the host OS and the  guest OS. i really need to know.
thanks in advance
My best guess would be to set up a file server on the host OS and the corresponding client inside the guest OS (for example, if you're running XP inside Ubuntu, you could install the openssh-server package, then use an SFTP client from Windows; I like the one [here]("ftp://ftp.ssh.com/pub/ssh/SSHSecureShellClient-3.2.9.exe"); it's free for non-commercial use).

You might also be able to virtualize your file system so that it can be detected in the guest OS. If that's the case, there are programs for Windows that can read and write using EXT2/3.

---

### Post by d_xtremw on 2007-10-13
im a bit of a newb when it comes to networking so please excuse my lack of knowledge, i downloaded the ssh-secure shell client(thanx for that by the way) and installed the open-ssh package on ubuntu,  what would be the next series of steps 

and is there a way to enable drag & drop from 1 OS to the other, i was reading about it here
[http://www.vmware.com/support/ws4/doc/running_dragdrop_html.html](http://www.vmware.com/support/ws4/doc/running_dragdrop_html.html)

but i didnt see any "guest isolation" option :S:S

---

### Post by bmartin on 2007-10-13
In the client program, for the host, you'd put your IP address on the host machine (normally 192.168.something, assuming you're behind a router; you can check using the ifconfig command). For the user name and password, put your Linux user name and password in. The other settings can be left on the defaults; 22 is the default port for SSH, but I used to run it on 443 to trick my workplace computers into allowing me to shell into my home computer from work.

---

### Post by d_xtremw on 2007-10-13
i clicked the connect button and entered the remote host as the IP address and the user name as the my linux username, it didnt ask for a password or anything so im assuming im doing the wrong thing.. considering it didnt work :-$. anyone know what i'm doing wrong??

---

### Post by bmartin on 2007-10-13
Try ssh'ing from your Linux box to your Linux box. Open a terminal and type **ssh localhost**. If you can't log in, there's something wrong with your SSH server. Otherwise, it's probably a problem with your emulator's network connection.

---

### Post by d_xtremw on 2007-10-13
ok that worked. i tried again in the vmware windows and now it keeps asking me for a password, when i put in my linux user password the window comes back as if i've entered it wrong. ive tried entering it about 4 times though.. veryyy slowly so i know its right

---

### Post by d_xtremw on 2007-10-13
ok i found the problem wit that. my username had a capital letter at the beginning. sorry about that :-$. but now everything is working perfectly. thanks everyone

---

### Post by bmartin on 2007-10-13
What are you putting in for the host name and user name?

---

### Post by d_xtremw on 2007-10-14
i've got another problem. VMware doesn't recognise any of my sound devices. ive been reading the thread and ppl have said they solved with this just a click but i went thru all the settings and i see nothing i can click or enable to get this working.

also the usb devices are not recognized and although this isnt that much of a problem right now since i set up the file sharing but im pretty sure it'll become more of a problem soon

---

### Post by syyid on 2007-10-14
I had a question that I couldn't find an answer to from VMWare's site or googling. How do I know if VMWare is using the SVM extensions with my AMD AM2 CPU (or VT for those using intel cpu's)? Also what sort of performance advantage should I expect (at the moment it seems a little sluggish). Thanks

---

### Post by rvickers on 2007-10-15
I used the guide and it works perfectly but I noticed that when I click the update button, it tells me there is a new version and do I want to visit the site. How do I update to a newer version?
Thanks

---

### Post by shoeverine on 2007-10-18
I get the following errors during installation after I accept the agreement and set some file locations:

> Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Any help would be greatly appreciated.

---

### Post by Bobdaboa on 2007-10-18
That easyvmx.com site looks promising.  I'm gonna try it out and see if it works ok.

---

### Post by carlinwithin on 2007-10-20
Quick question.  Is there a way to stop the mouse from only moving in a sloppy fashion?  If one would install a game in it, it would suck.  The more help the better. Thanks!

---

### Post by carlinwithin on 2007-10-20
actually, wow such a noob.  Forget the last question.  My next question will seem a little less noobish?  Umm, how does one install drivers for their video card inside the vmware?  I am wanting to install a game and I don't know if it will work without it.

---

### Post by Aonxe on 2007-10-20
> **carlinwithin said:**
> actually, wow such a noob.  Forget the last question.  My next question will seem a little less noobish?  Umm, how does one install drivers for their video card inside the vmware?  I am wanting to install a game and I don't know if it will work without it.

When you are in your VMWared operating system, the operating system uses a virtual video card, not the one that you have in your system. Well it is the same one, but it only has so many of its resources allocated to it. So, to answer your question I dont think you can install a graphics card driver. I could be wrong tho as I have only VMWared Vista and I dont know if it is different for XP.

---

### Post by Do0odz on 2007-10-22
reallly thank u :D .. I loved the way u explained it ... so simple :D

---

### Post by d_xtremw on 2007-10-23
ok i found out how to get sound devices and usb devices working. really simple actually so its probly on this thread.. anyway here goes
u open ur virtual machine, (but dont turn it on yet)
click on VM and go to settings then click add. u should see something there that says sound adapters and usb controllers. and there ya go. anytime u wanna detect a usb device go to 
vm-->removable devices--> usb

my new question put forth now is:
when using the secure shell file transfer, is there a way that i can save the profile and not have to type in the password everytime??

---

### Post by KillaB7 on 2007-10-25
For those using Gutsy, I just wanted to point out that this guide worked flawlessly for me.
[http://lunapark6.com/ubuntu-710-gutsy-desktop-edition-review.html](http://lunapark6.com/ubuntu-710-gutsy-desktop-edition-review.html)

> 
VMware Server (Run Windows and Windows applications in Ubuntu 7.10)
1.) Register for a VMware Server serial number here.
2.) from terminal “sudo apt-get install build-essential”
3.) download VMware Server for Linux - Binary (.tar.gz) here.
4.) from terminal cd dir to the downloaded file and type “tar zvxf VMware-server-1.0.4-56528.tar.gz”
5.) from terminal “cd vmware-server-distrib/”
6.) from terminal “sudo ./vmware-install.pl”
7.) hit the “enter” key for every question asked, if question doesn’t accept the “Enter” key then select “Yes”.
8.) Run VMware Server by selecting “Applicatoins –> System Tools –> VMware Server Console”


Now I just need to get Samba to play nice so I can move files in both directions.

---

### Post by iansane on 2007-10-26
I'm still a newb and since I've updated to Gutsy a lot of things have been working right on the first try. 

I just downloaded the tar.gz from the vmware sight unzipped and ran the vmware-install.pl file from a sudo terminal. Accepted all defaults and then installed windowsXPpro. Everything was easy and works great except it won't recognise my thumbdrive and I can't get Samba working right so I can't get any files to or from the VM without using an FTP and that's not practical when your in a hurry.. Runs beutifully but what good is it if everything is stuck on it? Old version on XP over a year ago had shared folders in the vmware tools but now server doesn't and workstation costs money? I'm trying my best to loose the duel boot but I can't win for loosing.

---

### Post by iansane on 2007-10-26
> **KillaB7 said:**
> For those using Gutsy, I just wanted to point out that this guide worked flawlessly for me.
[http://lunapark6.com/ubuntu-710-gutsy-desktop-edition-review.html](http://lunapark6.com/ubuntu-710-gutsy-desktop-edition-review.html)



Now I just need to get Samba to play nice so I can move files in both directions.

Moving them in at least one direction would be nice. :)

---

### Post by d_xtremw on 2007-10-26
for the usb flash drive you need to enable the usb controller and then select it from the VM menu. dont know much about samba yet so i'll hafta read up on that

---

### Post by KillaB7 on 2007-10-26
> **iansane said:**
> Moving them in at least one direction would be nice. :)

There seems to be a little problem with Gutsy in that it defaults the Workgroup name to MSHOME even if you make it WORKGROUP.

I got things working by installing "system-config-samba" via Synaptic.

---

### Post by RogueLeader on 2007-10-28
I originally had the same problems **frickea86** and **shoeverine** were having, where the modules wouldn't compile for my distribution.  I looked at the websites that the error text spit out for help, namely the Installing VMWare on Unsupported Distros link: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1623]("http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1623")

I tried out the any to any patch available there (by running the "runme.pl" script in that package's root director after untarring).  The object files needed by vmware's configuration scripts were finally able to be compiled.  After some configuring, everything works as before, with my old VMs.  This was pretty clutch, as I needed my Windows VM to use some proprietary software for a current project.

Happy patching!

---

### Post by StefanPieter on 2007-10-29
Thanks

---

### Post by psavva on 2007-10-30
VMware Crashes my Windows XP console...

I installed vmware successfully, I installed Windows XP Sucessfully too.
After about 5 minutes, VMware console screen powers off . 

How do i fix this probem?

---

### Post by mdpalow on 2007-10-30
Hi Everyone,

I brought up a Guest OS (Win XP) and then SUSPENDED it. I then partitioned a SPARE portion of the USB External HD that was already set up and attached in the Guest OS.

Later, when I went into VMware again and tried to power up the OS, it said it couldn't load because the HD partition had changed and that I needed to delete the HD from the virtual machine and then add it again. I assume it just wants to read the new partition info, so it can make it available.

However, you can't edit the Guest OS hardware/preferences unless you close it down first, BUT I can't run/power up the Guest OS to log out.

Is there maybe a config file that I can get into and remove the USB HD line?

Thanks in advance..

Edit...

P.S. Here's the ERROR I get:

"Cannot open the disk '/home/myname/vmware/Windows XP/Windows XP-0.vmdk' or one of the snapshot disks it depends on.
Reason: The partition table on the physical disk has changed since the disk was created. Remove the physical disk from the virtual machine, then add it again."

I'm gonna check that directory in the meantime. Hope to hear from someone soon. Thanks again..


**[SIZE="6"]SOLVED[/SIZE]**


I'll post so someone else can benefit.

I went into my folder where the suspend/snapshot files are and found the Windows XP-0.vmdk file and looked for the USB HD entry and removed it.

It then came back, so I was able to shut guest down and then add the HD again, but this time with the new partition.

Windows didn't like it when I tried to shut it down at first, but I had no choice but to just hit the OK key every time it whined. After adding the HD again it booted up fine. All is well.

If your folder location or filenames are different, which they might - just open each file with an editor until you find one that looks like it's got all the hardware you added and that will likely be the one to edit. Good luck...

---

### Post by singlewc on 2007-11-02
I found this thread on a google search, and read it through. Great information.

The reason for my search, is that I am looking for a solution just like this one, but the critical factor is the USB connectivity.

The windows apps that I want to use in Ubuntu, require the USB port, such as syncing with a pocketPC, and communicating with my GPS.

There are other needs, and most all of them depend on USB.

Can anyone who has done it, tell me, and us, <g> if the guest system has full access to the USB ports? Not just a flash drive or USB external drive, but complete USB, just as if it was a standard windows install?

I sure would like to know this, before I jump through all the hoops, and install everything only to find out it cannot work :-)

Thanks a lot

---

### Post by veloce on 2007-11-03
> **singlewc said:**
> 

Can anyone who has done it, tell me, and us, <g> if the guest system has full access to the USB ports? Not just a flash drive or USB external drive, but complete USB, just as if it was a standard windows install?



In theory yes you can get full access to the usb ports.  

But with some caveats, the usb device has to be physically recognised as connected by the host - but doesn't have to be useable by the host.

Also, if the host does try to use it, it can disable it for the vm.

So the only way to be sure your device will work, is to try it.

---

### Post by dethdeks on 2007-11-04
i went to install it n it wouldnt install for me it got passed the eula but then after it asked about icon directory's it failed n said it couldnt complete this is what it said


```

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:80:
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by Lord_Dicranius on 2007-11-05
Awesome guide!  I've been wanting to be Windows free for awhile now, but I still left Windows installed on my wife's laptop so that we could utilize Deposit@Home through our bank, USAA.  I've been unable to get it to work with Ubuntu/Firefox because one of the requirements was to use "Java for Windows".  I wrote them and asked about it, they verified they haven't had any luck with anybody getting it to work with Linux, and weren't show when they'd have support for it.  So I started searching and found a thread here about a guy who uses WinXP in a virtual machine and how it works perfectly!  I found this guide for installing VMWare as I've never used it before, and WinXP boots up!  Now I just need it to detect my USB printer...

Again, great guide!  And thanks for putting forth the work to put it together! :-)

---

### Post by iansane on 2007-11-06
> **veloce said:**
> In theory yes you can get full access to the usb ports.  

But with some caveats, the usb device has to be physically recognised as connected by the host - but doesn't have to be useable by the host.

Also, if the host does try to use it, it can disable it for the vm.

So the only way to be sure your device will work, is to try it.

Well I've tried and nothing usb including thumb drive will work. I know how to add one from "removable devices" but the usb list is empty.

Funny how something so simple can be such a problem. I have a dual boot vm, (Server 2003 and Ubuntu), Cent OS vm, and an XP vm all on top of Ubuntu and they can all connect through ssh, http, https, and ftp to each other but I can't get samba to work and can't use a thumbdrive. LOL Think I'll install another vm on my ubuntu vm just for kicks.

---

### Post by iansane on 2007-11-06
> **KillaB7 said:**
> There seems to be a little problem with Gutsy in that it defaults the Workgroup name to MSHOME even if you make it WORKGROUP.

I got things working by installing "system-config-samba" via Synaptic.

Thanks! That's probably my problem. Only computer I could access was one that had mshome. Did Bill Gates pay someone off? LOL

---

### Post by IainB on 2007-11-06
Install ran fine, but when I ran the Server Console, nothing, running the vmware command from terminal produced a 2 messages about missing files, these I fixed, and a message about an error:

/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:42: error: unexpected character `@', expected string constant

Appreciate any clues ... :-)

---

### Post by GuruX on 2007-11-07
I'm used this guide and it worked out perfect. If it hasn't been said before. It's not possible to bridge a wireless card through VMware server. I don't think the drivers support it. But NAT is perfecctly good. Also bridge on wired cards.

Now for my question. I run normal Ubuntu on my laptop with 768mb ram. When I set up my hosts in VMware it recommends me to not go beyond 464mb of ram (beyond that memory swapping might occur). But, when I run VMware I usually don't run any programs in Ubuntu. Wouldn't it be better to increase ram for my VMware host? Isn't Win XP swapping already inside the virtual machine?
Please explain this to me.

I'm also trying out VMware with Windows Vista, which I belive is a little more memory heavy.

---

### Post by kditty on 2007-11-08
when i run vmware from terminal i get this message:

kditty@kditty-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/home/kditty/vmware/vmware-config.pl.

---

### Post by GuruX on 2007-11-08
> **kditty said:**
> when i run vmware from terminal i get this message:

kditty@kditty-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/home/kditty/vmware/vmware-config.pl.

You need to run:
```
sudo /home/kditty/vmware/vmware-config.pl
```
Make sure that nothing has the status failed in the end of the configuration. Then you need to configure that device in another way.

---

### Post by kditty on 2007-11-09
> **GuruX said:**
> You need to run:
```
sudo /home/kditty/vmware/vmware-config.pl
```
Make sure that nothing has the status failed in the end of the configuration. Then you need to configure that device in another way.

i ran into this:

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed

The configuration of VMware Server 1.0.4 build-56528 for Linux for this running kernel completed successfully.


this is right above that in setup in terminal:

WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko

---

### Post by kditty on 2007-11-09
i have got vmware up and running, but i can not connect to internet on my guest/xp! wireless works fine in ubuntu but xp doesnt even recognize it. is there a setting i should tweek or should i install wireless drivers in my xp inside vmware? i dont even think xp/vmware recognizes my wireless card :\

---

### Post by veloce on 2007-11-11
> **kditty said:**
> i have got vmware up and running, but i can not connect to internet on my guest/xp! wireless works fine in ubuntu but xp doesnt even recognize it. is there a setting i should tweek or should i install wireless drivers in my xp inside vmware? i dont even think xp/vmware recognizes my wireless card :\

This goes back to your error that bridged networking failed.  I read somewhere that vmware will not bridge a wireless network.  You need to switch to a NAT virtual network.

---

### Post by Trance Machina on 2007-11-12
> **kditty said:**
> when i run vmware from terminal i get this message:

kditty@kditty-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/home/kditty/vmware/vmware-config.pl.

I have this exact same error.  Except that I invoked the command that it asked to about three or four times.  And at the end they all say:

```
The configuration of VMware Server 1.0.4 build-56528 for Linux for this running
kernel completed successfully.

```

Yet the problem still persists.  Any ideas? :/

---

### Post by almoravid on 2007-11-14
How to get the sound work on vmware

---

### Post by veloce on 2007-11-15
> **almoravid said:**
> How to get the sound work on vmware

works for me.  what's your actual problem?

---

### Post by keskew on 2007-11-15
This is a great guide.  Thanks so much!  I got VMware Server working right away.  The only problem I had was getting bridged networking to work with my wireless card.  I found a solution on the thread below.

[http://ubuntuforums.org/showthread.php?p=3772591]("http://ubuntuforums.org/showthread.php?p=3772591")

---

### Post by burn84 on 2007-11-19
This is a really easy to follow step by step but I encountered the same problem. I installed Virtualbox also and a similar problem arises.

Error message says:

"Warning:
No bootable CD, floppy or hard disk was detected.
To install and operating system, insert a bootable CD or Floppy
and restart the virtual machine
by clickng the Reset button."

I am trying to install Windows XP.I had a similar message on virtualbox. I selected loading using winxp.iso file. Could it be that I am loading the wrong kind of ,iso file? I do this because my CD drive is busted and I have no floppy drive on this laptop of mine: Acer Aspire 1680, it didnt come with one. Would REALLY REALLY appreciate help as I really need to use some old windows programs.

---

### Post by veloce on 2007-11-19
> **burn84 said:**
> This is a really easy to follow step by step but I encountered the same problem. I installed Virtualbox also and a similar problem arises.

Error message says:

"Warning:
No bootable CD, floppy or hard disk was detected.
To install and operating system, insert a bootable CD or Floppy
and restart the virtual machine
by clickng the Reset button."

I am trying to install Windows XP.I had a similar message on virtualbox. I selected loading using winxp.iso file. Could it be that I am loading the wrong kind of ,iso file? I do this because my CD drive is busted and I have no floppy drive on this laptop of mine: Acer Aspire 1680, it didnt come with one. Would REALLY REALLY appreciate help as I really need to use some old windows programs.

I don't understand what you mean by "selected loading using winxp iso file"

In vmware server console, you:
[LIST]
[*]open or create a virtual machine
[*]edit virtual machine settings
[*]select cdrom
[*]selct the "use iso image" radio button
[*]browse to the file you want
[*]check the "connected" and "connect at power on" boxes
[*]click OK
[*]Power on the virtual machine
[/LIST]

Is this what you did?

---

### Post by burn84 on 2007-11-19
Hi Veloce,

Yes that is what I did, the CD rom was mounted with the winxp.iso.

Here is the screenshot:

[http://i74.photobucket.com/albums/i246/burn1984_2006/VMWareError.png](http://i74.photobucket.com/albums/i246/burn1984_2006/VMWareError.png)

I dont know why it went to network boot?

---

### Post by veloce on 2007-11-20
> **burn84 said:**
> Hi Veloce,

Yes that is what I did, the CD rom was mounted with the winxp.iso.

Here is the screenshot:

[http://i74.photobucket.com/albums/i246/burn1984_2006/VMWareError.png](http://i74.photobucket.com/albums/i246/burn1984_2006/VMWareError.png)

I dont know why it went to network boot?

If you click on the cdrom icon does it still show the iso as set up? (I assume that it's the floppy drive that has the red cross on it.)

If the iso is set up correctly, as the cdrom icon indicates, then the iso must not be bootable.  (So there *is* something wrong with your iso.)

---

### Post by fenixphire07 on 2007-11-20
hey, ok i'm guilty of being lazy ;) i have installed VMWare Server 1.0.4 successfully, plus i have installed Windows Professional XP successfully again...WOAH!!!

Anyway, now i have a problem, no internet. How can i set up a link to the connection i have on Ubuntu 7.10 Gutsy Gibson. I'm running a PPPOE which requires authentication, so the user name and password can't be reused for connection. 

What do i do? Pls, i'm not a networking guy so pls give me step by steps..if u dnt mind awfully...

PS. If i can get this working...GOODBYE DUAL BOOT..WELCOME UBUNTU AND LINUX.. (insert EVIL LAUGH HERE)

thank you in advance..

FENIXPHIRE - Hope is always there
-------------------------------------------
I'm addicted and I am loving it...

I open my mouth, let out a scream, and the silence is deafening...

---

### Post by veloce on 2007-11-20
> **fenixphire07 said:**
> hey, ok i'm guilty of being lazy ;) i have installed VMWare Server 1.0.4 successfully, plus i have installed Windows Professional XP successfully again...WOAH!!!

Anyway, now i have a problem, no internet. How can i set up a link to the connection i have on Ubuntu 7.10 Gutsy Gibson. I'm running a PPPOE which requires authentication, so the user name and password can't be reused for connection. 



If you want step by step, search for a howto. :)

The answer depends on the answers you gave about networking during setup.

If you set up bridged networking then your vm should see the internet anytime your ubuntu is connected.

---

### Post by popophobia on 2007-11-20
Help.
I'm having problem with the step where it asks for the header of the kernel. I installed PHC to control my cpu voltage before (modding kernel a little bit).  Now I get error why trying to install vmware.

> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /lib/modules/2.6.22-14-generic/build/include

The path "/lib/modules/2.6.22-14-generic/build/include" is a kernel header file
directory, but it is not part of kernel source tree.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 


What would I do? I tried to install the header again, even the kernel from apt-get. Doesn't seem to fix the problem.

---

### Post by bparncutt on 2007-11-22
Anyone willing to listen,

I installed VMware server beta 2.0 and it wouldn't run.  Everything seemed to install correctly.  Unfortunately, I deleted the /etc directory which contained vmware server.  Now i can neither uninstall or reinstall the program.  any suggestions?

---

### Post by fusion.fake on 2007-11-25
hi, 

im running vmware server and xp now on ubuntu, but i can't manage to see my ipod in XP :/ i added usb connector but still no luck, it shows however in ubuntu.

does anyone have a solution or any tips ? 

thanks :)

---

### Post by o3h on 2007-11-26
Hello when i run the installtion script and have answered a couple of questions i get the following error.
Any one who can help me?

```
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

```

---

### Post by auskento on 2007-11-29
This is getting really frustrating now, everything installs fine, but vmware will just not power up any instances.

I get the following log entries, no matter what i have tried.

```

Nov 29 22:28:01: app| Adding to list of running vms: /var/lib/vmware/Virtual Machines/XP/Windows 2000 Professional.vmx
Nov 29 22:28:01: app| Attempting to launch vmx : /var/lib/vmware/Virtual Machines/XP/Windows 2000 Professional.vmx
Nov 29 22:28:01: app| New connection on socket server-vmxvmdb from host localhost (ip address: local) , user: root
Nov 29 22:28:01: app| Connection from : /var/lib/vmware/Virtual Machines/XP/Windows 2000 Professional.vmx
Nov 29 22:28:01: app| Setting up autoDetect info.
Nov 29 22:28:01: app| VMServerdConnect: connecting to /var/lib/vmware/Virtual Machines/XP/Windows 2000 Professional.vmx
Nov 29 22:28:02: app| Failed to connect to vm: /var/lib/vmware/Virtual Machines/XP/Windows 2000 Professional.vmx
Nov 29 22:28:02: app| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
Nov 29 22:28:02: app| Error during launch: 11, The process exited with an error:
Nov 29 22:28:02: app| End of error message
Nov 29 22:28:02: app| Operation failed to change the VM to the expected power state.
Nov 29 22:28:02: app| VM suddenly changed state: poweredOff.
Nov 29 22:28:02: app| VM suddenly changed state: poweredOff.

```

I am running a console linux server only

Dapper 6.06 LTS
GCC 4.0.3
All depndencies are met
Running a 750GB SATA HDD

---

### Post by psychobeauty on 2007-12-01
hello..

i ve done all the steps correctly..but vmware player does not launch...
why??

---

### Post by Scruffynerf on 2007-12-01
Edit: Nevermind - please delete

---

### Post by jacobsn on 2007-12-09
Hey.. Im new to linux and have a problem.

when i try to install i the terminal writes 

'
Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

'

I have wrote following in the terminal.

'
Installing the content of the package.

In which directory do you want to install the binary files? 
[/home/jacob/vmware] /home/jacob/vmware

The path "/home/jacob/vmware" does not exist currently. This program is going 
to create it, including needed parent directories. Is this what you want? 
[yes] yes        

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] /etc

What is the directory that contains the init scripts? 
[/etc/init.d] /etc/init.d

In which directory do you want to install the daemon files? 
[/home/jacob/sbin] /home/jacob/sbin

The path "/home/jacob/sbin" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] yes

In which directory do you want to install the library files? 
[/home/jacob/lib/vmware] /home/jacob/lib/vmware

The path "/home/jacob/lib/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] yes

In which directory do you want to install the manual files? 
[/home/jacob/man] /home/jacob/man

The path "/home/jacob/man" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] yes

In which directory do you want to install the documentation files? 
[/home/jacob/doc/vmware] /home/jacob/doc/vmware

The path "/home/jacob/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] yes

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

'

---

### Post by veloce on 2007-12-10
> **jacobsn said:**
> 

'
Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

'
'

You need to run these as root.  To do this, precede the commands with "sudo ".  It will ask you for a password - use the one you logged in with.

---

### Post by dcstar on 2007-12-22
> **KillaB7 said:**
> For those using Gutsy, I just wanted to point out that this guide worked flawlessly for me.
[http://lunapark6.com/ubuntu-710-gutsy-desktop-edition-review.html](http://lunapark6.com/ubuntu-710-gutsy-desktop-edition-review.html)
.......
Now I just need to get Samba to play nice so I can move files in both directions.

Using Synaptic, I just installed vmware-server from the Gutsy repos and it seemed to install fine (all I needed was a S/N), is this the way it should be done now that it is in the repos?

---

### Post by CanonKen on 2007-12-27
I did the same, installed from repos too then just kept an eye on the tutorial as I was going along, install went great, put a couple of programs on that i might need, everything seems to be working OK, I can do away with Wine now.
My only gripe now is the "restart windows" messages that I haven't seen for months :)

---

### Post by Orfintain on 2007-12-28
Gusty 7.1

I just installed VMware and I'm getting 
Try 'man vmware' for more information.

when i try to run "vmware" or "
sudo vmware"

installation seamed to fine but there is nothing new in my system tools either

thanks

---

### Post by dcstar on 2007-12-28
> **CanonKen said:**
> I did the same, installed from repos too then just kept an eye on the tutorial as I was going along, install went great, put a couple of programs on that i might need, everything seems to be working OK, I can do away with Wine now.
My only gripe now is the "restart windows" messages that I haven't seen for months :)

I have also found that I could import my current Windows XP install into a vmware virtual machine with the free utility available from the vmware site!

No need to do a fresh Windows install and then reinstall all of your apps, just do the import (a Windows executable) and off you go!

I have my vm Windows now using my USB Linux printer and also recognising my Sony USB Walkman (although it is bloody slow......), my vm Ubuntu goes a lot faster.....    :-)

---

### Post by Orfintain on 2007-12-28
When I 

laptop:~$ sudo /usr/bin/vmware-config.pl

Making sure services for VMware Server are stopped.

Bridged networking on /dev/vmnet0 is running
Host network detection is not running
Module vmmon loaded
Module vmnet loaded
Stopping VMware autostart virtual machines:
   Virtual machines                                                    done
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent

I get the here and just stops I can still enter and move done and line but process seams to have just stopped...

---

### Post by sf_basilix on 2007-12-29
I'm getting the same error as Orfintain:

I installed the latest version of Ubuntu Desktop (just downloaded two days ago), and then installed VMWare server, which was successful, but when I run vmware from the command line as such:

$ vmware
or
$ sudo vmware

all I get is this:

"Try 'man vmware' for more information"

I cannot find the icon for VMWare in the  System Tools menu, because my installation (default for everything) does not show a System Tools menu (version is the latest Ubuntu Desktop).  I even patched the entire Ubuntu system, but cannot find the System Tools menu under Applications.

Is there an option or another way to pull up the vmware console so I can install windows on vmware?

Also - how can I show the System Tools menu in my Ubuntu Desktop version?

Thanks in advance!

---

### Post by CanonKen on 2007-12-29
Try right clicking on your menu buttons, edit menus, make sure you have system tools checked.
System tools will then appear in the left hand column, highlight it, then put a tick in the VMWare Server Console.

---

### Post by ronb94 on 2007-12-29
hello
because of some problems i removed vmware and tried to install again. i am getting this messege:
[HTML]The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmnet
vmmon

Execution aborted.[/HTML]
thanks

---

### Post by sf_basilix on 2007-12-30
OK, so with a little bit of digging here is my analysis:

Apparently, because I was using the 64 bit version of Ubuntu, VMWare does not ship (or compile) a 64bit version of it's GUI - they only have a 32 bit version which installs in the sub-menus.  I did come across another blog which illustrated the files needed to install 32 bit libraries to get it to run, but that just seemed silly once I found out the other way.

So, instead of typing vmware, you would just open a browser and put in [http://localhost](http://localhost) (you may need to add a port at the end, if needed - this is specified during the install, if the port is anything other than 80).  Once you connect locally, you will need to login as root.  If you do not have a password set for root, you will need to change it through the command line before proceeding.  Then after logging in, you'll need to install a firefox plugin - which a link is available through the web-gui.

Not as nice as having a console, but it seems to work about the same way.  The only thing I haven't been able to do is run full-screen with the auto-hide menu bar at the top - like the older server had.  I really miss that!  If its there somewhere, someone please post a followup....

---

### Post by sf_basilix on 2007-12-30
> **ronb94 said:**
> hello
because of some problems i removed vmware and tried to install again. i am getting this messege:
[HTML]The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmnet
vmmon

Execution aborted.[/HTML]
thanks

After you run the uninstaller script, I would remove any vmware directories and/or config files left behind.  The installer does not remove everything that it imagines you to believe.  There were a significant number of vmware directories and config files left behind in /etc, /var and /lib (if I remember correctly).  Try running this:

$ sudo find / -print | grep vmware

and you will see the plethora of junk left behind.  I did this myself and removed everything but the man pages and documents as these are not necessary and will be overwritten.  After you uninstall everything manually, I would reboot before reinstalling - to ensure that all services were indeed dropped from memory, if any were accidentally left running (although that isn't as likely, but definitely ensures it)

---

### Post by sf_basilix on 2007-12-30
> **ronb94 said:**
> hello
because of some problems i removed vmware and tried to install again. i am getting this messege:
[HTML]The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmnet
vmmon

Execution aborted.[/HTML]
thanks

oh... also check your modules config file - I'm not in front of my system or I'd tell you where it is.  I'm sure it does something in there.  Are you using the uninstall.pl script within the downloaded tar directory from vmware?

Updated:

I also came across this:

remove this service by editing your xinetd config file:

service vmware-authd
{
disable = no
port = 902
socket_type = stream
protocol = tcp
wait = no
user = root
only_from = 192.168.0.0/24
server = /opt/vmware/server/sbin/vmware-authd
type = unlisted
}

check for any other vmware services that may be in there....

---

### Post by ronb94 on 2007-12-30
ok i uninstalled the beta 2 version and installed the 1.04, but when i try to power on the virual machine i get this:
[IMG]http://img338.imageshack.us/img338/4352/screenshotwindowsxpprofse0.png[/IMG]

---

### Post by Zenerek on 2008-01-03
Bah,I was hoping i could solve the gaming issue with this or something like it but i understand, and it makes sense why it why it currently is not possible, kinda like when i ran winamp in wine and file would not play...or something like that, reason probably because ubuntu did not have that codec installed then...makes me wonder if it might work now?

Anyway i was hoping it might be possible(though i would be it was not) to game via a stripped down vmwared xp...oh guess me and bunch of others will stay using windows for gaming...damn.

---

### Post by dimaoo7 on 2008-01-04
I've installed VMware 1.04 and created a new VMachine for Windows XP, however with the CD in the drive I just get a blank screen for a few seconds and then it returns to the VM Screen. I've even tried booting from the XP ISO file but still the same thing happens. Any suggestions?

---

### Post by mezcla on 2008-01-21
Ok, I have successfully installed vmware server and windows XP Pro.  I am unable to get my internet connection to work.  What info would be needed to troubleshoot this?  I have tried changing from Bridged to NAT and back to no avail.  My Ubuntu connection works fine.  In XP all I can see is "acquiring network address" but it never finds the connection.  My internet is wired but through a router.  I've read through and searched most of this thread/google and cannot find a clear answer.  It seems to just work in all the how-tos.

Any help would be awesome, thanks in advance.

---

### Post by geezerone on 2008-01-23
I used to have vmware player/server working but get errors configuring vmnat etc when trying upgrades and saw an error "gcc 4:4.1.1 needs 4:4.0.3-1" and the same for g++?

I have an XP installation but if the above can't be easily fixed is there a way to save the XP installation and use on a brand new vmware installation?

TIA

---

### Post by big dizzle on 2008-01-27
> **Endwin said:**
> I had the same problem aparently it validates the key through some X11 library if you install libx11-dev and/or libx11-6 it should work.

your suggestion worked perfectly :)

---

### Post by Beowulf.1000 on 2008-01-27
> **Peturrr said:**
> Are you too having problems with software that is only available on Windows and not on Linux? Are you still Dual Booting to solve this problem? After this HowTo you will never need to dual-boot again for your windows only software, like Adobe CS!
[SIZE=4]**Info[SIZE=6][SIZE=3][/SIZE][/SIZE] **[/SIZE] That sounds great, but how?
Did you ever heard about Virtual Machines? ....

I keep going through the configuration, getting a message it was installed, then I run "vmware" and am back at square one. No joy. Ubuntu 7.10. 
[INDENT]The configuration of VMware Server 1.0.4 build-56528 for Linux for this running kernel completed successfully.

beowulf@ubuntu:~/vmware-server-distrib$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

beowulf@ubuntu:~/vmware-server-distrib$
 
[/INDENT]

---

### Post by emtjr928 on 2008-01-30
I am trying to install vmware using this guide and have a problem that I can't fix myself. The installation runs untill it gets to the vmmon module when I get this:

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.0.3", while you are trying to use 
"/usr/bin/gcc" version "4.1.2". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.1.2" anyway? [no]


If I let it go ahead it aborts. My system does have gcc 4.0.3-4 installed.

Any help would be appreciated.
Thanks,  Ed

---

### Post by evarlast on 2008-01-31
I have the same problem as ronb above and this is in my vmware-serverd.log file

Jan 31 21:56:00: app| Adding to list of running vms: /var/lib/vmware/Virtual Machines/whs/whs.vmx
Jan 31 21:56:00: app| Attempting to launch vmx : /var/lib/vmware/Virtual Machines/whs/whs.vmx
Jan 31 21:56:00: app| Error during launch: 11, The process exited with an error:
Jan 31 21:56:00: app| End of error message
Jan 31 21:56:00: app| VmsdVmStatePendingCmdFailed: cmd status is already set
Jan 31 21:56:03: app| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
Jan 31 21:56:03: app| SP: Deleting user session: 0 username: jrwren


I google for VmsdVmStatePendingCmdFailed and vmdbPipe_Streams Couldn't read and I find many people with the same problem, but no solutions!


Until I stumbled across someones LiveJournal where they said... check the permissions on ~/.vmware.  sudo had marked it as root!  :(

sudo chown $USER ~/.vmware

FIXED ALL MY PROBLEMS!!!

SHEESH!

---

### Post by santam on 2008-02-05
Thanks, Thanks and more thanks,
I have been using Linux exclusively for the past 8 months and till date there were just 2 softwares that were making me want to go back to Windows or at least to dual boot - Google talk and SPSS. Both work flawlessly from inside Ubuntu now and my computer nirvana is here at last.
Thanks once again
Santam

---

### Post by highpitch on 2008-02-28
Use the vmware-uninstall.pl to uninstall VMWARE. If the vmware is somehow corrupted, try reinstall first, then uninstall.

---

### Post by Pro4Life on 2008-03-02
Hello everyone Awsome thread :) 
I've done everythink and workd so fare like a charm I have the menu VMPlayer but when I fire it up it says that can't open EULA.txt in /usr/lib/vmware/share ;]] I go to that directory in Terminal tried to open the file manualy and get error corupted or something. I delete it and I wanted to create anather EULA.txt but : bash: EULA.txt: Permission denied (I use sudo) and I can accept the agreement. Stupid hah ;]] suggestions ?? :confused:

Edit: I get it working ;) new file creation was imposible but copying was  .. Everything is fine now :)

---

### Post by frogotronic on 2008-03-02
Hi,

I have two problems which I haven't been able to solve:

1) I'm getting a strange error with some programs on VMWare Server 1.0.4 on Gusty Gibbon.  Basically the XP program incorrectly interprets the resolution and refuses to run.  Please see attached png image.  Current issue is with TurboTax2007.  There** must** be a workaround for this issue.  I installed VMWare server from Synaptic and  have VMWare tools installed (via the VM menu).

2) Can't get USB devices to install correctly.  Always ends up with an "Error Code 10 - this device can't start" when I check it with the XP Device manger.

Any suggestions on either of these problems would be appreciated.

- CH

---

### Post by Peturrr on 2008-03-02
I have not been very active here keeping this guide clean, so today I updated it. 

**Gutsy and Feisty users can now just use the vmware-server from the repo's !**

** Check the updated instructions in the main post.**

I won't be able to help you guys with problems, but it looks like everybody is helping each other, so that will be no problem.

---

### Post by jmattos on 2008-03-04
Everything seems to be going fine when I run 

```

 sudo /usr/bin/vmware-config.pl

```

until I get to...

```

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Unable to compile the VMware VmPerl Scripting API.

********
The VMware VmPerl Scripting API was not installed.  Errors encountered during 
compilation and installation of the module can be found here: 
/tmp/vmware-config5

You will not be able to use the "vmware-cmd" program.

Errors can be found in the log file: 
'/tmp/vmware-config5/control-only/make.log'
********

Hit enter to continue. 

Generating SSL Server Certificate

Unable to copy the source file /usr/lib/vmware-server/serverd/init.pl.default 
to the destination file /usr/lib/vmware-server/serverd/init.pl.

Execution aborted.


```

When I look in /usr/lib/vmware-server/serverd/ I dont see anything in there... Argh.

Anyone know what ?I'm doing wrong? I've attached the make.log file. I'm no C programmer, this is for sure....

---

### Post by bharadwaj on 2008-03-04
Or try vBox easy and stable....

---

### Post by SloYerRoll on 2008-03-04
UPDATE: Fixed the problem. Please disregard question.:P

New install of Ubuntu here:

I did search this thread and was surprised to see my simple problem hadn't been addressed. (at least that I saw)

I ran:
sudo gedit /etc/apt/sources.list
and uncommented the two lines requested in the tut..

Then I ran:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
and it tells me:
bash:deb: command not found

What gives? I'm new to Ubuntu, but have been able to stumble my way through most things. 

Thanks for your time and help. 

-Jon

---

### Post by jmattos on 2008-03-04
Okay, I've made some progress. I have installed the "libssl-dev" package and after I've done that, I re run the -config command and I get....I'm still choosing all the defaults. The problem seems to be in the certificate now...

I found this answer [here]("http://www.linuxquestions.org/questions/linux-software-2/vmware-server-install-error-the-vmware-vmperl-scripting-api-was-not-installed.-476129/") to get past the first problem (the perl problem)
I then copied the pl file to the directory manually to /usr/lib/vmware-server/serverd and things SEEEEEEM to work fine, but now im getting

```

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files? 
[/home/jmattos/virtualmachines] 

Do you want to enter a serial number now? (yes/no/help) [no] yes

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  9004D-YKE6G-13JD4-4KD29

[COLOR="Red"]VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

The configuration of VMware Server 1.0.3 build-44356 for Linux for this running
kernel completed successful[/COLOR]

```

this happens when I run the -config command again, too. I can't figure out where the issue is in the configuration.. any ideas?

---

### Post by tcs1400 on 2008-03-05
Would installing the Virtual Machine still work if you only had the system restore disk for the computer, since it recognizes the hardware. It is still the same hardware but can it still install through ubuntu

---

### Post by jonelnz on 2008-03-05
A big big thank you to Peturr and all who contibuted to this How-to.
Couldn't believe how easy it was to install and setup VWWare Server.
The only problem i had was a minor typo in the initial terminal window:
file not found! vmware-serve (duuh!) and trying to use VMWare Workstation serial No. for VMWare Server (duuh!)

Once again thanks Peturr for this  :guitar:

---

### Post by Peturrr on 2008-03-13
@sloyerroll:
The command you give: deb [..] is not mentioned in the guide. That command also does not exist, therefore the error.
The 2 lines that are mentioned are not commands, they need to be uncommented. After that, you save the file and enter the command ```
sudo apt-get update && sudo apt-get install vmware-server
```

---

### Post by Peturrr on 2008-03-13
@tcs1400: I don't know. The hardware is part emulated, but the only thing I can say is: just try it out. :)

---

### Post by Jimi B on 2008-03-25
Hi guy, sorry to newb it up in here but I've googled until my eyes bled and I still can't find a solution to my problem. 

I've installed VMWare on my Hardy AMD 64 system, but whenever I try and start it up I get this error:

```
$ vmware
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)

```

Someone suggested I tried installing an older version of the ia32libs, and that got VMWare working, but I just got more errors when trying to 'power on' the virtual machine, I tried following the tips online but none of them worked for me, although there was one suggest that i... yep... updated to the latest ia32libs, which brings us tidily back round to this problem again!

EDIT:

Obviously I didn't google hard enough:

> 
Since two days I&#8217;m running a beta of Ubuntu Hardy and also since two days, my VMware Server Console refused to work. As it turned out, this was caused by two libraries shipped with the VMware Server Console: libpng.12.so and libgcc_s.so.1. Since the library pathes aren&#8217;t hard-coded into the executable, all we&#8217;ve got to do is move VMware&#8217;s version of the offending libraries out of the way:

cd /usr/lib/vmware-server-console/lib/libgcc_s.so.1

mv libgcc_s.so.1 libgcc_s.so.1.org

cd ../libpng12.so.0

mv libpng12.so.0 libpng12.so.0.org


So I'm past that original error and I'm stuck with the 'power on error' 

```
Unable to change virtual machine power state: The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

POST(no connection): Failed to initialize monitor device.

Failed to initialize VM.
End of error message.
```

I just can't win with this, the more i try the harder it gets to work out. I tried that any-any patch, but that just leads into further alleys of despair

```
 Updating /usr/bin/vmware-config.pl ... corrupted
The file /usr/lib/vmware-server/modules/source/vmmon.tar that this script was 
about to install already exists. Overwrite? [yes] y

The file /usr/lib/vmware-server/modules/source/vmnet.tar that this script was 
about to install already exists. Overwrite? [yes] y

Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware-server/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware-server/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware-server/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] y

sh: /usr/bin/vmware-config.pl: not found

```

I'm pretty much at the giving up stage now :(

---

### Post by jonask on 2008-03-26
sounds great!! I have a HP dv9700t laptop with ubuntu installed. I have tried to install windows xp as well, but apparenty the computer is so "new that xp donte reginize the hard ware/harddrive" Do somebody know if it would work to install xp with the WMware?(I just need it for photoshop and cant get it to work with wine)

cheers

Jonas

---

### Post by robertchahine on 2008-03-28
> **jonask said:**
> sounds great!! I have a HP dv9700t laptop with ubuntu installed. I have tried to install windows xp as well, but apparenty the computer is so "new that xp donte reginize the hard ware/harddrive" Do somebody know if it would work to install xp with the WMware?(I just need it for photoshop and cant get it to work with wine)

cheers

Jonas

read this article [http://news.softpedia.com/news/Install-Photoshop-CS2-on-Your-Ubuntu-PC-77260.shtml](http://news.softpedia.com/news/Install-Photoshop-CS2-on-Your-Ubuntu-PC-77260.shtml)

they could install photoshop cs2 with wine

---

### Post by robertchahine on 2008-03-29
please help.
when i wrote in the terminal
```
vmware
```

i get this error:

/usr/bin/vmware: 166: cannot open /etc/vmware/locations: No such file
exec: 180: /lib/wrapper-gtk24.sh: not found

---

### Post by robertchahine on 2008-03-30
i removed vmware and installed from synaptic , i still have the same error 
```
/usr/bin/vmware: 166: cannot open /etc/vmware/locations: No such file
exec: 180: /lib/wrapper-gtk24.sh: not found

```

---

### Post by Paladin Michael on 2008-04-03
I'm not sure if this is useful information for anyone, But I have my virtual machine in a sub-directory of my home directory in order to avoid the necessity of using sudo when I'm dealing with vmware.  So far it does this nicely.  

The default location for the virtual machine was /var/lib/vmware-server/Virtual Machines/<vmname>.  I've tested it now and I can play inside that 'Virtual Machines' directory so I was probably overcautious, but others dealing with the need for using sudo for vmware made me wonder if others should try this or if they were simply being creative about where they put their virtual machines.

---

### Post by gmcauley on 2008-04-08
Thanks for the Howto!

> **Peturrr said:**
> 
[*] Hopefully it detects your Windows install CD and will start the installation! If it won't boot from the CD, stop the virtual machine and check/change the preferences for the virtual machine regarding the CD drive.
 
My Windows install CD does not seem to be detected.  When I try to "power on" the vm a dialog box pops up saying:
```
Unable to change virtual machine power state: The process exited with an error:
End of error message.
```

I guess I can't be sure that this error means CD detection is the problem.  In any case I tried various CD drive settings for the vm, and still the same result (see attached image for current settings).  

Any clues would be much appreciated.

---

### Post by veloce on 2008-04-09
> **gmcauley said:**
> Thanks for the Howto!


 
My Windows install CD does not seem to be detected.  When I try to "power on" the vm a dialog box pops up saying:
```
Unable to change virtual machine power state: The process exited with an error:
End of error message.
```

I guess I can't be sure that this error means CD detection is the problem.  In any case I tried various CD drive settings for the vm, and still the same result (see attached image for current settings).  

Any clues would be much appreciated.

This isn't to do with the cd.  The first thing you need is to actually get the error message.  VMWare doesn't give you the error message unless debugging is on, this is a simple option on your vm.  In vmware server console:

[LIST=1]
[*]select your vm and press edit settings
[*]select the "options" tab
[*]select "advanced"
[*]Check the "run with debugging information" box
[/LIST]

When you try to start the vm you should actually get an error message.  Let us know what it is and we can go from there.

---

### Post by gmcauley on 2008-04-09
Thanks for your reply.  I greatly appreciate your help.

Here is the error message:```
vmxvmdb: Index name being generated from config file
POST(no connection): Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

POST(no connection): Failed to initialize monitor device.

Failed to initialize VM.
```

I installed vmware-server-kernel-modules and vmware-server-kernel-modules-2.6.22-14.  Adept confirms that they are installed.

I am rather new at this but I tried:
```
grant@zzz:~$ sudo modprobe vmmon
[sudo] password for grant:
FATAL: Module vmmon not found.

```

Further help would be greatly appreciated!

---

### Post by gmcauley on 2008-04-09
Ok - I was booting a different kernel than 2.6.22-14-generic.

It works!  Thanks Peturrr for the Howto, and thanks veloce for your reply.

I am installing XP as I write this.

---

### Post by jmullagh on 2008-04-10
I am excited about this product and plan on using it this week end. However, I have a question.Anti-Virus, Firewall and Spam that you normally use when employing windows, do you have to install various anti-virus software on the 'Windows' (guest)  virtual machine or does it utilize the Linux (Host) and use those resources? I have been looking around and cannot find an answer to this question... yet. The whole reason for my changeover a few years back to Linux was because of all the virus/spam/adware issues associated with teh Windows environment! I do not want a return to that....

---

### Post by ninar on 2008-04-15
> **Jimi B said:**
> Hi guy, sorry to newb it up in here but I've googled until my eyes bled and I still can't find a solution to my problem. 

I've installed VMWare on my Hardy AMD 64 system, but whenever I try and start it up I get this error:

```
$ vmware
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)

```

Someone suggested I tried installing an older version of the ia32libs, and that got VMWare working, but I just got more errors when trying to 'power on' the virtual machine, I tried following the tips online but none of them worked for me, although there was one suggest that i... yep... updated to the latest ia32libs, which brings us tidily back round to this problem again!

EDIT:

Obviously I didn't google hard enough:



So I'm past that original error and I'm stuck with the 'power on error' 

```
Unable to change virtual machine power state: The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

POST(no connection): Failed to initialize monitor device.

Failed to initialize VM.
End of error message.
```

I just can't win with this, the more i try the harder it gets to work out. I tried that any-any patch, but that just leads into further alleys of despair

```
 Updating /usr/bin/vmware-config.pl ... corrupted
The file /usr/lib/vmware-server/modules/source/vmmon.tar that this script was 
about to install already exists. Overwrite? [yes] y

The file /usr/lib/vmware-server/modules/source/vmnet.tar that this script was 
about to install already exists. Overwrite? [yes] y

Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware-server/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware-server/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware-server/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] y

sh: /usr/bin/vmware-config.pl: not found

```

I'm pretty much at the giving up stage now :(

Hi guys,

I got the same problem as Jimi B,  its VMserver on Hardy AMD 64 system. After the installation I can't launch to the vmware.
 
```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
```

who can help me?

---

### Post by ninar on 2008-04-15
Now it works!!

I have fixed this problem.


```
cd /usr/lib/vmware/lib/

sudo mv libpng12.so.0/libpng12.so.0 libpng12.so.0/libpng12.so.0.disabled

sudo ln -sf /usr/lib/libpng12.so.0 libpng12.so.0/libpng12.so.0

sudo mv libgcc_s.so.1/libgcc_s.so.1 libgcc_s.so.1/libgcc_s.so.1.disabled

sudo ln -sf /lib/libgcc_s.so.1 libgcc_s.so.1/libgcc_s.so.1
```

But I got another error:

```
 Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7041767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf70418b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7ec329d]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7db0969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7db0f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf6180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf6d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bc6c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bd324f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bc6c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7bd2b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad7298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad7586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad977e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7cec459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cd43a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7cd4076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7ceb6eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7cead46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7ceb0b8]
vmware: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
```

It was solved with:

```
ln -s /usr/lib32 /usr/l32
sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

---

### Post by robertchahine on 2008-04-15
and now you can install any os and work all fine?

---

### Post by ninar on 2008-04-20
I install win xp on vmserver, it works no problem at all.

---

### Post by dimaoo7 on 2008-04-25
I've just upgraded to Hardy, during the upgrade the vmware was uninstalled. Now when I try to install it I get the 
```
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

```
Message, however the suggestions in the first page do not work as the vmware directory isn't there.

Any suggestions?

---

### Post by nick09 on 2008-04-27
How do I install this with Hardy?

---

### Post by dhysk on 2008-04-28
It's been asked a few times in this thread already.  Can you run your ACTUAL, CURRENT, XP install with VMserver?  YES you can

I haven't read all the pages but for anyone interested here is a quick tutorial once you get VMserver running. 

[http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/)

Basicaly all you do is create another hardware profile under XP with the VMware's drivers for the disks.  Create a virtual machine using VMserver threw linux that uses the actual physical drives on your computer making sure to include Linux and Win partitions for the complete grub loader.  And most of all DONT EVER EVER EVER EVER boot into linux threw the server while your already using it.. ITs bad.. trust me.  

However you can recover linux threw the command line.. I love Linux.  Basically if you screw up you will loose x session and the Linux root drive will be corrupted.

---

### Post by Tnhl1989 on 2008-05-01
I get this error. How do i get access rights?


The path "/home/tony/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

---

### Post by dhysk on 2008-05-04
this might be dumb but did you run it as root?

---

### Post by Bookmaster on 2008-05-04
Is it works with amd64 versions of Ubuntu please?

---

### Post by Tnhl1989 on 2008-05-04
Yes i did run it as root

---

### Post by Mr_B on 2008-05-06
> **nick09 said:**
> How do I install this with Hardy?

There is a quick tutorial here:
[http://howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p5](http://howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p5)
Scroll 3/4 down the page for the VMware install instructions, including a link to patch needed.

---

### Post by dhorkoff on 2008-05-15
> **ninar said:**
> Now it works!!

I have fixed this problem.
<SNIP>


Excellent post Ninar! Exactly what I needed to fix VMWare on my Hardy AMD64 (upgraded from Gutsy) install. For others out there, I only needed to do the first part of your post to make things work. There is no need to run the sed commands with the current version of Hardy.

---

### Post by unused_bagels on 2008-05-17
I'm a noob, does this work on HH? And did they ever get 3D support so I could play my windows games?

---

### Post by Ron@ld on 2008-05-26
Hello all,

I new here and I have recently installed Ubuntu 8.04.
So I left Windows on my private computer, but for my works I need some windows tools.

So, I already use VMWare on my Windows machine and now I want to use VMWare on my Linux machine to do some windows things.

I have installed the VMWare server, but I get the following error;

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Is there anybody who could help me?

Thanks.

---

### Post by erick_tuk on 2008-05-30
Hi, I've been using Ubuntu for two years now and I've never been happier with my lapton in my entire life haha, now I installed vmware and have Windows XP in a different desk, using the cube from compizfusion, I have a hp 530 centrino duo, so I use 1 processor for linux and the other for XP, 512 ram each, look at it! haha so cool

---

### Post by bigteks on 2008-06-11
I'm getting a bluescreen (in the guest) trying to boot my Windows XP guest under my Ubuntu 8.04 VMware server 1.0.6.

I created the guest using ghost + converter. The guest works great on my Windows XP VMware server 1.0.6. When I tried to run it on the Ubuntu server first I had to create a new config for the guest and point it at the virtual harddrive image because the VM config that ran under XP wouldn't start at all under Ubuntu.

Once I created a new config on the Ubuntu version of VMware it seems to start - I get the Windows XP boot screen with the animated block moving back and forth at the bottom.

Then it goes blue-screen and I can't see what it says because it's only visible for half a second and then it pops into the safe boot screen. None of the safe boot options work - they all start to boot and then go into bluescreen for 1/2 second and then back to the safe boot screen again.

Any ideas on what might be wrong or how to go about debugging this?

This is a laptop. What I've done is turned the original laptop OS into a guest and replaced the Windows base OS with Ubuntu. So the guest that is having so much trouble is the original OS from this physical machine, just running now as a VM under Ubuntu.

---

### Post by blznheem on 2008-06-26
These are the errors which I am getting:
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

Please help me out to solve this issue

---

### Post by imjscn on 2008-06-28
I'm new...where to download the vmware server? I'm using Xubuntu, I can't find WMware in Add/Remove, I see several components in Synaptic Package Manager under the vmware catalog but none of them looks like the thing.

When install WinXP, does VMware reqire a certain information of winxp version? I wish to install an extra-mini-xp, it cut off xp's nonsenses, keeps only the nessesoray components. So, the version and the CD's name doesn't match standard xp. Is it a problem?

---

### Post by bodhi.zazen on 2008-06-28
> **imjscn said:**
> I'm new...where to download the vmware server? I'm using Xubuntu, I can't find WMware in Add/Remove, I see several components in Synaptic Package Manager under the vmware catalog but none of them looks like the thing.

When install WinXP, does VMware reqire a certain information of winxp version? I wish to install an extra-mini-xp, it cut off xp's nonsenses, keeps only the nessesoray components. So, the version and the CD's name doesn't match standard xp. Is it a problem?

See if this link helps with the VMWare part :

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Good luck with the rest, no comment on legality ... but I do not think you are "allowed" by the EULA to do that (so please do not look to the Ubuntu forms for support of the modified windows thing).

---

### Post by froller on 2008-06-30
Ninar,

Thanks for the fix.  I didn't have the second error though.  I used the following installation procedure at:

[http://www.iki.fi/kuparine/comp/ubuntu/en/server.html](http://www.iki.fi/kuparine/comp/ubuntu/en/server.html)

coupled with your fix.  The build is on an Acer Aspire 7520 laptop.

Thanks again, good work.

Fred

---

### Post by fishman78 on 2008-07-02
Hi Everyone,

   Here are the errors I got after installing the vmware package.  Everything seemed okay, no noticeable errors.  Any help on how to fix this would be greatly appreciated!!

[COLOR="Blue"]image@image-desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
image@image-desktop:~$ [/COLOR]

Thanks again!

Kurt

---

### Post by tdn on 2008-07-09
How do I install VMWare Server in Ubuntu 8.04 Hardy Heron?

---

### Post by bodhi.zazen on 2008-07-09
> **tdn said:**
> How do I install VMWare Server in Ubuntu 8.04 Hardy Heron?

There is a sticky in the Virtualization forums.

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934")

---

### Post by bodhi.zazen on 2008-07-09
> **fishman78 said:**
> Hi Everyone,

   Here are the errors I got after installing the vmware package.  Everything seemed okay, no noticeable errors.  Any help on how to fix this would be greatly appreciated!!

[COLOR=Blue]image@image-desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
image@image-desktop:~$ [/COLOR]

Thanks again!

Kurt

There are a number of solutions posted in various locations.

```
sudo rm /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
```

---

### Post by borlosky on 2008-07-11
would i be able to setup vmware to run an already installed version of xp within ubuntu? i'm currently dual booting with xp and ubuntu 8.04. i would think it wouldn't be that difficult to run vmware and use my current installation of xp to run instead of installing xp again within vmware.


::edit:: i would normally look for a solution in the thread, but there are just WAY too many pages to go thru efficiently, or if someone can point me at least to a certain page of the thread to find an answer would be greatly appreciated.

---

### Post by bodhi.zazen on 2008-07-11
> **borlosky said:**
> would i be able to setup vmware to run an already installed version of xp within ubuntu? i'm currently dual booting with xp and ubuntu 8.04. i would think it wouldn't be that difficult to run vmware and use my current installation of xp to run instead of installing xp again within vmware.


::edit:: i would normally look for a solution in the thread, but there are just WAY too many pages to go thru efficiently, or if someone can point me at least to a certain page of the thread to find an answer would be greatly appreciated.

It is experimental, but it may be possible.

---

### Post by Th3Professor on 2008-07-20
Hi, I tried all the steps (including defaults during install) in the original post and during vmware server config I received [COLOR=black]error[/COLOR]s that prevented me from completing the steps. Any ideas on how I can get this working?

Here they are:
```


The installation of VMware Server 1.0.5 build-80187 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this 
program to invoke the command for you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

You must read and accept the End User License Agreement to continue.
Press enter to display it. 

VMWARE MASTER END USER LICENSE AGREEMENT

[omitting EULA]

Do you accept? (yes/no) yes

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:161: [COLOR=black]error[/COLOR]: conflicting types for ‘uintptr_t’
include/linux/types.h:40: [COLOR=black]error[/COLOR]: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: [COLOR=black]error[/COLOR]: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: [COLOR=black]error[/COLOR]: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1659: [COLOR=black]error[/COLOR]: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] [COLOR=black]Error[/COLOR] 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] [COLOR=black]Error[/COLOR] 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmon.ko] [COLOR=black]Error[/COLOR] 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

me@pc:~/vmware-server-distrib$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```I'm running Ubuntu Studio 8.04 with Linux kernel 2.6.24-19-generic.

I see the following [COLOR=black]error[/COLOR]s standing out:

```

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path

/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here

/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here

/tmp/vmware-config0/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.
```Thanks in advance for any input, suggestions, recommendations, etc.

---

### Post by sayotte on 2008-07-20
I've encountered the same problems as the last poster; I'm using Hardy with kernel 2.6.24-16-server, and trying to get VMware-server-1.0.5-80187 working.

I tried applying the vmware-any-any-update115.tar.gz available here: [http://knihovny.cvut.cz/ftp/pub/vmware/](http://knihovny.cvut.cz/ftp/pub/vmware/)

This cleared up the error regarding a struct having no member "dumpable", but ran into a problem with a kernel header file. The error is as follows:

```

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-server/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

VMware 2 or VMware Express detected, building for VMware 2, VMware Express and VMware Workstation 4.0.x.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.24-16-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-server'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config3/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config3/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config3/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config3/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config3/vmmon-only/common/cpuid.c:15:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config3/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-server'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

```

I edited the file /usr/src/linux-headers-2.6.24-16-server/include/asm/bitops_32.h, changing this line:
```

From this:
#error only <linux/bitops.h> can be included directly
To this:
/* #error only <linux/bitops.h> can be included directly */

```

It then built, albeit with a lot of warnings, and the kernel module loaded successfully. However, I'm still getting these errors in /var/log/vmware/vmware-serverd.log:

```

Jul 20 16:11:30: app| Msg_Post: Error
Jul 20 16:11:30: app| [msg.vmmonPosix.badVersion] Version mismatch with vmmon module: expecting 138.0, got 137.0.
Jul 20 16:11:30: app| [msg.vmmonPosix.badDriver] You have an incorrect version of the `vmmon' kernel module.
Jul 20 16:11:30: app| Try reinstalling VMware Server.
Jul 20 16:11:30: app| [localized] Version mismatch with vmmon module: expecting 138.0, got 137.0.
Jul 20 16:11:30: app| You have an incorrect version of the `vmmon' kernel module.
Jul 20 16:11:30: app| Try reinstalling VMware Server.
Jul 20 16:11:30: app| ----------------------------------------
Jul 20 16:11:30: app| Msg_Post: Version mismatch with vmmon module: expecting 138.0, got 137.0.
Jul 20 16:11:30: app| You have an incorrect version of the `vmmon' kernel module.
Jul 20 16:11:30: app| Try reinstalling VMware Server.
Jul 20 16:11:30: app|
Jul 20 16:11:30: app| Msg_Post: Error
Jul 20 16:11:30: app| [msg.vmmonPosix.initFailed] Failed to initialize monitor device.
Jul 20 16:11:30: app| [localized] Failed to initialize monitor device.
Jul 20 16:11:30: app| ----------------------------------------
Jul 20 16:11:30: app| Msg_Post: Failed to initialize monitor device.
Jul 20 16:11:30: app|

```

I suspect a newer vmware-any-any-update will take care of this, but I don't see one available.

I'll try the VMWare-2.0 beta/RC and post back here if that ends up working.

---

### Post by Th3Professor on 2008-07-20
> **sayotte said:**
> It then built, albeit with a lot of warnings, and the kernel module loaded successfully. However, I'm still getting these errors in /var/log/vmware/vmware-serverd.log:

A little confused... do you mean it *is* working now but has errors in the log?

Or that it sill isn't working and also has errors in the log?

On a similar note, since this appears to be a kernel issue, if I were to go back to a previous kernel, would vmware server probably install and configure?

If that's the case, is there a specific kernel version that should definitely (hopefully) work?

Thanks!

---

### Post by sayotte on 2008-07-20
It's *not* working, but it is *close* to working. Basically it would not build before, and now it builds and runs but doesn't actually do anything useful.

The vmware-any-any update makes the vmware-config.pl and the associated kernel patches be less picky about what versions the modules will compile against et cetera. It seems that in this case, the vmware-any-any update was actually targeted at an older release of VMWare-server, so it inserted code that had a version string for an older vmmon module. The vmware-serverd detects this version string in the vmmon module when it tries to load it, and refuses to finish loading it. It might be possible to go and edit the version string, but it's probably not the best idea unless you're willing to do what the guy who maintains vmware-any-any does between each of his releases.... no idea how much work he does, do it at your own risk.


My past experiences have generally been that going with the most-common kernel and a slightly-older release of VMWare will get you the best coverage from support forums like this, patches like vmware-any-any, and so forth. So, I don't know of a specific release number or kernel version, but you might check for whatever the default kernel is for 8.04 and get the VMWare release that corresponds to vmware-any-any-update-115.



I haven't been having much luck with vmware-server-2.0 beta so far; the web admin interface is running poorly with lots of timeouts and such. Other people in IRC assure me they haven't had this problem so I am not ruling it out yet. Meanwhile, I'm installing vmware-server-1.x on a Windows machine in hopes that the idiot-proof packaging there will get me by.

---

### Post by Th3Professor on 2008-07-20
So an older vmware and an older kernel? (should work?)

...I can try that...

The Linux kernel versions don't get better with each release, yet they don't get worse. It's like a rollercoaster ride, with the ups and downs from one ver to the next.

---

### Post by Th3Professor on 2008-07-20
On 2nd thought, I had an old version before. I jsut tried the new one (1.0.6). Now it installed and configured... though when I tried "vmware" command, alone, it brought up the gcc stuff:

```

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```Any ideas?

I think I've got gcc 4.2 right now... not sure why it's not finding that. Though I don't know about the v 3.4 either. <ponders...>

EDIT:

Nevermind!

I did this:

```

[FONT=Times New Roman]sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0[/FONT]
```

And it's up and running now. :D

---

### Post by sayotte on 2008-07-20
I just got it working myself ...
Had to use a different vmware-any-any patch, which I found here: [http://www.nowhere.dk/archives/2008/03/10/updated_vmware-any-any_patch/index.php](http://www.nowhere.dk/archives/2008/03/10/updated_vmware-any-any_patch/index.php) 

Oddly the vmware-any-any-update-116 which one would expect to work better than t his addon to 115 didn't do the trick. Whatever, it works and I'm ok with that.

Happy hunting man; one of the two of us needs to document exactly what we have working on the ubuntu vmware-server wiki I think.

---

### Post by Th3Professor on 2008-07-20
You can :D <lol> :D ...but yeah it's weird.

I'm trying to get Maple Story running, though before I delve into that I've gotta get all the basic drivers and junk installed in XP. I had to switch from bridged to NAT to get online. Now to find those drivers, to get directx upgraded to v9+, who knows what else (beyond antivirus/etc. junk)...

---

### Post by Th3Professor on 2008-07-20
Okay this is odd... it's no longer working.

I had to reboot because it was acting fishy, my shift and control keys stopped working. I might have been fine with just logging out and back in, though needed a fresh reboot anyway. And it did the auto fsck, took a while... well now vmware won't run at all. I tried config again, nothing. Removing and re-installing it, nothing.

Every config attempt, and the current reinstall attempt, stop at this point:

```

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 
```

Any ideas what to do?

I've tried the various steps provided in here, nothing so far.

---

### Post by sayotte on 2008-07-20
"/usr/bin/gcc" looks suspicious, I think we overcame some errors earlier by setting the environment variable CC=/usr/bin/gcc-3.4 didn't we?
Also, the path to the kernel headers if you install the package "linux-headers-$(uname -r)" should be /usr/src/<some path that isn't just "linux">

---

### Post by Th3Professor on 2008-07-21
reboot... fixed. :D

---

### Post by Distortedgamer on 2008-08-06
I am getting an error.

I created a 16 gb folder for the virtual machine. It tried to default its position to var/lib/vmware-server/Virtual Machines/ although I changed that to /media/Storage/WindowsFiles/VirtualMachine/

It created the space correctly but when I go to 'Power On' the machine I get:

"Unable to change virtual machine power state: The process exited with an error:
End of error message."

Anyh ideas?

Oh, I even went and made a new machine in the default position and it did the same thing.

---

### Post by gmcauley on 2008-08-06
> **Distortedgamer said:**
> I am getting an error.

"Unable to change virtual machine power state: The process exited with an error:
End of error message."

Anyh ideas?



I think your next step is to get more info about the actual error.  Follow these steps:

   1. select 'VM -> Settings'
   2. select the 'Options' tab
   3. select 'Advanced'
   4. check 'Run with debugging information'

Then you should know more about why it is complaining.

---

### Post by kwein1 on 2008-08-12
> **bodhi.zazen said:**
> It is experimental, but it may be possible.
Yes, I used VMware converter on my live XP install to create a new VM.
I also used ghost 12 to create an image from an XP hard drive that wouldn't boot (motherboard failure) - but the drive was fine.  Then used the converter on that ghost image/backup to create another VM. I use that VM all the time. Windows will want to re-authenticate, since it "sees" that it's running on different HW.

---

### Post by kwein1 on 2008-08-12
Anybody know how to make VMware server do "fullscreen" on just one monitor in a dual-monitor setup?  Right now it splits the 2 screens, and blanks out the rest.

NVidia card, using TwinView. I can get firefox to maximize to just one screen.

---

### Post by biohazardouz on 2008-08-17
i installed vmware following the procedures mentioned. it is already on the "application/system tools", but it won't start. i typed vmware on terminal and these are the errors:
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

please, if you could, mail me at [email]biohazard_ten21@yahoo.com[/email]

---

### Post by bodhi.zazen on 2008-08-19
> **biohazardouz said:**
> i installed vmware following the procedures mentioned. it is already on the "application/system tools", but it won't start. i typed vmware on terminal and these are the errors:
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

please, if you could, mail me at [EMAIL="biohazard_ten21@yahoo.com"]biohazard_ten21@yahoo.com[/EMAIL]

See the sticky at the top of these forums :

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934") 

Step 5

---

### Post by Distortedgamer on 2008-08-21
Unable to change virtual machine power state: The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

POST(no connection): Failed to initialize monitor device.

Failed to initialize VM.
End of error message.
----------------------------

Sorry about the delay there.

Thats what I get whenever I try to turn the XP server on.

---

### Post by Mati_Jero on 2008-08-28
Great!!!

well but I have a question about it. how can i get access to internet for my virtual machine using a machine with a wireless card???

---

### Post by RetiredInMaine on 2008-08-30
Thank you for this thread and for all of the comments. I have been thinking about using VM to run xp and found this info very informative.

---

### Post by sunseeker888 on 2008-08-30
HI Guys

I am back to Ubuntu. I am had to go back to Vista :(, as my Ati card was not working properly and Ubuntu kept freezing and firefox would fail to work, so had no choice to move back. Now, I got a new XPS desktop, and got Nvidia card, so no more problem. 

I was wondering if my scanner will work with Vmare? I have canon slim line scanner, but have only the Vista driver. I really need a scanner.


Do I need Vmare fusion? I do not want dual boot anymore.

Any advice will be much appreciated.


S888:)

---

### Post by Jole on 2008-09-05
Hey to you all. I got Ubuntu 8.04 and I installed VMWare server 1.0.6 on it. Installation went fine, no problems or missing dependencies, but...I created a VM and I wanted to install WinXP on it. When I turn it on I get a black console screen and then nothing..the VM shuts down itself. I got an error after that that says...see screenshot.

Can someone help me with this please?

If it helps i got Ubuntu 8.04 running with nVidia cards along with Compiz. I tried to start the VM from a physical install CD and from a ISO image. No result.
[B][B][COLOR="DarkOrange"]
Update:[/COLOR][/B][/B] The problem was that I had my VM on a NTFS partiton. I made a new one on a ext3 partiton and everything went flawless. Installed winXP in 20 min, networking was up on startup. Performance inside the VM - very, very fast...:-)

aperently there is a fix for VMware if you want to have your Vm on a ntfs drive. Here's the [post]("http://sudan.ubuntuforums.com/showthread.php?t=684615").

---

### Post by Distortedgamer on 2008-09-15
So I changed to win XP Black and installed VMware and trying to get Ubuntu to run it. (If this is the wrong thread, sorry) I was able to install 8.04 and I finally had to enter static IPs to get out on the network. I can ping by IP but not by host. I changed the /etc/resolv.conf and added my name servers but it still didn't work. 

Does anyone have any other ideas on not being able to ping by hostname?

My second problem is that I installed openssh-server and opened port 22 through my router to the IP of Ubuntu but when I try to connect to it from the outside I get a connection timeout. 

Any ideas would be greatly appreciated!!

---

### Post by veloce on 2008-09-15
Are you using NAT or bridged networking?

Key question is where your ips are supposed to be coming from. If you are using bridging then you will be using the same dhcp server as your host.

If you are using NAT then vmware will be doing the dhcp serving.

I don't think vmware's dhcp server does dynamic host name resolution - which is why you can't refer to machine by name.  What is acting as dhcp server for the rest of your network (including host)?

---

### Post by bodhi.zazen on 2008-09-15
> **Distortedgamer said:**
> So I changed to win XP Black and installed VMware and trying to get Ubuntu to run it. (If this is the wrong thread, sorry) I was able to install 8.04 and I finally had to enter static IPs to get out on the network. I can ping by IP but not by host. I changed the /etc/resolv.conf and added my name servers but it still didn't work. 

Does anyone have any other ideas on not being able to ping by hostname?

My second problem is that I installed openssh-server and opened port 22 through my router to the IP of Ubuntu but when I try to connect to it from the outside I get a connection timeout. 

Any ideas would be greatly appreciated!!

to ping by host you either need to add them to the ect/hosts or register the host with DNS.

format of /etc/hosts is 

ip_address  hostname

---

### Post by fkerm on 2008-09-16
Successfully used this sticky, step by step, to install Windows XP Pro 64 bit edition on:


AMD Athlon 64 X2 Dual Core 6000
PNY Video Card G96512GXEB 9600GT RT
4GB RAM
Motherboard: GA-M57SLI-DS4

Ubuntu Release 8.04
Kernel: 2.6.24-19-generic
Gnome 2.22.3

THANKS!!!

---

### Post by Distortedgamer on 2008-09-17
Thank you for the responses.

I am not able to ping anything outside of my network by name. Like Google for instance. I can ping it by IP but not by name. 

Any ideas on the SSH issue? Is it possibly the HOST os that is blocking it? I am using a bridged connection and have Ubuntu with a static IP and the ports in my router are forwarded to that IP. Could my firewall in Windows be blocking it?

---

### Post by veloce on 2008-09-18
> **Distortedgamer said:**
>  Could my firewall in Windows be blocking it?

YES!

Turn it off and test again.  I don't use windows firewall at all, I make sure what I'm using is behind a real firewall and turn the dratted thing off.  

Given that you have a real firewall doing your port forwarding, you should be okay.

---

### Post by veloce on 2008-09-18
> **Distortedgamer said:**
> 
I am not able to ping anything outside of my network by name. Like Google for instance. I can ping it by IP but not by name. 

When you set up the fixed IP, did you not also tell what dns to use?  Sounds like you are not getting through to it - mistyped?  If you use dhcp it handles all that for you, can you set your dhcp to give you a fixed lease?  Then you'd have the static ip address for port forwarding.

---

### Post by RetiredInMaine on 2008-09-18
I need help installing vmware on ubuntu 8.04. I have a newly purchased oem copy of xp that I want to install and run under vm rather than dual boot. Dual boot would be my fall back but I think that means a total reinstall of ubuntu as well since windows wants to be first.

I tried following the sticky at the beginning of this thred but received a message indicating that it is not in the 8.04 repository. I then went to the vmware website and downloaded the VMware-server-1.0.7-108231.tar.gz file. I unarchived it into a new directory and tried to execute the installer file services.sh but received the following message: 

./services.sh: 176: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

I have looked for documentation for installing vmware but was not able to find any. I did register the product and received a serial number but have no idea what to do with that information.

Any help will be greatly appreciated.

---

### Post by Distortedgamer on 2008-09-19
Alright, so I had a trial version of Fortknox 2008 and I turned it off. I then ran putty from the host os (XP) and I was still getting network timeouts.

DNS issues - Here is what I have in my /etc/resolv.conf:
```

search localdomain
nameserver 76.85.229.110
nameserver 76.85.229.111

```

Those are just Road Runner's servers

**EDIT**
So I did some more tests and I am able to ping Google by IP from the CLI in Ubuntu but not by name. I opened Firefox and tried to browse to Google... address not found. I then tried to browse to Google by IP and it got the same error. I am also able to ping my router, but I couldn't browse to it through Firefox. Windows has no problems doing anything right now (surprisingly)

---

### Post by veloce on 2008-09-21
> **Distortedgamer said:**
> Alright, so I had a trial version of Fortknox 2008 and I turned it off. I then ran putty from the host os (XP) and I was still getting network timeouts.



There is an issue with communication between the vm and the host via bridged networking.  It is so slow as to be unusable so could be causing timeouts.  

> **Distortedgamer said:**
> 

DNS issues - Here is what I have in my /etc/resolv.conf:
```

search localdomain
nameserver 76.85.229.110
nameserver 76.85.229.111

```

Those are just Road Runner's servers



Can you ping these nameservers? 

> **Distortedgamer said:**
> 

**EDIT**
So I did some more tests and I am able to ping Google by IP from the CLI in Ubuntu but not by name. I opened Firefox and tried to browse to Google... address not found. I then tried to browse to Google by IP and it got the same error. I am also able to ping my router, but I couldn't browse to it through Firefox. Windows has no problems doing anything right now (surprisingly)

Firefox has it's own set of network setup settings - you may get completely different results from within firefox.

---

### Post by mohammad-mahmood on 2008-10-29
i am trying to install vmware on my ubuntu 8.04 and i download it but when i try to install it this problem appear

"
Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] 

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
"
i want to know what can i do
thanks

---

### Post by 080818jk on 2008-10-30
&#65292;[**&#32593;&#31449;&#24314;&#35774;**](http://www.71668.net/wangzhanjianshe.htm)&#24120;&#29992;&#30340;&#26041;&#27861;&#21253;&#25324;&#30005;&#23376;&#21002;&#29289;&#12289;&#20250;&#21592;&#36890;&#35759;&#12289;&#19987;&#19994;&#26381;&#21153;&#21830;&#30340;&#30005;&#23376;&#37038;&#20214;&#24191;&#21578;&#31561;&#12290; &#22522;&#20110;&#29992;&#25143;&#35768;&#21487;&#30340;Email&#33829;&#38144;&#19982;&#28389;&#21457;&#37038;&#20214;&#65288;Spam&#65289;&#19981;&#21516;&#65292;&#35768;&#21487;&#33829;&#38144;&#27604;&#20256;&#32479;&#30340;&#25512;&#24191;&#26041;&#24335;&#25110;&#26410;&#32463;&#35768;&#21487;&#30340;Email&#33829;&#38144;&#20855;&#26377;&#26126;&#26174;&#30340;&#20248;&#21183;&#65292;&#27604;&#22914;&#21487;&#20197;&#20943;&#23569;&#24191;&#21578;&#23545;&#29992;&#25143;&#30340;&#28363;&#25200;&#12289;&#22686;&#21152;&#28508;&#22312;&#23458;&#25143;&#23450;&#20301;&#30340;&#20934;&#30830;&#24230;&#12289;&#22686;&#24378;&#19982;&#23458;&#25143;&#30340;&#20851;&#31995;&#12289;&#25552;&#39640;&#21697;&#29260;&#24544;&#35802;&#24230;&#31561;&#12290; &#58865;&#58865; 3. &#36164;&#28304;&#21512;&#20316;&#32593;&#31449;&#25512;&#24191;&#20844;&#21496;&#26041;&#27861; &#58865;&#58865;[**&#32593;&#31449;&#20248;&#21270;**](http://www.71668.net/wangzhanyouhua.htm)&#36890;&#36807;&#32593;&#31449;&#20132;&#25442;&#38142;&#25509;&#12289;&#20132;&#25442;&#24191;&#21578;&#12289;&#20869;&#23481;&#21512;&#20316;&#12289;&#29992;&#25143;&#36164;&#28304;&#21512;&#20316;&#31561;&#26041;&#24335;&#65292;&#22312;&#20855;&#26377;&#31867;&#20284;&#30446;&#26631;&#32593;&#31449;&#20043;&#38388;&#23454;&#29616;&#20114;&#30456;&#32593;&#31449;&#25512;&#24191;&#30340;&#30446;&#30340;&#65292;&#20854;&#20013;&#26368;&#24120;&#29992;&#30340;&#36164;&#28304;&#21512;&#20316;&#26041;&#24335;&#20026;&#32593;&#31449;&#38142;&#25509;&#31574;&#30053;&#65292;&#21033;&#29992;&#21512;&#20316;&#20249;&#20276;&#20043;&#38388;&#32593;&#31449;&#35775;&#38382;&#37327;&#36164;&#28304;&#21512;&#20316;&#20114;&#20026;&#32593;&#31449;&#25512;&#24191;&#12290;     &#27599;&#20010;&#20225;&#19994;&#32593;&#31449;&#22343;&#21487;&#20197;&#25317;&#26377;&#33258;&#24049;&#30340;&#36164;&#28304;&#65292;&#36825;&#31181;&#36164;&#28304;&#21487;&#20197;&#34920;&#29616;&#20026;&#19968;&#23450;&#30340;&#35775;&#38382;&#37327;&#12289;&#27880;&#20876;&#29992;&#25143;&#20449;&#24687;&#12289;&#26377;&#20215;&#20540;&#30340;&#20869;&#23481;&#21644;&#21151;&#33021;&#12289;&#32593;&#32476;&#24191;&#21578;&#31354;&#38388;&#31561;&#65292;&#21033;&#29992;&#32593;&#31449;&#30340;&#36164;&#28304;&#19982;&#21512;&#20316;&#20249;&#20276;&#24320;&#23637;&#21512;&#20316;&#65292;&#23454;&#29616;&#36164;&#28304;&#20849;&#20139;&#65292;&#20849;&#21516;&#25193;&#22823;&#25910;&#30410;&#30340;&#30446;&#30340;&#12290;&#22312;&#36825;&#20123;&#36164;&#28304;&#21512;&#20316;&#24418;&#24335;&#20013;&#65292;&#20132;&#25442;&#38142;&#25509;&#26159;&#26368;&#31616;&#21333;&#30340;&#19968;&#31181;&#21512;&#20316;&#26041;&#24335;&#65292;&#35843;&#26597;&#34920;&#26126;&#20063;&#26159;&#26032;&#32593;&#31449;&#25512;&#24191;&#30340;&#26377;&#25928;&#26041;&#24335;&#20043;&#19968;&#12290;&#20132;&#25442;&#38142;&#25509;&#25110;&#31216;&#20114;&#24800;&#38142;&#25509;&#65292;&#26159;&#20855;&#26377;&#19968;&#23450;&#20114;&#34917;&#20248;&#21183;&#30340;&#32593;&#31449;&#20043;&#38388;&#30340;&#31616;&#21333;&#21512;&#20316;&#24418;&#24335;&#65292;&#21363;&#20998;&#21035;&#22312;&#33258;&#24049;&#30340;&#32593;&#31449;&#19978;&#25918;&#32622;&#23545;&#26041;&#32593;&#31449;&#30340;LOGO&#25110;&#32593;&#31449;&#21517;&#31216;&#24182;&#35774;&#32622;&#23545;&#26041;&#32593;&#31449;&#30340;&#36229;&#32423;&#38142;&#25509;&#65292;&#20351;&#24471;&#29992;&#25143;&#21487;&#20197;&#20174;&#21512;&#20316;&#32593;&#31449;&#20013;&#21457;&#29616;&#33258;&#24049;&#30340;&#32593;&#31449;&#65292;&#36798;&#21040;&#20114;&#30456;&#25512;&#24191;&#30340;&#30446;&#12290;&#20132;&#25442;&#38142;&#25509;&#30340;&#20316;&#29992;&#20027;&#35201;&#34920;&#29616;&#22312;&#20960;&#20010;&#26041;&#38754;&#65306;&#33719;&#24471;&#35775;&#38382;&#37327;&#12289;&#22686;&#21152;&#29992;&#25143;&#27983;&#35272;&#26102;&#30340;&#21360;&#35937;&#12289;&#22312;&#25628;&#32034;&#24341;&#25806;&#32593;&#31449;&#25512;&#24191;&#20013;&#22686;&#21152;&#20248;&#21183;&#12289;&#36890;&#36807;&#21512;&#20316;&#32593;&#31449;&#30340;&#25512;&#33616;&#22686;&#21152;&#35775;&#38382;&#32773;&#30340;&#21487;&#20449;&#24230;&#31561;&#12290;&#20132;&#25442;&#38142;&#25509;&#36824;&#26377;&#27604;&#26159;&#21542;&#21487;&#20197;&#21462;&#24471;&#30452;&#25509;&#25928;&#26524;&#26356;&#28145;&#19968;&#23618;&#30340;&#24847;&#20041;&#65292;&#19968;&#33324;&#26469;&#35828;&#65292;&#27599;&#20010;&#32593;&#31449;&#37117;&#20542;&#21521;&#20110;&#38142;&#25509;&#20215;&#20540;&#39640;&#30340;&#20854;&#20182;&#32593;&#31449;&#65292;&#22240;&#27492;&#33719;&#24471;&#20854;&#20182;&#32593;&#31449;&#30340;&#38142;&#25509;&#20063;&#23601;&#24847;&#21619;&#30528;&#33719;&#24471;&#20102;&#20110;&#21512;&#20316;&#20249;&#20276;&#21644;&#19968;&#20010;&#39046;&#22495;&#20869;&#21516;&#31867;&#32593;&#31449;&#30340;&#35748;&#21487;&#12290; &#58865;&#58865;4. &#20449;&#24687;&#21457;&#24067;&#32593;&#31449;&#25512;&#24191;&#26041;&#27861; &#58865;&#58865;[**&#21271;&#20140;google&#25490;&#21517;**](http://www.71668.net/bjgooglepaiming.htm)&#23558;&#26377;&#20851;&#30340;&#32593;&#31449;&#25512;&#24191;&#20449;&#24687;&#21457;&#24067;&#22312;&#20854;&#20182;&#28508;&#22312;&#29992;&#25143;&#21487;&#33021;&#35775;&#38382;&#30340;&#32593;&#31449;&#19978;&#65292;&#21033;&#29992;&#29992;&#25143;&#22312;&#36825;&#20123;&#32593;&#31449;&#33719;&#21462;&#20449;&#24687;&#30340;&#26426;&#20250;&#23454;&#29616;&#32593;&#31449;&#25512;&#24191;&#30340;&#30446;&#30340;&#65292;&#36866;&#29992;&#20110;&#36825;&#20123;&#20449;&#24687;&#21457;&#24067;&#30340;&#32593;&#31449;&#21253;&#25324;&#22312;&#32447;&#40644;&#39029;&#12289;&#20998;&#31867;&#24191;&#21578;&#12289;&#35770;&#22363;&#12289;&#21338;&#23458;&#32593;&#31449;&#12289;&#20379;&#27714;&#20449;&#24687;&#24179;&#21488;&#12289;&#34892;&#19994;&#32593;&#31449;&#31561;&#12290;&#20449;&#24687;&#21457;&#24067;&#26159;&#20813;&#36153;&#32593;&#31449;&#25512;&#24191;&#30340;&#24120;&#29992;&#26041;&#27861;&#20043;&#19968;&#12290; &#58865;&#58865; 5. &#24555;&#25463;&#32593;&#22336;&#32593;&#31449;&#25512;&#24191;&#26041;&#27861; &#58865;&#58865;&#21363;&#21512;&#29702;&#21033;&#29992;&#32593;&#32476;&#23454;&#21517;&#12289;&#36890;&#29992;&#32593;&#22336;&#20197;&#21450;&#20854;&#20182;&#31867;&#20284;&#30340;&#20851;&#38190;&#35789;&#32593;&#31449;&#24555;&#25463;&#35775;&#38382;&#26041;&#24335;&#26469;&#23454;&#29616;&#32593;&#31449;&#25512;&#24191;&#30340;&#26041;&#27861;&#12290;&#24555;&#25463;&#32593;&#22336;&#20351;&#29992;&#33258;&#28982;&#35821;&#35328;&#21644;&#32593;&#31449;URL&#24314;&#31435;&#20854;&#23545;&#24212;&#20851;&#31995;&#65292;&#36825;&#23545;&#20110;&#20064;&#24815;&#20110;&#20351;&#29992;&#20013;&#25991;&#30340;&#29992;&#25143;&#26469;&#35828;&#65292;&#25552;&#20379;&#20102;&#26497;&#22823;&#30340;&#26041;&#20415;&#65292;&#29992;&#25143;&#21482;&#38656;&#36755;&#20837;&#27604;&#33521;&#25991;&#32593;&#22336;&#35201;&#26356;&#21152;&#23481;&#26131;&#35760;&#24518;&#30340;&#24555;&#25463;&#32593;&#22336;&#23601;&#21487;&#20197;&#35775;&#38382;&#32593;&#31449;&#65292;&#29992;&#33258;&#24049;&#30340;&#27597;&#35821;&#25110;&#32773;&#20854;&#20182;&#31616;&#21333;&#30340;&#35789;&#27719;&#20026;&#32593;&#31449;&#8220;&#26356;&#25442;&#8221;&#19968;&#20010;&#26356;&#22909;&#35760;&#24518;&#12289;&#26356;&#23481;&#26131;&#20307;&#29616;&#21697;&#29260;&#24418;&#35937;&#30340;&#32593;&#22336;&#65292;&#20363;&#22914;&#36873;&#25321;&#20225;&#19994;&#21517;&#31216;&#25110;&#32773;&#21830;&#26631;&#12289;&#20027;&#35201;&#20135;&#21697;&#21517;&#31216;&#31561;&#20316;&#20026;&#20013;&#25991;&#32593;&#22336;&#65292;&#36825;&#26679;&#21487;&#20197;&#22823;&#22823;&#24357;&#34917;&#33521;&#25991;&#32593;&#22336;&#19981;&#20415;&#20110;&#23459;&#20256;&#30340;&#32570;&#38519;&#65292;&#22240;&#20026;&#22312;&#32593;&#22336;&#25512;&#24191;&#26041;&#38754;&#26377;&#19968;&#23450;&#30340;&#20215;&#20540;&#12290;&#38543;&#30528;&#20225;&#19994;&#27880;&#20876;&#24555;&#25463;&#32593;&#22336;&#25968;&#37327;&#30340;&#22686;&#21152;&#65292;&#36825;&#20123;&#24555;&#25463;&#32593;&#22336;&#29992;&#25143;&#25968;&#25454;&#21487;&#20063;&#30456;&#24403;&#20110;&#19968;&#20010;&#25628;&#32034;&#24341;&#25806;&#65292;&#36825;&#26679;&#65292;&#24403;&#29992;&#25143;&#21033;&#29992;&#26576;&#20010;&#20851;&#38190;&#35789;&#26816;&#32034;&#26102;&#65292;&#21363;&#20351;&#19982;&#26576;&#32593;&#31449;&#27880;&#20876;&#30340;&#20013;&#25991;&#32593;&#22336;&#24182;&#19981;&#19968;&#33268;&#65292;&#21516;&#26679;&#23384;&#22312;&#34987;&#29992;&#25143;&#21457;&#29616;&#30340;&#26426;&#20250;&#12290; &#58865;&#58865;6. &#32593;&#32476;&#24191;&#21578;&#32593;&#31449;&#25512;&#24191;&#26041;&#27861; &#58865;&#58865;[**google&#20248;&#21270;**](http://www.71668.net/googleyouhua.htm)&#32593;&#32476;&#24191;&#21578;&#26159;&#24120;&#29992;&#30340;&#32593;&#32476;&#33829;&#38144;&#31574;&#30053;&#20043;&#19968;&#65292;[**google&#20248;&#21270;&#25216;&#26415;**](http://www.71668.net/googleyouhuajishu.htm)&#22312;&#32593;&#32476;&#21697;&#29260;&#12289;&#20135;&#21697;&#20419;&#38144;&#12289;&#32593;&#31449;&#25512;&#24191;&#31561;&#26041;&#38754;&#22343;&#26377;&#26126;&#26174;&#20316;&#29992;&#12290;&#32593;&#32476;&#24191;&#21578;&#30340;&#24120;&#35265;&#24418;&#24335;&#21253;&#25324;&#65306;BANNER&#24191;&#21578;&#12289;&#20851;&#38190;&#35789;&#24191;&#21578;&#12289;&#20998;&#31867;&#24191;&#21578;&#12289;&#36190;&#21161;&#24335;&#24191;&#21578;&#12289;Email&#24191;&#21578;&#31561;

---

### Post by krusher on 2008-11-03
```

gaurav@marmat:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
gaurav@marmat:~$ 

```

I have tried sudo vmware also but getting same prbs. Some help in getting this work would be really great.
Thanks.

---

### Post by bodhi.zazen on 2008-11-03
> **krusher said:**
> ```

gaurav@marmat:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
gaurav@marmat:~$ 

```

I have tried sudo vmware also but getting same prbs. Some help in getting this work would be really great.
Thanks.

Although this is a great "how-to" it is quite outdated.

Did you try the stickies at the top of this forum ?

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Step 5 I believe will fix this problem.

---

### Post by ChaoticXSinZ on 2008-11-11
~message removed~
~solved~

---

### Post by anthonyhill on 2008-11-12
summary: no access to wireless card from xp vmware guest.

I've been running an xp guest under vmware on ubuntu for a few years now. (currently VMware Server 1.0.6 running on hardy). Its always been pretty good to me - BUT I have never got the networking working with my wireless card.

If I want to access the network from the windows guest - I have to plug an ethernet cable in.

The wireless card I am using is a Intel PRO/Wireless 3945ABG (the PC is a dell inspiron 1420) - the driver I am currently using is the iwl3945, which in many ways is an improvement on the ipw3945, but doesnt seem to affect my vmware problems.

vmware-config.pl will see and configure the device, and windows can use the device - I just dont ever see any real traffic. I have never been able to aquire an addess via DHCP, or receive any IP traffic.

Is this a known issue ? Does anyone know of a workaround ? The only times I ever use a wired connection these days (at work or home) is to access the net from the windows guest.

---

### Post by bodhi.zazen on 2008-11-13
> **anthonyhill said:**
> summary: no access to wireless card from xp vmware guest.

I've been running an xp guest under vmware on ubuntu for a few years now. (currently VMware Server 1.0.6 running on hardy). Its always been pretty good to me - BUT I have never got the networking working with my wireless card.

If I want to access the network from the windows guest - I have to plug an ethernet cable in.

The wireless card I am using is a Intel PRO/Wireless 3945ABG (the PC is a dell inspiron 1420) - the driver I am currently using is the iwl3945, which in many ways is an improvement on the ipw3945, but doesnt seem to affect my vmware problems.

vmware-config.pl will see and configure the device, and windows can use the device - I just dont ever see any real traffic. I have never been able to aquire an addess via DHCP, or receive any IP traffic.

Is this a known issue ? Does anyone know of a workaround ? The only times I ever use a wired connection these days (at work or home) is to access the net from the windows guest.

How are you installing vmware ?

I do not know if you are using it or not, but the any-any update will disable this option.

---

### Post by 081104jk on 2008-11-13
&#25918;&#38899;&#29305;&#24615;&#37319;&#29992;&#39640;&#20445;&#30495;&#25216;&#26415;&#65292;[**&#24405;&#38899;&#30005;&#35805;&#26426;**](http://www.googlejk.cn/lydhj.htm)&#39640;&#21697;&#36136;&#35821;&#38899;&#25773;&#25918;&#65292;&#38899;&#36136;&#28165;&#26224;&#12289;&#26580;&#21644;&#12290;&#22312;&#25773;&#25918;&#24405;&#38899;&#30340;&#36807;&#31243;&#20013;&#65292;[**&#30005;&#35805;&#24405;&#38899;&#31995;&#32479;**](http://www.googlejk.cn/xitongbaojia.htm)&#29992;&#25143;&#21487;&#20197;&#38543;&#26102;&#25353;&#38190;&#26469;&#35843;&#25972;&#38899;&#37327;&#22823;&#23567;&#12290;&#38500;&#20102;&#21487;&#20197;&#36880;&#26465;&#33258;&#21160;&#25773;&#25918;&#22806;&#65292;[**&#24405;&#38899;&#30005;&#35805;&#26426;**](http://www.googlejk.cn/lydhj.htm)&#29992;&#25143;&#21487;&#20197;&#25353;&#38190;&#24555;&#36895;&#36339;&#36807;&#26412;&#26465;&#24405;&#38899;&#32780;&#25773;&#25918;&#19979;&#19968;&#26465;&#25110;&#32773;&#19978;&#19968;&#26465;&#24405;&#38899;&#12290;&#29992;&#25143;&#23494;&#30721;&#25511;&#21046;&#25918;&#38899;&#21151;&#33021;&#65292;[**&#30005;&#35805;&#24405;&#38899;&#35774;&#22791;**](http://www.googlejk.cn/dhlysb.htm)&#24403;&#23494;&#30721;&#20026;&#31354;&#25110;&#32773;0000&#30340;&#26102;&#20505;&#65292;&#20219;&#20309;&#29992;&#25143;&#37117;&#21487;&#20197;&#25773;&#25918;&#26412;&#26426;&#24405;&#38899;&#65307;&#32780;&#24403;&#29992;&#25143;&#35774;&#23450;&#20102;&#33258;&#24049;&#30340;&#29992;&#25143;&#23494;&#30721;&#26102;&#65292;&#21482;&#26377;&#36755;&#20837;&#12288;&#12288;&#20102;&#27491;&#30830;&#30340;&#23494;&#30721;&#25165;&#21487;&#20197;&#25910;&#21548;&#26412;&#26426;&#24405;&#38899;&#65292;[**&#24405;&#38899;&#34920;**](http://www.googlejk.cn/lyb.htm)&#38450;&#27490;&#38750;&#27861;&#29992;&#25143;&#20351;&#29992;&#12290;

---

### Post by anthonyhill on 2008-11-23
Hey bodhi.zazen,

I have installed vmware (server) using a variety of methods over the years. (how come its not in the repositories anymore ?) Lately, I download the latest tar file from the vmware website, untar it, and run the install script.

I usually run into the odd error, the last install worked, but the executables would not run until I linked a few libraries into the vmware install tree :-

ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

..I dont apply the any-any patch - it doesnt seem to fix anything for me, and if I do I get this in the syslog :-

bridge-wlan0: is a Wireless Adapter
vmnet: You are trying to use wireless bridged networking together with
vmnet: vmware-any-any-update.  This is not supported configuration, and
vmnet: your wireless bridge will probably not work.

..if I dont apply the patch, I dont get the warnings - just messages like :-

device wlan0 entered promiscuous mode
audit(1227415009.517:3): dev=wlan0 prom=256 old_prom=0 auid=4294967295
bridge-wlan0: enabled promiscuous mode
device eth0 entered promiscuous mode
audit(1227415009.517:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
bridge-eth0: enabled promiscuous mode
/dev/vmmon[9054]: /dev/rtc open failed: -16
device wlan0 left promiscuous mode
audit(1227415030.956:5): dev=wlan0 prom=0 old_prom=256 auid=4294967295
bridge-wlan0: disabled promiscuous mode
device wlan0 entered promiscuous mode
audit(1227415030.956:6): dev=wlan0 prom=256 old_prom=0 auid=4294967295
bridge-wlan0: enabled promiscuous mode

Sometimes I suspect my problem has something to do with the iwl3945 wireless ethernet driver not properly supporting promiscuous mode - but if that were the case, I'd expect more people to be having this issue. (and ideally solving it)

Cheers.

---

### Post by 1oki on 2008-11-25
^^ thats the exact problem I have had! It's frustrating... 


also, why isn't it in the repo any more? 
/me scratches his head... 

that's annoying...

---

### Post by theDaveTheRave on 2008-11-26
Dear All, I have asked this elsewhere, but this may be the better thread for it...

I have a virtualisation question, that I've not yet found a definitive answer too... so if anyone out there can help I would be forever gratefull (as would my boss no doubt!);


My situation.

Currently I run a dualboot XP and Ubuntu system.

My personal preference is too work on the Ubuntu system all the time (I've used linux for years now and found working in windows extremely painfull at times!)

What I want to do is run the XP partition inside of a VM (or similar) on my ubuntu system.

However, we don't have any XP system disks, and all my "programs" that I really need are sitting on my XP partition (although I do have the install disks for the stuff I use!).

From what I have read I would need to create the virtual system as if I was creating a "new instal of XP", however as I have XP working fine on the extra partition on my computer this would seem a bit daft, can I not simply use the install that I allready have and boot straight into it??

From what I have read I have a few option:

Create an image of my XP, then create a "bootable" system disk from my instalation. Open a Virtualisation tool and set it up to hold XP...

Again to me this seems uneccesary due to having a fully functional XP system on my computer... also it is going to take a while to get set up!

but then I guess that is the case for anything!

thanks for the help in advance.

Dave

---

### Post by Jole on 2008-11-26
> **theDaveTheRave said:**
> Dear All, I have asked this elsewhere, but this may be the better thread for it...

I have a virtualisation question, that I've not yet found a definitive answer too... so if anyone out there can help I would be forever gratefull (as would my boss no doubt!);


My situation.

Currently I run a dualboot XP and Ubuntu system.

My personal preference is too work on the Ubuntu system all the time (I've used linux for years now and found working in windows extremely painfull at times!)

What I want to do is run the XP partition inside of a VM (or similar) on my ubuntu system.

However, we don't have any XP system disks, and all my "programs" that I really need are sitting on my XP partition (although I do have the install disks for the stuff I use!).

From what I have read I would need to create the virtual system as if I was creating a "new instal of XP", however as I have XP working fine on the extra partition on my computer this would seem a bit daft, can I not simply use the install that I allready have and boot straight into it??

From what I have read I have a few option:

Create an image of my XP, then create a "bootable" system disk from my instalation. Open a Virtualisation tool and set it up to hold XP...

Again to me this seems uneccesary due to having a fully functional XP system on my computer... also it is going to take a while to get set up!

but then I guess that is the case for anything!

thanks for the help in advance.

Dave

I didn't quite understand what you want, but this might help you:

[http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

---

### Post by theDaveTheRave on 2008-11-26
Thanks


On a first look I do believe that was what I have spend the whole of the weekend looking for!

Now I just hope I can get it working before christmas!

thanks to all for a great howto, and a brill community.

In fact this is the best community I've come across in terms of Forum attendence, I've posted messages to others and they have stayed silent for ages.

thanks to all at Ubuntu.

Dave

---

### Post by obst on 2008-12-03
Cant move my pointer in the boot menu, what shall i do? Thats why i cant boot from my Windows CD in the vm.

---

### Post by Caser on 2008-12-10
> **ElemonGW said:**
> You shouldn't have closed the terminal. Now you must uninstall it. If the problem continues run
```
sudo rm -rf /etc/vmware
```
in terminal.

thanks ,
:p

---

### Post by Jemradary on 2008-12-19
When will this be updated for 8.10?

---

### Post by akelsall on 2008-12-28
Is vmware server available for Intrepid (8.10)? I used the procedure you outlined and it bommbed at the end ("Unable to build the vmmon module.")

Thanks,

Andy

---

### Post by heiNey on 2009-01-01
ive got a quick question, is it possible to access my ubuntu drives from the xp inside vmware?  in other words, after installing xp in vmware, can i access my /home and other folders, since they are ext3 from within windows?

---

### Post by user-max on 2009-02-07
> **akelsall said:**
> Is vmware server available for Intrepid (8.10)? I used the procedure you outlined and it bommbed at the end ("Unable to build the vmmon module.")

Thanks,

Andy

I am currently running Intrepid 8.10 on my laptop. for virtualization purposes I am using VMWare Server 2.0, available for free from their website. All you have to do is to fill out registration form and then download VMWare server 2.0. They will send you your serial number for installation purposes in your email, so make sure you are using a real email.

Mine installed with default installation options.

---

### Post by user-max on 2009-02-07
> **heiNey said:**
> ive got a quick question, is it possible to access my ubuntu drives from the xp inside vmware?  in other words, after installing xp in vmware, can i access my /home and other folders, since they are ext3 from within windows?

Not sure, but the way I had to set up is to share a common folder between the two systems.

---

### Post by veloce on 2009-02-08
> **user-max said:**
> Not sure, but the way I had to set up is to share a common folder between the two systems.

If you share the host folder via Samba you should be able to access it from your XP vm.

However, I have often found permissions to be problematic that way around.  For some reason, accessing the XP vm's shared directories from the ubuntu host has always worked easier for me.

---

### Post by Lachlanus on 2009-02-20
Hi, I'm new to linux so please bare with me.  In the instructions in post 1 it says "opent the VM Ware console."  Where is this?  I followed all the previous instructions, but no VMWare app has turned up in my menus.

---

### Post by user-max on 2009-02-21
> **Lachlanus said:**
> Hi, I'm new to linux so please bare with me.  In the instructions in post 1 it says "opent the VM Ware console."  Where is this?  I followed all the previous instructions, but no VMWare app has turned up in my menus.

open any terminal or console and type 

vmware

This will open up login screen for vmware in your browser. You will have to login as root I believe. From there you can create a virtual machine, and manage all your presets. And after you install the guest os, you will have a console tab where you will have links to install the remote console. Thats it.

---

### Post by AppleIsCool on 2009-03-01
I'm sorry for being troublesome, but i have totally no clue of what to do, i download VMware already but i skipped all the codes and consoles stuff and especially Procedure Gutsy & Feisty and Procedure Edgy and earlier versions (what's does that even mean?)

I'm very noobish at Ubuntu now, so please help me

Apples

---

### Post by bodhi.zazen on 2009-03-01
LMAO apples.

Try following the how to , as posted #1 on this thread. Yes it involves commands in a terminal, I do not know of any way to avoid that. I suppose you could do some steps in the gui if you wish.

Otherwise, to advise you , we need to know what you have done, where you got stuck, and what, if any, error messages did you get ?

---

### Post by Greatatuin on 2009-03-09
Worked Great, Xp is running in VMware. How do I get connected to the internet from my virtual machine? I have tried bridged, host only and NAT but no go.

Can anyone help?

---

### Post by veloce on 2009-03-09
> **Greatatuin said:**
> Worked Great, Xp is running in VMware. How do I get connected to the internet from my virtual machine? I have tried bridged, host only and NAT but no go.

Can anyone help?

It depends how your host is connected to the internet.  

If your host is connected to a network with a dhcp server then use bridged networking.  The vm should receive an ip address from the dhcp server and a default gateway that will provide access to the internet.  You would test this in the same way as you would a new machine connected to the network (i.e. start with ipconfig /all to see what settings are provided by the dhcp server ...)

---

### Post by JerryI on 2009-03-14
I installed VMWare Server on Intrepid last night.  I received the successful installation messages, so I think everything should have gone ok.  However, when I type vmware into my terminal, my browser opens to [https://127.0.0.1.8333/ui/](https://127.0.0.1.8333/ui/) and indicates that the url is loading (apparently forever).

I read somewhere in my frantic, scattered forum research over the past several hours that VMWare Server works only in an intel environment or only on an intel machine or something to that effect, but I didn't see that on the VMWare website.  My HP s3100n desktop pc has an AMD64 dual-core processor.  I installed the 64-bit version of VMWare because the install program barfed when I tried to install the 32-bit version in my 32-bit Intrepid.  Based on this info, can you guess the source of my problem?  Do you have any further suggestions?

---

### Post by bodhi.zazen on 2009-03-15
your ip address is off.

localhost:8333

or 

127.0.0.1:8333

You need a : and not a . :twisted:

---

### Post by JerryI on 2009-03-15
re: the suggestion

your ip address is off.

localhost:8333

or

127.0.0.1:8333

You need a : and not a .

What can I do to 'fix' the problem now that we've identified it, and how did the problem come about in the first place.

---

### Post by JerryI on 2009-03-15
my mistake - the hanging url is [https://127.0.0.1:8333/](https://127.0.0.1:8333/)  

so should I just uninstall the whole app, or is there some way to get the installation to run?

---

### Post by bodhi.zazen on 2009-03-15
:lolflag:

Open your browser (firefox ?)

In the address bar, at the top, you manually type :

> localhost:8333

---

### Post by JerryI on 2009-03-15
When I type localhost:8333 into the url box, it still hangs and says connecting to [www.localhost.com](www.localhost.com) forever.  Should I uninstall the whole app, or do you think there is some way to fix what I have?

---

### Post by bodhi.zazen on 2009-03-15
You need to get rid of the "www" and ".com"

just 

[https://localhost:8333/ui](https://localhost:8333/ui)

---

### Post by JerryI on 2009-03-15
Then I got message:

Secure Connection Failed

localhost:8333 uses an invalid security certificate.

The certificate is not trusted because it is self signed.
The certificate is only valid for ubuntu

(Error code: sec_error_untrusted_issuer)
 
    * This could be a problem with the server's configuration, or it could be someone trying to impersonate the server.

    * If you have connected to this server successfully in the past, the error may be temporary, and you can try again later.

          Or you can add an exception…

So I added the exception and now I have a blank firefox page that says [https://localhost:8333/ui](https://localhost:8333/ui) in the url box and Done at the bottom.  I still seem to lack any functionality.

---

### Post by bodhi.zazen on 2009-03-15
sounds like Server 2.0

I found server 2.0 to be way too buggy.

You need to allow Java ?

---

### Post by JerryI on 2009-03-15
You are right.  I am going to 'downgrade' the more stable version 1.x.  Can you give me some guidelines in uninstalling 2.0?  Also, should I 'downgrade' to Hardy from Intrepid?  I'm not looking for bleeding edge, just stable functionality.  If you would tell me how to 'allow java' I would appreciate the help.

---

### Post by bodhi.zazen on 2009-03-15
As far as allowing java(script), it should run automatically unless you are running NoScript, in which case you need to allow localhost, :lolflag:

Removing is easy, just run the uninstall script.

If you wish "Stable" I suggest your run Ubuntu 8.04 , LTS.

---

### Post by user-max on 2009-03-15
I too have AMD dual core laptop, I run vmware 2.0 in 8.10 and it works fine. But I installed 32 bit package, because my ubuntu install is 32 bit optimized.

---

### Post by jsmac8218 on 2009-04-14
Hi, I installed using your script and I think it worked. I am installing on intrepid 8.10 and it did not create a menu link so I terminaled "vmware" and it opened a login page in firefox. it is asking for my login name and password; I've no idea what login name it wants, I never created one when compiling vmware. Any ideas?

---

### Post by user-max on 2009-04-14
> **jsmac8218 said:**
> Hi, I installed using your script and I think it worked. I am installing on intrepid 8.10 and it did not create a menu link so I terminaled "vmware" and it opened a login page in firefox. it is asking for my login name and password; I've no idea what login name it wants, I never created one when compiling vmware. Any ideas?

Login: root
Password: your root password (the one you use for sudo)

---

### Post by jsmac8218 on 2009-04-14
HI, tried root and my sudo password and it didn't work. I also tried root and no password (I don't have a login password when I start Ubuntu but that didn't work either. I am sure I typed it in correctly. I use the same sudo password as my keyring password and that is OK so it hasn't changed. I also just tried a sudo gedit command and the same password worked fine.

Now what?

---

### Post by jsmac8218 on 2009-04-14
My VMware install went fine on Intrepid 8.10 and I can run the firefox sign-in screen (dealing with login issues seperately) by typing vmware into a terminal, but why didn't I get a menu start item for VMware? and how do I create one? what is the command ?

---

### Post by veloce on 2009-04-14
> **jsmac8218 said:**
> HI, tried root and my sudo password and it didn't work. I also tried root and no password (I don't have a login password when I start Ubuntu but that didn't work either. I am sure I typed it in correctly. I use the same sudo password as my keyring password and that is OK so it hasn't changed. I also just tried a sudo gedit command and the same password worked fine.

Now what?

rerun vmware-config.pl and set the administrative user to be your normal login.

(The only other alternative is to set a root password so that you can log in as root.  Ubuntu doctrine considers this to be Bad (tm) so you won't find any instructions for doing so on this site.)

---

### Post by veloce on 2009-04-14
> **jsmac8218 said:**
> My VMware install went fine on Intrepid 8.10 and I can run the firefox sign-in screen (dealing with login issues seperately) by typing vmware into a terminal, but why didn't I get a menu start item for VMware? and how do I create one? what is the command ?

It's because vmware server console isn't a program anymore.  

However, if you add a menu item that uses the command "vmware" it will create a link (like a shortcut in windows) that will load your browser pointing to the right web address.

---

### Post by jsmac8218 on 2009-04-15
Got it, thanks. Ran Windows setup but then messages came up saying not enough resources. It's a pretty old PC so I'll have to try it on a newer one. I was using it as a test case before I mucked up my production PC.

Thanks for this help folks.

---

### Post by vdfritz on 2009-04-26
i can't get this to work :/

it installed successfully, but can't run vmware-config.pl

it says: unable to build the vmmon module.

i've installed and reinstalled linux-headers-generic (uname -r show's me generic at the end)

thanks o/

edit

i've tried just now installing the linux-headers-386 and server, but didn't work either

---

### Post by veloce on 2009-04-26
> **vdfritz said:**
> i can't get this to work :/

it installed successfully, but can't run vmware-config.pl

it says: unable to build the vmmon module.

i've installed and reinstalled linux-headers-generic (uname -r show's me generic at the end)

thanks o/

edit

i've tried just now installing the linux-headers-386 and server, but didn't work either

You need the version numbers from uname -r in the command as well, e.g.

sudo apt-get install linux-headers-2.6.28-11-generic

That's why the howto uses the command that substitutes the results of uname -r in it.

---

### Post by vdfritz on 2009-04-28
> **veloce said:**
> You need the version numbers from uname -r in the command as well, e.g.

sudo apt-get install linux-headers-2.6.28-11-generic

That's why the howto uses the command that substitutes the results of uname -r in it.

i tried that and got "the newest version of linux headers is already installed" (something like that heh)

then i used --reinstall, it reinstalled, and when running vmware-config.pl i get:

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)?

i type yes, and the following message appears:

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-11-generic/build/include]

i press enter, it tries to do something, and at the end:

Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by yoos on 2009-04-28
I have the same problem as vdfritz with trying to run vmware in jaunty... Any input would be appreciated!!! I can't use VMWare right now :(

Here's what I tried with the results:


```
mike@mike-desktop:~$ **uname -r**
2.6.28-11-generic
mike@mike-desktop:~$ **sudo apt-get install linux-headers-2.6.28-11-generic**
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.28-11-generic is already the newest version.
linux-headers-2.6.28-11-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@mike-desktop:/home/mike# **sudo /usr/bin/vmware-config.pl**
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-11-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.28-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:20,
                 from /tmp/vmware-config1/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/fixmap_32.h:29,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/fixmap.h:5,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:30,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:763,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:71:
/tmp/vmware-config1/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config1/vmmon-only/linux/driver.c:146: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:150: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1670: error: too many arguments to function &#8216;smp_call_function&#8217;
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
**Unable to build the vmmon module.**

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

---

### Post by veloce on 2009-04-29
What version of vmware are you using?

It sounds like you need a patch for vmware-config.pl but I would start by making sure you're using the latest version (1.0X or 2.01).  If you aren't then uninstall the one you are using and install the latest.

If that's not the case then search the forum for the links to the latest patch.

---

### Post by yoos on 2009-04-29
I am using VMware server version 1.0.6-91891... At least that's what I installed on March 24 2009. I installed it in linux 8.04, then upgraded to 8.10, then 9.04.... I'm new to linux, sorry... What's the best way to uninstall since I installed it in 8.04 and am now on 9.04? thank you!!!

---

### Post by yoos on 2009-04-29
OK, I got vmware working using the instructions here!

[http://ubuntuforums.org/showthread.php?t=1130174](http://ubuntuforums.org/showthread.php?t=1130174) 

I just did the patch part... I didn't upgrade... It appears to work now except it gave some weird error that it couldn't connect my floppy... I still am wondering about my upgrade question though... thx!

---

### Post by veloce on 2009-04-29
> **yoos said:**
> OK, I got vmware working using the instructions here!

[http://ubuntuforums.org/showthread.php?t=1130174](http://ubuntuforums.org/showthread.php?t=1130174) 

I just did the patch part... I didn't upgrade... It appears to work now except it gave some weird error that it couldn't connect my floppy... I still am wondering about my upgrade question though... thx!

* I thought you said you had upgraded? Or are you talking about vmware upgrading rather than Ubuntu upgrading.

* To get rid of the floppy disk error, delete the floppy disk from the virtual hardware on your vm.

---

### Post by loo0olz on 2009-04-29
thanx pro for ur help

---

### Post by yoos on 2009-04-30
> **veloce said:**
> * I thought you said you had upgraded? Or are you talking about vmware upgrading rather than Ubuntu upgrading.

* To get rid of the floppy disk error, delete the floppy disk from the virtual hardware on your vm.

thx for the floppy info! Yea, I'm talking about upgrading vmware now... What is the correct or recommended way to do that? Uninstall then install updated version, or just install updated version straight away? I don't see the program listed in the add/remove menu, but I can search/google how to uninstall if that's the recommended approach. thx!

---

### Post by veloce on 2009-04-30
> **yoos said:**
> thx for the floppy info! Yea, I'm talking about upgrading vmware now... What is the correct or recommended way to do that? Uninstall then install updated version, or just install updated version straight away? I don't see the program listed in the add/remove menu, but I can search/google how to uninstall if that's the recommended approach. thx!

Theoretically you can just run the vmware installer and it will try and uninstall first but it's pretty flakey.  Better to uninstall first.

Uninstall is just:

/usr/bin/vmware-uninstall

You may or may not have to patch the new version's vmware-config.

---

### Post by yoos on 2009-05-01
thanks veloce!

---

### Post by vdfritz on 2009-05-01
how do i install that patch?

---

### Post by yoos on 2009-05-01
> **vdfritz said:**
> how do i install that patch?

I used this link: [http://geekzine.org/2008/11/20/install-vmware-server-on-ubuntu-intrepid-810/](http://geekzine.org/2008/11/20/install-vmware-server-on-ubuntu-intrepid-810/)


and just did the patch part.... 
```

    wget [http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz](http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz)

    tar -xvzf vmware-update-2.6.27-5.5.7-2.tar.gz

    cd vmware-update-2.6.27-5.5.7-2

    ./runme.pl
```

---

### Post by vdfritz on 2009-05-01
> **yoos said:**
> I used this link: [http://geekzine.org/2008/11/20/install-vmware-server-on-ubuntu-intrepid-810/](http://geekzine.org/2008/11/20/install-vmware-server-on-ubuntu-intrepid-810/)


and just did the patch part.... 
```

    wget [http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz](http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz)

    tar -xvzf vmware-update-2.6.27-5.5.7-2.tar.gz

    cd vmware-update-2.6.27-5.5.7-2

    ./runme.pl
```

it's working, thanks!!! =D

edit

no wait

i used the patch, then tried vmware-config.pl again, it was all perfect, it says that vmware was successfully

but when trying to run the program, a window appears and then closes
and with the terminal i get:

vdfritz@vdfritz-laptop:~$ vmware
kde4-config: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)                               
kde4-config: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
vdfritz@vdfritz-laptop:~$

---

### Post by veloce on 2009-05-03
> **vdfritz said:**
> it's working, thanks!!! =D

edit

no wait

i used the patch, then tried vmware-config.pl again, it was all perfect, it says that vmware was successfully

but when trying to run the program, a window appears and then closes
and with the terminal i get:

vdfritz@vdfritz-laptop:~$ vmware
kde4-config: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)                               
kde4-config: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
vdfritz@vdfritz-laptop:~$

Copied from [http://ubuntuforums.org/showthread.php?t=779934]("http://ubuntuforums.org/showthread.php?t=779934")

Post-install configuration. Last, before running vmware :
Code:

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0

---

### Post by mach7out on 2009-07-20
Ubuntu 9.04
                - the Jaunty Jackalope

fixed the sources as indicated but after the update and install command it ran for a bit then said e: couldnt find package vmware-server

:confused:

Get:1 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                      
Get:3 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty Release.gpg [189B]        
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                 
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/restricted Translation-en_US     
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:5 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                  
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty Release       
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates Release                    
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/main Packages                      
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/main Sources  
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/universe Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/universe Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) jaunty-updates/multiverse Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [57.9kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2092B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [17.5kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [611B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [23.1kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [5238B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [14B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [14B]
Fetched 157kB in 2s (68.2kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmware-server

---

### Post by lordlortnoc on 2009-07-31
I got through the installation process, but when I went to run 'vmware' these are the errors I got...


```

root@UNKNOWN:/home/heroin/Desktop/vmware-server-distrib# vmware
Launching VMware Web Access using /usr/bin/xdg-open
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Error showing url: Operation not supported

```


Any suggestions anyone?   :confused:

---

### Post by tommytomato on 2009-08-02
very nice thanks for that, but for the life of me, i cant get xp browser to surf the net

i've tried what i know and i still cant get it to connect to the net

any ideas please..

tt

---

### Post by eshant_engineer on 2009-10-14
After installing XP on server. If i want to use VMware player(which is faster) then would i will be able to have the same system with same setting that i made in server. More specifically, player allows to have only one shared folder while server allows unlimitedly(i suppose). So would i will be able to have same no of shared folder with player as much i am having in server?

---

### Post by forrest charnock on 2009-10-19
hI

  the big draw for me with linux was virus resistance, this is probably a silly question but can windows get a virus when running in a virtual machine mode on linux?

---

### Post by corsakh on 2009-10-20
Of course it can, but it wont spread into your linux system.

---

### Post by albtross on 2010-03-10
Hello, I'm an trying to unpack the Vmware Server on Ubuntu 64bit unsuccessfully.

Here is the command
tar -zxvf VMware-server-2.0.2-203138.x86_64.tar.gz

The output gives seems to get to over 90%, then it fails at the following.
.
.
.
.
vmware-server-distrib/installer/
vmware-server-distrib/installer/services.sh
vmware-server-distrib/vmware-install.pl
tar: vmware-server-distrib/vmware-install.pl: Cannot create symlink to `bin/vmware-uninstall.pl': Operation not permitted
vmware-server-distrib/FILES
tar: vmware-server-distrib/lib/webAccess/java/jre1.5.0_15/lib/amd64/server/libjsig.so: Cannot create symlink to `../libjsig.so': Operation not permitted
tar: Exiting with failure status due to previous errors
andrew@desktop:/media/VMware$ 

Anyone know what causes this?

Ok, found out issue. Had to unpack the image on the filesystem drive.


Cheers

---

### Post by triva911 on 2010-08-13
Can i use this "HOW TO" for installing windwos xp on ubuntu 10.04 lucid lynx ???

---

### Post by nooto on 2010-10-14
Hi guys, 

I have a little problem with wmware server 2.01 build 156745 installed on linux.

The server was upgraded from version 1.0.6 ( probably reinstalled, i don't really know) and something has been messed up with the config  presume. Web access is not possible. The web console would not start.

-------------
server# /etc/init.d/vmware-mgmt restart
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                            done
Starting VMware management services:
   VMware Server Host Agent (background)                               done
   VMware Virtual Infrastructure Web Access
-------------

The server is still listening on port 902 (as 1.0.6 used to listen). But i receive errors when connecting to it with vsphere client. Web access is obviously not possible. So i can not connect.

The thing is that i want to reinstall, however I am newbie :) with wmware, have not done any intalls, not to mention reinstalls. The key thing is that i want to keep the virtual machines vmware server was controlling. I know the directory they reside.

Please let me know what should i do to backup the virtual machines, will I be able to run them on newest free wmware server ? And how to restore them to the new vmware server.

Just please add some steps, explanations to this scenario:

1. Backup ( how to ???)
2. Uninstall with: vmware-uninstall.pl
3. **Install with: [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)**
4. Recover from backup ( how to ??)

After this i need to run the web interface, download the client (vsphere client). And access the server. Manage and run my virtual machines (yeeey)

After the recovery i need the old snapshots to be working.

Hope any of you can help. I've been googling around for days. :(

---
nooto

---

### Post by belllleb on 2011-11-07
I have dual boot windows 7 and ubuntu. Is there a way to mount this existing windows7 system into vmware? (I have some programs inside windows already installed)
Do you have a link for a tutorial for beginner?

---

