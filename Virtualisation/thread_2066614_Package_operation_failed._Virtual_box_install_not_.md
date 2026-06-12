---
title: "Package operation failed. Virtual box install not working"
date: 2012-10-05
forum: Virtualisation
---

### Post by mdkwlan on 2012-10-05
Hello everyone!
I was messing around with Virtual box today and I saw I installed the wrong version. I install 4.1. So need less to say I wanted to install 4.2. So I removed it from the Ubuntu Software Center. Rebooted just for good measure once it was done. I downloaded the latest version of Vbox off the official website and went to run it and i got this error.
```
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 191220 files and directories currently installed.) 
Unpacking virtualbox-4.2 (from .../virtualbox-4.2_4.2.0-80737~Ubuntu~precise_amd64.deb) ... 
dpkg: error processing /home/mdk/Desktop/virtualbox-4.2_4.2.0-80737~Ubuntu~precise_amd64.deb (--install): 
 trying to overwrite '/usr/share/virtualbox/VBoxGuestAdditions.iso', which is also in package virtualbox-guest-additions-iso 4.1.12-1 
dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe 
dpkg-deb: error: subprocess paste returned error exit status 2 
Processing triggers for ureadahead ... 
Processing triggers for shared-mime-info ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ... 
Processing triggers for hicolor-icon-theme ... 
Errors were encountered while processing: 
 /home/mdk/Desktop/virtualbox-4.2_4.2.0-80737~Ubuntu~precise_amd64.deb 

```

Can anyone tell me what I can do to fix this?
Thanks
Also I'm sorry if I posted in the wrong place for it. Would seem fitting to be in the Virtualization section.

---

### Post by mdkwlan on 2012-10-05
I got it working by using
```
sudo dpkg -i --force-overwrite <filename>
 sudo apt-get -f install
```
Seems to be running just fine.

---

