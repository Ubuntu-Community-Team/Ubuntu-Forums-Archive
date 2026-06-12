---
title: "How to VMWare Server 1.0.6 and 2.0 RC1 in Ubuntu 8.04"
date: 2008-05-03
forum: Virtualisation
---

### Post by bodhi.zazen on 2008-05-03
[CENTER][FONT=Times New Roman][SIZE=6]Install VMWare in Ubuntu 8.04[/SIZE][/FONT][/CENTER]
[FONT=Times New Roman]
[CENTER][[IMG]http://tbn0.google.com/images?q=tbn:SalBlZhJj2MeFM:http://www.daniel15.com/blog/wp-content/uploads/2006/09/vmware-2.jpg[/IMG]]("http://www.daniel15.com/blog/wp-content/uploads/2006/09/vmware-2.jpg")
<click image for larger view>[/CENTER]


[COLOR=darkred]**[SIZE=2]_Update June 8, 2008_ ~ The any-any update is no longer required with VMWare Server 1.0.6[/SIZE]**[/COLOR]

[COLOR=darkred]**[SIZE=2]_Update July 12, 2008_ ~ Updated information on VMWAre Server 2.0 RC1[/SIZE]**[/COLOR]


[SIZE=4]Introduction[/SIZE]


[COLOR=blue]This update has been updated to VMWare server version 1.0.6 and 2.0 RC1. Installation of VMWAre Server 2.0 RC1 is very similar to 1.0.6 (scroll down a little).[/COLOR]

[COLOR=green]Anyone wishing to use the "old" method using the any-any-update see[/COLOR] [This thread]("http://ubuntuforums.org/showthread.php?t=826624").[INDENT][COLOR=blue]Thanks ~ [/COLOR][gtdaqua]("http://ubuntuforums.org/member.php?u=364412")[/INDENT]There have been a number of threads on the forums and hopefully this (brief) how to will help make the process as easy as possible.

*If you need a more detailed description please see this thread* :[INDENT][HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://ubuntuforums.org/showthread.php?t=183209")
[COLOR=blue] ~ Thanks[/COLOR][ Peturrr]("http://ubuntuforums.org/member.php?u=48310")[/INDENT]OttifantSir has made a copy of this how-to available for download as a pdf [Here]("http://www.megaupload.com/?d=MF9U2ZZN").

[COLOR=blue]~ Thanks[/COLOR] [/FONT][OttifantSir]("http://ubuntuforums.org/member.php?u=170483")
[FONT=Times New Roman] 
[SIZE=4][COLOR=navy]VMWare Server 1.0.6[/COLOR][/SIZE]


[LIST=1]
[*]If you have any problems installing 1.0.6, see the link at the bottom of this post under "trouble shooting" (or read through this thread for similar problems).
[*]Prep ~ Install the needed tools.
```
sudo apt-get install build-essential linux-headers-`uname -r` xinetd
```***64 bit users only***
In addition install ia32-libs (ia32-libs is in universe so you may need to enable the repository) :
```
sudo apt-get install ia32-libs
```
[*]Download vmware server (be sure to obtain a serial number) Place in an instalation directory ( I use ~/src/VMWare).

```
mkdir -p ~/src/VMWare #Download VMWare files here
```
[LIST]
[*]VMWare server : [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)
[*]VMWare serial number : [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)
[/LIST]
[*]Extract and uinstall VMWare Server.
```
cd ~/src/VMWare
tar xzf VMware-server-1.0.6-91891.tar.gz

cd ~/src/VMWare/vmware-server-distrib
sudo ./vmware-install.pl
```Select defaults.

***Enter your serial # during the installation.***
[*]Post-install configuration. Last, before running vmware :
```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
```
[*]In addition, for ***64 bit users only***. 
```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's:usr/lib/:usr/l32/:g'  /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```~ Thanks [fjgaude]("http://ubuntuforums.org/member.php?u=236865") and [Kokopelli]("http://ubuntuforums.org/member.php?u=109055") for the 64 bit information.
[/LIST]

That is all there is to it. VMWare should now be up and running.


[SIZE=4][COLOR=darkred]VMWare Server 2.0 RC1[/COLOR][/SIZE]

[COLOR=darkred]_Warning_ : I find VMWare Server 2.0 RC1 to be buggy, more then I would expect for a RC.[/COLOR]

Advantages of Server 2.0
[LIST]
[*]Web interface ~ this is a double edged sword. I would assume it may conflict with apache or lighttpd. It adds the convenience of remote admin over a web interface, but there is then a security risk.
[*]The web interface is a change, but I think I like it.
[*]It is easier to install.
[/LIST]


Limitations:
[LIST]
[*]The web interface is new, and takes some adjustment.
[*]Connecting to the web interface and allowing an exception for ssl and a plugin for firefox was a little strange.
[*]I could not give my virtual machines more then 2 CPU.
[*]Although I installed the 64 bit edition on a 64 bit system / cpu, and despite VMWare claiming support for 64 bit virtual machines, ***I could only emulate 32 bit guests***.
[*]You can NOT run VMWare and KVM (and likely Xen) at the same time. VMWare will install, but virtual machines will not start. *I had to disable KVM in my BIOS to enable VMWare*.
[*]_Security_. **VMWare server 2.0 installs a web server and uses ports 80 and 443 by default**. I would advise you change these ports, especially if you are already running a web server. I would firewall the non-ssl connection (port 80 by default) to ALL remote connections. I would limit the connections to the ssl port (443 by default) as much as possible, or even tunnel over ssh.
[/LIST]

[LIST=1]
[*]Download VMWare Server 2.0 from here :[INDENT][http://www.vmware.com/beta/server/index.html](http://www.vmware.com/beta/server/index.html)[/INDENT]Download *Both*VMware-server-2.0.0-101586.x86_64.tar.gz and VMware-vix-e.x.p-101586.x86_64.tar.gz (if you desire vix).

Again, I saved it in ~/src/VMWare

**Be sure to write down the serial number**
[*]Install build-essential```
sudo apt-get install build-essential
```
[*]Extract and install VMWare Server.
```
cd ~/src/VMWare
tar xzf VMware-server-2.0.0-101586.x86_64.tar.gz

cd ~/src/VMWare/vmware-server-distrib
sudo ./vmware-install.pl
```**[COLOR=blue]Select defaults.[/COLOR]**

***Enter your serial # during the installation.***
[*]Set a root password.

VMWare Server 2.0 uses a WEB INTERFACE. By default, the web interface is configured to allow root login, thus we need a root password. We will undo this later.

```
sudo passwd
```Enter your desired root password twice (second time to confirm). You will not see anything in the terminal as you type.
[*]Configure VMWare to allow users to log in.

Start vmware (as a user, not root):
```
vmware
```VMWare runs in FireFox at **[https://localhost/ui](https://localhost/ui)**

The first time you load the page, firefox will give you a warning. Go ahead and add an exception.

You will get a log in screen, log in as root.

Go to the "Permissions tab" -> click "New Permission"

From the pull down menus, add your user as an "Administrator"

Log out and back in as your user (rather then root).

Assuming that is working, lock the root account

```
sudo passwd root -l
```
[*]To get the web interface working (console tab), first create a Virtual machine. Once you start your first VM you need to allow firefox to install an addon. To do this, start your new VM, then click on the "Console" tab. You will see a black window with a text message [COLOR=red]"The VMWare Remote Console Plug-in is not installed ..."[/COLOR]

Click on the yellow "Install plugin". You will get a "warning" from firefox "Firefox prevented this site (127.0.0.1) from asking you to install software on your computer". **Click the "Allow" button on the upper Left** and install the plugin.

You will the need to re-start firefox, again log in and start your virtual machine. This time you will get notice that the VMWare  Remote Console Plug-in has been installed. Again click the Console tab. You will now see a black screen with the VMWare logo. Click anywhere in this screen to start the VMWare graphical screen (in a separate window).

From the VMWare console you have some limited options for admin of the VM (stop / reboot and access to removable devices).

*You can close Firefox and your Virtual Machine will continue to run. You can close the VMWare window or even log off and the virtual machine will continue to run*

Unfortunately, there is not a menu option to re-start the console, you have to re-start firefox, log in, and again start the console.
[/LIST]



[U][B][SIZE=4]Additional Options[/SIZE]
[/B][/U]

**_VMWare server mui_**
- VMware ESX-style web-access for configuration of your server
[LIST]
[*]Download [VMware-mui-1.0.6-91891.tar.gz]("http://download3.vmware.com/software/vmserver/VMware-mui-1.0.6-91891.tar.gz")
[*]Prep : ```
apt-get install libxi6 xfsprogs
```
[*]Install : ```
tar -xvzf VMware-mui-1.0.6-91891.tar.gz
cd cd vmware-mui-distrib
sudo ln -s -f /bin/bash /bin/sh # This may not be required
sudo ./vmware-install.pl
```
[*]Access [https://localhost:8333/](https://localhost:8333/)
[/LIST]


**_VMWare tools_**
- Quite easy : [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)


**_Directory (Folder) Sharing_**
This works by mounting a directory on the host onto the guest.
You need a patch, see this link :

[VMware Tools for VMware Workstation 6.0.4 build 93057 on Ubuntu 8.04 guest](http://ubuntuforums.org/showthread.php?t=846691)
[COLOR=blue]~ Thanks[/COLOR] [/FONT][Keithel]("http://ubuntuforums.org/member.php?u=191275")[FONT=Times New Roman]

**_File Sharing_**
- Samba is by far the easiest way to file share. It works out of the box with minimal end user configuration. See this page : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

*This link is specific to samba on VMWare*
[Sharing files between a Windows guest and Ubuntu host using VMware and Samba]("http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/")

[COLOR=blue]~ Thanks [/COLOR][gerula]("http://ubuntuforums.org/member.php?u=609282")

Do not let the size of that page distract you, follow the sections on graphical configuration. Samba also allows sharing of printers. [B][I]The only caveat with Ubuntu 8.04 is that after installing the samba server you need to log out and back in before your shares can be configured.
[/I][/B]
Alternates to Samba - [sshfs]("https://help.ubuntu.com/community/SSHFS"), [NFS]("https://help.ubuntu.com/community/NFSv4Howto"), ftp, http, or other network protocols.  


**_ Enable USB devices_**
- USB devices work out of the box with minimal (gui) configuration.
- Enable USB device sharing : Using any editor (gksu gedit /etc/fstab), add this line to /etc/fstab (works with VirtualBox as well) :twisted:

```
# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```Reboot and re-start VMWare Server.

- With your guest turned off : In the server window click "Edit virtual machine settings" -> Click "Add" in the lower left -> Select usb controller -> click finish.

Start your guest ...

- With your guest turned on : In the VMWare menu , at the top select "VM" -> Removable devices -> USB devices -> Select the USB device to share with your guest.


**_Kernel Upgrades_**
- After kernel upgrades you will need to re-run vmware-config-pl. Open a terminal and :

```
sudo vmware-config.pl
```Hope that helps. :)

[/FONT][FONT=Times New Roman]**_Trouble Shooting_**[/FONT]
[FONT=Times New Roman]- Problem installing ?
See this thread : [http://ubuntuforums.org/showthread.php?t=337040](http://ubuntuforums.org/showthread.php?t=337040)
[COLOR=blue]~ Thanks [/COLOR][/FONT][Illuvator]("http://ubuntuforums.org/member.php?u=205929")[FONT=Times New Roman] 


_**[SIZE=4]Remove (uninstall) VMWare[/SIZE]**_

 If you want to remove vmware, run :
```
sudo vmware-uninstall.pl
```[/FONT]

[IMG]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/IMG][FONT=times]*[SIZE=4][COLOR=navy][FONT=times]bodhi.[/FONT][/COLOR][FONT=times][COLOR=darkgray]zazen[/COLOR][/FONT][/SIZE]*[/FONT]

---

### Post by fjgaude on 2008-05-03
For 64 bit users there is one additional step in order to allow vmware console to launch:

```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

At least was necessary for my 64-bit installs.

Thanks for trying to put everything in one place, Bodhi.zazen!

frank

---

### Post by howipepper on 2008-05-03
Thanks for the info, it helped me immensely with VMWare Desktop (6.0.3) and Hardy.

---

### Post by bodhi.zazen on 2008-05-03
> **fjgaude said:**
> For 64 bit users there is one additional step in order to allow vmware console to launch:

```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```At least was necessary for my 64-bit installs.

Thanks for trying to put everything in one place, Bodhi.zazen!

frank


Thank you frank. I added this information to the post (and was able to get the code boxes working a little better).


This information is spread all over the forums and various internet sites, but I did not find all the information (ie links) and all the steps in any single place. Thanks to everyone who posted information on this, both on and off the Ubuntu forums.

---

### Post by fjgaude on 2008-05-03
We'll need to add to your post what it takes to use USBs in vmware. And also some info on samba and the like to access files host to guest, guest to host, eh?

---

### Post by Kokopelli on 2008-05-03
> **fjgaude said:**
> For 64 bit users there is one additional step in order to allow vmware console to launch:

```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

At least was necessary for my 64-bit installs.

Thanks for trying to put everything in one place, Bodhi.zazen!

frank

I would be cautious of running the sed commands in Hardy final.  It was needed during the Betas, but the loader was fixed to point to lib32 instead of lib at or near the final release.  If you run the sed commands on a properly updated libgtk2.0-0.loaders, the loader will point to "l3232" which is incorrect.

Also if I may make a suggestion.  Users should install the linux-headers metapackage for their running kernel. (Generally "linux-headers-general" for Desktop and "linux-headers-server" for a server install.)  This way if/when the kernel gets updated the headers are updated automatically as well.  It eliminates the confusion when they try and rebuild and the headers are not available.

---

### Post by fjgaude on 2008-05-03
What do you advise?

---

### Post by Kokopelli on 2008-05-03
> This information is spread all over the forums and various internet sites, but I did not find all the information (ie links) and all the steps in any single place. Thanks to everyone who posted information on this, both on and off the Ubuntu forums.

Guess you did not see my thread in either the beta or the Virtualization forums.  ;)  Good summary though and I am glad we got a sticky on the subject.

> What do you advise?

Are you talking to me?  If so my advice is to not run the sed commands unless you are getting the pixmap errors after completing all other steps.  Even then I would strongly advise checking the loader first.

if
```
cat /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders |grep lib32
```

comes back with any hits then running the sed commands will almost definitely break your loader.

---

### Post by bodhi.zazen on 2008-05-03
> **fjgaude said:**
> We'll need to add to your post what it takes to use USBs in vmware. And also some info on samba and the like to access files host to guest, guest to host, eh?

LOL, are you encouraging me to turn this into one of my "How-longs".

I added some basic information, I just do not recall the menus for adding usb devices (will add that later).

Other suggestions welcome.

:guitar:

---

### Post by Kokopelli on 2008-05-03
If you want a "safe" version of the sed commands you could do as follows:

```

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib\//usr\/l32\//g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib\//usr\/l32\//g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

```

that way "/usr/lib/<something>" would be updated to "/user/l32/<something>"  but "/usr/lib32/<something>" would be ignored and not update to "/usr/l3232/<something>".

NOTE: I have not tested this since I do not have any of my 64 bit machines with me, but the change was simple enough.

---

### Post by fjgaude on 2008-05-03
> **bodhi.zazen said:**
> LOL, are you encouraging me to turn this into one of my "How-longs".

I added some basic information, I just do not recall the menus for adding usb devices (will add that later).

Other suggestions welcome.

:guitar:

I'm not sure that the fixes, i.e., uncommenting four lines (#42 to #45) in the /etc/init.d/mountdevsubfs.sh file, is needed in the released 8.04. I ran a USB flash drive on a clean install and it loaded. Can't say if that would happen in vmware client or not... I don't have any systems I can test with at present.

---

### Post by fjgaude on 2008-05-03
> **Kokopelli said:**
> Are you talking to me?  If so my advice is to not run the sed commands unless you are getting the pixmap errors after completing all other steps.  Even then I would strongly advise checking the loader first.

if
```
cat /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders |grep lib32
```

comes back with any hits then running the sed commands will almost definitely break your loader.

Yes. Thanks. Maybe Bodhi.zazen can add your comment to his original post, to keep everything together.

---

### Post by bodhi.zazen on 2008-05-03
> **fjgaude said:**
> I'm not sure that the fixes, i.e., uncommenting four lines (#42 to #45) in the /etc/init.d/mountdevsubfs.sh file, is needed in the released 8.04. I ran a USB flash drive on a clean install and it loaded. Can't say if that would happen in vmware client or not... I don't have any systems I can test with at present.

I enable USB devices in a different way.

Add these lines to /etc/fstab :

```
# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

You need to re-boot for the changes to take effect, at least I could not get the changes to stick w/ simply mount -o remount ...

---

### Post by bodhi.zazen on 2008-05-03
> **Kokopelli said:**
> Also if I may make a suggestion.  Users should install the linux-headers metapackage for their running kernel. (Generally "linux-headers-general" for Desktop and "linux-headers-server" for a server install.)  This way if/when the kernel gets updated the headers are updated automatically as well.  It eliminates the confusion when they try and rebuild and the headers are not available.

This is good advice. On my system [FONT=Verdana][SIZE=2]```
apt-get install linux-headers-`uname -r`
```

installed 'linux-headers-generic" and "linux-headers-server" automagically.
[/SIZE][/FONT]

---

### Post by bodhi.zazen on 2008-05-04
> **fjgaude said:**
> [quote=Kokopelli;4871597]Are you talking to me? If so my advice is to not run the sed commands unless you are getting the pixmap errors after completing all other steps. Even then I would strongly advise checking the loader first.

if
```
cat /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders |grep lib32
```comes back with any hits then running the sed commands will almost definitely break your loader.

Yes. Thanks. Maybe Bodhi.zazen can add your comment to his original post, to keep everything together.[/quote]

If someone can confirm the sed commands for me I will change my first post (I do not have the hardware).

Also, with sed commands, I advise you consider a delineation other then /, for example :

sed -i -e 's_old_new_g' file

@Kokopelli : You were asking me earlier re: my sources of information. To be honest I have been running VMWare for some time, and learned about vmware-any-any-update from the Fedora forums some time ago. I have seen many requests for how to install VMWare in Ubuntu 8.04, but did not see a complete start-to-finish guide anywhere.

I found the cp commands here : 

[http://fiddlerelf.com/2008/04/27/howto-install-vmware-server-on-ubuntu-804/](http://fiddlerelf.com/2008/04/27/howto-install-vmware-server-on-ubuntu-804/)

And there was a second site, it was a blog, and to be honest I can not find it now (spent 15 minutes pooring through google searches).

---

### Post by Kokopelli on 2008-05-04
I was not asking for where you got the information, just pointing out there were at least two threads that already gave it. The important part is that we have a sticky now though, the rest does not matter.

I used the picket fence style in sed because that was what the original command used:

```

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

```

Will do the same thing. If you do a search for "l3232" on the virtualization forum you will see a number of hits where the original command was used on a loader already pointing to lib32.  It is more important that the command not be used unless needed than the particulars of the syntax. I am just trying to mitigate the risk with a command that should not actively break the loader should it be run when not needed.

---

### Post by bodhi.zazen on 2008-05-04
> **Kokopelli said:**
> I was not asking for where you got the information, just pointing out there were at least two threads that already gave it. The important part is that we have a sticky now though, the rest does not matter.

I used the picket fence style in sed because that was what the original command used:

```

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

Thank you Kokopelli, I will make the changes.

If you see a thread that merits a sticky, please report it (as you would "spam") or PM me. This way the mods can look into it.

On that note, I think I am going to take the current stickies in this forum and make a "mega sticky" with useful links ...

---

### Post by diablo75 on 2008-05-04
> **bodhi.zazen said:**
> 

Now run vmware-any-any-update-116
```
cd  ~/src/VMWare/vmware-any-any-update116
sudo ./runme.pl
```

Enter your serial # during the installation.


Thanks for the tutorial, it worked.  Since I've done this before, this part above didn't stump me.  But you should add a sentence here that tells people to say "YES" to that question about running the config script when they execute the any-any patch, because the default says "no" due to them entering no the first time around.  This might throw newbies off if that little detail isn't put in clear text.  :)

---

### Post by Matt26 on 2008-05-04
help!  i can't find the launch icon under the Applications/System Tools menu where the vmware applications normally reside.. i just installed and then removed server 2 beta 2 but i don't think this would have any bearing on my installation of server 1.5?  i've been able to install and run both workstation and server in the past with no issues.  any ideas?  thanks.

---

### Post by fjgaude on 2008-05-04
The icon may be in Applications/Other.

---

### Post by arang on 2008-05-04
hi guys i've been reading this and i have a few questions, one is, would vmware have any kind of crash with the kvm implementation in hardy, and also what about those lines for 64 bits that are posted at the beginning of the thread, could someone finally clarify them?? are they required or not, are they dangerous or not, cos i got so confused after reading what u all wrote.

And to end it, i wanna know if the any-to-any is needed for vmware 6.0.3 and 6.5 beta

---

### Post by KillaB7 on 2008-05-05
Does this method include support for AMD-V and IVT (vmx flag)?

---

### Post by Matt26 on 2008-05-05
> **fjgaude said:**
> The icon may be in Applications/Other.

thanks, i found it!

---

### Post by Matt26 on 2008-05-05
i am trying to open my vm and i get the following error message:

Unable to add virtual machine "/home/matthew/vmware/XP/Windows XP Professional/Windows XP Professional.vmx" to the inventory: No permission to perform this operation

i checked the permissions to the vm's parent directory and the only thing i updated was read and write access for group permissions (which was set to just read only) but that didn't do the trick...

any ideas?

---

### Post by fjgaude on 2008-05-05
Try this:

```
sudo vmware
```

and then see if you can add the VM. If you can then, exit, go back and run vmware from the icon.

---

### Post by fjgaude on 2008-05-05
> **KillaB7 said:**
> Does this method include support for AMD-V and IVT (vmx flag)?

Yes.

---

### Post by veloce on 2008-05-05
> **Matt26 said:**
> i am trying to open my vm and i get the following error message:

Unable to add virtual machine "/home/matthew/vmware/XP/Windows XP Professional/Windows XP Professional.vmx" to the inventory: No permission to perform this operation

i checked the permissions to the vm's parent directory and the only thing i updated was read and write access for group permissions (which was set to just read only) but that didn't do the trick...

any ideas?

Also, the vmx file needs to be executable.

---

### Post by Matt26 on 2008-05-05
> **veloce said:**
> Also, the vmx file needs to be executable.

i looked at the permissions for the vmx file and it says root is the owner- so i tried applying permissions from the parent folder (which is owned by my user account) to it's subfolders but that didn't take effect- how can i make the entire vm's folder (including all subfolders and files) owned by my user account?  thanks.

---

### Post by bodhi.zazen on 2008-05-05
sudo chown -R user.user /home/matthew/vmware/XP/

---

### Post by fjgaude on 2008-05-05
> **bodhi.zazen said:**
> sudo chown -R user.user /home/matthew/vmware/XP/

That should be a ":" between user:user, not a period?

---

### Post by Matt26 on 2008-05-05
> **bodhi.zazen said:**
> sudo chown -R user.user /home/matthew/vmware/XP/

that did the trick, thanks!  can you explain why any attempt to change these permissions in nautilus doesn't work?  i have run into this same problem in the past attempting to change permissions on files that are in my home folder and needed to resort to the terminal- maybe it's just me, but why bother having this GUI alternative if it doesn't work?

---

### Post by bodhi.zazen on 2008-05-05
> **fjgaude said:**
> That should be a ":" between user:user, not a period?

he he he ... nope, a . works as well as a : and you can type a . without the shift key :twisted:

> **Matt26 said:**
> that did the trick, thanks!  can you explain why any attempt to change these permissions in nautilus doesn't work?  i have run into this same problem in the past attempting to change permissions on files that are in my home folder and needed to resort to the terminal- maybe it's just me, but why bother having this GUI alternative if it doesn't work?

You can not change the ownership/permissions of a file or directory you do not own. In this case the directory was owned by root.

You could have done it with :

```
gksu nautilus
```

---

### Post by anelsa on 2008-05-06
Hi, All

I already install vmware-server @ hardy server and work.
The problem, I cannot install server-mui.
The installation can't detect that vmware-server already installed.
Anybody have same problem like this.
If there is a clue, please help for this problem.
Thank you.

---

### Post by aroddo on 2008-05-06
followed the guide - still doesn't work.

got the 64bit version of 8.04

>  vmware
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6f9c767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6f9c8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e1b1bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d0b969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7d0bf4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b51180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b51d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b21c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b2e24f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b21c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b2db34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a32298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a32586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a3477e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c47459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c2f3a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c2f076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c466eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7c45d46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7c460b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6f9c767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6f9c81e]
#2 /usr/lib32/libX11.so.6 [0xf7e1a518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7dfdc9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7d03ed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d028b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d02d39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7d02ec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b4f9b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b51d75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b21c14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b2e24f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b21c14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b2db34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a32298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a32586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a3477e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c47459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c2f3a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c2f076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.


---

### Post by aroddo on 2008-05-06
damn ... why do I find solutions always minutes after i post the problem ....

>  sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders 
doing this eliminates the l3232 problem.

---

### Post by anelsa on 2008-05-06
> **anelsa said:**
> Hi, All

I already install vmware-server @ hardy server and work.
The problem, I cannot install server-mui.
The installation can't detect that vmware-server already installed.
Anybody have same problem like this.
If there is a clue, please help for this problem.
Thank you.

Problem Solved after install :

apt-get install libxi6 xfsprogs

Thx all.

---

### Post by bodhi.zazen on 2008-05-06
> **anelsa said:**
> Problem Solved after install :

apt-get install libxi6 xfsprogs

Thx all.

anelsa: I added some information to my original post. If it needs to be updated please let me know.

---

### Post by hawk1278 on 2008-05-06
I followed the instructions but when I try to run sudo vmware I get the following.  What other libraries need to be installed?:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

---

### Post by KillaB7 on 2008-05-06
Is there any difference between the VMWare-tools install method listed on the [wiki](https://help.ubuntu.com/community/VMware/Tools#head-b3125d8f2afa6dd6c8b75732b6a397baf8e1b3d7) vs. just clicking VM-->Install VMWare Tools... from the Server Console?

I believe that's all I did in Gutsy and it worked fine.

---

### Post by bodhi.zazen on 2008-05-07
> **KillaB7 said:**
> Is there any difference between the VMWare-tools install method listed on the [wiki]("https://help.ubuntu.com/community/VMware/Tools#head-b3125d8f2afa6dd6c8b75732b6a397baf8e1b3d7") vs. just clicking VM-->Install VMWare Tools... from the Server Console?

I believe that's all I did in Gutsy and it worked fine.

No that works just fine for windows guests. With linux guests however you need to manually install (after mounting the iso image by VM -> Install VMWare Tools .... )

---

### Post by cwrather on 2008-05-09
> I followed the instructions but when I try to run sudo vmware I get the following. What other libraries need to be installed?:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

I managed to solve this problem in Workstation 5.5.6 by using the "any-any" patch, then doing the following:

sudo cp /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1.bak

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/

If it doesn't work for you, you can restore the original file with the backup.

---

### Post by UnknownFear on 2008-05-09
I am trying to follow this tutorial, but whne I go to install vmware-server, I get this:

```
dan@dan-desktop:~$ cd ~/src/VMWare/vmware-server-distrib
dan@dan-desktop:~/src/VMWare/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

dan@dan-desktop:~/src/VMWare/vmware-server-distrib$
```

I have completley removed vmware-server from synaptic package manager, so I don't know why it keeps saying there is a previous installation. I really need some help on this. And yes, I have both the vmware-server and update-any-any folders in ~/src/VMWare. Thanks for the help.

---

### Post by fjgaude on 2008-05-09
> **UnknownFear said:**
> I am trying to follow this tutorial, but whne I go to install vmware-server, I get this:

```
dan@dan-desktop:~$ cd ~/src/VMWare/vmware-server-distrib
dan@dan-desktop:~/src/VMWare/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

dan@dan-desktop:~/src/VMWare/vmware-server-distrib$
```

I have completley removed vmware-server from synaptic package manager, so I don't know why it keeps saying there is a previous installation. I really need some help on this. And yes, I have both the vmware-server and update-any-any folders in ~/src/VMWare. Thanks for the help.


The easiest way I've found to remove a previous install is to rename the vmware folder in /etc:

```
sudo mv /etc/vmware /etc/vmwarebak
```

Then re-install. You can then delete the bakcup file.

---

### Post by catmanoct on 2008-05-09
Hi all!
I'm running into an error message near the end of the "VMWare-any-any-update-116" part of the fix.  I'll post what I see there:
```
Please specify a port for remote console connections to use [902] 

 * Stopping internet superserver xinetd                               [ OK ] 
 * Starting internet superserver xinetd                               [ OK ] 
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
I added everything after the Port selection because I'm not really sure what's failing.  I'll admit, I'm very very green to Linux and Ubuntu in general, so I'm not sure if the "timestamp" message at the end is an easy fix that has nothing to do with either VMWware Server or the Any-any-update.

Any idea what I'm missing?  Thanks all :)

---

### Post by UnknownFear on 2008-05-09
> **fjgaude said:**
> The easiest way I've found to remove a previous install is to rename the vmware folder in /etc:

```
sudo mv /etc/vmware /etc/vmwarebak
```

Then re-install. You can then delete the bakcup file.

Umm.. I tried that but it said i cant move it. What is the rename command?

---

### Post by UnknownFear on 2008-05-09
Oh wait! I was able to install vmware-server and vmware-any-any update116! Now, I set up a new virtual machine. This is what I selected:

Custom, Microsoft Windows (XP Pro), Defeault Names, One Processor, Check make private, Default memory, NAT settings, BusLogic, Use physical disk, /dev/sdb (individual partitions), selected partition 1, default

Now, how do I set it up so I can boot into my existing windows xp harddrive?

---

### Post by UnknownFear on 2008-05-09
This is what appears after the BIOS appear. It goes to boot and this comes up

[http://img116.imageshack.us/my.php?image=screenshotsj0.png](http://img116.imageshack.us/my.php?image=screenshotsj0.png)

I am trying to boot my existing XP partition. Any help with this?

---

### Post by UnknownFear on 2008-05-09
I got it to work!!!! I can finally boot into my existing Windows XP Pro partition via VMware!! The problem I had was I wasn't choosing the right device. I had to choose both my Linux and Windows XP partitions, because Linux has the GRUB loader so you can choose which OS to boot into. It is a tad slow, but hey.. friggin AWESOME!! :)

---

### Post by fjgaude on 2008-05-09
> **UnknownFear said:**
> Umm.. I tried that but it said i cant move it. What is the rename command?

mv is the rename command in linux. Did you use sudo to get to be root?

Anyway you seem to have got to where you wished to go. Make sure you install the Tools. And set everything in the Edit, Preferences, and VM menus to what pleases you.

---

### Post by UnknownFear on 2008-05-09
Hey. Got a small question. After I set up VMware with my XP, I restarted my computer and, before it booted into the GRUB menu, it took a RIDICUIOUSLY long time to boot into GRUB. It took 10 minutes!!! Can someone tell me why this happens?

---

### Post by Kokopelli on 2008-05-09
> **catmanoct said:**
> Hi all!
I'm running into an error message near the end of the "VMWare-any-any-update-116" part of the fix.  I'll post what I see there:
```
Please specify a port for remote console connections to use [902] 

 * Stopping internet superserver xinetd                               [ OK ] 
 * Starting internet superserver xinetd                               [ OK ] 
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
I added everything after the Port selection because I'm not really sure what's failing.  I'll admit, I'm very very green to Linux and Ubuntu in general, so I'm not sure if the "timestamp" message at the end is an easy fix that has nothing to do with either VMWware Server or the Any-any-update.

Any idea what I'm missing?  Thanks all :)


Try this then rerun the config:

```
sudo touch /etc/vmware/ssl/rui.key
sudo touch /etc/vmware/ssl/rui.crt
```

---

### Post by hank@rdbss on 2008-05-10
Thank you!  I still had to add some libraries since I have not installed a desktop, but this brief was an excellent and irreplacable guide.

---

### Post by sebbouckaert on 2008-05-10
Very good guide, got VMware server running in Hardy in less than 5 minutes. Thank you! :)

---

### Post by altonbr on 2008-05-10
I wrote a script that takes care of the exact same thing.

I wouldn't mind collaborating with you to make it better :)

[http://ubuntuforums.org/showthread.php?t=788169](http://ubuntuforums.org/showthread.php?t=788169) (Install VMware with a script)

---

### Post by alien_mind on 2008-05-10
I can't launch vmware via the desktop launcher. I need to open a console and launch by hand.

Any ideas?

---

### Post by altonbr on 2008-05-10
> **alien_mind said:**
> I can't launch vmware via the desktop launcher. I need to open a console and launch by hand.

Any ideas?

Yeah, I had a piece of code in my script (as mentioned above) for this at one point. Run this:
```
echo "
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Categories=System
Terminal=false
Icon[en]=/usr/share/pixmaps/vmware-server.png
Name[en]=VMware Server
Exec=vmware
Name=VMware Server
Icon=/usr/share/pixmaps/vmware-server.png" | sudo tee /usr/share/applications/vmware-server-ubuntuforums.desktop
```

The new launcher will be found at 'Applications > System Tools > VMware Server'

---

### Post by pi13 on 2008-05-11
Hi all,

First of all I would like to point out that I'm newbie when it comes to Ubuntu, well linux in general.

I've managed to install VMWare using, not this but other very similar tutorial I've found on the internet while searching for a way to do this. Anyways it worked,I've managed to create and run VM without any problems but...

Installation of windows xp professional is taking forever, literally. I run the installation of XP for the first time, it started to copy system files, and after it reached 92% (after good 1-2 hours) my system froze and my screen went black. All I could do is restart my laptop manually.

So I've tried it again, after I deleted previously created VM since it reported error because no system has been installed and I didn't know what else to do, I got even worse results, my system froze as soon as installation started.

Has anyone had similar problems?

Tnx in advance.

Cheers!

---

### Post by catmanoct on 2008-05-12
> **Kokopelli said:**
> Try this then rerun the config:

```
sudo touch /etc/vmware/ssl/rui.key
sudo touch /etc/vmware/ssl/rui.crt
```

This worked, but then my installation ran into a problem when it came time to enter a key.  I've tried tons of keys now, and registered for new keys from VMware three times now, and each time the installer says the keys aren't valid.  ARGH!

I'm rolling back to Ubuntu 7.XX and will just upgrade when VMWare catches up with the new release.  Thanks for your help!

---

### Post by altonbr on 2008-05-12
> **pi13 said:**
> Hi all,

First of all I would like to point out that I'm newbie when it comes to Ubuntu, well linux in general.

I've managed to install VMWare using, not this but other very similar tutorial I've found on the internet while searching for a way to do this. Anyways it worked,I've managed to create and run VM without any problems but...

Installation of windows xp professional is taking forever, literally. I run the installation of XP for the first time, it started to copy system files, and after it reached 92% (after good 1-2 hours) my system froze and my screen went black. All I could do is restart my laptop manually.

So I've tried it again, after I deleted previously created VM since it reported error because no system has been installed and I didn't know what else to do, I got even worse results, my system froze as soon as installation started.

Has anyone had similar problems?

Tnx in advance.

Cheers!

How much RAM does your laptop have and how much did you give this Windows installation?

> **catmanoct said:**
> This worked, but then my installation ran into a problem when it came time to enter a key.  I've tried tons of keys now, and registered for new keys from VMware three times now, and each time the installer says the keys aren't valid.  ARGH!

I'm rolling back to Ubuntu 7.XX and will just upgrade when VMWare catches up with the new release.  Thanks for your help!

Really? Don't roll-back just yet! Try my installation script here: [http://ubuntuforums.org/showthread.php?t=788169](http://ubuntuforums.org/showthread.php?t=788169) before going back to 7.10. I'm pretty darn sure it will work.

---

### Post by pi13 on 2008-05-12
> **altonbr said:**
> How much RAM does your laptop have and how much did you give this Windows installation?


It has 1 GB of RAM. First time I forgot to change amount of RAM so it stayed on default size - 256, second time I've changed amount of RAM to 772 (blue point and probably overdid it). btw I have Dell Inspiron 6400.

Tnx.

---

### Post by catmanoct on 2008-05-12
> Really? Don't roll-back just yet! Try my installation script here: [http://ubuntuforums.org/showthread.php?t=788169](http://ubuntuforums.org/showthread.php?t=788169) before going back to 7.10. I'm pretty darn sure it will work.

I'm going to give your a script a go.  I also found a fix for the CD Key problem here: [http://ubuntuforums.org/showthread.php?t=337040](http://ubuntuforums.org/showthread.php?t=337040), but I'll run your script first.

I noticed from your other thread that you wanted someone with a 64-bit proc to run it, so I'll be your guinea pig :)  

I'll keep you all posted!

---

### Post by pmurnane on 2008-05-12
All:

Just a quick note.  When installing the VMware-MUI, I received the following error:

Starting httpd.vmware:-ne                                          failed

The solution is found at [http://searchservervirtualization.techtarget.com/tip/0,289483,sid94_gci1245056,00.html](http://searchservervirtualization.techtarget.com/tip/0,289483,sid94_gci1245056,00.html) (yes, even though the page says the fix is for Edgy, it worked for me in Hardy).

HTH,
--Phil

---

### Post by catmanoct on 2008-05-12
Ok, here's the entire turn of events I've faced installing VMWare 1.0.5 on Ubuntu 8.04:
-had same issue as hawk1278 regarding missing libraries, which cwrather's solution fixed for me (Thanks!)
-Had the SSL Timestamp issue which kokopelli fixed; I'm not really sure what this command did, but it did the trick (Thank you as well!)
-I tried running altonbr's script both by saving it to a file called install_vmware.sh and running it from terminal AND by copying it directly into a command prompt.  I'm not 100% sure that I ran this correctly as I've not very well versed in Terminal.  In the end due to time constraints, I just continued everything manually, sans Alton's script. (Thanks to you as well!)

So now VMWare is installed, but my launcher won't work; identical to Alien_Mind's issue.  Altonbr's script he posted only created a duplicate launcher icon in a different location, but still wouldn't launch for me.  Instead, I went into the properties of Applications > Other > VMware Server Console, and changed:
Type to: *Application in Terminal*
and
Command to: *sudo vmware*
Although the only problem with this fix, is now Terminal launches, requests a manual entry of the sudo password, and VMware will run WITH the Terminal window staying open.  If I close the Terminal window while VMware is running, then VMware shuts down also 

/me rolls eyes

SO, any ideas on this?  Either: A.  Why won't VMware launch from the Launcher icon, and B.  If launching from the launcher is out of the question, how do I launch it from Terminal WITHOUT having to enter a sudo password and/or leaving the Terminal window open?

---

### Post by bodhi.zazen on 2008-05-12
LOL

Only partial solutions ...

First, if it runs as root, then you are looking at a permissions problem. Fix this and the rest is irrelevant ....

Second, if you run as root, I advise you use gksu (kdesu for kubuntu) rather then sudo.

Third, you can configure sudo to allow you to run vmware w/o a password.

Fourth, to run an application separate from the terminal, use nohup

```
nohup gksu vmware
```

You can now close the terminal w/o closing VMWare.

---

### Post by catmanoct on 2008-05-12
> **bodhi.zazen said:**
> LOL

Only partial solutions ...

First, if it runs as root, then you are looking at a permissions problem. Fix this and the rest is irrelevant ....

Second, if you run as root, I advise you use gksu (kdesu for kubuntu) rather then sudo.

Third, you can configure sudo to allow you to run vmware w/o a password.

Fourth, to run an application separate from the terminal, use nohup

```
nohup gksu vmware
```

You can now close the terminal w/o closing VMWare.

the ```
nohup gksu vmware
``` worked fine.  If there is a permissions issue, I'm not really sure where to tackle that.  I'm assuming I have to set my username as owner of where ever VMware server is install (I used all program defaults).  Or would only specific folders require that my user name has ownership?

Sorry, I know that now we're shying away from VMware help and into Ubuntu Linux security basics, but I'm still new to Linux and don't know my way around yet. :)

---

### Post by cim on 2008-05-12
I successfully installed VMware Server by following the tutorial but I'm having some problems like some people in here, the VMware software hangs when I launch it from the Applications > Other shortcut. 

I tried the nohup gksu vmware command in the terminal and I get this 

```
nohup: ignoring input and appending output to `nohup.out'
```

It stays like that for a LONG time, I don't know exactly but I'm not sure waht is going on? Anybody having the same problem as me?

Also if I type vmware or sudo vmware on console it hangs for a long time too. I'm running Ubuntu Hardy 8.04 with 2 gigs of RAM and an AGP ATI card.

---

### Post by bodhi.zazen on 2008-05-12
Again, not sure about the problems at this point, but that output from nohup is normal.

---

### Post by cim on 2008-05-12
Hmm, you're right. I decided to wait for something to happen when I typed sudo vmware on the console. After a while the VMware server console appeared but now I can't connect to the localhost it says:

[B]The local VMware Server is not currently installed, or is not currently running.

Make sure that the server is properly installed and try again.[/B]

I'm pretty sure the install went fine, any suggestions?

---

### Post by cim on 2008-05-12
I think it might have to do something with step 4 using this post-installation commands:

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
```

I reinstalled VMware and typed in vmware in the console and it showed things that wasn't there before. And when I ran those commands, it went back to my old problem which was it would hang or take a long time to load.

Can anyone confirm this?

---

### Post by NikoC on 2008-05-13
Guide worked like a charm for me! Thanks!

---

### Post by schuelaw on 2008-05-13
Maybe I missed something in the instructions (which I appreciate BTW), but I couldn't get a VM started until I manually ran depmod -a, prior to that the vmmon kernel module wouldn't load.  If anyone is running into that problem here, try:

sudo depmod -a

after you've done everything else.

---

### Post by Nampla on 2008-05-14
I am pretty sure vmserver 1.05 has only usb 1.1 not 2.0 and vmware server 2 just released a beta version that can use usb 2.0.  I dont use any usb i simply mount the drive and share the folder thru samba. This works obviously only for storage devices.

---

### Post by Kosmi4 on 2008-05-15
hello there..i followed the " how to VMWare" from the first page of this post, downloaded the files (vmware-any-any-update-116.tgz & VMware-server-1.0.5-80187.tar.gz) to my desktop and i cant place them now to the ~/src directory,to continue to the next step (mkdir -P ~/src/VMWare #Download VMWare files here)..
Could you please help me to place them both in the same directory as bodhi.zazen says ( I use ~/src/VMWare) .
I tried to copy and paste them but i have no permission to do that..
Thanks for your time..

---

### Post by am7146 on 2008-05-15
Thank you!  Worked great -except- for one hitch on my Heron machine. Here's what happened (and the fix).  The install worked great but when I tried to start VMWare Server it would pop up an icon in the tray like it's starting, but then it would disappear after a few seconds.  Nothing in the logs that I could see, no error message.  I remembered something from when I installed VMWare a long time ago and looked for /etc/vmware/not_configured and it was there.  That's the file that tells vmware if you've run vmware-install.pl correctly (no idea why it was still there and didn't try to debug it).  Soooo...

```
sudo rm /etc/vmware/not_configured
```

and I was up and running.

Andy-

---

### Post by bodhi.zazen on 2008-05-15
> **Kosmi4 said:**
> hello there..i followed the " how to VMWare" from the first page of this post, downloaded the files (vmware-any-any-update-116.tgz & VMware-server-1.0.5-80187.tar.gz) to my desktop and i cant place them now to the ~/src directory,to continue to the next step (mkdir -P ~/src/VMWare #Download VMWare files here)..
Could you please help me to place them both in the same directory as bodhi.zazen says ( I use ~/src/VMWare) .
I tried to copy and paste them but i have no permission to do that..
Thanks for your time..

Sorry , small typo on my part.

that is a small p in :

```
mkdir -p ~/src/VMWare
```

Updated my original post as well.

---

### Post by Kosmi4 on 2008-05-15
Thanks for your reply.. but i still have the same problem ..i can't copy the folder VMWare (containing the downloaded files vmware-any-any-update-116.tgz & VMware-server-1.0.5-80187.tar.gz ) which is at my desktop, to the destination you propose (the ~/src directory).
When i go there (usr/src/) i can't paste the folder from my desktop cause i don't have permission as root. 
So i can't go on to the next step..
I have the files downloaded to my desktop and i can't place them to the ~/src directory..
Thank you again for your help

---

### Post by bodhi.zazen on 2008-05-15
> **Kosmi4 said:**
> Thanks for your reply.. but i still have the same problem ..i can't copy the folder VMWare (containing the downloaded files vmware-any-any-update-116.tgz & VMware-server-1.0.5-80187.tar.gz ) which is at my desktop, to the destination you propose (the ~/src directory).
When i go there (usr/src/) i can't paste the folder from my desktop cause i don't have permission as root. 
So i can't go on to the next step..
I have the files downloaded to my desktop and i can't place them to the ~/src directory..
Thank you again for your help

Well, you do not need to be running as root.

First run these commands in a terminal, as your user not root.

```
ls -l home | grep src
```

Do you own the src directory ?

If not :

```
sudo chown -R user.user /home/user/src
```

where "user" == your log in name.

Then mv ~/Desktop/*ware*.* ~/src/VMWare

Continue to follow the tutorial as your user, use sudo when you need to run as root.

---

### Post by kalyptus on 2008-05-16
Thanks for this info... Just planning to install a vmware server to my machine... it seems all the stuffs i need are here! again thanks...

---

### Post by andtsoreyu on 2008-05-16
Yeah everything worked fine for me too!  Thanks a lot!

---

### Post by pearsonapollo on 2008-05-16
Hello, I found this to be extremely helpful, however, I lost my internet connection shortly after installing VM.  I saw another post where someone deleted some VM files to get the network back online, but they did not specify which files they deleted.  I was wondering if anyone might know which files to delete.  Also, as soon as I uninstalled VM I got my network connection back.

I am pretty new to using linux, but I sure like it!!  Thank you in advance for any help.

I am running Ubuntu 8.04 LTS Hardy Heron.  AMD Athlon 3500+, 1GB DDR2, Belkin Wireless adapter.

---

### Post by giraf on 2008-05-16
Hi
After installing VMWARE in my UBUNTU 8.04 machine , I'm getting "Access denied " after the loggin window appears in the [https://27.0.0.1:8333/ui/#](https://27.0.0.1:8333/ui/#)
Any ideas

---

### Post by Kosmi4 on 2008-05-16
thank you for your help..
As i have said .. the support of the community is the major reason i love ubuntu..
:)

---

### Post by fjgaude on 2008-05-16
> **giraf said:**
> Hi
After installing VMWARE in my UBUNTU 8.04 machine , I'm getting "Access denied " after the loggin window appears in the [https://27.0.0.1:8333/ui/#](https://27.0.0.1:8333/ui/#)
Any ideas

If the message is from Ubuntu then you need your password placed in the Samba file:

```
sudo smbpasswd -a <login>
```

Use your login name and password as prompted.

---

### Post by kuehlc on 2008-05-18
Hey first of all thanks for the great tutorial, I've been tinkering with linux for years now but am new to Ubuntu and am blown away by the OS and the support available from people like you.

I would however like to point out that the any-any-116 patch does not allow bridging to a wireless adapter. After some googling I found the following patch which did work for me: [http://liken.otsoa.net/pub/vmware/vmware-any-any-update-115-K2.6.24-WirelessBridge.tar.gz](http://liken.otsoa.net/pub/vmware/vmware-any-any-update-115-K2.6.24-WirelessBridge.tar.gz)

I simply used it rather than the patch linked in your tutorial and I am now running XP Pro bridged to my wlan0 adapter in Hardy 8.04.

Thanks again, hope this helps

---

### Post by Black Sliver on 2008-05-18
The sound-problem: vmware-server 1.x uses oss/dsp for sound which can not be mixed by default, so you hear either vmware **or** the other program(s) depending on which opens the sound device first. 

As i heard pulse audio can also receive oss/dsp audio signals, so this "patch" might be useless if you use pulse. 

Here's a bash script that installs alsa-oss and replaces the start-scripts for **vmware-server 1.x** so it uses the alsa-oss-wrapper. I can't guarantee its working, but it worked for me on gutsy and hardy.
**Use at your own risk!**

To apply the patch
1. download the attachment
2. extract the .tar.gz
3. run the script from terminal

To remove the patch
1. delete /usr/bin/vmware and rename /usr/bin/vmware.real back to /usr/bin/vmware.
2. delete /usr/lib/vmware/bin/vmware-vmx and rename /usr/lib/vmware/bin/vmware-vmx.real back to /usr/lib/vmware/bin/vmware-vmx

---

### Post by Ximbiot on 2008-05-19
Thanks for the clear HOWTO.  Unfortunately it is not working for me.  Everything compiles cleanly, then I get the same problem starting vmmod as [another user mentioned]("http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/#comment-4527") (wanted vmmod version 138.0 found version 137.0).

I hacked vmware-any-any-update116 horribly to cause the driver that claimed to be #137 to claim to be #138 (this was a one-line change - otherwise it was already a simple wrapper for the 138 driver).

Now the server starts correctly without complaining about the vmmon version, but I cannot power on any guests.  First I get a warning about enabling VT support in my BIOS (I never had this problem on the same computer when booting into Windows), then the thing just powers right back off.  The server log says:

May 19 13:39:24: app| VMServerd IPC closed the connection with thread /host/Virtual Machines/Ubuntu/Ubuntu.vmx (0x83021d0)
May 19 13:39:24: app| Lost connection to /host/Virtual Machines/Ubuntu/Ubuntu.vmx (/host/Virtual Machines/Ubuntu/Ubuntu.vmx) unexpectedly.
May 19 13:39:24: app| cleanup: cleaned up 2 objects
May 19 13:39:24: app| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
May 19 13:39:24: app| VMHS: Connection to VM broken: cfg: /host/Virtual Machines/Ubuntu/Ubuntu.vmx; error: Pipe: Read failed; state: 3
May 19 13:39:24: app| Operation failed to change the VM to the expected power state.
May 19 13:39:24: app| VM suddenly changed state: poweredOff.

The same thing happens whether I'm connected as myself or root.

Any help is appreciated.

Thanks,

Derek

---

### Post by Ximbiot on 2008-05-19
> **Ximbiot said:**
> Now the server starts correctly without complaining about the vmmon version, but I cannot power on any guests.  First I get a warning about enabling VT support in my BIOS (I never had this problem on the same computer when booting into Windows), then the thing just powers right back off.  The server log says:


Never mind.  I think the problem had to do with the fact that I was working directly from an NTFS file system (I'm running via a Wubi install).

This brings up a second question, however.  Is there a way to run VMs I've stored on my NTFS partition without expanding my Wubi disk file and copying them over?

---

### Post by altonbr on 2008-05-19
> **Ximbiot said:**
> Never mind.  I think the problem had to do with the fact that I was working directly from an NTFS file system (I'm running via a Wubi install).

This brings up a second question, however.  Is there a way to run VMs I've stored on my NTFS partition without expanding my Wubi disk file and copying them over?

If you can mount the NTFS partition, then I'd say yes.

```
sudo aptitude install ntfs-config
``` will help. Once you run that program, the mount should show up on your desktop. Then use that path to run the partition off/in VMware.

---

### Post by djhayu on 2008-05-19
I am still trying to install vmware on hardy, but I keep getting the:

libXt.so.6 => not found
libICE.so.6 => not found
libSM.so.6 => not found

I cannot find which packages I need to install for these.

Any help woudl be greatly appreciated.

---

### Post by tomjennings on 2008-05-19
No joy here. I get an error, still, compiling vmstat. uname says
$ uname -a
Linux zx 2.6.24-16-rt #1 SMP PREEMPT RT Thu Apr 10 15:15:40 UTC 2008 i686 GNU/Linux

installed headers etc as instructed, carefully.

> 1000 lines of error (not warnings), ending in:

...
clared (first use in this function)
/tmp/vmware-config2/vmmon-only/linux/driver_compat2.h:1743: error: ‘EPERM’ undeclared (first use in this function)
/tmp/vmware-config2/vmmon-only/linux/driver_compat2.h: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver_compat2.h:2026: error: ‘EINVAL’ undeclared (first use in this function)
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-rt'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.


I ran runme.pl in vmware-any-any twice; any chance it patched something twice and wrecked it?

PS: I did vmware sever bin/vmware-unuinstall, untarred everything, etc same difference.

---

### Post by Ximbiot on 2008-05-20
> **altonbr said:**
> If you can mount the NTFS partition, then I'd say yes.

```
sudo aptitude install ntfs-config
``` will help. Once you run that program, the mount should show up on your desktop. Then use that path to run the partition off/in VMware.

The NTFS partition is already mounted (the Wubi install automatically mounts it as /host).  Unfortunately, as I was trying to explain, when I try to run a VM stored on the NTFS partition, even one created by the Linux VMWare install, VMWare exits without an intelligible error (see my post above).

VMs work just fine if I create and run them on/from the ext3 partition.  I've found some other posts implying that VMWare is very sensitive to permissions on Linux, so my current guess is that the NTFS mount (which has rwxrwxrwx root root permissions on everything) is confusing it somehow, but maybe it's something else.

This might not be the right place to ask, but I am having yet another difficulty.  I can run new VMs from ext3, but when I try to create one based on the physical Vista partition, I get an instant blue screen which vanishes into a reboot before I can read the error code.  Any ideas on how to get the physical Vista partition to boot?

---

### Post by Ximbiot on 2008-05-20
> **tomjennings said:**
> 
> 1000 lines of error (not warnings), ending in:

...
clared (first use in this function)
/tmp/vmware-config2/vmmon-only/linux/driver_compat2.h:1743: error: ‘EPERM’ undeclared (first use in this function)
/tmp/vmware-config2/vmmon-only/linux/driver_compat2.h: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver_compat2.h:2026: error: ‘EINVAL’ undeclared (first use in this function)

This looks like you are missing errno.h, which would imply you don't have the GNU C compiler installed.  Of course, that can happen if an early syntax error makes the compiler misinterpret or fail to include errno.h when it gets there.  What are the first few errors you are seeing?

> **tomjennings said:**
> 
I ran runme.pl in vmware-any-any twice; any chance it patched something twice and wrecked it?

To be sure, just start over.  Uninstall if you feel like it (you don't need to), then start over with the instructions in this post (installer, any-any, ln -fs...).

---

### Post by altonbr on 2008-05-20
@everyone
If you're having problems running these commands yourselves, I've tried to compile all of them into a script here: [http://ubuntuforums.org/showthread.php?t=788169](http://ubuntuforums.org/showthread.php?t=788169)

A lot of people are having luck with the script so I hope it works for you too!

My script largely comes from bodhi.zazen's post, so a lot of credit it due to him and other contributors. Please understand that I am not trying to take any light away from bodhi.zazen, as we are both trying to support Ubuntu users!

---

### Post by hodenkat on 2008-05-21
why doesn't it just work when you install it from the "add/remove programs" list?

---

### Post by altonbr on 2008-05-21
> **hodenkat said:**
> why doesn't it just work when you install it from the "add/remove programs" list?

VMware Server isn't supported by Ubuntu so its not in the Add/Remove Programs list.

---

### Post by war59312 on 2008-05-24
How do I get VMWare server mui started? After I rebooted it no longer is running.

---

### Post by Kokopelli on 2008-05-30
VMWare Server 1.0.6 is out and does not appear to require the any-any patch. 

 Unfortunately for Hardy guests where you want to run VMWare tools you still have to patch the tools with open-vm-tools which is a bit of a hassle.

---

### Post by gauss on 2008-05-30
> **bodhi.zazen said:**
> 
**_ Enable USB devices_**
- USB devices work out of the box with minimal (gui) configuration.
- Enable USB device sharing : Using any editor (gksu gedit /etc/fstab), add this line to /etc/fstab (works with VirtualBox as well) :twisted:

```
# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```Reboot and re-start VMWare Server.

- With your guest turned off : In the server window click "Edit virtual machine settings" -> Click "Add" in the lower left -> Select usb controller -> click finish.

Start your guest ...

- With your guest turned on : In the VMWare menu , at the top select "VM" -> Removable devices -> USB devices -> Select the USB device to share with your guest.
I did this but in the VMWare menu there is no device to select. When I check the Device Manager in the guest WinXP the USB controller is listed, however. But inserting a USB flash drive doesn't register with the guest WinXP. It *does* appear in the host's /proc/bus/usb/devices.

Any ideas on how to debug this?

Thanks.

---

### Post by raydar on 2008-05-30
I tried it, and it installed okay unlike before version 1.0.6, but I get error messages and a nonstart when I run vmware.  I don't have the any-any patch installed.

It reports that it's looking for GCC_3.4 and GCC 4.2.0.  I installed gcc-3.4 (& gcc-3.4-base), but that didn't fix the GCC_3.4 error messages; and I found gcc-4.2 & gcc-4.2-base already installed, so I installed gcc-4.2-multilib, but that didn't fix the GCC_4.2.0 error messages:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

I also couldn't find any gcc package in Synaptic that had a version of specifically 4.2.0, as opposed to just 4.2 or 4.2.3. 

You encounter anything like that, Kokopelli?

---

### Post by Kokopelli on 2008-05-31
> **raydar said:**
> I tried it, and it installed okay unlike before version 1.0.6, but I get error messages and a nonstart when I run vmware.  I don't have the any-any patch installed.

It reports that it's looking for GCC_3.4 and GCC 4.2.0.  I installed gcc-3.4 (& gcc-3.4-base), but that didn't fix the GCC_3.4 error messages; and I found gcc-4.2 & gcc-4.2-base already installed, so I installed gcc-4.2-multilib, but that didn't fix the GCC_4.2.0 error messages:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)

...

I also couldn't find any gcc package in Synaptic that had a version of specifically 4.2.0, as opposed to just 4.2 or 4.2.3. 

You encounter anything like that, Kokopelli?

Yes, you need to adjust some links in the install
```

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```

some people copy the files in question but I prefer to link so that updates will get reflected in VMWare and there is only one instance of each file.

---

### Post by pemur1 on 2008-05-31
I did this last week after upgrading to 8.04 and everything worked fine. Now, I can't get VMWare to run at all. Do I have to keep following these directions every time I want to use VMWare?

---

### Post by Kokopelli on 2008-05-31
> **pemur1 said:**
>  Do I have to keep following these directions every time I want to use VMWare?


No, however whenever the kernel is updated you will have to rerun vmware-config.pl

```

sudo vmware-config.pl

```

Generally the default options will keep the configuration the same as it is was before.

---

### Post by pemur1 on 2008-05-31
> **Kokopelli said:**
> No, however whenever the kernel is updated you will have to rerun vmware-config.pl

```

sudo vmware-config.pl

```

Generally the default options will keep the configuration the same as it is was before.

That did the trick. Thank you so much.

---

### Post by raydar on 2008-05-31
Thanks, Kokopelli--that did the trick. I can confirm no need for the any-any patch in Hardy with vmware server 1.0.6.

(I had one stumble on the way, & thought I'd mention it in case it's important, as well as embarrassing: Just before I found your reply, I found a procedure that included copying those files. I tried that, and vmware worked. But what you say about links is a good idea, so I did a rm -R on both copies in /usr/lib/vmware/lib, using -R because they were folders.  I then realized the link targets are just files, and I'd deleted more than I should've. So I created folders with the appropriate names & then created the links. Vmware server runs, but I'm left wondering what else was in those folders before I deleted them, & whether I'll eventually need it.)

---

### Post by Kokopelli on 2008-05-31
raydar:

The only thing in the folders are the corresponding .so files.  Not sure why VMWare does it that way but regardless you did not lose anything.

---

### Post by sunbird on 2008-05-31
I'm wondering whether anyone has gotten vmware player running in 8.04x64? I've tried running the regular install, just vm-install.pl followed by vm-config.pl using all default options and it won't start. I also tried the any-any-116 patch, but it looks like it's for server/workstation, not player:

```

vmware-any-any-update116$ sudo ./runme.pl 
Updating /usr/bin/vmware ... failed
Cannot open /usr/bin/vmware: No such file or directory
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

```

The modules all compile with the statement: "The module loads perfectly in the running kernel," but bridged networking on /dev/vmnet0 fails to load upon conclusion of the config.

Any thoughts? I'd rather use the player version since it's free and you can make vm files on qemu. I'm a bit desperate because there's a piece of software I have to run on XP and I don't want to triple-boot. Any help greatly appreciated.

---

### Post by CloudFX on 2008-05-31
Excellent!  It worked flawlessly :)

---

### Post by sunbird on 2008-06-01
**Bump.** Any help or suggestions?

---

### Post by ozzon on 2008-06-01
I have tried to put this together and run into a problem I don't see any reports of... 
```
root@uniqs:/home/ozz# /usr/bin/vmware-config.pl
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
and if I restart the server then I can run config but it sends me back to 
```
root@uniqs:/home/ozz# /etc/init.d/vmware start
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
```

Thanks,

Ozz.

---

### Post by mistakenidentity on 2008-06-01
How should I go about updating VMware Server 1.0.5 to 1.0.6? Any help would be greatly appreciated.

Edit: Well, I just basically installed VMware Server 1.0.6 like I was doing a fresh install, and when I booted up VMware Server it came up as 1.0.6 when I went to "Help" then "About", so I'm assuming things went well.

---

### Post by mooseydoom on 2008-06-03
Thanks.  I had to recompile my wireless madwifi driver (for a Toshiba Atheros wireless card) before the bridged connection to my wireless card would work.  Otherwise vmware wouldn't start, complaining that it wasn't configured properly.  I followed these instructions: [http://ubuntuforums.org/showpost.php?p=1679885&postcount=2](http://ubuntuforums.org/showpost.php?p=1679885&postcount=2) using this madwifi package [http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz) (link is out of date in the other post)

---

### Post by ShutterAce on 2008-06-05
My config keeps failing when trying to create vmmon. It thinks it already exists. I have ran the uninstall script and reinstalled with the same result. I have no idea what to do here. Below is the output. Thanks!

[INDENT][I]Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-18-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
cc1plus: warning: command line option "-Werror-implicit-function-declaration" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
In file included from /tmp/vmware-config1/vmmon-only/common/task.c:1194:
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV321]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV3]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageGSX1]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV2]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM_V4(VMDriver*, Vcpuid) [with VMCrossPage = VMCrossPageV4]’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMDriver*, Vcpuid)’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config1/vmmon-only/common/task_compat.h: In function ‘void Task_Switch_V45(VMDriver*, Vcpuid)’:
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config1/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
The module loads perfectly in the running kernel.

mknod: `/dev/vmmon': File exists
Unable to create the character device /dev/vmmon with major number 10 and minor
number 165.

Execution aborted.
[/I][/INDENT]

---

### Post by ShutterAce on 2008-06-05
I just ran config again and it worked. Thanks Anyway!

---

### Post by kenmiles on 2008-06-05
The latest version of VMware server now installs normally.
Regards, Kenneth.

---

### Post by siongz on 2008-06-06
hi.. i've got a problem when running ur commands.. everythin worked fine up till the serial number part.. den errors popped up.
this is what i got in the terminal near the end..

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Bridged networking on /dev/vmnet2                                   done

The configuration of VMware Server 1.0.5 build-80187 for Linux for this running
kernel completed successfully.

 -- Fixing library issues, continuing...
ln: creating symbolic link `/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0': No such file or directory
 -- Adding USB support to /etc/fstab, continuing...
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
 -- Safely exiting...
 -- Removing downloaded and extracted files, continuing...

any idea?? please help.. thx

---

### Post by luke16 on 2008-06-09
with the latest vmware (1.06 i think), and x_64 hardy, I get this when trying to run vmware config.

```
$ sudo vmware-config.pl 
[sudo] password for luke: 
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

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-18-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.24-18-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config4/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:48:
/tmp/vmware-config4/vmmon-only/./include/vm_basic_types.h:159: error: redefinition of typedef &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:49:
/tmp/vmware-config4/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config4/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:49:
/tmp/vmware-config4/vmmon-only/./include/compat_wait.h:60: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:65: error: previous declaration of &#8216;poll_initwait&#8217; was here
/tmp/vmware-config4/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config4/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config4/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/vmware-config4/vmmon-only/linux/driver.c:1659: error: &#8216;struct mm_struct&#8217; has no member named &#8216;dumpable&#8217;
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


```

Any suggestions?

---

### Post by gtdaqua on 2008-06-09
VMWare Server 1.0.6 DOES NOT solve the problem. You STILL NEED the vmware-any-any update. I can confirm this on my dozen Dell Hardy 8.04 64-bit servers. I am not sure if you need vmware-any-any update on 32-bit servers, but you definitely need them for 64-bit Hardys.

You will get this error when compiling:
```

Unable to build the vmmon module.

```

And you have to run the "runme.pl" in the vmware-any-any package.

Also, you need to do this to get VMware-mui (Mangement User Interface) working in Hardy Server:

```

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```

This sticky post is misleading. Someone pl correct it.

---

### Post by gtdaqua on 2008-06-09
VMware tools does not work either on the Linux VM. You have to do this to get your vmxnet modules working under your Linux VMs.

Note: The following is taken from: 
[How to Install VMware Tools on Ubuntu Hardy 8.04 under VMware Fusion]("http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html")

```

sudo apt-get install build-essential libproc-dev libdumbnet-dev xorg-dev libgtk2.0-dev

wget http://mesh.dl.sourceforge.net/sourceforge/open-vm-tools/open-vm-tools-2008.04.14-87182.tar.gz


```

WARNING: Ignore "xorg-dev" and "libgtk2.0-dev" in line 1 incase of a Linux VM server. 

Extract the contents of VMware-tools and the open-vm-tools package.

```

tar xzvf VMware*.gz
tar xzvf open-vm-tools*.gz

```

Now build the open-vm tools:
```

cd open-vm-tools-2008.04.14-87182/
./configure && make
cd modules/linux/

```

In the modules/linux folder we have the vmblock, vmhgfs, vmmemctl, vmsync and vmxnet modules that we need to tar up and place into the official VMware tools tarball:

```

for i in *; do mv ${i} ${i}-only; tar -cf ${i}.tar ${i}-only; done
cd ../../..

mv -f open-vm-tools-2008.04.14-87182/modules/linux/*.tar vmware-tools-distrib/lib/modules/source/

```

Now run the regular VMware tools installer:

```

cd vmware-tools-distrib/
sudo ./vmware-install.pl

```

It will correctly compile and install. Modules will load perfectly into the  kernel. Restart to check if everything is ok.

---

### Post by kenmiles on 2008-06-09
> **gtdaqua said:**
> VMWare Server 1.0.6 DOES NOT solve the problem. You STILL NEED the vmware-any-any update. I can confirm this on my dozen Dell Hardy 8.04 64-bit servers. I am not sure if you need vmware-any-any update on 32-bit servers, but you definitely need them for 64-bit Hardys.

You will get this error when compiling:
```

Unable to build the vmmon module.

```

And you have to run the "runme.pl" in the vmware-any-any package.

Also, you need to do this to get VMware-mui (Mangement User Interface) working in Hardy Server:

```

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```

This sticky post is misleading. Someone pl correct it.

Sorry about that, it is the 32 bit version I am running and it does work in that.
Regards, Kenneth.

---

### Post by nhcotrim on 2008-06-09
This how to worked fine and my virtual machines are running - only had to update the vmware tools - unistall the old one, restart Windows and install the new one. Everything smooth.
But now there are no icons - no CD, USB, power up, restart, etc...
I am using 8.04 64 (quad with 2gb RAM) and VMWare 1.0.6 without the any-any patch. I also tried it with the patch but the result is the same.
When I run $ vmware -L I get the following messages:

Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/console.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/upgrade-hw.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/pvn.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-off.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vmlist-on.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vmlist-suspend.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vmlist-not.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-new.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-settings.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-add.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-remove.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/team-off.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/team-on.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/team-suspend.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/team-broken.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/team-new.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/team-settings.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-clone.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-clone-on.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-clone-suspended.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-clone-broken.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-clone-settings.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-legacy-off.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-legacy-on.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-legacy-suspend.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-legacy-broken.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/disabled.png'

(vmware:8266): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/progress.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vmtools-16.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vmtools-32.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vmtools-cancel-16.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vmtools-cancel-32.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/recording-no-led.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/recording.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-cd.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-cpu.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-floppy.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-hd.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-memory.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-mouse.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-nic.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-parallel.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-scsi.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-serial.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-sound.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/dev-usb.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/hardware-video.xpm'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/option-general.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/option-power.xpm'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-checkpoint-enabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/option-startup.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-on-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-on-enabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-on-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-off-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-off-enabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-off-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-suspend-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-suspend-enabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-suspend-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-reset-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-reset-enabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-reset-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-fullscreen-enabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-fullscreen-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-fullscreen-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-maximize-enabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-maximize-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-maximize-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-checkpoint-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-checkpoint-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/snapshot-take-16.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-rollback-enabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-rollback-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-rollback-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-snapshot-mgr-on.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-snapshot-mgr-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-snapshot-mgr-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/snapshot-mgr-16.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-summary-enabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-summary-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-summary-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-console-enabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-console-hot.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/toolbar-console-disabled.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-clone-new-24.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-clone-new-hot-24.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-clone-new-disabled-24.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/vm-clone-new.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/console_banner.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/workstation.png'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/host_device_bw.xpm'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/host_device.xpm'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/client_device_bw.xpm'
Couldn't recognize the image file format for file '/usr/lib/vmware/share/pixmaps/client_device.xpm'


Anyone had the same problems?
I can live with it, but it is very annoying...

---

### Post by Methuselah on 2008-06-11
Thanks, I did all of this before except copying the library files. VMWare didn't start so I just removed it. I wonder how you're supposed to know to copy those files? :confused:

---

### Post by Methuselah on 2008-06-11
Darn, VMWare hangs during operating system installation as well.
Qemu is the only thing that works, amazing!
Now to get kqemu going.

EDIT: After manually restarting the VM, installation continued.

---

### Post by The DON on 2008-06-11
Thanks Heaps! Worked like a dream.

---

### Post by aeg1s on 2008-06-11
Thanks so much!  This got me working again...

---

### Post by se user on 2008-06-12
when i run step 3 i get this error ```
[B]A previous installation of VMware software has been detected.
[/B]
``` but i don't have vm ware installed i ran the installer once and it didn't install please help me

---

### Post by kenmiles on 2008-06-12
> **se user said:**
> when i run step 3 i get this error ```
[B]A previous installation of VMware software has been detected.
[/B]
``` but i don't have vm ware installed i ran the installer once and it didn't install please help me

Either locate vmware and delete all files or run the vmware uninstall script.
Regards, Kenneth.

---

### Post by se user on 2008-06-12
where can i find the uninstall script?

i got it to install sort of i get this error now 

Unable to get the access rights of source file "./vmware-vix/bin".

---

### Post by kenmiles on 2008-06-12
> **se user said:**
> where can i find the uninstall script?

i got it to install sort of i get this error now 

Unable to get the access rights of source file "./vmware-vix/bin".

/usr/bin/vmware-uninstall.pl

---

### Post by se user on 2008-06-12
thanks for all the help i gave ALL the files in the extracted folder read and right privileges (it took long) but it worked so now i only have one question is there any way of me getting my mic to work with vmware (i have a normal mic not a usb one)

---

### Post by kenmiles on 2008-06-12
> **se user said:**
> thanks for all the help i gave ALL the files in the extracted folder read and right privileges (it took long) but it worked so now i only have one question is there any way of me getting my mic to work with vmware (i have a normal mic not a usb one)

I am not sure about a mike but I use various USB ans serial devices without trouble, that is with windows XP as the guest.
I do not know why you had to change the file permissions after install.

---

### Post by b0b138 on 2008-06-13
I can't get mine to run a vm. Followed the directions. The console comes up, connect to local host. Made a vm and drive. But when I go to power it on, the screen (virtual tabbed windowed one, not my physical whole screen) goes black for a few seconds, then back to the console.

I've looked and looked but cant find any mention of this problem.

Anyone seen this or have a clue what its doing? :confused:

---

### Post by b0b138 on 2008-06-13
update...

In a nutshell, I'm duel booting with xp, and my ubuntu partition is small. So on the install, I told it store the vms on my xp ntfs drive. Either on a hunch or something I came across looking for a solution that mentioned problems with mounted ntfs partitions, I made another vm and stored it in my home folder, and sure enough, it booted :guitar:

Now while the drive I made for that (102 MB) is not big enough to install anything, it is booting to a live cd right this second.

Unfortunately, I have absolutely NO idea why its not liking my ntfs drive or how to fix it

---

### Post by kenmiles on 2008-06-13
> **b0b138 said:**
> update...

In a nutshell, I'm duel booting with xp, and my ubuntu partition is small. So on the install, I told it store the vms on my xp ntfs drive. Either on a hunch or something I came across looking for a solution that mentioned problems with mounted ntfs partitions, I made another vm and stored it in my home folder, and sure enough, it booted :guitar:

Now while the drive I made for that (102 MB) is not big enough to install anything, it is booting to a live cd right this second.

Unfortunately, I have absolutely NO idea why its not liking my ntfs drive or how to fix it

Why not give up on duel booting like I did a couple of years ago, install Ubuntu on the whole drive and then install VM server for XP.

Regards, Kenneth.

---

### Post by sjprice on 2008-06-13
So everything runs fine and dandy for me, but now I can only start Server by ```
sudo vmware
``` and not from the launcher. If I use the icon in Applications > System Tools > VMWare Server Console, it acts like it is starting up, but then goes away.

Any ideas?

---

### Post by kenmiles on 2008-06-14
> **sjprice said:**
> So everything runs fine and dandy for me, but now I can only start Server by ```
sudo vmware
``` and not from the launcher. If I use the icon in Applications > System Tools > VMWare Server Console, it acts like it is starting up, but then goes away.

Any ideas?

permissions are wrong somewhere. You should not have to use sudo. Run vmware by itself from the command line and see what messages you get.

---

### Post by sjprice on 2008-06-14
I had already checked all the permissions I could think of, so I ran it:
sprice@ubuntu:~$ vmware
Unable to alloc client: Cannot open file "/home/sprice/.vmware/preferences": Permission denied.

So I forgot to check the hidden files :) Fixed it and working great. Thanks a ton!

---

### Post by BoyBlunder on 2008-06-14
I get the following errors while trying to install.
Any ideas?

```

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [no] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-18-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-18-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:65: error: previous declaration of &#8216;poll_initwait&#8217; was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: error: &#8216;struct mm_struct&#8217; has no member named &#8216;dumpable&#8217;
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by kenmiles on 2008-06-14
What version of vmware server are you installing?
What version of Ubuntu?

---

### Post by BoyBlunder on 2008-06-14
eh got it working now.

for the record, I'm using hardy with VMWare 1.0.5

now, I popped my windows CD in, and powered up the VM, and it's not working.

my CD settings are set for it to use the Host CD-Rom, and legacy emulation is unchecked.

any insight?

---

### Post by kenmiles on 2008-06-15
> **BoyBlunder said:**
> eh got it working now.

for the record, I'm using hardy with VMWare 1.0.5

now, I popped my windows CD in, and powered up the VM, and it's not working.

my CD settings are set for it to use the Host CD-Rom, and legacy emulation is unchecked.

any insight?

Legacy emulation unchecked, and upgrade to 1.0.6 which means uninstall 1.0.5 first.

---

### Post by dogday on 2008-06-16
```
/tmp/vmware-config0/vmmon-only/common/vmx86.c: En la función ‘Vmx86_GetkHzEstimate’:
/tmp/vmware-config0/vmmon-only/common/vmx86.c:1899: aviso: se pasa el argumento 4 de ‘Div643264’ desde un tipo de puntero incompatible
/tmp/vmware-config0/vmmon-only/common/vmx86.c:1908: aviso: se pasa el argumento 4 de ‘Div643232’ desde un tipo de puntero incompatible
```

After following the proposed steps I get this error. VmWare starts but does not work. I cant configure network settings either.

Any ideas? 

(Ubuntu 8.0.4 kernel= 2.6.24.19 generic VmWare Server Console 1.0.6 build-91891)

Thanks in advance.

---

### Post by blasthand on 2008-06-17
Hi There,

Firstly - thanks for the guide - worked like a charm. Everything went smoothly and I had no problems at all. :)

However, I have just one issue post-install. After I launch the Console from the Applications/System menu I cannot select the option to create a new virtual machine as it is greyed-out. I thought it might be permission related so I tried using gksu from the terminal, but no dice, same problem.

If anyone has any suggestions as to why this is i'd be mighty grateful :)

Many thanks,
Mark.

---

### Post by Fazazi on 2008-06-18
oooooooooooooooyehhhhhhhhhh
i was struggling 4 days to get VMware work on my machine, but now i did it in just 1h :-) now i'm running VM.
thanks alot, i really appreciate what you provide on this post.

---

### Post by bradb-acc on 2008-06-18
Ubuntu 8.04 does _not_ have /usr/lib32/ ...  :confused:

Its ...   /usr/lib/gtk-2.0/ ...

here´s the readout of cat /usr/lib/gtk-2.0/2.10.0/loader-files.d/ etc.. etc...

bradb-acc@joanne-desktop:~$ cat /usr/lib/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders |grep lib
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-ani.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-bmp.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-ico.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-pcx.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-pnm.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-ras.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-tga.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-tiff.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-wbmp.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xbm.so"
"/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so"
bradb-acc@joanne-desktop:~$

---

### Post by Barmaleychik on 2008-06-19
I am very new at Linux and I am trying to install Vmware server. I red and trying to follow instructions in this thread but have problems to understand how file system works.

I was able to download tar package from VmWare.com site and the package end up on my desktop.. 

I was able to create folder ~/src/VMWare

Now I am trying to copy the tar package to this directory using Krusader but I can not find the desktop folder in Krusader.

Please, help :(

---

### Post by gtdaqua on 2008-06-19
> 
Now I am trying to copy the tar package to this directory using Krusader but I can not find the desktop folder in Krusader. 

you cant find which desktop folder??

from command line simply go to:

```

cd ~/src/VMWare
wget http://<<VMware-donwload-link-tar-file

```

That will download the tar file straigt to ~/src/VMware

If you can see tar file on the desktop, why dont you just extract the contents in the desktop??

```

tar xzvf VMware-tar-file.tar.gz

```

---

### Post by Unicyclone on 2008-06-19
I got the following error message when VMtools is trying to compile vmhgfs modules.  Error message is listed below.

I am running VMWare 1.0.6. Host OS is Windows. Guest OS is Ubuntu 8.04

I am following the general FAQ from [https://help.ubuntu.com/community/VMware/Tools]("http://https://help.ubuntu.com/community/VMware/Tools")

Did I do something wrong?

-- Begin: Screen dump --

Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] 


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-generic/build/include] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmhgfs-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config0/vmhgfs-only/cpName.o
In file included from include/linux/string.h:11,
                 from /tmp/vmware-config0/vmhgfs-only/cpName.h:18,
                 from /tmp/vmware-config0/vmhgfs-only/cpName.c:18:
include/linux/types.h:40: error: conflicting types for ‘uintptr_t’
/tmp/vmware-config0/vmhgfs-only/vm_basic_types.h:161: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/tmp/vmware-config0/vmhgfs-only/cpName.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 


-- end: SCreen Dump --

---

### Post by CruiserNut on 2008-06-19
ok...done this to death...it just doesnt work!  ](*,)

VMware Server Console will not connect to my server. (note the "."!)

Ive followed this guide, as well as others, started on this about three weeks ago, using Ubuntu Server 8.04 (server....no X installed) and VMware Server 1.05 (using the any-any patch).  This week I tried a clean rebuild of Ubuntu server and VMware server 1.06...same result.....console will not connect.  Tried a thousand 'fixes' posted on various forums all over the place, even tried turning the server off and giving up.  Im using an XP workstation as the client, tried other xp workstations to rule out client side (windows firehall turned off).  :cry:

I challange anyone to find something i havent tried to get this working! PLEASE! [-o<

I realy want to get this working (it used to work with fiesty).

Error i get on the console is attached:

---

### Post by CruiserNut on 2008-06-19
OK, RE previous, More info:

VMWare server installs, vmware-config.pl runs and compiles as this guide says.... let me know what more info would be usefull and ill post it up...

Telnet to the server with the following result, which is immediate:

[root@test /]# telnet 10.10.2.4 902
Trying 10.10.2.4...
Connected to 10.10.2.4.
Escape character is '^]'.
Connection closed by foreign host.

I check iptables and allowed 902 in, allthough i dont think this was anything to do with the problem.

Thanks

---

### Post by Barmaleychik on 2008-06-20
> **bodhi.zazen said:**
> [CENTER][FONT=Times New Roman][SIZE=6]Install VMWare in Ubuntu 8.04[/SIZE][/FONT][/CENTER]
[FONT=Times New Roman]

[*]Download vmware server (be sure to obtain a serial number) Place in an instalation directory ( I use ~/src/VMWare).

```
mkdir -p ~/src/VMWare #Download VMWare files here
```
[LIST]
[*]VMWare server : [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)
[*]VMWare serial number : [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)
[/LIST]
[*]Extract and uinstall VMWare Server.
```
cd ~/src/VMWare
tar xzf VMware-server-1.0.6-91891.tar.gz

cd ~/src/VMWare/vmware-server-distrib
sudo ./vmware-install.pl
```Select defaults.


[IMG]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/IMG][FONT=times]*[SIZE=4][COLOR=navy][FONT=times]bodhi.[/FONT][/COLOR][FONT=times][COLOR=darkgray]zazen[/COLOR][/FONT][/SIZE]*[/FONT]



I am trying to follow instructions to install VmWare server and I was able to download tar package from VmWare web site. My problem was that it download itself on desktop and not to directory ~usr/src

I was able to find that directory and tried to create subdirectory VmWare but I was told that I do not have permissions to do it.

What should I change recommended in this thread commands to salvage the installations. 

And I an just curious: why can not I create a directory Vmware and why can not I copy files to directory  ~usr/src?

Thank you in advance!

---

### Post by bodhi.zazen on 2008-06-20
The command :

```
mkdir -p ~/src/VMWare
``` makes a directory in :

/home/user_name/src/VMWare

~ == your home directory.

move the tar you downloaded from your Desktop to ~/src/VMWare

```
mv ~/Desktop/VMWare* ~/src/VMWare
```

cd into ~/src/VMWare and continue ... (tar .... )

---

### Post by Barmaleychik on 2008-06-20
Thank you guys, I finally installed VmWare Server. Then I copied a virtual machine which was created in a Windows VmWare Workstation to a folder on the desktop in Ubuntu and then tried to open this Virtual Machine in VmWare console. Unfortunately I got the message:

Unable to add virtual machine "/home/vasily/Documents/VmWare Virtyal Machine/Clone of Etalon SP2 and Office Babylon/Windows XP Professional.vmx" to the inventory: No permission to perform this operation


What this can be?

---

### Post by bodhi.zazen on 2008-06-20
You need to set the permissions of the copied disk.

[uhelp]/community/FilePermissions[/uhelp]

---

### Post by pemur1 on 2008-06-20
Disregard. Problem solved.

I installed VMWare without any problems. However, when I try to install WinXP, I get a message stating the following:

No bootable CD, floppy or hard disk was detected.
To install an operating system, insert a bootable CD or floppy and restart the virtual machine by clicking the Reset button.

I have the disk in the CD drive, but I still can't get it to work.

---

### Post by SteB on 2008-06-21
For me, the final piece of the puzzle...

When running VMWare the Console window would never come up.
When I started the services there was nothing VMware related when I typed 'ps aux' -- even though it said the services had started OK.

If I tried to manually invoke:
/usr/bin/vmware  

...I was getting problems regarding missing GCC_4.2.0

Solution from ([http://radio.javaranch.com/davo/replyToComment.action?entry=1213791596327&comment=1213816062756](http://radio.javaranch.com/davo/replyToComment.action?entry=1213791596327&comment=1213816062756))

was to delete a file:
cd /usr/lib/vmware/lib
rm mv libgcc_s.so.1/libgcc_s.so.1


Now my VMware is working - hurrah!

Stephen

---

### Post by ShutterAce on 2008-06-21
> **SteB said:**
> For me, the final piece of the puzzle...

When running VMWare the Console window would never come up.
When I started the services there was nothing VMware related when I typed 'ps aux' -- even though it said the services had started OK.

If I tried to manually invoke:
/usr/bin/vmware  

...I was getting problems regarding missing GCC_4.2.0

Solution from ([http://radio.javaranch.com/davo/replyToComment.action?entry=1213791596327&comment=1213816062756](http://radio.javaranch.com/davo/replyToComment.action?entry=1213791596327&comment=1213816062756))

was to delete a file:
cd /usr/lib/vmware/lib
rm mv libgcc_s.so.1/libgcc_s.so.1


Now my VMware is working - hurrah!

Stephen

Same here. Thank You!!!:guitar:

---

### Post by Barmaleychik on 2008-06-21
in a previous post i asked;


> **Barmaleychik said:**
> Thank you guys, I finally installed VmWare Server. Then I copied a virtual machine which was created in a Windows VmWare Workstation to a folder on the desktop in Ubuntu and then tried to open this Virtual Machine in VmWare console. Unfortunately I got the message:

Unable to add virtual machine "/home/vasily/Documents/VmWare Virtyal Machine/Clone of Etalon SP2 and Office Babylon/Windows XP Professional.vmx" to the inventory: No permission to perform this operation


What this can be?

i got a good reply with a suggestion to set permissions. i believe it is a good idea, however i do not understand whom should i give permission and how can i do it as well i am concern about security since i red that if i do something wrong i can destroy security of my system. any help will be appreciated

---

### Post by sbeattie on 2008-06-24
One other note for using VMWare Server, make sure you don't have any of the other virtualization kernel modules loaded; attempts to boot VMWare guest images while also having the kvm kernel module loaded caused my hardy host kernel to lock up hard, requiring a reboot. 

(If you try to run the VMWare Server 2 betas while having kvm loaded, the vmware kernel modules will at least spit out a message to syslog about why they failed to run.)

---

### Post by genecaldwell on 2008-06-24
There are currently 16 pages (as of june 24th ) of comments, suggestions, cautions and corrections. Since I read all 16 pages I'm a bit nervous about upgrading to VMWare Server 1.0.6 since I have currently a working 1.0.5. Things about breaking the loader if a command was not needed ( something about SED, this worries me)....I am just not skilled enough to have any clue how to unbreak it. My question is this: Has the tutorial been updated to reflect all the corrections needed ? I run Hardy AMD64bit, it runs great, I'd be kinda upset if I broke it, but I like to run the latest versions of software and thats why I am contemplating the update.

I prefer to wait till VMWare is availible thru Synaptic in the repro, but its now nearly july and 8.04 came out in april, I got tired of waiting.....when is vmware going to start to be supported in ubuntu again ? in the past it took a month, but geezzz, this waiting with no word when we will see vmware in synaptic is frustrating.

---

### Post by bodhi.zazen on 2008-06-24
> **genecaldwell said:**
> There are currently 16 pages (as of june 24th ) of comments, suggestions, cautions and corrections. Since I read all 16 pages I'm a bit nervous about upgrading to VMWare Server 1.0.6 since I have currently a working 1.0.5. Things about breaking the loader if a command was not needed ( something about SED, this worries me)....I am just not skilled enough to have any clue how to unbreak it. My question is this: Has the tutorial been updated to reflect all the corrections needed ? I run Hardy AMD64bit, it runs great, I'd be kinda upset if I broke it, but I like to run the latest versions of software and thats why I am contemplating the update.

I prefer to wait till VMWare is availible thru Synaptic in the repro, but its now nearly july and 8.04 came out in april, I got tired of waiting.....when is vmware going to start to be supported in ubuntu again ? in the past it took a month, but geezzz, this waiting with no word when we will see vmware in synaptic is frustrating.

If you refer back to my first post ...

Yes this guide is up to date.

I have both upgraded vmware and performed several fresh installs using this guide, but as you can see there are no guarantees. It works for most people most of the time.

With your background, I would say if it is not broken don't fix it. You cant have your cake and eat it too. If you want to run the newest, latest, greatest you should be prepared to do some problem solving. If you are running a mission critical server you should not be playing with it :lolflag:

---

### Post by genecaldwell on 2008-06-24
> **bodhi.zazen said:**
> If you refer back to my first post ...

Yes this guide is up to date.

I have both upgraded vmware and performed several fresh installs using this guide, but as you can see there are no guarantees. It works for most people most of the time.

With your background, I would say if it is not broken don't fix it. You cant have your cake and eat it too. If you want to run the newest, latest, greatest you should be prepared to do some problem solving. If you are running a mission critical server you should not be playing with it :lolflag:

humm, maybe I came across differently than I thought I was. lol, I used your previous tutorial and it installed perfectly Thank you for that awesome how-to! My intent with my question was to try to determine what the risks were using the how-to as it is currently. Now that I know for certain that it has been updated to be as trouble free as is known at this point, I think it is a reasonable risk. As I said, I would hate it if "**I**" broke it by upgrading, but I would in no way think that it was not my own fault or responsibility. Keep up the good work ! I also appreciate your efforts !

Can you comment on when the repro's will deliver vmware ? have you heard anything ? is there some post somewhere that talks about whats taking so long to get VMWare in the partner's repro ?

---

### Post by bodhi.zazen on 2008-06-24
> **genecaldwell said:**
> humm, maybe I came across differently than I thought I was. lol, I used your previous tutorial and it installed perfectly Thank you for that awesome how-to! My intent with my question was to try to determine what the risks were using the how-to as it is currently. Now that I know for certain that it has been updated to be as trouble free as is known at this point, I think it is a reasonable risk. As I said, I would hate it if "**I**" broke it by upgrading, but I would in no way think that it was not my own fault or responsibility. Keep up the good work ! I also appreciate your efforts !

Can you comment on when the repro's will deliver vmware ? have you heard anything ? is there some post somewhere that talks about whats taking so long to get VMWare in the partner's repro ?

LOL, my mistake then. Sorry if I came across too harsh myself, my intention was to caution you about upgrading in a production environment.

From personal experience VMWare has been quite stable and versatile. Personally, I have performed 2 upgrades (and several "fresh installs") without any problem.

VMWare has not been in the repos for a while, and I suspect it had to do with technical issues with the kernel (and needing to use the any-any-update, which is not supported by either Ubuntu or VMWare).

Now that 1.06 is working we can hope it will again find it's way into the repos, although I have not heard anything official.

---

### Post by murphyb on 2008-06-25
Is it required to uninstall the old VMware Server when performing an upgrade?  If you do, does it keep all the same settings or will I have to config everything all over again?

also, for the post-install config, step 4.  can you just symbolic link it or does that not work for some reason?

Thank you.  You're post is very helpful.

---

### Post by bodhi.zazen on 2008-06-25
> **murphyb said:**
> Is it required to uninstall the old VMware Server when performing an upgrade?  If you do, does it keep all the same settings or will I have to config everything all over again?

No, you can just install the new. Works this way with each new update of VMWare.

> also, for the post-install config, step 4.  can you just symbolic link it or does that not work for some reason?

/me looks ....

You could likely symlink that if you wish (I have not tried, but it looks like it would work).

> Thank you.  You're post is very helpful.

You are most welcome :)

Although I "maintain" this thread, it is a community effort and I can not take all the credit.

+1 Ubuntu community.

---

### Post by gerula on 2008-06-26
Thanks a lot bodhi.zazen! It worked smoothly.

You wrote:

>>>**_File Sharing_**
- Samba is by far the easiest way to file share. It works out of the box with minimal end user configuration. See this page : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)<<<

However, I found a very nice and clear tutorial which you might want to consider. It was written by Russ Hall and posted at:

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

Even if the Ubuntu Feisty was used as reference it works for Ubuntu 8.04 too. I am running Hardy's 64 bit version.

fjgaude and Kokopelli, I thank you too for the 64 bit stuff!

Cheers!

---

### Post by dmsimms on 2008-06-27
I followed the instructions from the sticky; Hardy 8.04 64-bit, VMWare 1.06. It runs as sudo but if I without sudo I get this error:

 /usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7054767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf70548b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7ed31bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7dc3969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7dc3f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c09180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c09d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bd9c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7be624f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bd9c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7be5b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aea298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aea586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aec77e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7cff459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7ce73a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7ce7076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cfe6eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7cfdd46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7cfe0b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7054767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf705481e]
#2 /usr/lib32/libX11.so.6 [0xf7ed2518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7eb5c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7dbbed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7dba8b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7dbad39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7dbaec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c079b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c09d75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bd9c14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7be624f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bd9c14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7be5b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aea298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aea586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aec77e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7cff459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7ce73a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7ce7076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

---

### Post by devnulljp on 2008-06-27
> **kenmiles said:**
> permissions are wrong somewhere. You should not have to use sudo. Run vmware by itself from the command line and see what messages you get.

having a similar problem. I've been using vmware 5.x workstation on Kubuntu feisty, but I just upgraded to Hardy and installed vmware 6.04. I can run it as root, but get permissions errors if I try to run as a regular joe.
What files need to be changed and to what?

regular@joe:~$vmware
bash: /usr/bin/vmware: Permission denied

sudo vmware works fine.

---

### Post by student eternal on 2008-07-01
First off let me add my thanks to the chorus to all you gurus that help out with this,  thanks! :biggrin:

Now though, I have encountered a bit of a problem, I folowed the directions verbatium, however when I try to launch VMware through Applications\system tools\VMware server console I get a window on the taskbar that says it is loading, but nothing ever pops up and after a few seconds the window goes away.

When I try to run it from the command line as with our with out sudo I get:
"/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
"

This is after running the config program a couple of times.  Also oddly it did not ask for a serial at any point during installation.  I am running hardy and trying to install VMware 1.0.6  Any help would be appreciated.

Thank you:

---

### Post by fnjordy on 2008-07-02
> **devnulljp said:**
> 
regular@joe:~$vmware
bash: /usr/bin/vmware: Permission denied


I get this:
```

The configuration of VMware Server 1.0.6 build-91891 for Linux for this running
kernel completed successfully.

steve-o@aiko:/tmp/moo/vmware-server-distrib$ vmware
/bin/sh: Can't open /usr/bin/vmware
steve-o@aiko:/tmp/moo/vmware-server-distrib$ ls -ltr /usr/bin/vmware
-r-x--x--x 1 root root 4570 2008-07-02 18:59 /usr/bin/vmware
```

Then a library error with libcrypto:
```

steve-o@aiko:~$ sudo vmware-cmd "/srv/vmware/Virtual Machines/Trade Link/win98.vmx" getstate
/usr/bin/vmware-cmd: Could not connect to VM /srv/vmware/Virtual Machines/Trade Link/win98.vmx
  (VMControl error -14: Unexpected response from vmware-authd: The process exited with an error:
SSLLoadSharedLibrary: Failed to load library /usr/lib/vmware/bin/libcrypto.so.0.9.7:/usr/lib/vmware/bin/libcrypto.so.0.9.7: cannot open shared object file: No such file or directory


VMware Server Error:
VMware Server unrecoverable error: (vmx)
SSLLoadSharedLibrary: Failed to load library /usr/lib/vmware/bin/libcrypto.so.0.9.7:/usr/lib/vmware/bin/libcrypto.so.0.9.7: cannot open shared object file: No such file or directory
Please request support.  
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.

Press "Enter" to continue...
End of error message)

```

---

### Post by dmsimms on 2008-07-02
I got it working! Found this link:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=486507](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=486507)

Apparently at some point I had set the LD_LIBRARY_PATH environment variable (it was pointing to /usr/lib32). I cleared that (set it to nothing) and now VMWare starts up without having to use sudo!

> **dmsimms said:**
> I followed the instructions from the sticky; Hardy 8.04 64-bit, VMWare 1.06. It runs as sudo but if I without sudo I get this error:

 /usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7054767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf70548b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7ed31bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7dc3969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7dc3f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c09180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c09d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bd9c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7be624f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bd9c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7be5b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aea298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aea586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aec77e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7cff459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7ce73a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7ce7076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cfe6eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7cfdd46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7cfe0b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7054767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf705481e]
#2 /usr/lib32/libX11.so.6 [0xf7ed2518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7eb5c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7dbbed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7dba8b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7dbad39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7dbaec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c079b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c09d75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bd9c14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7be624f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bd9c14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7be5b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aea298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aea586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aec77e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7cff459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7ce73a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7ce7076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

---

### Post by fnjordy on 2008-07-02
[QUOTE=fnjordy;5304294]I get this:
```

The configuration of VMware Server 1.0.6 build-91891 for Linux for this running
kernel completed successfully.

steve-o@aiko:/tmp/moo/vmware-server-distrib$ vmware
/bin/sh: Can't open /usr/bin/vmware
steve-o@aiko:/tmp/moo/vmware-server-distrib$ ls -ltr /usr/bin/vmware
-r-x--x--x 1 root root 4570 2008-07-02 18:59 /usr/bin/vmware
```

:KS Found the problem, please update the OP as it is wrong.  The VMware Server tarball **must be extracted as superuser,**, possibly umask 0022 will work too :KS

Regular user has no group/all read permissions, as per my umask 0066:
```

steve-o@aiko:/tmp/moo$ ls -ltr vmware-server-distrib/bin/
total 2016
-r-x--x--x 1 steve-o miru  99602 2008-05-10 12:26 vmware-uninstall.pl
-r-x--x--x 1 steve-o miru   8172 2008-05-10 12:26 vmnet-sniffer
-r-x--x--x 1 steve-o miru   5192 2008-05-10 12:26 vmnet-netifup
-r-x--x--x 1 steve-o miru   6160 2008-05-10 12:26 vmnet-bridge
-r-x--x--x 1 steve-o miru 490464 2008-05-10 12:26 vmware-loop
-r-x--x--x 1 steve-o miru 110872 2008-05-10 12:26 vmnet-dhcpd
-r-x--x--x 1 steve-o miru   4570 2008-05-10 12:26 vmware
-r-x--x--x 1 steve-o miru 718200 2008-05-10 12:26 vmware-vdiskmanager
-r-x--x--x 1 steve-o miru  10852 2008-05-10 12:26 vmware-ping
-r-x--x--x 1 steve-o miru  25488 2008-05-10 12:26 vmware-mount.pl
-r-x--x--x 1 steve-o miru 290800 2008-05-10 12:26 vmware-config.pl
-r-x--x--x 1 steve-o miru  23333 2008-05-10 12:26 vmware-cmd
-rwx--x--x 1 steve-o miru   4946 2008-05-10 12:26 vmrun
-r-x--x--x 1 steve-o miru 119076 2008-05-10 12:26 vmnet-natd
-r-x--x--x 1 steve-o miru  73092 2008-05-10 12:26 vmware-authtrusted
-r-x--x--x 1 steve-o miru  11456 2008-05-10 12:26 vm-support
```

Super-user has correct permissions:
```

-r-xr-xr-x 1 root root  99602 2008-05-10 12:26 vmware-uninstall.pl
-r-xr-xr-x 1 root root   8172 2008-05-10 12:26 vmnet-sniffer
-r-xr-xr-x 1 root root   5192 2008-05-10 12:26 vmnet-netifup
-r-xr-xr-x 1 root root   6160 2008-05-10 12:26 vmnet-bridge
-r-xr-xr-x 1 root root 490464 2008-05-10 12:26 vmware-loop
-r-xr-xr-x 1 root root 110872 2008-05-10 12:26 vmnet-dhcpd
-r-xr-xr-x 1 root root   4570 2008-05-10 12:26 vmware
-r-xr-xr-x 1 root root 718200 2008-05-10 12:26 vmware-vdiskmanager
-r-xr-xr-x 1 root root  10852 2008-05-10 12:26 vmware-ping
-r-xr-xr-x 1 root root  25488 2008-05-10 12:26 vmware-mount.pl
-r-xr-xr-x 1 root root 290800 2008-05-10 12:26 vmware-config.pl
-r-xr-xr-x 1 root root  23333 2008-05-10 12:26 vmware-cmd
-rwxr-xr-x 1 root root   4946 2008-05-10 12:26 vmrun
-r-xr-xr-x 1 root root 119076 2008-05-10 12:26 vmnet-natd
-r-xr-xr-x 1 root root  73092 2008-05-10 12:26 vmware-authtrusted
-r-xr-xr-x 1 root root  11456 2008-05-10 12:26 vm-support
```

The installer incorrectly just copies all the files without explicitly setting the permissions.

---

### Post by bodhi.zazen on 2008-07-02
> **fnjordy said:**
> :KS Found the problem, please update the OP as it is wrong.  The VMware Server tarball **must be extracted as superuser,**, possibly umask 0022 will work too :KS

Regular user has no group/all read permissions, as per my umask 0066:
```

steve-o@aiko:/tmp/moo$ ls -ltr vmware-server-distrib/bin/
total 2016
-r-x--x--x 1 steve-o miru  99602 2008-05-10 12:26 vmware-uninstall.pl
-r-x--x--x 1 steve-o miru   8172 2008-05-10 12:26 vmnet-sniffer
-r-x--x--x 1 steve-o miru   5192 2008-05-10 12:26 vmnet-netifup
-r-x--x--x 1 steve-o miru   6160 2008-05-10 12:26 vmnet-bridge
-r-x--x--x 1 steve-o miru 490464 2008-05-10 12:26 vmware-loop
-r-x--x--x 1 steve-o miru 110872 2008-05-10 12:26 vmnet-dhcpd
-r-x--x--x 1 steve-o miru   4570 2008-05-10 12:26 vmware
-r-x--x--x 1 steve-o miru 718200 2008-05-10 12:26 vmware-vdiskmanager
-r-x--x--x 1 steve-o miru  10852 2008-05-10 12:26 vmware-ping
-r-x--x--x 1 steve-o miru  25488 2008-05-10 12:26 vmware-mount.pl
-r-x--x--x 1 steve-o miru 290800 2008-05-10 12:26 vmware-config.pl
-r-x--x--x 1 steve-o miru  23333 2008-05-10 12:26 vmware-cmd
-rwx--x--x 1 steve-o miru   4946 2008-05-10 12:26 vmrun
-r-x--x--x 1 steve-o miru 119076 2008-05-10 12:26 vmnet-natd
-r-x--x--x 1 steve-o miru  73092 2008-05-10 12:26 vmware-authtrusted
-r-x--x--x 1 steve-o miru  11456 2008-05-10 12:26 vm-support
```

Super-user has correct permissions:
```

-r-xr-xr-x 1 root root  99602 2008-05-10 12:26 vmware-uninstall.pl
-r-xr-xr-x 1 root root   8172 2008-05-10 12:26 vmnet-sniffer
-r-xr-xr-x 1 root root   5192 2008-05-10 12:26 vmnet-netifup
-r-xr-xr-x 1 root root   6160 2008-05-10 12:26 vmnet-bridge
-r-xr-xr-x 1 root root 490464 2008-05-10 12:26 vmware-loop
-r-xr-xr-x 1 root root 110872 2008-05-10 12:26 vmnet-dhcpd
-r-xr-xr-x 1 root root   4570 2008-05-10 12:26 vmware
-r-xr-xr-x 1 root root 718200 2008-05-10 12:26 vmware-vdiskmanager
-r-xr-xr-x 1 root root  10852 2008-05-10 12:26 vmware-ping
-r-xr-xr-x 1 root root  25488 2008-05-10 12:26 vmware-mount.pl
-r-xr-xr-x 1 root root 290800 2008-05-10 12:26 vmware-config.pl
-r-xr-xr-x 1 root root  23333 2008-05-10 12:26 vmware-cmd
-rwxr-xr-x 1 root root   4946 2008-05-10 12:26 vmrun
-r-xr-xr-x 1 root root 119076 2008-05-10 12:26 vmnet-natd
-r-xr-xr-x 1 root root  73092 2008-05-10 12:26 vmware-authtrusted
-r-xr-xr-x 1 root root  11456 2008-05-10 12:26 vm-support
```

The installer incorrectly just copies all the files without explicitly setting the permissions.

I did not have this problem.

> user@hostname:vmware-server-distrib/bin$ ls -lA
total 2016
-r-xr-xr-x 1 user user   6160 2008-06-07 22:57 vmnet-bridge
-r-xr-xr-x 1 user user 110872 2008-06-07 22:57 vmnet-dhcpd
-r-xr-xr-x 1 user user 119076 2008-06-07 22:57 vmnet-natd
-r-xr-xr-x 1 user user   5192 2008-06-07 22:57 vmnet-netifup
-r-xr-xr-x 1 user user   8172 2008-06-07 22:57 vmnet-sniffer
-rwxr-xr-x 1 user user   4946 2008-06-07 22:57 vmrun
-r-xr-xr-x 1 user user  11456 2008-06-07 22:57 vm-support
-r-xr-xr-x 1 user user   4570 2008-06-07 22:57 vmware
-r-xr-xr-x 1 user user  73092 2008-06-07 22:57 vmware-authtrusted
-r-xr-xr-x 1 user user  23333 2008-06-07 22:57 vmware-cmd
-r-xr-xr-x 1 user user 290800 2008-06-07 22:57 vmware-config.pl
-r-xr-xr-x 1 user user 490464 2008-06-07 22:57 vmware-loop
-r-xr-xr-x 1 user user  25488 2008-06-07 22:57 vmware-mount.pl
-r-xr-xr-x 1 user user  10852 2008-06-07 22:57 vmware-ping
-r-xr-xr-x 1 user user  99602 2008-06-07 22:57 vmware-uninstall.pl
-r-xr-xr-x 1 user user 718200 2008-06-07 22:57 vmware-vdiskmanager

---

### Post by Apex-jb on 2008-07-03
Is there any way to enable sound in vmware server? I have been searching but have come up empty handed so far.

---

### Post by kenmiles on 2008-07-04
> **Apex-jb said:**
> Is there any way to enable sound in vmware server? I have been searching but have come up empty handed so far.

In VM-Settings, Hardware tab, Add, Sound Adapter

Regards, Kenneth.

---

### Post by orrorin on 2008-07-06
Now that VMWare Server 2.0 RC1 is out, has anyone tried it with Hardy-64?

---

### Post by varun990 on 2008-07-06
I am getting the following error when I run the vmware-install.pl script.
[I]
A previous installation of VMware software has been detected.

Failure

Execution aborted.
[/I]
I never installed vmware before, when I search synaptics for vmware this came up as installed "xorg-xserver-video-vmware".

I am running Ubuntu 8.04 on Dell E1505.

---

### Post by ixus_123 on 2008-07-06
> **orrorin said:**
> Now that VMWare Server 2.0 RC1 is out, has anyone tried it with Hardy-64?

I've just installed it.  Got the web interface up okay, and copied over 2 virtual machines I made on my Mac with VMware Fusion.

They started with a few errors but vmware2 was able to fix them.

The only problem I have is that I can't acces them. This is my first time using vmware server and it has a console tab (which I guess you can use to administer the virtual machine). When I access this it gives a popup window to download a firefox plugin.

```
Please install the VMware Remote Console Plug-in to access this virtual machine's console.
```

However, I get an error message when I try to install this

---

### Post by haz2a on 2008-07-08
For installing VMware Server 1.0.6 on Ubuntu 8.04LTS LTSP Server, do not install xinetd at step 1 - it replaces openbsd-inetd, breaking LTSP.
VMware Server 1.0.6 installs fine with openbsd-inetd and I have not encountered any problems running it. My host 64-bit.

Thanks for a great howto.

---

### Post by neuman1812 on 2008-07-08
Hey Im hoping someone can help here.  
I recently installed Hardy from the CD and I cant get VMware to work.

After the install of the OS.  I made sure to install all updates that it was requesting. 216! and then rebooted.  Then I wanted to install VMware.  On 7.10 I was able to find it in Synaptic..but I guess in 8.04 its not available.  So I Dl'ed Vmware from the site and ran

sudo ./Vmware-install.pl

It ran fine until this point 
```

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

 Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:48:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config2/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

anyone have an Idea how to fix it?

---

### Post by calibre97 on 2008-07-11
I can't get networking going in the guest OS.
Here's what I did:
Booted into XP.
Ran VMWare's Converter and created a VM of XP on an external USB drive formatted NTFS (only thing that had room at the time).
Booted into Rescue CD and Gparted the laptop disk:
-blew away openSUSE partition (I needed the ext3 room!)
-grew the partition and formatted ext3.
Then I rebooted into Kubuntu:
-mounted /dev/hda6 as /mnt/VAULT
-chmod 777 /mnt/VAULT (didn't want permissions issues)
-copied Converter's files to VAULT
-installed VMWare Server
-opened the XP VM files
-registered XP again with a nice call to India
-Added maxWidth and maxHeight lines to VMX file
-enjoyed my XP VM in full screen mode
until...
I just cannot get networking to happen. I reran vmware-config.pl and I am bridging to wlan0 like I want. I tried bridging, NATing, setting the IP address, everything. With some attempts I can see in XP that I am sending AND receiving packets, but Firefox is no go. I even tried a direct IP address for Yahoo and it timed out.

What can I possibly be missing? It's completely set up and no errors during VMWare Server install and guest OS boot and run.

Host: Kubuntu 8.04 with 2.6.24-18 (Yes, I followed the instructions and used the proper kernel items)
Guest: XP MCE SP2 that was the first partition on the laptop (still is but I'm hoping to not ever have to boot into it again).

What else should I post that might help someone help me? If I wasn't even receiving packets, I'd figure I was just missing something obvious but this just has me stumped. I even tried going direct LAN line to the router and that didn't work either (naturally since I am bridged to wlan0 as I said but I had to try it to rule it out).

Almost forgot:
Yes I installed VMWare tools from the VM menu. Twice even, though natch the second time didn't do anything. I just thought I was supposed to see that grayed out if they were installed.

---

### Post by bodhi.zazen on 2008-07-11
> **haz2a said:**
> For installing VMware Server 1.0.6 on Ubuntu 8.04LTS LTSP Server, do not install xinetd at step 1 - it replaces openbsd-inetd, breaking LTSP.
VMware Server 1.0.6 installs fine with openbsd-inetd and I have not encountered any problems running it. My host 64-bit.

Thanks for a great howto.

Just curious what you are basing this information on ?

I ask because I am re-working this how to as there have been a lot of developments ....

I just installed VMWare Server 1.0.6 on a fresh install of Ubuntu 8.04.1 (64 bit).

First openbsd-initd is not installed by default.

Second, I installed openbsd-initd and it did not work. I removed openbsd-initd and instead installed xinetd and VMWare then installed.

What exactly is the problem with xinetd ? How did you get openbsd-inetd working and why is this "better" then xinetd ?

Thanks in advance :)

---

### Post by calibre97 on 2008-07-11
Turns out the problem was ZoneAlarm Pro. Shut it down and internet connection works fine (I'm updating Divx as I type). Anyone have any issues with using MS's firewall? I don't feel comfortable running 'naked' so to speak. I think I should be running SOMEthing. Oh well, the beauty of being virtual is I can try it out and if it FUBAR's I can always revert back to snapshot.

---

### Post by descendency on 2008-07-13
> **calibre97 said:**
> Turns out the problem was ZoneAlarm Pro. Shut it down and internet connection works fine (I'm updating Divx as I type). Anyone have any issues with using MS's firewall? I don't feel comfortable running 'naked' so to speak. I think I should be running SOMEthing. Oh well, the beauty of being virtual is I can try it out and if it FUBAR's I can always revert back to snapshot.

[http://technology.timesonline.co.uk/tol/news/tech_and_web/article4304820.ece](http://technology.timesonline.co.uk/tol/news/tech_and_web/article4304820.ece)

Uninstall that "update" and your Zone Alarm will work fine again.

---

### Post by OttifantSir on 2008-07-13
I always want to have a copy of HOWTOs on my system should I need it again one time and find myself without netaccess at that time. To facilitate this, I have made a PDF of the first post. Anyone else interested in it, here's a link to the file (too large to attach): [HOWTO_VMWare_Server.pdf]("http://www.megaupload.com/?d=MF9U2ZZN")

---

### Post by nycste on 2008-07-19
Hello everyone, im new to linux and ubuntu. I tried following the guide and well even though im pretty good at windows just peoples assumptions on understanding things and way things are worded in linux are very different.

Anyways onto the point.

step 3
mkdir -p ~/src/VMWare #Download VMWare files here

this makes no sense to me, but i was able to finally figure it out, but again just sharding my advice either describe in more detail what this means possibly or leave it be just saying its confusing for beginners

also the command wouldnt work, tried sudo as well and nothing

finally i got around to running
sudo ./vmware-install.pl

i didnt fully install vmware, and tried installing it again at a later time and got this error
```
sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.


```

i then deleted the vmware folder and files i could find on linux other then the install tar.gz file

i then just uncompressed it on desktop, doubleclicked the 
vmware-install.pl

and got the same error message, so im just asking for Help

summary

1. please consider updating your guide section 3 thanks

2. help me uninstall full vmware from my system minus the install file tar.gz on desktop

3. then install vmware server, which i can prob do once i finish step 2 properly, thanks


EDIT....

just wanted to say that i found one extra folder searching through things in the /etc folder, i deleted that and then tried to reinstall vmware server and it worked

billion clicks later like wow lol and it just finished and im happy
```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Server 1.0.6 build-91891 for Linux for this running
kernel completed successfully.

```

now i assume i have to 

STEP 5
Post-install configuration. Last, before running vmware :
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0

then all should be golden right

---

### Post by bodhi.zazen on 2008-07-19
sweet, not bad for a new user :)

---

### Post by nycste on 2008-07-19
> **bodhi.zazen said:**
> sweet, not bad for a new user :)

yup everything is working now i just havent set a VM up yet

---

### Post by ezramorris on 2008-07-21
Hi, when I try to run vmware, I get this error:
```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```

Any ideas? Thanks.

---

### Post by bodhi.zazen on 2008-07-21
> **ezramorris said:**
> Hi, when I try to run vmware, I get this error:
```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```Any ideas? Thanks.

See the first post on this thread, vmware server 1.0.6, step 5

---

### Post by ezramorris on 2008-07-21
> **bodhi.zazen said:**
> See the first post on this thread, vmware server 1.0.6, step 5

How did I miss that?
I must have read right over it; I did see the 64 bit afterwards, and ignored that.
](*,)

Thanks, anyway. It works.

---

### Post by silentbob1978 on 2008-07-22
I get the following error using vmware 2.0 beta when I try and launch it using the command line vmware or sudo vmware

Failed to launch VMware Web Access: unable to find a graphical web browser.


any ideas??

---

### Post by bodhi.zazen on 2008-07-22
> **silentbob1978 said:**
> I get the following error using vmware 2.0 beta when I try and launch it using the command line vmware or sudo vmware

Failed to launch VMware Web Access: unable to find a graphical web browser.


any ideas??

Are you running X ?

---

### Post by unabatedshagie on 2008-07-24
I'm struggling to get this working.

I have followed the instruction but when I enter vmware into the console to start the web interface a new tab opens and the tab title just stays as **Loading...**

I have accepted the certificate but the page just wont load.

If I go to [https://127.0.0.1/ui](https://127.0.0.1/ui) the page title just says loading
If I go to [http://127.0.0.1/ui](http://127.0.0.1/ui) the page title says VMWare Infrastructure Web Access

Both of the pages are a kind of creamy white colour and blank.

I tried a new firefox profile just incase it was any of my extensions but still no joy.

Any ideas?

---

### Post by bodhi.zazen on 2008-07-24
> **unabatedshagie said:**
> I'm struggling to get this working.

I have followed the instruction but when I enter vmware into the console to start the web interface a new tab opens and the tab title just stays as **Loading...**

I have accepted the certificate but the page just wont load.

If I go to [https://127.0.0.1/ui](https://127.0.0.1/ui) the page title just says loading
If I go to [http://127.0.0.1/ui](http://127.0.0.1/ui) the page title says VMWare Infrastructure Web Access

Both of the pages are a kind of creamy white colour and blank.

I tried a new firefox profile just incase it was any of my extensions but still no joy.

Any ideas?

Yes, as I said Server 2.0 RC1 is a little flaky ...

Try : [http://localhost](http://localhost)

---

### Post by unabatedshagie on 2008-07-25
Nope exactly the same.

---

### Post by ruipedroca on 2008-07-27
Hi,

I've just made a fresh install of ubuntu 64 and updated all the packages before installing vmware server 1.0.6 (latest).
Them, I followed the instructions on this post and thus was able to successful install the vmware server.

My problem is I'm not able to access the internet in the guests nor even ping them.


Any ideas?..

---

### Post by bodhi.zazen on 2008-07-28
> **ruipedroca said:**
> Hi,

I've just made a fresh install of ubuntu 64 and updated all the packages before installing vmware server 1.0.6 (latest).
Them, I followed the instructions on this post and thus was able to successful install the vmware server.

My problem is I'm not able to access the internet in the guests nor even ping them.


Any ideas?..

Hard to tell from the information you posted. There are several options here ...

On the host, are you using a wireless card ?

On the guest what type of options? Are you using NAT, Bridged, host only ?

---

### Post by Micro-soft_WIn_Dos_SuCkS on 2008-07-28
So Which is better to use to have an Windows Exe running fine on Ubuntu?

Wine(1.0.0.1)

Win4Lin(3.5,5)

VMware(1.06, 2.0)

Virtual Box (1.6.2) <I used this back when I used Windows Xp and I install Ubuntu 7.04 (Faisty Fawn) as a virtual OS) Now I think I will use it to install Winxp on Ubuntu 8.04 using Virtual Box, really easy tough>

VirtualPC (unknown) 

Which one?  Is better? 

Which one is easiest to install? 

Which one is Ubuntu-Desktop Reliable? 
(Opens there on the Ubuntu Desktop and not in a virtual Desktop)

So anyone would like to answer this?

---

### Post by RealG187 on 2008-07-30
How do I start it?

When I press Alt+F2 and type vmware it does nothing or when I type vmware-serverd

---

### Post by bodhi.zazen on 2008-07-31
> **RealG187 said:**
> How do I start it?

When I press Alt+F2 and type vmware it does nothing or when I type vmware-serverd

Should be in your menu .... "VMWare Server Console"

If not, open a terminal and enter :

```
vmware
```

post any error messages

---

### Post by RealG187 on 2008-07-31
It said to configure by typing this command, I did but it does not seem to configure

> 
mpg@MIKED5:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

mpg@MIKED5:~$ 
mpg@MIKED5:~$ 
mpg@MIKED5:~$ /usr/bin/vmware-config.pl
Please re-run this program as the super user.

Execution aborted.

mpg@MIKED5:~$ sudo /usr/bin/vmware-config.pl
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
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
/tmp/vmware-config0/vmmon-only/common/vmx86.c: In function &#8216;Vmx86_GetkHzEstimate&#8217;:
/tmp/vmware-config0/vmmon-only/common/vmx86.c:1899: warning: passing argument 4 of &#8216;Div643264&#8217; from incompatible pointer type
/tmp/vmware-config0/vmmon-only/common/vmx86.c:1908: warning: passing argument 4 of &#8216;Div643232&#8217; from incompatible pointer type
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
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
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

Unable to find any instance of the super-server "inetd" or "xinetd".  It is 
possible that you do not have one of these packages installed on this machine. 
Please install "inetd" or "xinetd".

If you do have "inetd" or "xinetd" installed, make sure that /etc/inetd.conf or
/etc/xinetd.d exists.
The configuration will continue, but you should re-run 
/usr/bin/vmware-config.pl after you fix the super-server.

Hit enter to continue. 

mpg@MIKED5:~$ 
mpg@MIKED5:~$ 


---

### Post by bodhi.zazen on 2008-08-01
Look at the first post in this thread, step 1 ;)

---

### Post by alillowr on 2008-08-01
Does anyone have the sound working on a guest machine?  I installed a audio device in vmware but in my guest machine it says under control panel and sounds, No audio device

I am running hardy 8.04 host and win xp guest

---

### Post by Mononofu on 2008-08-01
I have qiute a problem with the new web interface:
with FF 3 the console doesn't open a new window (after installing the plugin with the dev plugin) and with FF 2 I can't even install the plugin. I always get error -203.

I'm using Ubuntu 8.04 and VMWare installed fine.

Any ideas or hints?

The error:
Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 4034

Edit: nevermind, fixed the problem with the help of [this post]("http://ubuntuforums.org/showpost.php?p=4706531&postcount=12").
It was just a conflict between FF2 and FF3

---

### Post by bodhi.zazen on 2008-08-01
Server 2.0 RC1 needs a little love ...

The web interface is flaky, and the quality is more like an alpha then a RC. Support for 64 bit and multiple processors is lagging as well.

At this time I consider server 2.0 RC1 a novelty, a glimpse of the next generation, but certainly not for "production".

---

### Post by kenmiles on 2008-08-02
> **bodhi.zazen said:**
> Server 2.0 RC1 needs a little love ...

The web interface is flaky, and the quality is more like an alpha then a RC. Support for 64 bit and multiple processors is lagging as well.

At this time I consider server 2.0 RC1 a novelty, a glimpse of the next generation, but certainly not for "production".

Certainly not a novelty!
On my 32 bit box running Ubuntu 8.04 I have no trouble at all with firefox or the web interface. Having said that I always start my virtual machine via the desktop shortcut which bypasses the web interface.
Also in Version 2 I find that if I forget to switch my usb printer on when starting my VM it will still find it in the VM when I do switch on which never happened with version 1.
I use it to run XP pro mainly for OS mapping and GPS in google earth.
Regards, Kenneth.

---

### Post by bodhi.zazen on 2008-08-02
Nice to hear, glad it turned out well for you of course. Still, I am not sure RC1 is for everyone ;)

---

### Post by EmyrB on 2008-08-03
Hi All

I am using 64bit 8.04.1 and I have just installed VMWare Server 1.06 build 91891 and I am having quite a tough time with it.

Basically I had issues with running my VM on a NTFS based partition, but I got around that by adding mainMem.useNamedFile=FALSE to the .vmx file.

I am trying to install intrepid aplha 3 and when it gets to the point of detecting the hard drive it bombs.

This is what is in the vmware.log (sorry, big file)

Aug 03 12:31:28: vmx| Log for VMware Server pid=8869 version=1.0.6 build=build-91891 option=BETA
Aug 03 12:31:28: vmx| Command line: "/usr/lib/vmware/bin-debug/vmware-vmx" "-C" "-@" """" "/home/emyr/Downloads/VMWare/Ubuntu/Ubuntu.vmx"
Aug 03 12:31:28: vmx| vmxvmdb: Index name being generated from config file
Aug 03 12:31:28: vmx| VMXVmdbConnectServerd - Trying to discover serverd
Aug 03 12:31:28: vmx| AllocTrack: Successfully initialized, pass-through mode, log level 0, log stack crawl FALSE.
Aug 03 12:31:28: vmx| AllocTrack: Options changed globally, now log level 1, log stack crawl FALSE.
Aug 03 12:31:28: vmx| MStat: Creating Stat system.cpuusage
Aug 03 12:31:28: vmx| MStat: Creating Stat system.ram
Aug 03 12:31:28: vmx| MStat: Creating Stat system.uptime
Aug 03 12:31:28: vmx| MStat: Creating Stat system.load
Aug 03 12:31:28: vmx| cpuids[0].id81.ecx = 0x11f
Aug 03 12:31:28: vmx| cpuids[1].id81.ecx = 0x11f
Aug 03 12:31:28: vmx| pcpu #0 CPUID numEntries=1 AuthcAMDenti
Aug 03 12:31:28: vmx| pcpu #0 CPUID version=0x60fb2 id1.edx=0x178bfbff id1.ecx=0x2001 id1.ebx=0x20800
Aug 03 12:31:28: vmx| pcpu #0 CPUID id80.eax=80000018 id81.edx=0xebd3fbff id81.ecx=0x11f
Aug 03 12:31:28: vmx| pcpu #1 CPUID numEntries=1 AuthcAMDenti
Aug 03 12:31:28: vmx| pcpu #1 CPUID version=0x60fb2 id1.edx=0x178bfbff id1.ecx=0x2001 id1.ebx=0x1020800
Aug 03 12:31:28: vmx| pcpu #1 CPUID id80.eax=80000018 id81.edx=0xebd3fbff id81.ecx=0x11f
Aug 03 12:31:28: vmx| CPUID id1.edx: 0x178bfbff id1.ecx: 0x2001 id81.edx: 0xebd3fbff id81.ecx: 0x11f
Aug 03 12:31:28: vmx| CPUID id88.ecx: 0 id88.edx: 0
Aug 03 12:31:28: vmx| Removing stale symlink /var/run/vmware/%2Fhome%2Femyr%2FDownloads%2FVMWare%2FUbuntu%2FUbuntu%2Evmx
Aug 03 12:31:28: vmx| Setup symlink /var/run/vmware/%2Fhome%2Femyr%2FDownloads%2FVMWare%2FUbuntu%2FUbuntu%2Evmx -> /var/run/vmware/emyr/8869
Aug 03 12:31:28: vmx| ACL_InitCapabilities: here 1 (bug 63252)
Aug 03 12:31:28: vmx| changing directory to /home/emyr/Downloads/VMWare/Ubuntu/.
Aug 03 12:31:28: vmx| Config file: /home/emyr/Downloads/VMWare/Ubuntu/Ubuntu.vmx
Aug 03 12:31:28: vmx| CnxAcceptConnection: Could not receive fd on 27: invalid control message
Aug 03 12:31:28: vmx| Failed to get IPC connection
Aug 03 12:31:28: vmx| Read from FIFO 32 -- connecting to serverd...
Aug 03 12:31:29: vmx| VMDB: Connected to serverd
Aug 03 12:31:29: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
Aug 03 12:31:29: vmx| PowerOn
Aug 03 12:31:29: vmx| Host ACPI: can't find SRAT
Aug 03 12:31:29: vmx| Msg_Hint: msg.loader.debug.release (not shown)
Aug 03 12:31:29: vmx| HOST sysname Linux, nodename linux-downstairs, release 2.6.24-19-generic, version #1 SMP Fri Jul 11 21:01:46 UTC 2008, machine x86_64, SMP, hz=250
Aug 03 12:31:29: vmx| DICT --- USER PREFERENCES
Aug 03 12:31:29: vmx| DICT --- USER DEFAULTS
Aug 03 12:31:29: vmx| DICT --- HOST DEFAULTS
Aug 03 12:31:29: vmx| DICT    vmnet1.hostonlyaddress = 192.168.92.1
Aug 03 12:31:29: vmx| DICT     serverd.init.fullpath = /usr/lib/vmware/serverd/init.pl
Aug 03 12:31:29: vmx| DICT         authd.client.port = 902
Aug 03 12:31:29: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Aug 03 12:31:29: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Aug 03 12:31:29: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Aug 03 12:31:29: vmx| DICT                    libdir = /usr/lib/vmware
Aug 03 12:31:29: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Aug 03 12:31:29: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Aug 03 12:31:29: vmx| DICT                     vmdir = /var/lib/vmware/Virtual Machines
Aug 03 12:31:29: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Aug 03 12:31:29: vmx| DICT          serverd.fullpath = /usr/sbin/vmware-serverd
Aug 03 12:31:29: vmx| DICT            datastore.name = local
Aug 03 12:31:29: vmx| DICT       datastore.localpath = /var/lib/vmware/Virtual Machines/
Aug 03 12:31:29: vmx| DICT --- SITE DEFAULTS
Aug 03 12:31:29: vmx| DICT                  tag.help = introduction.htm
Aug 03 12:31:29: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Aug 03 12:31:29: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Aug 03 12:31:29: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Aug 03 12:31:29: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Aug 03 12:31:29: vmx| DICT             tag.netConfig = devices_netadapter.htm
Aug 03 12:31:29: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Aug 03 12:31:29: vmx| DICT          tag.serialConfig = devices_serial.htm
Aug 03 12:31:29: vmx| DICT           tag.soundConfig = devices_sound.htm
Aug 03 12:31:29: vmx| DICT             tag.memConfig = configvm_memory.htm
Aug 03 12:31:29: vmx| DICT            tag.miscConfig = configvm.htm
Aug 03 12:31:29: vmx| DICT             tag.usbConfig = devices_usb.htm
Aug 03 12:31:29: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Aug 03 12:31:29: vmx| DICT                 tag.tools = vmtools.htm
Aug 03 12:31:29: vmx| DICT --- COMMAND LINE
Aug 03 12:31:29: vmx| DICT          gui.managementUI = TRUE
Aug 03 12:31:29: vmx| DICT --- CONFIGURATION
Aug 03 12:31:29: vmx| DICT      mainMem.useNamedFile = FALSE
Aug 03 12:31:29: vmx| DICT            config.version = 8
Aug 03 12:31:29: vmx| DICT         virtualHW.version = 4
Aug 03 12:31:29: vmx| DICT             scsi0.present = TRUE
Aug 03 12:31:29: vmx| DICT          scsi0.virtualDev = lsilogic
Aug 03 12:31:29: vmx| DICT                   memsize = 1024
Aug 03 12:31:29: vmx| DICT           scsi0:0.present = TRUE
Aug 03 12:31:29: vmx| DICT          scsi0:0.fileName = Ubuntu.vmdk
Aug 03 12:31:29: vmx| DICT      scsi0:0.writeThrough = TRUE
Aug 03 12:31:29: vmx| DICT            ide1:0.present = TRUE
Aug 03 12:31:29: vmx| DICT           ide1:0.fileName = /media/sdb5/intrepid-alternate-i386.iso
Aug 03 12:31:29: vmx| DICT         ide1:0.deviceType = cdrom-image
Aug 03 12:31:29: vmx| DICT          floppy0.fileName = /dev/fd0
Aug 03 12:31:29: vmx| DICT         Ethernet0.present = TRUE
Aug 03 12:31:29: vmx| DICT               displayName = Ubuntu
Aug 03 12:31:29: vmx| DICT                   guestOS = ubuntu
Aug 03 12:31:29: vmx| DICT          priority.grabbed = normal
Aug 03 12:31:29: vmx| DICT        priority.ungrabbed = normal
Aug 03 12:31:29: vmx| DICT        powerType.powerOff = hard
Aug 03 12:31:29: vmx| DICT         powerType.powerOn = hard
Aug 03 12:31:29: vmx| DICT         powerType.suspend = hard
Aug 03 12:31:29: vmx| DICT           powerType.reset = hard
Aug 03 12:31:29: vmx| DICT              scsi0:0.redo = 
Aug 03 12:31:29: vmx| DICT     ethernet0.addressType = generated
Aug 03 12:31:29: vmx| DICT             uuid.location = 56 4d 47 da 67 47 4f 28-08 bd d7 9d 92 57 2d b1
Aug 03 12:31:29: vmx| DICT                 uuid.bios = 56 4d 47 da 67 47 4f 28-08 bd d7 9d 92 57 2d b1
Aug 03 12:31:29: vmx| DICT ethernet0.generatedAddress = 00:0c:29:57:2d:b1
Aug 03 12:31:29: vmx| DICT ethernet0.generatedAddressOffset = 0
Aug 03 12:31:29: vmx| DICT                     debug = TRUE
Aug 03 12:31:29: vmx| DICT --- USER DEFAULTS
Aug 03 12:31:29: vmx| DICT --- HOST DEFAULTS
Aug 03 12:31:29: vmx| DICT    vmnet1.hostonlyaddress = 192.168.92.1
Aug 03 12:31:29: vmx| DICT     serverd.init.fullpath = /usr/lib/vmware/serverd/init.pl
Aug 03 12:31:29: vmx| DICT         authd.client.port = 902
Aug 03 12:31:29: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Aug 03 12:31:29: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Aug 03 12:31:29: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Aug 03 12:31:29: vmx| DICT                    libdir = /usr/lib/vmware
Aug 03 12:31:29: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Aug 03 12:31:29: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Aug 03 12:31:29: vmx| DICT                     vmdir = /var/lib/vmware/Virtual Machines
Aug 03 12:31:29: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Aug 03 12:31:29: vmx| DICT          serverd.fullpath = /usr/sbin/vmware-serverd
Aug 03 12:31:29: vmx| DICT            datastore.name = local
Aug 03 12:31:29: vmx| DICT       datastore.localpath = /var/lib/vmware/Virtual Machines/
Aug 03 12:31:29: vmx| DICT --- SITE DEFAULTS
Aug 03 12:31:29: vmx| DICT                  tag.help = introduction.htm
Aug 03 12:31:29: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Aug 03 12:31:29: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Aug 03 12:31:29: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Aug 03 12:31:29: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Aug 03 12:31:29: vmx| DICT             tag.netConfig = devices_netadapter.htm
Aug 03 12:31:29: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Aug 03 12:31:29: vmx| DICT          tag.serialConfig = devices_serial.htm
Aug 03 12:31:29: vmx| DICT           tag.soundConfig = devices_sound.htm
Aug 03 12:31:29: vmx| DICT             tag.memConfig = configvm_memory.htm
Aug 03 12:31:29: vmx| DICT            tag.miscConfig = configvm.htm
Aug 03 12:31:29: vmx| DICT             tag.usbConfig = devices_usb.htm
Aug 03 12:31:29: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Aug 03 12:31:29: vmx| DICT                 tag.tools = vmtools.htm
Aug 03 12:31:29: vmx| DICT --- GLOBAL SETTINGS
Aug 03 12:31:29: vmx| WSSCAN: reserved mem (in MB) min=32 max=1920 recommended=1920
Aug 03 12:31:29: vmx|         hostMem=2016 maxAllowedAll=-1 maxAllowedVM=3600
Aug 03 12:31:29: vmx|         totOverhead=16
Aug 03 12:31:29: vmx| WSSCAN: used rec mem (in MB) 1920
Aug 03 12:31:29: vmx| WSSCAN: Overhead 268529 paged 7072 nonpaged 4096 maxFBSize
Aug 03 12:31:29: vmx| WSSCAN 1 1 491520 -1 491520 -1 50 0
Aug 03 12:31:29: vmx| MX: init lock: rank(monAct)=65535
Aug 03 12:31:29: vmx| MX: init lock: rank(monAct)=65535
Aug 03 12:31:29: vmx| MX: init lock: rank(monAct)=65535
Aug 03 12:31:29: vmx| MX: init lock: rank(monAct)=65535
Aug 03 12:31:29: vmx| MX: init lock: rank(monAct)=65535
Aug 03 12:31:29: vmx| MX: init lock: rank(monAct)=65535
Aug 03 12:31:29: vmx| MX: init lock: rank(monAct)=65535
Aug 03 12:31:29: vmx| MX: init lock: rank(monAct)=65535
Aug 03 12:31:29: vmx| MX: init lock: rank(stTable)=99
Aug 03 12:31:29: vmx| MX: init lock: rank(log)=0
Aug 03 12:31:29: vmx| LICENSE using: '/etc/vmware/license.vs.1.0-00' 
Aug 03 12:31:29: vmx| STATDECLGROUP stats Root "" null
Aug 03 12:31:29: vmx| MX: init lock: rank(iospaceLock)=120
Aug 03 12:31:29: vmx| Host CPUID features: version 0x60fb2 id1.edx 0x178bfbff id1.ecx 0x2001 id81.edx 0xebd3fbff id81.ecx 0x11f
Aug 03 12:31:29: vmx| CPU.cpuFeatures = 0xd83dfff8
Aug 03 12:31:29: vmx| CPUID after masking: version 0x60fb2 id1.edx 0x78bfbff id1.ecx 0x2001 id81.edx 0xebd3fbff id81.ecx 0x109 id88.ecx 0x0
Aug 03 12:31:29: vmx| CPU.cpuFeatures = 0xd83dfff8
Aug 03 12:31:29: vmx| APIC: Local APIC at 0xfee00000
Aug 03 12:31:29: vmx| KHZEstimate 2500000
Aug 03 12:31:29: vmx| MHZEstimate 2500
Aug 03 12:31:29: vmx| NumVCPUs 1
Aug 03 12:31:29: vmx| MX: init lock: rank(monitorPoll)=65534
Aug 03 12:31:29: vmx| MX: init lock: rank(userlevelLock)=100
Aug 03 12:31:29: vmx| MX: init lock: rank(bigDeviceLock)=110
Aug 03 12:31:29: vmx| UUID: location-UUID is 56 4d 47 da 67 47 4f 28-08 bd d7 9d 92 57 2d b1
Aug 03 12:31:29: vmx| MM: Using partialmap, 262144 pages AC 1 CE 1 TM 1 DOHU 0
Aug 03 12:31:29: vmx| MX: init condvar: MMCpt
Aug 03 12:31:29: vmx| MX: init lock: rank(MMCpt)=65533
Aug 03 12:31:29: vmx| Msg_Reset:
Aug 03 12:31:29: vmx| ----------------------------------------
Aug 03 12:31:29: vmx| Opened paging file anon
Aug 03 12:31:29: vmx| Mapped mainmem as pageable
Aug 03 12:31:29: vmx| MStat: Creating Stat vm.cpuusage
Aug 03 12:31:29: vmx| MStat: Creating Stat vm.ram
Aug 03 12:31:29: vmx| MStat: Creating Stat vm.uptime
Aug 03 12:31:29: vmx| MX: init lock: rank(intrLock)=65532
Aug 03 12:31:29: vmx| DISK: OPEN scsi0:0 '/home/emyr/Downloads/VMWare/Ubuntu/Ubuntu.vmdk' persistent R[(null)]
Aug 03 12:31:29: vmx| FILEIO: Found a previous instance of lock file '/home/emyr/Downloads/VMWare/Ubuntu/Ubuntu.vmdk.WRITELOCK'. It will be removed automatically.
Aug 03 12:31:29: vmx| MX: init lock: rank(IOGGlobalLock)=65535
Aug 03 12:31:29: vmx| MX: init condvar: IOGPendingOps
Aug 03 12:31:29: vmx| AIOGNRC: Starting 6 I/O threads.
Aug 03 12:31:29: vmx| DISKLIB-DSCPTR: Opened [0]: "Ubuntu-f001.vmdk" 0 (0x2a)
Aug 03 12:31:29: vmx| DISKLIB-DSCPTR: Opened [1]: "Ubuntu-f002.vmdk" 0 (0x2a)
Aug 03 12:31:29: vmx| DISKLIB-DSCPTR: Opened [2]: "Ubuntu-f003.vmdk" 0 (0x2a)
Aug 03 12:31:29: vmx| DISKLIB-DSCPTR: Opened [3]: "Ubuntu-f004.vmdk" 0 (0x2a)
Aug 03 12:31:29: vmx| DISKLIB-DSCPTR: Opened [4]: "Ubuntu-f005.vmdk" 0 (0x2a)
Aug 03 12:31:29: vmx| DISKLIB-DSCPTR: Opened [5]: "Ubuntu-f006.vmdk" 0 (0x2a)
Aug 03 12:31:29: vmx| DISKLIB-LINK  : Opened '/home/emyr/Downloads/VMWare/Ubuntu/Ubuntu.vmdk' (0x2a): twoGbMaxExtentFlat, 20971520 sectors / 10240 Mb.
Aug 03 12:31:29: vmx| DISKLIB-LIB   : Opened "/home/emyr/Downloads/VMWare/Ubuntu/Ubuntu.vmdk" (flags 0x2a).
Aug 03 12:31:29: vmx| DISK: OPEN '/home/emyr/Downloads/VMWare/Ubuntu/Ubuntu.vmdk' Geo (1305/255/63) BIOS Geo (0/0/0) freeSpace=16103Mb
Aug 03 12:31:29: vmx| MX: init lock: rank(timeTracker)=65533
Aug 03 12:31:29: vmx| TimeTracker host to guest rate conversion 4934820761936 @ 2500000000Hz -> 4934820761936 @ 2500000000Hz
Aug 03 12:31:29: vmx| TimeTracker host to guest rate conversion ((x * 2147483648) >> 31) + 0
Aug 03 12:31:29: vmx| DISK: DELAY: vide.vtdelay=0 hard-disk.minVirtualTime=0 magicBoot1=0
Aug 03 12:31:29: vmx| MX: init lock: rank(VIDELock)=111
Aug 03 12:31:29: vmx| MStat: Creating Stat ide1:0.bytesread
Aug 03 12:31:29: vmx| MStat: Creating Stat ide1:0.byteswritten
Aug 03 12:31:29: vmx| MX: init lock: rank(LSI_LCK_0)=60
Aug 03 12:31:29: vmx| MStat: Creating Stat scsi0:0.bytesread
Aug 03 12:31:29: vmx| MStat: Creating Stat scsi0:0.byteswritten
Aug 03 12:31:29: vmx| DISKUTIL: scsi0:0 : capacity=20971520
Aug 03 12:31:29: vmx| DISKUTIL: scsi0:0 : geometry=1305/255/63
Aug 03 12:31:29: vmx| SCSI0: UNTAGGED commands will be converted to ORDER tags.
Aug 03 12:31:29: vmx| MX: init lock: rank(timer)=30
Aug 03 12:31:29: vmx| MStat: Creating Stat vm.heartbeat
Aug 03 12:31:29: vmx| DISKUTIL: scsi0:0 : toolsVersion = 0
Aug 03 12:31:29: vmx| DISKUTIL: Offline toolsVersion = 0
Aug 03 12:31:29: vmx| TOOLS INSTALL initializing state to IDLE on power on.
Aug 03 12:31:29: vmx| MX: init lock: rank(mksLock)=130
Aug 03 12:31:29: vmx| XINFO no-auth XOpenDisplay failed.  Trying auth info from UI (0).
Aug 03 12:31:29: vmx| MX: init lock: rank(vgaLock)=60
Aug 03 12:31:29: vmx| MX: init lock: rank(svgaLock)=30
Aug 03 12:31:29: vmx| MX: init condvar: svgaStopCondition
Aug 03 12:31:29: vmx| MX: init lock: rank(svgaPseudoCallLock)=101
Aug 03 12:31:29: vmx| MX: init condvar: svgaPseudoCallCondVar
Aug 03 12:31:29: vmx| VMMon_GetkHzEstimate: Calculated 1521305 kHz
Aug 03 12:31:29: vmx| VLANCE: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks
Aug 03 12:31:29: vmx| MX: init lock: rank(vlanceLock)=30
Aug 03 12:31:29: vmx| MStat: Creating Stat ethernet0.bytesread
Aug 03 12:31:29: vmx| MStat: Creating Stat ethernet0.byteswritten
Aug 03 12:31:29: vmx| Ethernet0 MAC Address: 00:0c:29:57:2d:b1
Aug 03 12:31:29: vmx| VMXNET: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks, dontClusterSize is 128
Aug 03 12:31:29: vmx| E1000: checksum cycles/kB: C=906 asm=292
Aug 03 12:31:29: vmx| MX: init lock: rank(TestAutomationGlobalLock)=65535
Aug 03 12:31:29: vmx| MX: init lock: rank(pollLock)=65534
Aug 03 12:31:29: vmx| VMX_PowerOn: ModuleTable_PowerOn = 1
Aug 03 12:31:29: vmx| VMX setting maximum IPC write buffers to 0 packets, 0 bytes
Aug 03 12:31:29: mks| Async MKS thread is alive
Aug 03 12:31:29: vcpu-0| MX: init lock: rank(offline)=99
Aug 03 12:31:29: vcpu-0| APIC: version = 0x10, max LVT = 5
Aug 03 12:31:29: vcpu-0| APIC: LDR = 0x2000000, DFR = 0xffffffff
Aug 03 12:31:29: vcpu-0| MX: init lock: rank(stopLock)=1
Aug 03 12:31:29: vcpu-0| MX: init lock: rank(respLock)=3
Aug 03 12:31:29: vcpu-0| MX: init lock: rank(busMemLock)=80
Aug 03 12:31:29: vmx| Accepted new connection at 177 for thread servercontrol (0x853d360)
Aug 03 12:31:29: vmx| VUINewControlConnection: before slow ACL gunk (bug 63252).
Aug 03 12:31:29: vmx| ACL_InitCapabilities: here 2 (bug 63252)
Aug 03 12:31:29: vmx| VUINewControlConnection: after slow ACL gunk (bug 63252).
Aug 03 12:31:29: vmx| VUI: A new VMControl client connected.
Aug 03 12:31:29: vcpu-0| MX: init lock: rank(busmemSample)=99
Aug 03 12:31:29: vcpu-0| MX: init lock: rank(vmkRelMemLock)=99
Aug 03 12:31:29: vcpu-0| PShare: enabled 1, scanRate 4, checkRate 16
Aug 03 12:31:29: vcpu-0| guestCpuFeatures = 0xd83dfff8
Aug 03 12:31:29: vcpu-0| Init modules.
Aug 03 12:31:29: vmx| IPC version negotiation version: VMX returning 2.1 to servercontrol
Aug 03 12:31:29: vmx| IPC vmcontrol-temp version: VMX returning 11.4 to servercontrol that tried 11.4
Aug 03 12:31:29: vcpu-0| CPU reset: hard
Aug 03 12:31:29: vmx| VNET: Notification enabled for Ethernet0
Aug 03 12:31:29: vmx| FLOPPYLIB-LIB  : GenIoctl: syserror Invalid argument.
Aug 03 12:31:29: vcpu-0| sz=2723808
Aug 03 12:31:29: vcpu-0| MX: init lock: rank(barrierLck)=3
Aug 03 12:31:29: vcpu-0| MX: init condvar: barrierCV
Aug 03 12:31:29: vcpu-0| MX: init lock: rank(barrierLck)=3
Aug 03 12:31:29: vcpu-0| MX: init condvar: barrierCV
Aug 03 12:31:29: vcpu-0| vmm32 initialized: BETAbuild-91891. cflags: 0x08000002.01c41400.00000150
Aug 03 12:31:29: mks| Connecting to window system.
Aug 03 12:31:29: mks| XINFO X fd is 43
Aug 03 12:31:29: mks| XINFO depth 24 bpp 32 class 4
Aug 03 12:31:29: mks| XINFO WARNING: XF86MISC version 0.9
Aug 03 12:31:29: mks| XINFO X Error Event display 0x8715278, request 136.3, error 2.
Aug 03 12:31:29: mks| VT redirected kernel output to /dev/tty1
Aug 03 12:31:29: mks| rasterops MMXEXT accelerations enabled
Aug 03 12:31:29: mks| XINFO unsupported XF86VidMode version: 2.2
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 0: 800x600 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 1: 1024x768 flags: 0xa
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 2: 800x600 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 3: 1280x960 flags: 0x6
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 4: 640x480 flags: 0xa
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 5: 1280x1024 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 6: 1024x768 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 7: 1280x1024 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 8: 1280x960 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 9: 1280x800 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 10: 1280x768 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 11: 1152x864 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 12: 1152x768 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 13: 1024x768 flags: 0xa
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 14: 832x624 flags: 0xa
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 15: 800x600 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 16: 800x600 flags: 0x5
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 17: 800x512 flags: 0x2a
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 18: 720x450 flags: 0x25
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 19: 700x525 flags: 0x25
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 20: 640x480 flags: 0xa
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 21: 640x480 flags: 0xa
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 22: 640x480 flags: 0xa
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 23: 576x384 flags: 0x25
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 24: 512x384 flags: 0x2a
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 25: 512x384 flags: 0x2a
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 26: 400x300 flags: 0x25
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 27: 320x240 flags: 0x2a
Aug 03 12:31:29: mks| XINFO XFree86 VidMode 28: 320x240 flags: 0x2a
Aug 03 12:31:29: mks| Failed to autodetect the mouse type. Please set the mouse type and device using the configuration editor to enable full screen mode for your virtual machine.
Aug 03 12:31:29: mks| MKSHostDVGAPowerOn failed, full screen VGA will not be available.
Aug 03 12:31:29: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:31:29: mks| Adding local console 0x8723220
Aug 03 12:31:29: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:31:29: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0x0) and 0xec000000(0x0)
Aug 03 12:31:29: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Aug 03 12:31:29: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Aug 03 12:31:29: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Aug 03 12:31:29: vcpu-0| SVGA: Registering IOSpace at 0x1060 (0x0)
Aug 03 12:31:29: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Aug 03 12:31:29: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:31:29: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:31:29: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:31:29: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:31:30: vcpu-0| maxStackDepth(1) = 3120
Aug 03 12:31:31: vcpu-0| DISKUTIL: scsi0:0 : geometry=1305/255/63
Aug 03 12:31:32: vcpu-0| BIOS-UUID is 56 4d 47 da 67 47 4f 28-08 bd d7 9d 92 57 2d b1
Aug 03 12:31:32: vcpu-0| DISKUTIL: scsi0:0 : toolsVersion = 0
Aug 03 12:31:32: vcpu-0| DISKUTIL: Offline toolsVersion = 0
Aug 03 12:31:32: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:31:32: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:31:32: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:32: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:32: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:32: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:32: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:33: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:33: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:33: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:33: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:33: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:33: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:33: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Aug 03 12:31:35: mks| MKS enabling SVGA
Aug 03 12:31:38: mks| MKS lock acquiring
Aug 03 12:31:38: mks| MKS lock not locked
Aug 03 12:31:38: mks| MKS lock acquiring
Aug 03 12:31:40: vcpu-0| Unknown int 10h func 0x0000
Aug 03 12:31:40: mks| MKS disabling SVGA
Aug 03 12:31:40: mks| HostOps hideCursor before defineCursor!
Aug 03 12:31:40: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:31:40: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:31:40: vcpu-0| maxStackDepth(0) = 3728
Aug 03 12:31:41: vcpu-0| maxStackDepth(1) = 3568
Aug 03 12:31:55: mks| MKS lock releasing
Aug 03 12:31:56: vcpu-0| SVGA: Unregistering IOSpace at 0x1060 (0x1060)
Aug 03 12:31:56: vcpu-0| SVGA: Registering IOSpace at 0xfff0 (0x0)
Aug 03 12:31:56: vcpu-0| SVGA: Unregistering IOSpace at 0xfff0 (0xfff0)
Aug 03 12:31:56: vcpu-0| SVGA: Registering IOSpace at 0x1060 (0x0)
Aug 03 12:32:03: vcpu-0| maxStackDepth(0) = 3884
Aug 03 12:32:05: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:32:05: mks| Ignoring update request in VGA_Expose (mode change pending).
Aug 03 12:32:40: mks| MKS lock acquiring
Aug 03 12:32:40: mks| MKS lock not locked
Aug 03 12:32:40: mks| MKS lock acquiring
Aug 03 12:33:10: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
Aug 03 12:33:46: vcpu-0| SCSI0: RESET BUS
Aug 03 12:33:47: vcpu-0| SCSI DEVICE (scsi0:0): MODE SENSE(6) for unsupported page 0
Aug 03 12:33:47: vcpu-0| SCSI DEVICE (scsi0:0): MODE SENSE(6) for unsupported page 0x8
Aug 03 12:33:47: vcpu-0| SCSI DEVICE (scsi0:0): MODE SENSE(6) for unsupported page 0
Aug 03 12:33:47: vcpu-0| SCSI DEVICE (scsi0:0): MODE SENSE(6) for unsupported page 0x8
Aug 03 12:33:47: vcpu-0| SCSI DEVICE (scsi0:0): INQUIRY request with EVDP set
Aug 03 12:33:50: vcpu-0| SCSI DEVICE (scsi0:0): INQUIRY request with EVDP set
Aug 03 12:33:56: vcpu-0| VLANCE: Returning 0x0 for LANCE_EXTINT IN
Aug 03 12:33:56: vcpu-0| VLANCE: Ignoring LANCE_EXTINT OUT of 0x1
Aug 03 12:33:56: vcpu-0| VLANCE: IN on LANCE_MODE while not stopped: 0x73
Aug 03 12:33:56: vcpu-0| NOT_IMPLEMENTED /build/mts/release/bora-91891/pompeii2005/bora/devices/net/vlance.c:1802
Aug 03 12:33:56: vcpu-0| Backtrace:
Aug 03 12:33:56: vcpu-0| Backtrace[0] 0xf1cc4e48 eip 0x805dbd0 
Aug 03 12:33:56: vcpu-0| Backtrace[1] 0xf1cc5268 eip 0x80d618b 
Aug 03 12:33:56: vcpu-0| Backtrace[2] 0xf1cc5298 eip 0x81e8af9 
Aug 03 12:33:56: vcpu-0| Backtrace[3] 0xf1cc52c8 eip 0x81e6897 
Aug 03 12:33:56: vcpu-0| Backtrace[4] 0xf1cc52e8 eip 0x831a803 
Aug 03 12:33:56: vcpu-0| Backtrace[5] 0xf1cc5318 eip 0x831b04a 
Aug 03 12:33:56: vcpu-0| Backtrace[6] 0xf1cc5358 eip 0x8325f14 
Aug 03 12:33:56: vcpu-0| Backtrace[7] 0xf1cc5368 eip 0x831b371 
Aug 03 12:33:56: vcpu-0| Backtrace[8] 0xf1cc53d8 eip 0x806cb60 
Aug 03 12:33:56: vcpu-0| Backtrace[9] 0xf1cc54c8 eip 0xf7f484fb 
Aug 03 12:33:56: vcpu-0| Backtrace[10] 00000000 eip 0xf7d4408e 
Aug 03 12:33:56: vcpu-0| Dumping core...
Aug 03 12:33:57: vcpu-0| Msg_Post: Error
Aug 03 12:33:57: vcpu-0| [msg.log.error.unrecoverable] VMware Server unrecoverable error: (vcpu-0)
Aug 03 12:33:57: vcpu-0| NOT_IMPLEMENTED /build/mts/release/bora-91891/pompeii2005/bora/devices/net/vlance.c:1802
Aug 03 12:33:57: vcpu-0| [msg.panic.haveLog] A log file is available in "/home/emyr/Downloads/VMWare/Ubuntu/vmware.log".  [msg.panic.haveCore] A core file is available in "/home/emyr/Downloads/VMWare/Ubuntu/core".  [msg.panic.requestSupport.withLogAndCore] Please request support and include the contents of the log file and core file.  [msg.panic.requestSupport.linux] 
Aug 03 12:33:57: vcpu-0| To collect files to submit to VMware support, run vm-support.
Aug 03 12:33:57: vcpu-0| [msg.panic.response] We will respond on the basis of your support entitlement.
Aug 03 12:33:57: vcpu-0| ----------------------------------------
Aug 03 12:33:57: vcpu-0| POST(no connection): VMware Server unrecoverable error: (vcpu-0)
Aug 03 12:33:57: vcpu-0| NOT_IMPLEMENTED /build/mts/release/bora-91891/pompeii2005/bora/devices/net/vlance.c:1802
Aug 03 12:33:57: vcpu-0| A log file is available in "/home/emyr/Downloads/VMWare/Ubuntu/vmware.log".  A core file is available in "/home/emyr/Downloads/VMWare/Ubuntu/core".  Please request support and include the contents of the log file and core file.  
Aug 03 12:33:57: vcpu-0| To collect files to submit to VMware support, run vm-support.
Aug 03 12:33:57: vcpu-0| We will respond on the basis of your support entitlement.
Aug 03 12:33:57: vcpu-0| 
Aug 03 12:33:57: vmx| VTHREAD watched thread 4 "vcpu-0" died
Aug 03 12:33:57: IO#4| VTHREAD watched thread 0 "vmx" died
Aug 03 12:33:57: mks| VTHREAD watched thread 0 "vmx" died
Aug 03 12:33:57: mks| MKS release: start, nesting 0
Aug 03 12:33:57: mks| MKS starting full screen: off force
Aug 03 12:33:57: mks| MKS already off
Aug 03 12:33:57: mks| MKS finished full screen: done
Aug 03 12:33:57: mks| ASSERT /build/mts/release/bora-91891/pompeii2005/bora/mks/main/mks.c:854
Aug 03 12:33:57: mks| Panic loop
Aug 03 12:33:57: mks| Backtrace:
Aug 03 12:33:57: mks| Backtrace[0] 0xf24c5d08 eip 0x805dbd0 
Aug 03 12:33:57: mks| Backtrace[1] 0xf24c6128 eip 0x80d616c 
Aug 03 12:33:57: mks| Backtrace[2] 0xf24c6148 eip 0x81ac114 
Aug 03 12:33:57: mks| Backtrace[3] 0xf24c6168 eip 0x81ac3c7 
Aug 03 12:33:57: mks| Backtrace[4] 0xf24c6178 eip 0x81a203b 
Aug 03 12:33:57: mks| Backtrace[5] 0xf24c61a8 eip 0x806f974 
Aug 03 12:33:57: mks| Backtrace[6] 0xf24c61e8 eip 0x8110e0b 
Aug 03 12:33:57: mks| Backtrace[7] 0xf24c6218 eip 0x806de9a 
Aug 03 12:33:57: mks| Backtrace[8] 0xf24c6238 eip 0x806e0e3 
Aug 03 12:33:57: mks| Backtrace[9] 0xf24c6268 eip 0x806beb9 
Aug 03 12:33:57: mks| Backtrace[10] 0xf24c62c8 eip 0x806b424 
Aug 03 12:33:57: mks| Backtrace[11] 0xf24c6318 eip 0x806ad14 
Aug 03 12:33:57: mks| Backtrace[12] 0xf24c6338 eip 0x806abc9 
Aug 03 12:33:57: mks| Backtrace[13] 0xf24c6368 eip 0x81a210e 
Aug 03 12:33:57: mks| Backtrace[14] 0xf24c63d8 eip 0x806cb60 
Aug 03 12:33:57: mks| Backtrace[15] 0xf24c64c8 eip 0xf7f484fb 
Aug 03 12:33:57: mks| Backtrace[16] 00000000 eip 0xf7d4408e 

Any ideas?

Cheers

---

### Post by fsando on 2008-08-03
Hi, and thanks for the howto

I don't know if this has come up earlier in this thread (too long to read through, but I did a google search that should have it if was mentioned)

When trying to install the VMWare server mui I get this error
```
ubuntu VMware Server must be installed on this machine for the VMware Management Interface to work
```

[Wolfs ubuntu blog]("http://wolfs-ubuntu.blogspot.com/2008/06/updating-vmware-server-and-mui.html") explains how to fix it.

It appears to be an incompatibility with vmw server 1.06.
He essentially suggests to rename 'libgcc_s.so.1' in the vmw lib folder.

```
sudo mv /usr/lib/vmware/lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1_orig
```

Now the MUI installs fine. 

There is also a mention of how to solve a conflict with Apache.

---

### Post by bodhi.zazen on 2008-08-03
> **fsando said:**
> Hi, and thanks for the howto

I don't know if this has come up earlier in this thread (too long to read through, but I did a google search that should have it if was mentioned)

When trying to install the VMWare server mui I get this error
```
ubuntu VMware Server must be installed on this machine for the VMware Management Interface to work
```[Wolfs ubuntu blog]("http://wolfs-ubuntu.blogspot.com/2008/06/updating-vmware-server-and-mui.html") explains how to fix it.

It appears to be an incompatibility with vmw server 1.06.
He essentially suggests to rename 'libgcc_s.so.1' in the vmw lib folder.

```
sudo mv /usr/lib/vmware/lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1_orig
```Now the MUI installs fine. 

There is also a mention of how to solve a conflict with Apache.

That was mentioned in the first post on this thread, step #5

Although your explanation why is better and the link you posted is appreciated.

---

### Post by sjpritch25 on 2008-08-04
Getting the following error trying to install vmware server 1.0.5

```
Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] /usr/share/icons

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] /usr/share/applications

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] /usr/share/pixmaps

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-generic/build/include] /lib/modules/2.6.24-19-generic/build/include

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

```

---

### Post by bodhi.zazen on 2008-08-04
VMWare Server 1.0.5 is out dated, while 1.0.6 works flawlessly (usually).

I suggest you install 1.0.6

---

### Post by sjpritch25 on 2008-08-04
thanks went ahead with 1.0.6

get this error

```
stefan@stefan-desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

---

### Post by bodhi.zazen on 2008-08-04
:lolflag:

See step 5 on the first post of this thread :twisted:

---

### Post by sjpritch25 on 2008-08-04
:biggrin::biggrin::biggrin::biggrin:

Thanks.

it worked

didn't look at that

---

### Post by sjpritch25 on 2008-08-04
wow its so much faster in hardy.

:guitar:

---

### Post by RealG187 on 2008-08-04
> **bodhi.zazen said:**
> Look at the first post in this thread, step 1 ;)

It says to look at the troubleshooting thread, but I do not even know what's going on

---

### Post by bodhi.zazen on 2008-08-05
oops, me bad :redface:

Step 2:

[FONT=Times New Roman]```
sudo apt-get install build-essential linux-headers-`uname -r` **xinetd**[/FONT]
```


you need to install the dependencies, including xinetd

---

### Post by RealG187 on 2008-08-06
I already have build-essential so I skipped that step.

Should I type:

sudo apt-get install  linux-headers-`uname -r` xinetd

or will it already know I have it so skip it anyways?

---

### Post by bodhi.zazen on 2008-08-06
That looks good to me RealG187

---

### Post by RealG187 on 2008-08-07
> **bodhi.zazen said:**
> That looks good to me RealG187

What typing with or without? Are they both good at this point?

---

### Post by bodhi.zazen on 2008-08-07
```
sudo apt-get install  linux-headers-`uname -r` xinetd
```

assuming build-essential is already installed.

---

### Post by Kobalt on 2008-08-08
Thank you very much for this clean HowTo bohdi.zazen, now I can use vmware_server just like a pro ;)

---

### Post by davidw89 on 2008-08-09
How does this compare to VirtualBox OSE?

---

### Post by Bosconian on 2008-08-10
> **bodhi.zazen said:**
> _**[SIZE=4]Remove (uninstall) VMWare[/SIZE]**_

 If you want to remove vmware, run :
```
sudo vmware-uninstall.pl
```



How do you uninstall 2.0 RC1? There is no vmware-uninstall.pl. Frankly 2.0 is terrible and I want to get it completely cleaned off my system.

---

### Post by kenmiles on 2008-08-10
> **Bosconian said:**
> How do you uninstall 2.0 RC1? There is no vmware-uninstall.pl. Frankly 2.0 is terrible and I want to get it completely cleaned off my system.

/usr/bin/vmware-uninstall.pl

It is there on mine and 2.0 works without any problems with XP.

Regards, Kenneth.

---

### Post by RealG187 on 2008-08-10
> mpg@MIKED5:~$ sudo apt-get install build-essential linux-headers-`uname -r` xinetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.24-16-generic is already the newest version.
The following NEW packages will be installed:
  xinetd
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 137kB of archives.
After this operation, 377kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main xinetd 1:2.3.14-5 [137kB]
Fetched 137kB in 2s (64.2kB/s) 
Selecting previously deselected package xinetd.
(Reading database ... 141345 files and directories currently installed.)
Unpacking xinetd (from .../xinetd_1%3a2.3.14-5_i386.deb) ...
Setting up xinetd (1:2.3.14-5) ...
 * Stopping internet superserver xinetd                                  [ OK ] 
 * Starting internet superserver xinetd                                  [ OK ] 

mpg@MIKED5:~$ 


Sucess! I redid the config script and it asked for the serial. It's wierd, it said I already had linux headers, I do not remember installing it, does it come with Ubuntu?

Anyways I tried to open a VM I already made in Windows Vista VM Ware ACE:
[img]http://img93.imageshack.us/img93/1845/VM.png[/img]

after that didnt work I made a new VM but tried to use the same hard disk image file:
[img]http://img93.imageshack.us/img93/3345/disk.png[/img]

This was my fear, that it wouldnt be compatible with the windows version...

Is there a way to make it run. Perhaps can I go back into ACE and change some settings so they are compatible with server?

Also about the commaand:
sudo apt-get install build-essential linux-headers-`uname -r` xinetd

I understand that sudo means root, apt-get install means to install a program, build-essential, linux-headers and xinetd are the packages to be installed, but what is "`uname -r`"?

---

### Post by alcatraz678 on 2008-08-11
Hey guys, I'm stuck on step 3. I'm a new user so please be considerate. =D

---

### Post by bodhi.zazen on 2008-08-11
How are you stuck ?

---

### Post by alcatraz678 on 2008-08-12
i don't know what to put in this line right here. i have no idea

mkdir -p ~/src/VMWare #Download VMWare files here

---

### Post by supremedalek on 2008-08-12
I too seem to be having a bit of a problem: I did a clean reinstall in my laptop to go to 8.04 and now cannot get vmware server 1.0.6 to run on my machine. Only clues I have (that I know of) are this warning message during the install process,

```
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
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
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

```

Other than that, and that I need to do something for it to use my wireless card, it acted like it installed without an issue. Here is the error message I am getting:

```
raub@monaco:~/todo/vmware-server-distrib$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/local/bin/vmware-config.pl.

raub@monaco:~/todo/vmware-server-distrib$ 

```

I thought on removing /etc/vmware/not_configured to see if it makes it work. Other than that, I have no clues.

---

### Post by bodhi.zazen on 2008-08-12
> **alcatraz678 said:**
> i don't know what to put in this line right here. i have no idea

mkdir -p ~/src/VMWare #Download VMWare files here

You put that command into a terminal.

You then download files from VMWare and save them there, rather then on the desktop.

~ is short hand for your home directory.

so ~ = /home/<username> where <username> == you log in name.

You will see later on you cd into ~/src/VMWare ;)

These commands are very basic, if you do not understand them, I suggest you stop and do some reading.

[http://linuxcommand.org/](http://linuxcommand.org/)

Assisting with the command line is a little beyond this thread, however, so if you get stuck, ask questions in ABT or general help.

---

### Post by RealG187 on 2008-08-13
Is there a way to get shared folders. I thought since server was free they wouldn't include this features, the &(*^%)^&s!).

I tried to install VM Ware workstation workstation-5.5.3-34686 and get this when trying to configure

> mpg@MIKED5:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

mpg@MIKED5:~$ sudo /usr/bin/vmware-config.pl
[sudo] password for mpg: 
Making sure services for VMware Workstation are stopped.

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

/usr/share/applications/vmware-workstation.desktop: warning: value "vmware-workstation.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-player.desktop: warning: value "vmware-player.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:48:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_types.h:160: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:60: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:65: error: previous declaration of &#8216;poll_initwait&#8217; was here
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:80:
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
/tmp/vmware-config2/vmmon-only/linux/driver.c:145: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:149: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1661: error: &#8216;struct mm_struct&#8217; has no member named &#8216;dumpable&#8217;
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


---

### Post by bodhi.zazen on 2008-08-14
Personally I just use a network protocol to such as samba, ssh (scp), ftp, nfs, etc. Samba is easy to set up.

---

### Post by RealG187 on 2008-08-14
How do I do that? Is there a way to communicate between the host OS and guest OS?

But then again I might want VM Ware workstation since it can run that other VM I made...



[http://www.debuntu.org/how-to-vmware-server-workstation-under-ubuntu-feisty](http://www.debuntu.org/how-to-vmware-server-workstation-under-ubuntu-feisty)

I found this but it is for an older Ubuntu and cd lib/modules/source/ doesnt exist.

---

### Post by kenmiles on 2008-08-15
> **RealG187 said:**
> How do I do that? Is there a way to communicate between the host OS and guest OS?

But then again I might want VM Ware workstation since it can run that other VM I made...



[http://www.debuntu.org/how-to-vmware-server-workstation-under-ubuntu-feisty](http://www.debuntu.org/how-to-vmware-server-workstation-under-ubuntu-feisty)

I found this but it is for an older Ubuntu and cd lib/modules/source/ doesnt exist.

Follow this link, it makes it so easy -

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

Regards, Kenneth.

---

### Post by RealG187 on 2008-08-15
I kinda "Broke" server:
[http://ubuntuforums.org/showthread.php?t=791708&page=2](http://ubuntuforums.org/showthread.php?t=791708&page=2)
See post #20 (How do I link to a single post?)

Will it work for a Windows 98 guest? See for me 98 is the perfect (Windows) OS except for the fact that for every flash drive you plugin you gotta install a driver, when I got my 2nd Samsung MP3 Player/Flash Drive I had to install a driver, even though I already had the driver for the first one. In Ubuntu I just plug it in! So I want shared folders to allow the guest 98 to access flash drives via the (virtual) network and not the USB protocol. This way I should only need netowrking support, and Ubuntu will take care of the drivers for the flash drives! That should work right?

ALso, do I need two computers to do this?

UPDATE: I redid the insturctions here but this is what happens:

> vmpg@MIKED5:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
mpg@MIKED5:~$ 

---

### Post by bodhi.zazen on 2008-08-15
That problem should be fixed by step 5 ...

> [FONT=Times New Roman]Post-install configuration. Last, before running vmware :

   ```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0 
```[/FONT][FONT=Times New Roman]
[/FONT]

---

### Post by RealG187 on 2008-08-15
> **bodhi.zazen said:**
> That problem should be fixed by step 5 ...

[FONT=Times New Roman]
[/FONT]

I typed that and it works.

It said to enter the serial when insalling and it never went that far so I assumed something was wrong, but it never asked for the serial because I entered it from before...

---

### Post by bodhi.zazen on 2008-08-15
> **RealG187 said:**
> I typed that and it works.

It said to enter the serial when insalling and it never went that far so I assumed something was wrong, but it never asked for the serial because I entered it from before...

:guitar:

---

### Post by RealG187 on 2008-08-15
Regarding [http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

How do I find the IP of the Host OS in Windows 98?

---

### Post by Yaka on 2008-08-19
hi

i have followed the guide and used defualts as suggested by the guide
but i get a nat error every time i try to run vmware. i have reconfigured it twice

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed


preety sure as i am a total n00b, i am missing something or doing something wrong

---

### Post by RealG187 on 2008-08-20
I can access the guest from the host, but not the host from the guest. Well I can but there is a password I do not know.

> mpg@MIKED5:~$ sudo smbpasswd
[sudo] password for mpg: 
New SMB password:
Retype new SMB password:
Failed to find entry for user root.
Failed to modify password entry for user root


I can connect to it from windows but I do not know the password and it won't let me change it! I tried my login password and the one I made during samba setup...

---

### Post by kenmiles on 2008-08-20
> **RealG187 said:**
> I can access the guest from the host, but not the host from the guest. Well I can but there is a password I do not know.



I can connect to it from windows but I do not know the password and it won't let me change it! I tried my login password and the one I made during samba setup...

Try this, if you followed the guide fully-

sudo smbpasswd -a sandbox

Regards, Kenneth.

---

### Post by RealG187 on 2008-08-20
> **kenmiles said:**
> Try this, if you followed the guide fully-

sudo smbpasswd -a sandbox

Regards, Kenneth.

So I changed the password but I still cannot access the host...

---

### Post by kenmiles on 2008-08-20
> **RealG187 said:**
> So I changed the password but I still cannot access the host...

Are you sure that you are using the right ip, it is normally the first one.

/home/kenneth-->ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:ec:ea:d3:05
          inet addr:213.123.183.61  Bcast:213.123.183.63  Mask:255.255.255.252
          inet6 addr: fe80::216:ecff:feea:d305/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:524129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:382308021 (364.5 MB)  TX bytes:101338647 (96.6 MB)
          Interrupt:19 Base address:0x2800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:90821967 (86.6 MB)  TX bytes:90821967 (86.6 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:172.16.168.1  Bcast:172.16.168.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:172.16.79.1  Bcast:172.16.79.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Regards, Kenneth.

---

### Post by RealG187 on 2008-08-20
> **kenmiles said:**
> Are you sure that you are using the right ip, it is normally the first one.

/home/kenneth-->ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:ec:ea:d3:05
          inet addr:213.123.183.61  Bcast:213.123.183.63  Mask:255.255.255.252
          inet6 addr: fe80::216:ecff:feea:d305/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:524129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:382308021 (364.5 MB)  TX bytes:101338647 (96.6 MB)
          Interrupt:19 Base address:0x2800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:90821967 (86.6 MB)  TX bytes:90821967 (86.6 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:172.16.168.1  Bcast:172.16.168.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:172.16.79.1  Bcast:172.16.79.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Regards, Kenneth.

What is the IP in your case? I can also type my host name and access it but it does the same thing as well...

---

### Post by kenmiles on 2008-08-20
Post the output from a linux console-
$ ifconfig

Regards, Kenneth.

---

### Post by kenmiles on 2008-08-20
After you have set up your network drive in windows you connect to it by logging in as - 
your_linux_user_name\sandbox
password is your samba password

Regards, Kenneth.

---

### Post by Yaka on 2008-08-20
nm mind solved it,

---

### Post by RealG187 on 2008-08-20
> mpg@MIKED5:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:4f:9b:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:d3:4f:9b:ce  
          inet addr:169.254.9.28  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86720 (84.6 KB)  TX bytes:86720 (84.6 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.241.1  Bcast:172.16.241.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.194.1  Bcast:192.168.194.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:45:2a:a2  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe45:2aa2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:572538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:533054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:439868463 (419.4 MB)  TX bytes:304230060 (290.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-45-2A-A2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

The ipadress I was using before, 192.168.1.100, was the my IP for my laptop on my Wifi and not the vm virtual adaptor....

---

### Post by RealG187 on 2008-08-22
Okay I think I know why the password isnt working.

Okay when I try to connect to my own PC from "Network" (as a test) in Ubuntu, I have to change the username to sandbox, right? Well when I accessed from XP and went to "Login as a different user" and entered sandbox, it worked!

The problem is in Windows 98 has no option to "Logon as other user"

Is there a way to make it so anyusername can login, or remove the samba password (I have a WEP key and really wouldn't put any valueble information on a samba share anyways!)

---

### Post by kenmiles on 2008-08-23
> **RealG187 said:**
> Okay I think I know why the password isnt working.

Okay when I try to connect to my own PC from "Network" (as a test) in Ubuntu, I have to change the username to sandbox, right? Well when I accessed from XP and went to "Login as a different user" and entered sandbox, it worked!

The problem is in Windows 98 has no option to "Logon as other user"

Is there a way to make it so anyusername can login, or remove the samba password (I have a WEP key and really wouldn't put any valueble information on a samba share anyways!)

In windows 98 post the available drives listed in windows explorer.

Regards, Kenneth.

---

### Post by RealG187 on 2008-08-23
> **kenmiles said:**
> In windows 98 post the available drives listed in windows explorer.

Regards, Kenneth.

You mean "My Computer?" I have floppy (dunno why my laptop [the host] doesnt have a floppy and it just says the device is not ready), C:\ and CD-Rom Drive D:\...

When I map a network drive there is no option to logon as other user like there is in XP!

---

### Post by kenmiles on 2008-08-24
> **RealG187 said:**
> You mean "My Computer?" I have floppy (dunno why my laptop [the host] doesnt have a floppy and it just says the device is not ready), C:\ and CD-Rom Drive D:\...

When I map a network drive there is no option to logon as other user like there is in XP!

It would seem that the reason you cant access the drive is that it has not been mapped, it should be something like z:/sandbox on 192.xxx.xxx.
Have you got two vm machines set up, one for XP and one for 98?

Regards, Kenneth.

---

### Post by tigerplug on 2008-08-24
great post - updating to 2.0 now.  

USB 2.0 support!!! wooohooOo!

---

### Post by RealG187 on 2008-08-26
I think I F'ed up my samba. I deleted sandbox as I cannot access it and made a new share the normal way (right click -- sharing) but when I access my machine it shows sansbox and not my new share, it shows what it shouldn't amd won't show what it should!

I typed

```
sudo /etc/init.d/samba restart
```
and it still wont do it

---

### Post by MacDuff on 2008-08-29
Tried to use this and things seemed to go OK.  Got a final message the it installed correctly but when I tried to run VMWare Server from the GUI the load icon spun a few times then quit and nothing appeared.
I then tried the command line ~$ vmware and got the following message:

[PHP]mac@comm:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
mac@comm:~$ [/PHP]

What do I do to address this problem please.

---

### Post by kenmiles on 2008-08-29
> **MacDuff said:**
> Tried to use this and things seemed to go OK.  Got a final message the it installed correctly but when I tried to run VMWare Server from the GUI the load icon spun a few times then quit and nothing appeared.
I then tried the command line ~$ vmware and got the following message:

[PHP]mac@comm:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
mac@comm:~$ [/PHP]

What do I do to address this problem please.

Are you using vmware server 1.0.7 as this problem is related to earlier versions where the any any patch was required.
Regards, Kenneth.

---

### Post by MacDuff on 2008-08-29
Yes, I originally installed 1.0.6 and had the same problem so I un-installed it and then did an install of 1.0.7 but the problem re-occurred.

Can't be certain that all of 1.0.6 was removed however.  I am still a bit green when it comes to Linux

---

### Post by bodhi.zazen on 2008-08-29
MacDuff : See step 5 on the first post on this very thread :twisted:

---

### Post by RealG187 on 2008-08-29
How can I fix my Samba so shares other than sandbox show up?

---

### Post by MacDuff on 2008-08-29
Sure does make a fellow feel stupid...  Could have SWORN I did that step but I re-did it and here is the result of the second part:
 mac@comm:~$ sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
sudo: unable to resolve host comm
mac@comm:~$ 

It appears that something is still missing.  Perhaps I should configure it again?

Mac

---

### Post by bodhi.zazen on 2008-08-29
Well, that sounds like a problem with sudo, not vmware.

boot to recovery mode, edit /etc/hostname and /etc/hosts

make sure your hostname is the same in both files and that the host name in /etc/hosts is listed on the line that starts with:

127.0.1.1 

While you are there you can do the cp, then 

```
telinit 2
```

---

### Post by kenmiles on 2008-08-30
> **MacDuff said:**
> Yes, I originally installed 1.0.6 and had the same problem so I un-installed it and then did an install of 1.0.7 but the problem re-occurred.

Can't be certain that all of 1.0.6 was removed however.  I am still a bit green when it comes to Linux

Try this
:~$ sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

:~$ sudo cp /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

Regards, Kenneth.

---

### Post by MacDuff on 2008-08-30
kenmiles:  Thanks for the suggestion but it did not change anything.

As usual, bodhi.zazen came through with flying colours.  Your idea about cross checking the hosts and hostname files was brilliant.  One of them had the computer name followed by the network name as in "comm.macnet"

There are millions of things that I do not yet understand about Ubuntu. The experience of learning Linux has been a real character builder but the generous help of forum members has enabled me to prevail.

Thank you

---

### Post by daverab on 2008-08-31
Yeah, I'm having issues myself.

First, before I go any further, yes, I'm using Ibex and not Hardy.

I'm under the new 2.6.27-2 kernel. Normally I could just do the ./vmware-config.pl command and everything was fine.

No longer, vmmon won't build anymore. I've tried several different things, the any-any-patch115, and the two copy lines listed in the directions. No luck. The error is this:

/tmp/vmware-config4/vmmon-only/linux/driver.c:1781: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-2-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

This is happening under both server and player (attempted to do player as well since I realize I don't need server anymore since the vm is already up and running).

I tried to get some help in the Ibex forum, but no answer. I hope someone can help here.

---

### Post by veloce on 2008-09-01
> **daverab said:**
> 
First, before I go any further, yes, I'm using Ibex and not Hardy.

I'm under the new 2.6.27-2 kernel. Normally I could just do the ./vmware-config.pl command and everything was fine.

No longer, vmmon won't build anymore. I've tried several different things, the any-any-patch115, and the two copy lines listed in the directions. No luck. The error is this:



This sounds like an any-any-patch issue.

Check that 115 is the latest patch available.

If it is, then I suspect you will either have to wait for a patch that copes with Ibex or revert to Hardy.

---

### Post by daverab on 2008-09-01
Sorry for the begging. It's an issue with 2.6.27. The devs just pushed it out for testing, and they haven't had enough time to iron out all the issues like this. I reverted back to the previous kernel with Ibex, 2.6.26-5, and everything works fine again.

There is a 117d patch for 2.6.25 that is mostly un-needed. The author posts the versions here: [http://groups.google.com/group/vmkernelnewbies/files](http://groups.google.com/group/vmkernelnewbies/files) and has a blog to explain the updates here (this is just a howto article for the 2.6.25 kernel install): [http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2625-kernel](http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2625-kernel)

Both of those might be handy for future reference.

---

### Post by jflowers on 2008-09-01
I am trying to use VMware 1.06 to run my existing Windows XP parition in Ubuntu 8.04.  I installed VMware following this link, and the followed the instructions for creating the virtual machine using this link:

[http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu)

and when I start the run, I get the BSOD in the virtual machine.  My hard drives are IDE, but the virtual device node in VMware only provides SCSI options.  

Any ideas if the hard drive is the issue or something else?

Thank you for your help.

BTW, I did not do the any-any patch sense it does not state that this is required.

---

### Post by jflowers on 2008-09-03
Well, it turns out I was right.  I had to install the vmscsi drivers on my Windows OS in the Virtual (or VMware) hardware profile.  Information on this can be found at: 

[http://www.kvaes.be/unix-linux/running-your-dual-boot-windows-inside-vmware-server-within-ubuntu/](http://www.kvaes.be/unix-linux/running-your-dual-boot-windows-inside-vmware-server-within-ubuntu/)

I hope this helps others.

---

### Post by RealG187 on 2008-09-03
Can somebody please help me [here]("http://ubuntuforums.org/showthread.php?t=905998")?!?!?

---

### Post by chootarlaal on 2008-09-08
anyone have issues with Server 2.0 RC2, creating a user for the first time?  i run VMWare as root and then try to create a user, but it keeps erroring out.

edit:  ok, i managed to create a user "user1" which is my regular username under kubuntu.  when i create the "user1" as an administrator, how do u set the password?  because when i log out of root and try to log back in with "user1", it asks for the password.  i tried the password i use when i log into kubuntu and also the root password, neither works.

im running Server 2.0 RC2 build 110948.

---

### Post by marcon00 on 2008-09-12
```
Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] 
```

why !! :S
 I had it working on the same system couple days before,i had to format my pc and how look :S whyy ! :P anyone ? :) i tried applying some patch that i googled , but its not working .. any suggestions ? thanks in advance

---

### Post by bodhi.zazen on 2008-09-12
> **marcon00 said:**
> ```
Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] 
```why !! :S
 I had it working on the same system couple days before,i had to format my pc and how look :S whyy ! :P anyone ? :) i tried applying some patch that i googled , but its not working .. any suggestions ? thanks in advance

Start your own thread. You are unlikely to get an answer on this thread.

When starting a new thread, please provide additional information such as version of Ubuntu, version of VMWare, link to patch, and reason for needing a patch.

If you are on Ubuntu 8.04 and VMWare 1.0.6 , the any-any patch is not needed.

---

### Post by marcon00 on 2008-09-12
but i installed this vmware like week ago, i had to formay my pc,shouldnt it be workin fine ? there is nothing new in the equation :S unless something new in the updates?

---

### Post by bodhi.zazen on 2008-09-12
Without additional information may I suggest google ?

[http://www.go2linux.org/Your_kernel_was_built_with_gcc_version_while_you_are_trying_to+use_version](http://www.go2linux.org/Your_kernel_was_built_with_gcc_version_while_you_are_trying_to+use_version)

[http://ubuntuforums.org/showthread.php?p=5770860](http://ubuntuforums.org/showthread.php?p=5770860)

[http://www.google.com/search?q=VMware+Your+kernel+was+built+with+%22gcc%22+version+%224.2.3%22&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=VMware+Your+kernel+was+built+with+%22gcc%22+version+%224.2.3%22&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by MacDuff on 2008-09-12
Tried to install as per these excellent instructions but apparently in a past life I installed and later removed (or did not remove but cannot find) VMWare server.  This message appears when trying to install:

> A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to find the binary installation directory (answer BINDIR)
       in the installer database file "/etc/vmware/locations".

Failure

Execution aborted.

How do I go about dealing with this?

---

### Post by bodhi.zazen on 2008-09-12
```
sudo rm -rf /etc/vmware 
sudo rm -rf /lib/modules/[version kernel]/vmware*
```

Then try re-installing.

---

### Post by MacDuff on 2008-09-12
Thank you, Thank you!

That worked a treat.  
I will master this Ubuntu stuff yet....  Well maybe minor it.

Mac

---

### Post by war59312 on 2008-09-14
Every time I try and power on a VM I get:

> Unable to change virtual machine power state: The process exited with an error:
End of error message.

This is a new install of VMWare Server 1.0.7. Real helpful error um... :(

Update: ok figured it out, just had to run sudo chown %username% ~/.vmware

---

### Post by veloce on 2008-09-14
> **war59312 said:**
> Every time I try and power on a VM I get:



This is a new install of VMWare Server 1.0.7. Real helpful error um... :(

Update: ok figured it out, just had to run sudo chown %username% ~/.vmware

For future reference, error messages are off by default.  You have to turn on debugging.  For a powered off vm:
Edit virtual machine settings - Options - Advanced
There is a checkbox labelled "Run with debugging information" 

Voila, you get error messages.

---

### Post by zachtib on 2008-09-22
> **veloce said:**
> For future reference, error messages are off by default.  You have to turn on debugging.  For a powered off vm:
Edit virtual machine settings - Options - Advanced
There is a checkbox labelled "Run with debugging information" 

Voila, you get error messages.

Does anyone know how I could get server console 1.0.7 to use my installed GTK theme (Dust)? Right now, it just uses an ugly default fallback theme.

---

### Post by Roygbiv on 2008-09-25
Hi,  I'm relitively new to Ubuntu and Ubuntu Forums.  Everything has been working fine with my VM ware until I updated my Firefox browser.  VM ware now won't boot.  I've tried reinstalling the drivers through Synaptic but with no luck. Can you help? 

Cheers,

---

### Post by kenmiles on 2008-09-25
> **Roygbiv said:**
> Hi,  I'm relitively new to Ubuntu and Ubuntu Forums.  Everything has been working fine with my VM ware until I updated my Firefox browser.  VM ware now won't boot.  I've tried reinstalling the drivers through Synaptic but with no luck. Can you help? 

Cheers,
 If you are using VMware 2.0 then the add on is not compatible with the updated firefox.
To run your virtual machine type 
localhost:8333
in the browser address bar.

Regards, Kenneth.

---

### Post by vgrisham on 2008-09-27
I've just installed VMWare in Hardy 64 bit and created a windows vista 32bit virtual machine. I got windows installed and working within the vm, but there is no sound. When I mouse over the speaker icon in windows, a message pops up that says, "No audio output device is installed." 

How do I go about getting sound to work within the virtual machine?

Thanks,
Vaughn

NEVER MIND. I searched the thread and found that I needed to add the hardware on the vm server side.

---

### Post by vgrisham on 2008-09-27
I would like to add a virtual machine and have it's hard disk reside on a second internal sata drive. Is that possible? If so, how would I go about setting that up?

---

### Post by veloce on 2008-09-27
> **vgrisham said:**
> I would like to add a virtual machine and have it's hard disk reside on a second internal sata drive. Is that possible? If so, how would I go about setting that up?

You set the default directory for vms in  Host: Settings: Default

You can change it at any time, doesn't affect existing vms.

---

### Post by xrvjorn on 2008-09-28
Is there any difference in the install procedures between VMWare Server 1.06 and 1.07? I tried install 1.07, using these instructions on a fresh 8.04 Server install. When I get to the part where VMWare asks for the serial no, I get a complaint about some missing file called **libX11.so.6**.

```
Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  90R2X-Y4R42-2FNF2-zzzzz

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
The serial number 90R2X-Y4R42-2FNF2-zzzzz is invalid.
```

The serial no I entered is correct BTW, copied and pasted straight from VMWare's registration page. I even tried a couple of different ones.

---

### Post by bodhi.zazen on 2008-09-28
See the trouble shooting post by [Illuvator]("http://ubuntuforums.org/member.php?u=205929")[FONT=Times New Roman] [/FONT](and posted at the bottom of the first post)

[http://ubuntuforums.org/showthread.php?t=337040](http://ubuntuforums.org/showthread.php?t=337040)

---

### Post by xrvjorn on 2008-09-28
> **bodhi.zazen said:**
> See the trouble shooting post 
[http://ubuntuforums.org/showthread.php?t=337040](http://ubuntuforums.org/showthread.php?t=337040)
I tried it, but no joy. Its' proposed remedy is "sudo apt-get install ia32-libs", but **ia32-libs** is only available in the repository for 64-bit Ubuntu ([http://ubuntuforums.org/showpost.php?p=3879162&postcount=3](http://ubuntuforums.org/showpost.php?p=3879162&postcount=3)). I'm running a 32-bit system.

---

### Post by vgrisham on 2008-09-28
I'm confused about which VMWare product I need. I have a single AMD64 pc running Hardy 64 bit. I want to be able to occasionally pull up Vista for a couple of applications I can't run through wine. Do I need VMWare Server or Desktop?

---

### Post by vgrisham on 2008-09-28
I got vmware installed and setup Vista as a guest. Everything works except for network and internet access.

I answered yes to the host-only question in the interview. 

Any ideas?

Thanks.

Once again, NEVER MIND. I switched the network card to bridged and Vista picked it up.

---

### Post by bodhi.zazen on 2008-09-28
> **vgrisham said:**
> I'm confused about which VMWare product I need. I have a single AMD64 pc running Hardy 64 bit. I want to be able to occasionally pull up Vista for a couple of applications I can't run through wine. Do I need VMWare Server or Desktop?

Go for server :)

VMWare server is freely available.

---

### Post by clydegoffe on 2008-09-29
This worked for me running Ubuntu Hardy 32-bit w/ VMware Server 2.0 Final Release

Thanks!

> **Black Sliver said:**
> The sound-problem: vmware-server 1.x uses oss/dsp for sound which can not be mixed by default, so you hear either vmware **or** the other program(s) depending on which opens the sound device first. 

As i heard pulse audio can also receive oss/dsp audio signals, so this "patch" might be useless if you use pulse. 

Here's a bash script that installs alsa-oss and replaces the start-scripts for **vmware-server 1.x** so it uses the alsa-oss-wrapper. I can't guarantee its working, but it worked for me on gutsy and hardy.
**Use at your own risk!**

To apply the patch
1. download the attachment
2. extract the .tar.gz
3. run the script from terminal

To remove the patch
1. delete /usr/bin/vmware and rename /usr/bin/vmware.real back to /usr/bin/vmware.
2. delete /usr/lib/vmware/bin/vmware-vmx and rename /usr/lib/vmware/bin/vmware-vmx.real back to /usr/lib/vmware/bin/vmware-vmx

---

### Post by rhart211 on 2008-09-29
okay...dumb question...
In hardy how do you upgrade vmware server 1.06 to version 2.0?
I have searched and have been unsuccessful.

---

### Post by xrvjorn on 2008-09-29
After much googling about this problem, ...

```
Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  90R2X-Y4R42-2FNF2-zzzzz

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
The serial number 90R2X-Y4R42-2FNF2-zzzzz is invalid.
```

... I found another VMWare server setup guide, which included an instruction which is missing in the guide in this thread:

```
sudo apt-get install libx11-6 libxtst6 libice-dev libsm-dev libxt6
```
Unfortunately, that only changes the error message into complaining about libXrender.so.something, so that guide is also missing information. Back to the drawing board and some more googling led me to yet another guide with yet another set of libraries to be installed:

```
sudo apt-get install libxrender1 libxt6 libxtst6 libx11-6
```
Alas, that didn't do the trick either. However, combining the two did:

```
sudo apt-get install libxrender1 libxt6 libxtst6 libx11-6 libice-dev libsm-dev
```

So, combining this guide with the two other, I finally got through the installation. Phew... 

I wish that was the end of the problems, but when I attempt the post-install configuration, I can't copy **/usr/lib/libpng12.so.0**, because it's not there. It's apparently used for handling PNG files, so I guess I won't need it in my text-only server environment?

---

### Post by dark_phantom on 2008-09-29
> **rhart211 said:**
> okay...dumb question...
In hardy how do you upgrade vmware server 1.06 to version 2.0?
I have searched and have been unsuccessful.

Two ways, either uninstall it (via vmware-uninstall.pl) then install the newly downloaded version or just run the new version and it should upgrade (remove old and install new).

---

### Post by chielchiel on 2008-10-03
hello,

i' followed this howto and all is working, thank you.
i just have one question, how do you switch from workspace with vmware in fullscreen? like the image on the frirst post.

---

### Post by bodhi.zazen on 2008-10-03
The image on the first post is Beryl, now called compiz, with the infamous "desktop cube".

---

### Post by chielchiel on 2008-10-05
I know, But how do you rotate the cube when vmware (windows) is in full screen mode?

---

### Post by zer0efx on 2008-10-05
Thanks for the tutorial! worked like a charm on the first attempt!

---

### Post by gerryg001 on 2008-10-06
Using VMWare server 2.0.0 build 110948 with Hardy. Ubuntu desktop-64 with 8Gb ram.

Used their Workstation for years, and install went smooth after I figured out their new browser UI. Went for Samba instead of VMWare shared folders, and all went well.

Until I tried a USB device. Traced the problem between Ubuntu host and VMWare, but couldn't find the issue. After many (many) hours, finally found this thread, and your fstab entry for USB sharing.

All now working, with multiple XP guests and Ubuntu 32 and 64. You mentioned an issue with Ubuntu-64 guests, but it seems to work okay, with a 64-bit host, which they say is required.

Read through your install guide, and it's nearly the same as what I did. Very nice work and thanks for the help.

---

### Post by drifting on 2008-10-11
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual machine communication interface                             done
   VM communication interface socket family:                          failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Bridged networking on /dev/vmnet2                                   done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                         failed

Followed the instructions, quite a newbie to vmware, had a working version 1.5 before, any ideas why the above failed? or even the implications of the failure, my VM is running fine ? This is on a 64 bit OS Ubuntu server.

Regards Paul.

---

### Post by bg1256 on 2008-11-01
Just curious if this thread will be updated for Intrepid Ibex or if anyone knows of a similar guide.

---

### Post by bodhi.zazen on 2008-11-01
> **bg1256 said:**
> Just curious if this thread will be updated for Intrepid Ibex or if anyone knows of a similar guide.

Look up ...

I posted an update for 8.10 already :twisted:

---

### Post by le_vainqueur on 2008-11-02
> **bodhi.zazen said:**
> Look up ...

I posted an update for 8.10 already :twisted:


Thanks for updating the thread, but maybe it would be a good idea to include this update in the first post so that it's easy to find.

---

### Post by RandyRandola on 2008-11-05
VMWare Server 1.0.7
Kernel 2.6.24-21-generic
Fresh install of ubuntu 8.04

Error:
/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no]

Any ideas on a fix?

Thanks!

Randy

---

### Post by frogotronic on 2008-11-05
> **jflowers said:**
> Well, it turns out I was right.  I had to install the vmscsi drivers on my Windows OS in the Virtual (or VMware) hardware profile.  Information on this can be found at: 

[http://www.kvaes.be/unix-linux/running-your-dual-boot-windows-inside-vmware-server-within-ubuntu/](http://www.kvaes.be/unix-linux/running-your-dual-boot-windows-inside-vmware-server-within-ubuntu/)

I hope this helps others.

I get the BSOD now with VMWare Server 2.0.  Never had it with 1.06.  Anyway, it keeps coming up with hardware BSOD errors (IRQ).  Will this "fix" it?

- CH

---

### Post by gerryg001 on 2008-11-08
Perhaps a bit confusing at this point. jflowers referenced another post that used vmware converter to take an existing windows OS into a vmware session, and that has additional requirements on disk matching. I don't know if cement_head or any others have that specific need.

If not, those issues (maybe) shouldn't happen. I have Hardy-64bit 2.6.24-21 with vmware server 116487, and sata drives. Using IDE disks with no extra drivers, I've created several XP machines with no problems. I have also moved an old XP (from vmware workstation) from another machine into this one, and all are working. My method was consistent with what was given in this thread. The only issue was the rebuild for the Hardy -21 kernel update, and a few new warnings.

While I now have gcc 4.2.4, I'm not sure which version was used for the vmware server rebuild. However, one could easily back up a gcc version if needed. On Randy's post it sounds like something broke earlier, and I'd suggest removing all and starting again. At one point, I was able to do a complete removal and reinstall of vmware server without losing any of the previously installed virtual machines.

Gerry

---

### Post by pwk on 2008-11-18
> **RandyRandola said:**
> VMWare Server 1.0.7
Kernel 2.6.24-21-generic
Fresh install of ubuntu 8.04

Error:
/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no]

Any ideas on a fix?

Thanks!

Randy

I decided to proceed anyway. When I started vmware it gave an error like

~/vmware-server-distrib$ /usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

so I ran

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

and that seems to have it fixed. (Although I haven't had a chance to test it extensively.)

---

### Post by bodhi.zazen on 2008-11-18
> **pwk said:**
> I decided to proceed anyway. When I started vmware it gave an error like

<clip>

so I ran

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

and that seems to have it fixed. (Although I haven't had a chance to test it extensively.)

See setp 5 of the first post on this thread :twisted:

---

### Post by pwk on 2008-11-18
> **bodhi.zazen said:**
> See setp 5 of the first post on this thread :twisted:

Indeed, but we are talking about 1.0.7. Is there any sure fix for the GCC kernel warning about crashing?

---

### Post by bodhi.zazen on 2008-11-18
> **pwk said:**
> Indeed, but we are talking about 1.0.7. Is there any sure fix for the GCC kernel warning about crashing?

I am not completely certain about those errors with 1.0.7, I do not get them when I do a fresh install of 8.10 + fresh install of 1.0.7. So I think the issue occurs when upgrading form 8.04 -> 8.10, but that is a guess on my part.

As to the solution, opinions seem to vary from compiling anyway to making a temporary link for gcc, and again, I am not certain which is better.

---

### Post by pwk on 2008-11-19
> **bodhi.zazen said:**
> I am not completely certain about those errors with 1.0.7, I do not get them when I do a fresh install of 8.10 + fresh install of 1.0.7. So I think the issue occurs when upgrading form 8.04 -> 8.10, but that is a guess on my part.

As to the solution, opinions seem to vary from compiling anyway to making a temporary link for gcc, and again, I am not certain which is better.

Thanks but I'm still using 8.04, I was only upgrading 1.0.6 to 1.0.7.

---

### Post by veloce on 2008-11-19
> **pwk said:**
> Thanks but I'm still using 8.04, I was only upgrading 1.0.6 to 1.0.7.

I used that configuration for a while.  I had ignored the gcc warning and suffered no ill effects.  I had two machines with that set up, an Ubuntu server and a workstation.  The Server has 5 vms running including a win2003 server, two xp, ubuntu and even an opensuse.  No problems on any of them.

(I have now upgraded both machines to 8.10 and vmware server 2 and am very happy with the setup - seems more efficient on resources.)

---

### Post by pwk on 2008-11-20
> **veloce said:**
> I used that configuration for a while.  I had ignored the gcc warning and suffered no ill effects.

OK great, thanks.

---

### Post by redsun82 on 2008-11-23
Hi!

I did not read all the pages of this long thread, so I don't know if it has been pointed out. I would like to point out that while I installed VMware (version 2) I did not have to set a password for root. In fact during the installation (the place in the howto where it is said to select all defaults options) there is a point where it asks you whether to set the default user as administrator (where the dfault is ''). I answered "no", it asked me which user to use, I typed my user name and there you are, at the end I was able to log in the web interface with my usual user and password, without first passing by root.

Good how-to, I'm running Win XP under VMWare without any hassle (though I still have to reboot to try the usb device).

Cheers!

---

### Post by GGITech on 2008-12-10
Epic Fail.

So how do you start 'vmware' when Ubuntu 8.04 Server has not GUI/Web browser?

---

### Post by bodhi.zazen on 2008-12-10
> **GGITech said:**
> Epic Fail.

So how do you start 'vmware' when Ubuntu 8.04 Server has not GUI/Web browser?


VMWare (2.x) installs its own server for http and https access.

What problem are you having ?

What version of VMWare are you using ?

---

### Post by veloce on 2008-12-11
> **GGITech said:**
> Epic Fail.

So how do you start 'vmware' when Ubuntu 8.04 Server has not GUI/Web browser?

You type "vmware" at the prompt.

Then you log onto the server remotely (either web interface for v2 or using the remote console for earlier versions).

This is how most of my vms run.  I'm using v2 on Ubuntu server 8.10.  All the windows vms are accessed using rdp the linux ones using xdmcp.

---

### Post by RealG187 on 2008-12-12
I just noticed something, does VM Ware Server have sound?

---

### Post by gerryg001 on 2008-12-13
Under "Add Hardware" you can add a sound adapter. I'm running Hardy-64 desktop host, VMware server 2, build 122956, with XP, Ubuntu and Fedora sessions, and sound is working. Don't know about Server 1.

---

### Post by RealG187 on 2008-12-14
> **gerryg001 said:**
> Under "Add Hardware" you can add a sound adapter. I'm running Hardy-64 desktop host, VMware server 2, build 122956, with XP, Ubuntu and Fedora sessions, and sound is working. Don't know about Server 1.

I say I have connected the hardware and it searched and can't find anyting and then asks me to select from a list, what do I select?

I have 1.0.6 build-91891

---

### Post by heiNey on 2009-01-01
...

---

### Post by vgrisham on 2009-01-11
Is there a way to have my vmware hosted operating system (vista) reside on a second internal hard drive?

---

### Post by supremedalek on 2009-01-11
I am going here based on my experience with 1.X. In it, I had no problem running my vmware clients in a different directory. In my case, I created a lvm partition, /export. and put all my clients under /export/hosts. Then, it is just a matter of telling vmware where those machines are. 

If you have already created the machine, just move it to the new location while it is off and then edit the path to it under the vmware console. If you are concerned vmware will have a cow when the console starts and it can't see the vista machine, copy it preserving all attributes to the new location and then change its directory.

i can produce screen captures if needed. :D

---

### Post by vgrisham on 2009-01-11
Thanks for the quick reply. No, I haven't already installed vmware, so I've got nothing to lose on this end.

I did install vmware last year, but my Home directory filled up after installing Vista, so I deleted the whole shebang and went back to dual boot. I'd rather drop the dual boot setup now and go with Vista in a VM.

---

### Post by spoonernash on 2009-01-11
I think you can have them any where in the file system. I keep them in a partition using reiserfs because my understanding is that is faster at handling large files than ext3. I would be interested in comments about the best file system to use with VMs.

---

### Post by coolspot02@hotmail.com on 2009-01-23
> **xrvjorn said:**
> After much googling about this problem, ...

```
Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  90R2X-Y4R42-2FNF2-zzzzz

/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
The serial number 90R2X-Y4R42-2FNF2-zzzzz is invalid.
```

... I found another VMWare server setup guide, which included an instruction which is missing in the guide in this thread:

```
sudo apt-get install libx11-6 libxtst6 libice-dev libsm-dev libxt6
```
Unfortunately, that only changes the error message into complaining about libXrender.so.something, so that guide is also missing information. Back to the drawing board and some more googling led me to yet another guide with yet another set of libraries to be installed:

```
sudo apt-get install libxrender1 libxt6 libxtst6 libx11-6
```
Alas, that didn't do the trick either. However, combining the two did:

```
sudo apt-get install libxrender1 libxt6 libxtst6 libx11-6 libice-dev libsm-dev
```

So, combining this guide with the two other, I finally got through the installation. Phew... 

I wish that was the end of the problems, but when I attempt the post-install configuration, I can't copy **/usr/lib/libpng12.so.0**, because it's not there. It's apparently used for handling PNG files, so I guess I won't need it in my text-only server environment?




Tried this command along with several other and i still get the 
/usr/lib/vmware/bin/vmware-vmx: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
when the installer starts and it gives a list of all the libraries i get this
libXt.so.6 => not found
libICE.so.6 => not found
libSM.so.6 => not found


i also did the touch command to create the files that it wanted the timestamp for.  I have spent the last 2 weeks trying to get this to work and i am pretty much out of ideas so if anyone has any ideas i would appreciate it

---

### Post by RealG187 on 2009-02-03
> "EVALUATION LICENSES" section.

2.3	Evaluation Product Warranty Disclaimer.  
During the use of the Evaluation Product, 
the limited 90-day warranty referenced in 
Section 7.1 below is not applicable to 
you.  THE EVALUATION PRODUCT IS PROVIDED 
TO YOU "AS IS" WITHOUT WARRANTY OF ANY 
KIND, WHETHER EXPRESS, IMPLIED, STATUTORY, 
OR OTHERWISE.  VMWARE BEARS NO LIABILITY 
FOR ANY DAMAGES RESULTING FROM USE (OR 
ATTEMPTED USE) OF THE EVALUATION PRODUCT 
THROUGH AND AFTER THE EXPIRATION DATE.

2.4	No Support.  VMware has no duty to provide 
support to you during your use of the 
Evaluation Product.

3.	GRANT AND USE RIGHTS FOR SOFTWARE.

3.1	License.  The Software is licensed, not 
sold.  Subject to the terms of this EULA, 
VMware hereby grants you a non-exclusive, 
non-transferable license, without rights 
to sublicense, to use the object code of 
the Software for the purpose as set forth 
in the applicable documentation for the 
Software and to the extent permitted by 
your payment of applicable license fees 
under a VMware approved licensing model 
and/or your Software License Key subject 
to the software product specific terms 
specified in this EULA.  Depending upon 
the model utilized to compute the 
applicable license fees paid by you to use 
the Software (whether per Processor, per 
Virtual Machine, per user, or any other 
VMware approved licensing model), an 
applicable Software License Key may limit 
your usage of the Software accordingly.  
You may use the documentation accompanying 
the Software in connection with permitted 
uses of the Software.  Notwithstanding 
anything to the contrary herein, in the 
event that you have licensed VMware 
Infrastructure - Starter Edition, your 
license to use such Software is restricted 
to a Server that has no more than eight 
gigabytes (8 GB) of physical memory.

3.2	License Limitations.  You may not copy the 
Software except for a reasonable number of 
machine-readable copies of the Software 
for backup or archival purposes and except 
as expressly permitted in this EULA.  You 
may not remove any titles, trademarks or 
trade names, copyright notices, legends, 
or other proprietary markings on the 
Software.  You are not granted any rights 
to any trademarks or service marks of 
VMware.  VMware retains all rights not 
expressly granted to you.

3.3	Restrictions.  You may not (i) sell, 
lease, license, sublicense, distribute or 
otherwise transfer in whole or in part the 
Software or the Software License Key to 
another party; (ii) provide, disclose, 
divulge or make available to, or permit 
use of the Software in whole or in part 
by, any third party (except Designated 
Administrative Access) without VMware's 
prior written consent; or (iii) modify or 
create derivative works based upon the 
Software.  Except to the extent expressly 
permitted by applicable law, and to the 
extent that VMware is not permitted by 
that applicable law to exclude or limit 
the following rights, you may not 
decompile, disassemble, reverse engineer, 
or otherwise attempt to derive source code 
from the Software, in whole or in part.   
You may use the Software to conduct 
internal performance testing and 
benchmarking studies, the results of which 
you (and not unauthorized third parties) 
may publish or publicly disseminate; 
provided that VMware has reviewed and 
approved of the methodology, assumptions 
and other parameters of the study.  Please 
contact VMware at [email]benchmark@vmware.com[/email] to 
request such review.

3.4	GPL Software. You can redistribute and/or 
modify the GPL Software under the terms of 
the GPL.  You may obtain a copy of the 
source code corresponding to the binaries 
for the GPL Software (the "GPL Source 
Files") by downloading the GPL Source 
Files from VMware's Web site at 
[http://www.vmware.com/download/open_source](http://www.vmware.com/download/open_source)
s.html, or by sending a request, with your 
name and address, to VMware at the address 
specified under the heading "Contact 
Information" below, in which case VMware 
will mail a copy of the GPL Source Files 
to you on a CD or equivalent physical 
medium.  This offer to obtain a copy of 
the GPL Source Files is valid for three 
years from the date you acquired this 
Software product.

3.5	VMware Tools.  You may distribute the 
VMware Tools internally within your entity 
provided that (i) you do not modify the 
VMware Tools; (ii) you distribute the 
VMware Tools in object code format only 
and solely in conjunction with, and as 
part of, the Virtual Machine you create 
with the Software and are sharing 
internally; (iii) you do not distribute 
the VMware Tools to any third party; (v)  
you do not use VMware's name, logo or 
trademarks to market the Virtual Machine 
you create with the Software and (vi) you 
agree to indemnify, hold harmless, and 
defend VMware from and against any claims 
or lawsuits, including attorneys' fees, 
that arise or result from the use or 
distribution of the Virtual Machine you 
create.  Notwithstanding the foregoing, 
you may refer to VMware names, logos or 
trademarks to indicate that the Virtual 
Machine you create with the Software are 
compatible with or designed for use with 
the Software.

3.6	Licenses required for third-party 
software.  The Software enables you to run 
multiple instances of third-party guest 
operating systems and application 
programs. You are responsible for 
obtaining any licenses necessary to 
operate any such third-party software, 
including Guest Operating Systems.

3.7	Sample Programs.  The Software may include 
Sample Programs.  You may use and 
distribute Sample Programs under the terms 
set forth in the applicable Sample 
Programs files.  VMware does not provide 
support services for Sample Programs.

3.8	VMware License Programs.  VMware makes 
available VMware License programs (for 
e.g., VMware Academic License, VMTN).  If 
you have received the Software pursuant to 
these VMware License programs, the then-
current terms and conditions posted on 
[http://www.vmware.com](http://www.vmware.com) for that program 
shall apply for use of the products under 
such VMware License programs.

4.	TITLE.  VMware retains all right, title, 
and interest in and to the Software and 
the Software License Key and in all 
related copyrights, trade secrets, 
patents, trademarks, and any other 
intellectual and industrial property and 
proprietary rights, including 
registrations, applications, renewals, and 
extensions of such rights.

5.	SUPPORT AND SUBSCRIPTION SERVICES NOT 
INCLUDED

VMware will not provide any support 
services under this EULA.  This EULA does 
not give you any rights to any updates or 
upgrades to the Software or to any 
extensions or enhancements to the Software 
developed by VMware at any time in the 
future.   VMware may offer support and 
subscription services separately.  If you 
have purchased VMware support and 
subscription services with the Software, 
these services are provided to you under 
the Support Contract Terms and Conditions 
posted on VMware's Web site at  
[http://www.vmware.com/support](http://www.vmware.com/support) and by 
accepting the terms of this EULA you are 
accepting these Support Contract Terms and 
Conditions.  Any supplemental software 
code or related materials that VMware 
provides to you as part of any support and 
subscription services are to be considered 
part of the Software and are subject to 
the terms and conditions of this EULA.  
VMware may use any technical information 
you provide to VMware for any VMware 
business purposes without restriction, 
including for product support and 
development. VMware will not use 
information in a form that personally 
identifies you.

6.	TERMINATION

6.1	Termination.  VMware may terminate this 
EULA immediately and without notice if you 
fail to comply with any term of this EULA.
  
6.2	Effect of Termination.  In the event of 
termination, you must destroy all copies 
of the Software and Software License Key.  
In addition you must remove all copies of 
the Software, including all backup copies, 
from the Server and all computers and 
terminals on which it is installed.  From 
time to time, VMware may change the terms 
of this EULA.  VMware will notify you of 
such change.  Your continued use of the 
Software will indicate your agreement to 
the change.

7.	LIMITED WARRANTY AND LIMITATION OF 
LIABILITY

7.1	Limited Warranty. VMware warrants that the 
media, if any, on which the Software is 
delivered will be free of defects and that 
the Software will substantially conform to 
the description contained in the 
applicable end user documentation in each 
case for a period of 90 days after the 
date of shipment of the Software License 
Key.  EXCEPT FOR THE PRECEDING EXPRESS 
LIMITED WARRANTY, TO THE MAXIMUM EXTENT 
PERMITTED BY APPLICABLE LAW, VMWARE 
PROVIDES THE SOFTWARE WITHOUT ANY 
WARRANTIES OF ANY KIND, EXPRESS, IMPLIED, 
STATUTORY, OR IN ANY OTHER PROVISION OF 
THIS EULA OR COMMUNICATION WITH YOU, AND 
VMWARE SPECIFICALLY DISCLAIMS ANY IMPLIED 
WARRANTIES OF MERCHANTABILITY, FITNESS FOR 
A PARTICULAR PURPOSE, AND NON-
INFRINGEMENT.

7.2	TO THE MAXIMUM EXTENT PERMITTED BY 
APPLICABLE LAW, IN NO EVENT WILL VMWARE BE 
LIABLE FOR ANY LOST PROFITS OR BUSINESS 
OPPORTUNITIES, LOSS OF USE, BUSINESS 
INTERRUPTION, LOSS OF DATA, OR ANY OTHER 
INDIRECT, SPECIAL, INCIDENTAL, OR CONSE-
QUENTIAL DAMAGES UNDER ANY THEORY OF 
LIABILITY, WHETHER BASED IN CONTRACT, 
TORT, NEGLIGENCE, PRODUCT LIABILITY, OR 
OTHERWISE.  BECAUSE SOME JURISDICTIONS DO 
NOT ALLOW THE EXCLUSION OR LIMITATION OF 
LIABILITY FOR CONSEQUENTIAL OR INCIDENTAL 
DAMAGES, THE PRECEDING LIMITATION MAY NOT 
APPLY TO YOU.  VMWARE'S LIABILITY UNDER 
THIS EULA WILL NOT, IN ANY EVENT, EXCEED 
THE LICENSE FEES, IF ANY, PAID BY YOU FOR 
THE SOFTWARE LICENSED TO YOU UNDER THIS 
EULA. THE FOREGOING LIMITATIONS SHALL 
APPLY TO THE MAXIMUM EXTENT PERMITTED BY 
APPLICABLE LAW, REGARDLESS OF WHETHER 
VMWARE HAS BEEN ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGES AND REGARDLESS OF WHETHER 
ANY REMEDY FAILS OF ITS ESSENTIAL PURPOSE. 

8.	GENERAL

8.1    Entire Agreement. This Agreement sets 
forth VMware's entire liability and your 
exclusive remedy with respect to the 
Software and supersedes the terms of any 
purchase orders and any other 
communications or advertising with respect 
to the Software. You acknowledge that this 
Agreement is a complete statement of the 
agreement between you and VMware with 
respect to the Software, and that there 
are no other prior or contemporaneous 
understandings, promises, representations, 
or descriptions with respect to the 
Software.  

8.2	Headings. Headings under this EULA are 
intended only for convenience and shall 
not affect the interpretation of this 
EULA.

8.3	Waiver and Modification.  No failure of 
either party to exercise or enforce any of 
its rights under this EULA will act as a 
waiver of those rights.  This EULA may 
only be modified, or any rights under it 
waived, by a written document executed by 
the party against which it is asserted.

8.4	Severability.  If any provision of this 
EULA is found illegal or unenforceable, it 
will be enforced to the maximum extent 
permissible, and the legality and 
enforceability of the other provisions of 
this EULA will not be affected.

8.5	Governing Law.  This EULA will be governed 
by California law and the United States of 
America, without regard to its choice of 
law principles. The United Nations 
Convention for the International Sale of 
Goods shall not apply.

8.6	Government Restrictions.  You may not 
export or re-export the Software except in 
compliance with the United States Export 
Administration Act and the related rules 
and regulations and similar non-U.S. 
government restrictions, if applicable.  
The Software and accompanying 
documentation are deemed to be "commercial 
computer software" and "commercial 
computer software documentation," 
respectively, pursuant to DFAR 
Section 227.7202 and FAR 
Section 12.212(b), as applicable.  Any 
use, modification, reproduction, release, 
performing, displaying, or disclosing of 
the Software by the U.S. Government shall 
be governed solely by the terms of this 
EULA.

8.7	Contact Information.  If you have any 
questions about this EULA, or if you want 
to contact VMware for any reason, please 
direct all correspondence to: VMware, 
Inc., 3145 Porter Drive, Palo Alto, CA 
94304, United States of America or email 
[email]info@vmware.com[/email].

8.8	Other. VMware and VMTN are trademarks 
and/or registered trademarks of VMware, 
Inc. in the United States and/or various 
jurisdictions.  


9.	SOFTWARE PRODUCT SPECIFIC TERMS AND 
CONDITIONS

In addition to the above, the following 
Software products shall also be subject to the 
following terms and conditions set forth 
below.  In the event of any conflict between 
the following product-specific terms and 
conditions and the preceding sections, the 
product-specific terms and conditions shall 
control.


9.1	VMware Server: 

(a)  Additional Definitions:

"VMware Server Console" is a proprietary 
console component included with the Software.

(b)  Additional License Terms:

VMware grants you a nonexclusive, 
nontransferable license, without rights to 
sublicense, to (i) install or have installed a 
single instance of the Software on a single 
Server, unless permitted by VMware to have a 
single instance of the Software on multiple 
Servers; (ii) use the Software solely for your 
own internal information processing services 
and computing needs in connection with 
permitted uses of the Software, including the 
hosting of computer application-based services 
from a Virtual Machine and provision of such 
services via an internal or external network, 
provided such services may not consist of 
services to a third party that provide 
primarily computing or processing power (such 
as utility computing or grid computing) or any 
computer application-based service that is 
traded, rented, leased or sold on a Virtual 
Machine basis; (iii) use and reproduce the 
VMware Server Console for installation and 
operation on an unlimited number of your own 
internal computers or terminals solely for the 
purpose of accessing the Server on which the 
Software is installed; (iv) internally use and 
reproduce the Redistributable Components to 
create programs that interface with the 
Redistributable Components to manage Virtual 
Machines ("Your Management Programs"); and (v) 
internally use Your Management Programs solely 
for the purpose of managing Virtual Machines 
operated on VMware software products installed 
on your own internal Servers and computers. 
Subject to the above, each copy of the 
Software may not be used by any other person, 
whether or not such person is employed by or 
otherwise associated with your entity.  

Distributing the Software.  If you are 
interested in distributing the Software 
electronically or via internal Web site, CD or 
other media, or are interested in placing a 
VMware provided logo on your printed material, 
please send a request to 
[email]VMware_server_distribution@vmware.com[/email] and we 
will provide you with a copy of our 
distribution agreement for your signature.   





Do you accept? (yes/no) y

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
kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:71:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

mpg@MIKED6:~/VMWare/vmware-server-distrib$ 


Does it work on 8.10? How do you make it work?

---

### Post by RealG187 on 2009-02-06
VM Ware shows up in my applications menu now, but doesn't run, when I get the terminal it says to configure VM Ware. I get this when I do

> mpg@MIKED6:~$ /usr/bin/vmware-config.pl
Please re-run this program as the super user.

Execution aborted.

mpg@MIKED6:~$ sudo /usr/bin/vmware-config.pl
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

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:71:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

mpg@MIKED6:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


---

### Post by veloce on 2009-02-08
> **RealG187 said:**
> VM Ware shows up in my applications menu now, but doesn't run, when I get the terminal it says to configure VM Ware. I get this when I do

You need to patch your vmware-config.pl file to do the install properly.  If you search the forum for the version of vmware you are trying to install and the word "patch" you should find the discussion on where to get the correct patch.

---

### Post by RealG187 on 2009-02-09
I never had to do that before. is it because I am using 8.10, or rathere the newer Linux Kernel it uses?

---

### Post by veloce on 2009-02-10
> **RealG187 said:**
> I never had to do that before. is it because I am using 8.10, or rathere the newer Linux Kernel it uses?

Yes, it is the combination of vmware version and Linux Kernel. 

You could try upgrading to vmware 1.07, but you still may need a patch.

---

### Post by nubie177 on 2009-02-17
> **gauss said:**
> I did this but in the VMWare menu there is no device to select. When I check the Device Manager in the guest WinXP the USB controller is listed, however. But inserting a USB flash drive doesn't register with the guest WinXP. It *does* appear in the host's /proc/bus/usb/devices.

Any ideas on how to debug this?

Thanks.

If Ubuntu host is 64bit:
...edit the file '/etc/init.d/mountdevsubfs.sh' and uncomment the code after line 40 so it reads:
 # Magic to make /proc/bus/usb work
  #
  mkdir -p /dev/bus/usb/.usbfs
  domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
  ln -s .usbfs/devices /dev/bus/usb/devices
  mount --rbind /dev/bus/usb /proc/bus/usb
Execute the script manually to enable the change before a system reboot:
$ sudo /etc/init.d/mountdevsubfs.sh start

[https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085)

---

### Post by diogo_almeida on 2009-02-25
hello!
I have installed vmware server console but i'm with this problem:

~/vmware-server-console-distrib# vmware-server-console
No protocol specified
No protocol specified


can you help me?
Thanks in Advance

---

### Post by bodhi.zazen on 2009-02-25
What version of vmware ?

Usually you start vmware either from the menu or with the command :

```
vmware
```

---

### Post by diogo_almeida on 2009-02-25
i was not sure.. But i have unnistaled and reinstaled and now works.

Thanks :)

---

### Post by RealG187 on 2009-02-27
This tut helped me:

[http://ubuntuforums.org/showthread.php?t=973729](http://ubuntuforums.org/showthread.php?t=973729)

Thanks Bodi.Zazen!

Only problem is it seems to be slow, I am not sure if it's my mind playing tricks on me or if it really is slow...

---

### Post by bodhi.zazen on 2009-02-27
You are most welcome , glad the tutorial worked.

My personal impression was Server 2 was slower. I did not do benchmarks and some people have commented that machines migrated from 1.0.x to 2.y are slower.

Try making a new machine perhaps ?

---

### Post by RealG187 on 2009-02-27
I think it's just booting that takes longer. Not sure if I want to take the time to make a new machine...

---

### Post by ttl_infinity on 2009-03-13
respected learned ones,
im sorry for posting such a big output but i couldnt help but ask you all about my problem. I was religiously following the steps mentioned in earlier pages but at step 4 i received the following output.If you could please tell me what may be wrong i am having my first hand at Linux.
thank you in advance...

tar: vmware-server-distrib/lib/lib/libpam.so.0/security/pam_rps.so: Cannot open: No such file or directory
vmware-server-distrib/lib/lib/libpam.so.0/security/pam_securetty.so
tar: vmware-server-distrib/lib/lib/libpam.so.0/security/pam_securetty.so: Cannot open: No such file or directory
vmware-server-distrib/lib/lib/libpam.so.0/security/pam_shells.so
tar: vmware-server-distrib/lib/lib/libpam.so.0/security/pam_shells.so: Cannot open: No such file or directory
vmware-server-distrib/lib/lib/libpam.so.0/security/pam_stack.so
tar: vmware-server-distrib/lib/lib/libpam.so.0/security/pam_stack.so: Cannot open: No such file or directory

Edit bodhi.zazen : I clipped the output. Please use attachments (attach it a a .txt file) for long output like that.

For everyone else, it was a long list of the same error over and over, same error message , different directory.

---

### Post by ttl_infinity on 2009-03-13
i am using ubuntu 8.04 LTS desktop edition running on AMD athlon(64 bit) processor on an ASUS M2V-TVM board with 1 Gb of RAM.....

---

### Post by bodhi.zazen on 2009-03-14
I clipped your output a bit.

What command did you run exactly and where did you place the vmware tar ?

My guess is you either have a permissions problem (use sudo) or a corrupt archive (tar). Check the md5sum.

---

### Post by ttl_infinity on 2009-03-14
sir
 i followed the steps again and my vmware is up and running like a charm thank you all for the really helpful post.
next i was facing problems with sound and usb not being detected in Windows Xp which i have installed as a guest OS and now that also is solved.If any help required i can post a quick solution but thank you all once again....:D

---

