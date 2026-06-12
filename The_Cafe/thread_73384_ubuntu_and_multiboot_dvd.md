---
title: "ubuntu and multiboot dvd"
date: 2005-10-08
forum: The Cafe
---

### Post by kingroach on 2005-10-08
I am creating a multiboot dvd with windows pe, windows xp and all other crap.. Now, I wanna add ubunu live cd to the dvd.. so I place the files in dvd and load isolinux.. ubuntu boots fine but after I select my lanuage, and keyboard.. it starts scanning for cd and gives me "ubuntu cd not found error".. well its defenately not an ubuntu cd since many other things are there.. I was wondering if theres anyway I can disable the check.. :confused: :confused:

---

### Post by UbuWu on 2005-10-10
Did you copy the .disk directory as well? (it is a hidden directory) I think it checks for files in this directory.

---

### Post by Padvinder on 2005-10-14
[QUOTE=kingroach]I am creating a multiboot dvd with windows pe, windows xp and all other crap.. Now, I wanna add ubunu live cd to the dvd.. so I place the files in dvd and load isolinux.. ubuntu boots fine but after I select my lanuage, and keyboard.. it starts scanning for cd and gives me "ubuntu cd not found error".. well its defenately not an ubuntu cd since many other things are there.. I was wondering if theres anyway I can disable the check.. :confused: :confused:[/QUOTE]

I had a problem which looked simulair to what you describe. In my case Ubuntu seemed to have a problem with my IDE ( PATA ) and SATA disk detection.

I solved the problem to config a BIOS setting. Maybe this information is usefull for you!

Goodluck! ;)

---

### Post by Padvinder on 2005-10-14
[QUOTE=Padvinder]I solved the problem to config a BIOS setting. Maybe this information is usefull for you![/QUOTE]

Maybe some usefull links :

[LIST]
[*][http://linuxmafia.com/faq/Hardware/sata.html]("http://linuxmafia.com/faq/Hardware/sata.html")
[*][http://ubuntuforums.org/archive/index.php/t-4422.html]("http://ubuntuforums.org/archive/index.php/t-4422.html")
[/LIST]

Edit : Maybe I have to read better next time! Your CD is probably working correct with your hardware since you want to make a dual boot cd of it! My bad!

---

### Post by Omnibian on 2005-10-18
I was also searching for a way to do that, and found yesterday (I downloaded Ubuntu sources and found the "cd checker" validation code, which is a combination of c code and shell script).

To add the Live CD to any isolinux based multiboot DVD, copy all these elements from the Live CD root to the multiboot DVD root :
- Folders : .disk, casper, disctree, dists, doc, install, pics, pool, preseed
- Files : README.diskdefines, ubuntu
(other folders seems to be only Windows stuff used for autorun or OpenOffice win32 setup ...). The Live CD seems to work well without.

Add the Ubuntu Live CD boot command to your custom isolinux.cfg file (may be in /boot/isolinux or /isolinux depending on the DVD layout) : just copy one of the Live CD boot commands (found in /isolinux/isolinux.cfg).

And now the magic patch :
- go into folder /dists, 
- delete the file "stable",
- create a new directory "stable" (lower case) in place of the deleted file,
- copy the whole /dists/breezy content (including sub folders) into /dists/stable.

That should work (it's ok for my combo DVD, tested on 2 computers, which includes Ubcd, Ubcd4win, Breezy Live, Knoppix, Auditor, Damn Small Linux, Slax, RIP, Freedos, and Acronis TrueImage / PartitionExpert, all stuff managed with cdshell, bcdw and isolinux).

In fact some debian code inside the "cd checker" shell script tries to read the "Release" file in /dists/stable, /dists/unstable or /dists/testing, not in /dists/breezy.

Anyway, I don't know how the original Live CD may boot without that missing folder.

Sorry if some typos or miswordings in my english, I am not an english native speaker.

Hope that will help you.

---

