---
title: "Ubuntu server for VirtualBox"
date: 2007-11-18
forum: Virtualisation
---

### Post by self-defence on 2007-11-18
Hi,

I've got a server running Ubuntu 6.06 but no GUI and I would like to be able to run a virtual system. And since the hardware is quite good and the work load is very low I could run different systems on the VirtualBox. But can this be done without a GUI?
I can put a few more network cards in the server so that the virtual system would have their own connection.
I figured out that I could install the system via my system in a GUI and then copy the files to another system. Would that work?
Or can it be done another way?
And how can I get the virtual system running on the server without the GUI? If I try VirtualBox console commands it always opens a GUI.
And I saw that I can cross mount some folders or something to share files between systems?
And how could I mount the VirtualBox disk image on my system?

Thanks for all the help and a nice day to all.

---

### Post by UbuWu on 2007-11-18
If you want to run ubuntu on them it might be easier to setup some thin clients using ubuntu's ltsp.

---

### Post by Lem on 2007-11-18
Download the manual and look at VBox VRDP. You can use this to run remote sessions.

The VRDP server is pretty cool as you can reboot the machine and not lose contact.
The downsides with VBox over VMWare Server for this are that;

There is no GUI for remote management.
The reboot/hibernate buttons are not disabled as per regular RDP

The best solution in my opinion is VMware server with RDP running on Windows clients and NX on Linux.

However, if you plan to run Linux clients only, use LTSP. It's far easier to setup and uses considerably less overheads.

---

### Post by self-defence on 2007-11-18
No no, I would like to install test systems, and systems that run different tasks on the virtual machines. Also I could have different systems for different networks which would really make my life easier because I can configure a server for let's say the student's development web server. And an online web server for the main website.... But I've only got one server that I can use. So I'd like to run  virtual systems on this server since the work load on it is low. The system is Ubuntu 6.06 and I've been able to install VirtualBox via command line. But I'm still not sure on how if I can run systems in the background without a GUI running.

Thanks for the input UbuWu anyway.

---

### Post by bodhi.zazen on 2007-11-19
> **self-defence said:**
> Hi,

I've got a server running Ubuntu 6.06 but no GUI and I would like to be able to run a virtual system. And since the hardware is quite good and the work load is very low I could run different systems on the VirtualBox. But can this be done without a GUI?
I can put a few more network cards in the server so that the virtual system would have their own connection.
I figured out that I could install the system via my system in a GUI and then copy the files to another system. Would that work?
Or can it be done another way?
And how can I get the virtual system running on the server without the GUI? If I try VirtualBox console commands it always opens a GUI.
And I saw that I can cross mount some folders or something to share files between systems?
And how could I mount the VirtualBox disk image on my system?

Thanks for all the help and a nice day to all.

OpenVZ is an ideal solution for this.

---

### Post by self-defence on 2007-11-22
Lem -> Thank you I got it working. I can even copy the existing systems that I've got on my pc. Then I just run the virtual system and connect to it via rdesktop.

bodhi.zazen -> Thanks. I had a quick look and I'll have a more detail look at it this weekend. :)

Now the only thing I have to figure out is how to start all the VMs that I need at the time the server starts. I'll probably try to do something with a scrip that's run at startup. It should work.

So thanks for the help and if I screw something up I'll check back. ;)

---

### Post by jocampo on 2009-07-30
Hi self-defence

Years or months later :-) ... I'm facing same challenge. And thanks to the marvelous of Internet and Forum, found your thread. 

I would like to install VirtualBox on an Ubuntu headless server (no Gnome or GUI on it) but run the VMs from my Ubuntu desktop laptop (which uses a Gnome/GUI)

How can I accomplish this, especially, the VirtualBox installation with no Gnome. The servers is running like a charm and connected to Internet.

Any help is appreciated!

---

### Post by ericab on 2009-07-30
> **jocampo said:**
> Hi self-defence

Years or months later :-) ... I'm facing same challenge. And thanks to the marvelous of Internet and Forum, found your thread. 

I would like to install VirtualBox on an Ubuntu headless server (no Gnome or GUI on it) but run the VMs from my Ubuntu desktop laptop (which uses a Gnome/GUI)

How can I accomplish this, especially, the VirtualBox installation with no Gnome. The servers is running like a charm and connected to Internet.

Any help is appreciated!

its easier then you think.
install virtualbox on your headless system through ssh (make sure it installs dkms as a suggested package)
reboot your pc

once back up, refer to this chart i wrote up for my own use on my headless virtualbox host, which i refer to every time i want to create a virtual system. just copy and paste.
you may need to modify some of the options, which can be viewed by typing "VBoxManage modifyvm" and it will show you a list of option types. enjoy.
oh and remember, the items within < and > need to be added by YOU. dont leave it as it is. also, there are locations that need to be changed to fit your own iso locations... just read through it, youll see. 
oh and you probabally will want to change the amount of ram you dedicate to your VM; i have mine set at 4 gigs... (i have 8 gigs in my server) :P
also as mentioned earlier in this thread... download the manual (pdf)

###########################

1.	CREATE

CREATE VM (Creation of VM):

VBoxManage createvm --name <name-of-vm> --ostype <ostype> (use "VBoxManage list ostypes" for a possible list of guest types) --register


