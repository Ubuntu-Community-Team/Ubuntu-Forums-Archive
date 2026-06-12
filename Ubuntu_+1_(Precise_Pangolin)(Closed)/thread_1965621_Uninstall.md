---
title: "Uninstall"
date: 2012-04-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Miykel on 2012-04-26
G'Day; Please forgive me but I'm still doing battle with the new kernel issue.
  
  I'm not sure if it's relevant to the problem I'm having, i.e. will not boot into new kernel, I tried to    sudo update-grub  but found it still had the entry for the 3.4.0rc4 kernel, even though I'd purged it, I had a look in /boot and found files labeled linuz-3.4.0 rc4, take ownership worked, tried to delete, no good, then cd /boot, ok, sudo apt-get purge ... "no such file or directory". Is there a way I can remove these files from /boot  ???
Regards Miykel   :confused:

---

### Post by Harry33 on 2012-04-26
Installing/uninstalling kernel packages (there are three of them for each kernel version) will automatically run update-grub and remove the uninstalled kernel link from there.

Please use Synaptic and see that you have completely removed (purged) all three kernel (3.4) packages:
- linux-headers-3.4.*-generic
- linux-headers-3.4.*
- linux-image-3.4.*-generic

In case you have messed too much with the files, you can try to reinstall exactly the same three kernel packages and then uninstall completely them with Synaptic.

---

### Post by Miykel on 2012-04-26
Thanks for the reply  Harry;  synaptic wouldn't work either, dman, ended up simply using 

code;
cd /boot
sudo rm  <files>
Have to learn to keep it simple instead of looking for the most complicated path, 
Regards Miykel

---

