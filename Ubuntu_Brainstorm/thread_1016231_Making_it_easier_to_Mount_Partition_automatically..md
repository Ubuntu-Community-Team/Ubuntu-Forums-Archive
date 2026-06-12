---
title: "Making it easier to Mount Partition automatically..."
date: 2008-12-19
forum: Ubuntu Brainstorm
---

### Post by AlexBellisBrown on 2008-12-19
Ive been reading a few threads, and a number of people, including myself, hold all our music (or photos... etc...) in a seperate partition other than the pics or music folder in Ubuntu. Now, its a HUGEEE problem to get these things to mount on boot up, you have to play with files... terminal, etc, so, how about a feature in the Partition editor to "mount on startup". Yes, you can mount it manually just by clicking it in the places folder, BUT!!! When i start my computer, lets see, i click Firefox, aMSN and then Songbird, or Rythmbox, whatever, a music program, i click a song and Poof... not found. I then have to open places, click it, wait a second, and then i can play music off the partition. Not very efficient. So how about a feature to make it easy to Mount automatically, which is easy to select, turn on and off in the Partition Editor? It couldnt be that hard, could it? :) Thanks for reading.

:popcorn:

---

### Post by xjcannonx on 2008-12-19
Im not at my linux now, but I know there is a solution as I did it with my 8.10 mounting windows share automatically, I will look at home later to see what I did if no one else gets you an answer.

---

### Post by smartboyathome on 2008-12-19
The problem is that this would require one to set a disk label for each disk (which requires root access) in order for the mount point to remain the same. Only other way around that is to have the person specify a mount point, and (possibly) create it, which also requires root access. Then, finally, they would have to add the entry to fstab, which also requires one to be root.

---

### Post by xjcannonx on 2008-12-19
So I re read your post again and I actually have my media on an external drive connected to my desktop and i access it from my laptop wirelessly and all I need to do is play a song and it works automatically

For your case I dont know for sure because I haven't done it but check out the debian policy manual section 9.3 for some more details on what you need to do, it doesn't look that hard..

[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit]("http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinithttp://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit")

---

### Post by rockin_goliath on 2008-12-20
Actually, if you right click on the desktop icon, click properties, then click the "volume" tab, you can define a custom mount point under the "settings" drop down arrow. See the screenshot.

I have no idea how to edit fstab files or make drive labels, but this works great for me. I keep all my Rhythmbox music on me external drive, so this way every time the drive is mounted it always has the same mount point.

---

### Post by rockin_goliath on 2008-12-20
Also, if you define the drive that you have all your music and stuff on during the installation process, it will be mounted at bootup. It would be nice to have in the nautilus properties dialogue to have a "mount at startup" check box, i agree.

---

### Post by AlexBellisBrown on 2008-12-20
I still belive it should be easier to do... In the screenshot i included, ive opened the (mounted) music drives propertys, and got this under a tab. Is one (oh how very english that sounded...), Is one supposed to write something like "bootup" as mount point or something? Surely an option with a tick/untick box which says "mount automatically" would be better? Opinions people! :)

P.S Thanks to all who have replied so far. :):popcorn:

---

### Post by AlexBellisBrown on 2008-12-20
> **rockin_goliath said:**
> Also, if you define the drive that you have all your music and stuff on during the installation process, it will be mounted at bootup.

Ah yes, excellent point, but what if somebody created the partition after installing, like i did?:KS

---

### Post by smartboyathome on 2008-12-20
> **rockin_goliath said:**
> Actually, if you right click on the desktop icon, click properties, then click the "volume" tab, you can define a custom mount point under the "settings" drop down arrow. See the screenshot.

I have no idea how to edit fstab files or make drive labels, but this works great for me. I keep all my Rhythmbox music on me external drive, so this way every time the drive is mounted it always has the same mount point.

Cool, I didn't know that. But that would be using hal to automatically mount. You will want to talk to the hal devs to see if this is even possible before Nautilus would be likely to impliment it.

---

### Post by AlexBellisBrown on 2008-12-20
Where do you guys think we should go from here? Ubuntu idea pool? Ive never had an idea for Ubuntu before.... :)

---

### Post by smartboyathome on 2008-12-20
Nautilus dev mailing list is the next step, probably.

---

### Post by anapob on 2008-12-21
Even i had the same problem.My Exaile or amarok or infact any music player wouldn't detect my songs in the library(had to rescan evrytime i boot)........i did dig deep into the ubuntuforums and found that a application by the name STORAGE DEVICE MANAGER (type pysdm in synaptic) was able to automount it...so including it as a default package into ubuntu or allowing that feature in the partition editor would be good

---

### Post by shuttleworthwannabe on 2008-12-21
to automount my NTFS partitions (common Vista|Ubunt data and music folder) i have installed ntfs-config from the repo's. The app can then be found under Applications>System Tools>NTFS Configuration Tool

---

### Post by AlexBellisBrown on 2008-12-21
> **shuttleworthwannabe said:**
> to automount my NTFS partitions (common Vista|Ubunt data and music folder) i have installed ntfs-config from the repo's. The app can then be found under Applications>System Tools>NTFS Configuration Tool

Great! Ill give that a try in a moment.:popcorn:

---

### Post by xjcannonx on 2008-12-22
I can confirm, ntfs-config indeed works, just need to make sure whatever you want to automount is unmounted at the time you run NTFS configuration Tool

---

### Post by shuttleworthwannabe on 2008-12-22
Here is a simple [HOWTO]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html"). I have been using it since feisty days. However, this feature (ntfs-config) is not standard in Ubuntu because I read somewhere that it is a security hazard???. Could some some confirm or elaborate further on this?

---

### Post by AlexBellisBrown on 2008-12-24
> **xjcannonx said:**
> I can confirm, ntfs-config indeed works, just need to make sure whatever you want to automount is unmounted at the time you run NTFS configuration Tool

Second, it now mounts BOTH my ntfs partitions automatically, on boot, but, of course, as the program is not installed by default, and as the poster above states, could it be a security risk? I appreciate there is a how-to, but thats not the way forward. People want things to "just work", im thinking of a cross between Control Panel, and System monitor. If you could see a list of your partitions/HDD´s, whatever, and a tickbox on either to boot automatically or not, surely thats better than a how-to? 

Actually, now that i come to think of it, why isnt there a Control-Panel-esk thing in Ubuntu. Think about it,it could pool most of whats in System-Preferences/Admin into one box. Display settings, Partition Settings, Etc, and it would be familiar to people experienced in Windows.

:popcorn::popcorn:

---

