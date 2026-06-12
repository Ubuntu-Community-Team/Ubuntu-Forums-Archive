---
title: "Ubuntu 7.1 Installation horror story, semi-happy ending"
date: 2007-11-26
forum: Testimonials &amp; Experiences
---

### Post by Semi-clueful Newby on 2007-11-26
Maybe this is an old story.  If it is, then shame on Ubuntu installer authors. Otherwise, maybe somebody will fix the Ubuntu 7.1 installation CD.

I've been running Windoz 98 for years, not because I like it, but because it is there, my (fairly obscure and old) installed apps work, and I tend to adhere to the principle "if it works, don't fix it".   The following account is very foreshortened.  The process actually took several days.

A friend handed me the Ubuntu 7.1 CD.  I decided that a cautious move, installing dual boot Windoz/Ubuntu on a new HD would be a reasonable first step away from Windoz.  So, I got a new 320 gig HD, moved my Windoz installation (2 FAT32 partitions) to the first 128 gigs, and left the rest untouched.  Then I went to install Ubuntu 7.1 from the CD.

Saving my old HD for backup, and knowing how to fix a broken boot sector, saved me the ultimate horrors, but what I endured was bad enough to tell me why more people don't migrate.

Firing up the Ubuntu CD, I clicked on "install" and let 'er rip.  The installer noted the 2 FAT32 partitions, and I let it install Ubuntu on the unused real estate.  After an apparently successful install, I clicked on "reboot", hoping to see Grub allow me to select between Windoz and Ubuntu Linux.

Instead, Grub died unceremoniously after printing "Error 18" on my monitor.  Now I couldn't boot either Windoz or Linux.  Back to the drawing board. I fixed the boot sector to boot Windoz only, and repeated the exercise, this time telling Ubuntu installer to use the entire HD.  I hoped that would propitiate the Linux gods by eliminating my Windoz installation entirely.  Wrong.

After the install, Grub died the same way.   Now having a completely useless HD, I recloned from my backup.  Rinse, lather, repeat, thinking I had made some silly error following the Ubuntu instructions..  Same results.  So, I reclone again, fire up Windoz, and google for information about this hideously touchy Grub with its entirely uninformative "Error 18" message.  Finally, in some obscure forum somewhere, I found a buried message from someone with similar experience.  The upshot was that Grub can't handle booting from a partition that starts above 128 gigs.

So, reclone from backup, but with smaller FAT32 partitions.  Reinstall from Ubuntu CD.  This time it went well.

So why don't more people migrate to Linux?  I'm actually surprised that anybody would have to ask the question.  But here are a couple of good reasons:

1. The Ubuntu installer does not warn them that an installation will trash their master boot record with a useless boot loader if their Windoz partitions are too big.

2. Grub will die with an utterly uninformative error message.

There is really no excuse for any organization laying any claim to professionalism putting out an installation disk that will willy-nilly trash a prospective user's HD without warning.   There is no excuse for not issuing a message about the partitioning issue on the first screen of the installer, or even on the first screen when booting from CD.   There is no excuse for Grub issuing an error message that is utterly useless without a new user going to the 'net and googling for an answer.

Why do I say no excuse?  Because I'm a crotchety retired old fart.  I was programming computers before most Linux enthusiasts were a twinkle in their parents' eyes, and before even the 8080 existed.  In my day, delivering a piece of software that would crash a system without warning, especially if the condition that could cause the crash was simple and easily corrected, would be a firing offense.

If step one of my experience happened to most prospective users, they would likely throw up their hands and walk away hating Ubuntu for trashing their hard drive that they hadn't bothered to back up.  Maybe they'd realize that the installer only trashed their boot sector and they could recover their data to make a backup. Or maybe not.  Either way, they wouldn't be inclined to ever try Linux again.

The belief that Linux is "unfriendly" has long been widespread. For Linux proponents to put out a distro disk which proves that belief beyond a shadow of a doubt isn't just stupid -- it's marketplace suicide.

