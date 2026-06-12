---
title: "Need to trim Vista for a dual boot"
date: 2008-10-09
forum: Windows
---

### Post by Helios1276 on 2008-10-09
Hey folks, the new laptop just arrived with Vista, I had managed to avoid it until now. Anyway, I'm getting ready to get some Linux on here(dual boot) but Vista is taking ALOT of my hd! I'm just wondering if anyone has any experience of slimming down Vista a bit. I got rid of most of the bloatware that came with the laptop but still see alot of space 'occupied'. Went to the command line and ran 'dir' ..wow..compared to XP there is ALOT going on! It's possible I'm just naive to the ways of Windows latest spawn:).

---

### Post by bpalone on 2008-10-09
I am no help on trimming it.  But it is obscenely OBESE.  SP1 was a 50 meg download and required something like 50 gig to install.  I can't remember for sure, but I like to of fallen out of my chair when I read it.  I don't have it and refuse to have it. Of course, I didn't like XP either, just tolerated it on some newer equip.  

Good luck on getting it trimmed down.  Might try a Google for VistaLite.  There are some things out there for make lite versions of 2000 & XP.  Maybe they have done something on Vista.

---

### Post by neoAnderson on 2008-10-10
My HP laptop had a lot of HP stuff - HP connections, HP total health care adviser, etc etc - you can remove a lot of stuff. But unless you want to render your Vista partition useless, be careful with what you remove ;-)

---

### Post by Helios1276 on 2008-10-10
> **neoAnderson said:**
> My HP laptop had a lot of HP stuff - HP connections, HP total health care adviser, etc etc - you can remove a lot of stuff. But unless you want to render your Vista partition useless, be careful with what you remove ;-)

Same here, HP laptop fulla crap lol. It just boggles my mind how much space I'm losing to Vista , it's a 250 gb Hd (the laptop is a week old) and Vista is taking up almost 60 gb already?! Worst thing is , I can't for the life of me see where all this space is going??.If I could run the Bluray drive in Ubuntu it would be gone!

---

### Post by fiddledd on 2008-10-10
> **Helios1276 said:**
> Same here, HP laptop fulla crap lol. It just boggles my mind how much space I'm losing to Vista , it's a 250 gb Hd (the laptop is a week old) and Vista is taking up almost 60 gb already?! Worst thing is , I can't for the life of me see where all this space is going??.If I could run the Bluray drive in Ubuntu it would be gone!

I can't imagine how 60gb can be used up. My Laptop with Vista installed, and with all my programs and documents added, isn't even 25gb.

Of that 25gb 11gb is the recovery partition. So Vista is 14gb, but that's with my stuff added.

Oh, and I've been using Vista on this Laptop for nearly 8 months now.

Download [WinDirStat](http://windirstat.info/), it's FOSS. It will show you exactly what space is used by every file.

---

### Post by Tomatz on 2008-10-10
If you are planing to use ubuntu as your main OS then i would advise that you format, install XP then install ubuntu.

There really is no reason to have vista ;)

---

### Post by Helios1276 on 2008-10-10
> **Tomatz said:**
> If you are planing to use ubuntu as your main OS then i would advise that you format, install XP then install ubuntu.

There really is no reason to have vista ;)

The only thing keeping me with Vista is HP telling me my Bluray drive wont work with anything but their  pre-installed software:mad:. But ya, the drive is 250 gb: 11 recovery and apparently 185 of 221 on C free, this is after I took about 35/40 gb of my own personal files off the drive. The numbers make me mad.

---

### Post by Helios1276 on 2008-10-10
> **fiddledd said:**
> I can't imagine how 60gb can be used up. My Laptop with Vista installed, and with all my programs and documents added, isn't even 25gb.

Of that 25gb 11gb is the recovery partition. So Vista is 14gb, but that's with my stuff added.

Oh, and I've been using Vista on this Laptop for nearly 8 months now.

