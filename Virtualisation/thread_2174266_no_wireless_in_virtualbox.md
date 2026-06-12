---
title: "no wireless in virtualbox"
date: 2013-09-13
forum: Virtualisation
---

### Post by david98 on 2013-09-13
hi im running ubuntu 12,04 and trying to use backtrack 5 r3 through the virtual box but i cant seem to detect my wireless card. got no problems getting wireless on the same edition of back track which i have installed on a partition. any ideas what i could try to fix this little problem

---

### Post by david98 on 2013-09-14
solved got hel on another forum

---

### Post by TheFu on 2013-09-16
> **david98 said:**
> hi im running ubuntu 12,04 and trying to use backtrack 5 r3 through the virtual box but i cant seem to detect my wireless card. got no problems getting wireless on the same edition of back track which i have installed on a partition. any ideas what i could try to fix this little problem

David98, 
It is great that you found a solution, but could you post what you did here please?  This community only works because we help each other out.

For any lurkers ... the devices shown inside a VM are usually "virtual" and have NOTHING to do with your real hardware.  The only way to get "some" access to hardware is though a USB passthru ... and that is really meant for flash drives and external HDDs, though some other devices probably work well too.   I would not expect a USB-wifi adapter to work using the USB passthru of any virtual machine.  That isn't to say that other devices will not work, they may.

BTW, BackTrack has been replaced by a different distro ... like 9 months ago - maybe over a year now. [Kali]("http://www.offensive-security.com/offsec/backtrack-reborn-kali-linux/") is what all the DC folks use.  It will include the latest available versions of all the tools, BT is basically dead.

---

