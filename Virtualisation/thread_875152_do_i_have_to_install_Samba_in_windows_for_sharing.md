---
title: "do i have to install Samba in windows for sharing?"
date: 2008-07-30
forum: Virtualisation
---

### Post by eival on 2008-07-30
i already have it installed in ubuntu but i still couldnt share, so i thought i perhaps had to download in windows too, but i dont see a windows version of Samba to download.

what am i doing wrong? or what should i do instead


Ubuntu 8.04 is my main OS with Windows XP throug VM

EDIT:nevermind i found a walkthrough
[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

---

### Post by Keithel on 2008-07-30
You don't need samba for windows.  Samba is just an implementation of the SMB filesharing API that Microsoft uses in it's folder sharing.

Just make sure you have your workgroup in Samba (on the host Ubuntu side) set to the same workgroup in your XP guest VM, and that on the XP side, you have some folders shared out (right click the folder, choose Sharing, configure sharing via the window that pops up).

---

### Post by eival on 2008-07-30
> **Keithel said:**
> You don't need samba for windows.  Samba is just an implementation of the SMB filesharing API that Microsoft uses in it's folder sharing.

Just make sure you have your workgroup in Samba (on the host Ubuntu side) set to the same workgroup in your XP guest VM, and that on the XP side, you have some folders shared out (right click the folder, choose Sharing, configure sharing via the window that pops up).

alright imma try this, cause it sounds alot less complicated than the walkthrough i just posted, lolz:popcorn:

---

### Post by eival on 2008-07-30
alright i got it all working, thanks to Keithel for trying to help me, but i needed more than just your info, but i appreciate it.

how ever i followed that walkthrough i posted an it worked fine using the NAT connection. i highly recommend it to anyone else that has trouble.

---

