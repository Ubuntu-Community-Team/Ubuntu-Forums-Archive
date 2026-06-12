---
title: "how best to install DD daily onto old 18.04 partition"
date: 2019-02-06
forum: Ubuntu Development Version
---

### Post by Kris_M on 2019-02-06
I run 18.10 which was fresh installed on a clean partition.
Also have on this SSD: 18.04, swap, and 2 NTFS partitions (win7 and used-to-be-win-10-that doesn't boot), plus a couple other ntfs shared partitions. My shared ext4 partitions and other ntfs partitions (backups and such) are on a different, switchable, spindle.(actually, 2 different switchable USB3 plugable spindles)

I have 2 ubuntu partitions plus a swap partition on this SSD.
Both can be currently booted to by grub, though I can't remember last time I used 18.04.(poor thing tried to update itself)

What I want to do is install the DD daily onto the partition that has the old 18.04 :
Should I just "do it"? (I think I can format in the install, if booting from iso on thumb drive).
Should I somehow remove it from existence and then create a new partition there and then install the DD daily (don't know how I would do this.)(and keep grub happy)
I am BIOS/MBR and intend to stay that way so _don't waste time telling me to go UEFI - btdt_ - :(

Yes, I am bored
Yes I am a glutton for punishment (2 1/2 full months before 19.04LTS)
Yes, I have gparted, rescatux etc on usb sticks.
I am full SSD image backed up via Macrium (this has been tested in the past and has worked fine for me if I get in trouble). Can be executed via win7 or boot stick.

Thanks!

---

### Post by oldfred on 2019-02-06
With MBR, the last install will be the version of grub in control of the MBR.
There are ways to install to in effect, not install grub to MBR, so your main working install stays in charge. And  you can then create a 40_custom boot entry to boot your new install.

       I first saw this from Ranch hand who at time was testing installs and did not want to always be updating grub.
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

I keep a partition just for ISO and use grub to boot ISO from SSD to install to HDD. Also one on HDD for installs to SSD. And I am changing to use labels to boot install, but if I reformat it, which I normally do, I have to reset label back to disco. Using configfile loads the grub on disco rather than directly booting the kernel as Ranch Hand was doing.
```

menuentry "Ubuntu 19.04 Disco  (on /dev/sdb8)" {
    set root=(hd1,gpt8)
    search --set=root --label disco --hint hd1,gpt8
    configfile /boot/grub/grub.cfg
}
```

---

### Post by Kris_M on 2019-02-06
Thanks!

If I don't mind letting it update grub (program or menu) during the install, it seems I could just select the 18.04 partition and it will then call it 19.04 in grub menu (see pic).? (plus I assume I would check the format box)

I don't care if old 18.10 is not default since I will quickly install grub customizer and change that if need be.  There would be a bit of initial back and forth anyway while I am copying over FF stuff, etc.

do you see a prob with that?  That would also be what I would do when 19.04LTS is released in Apr (plus I add a couple weeks for updates so call it May 1).

Thanks

pic is from latest DD daily run in part way to show "other" on install.
By the By, the USB stick wouldn't boot after Ubuntu Startup Disk Creator - had to go to Rufus in win7. boot logo error.

---

### Post by oldfred on 2019-02-06
I have done so many test installs, that I scripted probably 75% of my configuration. And anytime I see a command line way to do something, I add it to my script.

I have installed disco several times. But I only downloaded ISO once, and then zsync'd it every time after that. Saves bandwidth/time.

---

### Post by Kris_M on 2019-02-06
Thanks!!!

---

### Post by Doug S on 2019-02-09
> **Kris_M said:**
> ...That would also be what I would do when 19.04LTS is released in Apr (plus I add a couple weeks for updates so call it May 1).19.04 is not and LTS release. The next LTS (Long Term Support) release will be 20.04.

---

### Post by Kris_M on 2019-02-09
> **Doug S said:**
> 19.04 is not and LTS release. The next LTS (Long Term Support) release will be 20.04.

Yes, thanks - I'd only be using it for  year anyway. :)

On another topic - I have the 4 debs for 4.19 kern, but does running them take care of adding it to the grub menu?  Guess I'll find out! Don't want to do 20 now although it sounds good I'll wait until it's "done".
Thanks!

---

### Post by Doug S on 2019-02-09
> **Kris_M said:**
>  I have the 4 debs for 4.19 kern, but does running them take care of adding it to the grub menu?Yes, it will also update grub. If you are going to experiment with kernels, suggest you set the grub menu to be visible upon boot with a long enough timeout for you to decide which kernel to boot to each time.

---

### Post by Kris_M on 2019-02-09
> **Doug S said:**
> Yes, it will also update grub. If you are going to experiment with kernels, suggest you set the grub menu to be visible upon boot with a long enough timeout for you to decide which kernel to boot to each time.

Yes, sorry, slow getting back to this - did daiy install fine, did kern install 19 fine. Boots to 19 kern fine by default.

Did fstab with stuff as in 18.10 and fine except it waited 1m30s for a ext work partition that had "nofail" in it, so just commented it out for now (that is another spindle that this kern hasen't seen yet).(kern seems to default delay for 10 secs or something which is plenty o time for me to stab the down arrow and halt timer and play which I have already done)

Copied over .mozilla and .thunderbird and both started up perfectly. That's an awful lot of what I do, right there. Done!

Bunch of tpm errors on startup - haven't researched.
Have system-monitor on top bar.
Darn thing seems perfect - shortly I should have most everything over here.
It makes life simple using laptop and having intel builtin graphics - everything is default and everything works. will try movies to hdtv later. 
Oh, gotta go do the 2 debs for the printer (canon TS6020)
Thanks!!!
Later!

---

### Post by Kris_M on 2019-02-10
This all worked out very very well.

One thing I noticed is that the daily has a "simple scan" app installed. Shouldn't be.

[strike]Having nothing to do with the above, I was unable to get the scanner to work for my Canon TS6020, as it did in 18.10 and previous(European Canon drivers). But this could well be fixed by April, and in the rare instance I need to scan, I can use win7.[/strike]
EDIT: fixed here: [https://ubuntuforums.org/showthread.php?t=2412289](https://ubuntuforums.org/showthread.php?t=2412289)

Work: kern19,FF,TBird,GrubCustomizer,AdobeFlash,Tweaks,MSFonts,system-monitor graphs on top bar,Skype,Canon TS6020 printer/scanner.

---

