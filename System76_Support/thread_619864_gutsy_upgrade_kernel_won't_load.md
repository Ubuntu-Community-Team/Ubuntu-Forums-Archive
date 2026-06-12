---
title: "gutsy upgrade kernel won't load"
date: 2007-11-21
forum: System76 Support
---

### Post by dgermann on 2007-11-21
Hi--

System is a gazelle value. Got it about 3 months ago.

Used update-manager to upgrade from 7.04 to 7.10.

After reboot, the system hangs almost immediately when it gets to the progress bar, and dumps me out to BusyBox.

I can get to the grub menu and load the old kernel, 2.6.20-16.  lsb_release -a reveals that I have 7.10 gutsy, and it says No LSB modules are available.

I tried sudo apt-get update && sudo apt-get --assume-yes dist-upgrade
and it says there is nothing to upgrade.

Not sure which log to look at for clues. In /var/log/messages toward the end of the last boot attempt that aborted, there are several entries that have "ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for" and from here it varies. redhat???

Sound seems to be working but I installed System76 drivers anyway.

Any ideas of what I should try next?

Thanks!

---

### Post by BrandanLloyd on 2007-11-22
I had this same problem.  I had to roll back to a previous kernel version to get my laptop (GAZV3) to work properly.  I did some Googling and somewhere found a post that mentioned that the 2.22 kernel version doesn't work well with the Intel motherboard.  

I haven't tried a clean install, though I plan to attempt one this weekend so I will try to remember to report back on how it went.

---

### Post by dgermann on 2007-11-22
Brandan--

Thanks. Let us know what you discover.

I tried using synaptic to reinstall linux-generic, linux-image-2.6.22, linux-image-generic, and linux-restricted-modules 2.6.22. None of this made any changes. Still need to use the esc to grub and choose earlier kernel routine.

I note as well that suspend and hibernate do not seem to work well, but they did not under Feisty either. Suspend just seems to lock things up, requiring holding the power key down for about 10 seconds to get out of.

---

### Post by thomasaaron on 2007-11-23
Here is the fix:

Press Escape when you see Grub loading
Choose an earlier kernel (2.6.20-something if I remember correctly)
Your system will boot - open up a terminal and run the following commands

sudo rm /etc/modprobe.d/blacklist-ata
sudo gedit /etc/initramfs-tools/modules

remove "piix" from the bottom of the file > save and close
sudo update-initramfs -u

sudo reboot

---

### Post by BrandanLloyd on 2007-11-23
Well, I was able to run the fresh install this morning and in under 30 minutes I was back up and running smoothly on the new kernel.  'uname -r' says "2.6.22-14-generic".

---

### Post by dgermann on 2007-11-23
Thomas--

You certainly are Johnny on the Spot! Thank you for your swift reply.

I did essentially what you suggested except for two things and it did not work for me--still stalls at that first progress bar, right at the beginning.

What I changed was that I did not rm but instead mv the first file by adding "-20071123" to the end of it; then I commented out the offending line in the modules file.

The next command chugged for a while but eventually came back with a prompt and no error messages. 

What next, O guru?

Brandan--

Good for you! You give me hope that it can work!

---

### Post by dgermann on 2007-11-23
Thomas--

Well, maybe it makes a difference after all!

I took the file I renamed & moved to my home directory instead. The file I commented out I copied to my home directory and then deleted the material as you suggested at first from the copied from file. Then re-ran the update. On reboot, all worked, except I had to reload the system76 drivers to get my sound back.

uname -r produces 2.6.22-14-generic

So it looks like all is well with this problem!

Thanks, Thomas!

PS: can you tell us why this was necessary so we can recognize this problem if it happens with another machine? Is it just limited to System76 machines, or is it general?

---

### Post by thomasaaron on 2007-11-26
The problem could happen to a number of machines.

If memory serves, Feisty's piix module conflicted with the pata drive in the gazelle values and DarU1 computers. This problem was fixed in Gutsy, so blacklisting the piix module became unnecessary.

---

### Post by dgermann on 2007-11-26
Thomas--

Thanks very much.

You sure are great with service here. I really appreciate that I can count on you.

---

### Post by helix on 2007-11-29
> **thomasaaron said:**
> Here is the fix:

Press Escape when you see Grub loading
Choose an earlier kernel (2.6.20-something if I remember correctly)
Your system will boot - open up a terminal and run the following commands

sudo rm /etc/modprobe.d/blacklist-ata
sudo gedit /etc/initramfs-tools/modules

remove "piix" from the bottom of the file > save and close
sudo update-initramfs -u

sudo reboot

I've got the same issue but when I issue the first command theres no directory, and there is no "piix" line in the modules file. Any suggestions?

---

### Post by thomasaaron on 2007-11-29
Then you are probably not running a System 76 Gazelle or Darter, I'd guess?

---