###########################

2.	CONFIG

MODIFY VM (Setup Options) For INITIAL INSTALL, OR LIVE CDs:

VBoxManage modifyvm <name-of-vm> --memory 4024MB --boot1 dvd --boot2 disk --clipboard bidirectional --acpi on --cpus 1 --hwvirtex on --nestedpaging on --vram 12MB --accelerate3d off --vrdp on --vrdpport 3390 --idecontroller PIIX4 --dvd /home/eric/Win-Dls/<iso-name>.iso --floppy disabled --audio none --nic1 bridged --bridgeadapter1 eth0 --nictype1 Am79C973 --cableconnected1 on --usb off


###########################

3.	CREATE HARD-DISK

CREATE HD (Virtual Disk Image)

VBoxManage createhd --filename /home/eric/.VirtualBox/<vdi-image-name>.vdi --size <size-of-vdi-in-megabytes> --register


###########################

4A.	ADD THE CREATED HARD-DISK TO VM (From Step 3)

REGISTER TO VM (VDI)

VBoxManage modifyvm <name-of-vm> -hda '/home/eric/.VirtualBox/<vdi-image-name>.vdi'


###########################

4B.	INSTALL IF *NESSESSARY* (Stop here, if you are only running a live CD)

###########################

5.	CONFIG

MODIFY VM - For BOOTING FORM HARDDRIVE FIRST (Step 2 set the DVD as the first boot device, now we set it back to the Harddrive), & DVD SECOND (DVD HAS GUEST ADDITIONS attached. download the guest additions iso and modify location to fit your needs.):

VBoxManage modifyvm <name-of-vm> --memory 4024MB --boot1 disk --boot2 dvd --clipboard bidirectional --acpi on --cpus 1 --hwvirtex on --nestedpaging on --vram 12MB --accelerate3d off --vrdp on --vrdpport 3390 --idecontroller PIIX4 --dvd /home/eric/.VirtualBox/GuestAdditions/VBoxGuestAdditions_3.0.0.iso --floppy disabled --audio none --nic1 bridged --bridgeadapter1 eth0 --nictype1 Am79C973 --cableconnected1 on --usb off


###########################

6.	** STARTING THE VM **

START

VBoxHeadless -startvm <name-of-vm> &


###########################

7.	** POWERING OFF THE VM (NOTE this is a FORCEFUL Poweroff. Dont use unless you absolutley need too. Normally you will power the guest OS off from with in itself)**

VBoxManage controlvm <name-of-vm> poweroff

###########################

---

### Post by jocampo on 2009-07-30
ericab:

Thanks so much, that helps a lot! 
Just one quick question and it's regarding the VirtualBox installation (on the Ubuntu headless server) I found this guide, is basically what you're pointing, right?

[http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/]("http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/")

Looks like is the process I must follow via console in order to setup VirtualBox

---

### Post by ericab on 2009-07-30
yeah that guide should do just fine.

---

### Post by bodhi.zazen on 2009-07-30
[ericab]("http://ubuntuforums.org/member.php?u=238079") : Thank you for such a detailed response, it is helpful.

I would add that the Virtualbox manual is a very nice document and as such is a great resource for detailed information of this kind.

[User Manual]("http://download.virtualbox.org/virtualbox/3.0.2/UserManual.pdf")

---

### Post by jocampo on 2009-07-30
> **bodhi.zazen said:**
> [ericab]("http://ubuntuforums.org/member.php?u=238079") : Thank you for such a detailed response, it is helpful.

I would add that the Virtualbox manual is a very nice document and as such is a great resource for detailed information of this kind.

[User Manual]("http://download.virtualbox.org/virtualbox/3.0.2/UserManual.pdf")

Thanks!

I love this forum...I love UBUNTU :-) ... 
For this particular topic/thread, I would point people to chapter 7, which is highly related...but the whole manual is a great aid

---

### Post by jocampo on 2009-08-01
ericab / folks

Well, I finally installed :-) and it's running like a charm but, it was not so easy as expected. I found some difficulties. 

The 1st one was that following the tutorial I found, I tried to install VBox 3.0 but at some point it asked me to recompile; I did that but setup gave me an error saying service won't start until I change or upgrade my Linux Headers. Well, I did that ... and still, VirtualBox refused to start. During that process, something really weird happened, my account lost its "sudo" powers. Yeah, how? I have no idea. That was after change the Ubuntu Server Linux Headers.

So, I decided to wipe out everything (is a fresh server installation) and start from zero again. This time I downloaded a lower version, 2.3 I think and setup did not complain about anything. I created machines, attached ISO files, etc and was able to connect via rdp ... but ... there was a weird problem with mouse; the pointer was not in sync with my laptop (the position) so clicking something inside the VM was an acrobatic task. I fixed it with VirtualBox additions but when I try to resize the guest window, problem is there again. So, I deleted and recreate the VM using the ISO file and this time I did not resize the window. Looks ok so far.

I wonder is there is some kind of bug between VirtualBox 3.0 and Ubuntu Sever Jaunty edition. It just does not work for me and complain about the kernel.

---

### Post by CharlesA on 2011-11-18
Back to sleep thread...

---

