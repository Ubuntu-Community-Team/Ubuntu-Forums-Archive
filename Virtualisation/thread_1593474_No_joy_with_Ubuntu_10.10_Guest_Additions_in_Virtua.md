---
title: "No joy with Ubuntu 10.10 Guest Additions in VirtualBox"
date: 2010-10-11
forum: Virtualisation
---

### Post by nlsthzn on 2010-10-11
Currently running Ubuntu 10.04 and I wanted to run Ubuntu 10.10 under VirtualBox but I am unable to get the Guest Additions to work (I did try "sudo apt-get install virtualbox-ose-guest-x11" and it didn't work)...

I even tried removing the OSE version and getting the latest one from the Oracle web site but still the same problem persists and I cannot get my displays resolution higher than 800x600... any other ideas?


Thanks
Neil

---

### Post by nlsthzn on 2010-10-11
Currently running Ubuntu 10.04 and I wanted to run Ubuntu 10.10 under VirtualBox but I am unable to get the Guest Additions to work (I did try "sudo apt-get install virtualbox-ose-guest-x11" and it didn't work)...

I even tried removing the OSE version and getting the latest one from the Oracle web site but still the same problem persists and I cannot get my displays resolution higher than 800x600... any other ideas?


Thanks
Neil

---

### Post by nlsthzn on 2010-10-11
Currently running Ubuntu 10.04 and I wanted to run Ubuntu 10.10 under VirtualBox but I am unable to get the Guest Additions to work (I did try "sudo apt-get install virtualbox-ose-guest-x11" and it didn't work)...

I even tried removing the OSE version and getting the latest one from the Oracle web site but still the same problem persists and I cannot get my displays resolution higher than 800x600... any other ideas?


Thanks
Neil

---

### Post by Morbius1 on 2010-10-11
All I can do is tell you how I resolved this issue:

_ PLEASE NOTE THIS WAS ALL DONE FROM WITHIN THE UBUNTU 10.10 GUEST AND NOT THE HOST:_

(1) I downloaded to my Downloads folder the latest testing Guest Additions from here:

[http://www.virtualbox.org/download/testcase/VBoxGuestAdditions_3.2.9-66155.iso](http://www.virtualbox.org/download/testcase/VBoxGuestAdditions_3.2.9-66155.iso)

(2) Then extracted the iso by double clicking it

(3) Then ran the VBoxLinuxAddition..run file:

```
cd /home/morbius/Downloads
``````
sudo sh VBoxLinuxAdditions-x86.run
```If your guest screen becomes distorted just let it run for about 10 minutes. You will eventually have to do a forced shutdown of the guest but upon reboot ( of the guest ) you'll have your guest additions installed correctly with the right video driver.

---

### Post by cariboo on 2010-10-11
Merged by request. :)

---

### Post by nlsthzn on 2010-10-11
> **Morbius1 said:**
> All I can do is tell you how I resolved this issue:

_ PLEASE NOTE THIS WAS ALL DONE FROM WITHIN THE UBUNTU 10.10 GUEST AND NOT THE HOST:_

(1) I downloaded to my Downloads folder the latest testing Guest Additions from here:

[http://www.virtualbox.org/download/testcase/VBoxGuestAdditions_3.2.9-66155.iso](http://www.virtualbox.org/download/testcase/VBoxGuestAdditions_3.2.9-66155.iso)

(2) Then extracted the iso by double clicking it

(3) Then ran the VBoxLinuxAddition..run file:

```
cd /home/morbius/Downloads
``````
sudo sh VBoxLinuxAdditions-x86.run
```If your guest screen becomes distorted just let it run for about 10 minutes. You will eventually have to do a forced shutdown of the guest but upon reboot ( of the guest ) you'll have your guest additions installed correctly with the right video driver.

Will be trying it out ASAP!

> **cariboo907 said:**
> Merged by request. :)

Thanks... not sure what went wrong there :confused:

---

### Post by nlsthzn on 2010-10-11
Just a heads up that Morbius1's solution worked for me too... 

Thanks!!
Neil

---

### Post by JustinR on 2010-10-11
> **nlsthzn said:**
> Just a heads up that Morbius1's solution worked for me too... 

Thanks!!
Neil

Hi,

You had to install the guest additions and then, in ***the guest Ubuntu***, install:
```

sudo apt-get install virtualbox-ose-guest-x11

```
. Morbius1's solution did not work for me.

---

### Post by khaki54 on 2010-10-11
OK--
So my problem was even more severe in that X wouldn't even start.  If that's the case you will need to do the below commands.  Also I couldn't copy and paste anything (since the guest additions are not working) so make sure you use tab completion in steps 2,4,5,6.

1. Login as root if you have a root password set.

Many novice users probably don't have a root password set so you will need to do a ```
sudo su -
```to become root after you login as your superuser.

2. ```
umount /media/cdrom0
```If this returns a "nothing to unmount" that's fine

3. ```
wget http://www.virtualbox.org/download/testcase/VBoxGuestAdditions_3.2.9-66155.iso
```case sensitive

4.```
mount -o loop VBoxGuestAdditions_3.2.9-66155.iso /media/cdrom0
```5. ```
cd /media/cdrom0
```6. ```
sh ./VBoxLinuxAdditions-amd64.run 
```if you use the x86_32 version of linux you will need to
```
sh ./VBoxLinuxAdditions-x86.run 
``` instead

Boom headshot -- good luck

---

### Post by ACanuck on 2010-10-12
New Virtualbox(3.2.10) was released today. Upgrading that then trying again did the trick for me.

edit:
Though visual effects won't work(normally they work fine), but oh well.

---

### Post by nlsthzn on 2010-10-12
Thanks to all the solutions listed... hopefully there is at least one solution here for all others struggling with this :D

---

### Post by Morbius1 on 2010-10-12
Although I haven't tested it myself it appears the ACanuck has the ultimate answer:

VBox 3.2.10 Changelog:
```
Additions/X.Org: support X.Org Server 1.9 (bug [#7306]("http://www.virtualbox.org/ticket/7306")) 
```Bug 7306:
> Ubuntu 10.10 (pre-beta now) switched to X.org 1.9.0 RC 5, it would be nice if Virtualbox drivers are updated to support it. 

---

### Post by Jive Turkey on 2010-10-12
For me, using the latest virtualbox (3.2.8) and the guest additions iso linked above had the corrupted screen mentioned above, I left it alone for a few min.  When I came back it was just a solid purple screen.  I pressed ctrl+F2 to get a shell and ran "sudo service gdm restart" and boom! gravy!

Thanks to all for the solution.

---

### Post by glx57318 on 2010-10-18
> **JustinR said:**
> 
You had to install the guest additions and then, in ***the guest Ubuntu***, install:
```

sudo apt-get install virtualbox-ose-guest-x11

```. Morbius1's solution did not work for me.

hi,
i had trouble installing additions on VB 3.2.6; updated VB to 3.2.10 and was able to install additions fine from iso provided in the download (with strange visual effects during install mentioned by Morbius1). yet, after installation, X server wouldnt start at all, so i followed JustinR footsteps. works fine, now.
regards,
galaxy

---

