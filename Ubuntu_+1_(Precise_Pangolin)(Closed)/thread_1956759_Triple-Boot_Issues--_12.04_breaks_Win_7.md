---
title: "Triple-Boot Issues-- 12.04 breaks Win 7"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Dngrsone on 2012-04-11
I am running Win 7 / 10.04 / 12.04 (beta-2) on an HP G72, all 64-bit.

Windows 7 was the original OS, I shrank the volume and installed 10.04 and used Grub 2 for a boot menu.

I installed 12.04-beta 2 alongside and somehow managed to get its grub 2 installed on the Windows boot partition (instead of just sda I suppose).

So, after installation, I got my old boot menu, tried to boot into 10.04 and got a new boot menu (a lovely purple color :rolleyes: ), which allowed me to get into 12.04 and nothing else.  I try to boot into Windows and it just redirects to the purple boot menu.

What I did was boot into a Windows Rescue disc, went into the console, and did:

```
bootrec /fixmbr
bootrec /fixboot
```

Which fixed Win 7, but I couldn't get into Ubuntu, obviously.  I downloaded and burned to disc the Ubuntu Boot-Repair disc, which allowed me to reinstall Grub 2, defaulting to 10.04 and allowing me to access all three operating systems.

Then came a massive update for 12.04... Once again, Windows was broken and I had two boot menus.

Now my question is-- how do I point Ubuntu 12.04 to the right Grub 2 setup (on sda as opposed to sda2 or whatever) so that any updates will go to the correct location and not break things again?

---

### Post by oldfred on 2012-04-11
Grub2 remembers where to reinstall on major updates.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You entry will have part1(at end of entry)  or similar showing the drive and a partition to reinstall to.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If you want your 10.04 grub2 to stay in the MBR, you can install the 12.04 grub2 boot loader to the partition you have installed 12.04 into. It will not be used as the grub from 10.04 will boot it. You also with the dpkg reinstall just be able to unselect all entries and it may erase the entry but you will have to check again what debconf says.

---

### Post by Dngrsone on 2012-04-11
Thanks, oldfred!

I used the reconfigure to get Grub 2 where it belongs, and everything works fine.

---

