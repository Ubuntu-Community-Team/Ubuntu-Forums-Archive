---
title: "Trying to update Virtualbox on 14.04"
date: 2014-11-15
forum: Virtualisation
---

### Post by sparky741pa on 2014-11-15
Hello all!  I have been using Virtualbox 4.3.10, with the extension pack, and running Win XP SP3.  I havent't had any issues until recently when I tried to copy some files from a USB stick into Windows and it would not see the drive.  After reading what I could find, it looks as though I need to update Virtualbox so I can install the newer extension pack, which then should allow me to get to the thumb drive on my windows install.  I found many pages that give instructions on adding the PPA to the sources.list file as well as adding the authorization key, which I have done and to the best of my knowledge, is correct.  I know the latest version available is 4.3.18, but Virtualbox does not update for whatever reason when I download any other updates.  Is there a way to force it manually?  Is there anything else I should check?  Thanks for any help. :)

---

### Post by kostkon on 2014-11-15
What's the output of
```
apt-cache policy virtualbox-4.3
```
It should be like this
```
:~$ apt-cache policy virtualbox-4.3
virtualbox-4.3:
  Installed: 4.3.18-96516~Ubuntu~precise
  Candidate: 4.3.18-96516~Ubuntu~precise
  Version table:
 *** 4.3.18-96516~Ubuntu~precise 0
        500 http://download.virtualbox.org/virtualbox/debian/ precise/contrib i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by sparky741pa on 2014-11-16
Hello!  This is the out put I get:

```
virtualbox-4.3:  Installed: (none)
  Candidate: 4.3.18-96516~Ubuntu~raring
  Version table:
     4.3.18-96516~Ubuntu~raring 0
        500 http://download.virtualbox.org/virtualbox/debian/ trusty/contrib amd64 Packages

```

Not sure why it says I have none installed. I have 4.3.10 which I use frequently.  When I open the Ubuntu Software Center, it shows up as installed there as well.  Any ideas on how to fix?

---

### Post by pqwoerituytrueiwoq on 2014-11-16
for Virtualbox on 14.04 this is the extension pack
[http://download.virtualbox.org/virtualbox/4.3.10/Oracle_VM_VirtualBox_Extension_Pack-4.3.10-93012.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.10/Oracle_VM_VirtualBox_Extension_Pack-4.3.10-93012.vbox-extpack)
i have used this for getting USB gamepads to work in VB

you can just network your /media/username folder as a share drive in virtualbox

you can pull the virtualbox from utopic

---

### Post by sparky741pa on 2014-11-16
> **pqwoerituytrueiwoq said:**
> for Virtualbox on 14.04 this is the extension pack
[http://download.virtualbox.org/virtualbox/4.3.10/Oracle_VM_VirtualBox_Extension_Pack-4.3.10-93012.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.10/Oracle_VM_VirtualBox_Extension_Pack-4.3.10-93012.vbox-extpack)

you can just network your /media/username folder as a share drive in virtualbox

you can pull the virtualbox from utopic

Not sure I'm following you.  I already have the extension pack for 4.3.10.  I need to update Virtualbox so I can use the newer extension pack in order to use my thumb drive in my Windows install.

---

### Post by pqwoerituytrueiwoq on 2014-11-16
[[img]http://www.zimagez.com/miniature/screenshot-11162014-035508pm.php[/img]](http://www.zimagez.com/zimage/screenshot-11162014-035508pm.php)
then google how to add virtualbox shared drive on windows
then dam if your flash drive is mounted in ubuntu you will be able to access it via windows
[[img]http://www.zimagez.com/miniature/screenshot-11162014-035809pm.php[/img]](http://www.zimagez.com/zimage/screenshot-11162014-035809pm.php)

---

### Post by kostkon on 2014-11-16
> **sparky741pa said:**
> Hello!  This is the out put I get:

```
virtualbox-4.3:  Installed: (none)
  Candidate: 4.3.18-96516~Ubuntu~raring
  Version table:
     4.3.18-96516~Ubuntu~raring 0
        500 http://download.virtualbox.org/virtualbox/debian/ trusty/contrib amd64 Packages

```

Not sure why it says I have none installed. I have 4.3.10 which I use frequently.  When I open the Ubuntu Software Center, it shows up as installed there as well.  Any ideas on how to fix?
You are using the version from the ubuntu repos. If you want the latest (from the virtualbox repos), you need to install the virtualbox-4.3 package.

---

### Post by sparky741pa on 2014-11-17
> **kostkon said:**
> You are using the version from the ubuntu repos. If you want the latest (from the virtualbox repos), you need to install the virtualbox-4.3 package.

OK, great. Thank you for your assitance.  I'm still learning commands and such, so do I need to remove the version I have before installing the other version?  What would the terminal commands be that I need to do this?  Thanks again for your help.

---

### Post by pqwoerituytrueiwoq on 2014-11-18
```
sudo apt-get remove virtualbox-4.3 virtualbox-guest-additions-iso
sudo apt-get install virtualbox-4.3 virtualbox-guest-additions-iso
```
i did tell you how to get your flashdrive working with your existing virtualbox install though

---

### Post by sparky741pa on 2014-11-18
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get remove virtualbox-4.3 virtualbox-guest-additions-iso
sudo apt-get install virtualbox-4.3 virtualbox-guest-additions-iso
```
i did tell you how to get your flashdrive working with your existing virtualbox install though

Yes, yes, you did and I thank you for that. I tried it and got it to work the way you show, but ultimately, my goal is to update to the latest version.

---

### Post by pqwoerituytrueiwoq on 2014-12-04
So i installed Virtualbox 4.3.18 (from vivid repos) on my system (xubuntu 14.04)
i installed it and upgraded the guest addons and the usb extension
windows cant find a driver for the flash drive

EDIT:
had to enable usb2 xhci under settings in VB

---

