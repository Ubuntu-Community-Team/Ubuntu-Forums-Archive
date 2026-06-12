---
title: "KVM and windows XP issues"
date: 2008-12-30
forum: Virtualisation
---

### Post by kasper22 on 2008-12-30
Hi,
I've been a long time xen user, but did an update to 8.10 the other day and found that xen hosts are not in ubuntu anymore.  So I decided it was time to try something new and went with KVM.

Installing my first ubuntu guest was a breeze everything went as the how to said it would.

Then I tried winXP and that is where the trouble started.  I was following the directions here: [https://help.ubuntu.com/community/KVM/CreateGuests](https://help.ubuntu.com/community/KVM/CreateGuests) for other systems.  The first step works, and I would be able to do the first step of the windows install.  Then on the reboot as soon as it tried to "boot" the image I would get a disk read error.  After a few different things I found this worked for me:
(from memory  as history seems to be random in what commands it keeps?)
qemu-img create windows.img 15G
kvm -m 512 -cdrom /dev/cdrom -boot d /home/user/windows.img
once basic setup was done
kvm -m 512 -cdrom /dev/cdrom -boot c /home/user/windows.img

After that I fixed up the xml file that was created by trying to follow the original directions and it worked.

Now I want to have that file run from a LV instead of a file.  So I did as was suggested here: [http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-8.10-p4](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-8.10-p4)

Now when I start it starts up, but then freezes.  So the first time I started it was just a black screen, then the next time, it gave me that windows didn't shut down properly message on the next start.  But as soon as I choose a start method it just freezes again.

Any ideas on what I might be missing to run windows from a LV?

Thanks,
Bryan

---

