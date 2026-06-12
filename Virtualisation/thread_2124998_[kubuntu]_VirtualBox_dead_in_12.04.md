---
title: "[kubuntu] VirtualBox dead in 12.04"
date: 2013-03-12
forum: Virtualisation
---

### Post by etfjr on 2013-03-12
I just upgraded to 12.04 and VirtualBox isn't working...

It says to execute '/etc/init.d/vboxdrv setup' as root, but when i do, it says vboxdrv is not found...

Any ideas?

Thanks,
Taylor

---

### Post by tombert on 2013-03-12
Try to load the module:

modprobe vboxdrv

---

### Post by varunendra on 2013-03-12
*Thread moved to **Virtualisation**.*
---------------------------

Try whatever is suggested in this thread : [http://ubuntuforums.org/showthread.php?t=2124725](http://ubuntuforums.org/showthread.php?t=2124725)

Post back the result.

---

### Post by etfjr on 2013-03-12
OK... finally solved it...
After verifying that the correct headers were installed, i did:
sudo apt-get install virtualbox-ose-dkms
now all is working... seemingly...

Taylor

---

