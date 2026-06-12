---
title: "Virtualbox + Ubuntu Host + Windows XP Guest Hangs All the Time"
date: 2007-11-10
forum: Virtualisation
---

### Post by mlapaglia on 2007-11-10
I installed virtualbox, and then stuck windows xp pro on their, the host is gutsy 7.10.

during the install, when it boots up, and when im using windows it will freeze, and the only way to make it unfreeze is to hit "ctrl" to move my mouse back to ubuntu. when windows freezes, so does ubuntu, nothing responds unless i press some keys on the keyboard or move my mouse.

any suggestions?

---

### Post by Nano Geek on 2007-11-10
Could you run Virtualbox in the command line, and output what it says?

---

### Post by mlapaglia on 2007-11-10
hmm, that's a little strange..



~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found

i installed it with a .deb i downloaded from their site.
i'm running gutsy

i installed virtualbox-ose and now i get this

"
Could not load the settings file '/home/mlapaglia/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'LogHistoryCount' is not declared for element 'SystemProperties'
Location: '/home/mlapaglia/.VirtualBox/VirtualBox.xml', line 27, column 159.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

 "

i went in and deleted the whole folder, and now i get to the regular screen when i run the command prompt, im gonna reinstall windows now.

maybe it was an older version or something?

---

### Post by mlapaglia on 2007-11-10
ok it's working fine now. lesson learned, used synaptic, not .deb files ;).

thanks for getting the ball rolling in my head :)

---

### Post by Nano Geek on 2007-11-10
Sure thing. :KS

P.S. For some strange reason, you have to run 'VirtualBox' instead of 'virtualbox'. I have no idea why they did that though.

---

### Post by saadabbasi.iba on 2008-05-11
> **mlapaglia said:**
> ok it's working fine now. lesson learned, used synaptic, not .deb files ;).

thanks for getting the ball rolling in my head :)

hey there. dude i also installed virtual box from the .deb and windows xp pro sp2 install is freezing. it freezes everytime in the setup i reach the point where the setup asks u to select partition to install xp to. 

i was wonderin if u could guide me how to install it from synaptics, cuz in your post here u said installing it from synaptics solved ur porblems.

---

### Post by Ameneon on 2008-05-11
While I installed from the deb as well (and it worked fine for me) installing it through synaptic is trivial. Go to system-administration-synaptic package manager, then search for virtualbox. Select the edition you wish to install and click 'apply' to install it..

---

### Post by hugh_h_chen on 2008-05-12
i had the same problem, and my fix was that this is due to my SCIM input method is chinese. some of you may be using non english scim input method. check my post here for the fix. 

it worked find for me so far.

[http://www.uluga.ubuntuforums.org/showthread.php?p=4937819#post4937819](http://www.uluga.ubuntuforums.org/showthread.php?p=4937819#post4937819)

---

