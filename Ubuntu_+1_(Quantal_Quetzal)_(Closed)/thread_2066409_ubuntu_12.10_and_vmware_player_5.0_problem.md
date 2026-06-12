---
title: "ubuntu 12.10 and vmware player 5.0 problem"
date: 2012-10-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by svenole on 2012-10-04
I've upgraded to 12.10 beta 2 and discovered that the latest kernel (3.5.0 xx) following this ubuntu release, crashes if you have vmware player 5.0 installed. The trace gives direct indication that it's caused by the vmmon process or module that follows vmware player.  Work around is to boot an older kernel (3.2.0-xx), mv /usr/lib/vmware to /usr/lib/vmware-, and then reboot the latest kernel. I've then moved /usr/lib/vmware- back, started vmware player and booted the virtual machine without problems. 

Now, I would like to fix this, but I do not dare to reinstall player compeletely because of potential compile problems. I have done "vmware-modconfig --console --install-all" to recompile the vmware modules running the latest kernel, but have not succeeded to fix this issue..

---

### Post by fjgaude on 2012-10-04
Well, I freshly installed Beta2 and then installed Player 5.0. All went well, except Player crashes the system when I try to access a previously built VM.

I'll try using an older kernel within 12.10 and see what happens. If all else fails we'll wait until VMware comes out with their next version, which could be any day or two months from now. <smile>

---

