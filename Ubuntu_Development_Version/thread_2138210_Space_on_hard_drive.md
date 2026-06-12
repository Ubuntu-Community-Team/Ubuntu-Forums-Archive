---
title: "Space on hard drive"
date: 2013-04-23
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-04-23
I've been happily using Ubuntu (12.10 & 13.04 daily) now for about 2 months. I've noticed on different sites differing advice about cleaning the junk off of hard drives. I'm a relative novice regarding Linux but have a great deal of computing experience. I've made a remastersys backup of 12.10 and am using 13.04 daily exclusively on my laptop.

My daily routine for 13.04 is sudo apt-get {update, upgrade, dist-upgrade, clean, autoclean, autoremove, bleachbit} I'm somewhat perplexed about all the 'junk' that I've been removing daily from my hard drive by using bleachbit. Normally about 30 - 50 Mb is freed. I've never experienced a fault upon reboot, and everything appears to be normal. 

Is my experience to be expected when using a 'beta' with the above procedures?

What advice should be provided to relatively inexperienced users regarding disk cleanup?

---

### Post by ibjsb4 on 2013-04-23
Clean, autoclean and autoremove are part of BleachBit.  Doing those commands separately is not nercessary.  And I don't think daily is necessary, probably once a month if you have to go by a schedule.  I probably use it 6 or 8 times a year.

I don't know how you have your BB set up, but my guess is that 20/50MB is your browser.

---

### Post by dino99 on 2013-04-23
The most important is to understand the settings/apps used
If you dont, then ignore it/them; except if you are hunting a breakage.

---

### Post by pfeiffep on 2013-04-23
> **ibjsb4 said:**
> Clean, autoclean and autoremove are part of BleachBit.  Doing those commands separately is not nercessary.  And I don't think daily is necessary, probably once a month if you have to go by a schedule.  I probably use it 6 or 8 times a year.

I don't know how you have your BB set up, but my guess is that 20/50MB is your browser.

Thanks for your reply. 
I think that daily is important for using a beta and keeping it up-to-date. I certain don't think that more than weekly for a released OS should be required - and maybe software updater should do the trick.

20 - 50 Mb daily seems like quite a bit for Chromium and Thunderbird. At that rate (without cleaning up) I'd soon fill up this 40Gb hard drive with stuff that I obviously don't require!

> [COLOR=#000000]dino99[/COLOR]
[COLOR=#000000][INDENT]**Re: Space on hard drive**
The most important is to understand the settings/apps used
If you dont, then ignore it/them; except if you are hunting a breakage.[/INDENT]
[/COLOR]
   
Thanks for your reply. 
I believe that someone else on these forums has s signature loosely quoted ... [I][COLOR=#b22222]if you haven't broken it you haven't tweaked it enough[/COLOR]
[/I]I'm using this laptop as a learning tool - my real system benefits from all the hard knocks education obtained by experimenting!

---

### Post by dino99 on 2013-04-23
to limit the package updates flood, you can disable the "proposed" archive inside /etc/apt/sources.list ( set : # above the line to comment it out)

---

### Post by Mathor on 2013-04-23
It's a good idea to periodically use synaptic or terminal to remove your unused config files and your unused kernel versions. Keep the kernel versions on hand for a day or so in case a recent kernel does not work, then remove them. Those cleaning programs are sort of useless, imho. Cookies and log files will load up in your /home folder (usually have to select 'show hidden files' in nautilus), and if you are not using those files, it's completely harmless to remove those as well.

edit: autoremove works wonders as well :)

---

### Post by pfeiffep on 2013-04-23
:)> **dino99 said:**
> to limit the package updates flood, you can disable the "proposed" archive inside /etc/apt/sources.list ( set : # above the line to comment it out)

Yes I've done that on my 12.10 installation ..... thanks

> [COLOR=#000000]Mathor[/COLOR]
[COLOR=#000000][INDENT]**Re: Space on hard drive**
It's a good idea to periodically use synaptic or terminal to remove your unused config files and your unused kernel versions. Keep the kernel versions on hand for a day or so in case a recent kernel does not work, then remove them. Those cleaning programs are sort of useless, imho. Cookies and log files will load up in your /home folder (usually have to select 'show hidden files' in nautilus), and if you are not using those files, it's completely harmless to remove those as well.

edit: autoremove works wonders as well :smile:[/INDENT]
[/COLOR]


Thanks - I use and Synaptic (great for identifying dependencies) and daily :)use the terminal. I think bleachbit removes most of the crud from Chromium and T-Bird effectively.

I'm really comfortable in my own practices ... I'm interested in what to advise ***others*** regarding keeping their installation up to date and clean. Many folks don't have the experience nor the inclination to 'get their hands dirty' with the command line. I'm a bit hesitant to suggest bleachbit because it can do some real damage is used incorrectly. I'm learning by researching other's questions and answering them!

---

