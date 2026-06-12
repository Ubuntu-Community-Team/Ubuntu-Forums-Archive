---
title: "HALP! Internal Error - Failed to initialize HAL, for Ubuntu v7.10 in VM"
date: 2008-07-17
forum: Virtualisation
---

### Post by xdanelx on 2008-07-17
I have an installation of Ubuntu v7.10 in a VMWare environment.  I have set it up to run our helpdesk system out of. Recently, after trying to change a few config settings for the helpdesk, and possibly some updates for Ubuntu, I restarted the entire lot. Now it won't come back on... :confused:

Some errors I am getting were:
1. GUI would now come up. I've got this part solved by following some package reconfiguration for gdm.

2. However, when I'm trying to load in recovery mode, it is showing that certain groups (i.e. audio) did not exist, or does not have permission.  Once, Ubuntu comes up, a message box saying "Internal Error - failed to initialize HAL!" comes up.

3. I cannot connect to the network, the CD, not even to an iso file I'm trying to load.  So basically, I have not idea how to get data in or out of it.

4. I'm trying to access MySql on it and that is not working either.

5. There are 13 updates pending on Ubuntu.  However, since I can't connect to the network, I can't complete this. I've read that it may be a possible cause but I can't find someway to remove those.

So there. Now I'm stuck and don't know what else to do. I'm not a Liunux person and have used because it was easy to install. This has basically put me off as I can easily fix Windows issues but Ubuntu is just beyond my ken.

Can anyone advise?  Ask away if more information is needed to assist.  Thanks.

---

### Post by mgol on 2008-12-04
I just got the same problem in Intrepid running in VirtualBox (not OSE) running in Intrepid... OS was running OK for most of the time and after one of restarts it happened and now appears every time... I can do nothing in GDM, only in tty1-tty6 terminals...

---

