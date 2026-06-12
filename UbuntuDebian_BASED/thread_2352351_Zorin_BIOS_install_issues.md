---
title: "Zorin BIOS install issues"
date: 2017-02-11
forum: Ubuntu/Debian BASED
---

### Post by malcolm102 on 2017-02-11
Machine (custom-built):
Processor: AMD Athlon 64 X2 Dual Core Processor 4600+ x2,  2.4 GHz
Memory    : 1.8 GB
Storage: sda1 - 214 GB; sda 5    -     16 GB (ext4 partition)            
Graphics : Gallium 0.4 on NV67
X11 Vendor : The X.Org Foundation
BIOS: 01/10/2008 Phoenix Technologies Version 6.00 PG
Dual boot Windows XP (SP3) and Zorin. Machine also operates on Puppy Linux 5.7.1, booted from CD.

I upgraded Zorin OS 9 core to Zorin OS12 core. (I should say that OS 9 had been a bit slow running and prone to 'freezing'.) 

When upgrading, I followed all instructions for making the bootable USB device,  and tried out and installed Zorin OS 12 according to the instructions - [https://zorinos.com/help/upgrade-zorin-os/](https://zorinos.com/help/upgrade-zorin-os/). Checksum was correct. Bootable USB works fine.

However, install seemed to hang at a blank screen at the end and I turned machine off. I don't know whether I had mis-hit a key or anything.

On re-booting I got the message:
Boot from CD:
error: file '/boot/grub/i386-pc/normal.mod' not found.
Entering rescue mode...
grub rescue>

I tried Boot-Repair-Disk on a CD, but it would not proceed beyond this message:
'Please close all your package managers (Software Center, Update Manager, Synaptic... ) then try again.' 
I have however created Boot-Info at [http://paste.ubuntu.com/23975279/](http://paste.ubuntu.com/23975279/)

I would be very glad of any advice on this problem, which is like Macamba's [which I read in another thread].

---

### Post by oldfred on 2017-02-11
Your system is using Zorin which is not Ubuntu.
So not identical issues to thread you posted in.
[https://ubuntuforums.org/showthread.php?t=2345077](https://ubuntuforums.org/showthread.php?t=2345077)

Often best to have your own thread anyway to avoid confusion on differences with original thread. Boot issues are rarely identical as systems vary a lot.

Install looks normal.
But Boot-Repair could not run update to grub as it found package manager open.
Were you also running something else that has package manager open. I often open synaptic and then try to run a command line task and have same issue.
Or did system leave a lock file that must be manually deleted to let you update. Maybe you forced shutdown or had power failure in the middle of updates, so lock file was not released?

---

### Post by malcolm102 on 2017-02-13
Thank you for the suggestions, Oldfred.
I have run Boot-Repair-Disk again a couple of times and tried to find anything that may be open relating to Synaptic, but no processes appear to be running there that I can see. It doesn't appear to be trying to perform any task. I can't find any Software Centre or Update Manager on the Menu. When I click on it, Boot-Repair seems to start off promisingly trying to do the job, with the message 'Applying changes. This may require several minutes,' and sometimes a message about GRUB flashes up, but then straight away the 'Please close all your package managers...' message comes up and the process stops.
 As regards the way the system shut down when I was updating Zorin, it was an irregular shutdown. I think it said the OS update was complete, but I know I brushed the End or Delete or Arrow keys area of the keyboard by mistake at that moment and I thought that I might have mis-hit a key in doing that because just after that, unless it was coincidence, the window closed and the text-only screen came up with the message:
sdb No caching mode page found (or similar)
sdb Assuming drive cache: write through (or similar)
sda Ubuntu carrying out installation ... (or similar)
This message carried on slowly flashing on and off for well over half an hour, so I assumed an error and turned off the power on the machine. I thought I had given it long enough to close of its own accord.

---

### Post by oldfred on 2017-02-13
Do not know Zorin and what differences it has.
If new install, may be quicker to reinstall.

If you want to try to repair, and Boot-Repair is not working you can chroot into system and run repairs & try to finish updates or grub reinstall from inside chroot.

Do you have separate system partitions or just / (root) as some other system partitions have to be mounted like /boot as part of chroot.

       To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Once chrooted you can run all the normal repair update type commands like:

 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get autoremove
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a

---

### Post by malcolm102 on 2017-02-14
Thanks very much for this info, Oldfred.
It will take me a bit of time to learn about chroot though. I only came to Linux about two years ago and am still at an early stage.
 As regards partitions, I only have the two as far as I understand it - Windows on sda1 and Zorin on sda5 (ext4).
It may be that reinstalling Zorin is the simplest option, as you describe. Whilst I find out more, I can at least continue using my machine via Puppy Linux, booted from CD. I will get back in due course and update on the situation. Many thanks for your help.

---

### Post by oldfred on 2017-02-14
You may be able to just delete the lock file.

In Ubuntu it is in or is:
/var/lib/dpkg/lock

---

### Post by malcolm102 on 2017-02-15
I've located the lock file, OldFred, thanks. 
It looks as if the command to use, having read a bit, is: 
sudo rm /var/lib/dpkg/lock
Something I don't understand, first, though is how is it that the Boot-Repair-Disk can contain this lock file? I am booting up live from the CD, which I downloaded from SourceForge, why should the CD contain a lock file which stops it operating? There isn't anything on it that has been updated, and, additionally, anyone booting up and using it is intending just to use Boot Repair. Synaptic isn't active, though presumably I could start it downloading. On the several occasions on which I have used the CD I have exited and shut down normally. I haven't seen or started any activity other than Boot Repair.
I can't work this out.
By the way, I have seen the message that Boot Repair displays just before it is shut off: 'Purge and reinstall GRUB of sda5'.

---

### Post by oldfred on 2017-02-15
I believe Boot-Repair is actually doing a chroot of essential partitions. 
Have not used it for a full reinstall of grub, but at the minimum to just install grub to MBR, it has to mount the / partition. 
And then it may see lock file? Not sure.
And if full chroot, it is using the installed system, the live install is just the kernel used to boot. 
chroot is CHange ROOT.

---

### Post by malcolm102 on 2017-06-01
I deleted the &#8216;lock&#8217; file as described. I saw in &#8216;Properties&#8217; that it was dated 2014.
However, Boot-Repair still didn&#8217;t work, unfortunately, and came up with the same error message.
I tried several times.
Doing certain things in Synaptic, for example, changing settings in &#8216;Preferences&#8217;, even resulted in the &#8216;lock&#8217; file coming back again. This time, though, it had today&#8217;s date on it.
Some of the Boot Info Summaries are:
[http://paste.ubuntu.com/24739235/](http://paste.ubuntu.com/24739235/)
[http://paste.ubuntu.com/24739250/](http://paste.ubuntu.com/24739250/)
[http://paste.ubuntu.com/24739365/](http://paste.ubuntu.com/24739365/)

---

### Post by oldfred on 2017-06-01
Afraid I do not know Zorin, it may be a specific to Zorin bug?

Opening any update command or program should set lock file, but when done it should close/delete it.

---

### Post by malcolm102 on 2017-06-02
Thanks OldFred. I am enquiring at Zorin.

---

### Post by yancek on 2017-06-02
Were you ever able to successfully install Zorin?  Your original post indicated you shut down before the installation completed and you then had an error about missing grub files.  The boot repair output files you posted in post # 9 all show Grub code in the MBR but do not show any Grub files on sda5, your Zorin partition.  Usually, Grub files will be shown here.  Almost always, the Grub boot menu file (grub.cfg) and it's contents will show and none of the boot repair output files show that.  Can you boot anything on this machine?

---

### Post by malcolm102 on 2017-06-03
&#65279;Hello Yancek,

This update to Zorin OS12 has never worked and I lost access to Windows XP as well, which I was previously dual-booting along with Zorin OS9. All I get on powering up and trying to boot from the hard drive is:
[I]&#65279;Boot from CD:
 error: file '/boot/grub/i386-pc/normal.mod' not found.
 Entering rescue mode...
 grub rescue>[/I]

I can still use the computer though - I boot [Puppy Linux 5.7]("http://puppylinux.com/") from CD, with its settings stored using a Squash file (sfs) on the hard drive. From Puppy Linux I have access to My Documents in Windows too.

I have mounted and searched partition sda5 and found the file grub.cfg in /mnt/sda5/usr/share/doc/grub-common/examples/grub.cfg

---

### Post by oldfred on 2017-06-03
Typically normal.mod not found means grub is not fully installed or you are booting a different version that what you have (old version in MBR?).

You may just need to reinstall grub to MBR or perhaps a full reinstall of all of grub.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

I assume it will also work with Zorin. You can in Advanced options totally uninstall & then reinstall grub.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

