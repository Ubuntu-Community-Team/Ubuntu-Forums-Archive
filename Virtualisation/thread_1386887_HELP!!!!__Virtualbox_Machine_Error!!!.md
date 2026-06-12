---
title: "HELP!!!!  Virtualbox Machine Error!!!"
date: 2010-01-21
forum: Virtualisation
---

### Post by bdws1975 on 2010-01-21
Hi all,

I am using virtual box running windows for some work programs.

I closed down my Vbox machine but didn't close the virtualbox box where you open the machine.

when I tried to open it up again, I got this:

the machine is inaccessible

 p, li { white-space: pre-wrap; }  Start tag expected, '<' not found.
 Location: '/home/brett/.VirtualBox/Machines/Work/Work.xml', line 1 (0), column 1.
 /home/vbox/vbox-3.1.2/src/VBox/Main/MachineImpl.cpp[5821] (nsresult Machine::loadSettings(bool)).
    Result Code: 
  [FONT= ]NS_ERROR_FAILURE (0x80004005)[/FONT]
   Component: 
  VirtualBox
   Interface: 
  IVirtualBox {2158464a-f706-414b-a8c4-fb589dfc6b62}


Please tell me how to solve it in simple terms.

thanks!!!!

brett

---

### Post by fouadatmeh on 2010-01-21
Hello,
It seems that the configuration file where the machine settings are stored is screwd up..
The easiest thing to try is to create a new machine whith the same settings as the one not working; but when it asks for creating a new harddrive, select use an existing image and select the image for your virtual machine's harddisk (probably work.vdi)..

---

### Post by bdws1975 on 2010-01-21
dude!  you're my fricking hero!!!!

I read on some other threads how you have to jump through hoops, clone this, convert that....and MAYBE get it back.

I'm all back up and running and am a happy camper.

Thanks again!

brett

---

### Post by fouadatmeh on 2010-01-22
Glad to have been of help :)

---

