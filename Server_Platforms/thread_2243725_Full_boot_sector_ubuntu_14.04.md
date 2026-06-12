---
title: "Full boot sector ubuntu 14.04"
date: 2014-09-10
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-09-10
My boot sector is full. I presume the boot sector is /boot/
Here is a screenshot of the directoy.
Which files can I delete?
[ATTACH=CONFIG]256339[/ATTACH]

---

### Post by oldfred on 2014-09-10
Generally most desktops do not need a separate /boot partition. But either way you should regualarly houseclean old kernels as they are not automatically deleted. 
I like to keep at least two, and only allow it to grow to a few and then go into synaptic and delete older ones.

       
Determine your current kernel:
uname -a
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

If you do not have synaptic 
sudo apt-get install synaptic

---

### Post by astarmathsandphysics on 2014-09-12
I read that threaf but the only installed kernal in synaptic is 3.5.47

---

### Post by oldfred on 2014-09-12
I have seen synaptic or dpkg not show old kernels after an upgrade as only the new ones are in dpkg list. Then you have to manually delete old kernels. Did you resort to have kernels in order?

If still in dpkg.

 Determine your current kernel change examples version to correct for yours:
uname -a
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic

---

### Post by astarmathsandphysics on 2014-09-13
ls vmlinuz* returns

vmlinuz-3.5.0-47-generic

I could start nautilus as root and delete some files needed for older kernels shown in the screenshot above.
Which files do I need to leave?

---

### Post by SeijiSensei on 2014-09-13
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=2242056](http://ubuntuforums.org/showthread.php?t=2242056)

---

### Post by oldfred on 2014-09-13
I do not understand how listing files at terminal gives such a huge difference?
Or did you reconfigure system and are now using a /boot folder inside / (root) as /boot and not the separate /boot partition?

If you use Nautilus at root, it moves files into root's trash and no space is gained. And deleting from root's trash is a bit more difficult and just using sudo. Better to use dpkg or rm commands.

---

### Post by astarmathsandphysics on 2014-09-13
Something magic happened late at night.
Possibly while I was druk - now everything is deleleted except those files pertaining to 3.5.0-47, the boot sector is down to 33.9 MB and my server boots ok

---

### Post by RogerDavis on 2014-10-11
I had a full boot sector.  Then I deleted all but 3 kernels.  I can look at the boot sector, it has much less in it.  

However, it STILL shows 100% full.

What do I do now?!?

---

### Post by ecophobia on 2014-10-11
ls -alhR /boot and remove old 
vmlinuz
system.map
initrd.img 
config
abi

files. Also if you have nay .bak files, delete them as well and run sudo apt-get autoremove to delete dependencies.

---

### Post by oldfred on 2014-10-11
Check your trash and if you used Nautilus with gksudo it probably is in root's trash.

  How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Last time I had to change ownership as even sudo would not let me empty root trash. I changed it back to be safe.

---