---

### Post by Roaster on 2007-11-26
"The upshot was that Grub can't handle booting from a partition that starts above 128 gigs." That is an interesting bit of information. How many of you fine folks here knew that? And I agree, that should be addressed. I have had 'some' unpleasant experiences with grub since I started using Ubuntu, but I'm still learning to like Ubuntu more each day. The best part about it is the support you can find, which, apparently, you did.  Best to you, btw, I'm a crotchety, old fart too!:)

---

### Post by adapterSD on 2007-12-11
I wanted to start a new thread called "A story of one installation..." but the wise Linux server suggested one of the existing threads with a similar topic. So, I'm posting here another comment on the difficulties of Ubuntu installation.

I had Windows XP on my Acer Aspire 3050-1908 laptop and it worked fine. By fine I mean, the display worked at 1280x800, I had Wi-Fi and network (cable) Internet capabilities, I could type in multiple languages and switch keyboard layouts on the fly, and - of course - I could watch encoded (blockbuster) DVD movies for hours on end.

But then it started looking like it was too easy. Everything works ... where' s the fun?

So, I downloaded an ISO-image of a Mandriva 2008. Installed it on a 2nd partition (alongside with XP) but somehow I wasn't happy. I googled "best linux distro for beginners" and UBUNTU came up in a story by PC World. Hey, I know this name! I tried Ubuntu a couple of years ago, when it just appeared on the scene.

