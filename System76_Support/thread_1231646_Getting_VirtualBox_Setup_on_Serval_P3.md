---
title: "Getting VirtualBox Setup on Serval P3"
date: 2009-08-04
forum: System76 Support
---

### Post by jdmelton on 2009-08-04
I recently installed VirtualBox 1.6.6 on my 2007 Serval P3 running Ubuntu 8.04.3 LTS AMD64 Desktop and want to share my experiences. Please read all of this before doing anything. (Edit: VirtualBox 3.0.4 is the latest as of 2009-08-06 which uses VirtualBox Graphical User Interface 1.6.6.)

Java must be installed for VirtualBox to work. I have OpenJDK 6 on my Serval.


First, read this execellent How-To: [http://maketecheasier.com/how-to-install-windows-in-ubuntu-hardy-with-virtualbox/2008/07/02](http://maketecheasier.com/how-to-install-windows-in-ubuntu-hardy-with-virtualbox/2008/07/02)


Second, get and install VirtualBox:
Download virtualbox_1.6.6-35336_Ubuntu_hardy_amd64.deb from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and install.
Applications -> System Tools -> GDebi Package Installer
A new menu item will be added at Applications-> System Tools -> Sun xVM Virtualbox


Third, enable USB:
Run sudo gedit /etc/init.d/mountdevsubfs.sh and uncomment these lines:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Then run sudo /etc/init.d/mountdevsubfs.sh start


Fourth, follow the How-To listed above to setup your first VM.
I have 2 GB RAM so I chose 512 MB for Memory. I chose a 10240 MB virtual hard disk and a dynamically expanding image. When you get to the part about the Settings options, I recommend that you change some things.

Settings -> General -> Basic
I set the video memory to 32 MB.

Settings -> General -> Advanced
Enable all of the extended features.
Set Boot Order to CDROM then Hard Disk.

Settings -> General -> Advanced
Uncheck Remember Media Mounted at Runtime

Settings -> Hard Disks
This should show the virtual disk you created earlier. I disabled SATA.

Settings CD/DVD-ROM
Enable the correct one for your system. I did not enable passthrough since I do not use Windows for writing CD-ROMs.

Settings -> Floppy
I disabled this since I do not have one.

Settings -> Audio
Select the correct audio driver, controller, and enable audio.
My Serval uses Alsa and AC97.

Settings -> Network
I was confused here intially. The adapter 0 was enabled with PCnet-FAST III and NAT. What this does is communicate with the host OS. I tried to make this harder than it was by trying to set up with my wireless. That was a waste of time. The default worked perfectly with the Ubuntu Linux setup which was already on wireless.

Settings -> Serial Ports
I left this disabled.

Settings -> USB
To add USB devices, click the second icon on the far right (Add Filter From Device). This will show all available USB devices. Click on a device. It will be added. Repeat for all devices. I chose the camera, fingerprint pad, bluetooth, and my USB trackball mouse. Enable USB and the 2.0 controller.

I created a Temp directory in home to share.
mkdir ~/Temp
Settings -> Shared Folders
Click the little icon on the far right (Add a new shared folder).
Folder Path ~/Temp (Enter the full pathname, ie /home/username/Temp)
Folder Name Temp
Click OK to finish.

Settings -> Remote Display
I left this one disabled.

Now go to File -> Preferences -> Input and check Auto capture keyboard. I found that after Windows was installed, it was necessary to disable this on my machine.


Fifth, time to install Windows XP. (Edit: I installed a 32 bit version of Windows XP.)
I used the 2002 Professional disk which already had service pack 2 installed. Insert the CD into the drive and close the Nautilus window if it opens.

You are ready to start the VM. It will boot the CD and you can proceed with the installation.
There were a couple of sticky points for me.

One, the keyboard is only captured when the mouse pointer is over the VM window, but if you click in the window, then it tries to capture the mouse. If it does this, you are stuck and have no easy way to regain conrtrol of your system since the Windows setup does not use a mouse. I did find out later that Fn+SysRq would release the mouse and keyboard, but not all of my machines have function keys like the laptop does.

Two, the VM window jumps around while booting and installing. Very annoying.

Three, the install will take a while and due to the mouse/keyboard capture ugliness, I ended up doing nothing else until the install completed.


Sixth, once Windows is installed, it is time to fix the mouse/keybord capture ugliness and add the shared folder.

Shutdown the VM.
VM window -> Machine -> ACPI Shutdown

Mouse and other goodies:
Applications-> System Tools -> Sun xVM Virtualbox
Help -> Contents -> The VirtualBox Guest Additions -> Windows Guest Additions
There are instructions on how to get this working, look for Windows Guest Additions.

Keyboard:
Applications-> System Tools -> Sun xVM Virtualbox -> File -> Preferences -> Input
Uncheck the Auto capture keyboard

Start the VM.
Start Windows Explorer and expand My Network Places, then Entire Network, and finally VirtualBox Shared Folders.
In my case, there was \\VBOXSVR\Temp
I mapped it as a network drive z.


Seventh, after I did all of this, I shutdown the laptop then rebooted, started the VM, and performed the numberous updates.


---> I hope this helps someone else. The basic install went smoothly, but the mouse and keyboard auto captures did not work intuitively and it took some searching around to find answers. I have a limited need for Windows XP and decided this could better than carrying around 2 laptops. There is a lot of useful information in the VirtualBox Help. I suggest you give it a read.

---

### Post by thomasaaron on 2009-08-05
Thanks, jdmelton.

Good tutorial. I'll definitely point people towards it if they inquire. The only thing I would recommend is, *if* you end up having any problems that seem like they might be java related, downloads Sun's java...

sudo apt-get install sun-java6-jre
sudo update-alternatives --configure java #and select Sun's java

Open JDK isn't 100%, and I occasionally run into issues with it, particularly with 3rd party software.

---

### Post by jeamer on 2009-08-05
Hey,

Great writeup. However, my experience with Virtualbox is that capture/uncapture is easily controlled (right from initial boot, even before OS install) with right-Ctrl, the "host-key". Also, the host key can easily be changed to whatever you like, Fn key or not, through the same thread that you unchecked "Auto-capture Keyboard". I dunno, I found it pretty intuitive.

And, STOKED on the seamless desktop. If anyone's dual-booting out there, you have to ask yourself why... the seamless desktop is awesome (check out the screenshot).

---

### Post by samalex on 2009-08-05
[QUOTE="jdmelton"]I recently installed VirtualBox 1.6.6 on my 2007 Serval P3 running Ubuntu 8.04.3 LTS AMD64 Desktop and want to share my experiences. Please read all of this before doing anything.[/QUOTE]

When my laptop arrives (it's in transit now), one of my first projects is setting-up Windows through VirtualBox for the apps I use at work.  My question though is why did you run with VirtualBox 1.6.6 when 3.0.4 is the latest build?

Just curious... Thanks,

Sam

---

### Post by Scotty Bones on 2009-08-05
> **jdmelton said:**
> Third, enable USB:
Run sudo gedit /etc/init.d/mountdevsubfs.sh and uncomment these lines:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Then run sudo /etc/init.d/mountdevsubfs.sh start


Just to note: This method of enabling USB in Intrepid and beyond is now depreciated. (and maybe even in Hardy if using a current version, I'm not sure on that though)

The current method can be found in the user manual. 
Chapter 11 Troubleshooting
11.5.7 USB not working (p.151)

You can pick-up the current version of VirtualBox  and the manual here:
[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

---

### Post by jdmelton on 2009-08-06
thomasaaron,

Thanks for the tip about OpenSunJDK. I will keep that in mind for the future is I run into problems. It is simple to install the Sun version.


jeamer,

I 'thought' that the auto capture seemed intuitively obvious. However, on my Serval P3 (purchased in December 2007) the Windows XP virtual machine would not receive keyboard inputs after the first reboot of the Serval itself. The right control key did not work for some reason even though the mouse was over the virtual machine window and the window was active. (Perhaps this was due to my use of OpenJDK 6?) The only way I got it to work again was a post from sdennie in this thread:
[http://ubuntuforums.org/showthread.php?t=775395](http://ubuntuforums.org/showthread.php?t=775395)
where the recommendation was to turn off the keyboard auto capture. That is not intuitive to me, at least. I am not sure why unchecking this feature works. I found some web references and a bug report, but no answers for 'why'. I do use SCIM and the second reference below has an entry by hugh_h_chen about this. I ran into the same problem as the original post (in the second reference below) which prompted my notes under the fifth part.
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/217364](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/217364)
[http://www.uluga.ubuntuforums.org/showthread.php?p=4937819](http://www.uluga.ubuntuforums.org/showthread.php?p=4937819)


samalex,

OOPs, I did download and install verison 3.0.4. When I wanted the version, I went to the Help -> About VirtulBox menu. I saw Version 1.6.6 there. After reading your post, I looked again, and now I see that this is for the VirtualBox Graphical User Interface. I will edit the first post to reflect this.


Scotty Bones,

I saw that, but my /etc/init.d/mountkernfs.sh (Ubuntu 8.04.3 LTS AMD64) does not contain the line 'domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev'. I have not used 9.04 yet, but will give it a try when my Meerkat arrives. I found these web references:
[http://www.blog.arun-prabha.com/2007/10/26/usb-not-working-with-virtualbox-in-ubuntu-7-10-gutsy-gibbon/](http://www.blog.arun-prabha.com/2007/10/26/usb-not-working-with-virtualbox-in-ubuntu-7-10-gutsy-gibbon/)
[http://forums.virtualbox.org/viewtopic.php?p=21294](http://forums.virtualbox.org/viewtopic.php?p=21294)
[http://ubuntuforums.org/showthread.php?t=341740](http://ubuntuforums.org/showthread.php?t=341740)
[http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy](http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy)
I thought that the process for adding a group was too convoluted for my taste in 8.04.3.


Thanks to everyone for the constructive comments.

---

