---
title: "Grub problem on 12.04/11.10 dual boot"
date: 2011-10-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by CaptainMark on 2011-10-18
ive never dual booted before so ive never had to even worry myself with grub, i used the 11.10 live cd to put a partition for 11.10 beside my 11.04 and then updated the 11.10 boot using methods outlined in the 12.04 subforum to update to 12.04, works great so far so good.

to describe my problem, when i first boot i have the main grub screen, if i select 12.04 no problem it boots, if however i select 11.04 it seems to pause at a further grub prompt and any changes made to the 11.04 grub.conf will only take effect on this second grub stage, i think i may have installed grub inside grub by mistake, any advice on how to sort this out, im confused, ive googled around but cant seem to tell what ive done, 

just to be clear, my setup still works but i think im waiting for grub twice during bootup into 11.04

---

### Post by oldfred on 2011-10-18
Moved to  [Ubuntu +1 (Precise Pangolin)]("http://ubuntuforums.org/forumdisplay.php?f=412")
You do know once they start updating packages there is likely to be a lot of breakage.

Post this from liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by grahammechanical on 2011-10-18
Perhaps Grub is working fine but Ubuntu starts to load you should get a Plymouth splash screen followed by the login screen. Perhaps Pylmouth is having difficulty progressing. Have you been modifying the desktop in any way.

I messed up my Plymouth splash. I have an image as a background for the Grub menu and when I choose 11.04 the Grub background image remains a long time and I do not always see the Plymouth screen. Just as in your case this does not happen if I select the other OS, which is 11.10.

You should also know that the last Ubuntu to be installed will put its own Grub in the MBR that is why changes to the 11.04 Grub do not work. You will also find that a kernel update in 12.10 will also update the 12.10 grub.

I use grub-customiser. Whenever grub gets altered b y the install of another Ubuntu or a kernel update on anothe Ubuntu, I load 11.04 and run Grub Customizer and get to save the 11.04 grub into the MBR. That fixes things for a while. See. the link.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

Regards.

---

### Post by effenberg0x0 on 2011-10-19
I think grub is installed to the MBR of /dev/sda and also to the boot sector os /dev/sd(n). Fixing that would be easier with this grub cds, startup manager, etc. But in the end, what it will do if use dd to zero the MBR and the bootsector and reinstall grub to one of them, and maybe recreate a partition table (which is not mandatory as most BIOS know where to look in the beginning of disks).


One thing I like: Google for "Creating 1MB GRUB Partition". It can't be overwritten unless mounted. You can auto-unmount it every time an OS boots. And you can mount it when you need to update-grub.

---

### Post by jerrylamos on 2011-10-19
> **CaptainMark said:**
> ive never dual booted before so ive never had to even worry myself with grub, i used the 11.10 live cd to put a partition for 11.10 beside my 11.04 and then updated the 11.10 boot using methods outlined in the 12.04 subforum to update to 12.04, works great so far so good.

to describe my problem, when i first boot i have the main grub screen, if i select 12.04 no problem it boots, if however i select 11.04 it seems to pause at a further grub prompt and any changes made to the 11.04 grub.conf will only take effect on this second grub stage, i think i may have installed grub inside grub by mistake, any advice on how to sort this out, im confused, ive googled around but cant seem to tell what ive done, 

just to be clear, my setup still works but i think im waiting for grub twice during bootup into 11.04

Symptoms are that the 12.04 install properly specified /dev/sda
and the 11.04 somehow specified /dev/sda1 (1 or whatever partition 11.04 is in).  Grub should only be put on /dev/sda or /dev/sdb or whatever, and never inside a partition unless you know a whole lot more about grub than I do.

If you can get the 11.04 up, try 
sudo update-grub
sudo grub-install /dev/sda

That way changes to the 11.04 should get to grub on /dev/sda.

do NOT specify /dev/sda1 or any other number after the "a".

I don't know how to get rid of the extra grub inside a partition. 

Any forum readers any idea?

Thanks, Jerry

---

### Post by jppr on 2011-10-19
I don´t have any dual boot problems. I have /dev/sda1 windows 8 and /dev/sdb1 windows 7 and ubuntu 12.04. Grub menu works fine, which I choose to turn on the system.

---

### Post by CaptainMark on 2011-10-19
> **jerrylamos said:**
> Symptoms are that the 12.04 install properly specified /dev/sda
and the 11.04 somehow specified /dev/sda1 (1 or whatever partition 11.04 is in).This is what i think has happened, its odd, 11.04 was there first and was (at the time) the only os, so i assume should have installed to /dev/sda, i assure you i do not know more of grub than you guys so appreciate the advice, i will try your commands, also thanks admin for moving the thread i was 50:50 as to whether to put it here in the first place

plus, bring on the breakage, i cant wait, i especially liked not having a desktop in 11.10 mid alpha 1, i was running that as my only os at the time, that was fun :P

---

### Post by oldfred on 2011-10-19
There is no need to remove grub from a PBR as it will never be used by grub unless you really want to boot that way. The space is only used by Windows & Lilo for booting.

You could possibly use dd to zero it but if you zero the wrong sector....

---

### Post by CaptainMark on 2011-10-19
your fix worked perfectly jerry, 

thanks
mark

---

