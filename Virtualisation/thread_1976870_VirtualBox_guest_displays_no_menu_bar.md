---
title: "VirtualBox guest displays no menu bar"
date: 2012-05-09
forum: Virtualisation
---

### Post by Goat Anti Rabbit on 2012-05-09
Dear all,


I have  a problem installing guest additions in virtualbox. My host is ubuntu 10.04 and the guest I try to run is Windows 7. 
I have googled a lot, but never found a solution to my problem. When I saw this thread [solved] I thought that my problem would be solved because this seems to be exactly the problem I have. Nevertheless I do not manage to solve it.

So the problem is: the window in which my guest is running, doesn't display any menu. So I have no "devices" menu where I can select "Install guest additions" at all. 

I know where I can find the guest additions .iso file on my host, but there seems to be no way to get it into my virtual machine, since guest additions have to be installed for shared folders to be accessible from inside the VM. 

Any help would be very much appreciated!
Thanks a lot!

---

### Post by Darth Matthias on 2012-07-03
I would like to know as well. I use VirtualBox 4.1.2. I have been using my Ubuntu One account to move schoolwork from guest to host, but that is a royal pain in the but. I have I am running Ubuntu 11.10 now. I was origionally running 12.04 when I ran into this problem, and thought that they were related, but I have the same problem here too.

---

### Post by QIII on 2012-07-03
If you are using Ubuntu with Unity, the menu will not be on the application window itself.

Generally, the menu bar for the active window will be in the top bar that says "Ubuntu Desktop" at the left side.  If you hover your cursor just to right of that, the active window's application menu will appear.

---

### Post by cipherboy_loc on 2012-07-03
Also, the guest additions, being an iso, are meant to be shown to the guest OS as being a CD/DVD and not as the .iso through a shared storage option. If you cannot get the menu to work, select the guest OS in the virtual box manager, press settings, select storage, and click the image of the CD/DVD in the storage tree box. On the right under attributes to the right of the drop down, click the image of the CD/DVD, and select choose a virtual CD/DVD disk file. Navigate to where you downloaded the iso to (below), and double click it. Hit okay on the previous screen, and start the vbox image. 

Download the guest additions here, selecting the folder of your current version.
[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)


Cipherboy

---

### Post by QIII on 2012-07-03
Using the Devices menu item and selecting "Install Guest Additions" is all that is needed.  There is no need for the nut roll of any more downloading.

When Guest Additions is installed that way, and the guest shut down and restarted, the Guest Additions image will be available and the script (or .exe for Windows guests) can be run from that media.

---

### Post by cipherboy_loc on 2012-07-03
Yes. I offered this option because he was having issues finding the menu.

---

### Post by QIII on 2012-07-04
In my estimation, two objectives presented themselves:

Understanding the Unity interface and learning how to install the Guest Additions.

I think the latter is a fish and the former is a pole.  I thought instruction in the use of the pole would be more generally useful.

---

### Post by Darth Matthias on 2012-09-05
Thank you. Got this working just fine. Now am running a 32-bit XP guest on a 12.04 64bit system. This Rocks!!

---

