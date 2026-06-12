---
title: "Leapfrog Connect"
date: 2011-09-22
forum: Tutorials
---

### Post by (Nes) on 2011-09-22
Getting Leapfrog Connect to work on Ubuntu took a bit of finagling, but if you don't go the long way (like I did) it's pretty easy to do.

First of all, Wine will not work for Leapfrog Connect. (Trust me, I **tried!!**)

Step One: Download [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") from the website NOT the Ubuntu software centre 
(different version, only website works with USB).

Step Two: To install you must open a terminal
 > cd (directory)
sudo dpkg -i fillename.debwhere instead of (directory) you just use the name of the folder you've got it downloaded into, in my case it would be 

> cd Downloads
sudo dpkg -i virtualbox-4.1_4.1.2-73507~Ubuntu~natty_i386.debLet it install.

Step Three: Set up virtual box, this is really easy, just follow the prompts. You do need a working version of Windows to install on the virtual box. 
Make coffee while Windows installs itself. (I used Vista, leapfrog works with 7/Vista/Xp)

Step Four: Download [Oracle VirtualBox Extensions]("http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html") that will open in your virtualbox Windows.

Step Five: Open up Users & Groups > Manage Groups > VirtualBox > Properties. Check your username.
Log on & off to make the change.

Step Six: Open up your virtualbox, navigate on the right side of the window to "USB" click the picture of the USB with the bluedot to add an empty filter (or usb spot).

Step Seven: Run windows, download [Leapfrog Connect]("http://www.leapfrog.com/en/pages/support.html") for windows, install as normal. You're going to need update Adobe Flash, but it'll prompt you to do that.

And it should be working!!! I really hope I didn't miss anything.
Now that you don't have to spend 3 weeks figure out how to fix this on your own, it shouldn't take more then an hour to set up. 

Leapfrog Tag is a great product, my 3 year old just LOVES his to bits, and "reads" to his little brother every night. Be aware, when you sign up for the software, they ask for the parents first & last name, and then ask for your kids first name. Now they have your kids full name part of the software is designed to give you feedback on how your child is "learning". So you may want to consider your/children's privacy when signing up for your account.

---

### Post by nadamsieee on 2013-01-01
I have this working with the "out-of-the-box" VirtualBox 4.1.12 that "ships" with Ubuntu 12.04 LTS running a Windows XP virtual machine.

Step One: Install VirtualBox:
```
sudo apt-get install virtualbox virtualbox-dkms virtualbox-fuse virtualbox-guest-additions virtualbox-guest-dkms virtualbox-guest-additions-iso virtualbox-guest-utils virtualbox-guest-x11 virtualbox-ose virtualbox-ose-dkms virtualbox-ose-fuse virtualbox-ose-guest-dkms virtualbox-ose-guest-utils virtualbox-ose-guest-x11 virtualbox-ose-qt virtualbox-qt
```

Step Two: Install Windows XP as a virtual machine inside VirtualBox...

Step Three: Plug in the LeapFrog device (e.g. "MyPal Violet").

Step Four: Select Windows XP in the Oracle VM VirtualBox Manager and then scroll down and click on USB.

Step Five: Click the USB icon with the green plus sign, and then select the LeapFrog device from the list. Click OK.

Step Six: Start-up the Windows XP virtual machine and install the LeapFrog software. Proceed as normal from here.

---