So I erased the entire disk and installed Ubuntu thus becoming a 100% linux comp user. Well, it seemed like a good idea for a few hours (I made backup of my most important files from the XP system, so I didn't lose anything) BUT:

Wi-Fi Internet didn't work
ATI display couldn't master 1280x800 res and I just couldn't make the new downloaded drivers to work.
Sound card didn't work.
Keyboard layouts were impossible to switch (at least I didn't see where I can activate the switches, so that I can write a letter - let's say - in 2 languages)
Booting took forever

The only thing that worked was the regular Internet by cable, but the speed of downloading was constantly changing. I was in the same spot a couple of days ago when I had the XP system on the laptop, and the speed of downloads - connected via supposedly slower WiFi - was much much faster. It was then that I was able to download these huge ISO installation images of Linux distros.

So, I wasn't happy. Couldn't find any answer re: the main problem of the display drivers in HELP or online. Googled "linux drivers acer laptops" and almost hits were complaints from people who couldn't get linux to work properly on an acer laptop.

Well, now I don't have any Windows. Smart folks at Acer don't give you an installation CD anymore ... they hide the system backup in the "invisible" sector on the disk, which I naturally erased (down with windows!).

So, what's left? Well, I thought 5 minutes and then ... reinstalled Mandriva 2008. Took me a while to erase the old bootloaders (they survived 3 re-installations) but after 2 hours I have a Mandriva working:

Wi-Fi W-O-R-K-S!!!!
Can't hear any sounds :(  but
Display looks much nicer than under Ubuntu, and it produces 1280x800 dpi res!
Keyboard layouts are easy to add, edit and switch. I already tried typing in Russian and English - it works!
Booting is fast, and the whole system is flying.

I'm one happy camper. Sorry, Ubuntu...

Here's my system config:
Acer Aspire 3050, ATI Radeon Xpress 1100, Mobile AMD Sempron 3400+, 14.1" inch WXGA 1280x800, 80 Gb hdd, dvd-burner, 1.5 Gb Ram, 802.11g Wi-Fi.

---

### Post by Threbus5 on 2007-12-12
Hi,

Well, you admit it, you wanted to play. Ouch!
Anyway, if all else fails, consider an OEM XP Windows install disk. They cost about $100.

Install Windows, add a VMware server for Ubuntu, then play.

Have fun

---

### Post by kevinatkins on 2007-12-12
Hi,

Installation problems can be very offputting but Linux isn't alone there - after all, most machines come with Windows pre-loaded, so most people never have to tangle with a full Windows install. And I remember, ruefully, when I upgraded a laptop running XP to Service Pack 2, only to be presented with a completely black screen on reboot..... after Googling, it turned out that the laptop's video card was no longer properly supported by SP2, nor was there any hope of the card manufacturer issuing a driver update - it took a bit of jiggery pokery to persuade the card to behave.

---

### Post by t0p on 2007-12-12
> **Semi-clueful Newby said:**
> 
So why don't more people migrate to Linux?  I'm actually surprised that anybody would have to ask the question.  But here are a couple of good reasons:

1. The Ubuntu installer does not warn them that an installation will trash their master boot record with a useless boot loader if their Windoz partitions are too big.

2. Grub will die with an utterly uninformative error message.

There is really no excuse for any organization laying any claim to professionalism putting out an installation disk that will willy-nilly trash a prospective user's HD without warning.   There is no excuse for not issuing a message about the partitioning issue on the first screen of the installer, or even on the first screen when booting from CD.   There is no excuse for Grub issuing an error message that is utterly useless without a new user going to the 'net and googling for an answer.
.

That's a **Grub** issue, not an Ubuntu issue.  Sez me.

---

### Post by Iceni on 2007-12-12
Weird, I have a 250-gb windows partition and grub gave me no errors. Maybe it is the comination of fat32 and grub thats giving you trouble.

---

### Post by forestpixie on 2007-12-12
might well be a grub issue but that's beside the point isn't it

---

### Post by Iceni on 2007-12-12
Yep, agreed. When a product is delivered it is the responsibility of the company that put it together. You don't see Merchedes blaming siemens because their E-series are crap, despite those parts being part of the messup.

---

### Post by cowkiller on 2007-12-12
Anyway Ubuntu comes with absolutely no warranty, isn't it?
But sooner or later, at least in my case, the solution was found at any forum or howto... and I've found myself dealing with much more problems with ubuntu than I'd like to, mostly at first.

On the other hand, I can tell about a problem I've got now with vista (preinstalled in my laptop, no chance to refuse or change, of course :D ) . At some random point the resoultion switches to 1024x768 and that's that. I found no support from Microsoft, neither from any forum I searched... 

so why don't more people migrate to linux? Because most of them think that Computers are like a freezer or a Tv, and they should work like that (wich is close to MS philosophy about users)

---

### Post by Sef on 2007-12-12
> The upshot was that Grub can't handle booting from a partition that starts above 128 gigs.

And Windows has to be on the first partition.  They all have their frustating quirks.

---

### Post by philinux on 2007-12-12
The best way to run ubuntu/linux is on another separate hard drive. They're so cheap now too.

---

### Post by Wynne G Oldman on 2007-12-12
Just to balance things a bit, I installed XP on an IBM x225 yesterday. I already had Ubuntu on it, and it picked up everything, first time, including  sound, LSI U320 adapter and Broadcom gigabit adapter. I've had to download the drivers for these from IBM's website to get them working with XP. There's still a few devices with question marks next to them in Hardware Manager, that I haven't had time to resolve yet.

---

### Post by gjtoth on 2007-12-12
> **Iceni said:**
> Weird, I have a 250-gb windows partition and grub gave me no errors. Maybe it is the comination of fat32 and grub thats giving you trouble.

Same here.  My partition is also 250GB.  Although, it's not FAT or NTFS.  Still...  it's over 128GB.  Come to think of it, before I dumped Windows totally (on this same system) I had no problems.  That was from version 6.10 on up.

Hmmmmmmmmm... SOMETHING'S goofy here.

---

### Post by Wynne G Oldman on 2007-12-28
My happy ending is that after trying lots of Linux distro's, and Vista, I am now a 100% Gutsy 64 bit user. (Freespire came a close second as an easy to set up and use OS). Even though it's free, and Vista costs a lot of cash, I think Gutsy is an all round better OS. Many thanks to all the good people who have put their time and money into developing Ubuntu. Much appreciated! :)

---

