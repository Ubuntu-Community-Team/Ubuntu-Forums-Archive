---
title: "Virtualization Problems"
date: 2010-05-18
forum: Virtualisation
---

### Post by adamsiddhi on 2010-05-18
[I][COLOR="DimGray"]
**Host System:** Windows Vista Home Premium SP1 64 bit
**Guest:** Ubuntu 10.04 (ubuntu-10.04-desktop-i386.iso) 32 bit
**VM:** VirtualBox 3.1.8
**Hardware:** Intel Core 2 Duo T6400 4GB SDRAM[/COLOR][/I]

I followed the tutorial called **Installing Ubuntu inside Windows using VirtualBox** located here:
[[COLOR="Indigo"]**http://www.psychocats.net/ubuntu/virtualbox**[/COLOR]]("http://www.psychocats.net/ubuntu/virtualbox") 

At first I downloaded **ubuntu-10.04-desktop-amd64.iso** because I figured that it would be a perfect fit with my Vista 64 OS. I was wrong because it turns out the my Intel Core 2 Duo T6400 CPU does not have Intel® Virtualization Technology. So I had to go with the **ubuntu-10.04-desktop-i386.iso** which is 32 bit. 

So I set up the VM in VirtualBox to prepare for the Ubuntu 10.04 virtualization. Please go [[COLOR="Indigo"]**to my Picassa web album**[/COLOR]]("http://picasaweb.google.com/rubysiddhi/ProblemVirtualizingUbuntu100432BitOnVirtualBox31OnWindowsVista64") to see the screen shots of my VM settings and Ubuntu boot process so you can see what I experienced (they appear in the order that I experienced them in). The first 15 images are the VM settings. The last 5 show Ubuntu 10.04 booting up but failing. Perhaps there is a clue in there that can help solve this problem. 

I should also mention that I found [[COLOR="Indigo"]**this post**[/COLOR]]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1479428") in the Ubuntu forums by **zonination** who seemed to have similar problems to mine even though they had a different set up. The main issue I think zonination and me may be having is the fact that we can not change the color mode to ***32 bit*** while it is booting. I think the ***16 bit*** color mode maybe making Ubuntu fail. Not certain though.  

Well I hope I explained my problem thoroughly and clearly. Thanks for the tutorial. It got me started but, now I hope to finish this process so I can start developing in Ubuntu. 

Thanks!

Regards,
Adam

---

### Post by cariboo on 2010-05-30
@adamsiddhi this is not the place to get help for your problem. please post a question in the [Virtualization]("http:///ubuntuforums.org/forumdisplay.php?f=308") sub-forum.

---

### Post by Sef on 2010-07-31
> @adamsiddhi this is not the place to get help for your problem. please post a question in the Virtualization sub-forum.


So moved to the Virtualization Forum.

---

