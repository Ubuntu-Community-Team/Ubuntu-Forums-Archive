---
title: "Had to reinstall Win98 and WinXp today..."
date: 2006-08-04
forum: The Cafe
---

### Post by Luk8 on 2006-08-04
And I can say it was a really big pain in the ... :) . Compared to Ubuntu I can say that they are MUCH harder to install. I just wasted a couple of hours today searching through tens of cds to find the one with the proper Win drivers , setting up stuff , finding free av and firewall . downloading installing , getting some media apps. This was the first time I had to install WinXP and Win98 after Breezy and Dapper and I can say I was really losing patience. Only now I see how is easy is to get Dapper up and running with pretty much everything you need (except gaming and some media codecs).Did anyone do this kind of work recently and can confirm that installing Win$ AND making it run properly is really harder then Ubuntu? *opens eyes*
God bless Ubuntu,Debian,Mark Shuttleworth and all people on this world !:KS

---

### Post by Toe on 2006-08-04
I know exactly what you're talking about.

Today I completely wiped my little brother's harddisk (his XP was in bad shape) and installed a dual-boot Ubuntu and XP-system.

By the way: He loves Ubuntu and only keeps Windows on his PC until Guild Wars works with Wine. He has even already put an Ubuntu sticker on his machine :D

Setting up Ubuntu was extremely easy. Everything ( ! ) just worked :)

XP on the other hand took way longer to install. During the basic install process I already wished for more verbose output. It's weird to only have the HDD light and an animated icon on the screen tell you that your system is still doing something.

The first major problem occured when Windows (with SP2 preinstalled) couldn't detect the ethernet card.
So I switched to Ubuntu's device manager, wrote down the specs (Broadcom) and downloaded the XP driver.
It still refused to work though.
At that point I considered exchanging my PC's ethernet card with my brother's and opened the case.
There I realized what was wrong: My brother's ethernet is onboard!
So the search for the mainboard driver CD began.

This little piece of plastic also solved the problem of missing sound (in XP - in Ubuntu, of course, it worked ;) ).

After that I fetched the latest DirectX, graphics drivers, antivirus software, WinTV drivers, lots of Windows Updates and had to click my way through countless installers, each one with its own kind of user interface.

The Ubuntu install on the other hand was painless: Basic install, install updates, run Automatix, fine-tune xorg.conf (got rid of the Nvidia logo), add a nice Grub-bootimage. Done :)

---

### Post by Michael_aust on 2006-08-04
Even if you had to install all the rubbish on ubuntu you have to install on windows (except drivers), its is still quicker in Ubuntu, everything is a quick apt-get install packagename, away.  Noen of this having to go to the site, find the download, doible click etc etc.

---

### Post by x64Jimbo on 2006-08-04
You should start using aptitude instead of apt-get. It handles the dependencies much more thoroughly & accurately than apt-get. Of course, the best way to do it is through synaptic or adept depending on whether you're running Ubuntu or Kubuntu, but if you need to use the command line, I highly recommend aptitude.

---

### Post by G Morgan on 2006-08-04
Win98!! I feel your pain, partitioning is a PITA in 9x. If you haven't got a FAT32 partition setup it moans and complains, why not just detect partitions at the begining and drop to a prompt so I can use fdisk. Also it has to be on hda1 or it cries (I moved my Windows disc to IDE0:1 recently but fortunately Ubuntu setup grub properly for me so I didn't have to bind HD1 to HD0 manually).

---

### Post by atrus123 on 2006-08-04
You are so totally correct.

I hate listening to Windows people tell me that: "Linux has no support" or "good luck finding drivers", etc.

It is considerably easier finding Linux drivers than Windows drivers, because most Linux drivers come bundled with the OS.

If you're using Windows (especially on a laptop), and you can't find your restore disc, good, bloody luck.  You'll have to pull a bunch of files off your vendor's website, and if you're really lucky and have a Gateway laptop, many of your drivers won't even be there.

Linux is easier to install.  Nobody believes me, but it's true.

.....of course, wireless can still be a bear.

---

### Post by x64Jimbo on 2006-08-06
> **atrus123 said:**
> You are so totally correct.

I hate listening to Windows people tell me that: "Linux has no support" or "good luck finding drivers", etc.

It is considerably easier finding Linux drivers than Windows drivers, because most Linux drivers come bundled with the OS.

If you're using Windows (especially on a laptop), and you can't find your restore disc, good, bloody luck.  You'll have to pull a bunch of files off your vendor's website, and if you're really lucky and have a Gateway laptop, many of your drivers won't even be there.

Linux is easier to install.  Nobody believes me, but it's true.

.....of course, wireless can still be a bear.
The key word there is "can."
Most machines that have wireless cards built in these days will auto-configure under Linux. I have come across my fair share of weird hardware that requires special drivers, but finding them was no more difficult for Linux than it was for Windows. I'm constantly surprised and impressed by Linux and Ubuntu's progress with hardware support and Community Participation leading to better user satisfaction and retention.

---

### Post by John T. Monkey on 2006-08-06
I run a Windows XP laptop and a Kubuntu desktop (which I'm using now). 

Luckily, my laptop is a Toshiba so all the basic stuff is on the restore CDs, but then I have 12 discs I keep nearby (I just counted them) I would need to get the system up and running as I like it. That doesn't count installing Open Office, GIMP, Firefox, Trillian, Foobar, Zone Alarm, Avira Antivirus, Spybot S&D and Ad-aware, all things I use in Windows. (edit: btw I like Windows so long as it's set up right, I'm not just bashing it or anything for no reason)

On the other hand, I have two discs for my Kubuntu system. The Kubuntu Live CD I would install from, and another one with DVD and Win32 codecs, and Real Player. I would need to get one or two things from the repositories, but it's much easier to get it set up. And an awful lot faster. 

Btw the Packard Bell retore program is the worst, I hated it with a passion. It left me with a completely useless system full of junk, and lots of work to do to get it useable. And it took nearly 2 hours before I coiuld get to work on it. :(

---

