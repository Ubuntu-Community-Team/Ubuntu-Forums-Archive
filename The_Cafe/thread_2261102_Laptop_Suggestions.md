---
title: "Laptop Suggestions"
date: 2015-01-16
forum: The Cafe
---

### Post by Jedwinjim on 2015-01-16
Hi hi, I'm in need of a new laptop as for the amount it will cost to repair mine I might as well get something new as its been a few years since my last purchase.

my rather basic requirements...

- 128/256gig SSD
- 4/8gig Ram
- battery life MIN 6 hours
- around the 14" screen size, preferably matte finish, preferably no bigger
- robust casing, probably will get bashed around a bit
- super light & portable, will come with me to and from work everyday, and I walk. 
- preferably OS free (unlikely I know)

budget around £600, happy to buy something second hand, or spend a bit more if someone can assure me its worth the extra dollar. After spending a couple of days looking around I was thinking the Samsung ATIV book 9 lite hit all the criteria, but a little more research suggests I will encounter quite a few problems getting UBUNTU on it, it would be nice to have something that will welcome UBUNTU going on hassle free straight out of the box. A local shop has a used HP Elitebook Folio 9470M (i5/4gigRam/250gigSSD) for £350 seems like a good deal no?

I'm UK based, so would like something bought here, rather than mail order only from US etc.

I'm here to get personal recommendations from peeps, not asking you to do the google searching for me :p

Many thanks xxx

---

### Post by oldfred on 2015-01-16
Almost all the laptops with UEFI and secure boot have issues. And now most vendors are internally modifying the UEFI to only boot the "Windows Boot" entry by description. 

We have multiple work arounds as if only Ubuntu we rename grub entry in UEFI to be "Windows" or create/rename the hard drive boot entry to be grub.

One user posted that he buys a system with a hard drive, and removes it before even booting Windows. Then installs SSD. Later he sells system and puts hard drive back in, so it has a "brand new" unused Windows. Not sure if all new thin laptops make it easy to swap drives.

       Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.

    
 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)

---

### Post by Barsoom88 on 2015-01-16
You might look into a Dell since they are still "friendly" towards Ubuntu distros.

---

### Post by grahammechanical on 2015-01-16
I recently tried searching the Dell UK web site for Ubuntu laptops and the only machine that was advertised as coming with Ubuntu was a nice but expensive laptop marketed as "developer machine." Hardly a consumer product.

Personally, after seeing all the problem posts on the forum, I would prefer purchasing a machine with Ubuntu pre-installed then mess with trying to get Ubuntu installed afterwards. If I was going to buy a new laptop, that is.

As for the hardware specification. Computers hardware has long since reached the point where the machines can do what ordinary users want to do without coming close to making maximum use of CPU and Memory resources.

Regards.

---

### Post by Jedwinjim on 2015-01-16
crikey, I didn't realise modern laptops were so inhospitable towards linux!

In that case, anyone have any good recommendations for laptops in the UK that come OS free? I bought my last one from NOVATECH which I thought was a pretty solid purchase but I went on their website yesterday & it would seem they too now only do windows machines & have dropped the option for buying OS free which is a huge shame & I think a step backwards (it was afterall the only reason I bought from them first time round).

---

### Post by PhilGil on 2015-01-16
[Dell's new XPS 13](http://www.dell.com/us/p/xps-13-9343-laptop/pd?ref=PD_OC) sounds almost prefect for you. A Linux version is supposed released in a couple of months, so I assume the hardware is Linux friendly. Other suggestions (although not as slim and light) would be something from the Dell Latitude line or a Lenovo Thinkpad, which typically have decent Linux support. Generally speaking enterprise-grade devices will have better Linux support than consumer gear.

---

### Post by Jedwinjim on 2015-01-16
Thanks Phil, the Dell does indeed look like a good fit, watching a couple on ebay, might be able to snag one for around a monkey!

---

