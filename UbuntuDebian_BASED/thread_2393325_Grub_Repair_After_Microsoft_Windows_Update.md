---
title: "Grub Repair After Microsoft Windows Update"
date: 2018-06-01
forum: Ubuntu/Debian BASED
---

### Post by ujjwale460 on 2018-06-01
Hello, i dual booted my Pop-OS system with Microsoft Windows 10, after upgrading to new version of Windows GRUB2 menu for OS selection for boot was disappeared and i could not log into my Linux system cause GRUB2 menu was not there then i found this link [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?) and did as it was instructed , Using Boot Repair tool. After completing the process of repair i finally got into my Linux system but i got two windows menu(you can check that in this image link [https://ibb.co/gaVCYJ](https://ibb.co/gaVCYJ) ) and wonder which one boot and one for Pop-OS i have collect the pastebin link  [http://paste.ubuntu.com/p/kQp32Q525b/](http://paste.ubuntu.com/p/kQp32Q525b/) , i want  to remove one windows menu to log in, Thank you.

---

### Post by oldfred on 2018-06-01
Many users do not know Windows uses a boot partition. And they delete it. But then they do not have the essential boot files for Windows. So now Boot-Repair backs up bootmgr & BCD into main install. 
But then grub2's os-prober finds both sets of boot files and adds boot entries for both.

Easiest is to copy the one boot stanza you want to keep into 40_custom and turn off os-prober.
Another alternative may be Grub Customizer, but it creates its own versions of grub files.

       Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
sudo -H gedit /etc/grub.d/40_custom
or
sudo nano -B /etc/grub.d/40_custom
Then do:
sudo update-grub 

Once new boot entry is known to work, turn off os-prober.
      
 sudo nano /etc/default/grub
#Add this line:
GRUB_DISABLE_OS_PROBER=true
sudo update-grub

---

