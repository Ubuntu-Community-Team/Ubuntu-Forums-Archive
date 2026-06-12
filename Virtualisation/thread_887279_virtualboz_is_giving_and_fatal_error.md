---
title: "virtualboz is giving and fatal error"
date: 2008-08-12
forum: Virtualisation
---

### Post by jkid on 2008-08-12
first thing fist i dont really know how to use virtualbox do i need a cd iso to start it or not ...........and the error that it give me it says [COLOR="Red"]FATAL NO BOOTABLE MEDIUM FOUND ! SYSTEM HALTED[/COLOR]                                                         






HERE IS A SCREENSHOT[ATTACH]81217[/ATTACH]

---

### Post by chronographer on 2008-08-12
Did you create a virtual disk image for the virtual machine? If you did then maybe it is saying there is nothing installed on there and you need to boot a XP or Ubuntu cd in there to install on the virtual mechine.

THis is the howto [http://www.debianadmin.com/create-virtual-machines-using-virtualbox-in-debian.html](http://www.debianadmin.com/create-virtual-machines-using-virtualbox-in-debian.html) I used a while ago, and it has been wroking practically ever since. Also check out the Virtualbox manual which is available from their website.

---

### Post by jkid on 2008-08-12
ok i dont thinks that because i just did what you told me and nothing happen...

---

### Post by OutOfReach on 2008-08-12
Click on the Settings button, then click on CD/DVD-ROM, enable 'Mount CD/DVD Drive' if you are planning to boot from an ISO file click on the ISO Image File tickbox and click on the little browse button on the side, click the 'Add' button on the dialog that comes up and browse to were the ISO file is and click OK, then click Select. If you want it to boot from your physical CD/DVD-ROM drive just select the 'Host CD/DVD Drive', apply the settings by clicking ok and try starting up the virtual machine again.

Hope that helps.

---

### Post by overdrank on 2008-08-12
Moved to Virtualization :)

---