Download [WinDirStat](http://windirstat.info/), it's FOSS. It will show you exactly what space is used by every file.

Thanks for the link, It looks a little something like this , the windows folder is 10 gb and the Temp folder is just over 9 gb, with Files and and others making up a further 20 odd now that I have cleared the vast majority of my stuff off ( ie. Music /Photos). I'm determined to get a lean Vista install, by hook or by crook..failing that I'll Dban it into the ether. I won't suffer this just for Bluray lol

---

### Post by fiddledd on 2008-10-11
> **Helios1276 said:**
> Thanks for the link, It looks a little something like this , the windows folder is 10 gb and the Temp folder is just over 9 gb, with Files and and others making up a further 20 odd now that I have cleared the vast majority of my stuff off ( ie. Music /Photos). I'm determined to get a lean Vista install, by hook or by crook..failing that I'll Dban it into the ether. I won't suffer this just for Bluray lol

If you look in the Windows folder you'll see a winsxs folder, this will be the largest folder. It's windows answer to backwards compatibility and keeps dlls etc for older programs. Unfortunately you can't touch it, as doing so will bork Vista.

The Temp folder can mostly be cleared, I suggest you run Disk Cleanup and also get [CCleaner](http://www.ccleaner.com/), that will clear out a lot of temp files.

---

### Post by Tomatz on 2008-10-11
Aparently media player classic supports blue ray discs under xp but i dont know if it can decrypt protected content. You could try it under vista and if it does you can just install XP.

[http://sourceforge.net/projects/guliverkli2/](http://sourceforge.net/projects/guliverkli2/)

I have posted a link below on how to streamline vista but i dont think you will save much space doing so.

[http://www.pcstats.com/articleview.cfm?articleid=2238&page=20](http://www.pcstats.com/articleview.cfm?articleid=2238&page=20)

Other than that you are pretty much stuck with vista. Now go do as Steve B says and buy a new HDD ;)

---

### Post by I-75 on 2008-10-11
Trimmimg Vista

Turn off UAC
Turn off System Restore
Turn Off Windows Defender
Turn Off Aero
Turn Off Norton Anti virus  Replace with AVG
Turn off Indexing Feature.

Vista should run better (relatively speaking). Vista also has a good built in partition shrink program if you want to do a permanent installation and install Ubuntu on the freed partition.

---

### Post by fiddledd on 2008-10-11
> **I-75 said:**
> Trimmimg Vista

Turn off UAC
Turn off System Restore
Turn Off Windows Defender
Turn Off Aero
Turn Off Norton Anti virus  Replace with AVG
Turn off Indexing Feature.


None of the above, apart from "Turn Off System Restore", will increase disk space, which is what the OP is asking.

I would also leave UAC, Windows Defender, and Aero.

I can think of no good reason to reduce Vista's security by disabling UAC, it is no more annoying than sudo in Linux.

The only reason to disable Aero is if your Hardware isn't up to it. 

Windows Defender has successfully kept Vista free from spyware on my Laptop for nearly 8 months (yes, I have used Spybot and Adaware to check it hasn't missed anything). Also Windows Defender does more than check for spyware, it gives you control of startup programs and services, and monitors any system wide changes.

As for AV software, I ran Avast for 8 months, it never detected anything(yes, I checked with other scanners), so I now use Clamwin, which is FOSS. It's not a resident scanner, so I scan once a week or before installing a new program.

---

### Post by SunnyRabbiera on 2008-10-11
me I would have just trashed the blueray drive and replace it with a DVD one, really why support a format that is corrupt and pro DRM just to view movies in HD?
I am all for boycotting blueray.

---

### Post by handy on 2008-10-11
> **sunnyrabbiera said:**
> me i would have just trashed the blueray drive and replace it with a dvd one, really why support a format that is corrupt and pro drm just to view movies in hd?
I am all for boycotting blueray.

+1

---

### Post by Helios1276 on 2008-10-11
Ok, well with regards to boycotting Bluray, I went the HD DVD route first to avoid Bluray (Xbox peripheral), this bit me in the ***. So I have a Plasma tv and it's going to waste.I buy Bluray for the simple fact that there is no alternative. Are you driving electric cars and turning your back on the oil companies? 

Secondly, I gave the Vista partitioner a shot but pagefiling wont allow me to make much of a dent, so I need to look up turning that off. Norton already got the boot as soon as the laptop booted up, along with office 2007 and other useless junk. The perfomance is not really the issue as the laptop is well able to cope. Though admittedly I can envisage Vista getting slower as time goes by. I merely want Vista down to a small install for playing Bluray and the odd game that requires it.

As for the alternative Bluray player ideas, I'm going to give them a shot but the encryption support might be a stumbling block.

---

### Post by Helios1276 on 2008-10-12
Update: Wiped the drive with the plan of installing Ubuntu and then re-installing Vista. Ubuntu went fine , set up my partitions and then The Vista recovery disc freakout out and failed on me..currently emailing HP to send me a working disc.

---

### Post by Tomatz on 2008-10-12
> **Helios1276 said:**
> Update: Wiped the drive with the plan of installing Ubuntu and then re-installing Vista. Ubuntu went fine , set up my partitions and then The Vista recovery disc freakout out and failed on me..currently emailing HP to send me a working disc.

I would install vista, then ubuntu ;)

---

### Post by Helios1276 on 2008-10-12
> **Tomatz said:**
> I would install vista, then ubuntu ;)

I think the disk is the problem ;)

---

### Post by Tomatz on 2008-10-13
> **Helios1276 said:**
> I think the disk is the problem ;)

