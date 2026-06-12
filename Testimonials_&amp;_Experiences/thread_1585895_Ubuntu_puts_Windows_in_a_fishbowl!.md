---
title: "Ubuntu puts Windows in a fishbowl!"
date: 2010-10-01
forum: Testimonials &amp; Experiences
---

### Post by ventrical on 2010-10-01
It is just amazing how Virtual Box OSE 'lifted the veil' off of Windows XP fresh install and a popular Anti-Virus program.

  Virtual Box allows you to see the tiny little flea circus that goes on behind the scenes. It's really frustrating , knowing how much time I have spent studying Windows from a Windows perspective and not from an Ubuntu perspective.

 It's is also very disappointing that this sort of pinball game is still going on with new releases of Windows.

Yep.. the truth hurts.

Fool me once, shame on you. Fool me twice , shame on me.

---

### Post by ubun2warrior on 2010-10-01
hi

i have installed xp through vbox ose.. i am using ubuntu 10.04. can u tell me how to access my pendrive in xp which is running in vbox??

regards
ubun2warrior

---

### Post by UKBB on 2010-10-01
> **ubun2warrior said:**
> hi

i have installed xp through vbox ose.. i am using ubuntu 10.04. can u tell me how to access my pendrive in xp which is running in vbox??

regards
ubun2warrior

You need to run the PUEL version of Vbox.

---

### Post by ventrical on 2010-10-01
> **ubun2warrior said:**
> hi

i have installed xp through vbox ose.. i am using ubuntu 10.04. can u tell me how to access my pendrive in xp which is running in vbox??

regards
ubun2warrior

The Dell Opti GX270 I am working on with the VBox XP install was struck by lighting a month ago  and blew out the USB and ethernet (but is still working).

  I plan to do a clean install of Ubuntu 10.4 on my Sony Vaio and install XP on VBox in that PC so I will get back to you.

  If your system in using an HDD then I would think that you would have to dismount the penDrive before you ran VirtualBox and then install it from there. Since my USB ports are fried I cannot give you any reliable documentation at this time.

  If you are running Ubuntu 10.4 from a persistve penddrive than that would be tough to dismount your OS but it may be worth a try (experiment) at your own risk.

  I'll get back to you after I have installed VBox on my Sony.

Thanks for your reply.

---

### Post by ventrical on 2010-10-01
There are <system> settings tab in the VBox OSE panel. By default  the two Serial Ports are not enabled. There is also an option to put in your own <user_defined> port:hex adress which should allow you to pipe FROM Ubuntu to Windows Install in VBox. The only USB option (so far) is to install a USB mouse tablet but using that option will not allow VBox Windows to recognize the USB pendrive. 

If you find the port address for USB first .. let me know :)

---

### Post by ventrical on 2010-10-01
We have to download the closed source version.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads).

 The OSE version does not allow for USB to be enabled.

---

### Post by 3rdalbum on 2010-10-02
If it's just a pen drive then you don't need low level access to it. You could tell Virtualbox to have a "shared folder" that is actually the folder where the drive is mounted. Then, whenever the drive is mounted on Ubuntu, the Windows guest will see it as a network share and you can read and write it.

---

### Post by ventrical on 2010-10-02
I think you got it. I just got to get the path and folder name correct . :)

  I put in    /media/<and then some number and letters> that said what the drive was but it didn't work yet.
  But I could see the pendrive light flashing when I loaded up windows in VBOX.

---

### Post by ventrical on 2010-10-07
Just a followup on the pen-drive issue.

Check out the screen shot.

The trick is to have the flash-drive inserted.Then, go to settings in VBox, double click USB then hold your mouse over the add icon folder and the menubar will  give you the option to install the mass storage from host. Then, when you run XP in VBox it will recognize the pendrive pronto.

cheers :)

---

### Post by Elfy on 2010-10-08
This is not the place for support. Closed.

---

