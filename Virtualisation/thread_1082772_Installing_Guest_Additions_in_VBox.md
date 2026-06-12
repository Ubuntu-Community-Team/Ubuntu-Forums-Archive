---
title: "Installing Guest Additions in VBox"
date: 2009-02-28
forum: Virtualisation
---

### Post by Universal344 on 2009-02-28
So I downloaded the latest alpha release of Ubuntu 9.04 and have successfully installed and updated it.  Now I want to install guest additions.  When I click "install guest additions" under the devices menu it correctly mounts the media and I get an autorun prompt asking if I want to run the software.  When I click run, however, I get an error saying "Cannot find the autorun program."  Am I going about this the wrong way?  Any help would be appreciated.

---

### Post by Therion on 2009-02-28
That's the usual method, but try this instead, since that isn't working for you.  

Open your VM, go to "My Computer" and double-click on the CD icon. This should launch the wizard to install Guest Additions.

Follow the wizard, accept the license, ignore the unsigned driver warnings, etc. At the end, reboot the virtual machine.

---

### Post by Universal344 on 2009-03-01
When I double click the on the disk it open the contents in a folder instead of running.  Could I try running it through the command line?  If so, what exactly is the command?

---

### Post by kelvin spratt on 2009-03-01
the easy way is to move the file you need to your home folder this is for 32bt 
VBoxLinuxAdditions-x86.run then open a terminal
                                                            kelvin@kelvin-desktop:~$ cd /home/kelvin/  
 kelvin@kelvin-desktop:~$ sudo sh VBoxLinuxAdditions-x86.run  
 [sudo] password for kelvin:  
 Verifying archive integrity... All good.  
 Uncompressing VirtualBox 2.1.4 Guest Additions for Linux installation........................................................................................................................................................................................................... 
 VirtualBox 2.1.4 Guest Additions installation  
 Building the VirtualBox Guest Additions kernel module...  
 Building the shared folder support kernel module...  
 Installing the VirtualBox Guest Additions...  
 

 Successfully installed the VirtualBox Guest Additions.  
 You must restart your guest system in order to complete the installation.  
 kelvin@kelvin-desktop:~$  
 This is how i just did it remember this is for 32bit

---

### Post by HotShotDJ on 2009-03-01
I don't think Guest Additions are available for Jaunty guests yet.

---

### Post by bodhi.zazen on 2009-03-01
Follow kelvin spratt's directions.

And yes, the Additions work on 9.04 Alpha (I have it running in VirtualBox on a Fedora Host, no problem).

---

### Post by HotShotDJ on 2009-03-01
> **bodhi.zazen said:**
> And yes, the Additions work on 9.04 Alpha (I have it running in VirtualBox on a Fedora Host, no problem).Excellent!

---

### Post by Universal344 on 2009-03-03
I successfully installed guest additions but whenever I go to hardware drivers in the VM it shows that the VBox drivers are deprecated (more specifically the sets module).  Is this a security concern?

---

### Post by Rafzepersian on 2009-03-04
NEED HELP WITH 3 ISSUES in VBOX

HOST: UBUNTU 8.10
GUEST: XP SP2

VBOX installed fine in ubuntu, guest additions installed fine in xp. Only 2 problems lurking me!

1) Everytime I start off VBOX to go to XP , it boots into XP and the resolution is extremely poor and its always in 8bit color, so I figured out that disabling the VBOX default driver for display adapter in device manager (requires a restart in xp) puts back a good resolution and good color. But it doesn't go fullscreen (it comes in 4:3 ratio after reboot), then I go to device manager again to enable VBOX driver for display adapter, this time it puts back the 16:9 ratio, nicely fitting my 10" laptop's screen with perfect 32bit color. (HP MINI 1000). How can I keep these settings instead of having to keep doing the above procedure everytime I start xp on vbox?

2) How do I use the internet in XP via VBOX??? eth0 is my wireless card on ubuntu, and I enabled it in the vbox settings, but Virtual xp seems not to see it. It tries to establish a connection but keeps saying a cable is unplugged every 10 seconds) 

3) How do I share the usb ports??? I've enabled usb in the settings, but seems like virtual xp doesn't even see the usb ports.


Any help will be greatly appreciated. Thanks for helping a noob. 

-Rafique

---

### Post by Dedoimedo on 2009-03-04
Hello,

See if this helps:
[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

Dedoimedo

---

### Post by FraggedLocust on 2009-03-04
I installed Virtualbox and the guest utilities through synaptic (the OSE version). Is this the same thing? How do I enable the additions?

---

### Post by jimmybarcelona on 2009-03-12
I have succesfully installed the guest additions on the guest windows xp. running ubuntu 8.10 as a host. I cannot get the xp guest to capture my touchpad. I've installed it, and restarted machine, but it still won't capture. any ideaa?

   A note, the download would not work for me within virtualbox, the download kept timing out. I had to manually download the iso on my host machine and then manually mount the iso on my guest machine.

---