The problem is that the recovery disc is just an image of an installed OS (its not a regular install disc). It's probably having a problem with the HDD's partitioning (or lack of). Besides you should always install Windows first before installing ubuntu because the windows bootloader overwrites grub. ;)

---

### Post by ivikas on 2008-10-13
Hello,

        There is an option in vista by which you can resize your partition.click  on right mouse button computer and from there you will get "manage disk" option and give the size you want to free to install ubuntu.Please do not alter the recovery disk partition or otherwise your vista will be in trouble.Also if you will find that your vista will be slow on 1GB Ram(though recommended).There is optimization for vista by which you can speed up vista booting and response time(do googling).

                          After freeing a partition,put the ubuntu  cd to install and hopefully it will pick up the partition that was freed by vista and repartition it to root and swap to install ubuntu.

---

### Post by Helios1276 on 2008-10-13
> **Tomatz said:**
> The problem is that the recovery disc is just an image of an installed OS (its not a regular install disc). It's probably having a problem with the HDD's partitioning (or lack of). Besides you should always install Windows first before installing ubuntu because the windows bootloader overwrites grub. ;)

your right ;)

---

### Post by Helios1276 on 2008-10-13
> **ivikas said:**
> Hello,

        There is an option in vista by which you can resize your partition.click  on right mouse button computer and from there you will get "manage disk" option and give the size you want to free to install ubuntu.Please do not alter the recovery disk partition or otherwise your vista will be in trouble.Also if you will find that your vista will be slow on 1GB Ram(though recommended).There is optimization for vista by which you can speed up vista booting and response time(do googling).

                          After freeing a partition,put the ubuntu  cd to install and hopefully it will pick up the partition that was freed by vista and repartition it to root and swap to install ubuntu.

Cheers for the post , I'm way beyond that now though. Impatience with Vista and not having a distro to mess with forced my hand and I destroyed Vista lol Also, that partitioner in Vista is horrible.

---

### Post by Helios1276 on 2008-10-17
Trimming is no longer my only problem, Recovering Vista is proving irksome: [http://ubuntuforums.org/showthread.php?t=950819](http://ubuntuforums.org/showthread.php?t=950819)

---

