---
title: "JOJ (Jaunty On Jaunty) or How to optimize a VirtualBox Linux guest"
date: 2009-05-18
forum: Virtualisation
---

### Post by tkoco on 2009-05-18
Some background info:

My quest for knowledge started with a desire to get an old Loki Linux game, Railroad Tycoon 2, up and running on my 64 bit system. I was familar with QEMU, however, the automated configuration of a Xorg server made it next to impossible to get a 1024 by 768 screen in the virtual monitor of a QEMU machine. Not wishing to pursue an unknown amount of time and research to fix this issue, I looked into VirtualBox. All posts, which I read, stated that this method of virtualization was ready for prime time. 

My machine is a 64 bit Dual core system running Jaunty 9.04 x84_64.
Concerning the VirtualBox software, I used the Synaptic Package Manager to install 'virtualbox-2.2', the Sun non-free version as the setup of guest machines appears to be better documented.

Since the Loki game was created prior to the availability of 64 bit systems, I decided to create a 32 bit Jaunty guest machine to run on top of my Jaunty 64 bit machine. Many 'virtual machines' were created before finding the right combination of parameters which eliminated sluggishness in the guest machine.

The nitty gritty info:

1) On your host machine, you will need -

To be running Jaunty (as the pulseaudio server is finally fixed and you will need the pulseaudio server running on the host machine)

A copy of 32 bit Jaunty -> ubuntu-9.04-desktop-i386.iso

To install gkrellm via Synaptic Package Manager. Gkrellm will allow you to monitor the CPU usage while you optimize the Linux guest machine later on.

2) In VirtualBox, you will need to create a new machine. The built-in wizard is very good. You can get more information on creating a new guest machine here [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

Now you have a new machine, these next few steps are very important. If you don't get the settings of the new Ubuntu guest machine just right, the process of building up the guest will be a long torturous process as it will be sluggish.

Highlight the new machine in the VirtualBox Control Panel and click on the Settings button.

3) General area (Left panel)
      General Tab: Maximize the Video memory. If this setting is too low, the guest machine will be sluggish.
      Advanced Tab: ONLY enable the 'ACPI'. Disable all other Extended features. Change the IDE Controller Type to 'ICH6'.

4) Hard Disks (Left panel)
      Click on Enable Additional Controller. Leave the type on 'SATA'. Click in the area under the Slot button and set the slot to 'SATA port 0'.

5) CD/DVD-ROM (Left Panel)
      Click on Mount CD/DVD Drive. Then Click on ISO Image File. Click on the button to the right of the text and the Virtual Media Manager will pull up. Within the Manager panel, Click on Add and browse for the Jaunty ISO file mentioned earlier. Once you add the ISO image to the Media list, highlight the file and Click on Select.

6) Audio (left Panel)
      Click on Enable Audio. Make sure that the Host Audio Driver is set to 'pulseaudio'. Make sure the Audio Controller is NOT set to SB16. The SB16 setting absolutely does not work with Jaunty.

Then just Click on OK.

7) Click on 'Start' and "install" Jaunty onto the guest virtual machine. At the end of the installation when you reach the point of having to eject the media, just kill the machine (the X in the upper right corner of the window).

8 ) Click on the Settings button, highlight CD/DVD-ROM in the left panel. Change the ISO Image File to the 'VBoxGuestAdditions.iso' file and click on OK. Click on Start and boot the guest machine.

In the Ubuntu Linux enviroment running on the VirtualBox guest, the ISO image will be mounted on the '/media/cdrom' directory. It should also show on the virtual desktop. Open a terminal window and run 
```
sudo sh /media/cdrom/VBoxLinuxAdditions-x86.run
```Restart the Ubuntu guest Machine.

Let's put the Ubuntu guest machine on a diet. The standard load of Ubuntu software includes many programs which are not needed by the guest machine. On the Host machine, start up gkrellm and move the gkrellm window out of the way of the virtual Ubuntu guest. You will be monitoring CPU usage on gkrellm. As you do each round of trimming, restart the guest machine and note how much faster it becomes.

First Phase:  Start with the system services. You need to disable any service not needed. (System -> Administration -> Services)
I disabled the ATD, Crash Reports, Bluetooth, Braille, Power Management (apmd), Printer Service, and Remote Backup.

Second Phase: Disable unneeded programs which are started with each session. (System -> Preferences -> Startup Applications)
I disabled the AT SPI, Bluetooth, Evolution Alarm, Indicator Applet, Print Queue Applet, Remote Desktop, Seahorse Daemon, Update Notifier, User Folders update, and Visual Assistance.

FYI Note: Before you start with this next phase, with the guest machine shutdown, make a snapshot of the guest machine in the VirtualBox Control Panel. That way, if you disable something vital, you can backup and recover your guest machine.
In a terminal window in the Guest Machine, do this ```
ps ax
``` and carefully note what programs are running. Ask yourself if you really need that program running. If you are not sure, do a google on the process name. I found out the 'gvfsd-burn' process is the one invoked when you insert a blank CDR/DVD+R(W) disk into a CDR/DVD burner drive. If you do not plan on using a 'burner' in the guest machine, then use Synaptic to remove all burner software. Then 'gvfsd-burn' will disappear on reboot and the guest machine will run a bit snappier.

And leads us to ...

Third Phase: Remove unneeded programs using Synaptic Package Manager. When you select a package for removal, make sure the dependency list (if there is one) does not have some program which you do need. If that happens, then just cancel the request. Again, keep in mind that you can always add the program to the guest machine via Synaptic.

Additionally, you do not need pulseaudio running on your Ubuntu guest machine. My Ubuntu guest machine is running strictly ALSA sound. However, the host machine must have pulseaudio running for smooth operation.

---

### Post by tkoco on 2010-11-21
Just a tip for everyone,  To get the Loki games up and running, you will need to load the "libgtk1.2" package. You will find that the newest releases for Ubuntu lack that library. Thus, it might be a good idea to keep some of the older ISO images around, like Hardy Heron (8.04 LTS) i386 desktop as an example.

---

