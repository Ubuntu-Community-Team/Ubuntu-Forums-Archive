---
title: "Guest can't detect USB"
date: 2014-09-16
forum: Virtualisation
---

### Post by satimis on 2014-09-16
Hi all,

host	Ubuntu 12.04 64bit
guest	Win7
Oracle VirtualBox
Epson Perfection 3490 photo scanner

I have encountered the problem making Win7 to detect the scanner and tried several days without a solution.  I found;
VirtualBox doesn't recognize USB [duplicate]
[http://askubuntu.com/questions/140081/virtualbox-doesnt-recognize-usb](http://askubuntu.com/questions/140081/virtualbox-doesnt-recognize-usb)

According to #22
I have installed gnome-system-tools on the host

$ groups satimis```

satimis : satimis adm cdrom dip plugdev scanner lpadmin sambashare

```

Please help.  Thanks in advance.

Regards
satimis

---

### Post by ian-weisser on 2014-09-17
Older versions of Virtualbox, like the version of 4.1 used in 12.04, cannot see USB. The workaround was to install the Oracle version of VB instead of the Ubuntu version of VB.

Newer versions, like 4.3 used in 14.04 can see USB without any workaround.

---

### Post by satimis on 2014-09-17
> **ian-weisser said:**
> Older versions of Virtualbox, like the version of 4.1 used in 12.04, cannot see USB. The workaround was to install the Oracle version of VB instead of the Ubuntu version of VB.

Newer versions, like 4.3 used in 14.04 can see USB without any workaround.
Hi,

Thanks for your advice.

My version was download on VirtualBox website

$ virtualbox --help | awk '/Oracle/{ print $5 }'```

4.3.16
```

$ vboxmanage --version```

4.3.16r95972
```

Virtual Manager -> Help -> About VirtualBox
GUI version 4.3.16 r95972


Previously I have been trying upgrade the host to Ubuntu 14.04 but failed.  I didn't continue because there are about 40 VMs running on this box.  I expect to find a sure-fire steps to run the upgrade safely.

Regards
satimis

---

