---
title: "Xbuntu guest on Win7 host VMWare.  On physical disk partitions."
date: 2011-01-23
forum: Virtualisation
---

### Post by thegrimace on 2011-01-23
So I have been searching the web for around 8 hours all said and done, and could not find a solution to my problem.  Posting this so if anyone else is trying to do what I finally managed to get working they will have some help.

I have been trying to get Xbuntu working as a guest in VMWare workstation (windows host) using a partition (seperate from windows) on my only disk drive.

You can't hand ubuntu VM the boot sector (partition). The only "simple way" around this is to install ubuntu as a dual boot on the partition you were going to use.  So do that.

On reboot grub will be there.  Boot back into windows.

Now create your ubuntu VM.  Tell it you will install the OS later and give it access to only the partitions with ubuntu installed (and the ubuntu swap partition of course).  power the machine.  You will find yourself at the GRUB menu, launch ubuntu.  For me it just brought up a prompt (instead of gnome).  You may be able to just type startx (or was it xstart?)(I'm pretty new at all this), but if you can't just reinstall "gnome" with 'sudo apt-get -install --reinstall ubuntu-desktop'  then startx.

And your done.  You are now running a Xbuntu guest VM using a physical disk from inside a Win7 host.

Hope this helps someone out there.

---

