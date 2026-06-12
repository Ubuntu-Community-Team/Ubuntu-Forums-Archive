---
title: "Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI"
date: 2013-06-04
forum: Tutorials
---

### Post by Dave231153 on 2013-06-04
I bought myself an Asus K55VD SX696H 8 Gb model. I stuck with the original size harddisk, because Asus wanted too much money to upgrade for a slow 750 GB drive, instead I purchased Seagate Momentus XL 750 GB Hybrid drive to fit myself. My problems started immediately, Windows 8 is horrible, I think this is another Lemon just as Vista was. The EFI and Gpt system is also difficult to get your head around.

The optical drive would not read my Ubuntu disk 12.04.2 (64 bit), so I had to mess with the bios, then it would only read it in Legacy mode. I tried installing in Legacy mode and no grub menu. To cut a very long story short, out came the hybrid, back went in the original drive and a massive hunt through forums and loads of research.

First I got hold of a free copy of Macrium Reflect (get it [here]("http://www.macrium.com/reflectfree.aspx")) and I did a full back up of all my original partitions, put the back up on a USB portable HDD, then made the rescue disk. The rescue disk will load with the optical drive and it found the back up so all was good.

I replaced the original drive with the new Seagate and did a full restore, and it worked.

I then found a program called Rufus (get it [here]("http://rufus.akeo.ie/")). This allows you to make bootable flash drives that work in EFI.

I used this to put my iso of Ubuntu 12.04.2 onto a bootable flash drive.

I then used another flash drive and made another bootable flash drive with Boot-Repair (get it [here]("http://sourceforge.net/projects/boot-repair-cd/files/")), and just to be sure I used a copy of Burnaware (get it [here]("http://www.burnaware.com/burnaware_free.html")) to make a bootable copy of the Reflect Rescue disk.

Once I had all of this I was ready to start.

1. I put the Ubuntu flash drive in the usb port, then restarted the computer, went into the bios (press F2) and went to the boot area. There at the bottom of the boot order was the Ubuntu usb drive.

2. I moved this up until it was first boot option, then pressed F10 and saved the settings and restarted. A grub menu appeared Try Ubuntu or Install Ubuntu, obviously I went for install. It worked like a dream and I loaded it along with Windows 8.

3. I then restarted the computer and lo and behold there was the grub menu, but it would only boot into Ubuntu, so I put in the Boot-repair flash drive and rebooted, pressed F2 went into the bios and boot section, and moved the repair usb drive to first boot. Then pressed F10 and restarted.

4. Boot-repair worked like a charm, it made all the necessary changes, and gave me the path at the end so I could make a new boot option. I wrote this down and rebooted when it had finished, and back into the bios, this time I went to boot and add a new boot option and followed the directions and made a new boot option with the command line given.

5. Removed all bootable flash drives, went back to boot options and moved the new boot option (I called it Ubuntu Loader) as the first option, held my breath, pressed F10 and rebooted.

6. The grub loader screen appeared and I was able to boot into either either Ubuntu or Windows. The menu I faced had the old Windows load command in there as well (I'm not sure how to delete it), but the one ending in EFI is the one that will boot you into windows.

Although this seemed a lot to do it didn't take long, and I feel confident that this same way would work on any computer with the new GPT and EFI system in place.

Good luck and I hope this helps.

---

### Post by Dave231153 on 2013-06-04
Just to add to this, the programs above are all for windows.

Since writing this a few hours ago, I have removed 12.04.2 and replaced it with 13.04 again following the same procedure, 13.04 is blindingly fast on load up. I have also found a nice grub loader customizer program that has nicely removed all those extra entries that were not needed, now it looks very clean. Windows still loads, but when I have to use Windows 8 it is not an enjoyable experience, whereas using Ubuntu is a joy and pleasure.

---

### Post by matt_symes on 2013-06-06
Thread moved to **Tutorials**

---

### Post by paulof2 on 2013-06-21
Hello [COLOR=#000000]Dave231153[/COLOR]!

Thank you a lot... Your tutorial helped me a lot...

I wanted Ubuntu and Windows 8 on my new Asus K55VJ but I couldn't find out how to do it right and your tutorial showed me the way :p

Thank you very much.

Best regards, paulof2

---

### Post by Dave231153 on 2013-07-11
It is nice to see that this has helped a few people.

---

