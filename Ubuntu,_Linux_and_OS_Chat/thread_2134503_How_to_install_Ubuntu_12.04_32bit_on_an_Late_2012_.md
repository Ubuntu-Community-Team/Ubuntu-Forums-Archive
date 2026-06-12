---
title: "How to install Ubuntu 12.04 32bit on an Late 2012 iMac using VirtualBox"
date: 2013-04-11
forum: Ubuntu, Linux and OS Chat
---

### Post by perrya on 2013-04-11
Hi,

I'm running the following;

New 27" Apple iMac i7 3.4GHz 8GB 1TB 7200 RPM 2012 THIN 2GB 680MX

And I just spent the last two days trying out VirtualBox and after a few rough starts it works fantastic. I can't imagine how well it'll work on a SSD drive that I'll pick up a little while later.

Here is what you do;

Download and install VirtualBox for OS X follow instructions to do that.

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Download a iso 32 bit version of Ubuntu 12.04 (do not get the 64 bit version, do not get 12.10)

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Once installed VirtualBox creates a directory VirtualBOX VMs off my home directory

Run VirtualBox and use this page as a guide, however there are a few changes from what he does that you need to do to get it working properly;

[http://www.tuaw.com/2009/09/07/how-to-set-up-ubuntu-linux-on-a-mac-its-easy-and-free/](http://www.tuaw.com/2009/09/07/how-to-set-up-ubuntu-linux-on-a-mac-its-easy-and-free/)

Study what he did BUT pay attention to the changes I did to get it working smoothly.

Step 1: Click the New icon, type in the name of the Ubuntu iso; ubuntu-12.04.2-desktop-i386

Step 2: Set yourself about 2 GB of memory, anything less than that is pointless. Your Linux will be slowed down significantly due to the Linux swap file.

Step 3: Create a virtual hard drive of about 20 GB FIXED SIZE, this will greatly reduce the lag you'd experience using Dynamically Allocated virtual disk.

Step 4: Change the Display to say 128 MB and enable 3D Acceleration

Step 5: Change the Storage to where the Ubuntu 12.04 iso is located

Step 6: Change the System Boot Order to Hard Disk, CD/DVD-ROM, no Floppy

Step 7: Hit the Start icon

Step 8: Inside the VM select Install Ubuntu

Step 9: Click Download updates while installing & Install this third-party software

Step 10: Answer questions asked by the dialogs to suit your fancy and click Continue (hopefully your mouse does not dissappear while trying to do this, if it does, guess your way around it) (recommend you select Log On Automatically)

Step 11: Ubuntu will finishing it's install and say you need to Restart then after you hit Restart it'll hang on a terminal screen. When this happens click on Machine->Reset (Host+R), it'll continue it's reboot.

Step 12: Now when Ubuntu 12.04 reboots it'll GO NUTS cause the xorg driver is out of wack. What you do here is go into Terminal mode by pressing CTRL-ALT-F1 or Fn-CTRL-ALT-F1, if F1 does not work try F2 F3 F4. You should end up with a terminal signon to Ubuntu.

Step 13: Sign in using the username and password you supplied during setup.

Step 14: Once inside issue the following commands;

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install dkms
sudo reboot

Step 15: At this point Ubuntu reboots and you are presented with either a sign on screen or your straight into Ubuntu this time with a working GUI.

YOUR NOT DONE YET

Step 16: In your Applications folder find VirtualBox and select Show Package Contents, Contents->MacOS inside that folder there is a iso called VBoxGuestAdditions.iso, find it and copy to where ever you put your Ubuntu iso file. 

Step 17: In VirtualBox select Storage and change the CD/DVD to point to VBoxGuestAdditions.iso 

Step 18: When you clicked Ok on VirtualBox a prompt should have come up in Ubuntu to automatically run the VBoxGuestAdditions.iso, click Run enter your password and wait.

(If you didn't get a prompt, open a Terminal box and cd /media you'll see the VBoxGuestAdditions.iso directory, click into the directory you see there and look for a VBoxGuestAdditions.run, issue this command sudo sh ./VBoxGuestAdditions.run  )

Restart Ubuntu

YOUR NOT DONE YET

Step 20: You should not be presented with a smoothly running Ubuntu 12.04 installation, test the browser, it should come up ALMOST as fast as if it were natively installed.

Step 21: Go to this website and add a bunch of extras to your installation

[http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/](http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/)

You should be great shape after that.

I've just spent the last two days testing out my brand new iMac and VirtualBox with Ubuntu and anything less than what I've shown you here will give you poor performance. I can't wait to test all this out with the new SSD drives, if you got a Fusion drive then you should be seeing wicked results.

I've got a 8GB system at the moment but even still, it runs Ubuntu with stuff like SecondLife in the back with no more effort than running Safari. Check the Activity Monitor you will see. Plan on upgrading your memory however for more than 8GB for practical uses.

Also, it's a good idea to keep your iMac defragged for stuff like this. Check out iDefrag for on this.

[http://www.coriolis-systems.com/iDefrag.php](http://www.coriolis-systems.com/iDefrag.php)

Also, be sure to check VirtualBox Devices for sharing Clipboard and Drag & Drop. I can get it to drag a zip file into Ubuntu but can't do it the other way. It clipboards text just fine however.

Report back here with any questions and how you made out.

Good Luck !
 :wink:

---

### Post by perrya on 2013-04-11
I have to say I am absolutely thrilled at the performance of Ubuntu inside VirtualBox. Other than not doing 3D applications (which is not why I installed in on the iMac) it performs absolutely beautifully. I only wish I could provide a demonstration.

---

### Post by gpaCook on 2013-05-09
Perrya,
I just ordered a 2012 27" iMac, and planned to try UbuntuStudio as a VirtualBox guest.  I have no experience with Mac or Ubuntu, so was really appreciative of your very extensive post. I will attempt to follow it when I get my imac.  I have a couple questions, tho:
1- Why use the 32-bit version, and not 64-bit?
2- Why use the back-level version?

Thanks

---

