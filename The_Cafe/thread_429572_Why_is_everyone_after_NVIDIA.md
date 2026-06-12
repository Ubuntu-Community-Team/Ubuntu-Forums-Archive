---
title: "Why is everyone after NVIDIA ?"
date: 2007-05-01
forum: The Cafe
---

### Post by rajeev1204 on 2007-05-01
Hi

i have been reading about this open source thing for long time here and i guess what people like they will choose - open or closed , free or non free .

But why try to create open source drivers for the beautifully supported nvidia cards ?

Those drivers are the reason i shifted to ubuntu .


Nvidia is a hardware company and they obviously are the best people to write drivers for it .Or thats what logic seems to say .

Maybe u should try it with ATI and their crappy drivers .

Nvidia provides excellent support with new drivers etc and iam sure all users are happy with the proprietary drivers .


Open sourcing something without any real need and just for morality ( or whatever u call it ) is what is bothering me so i created this thead


Please if advocates of open source could explain what is going on here i would be relieved .

Iam only referring to nvidia drivers here .



regards

rajeev

---

### Post by justin whitaker on 2007-05-01
There is a small, but vocal group, that think that any proprietary software should be demonized, and replaced with open source alternatives.

There are those who see open source as a political/religious movement, and as such, any proprietary software, particularly drivers that hook into the kernel, somehow mar the purity of their system. 

*shrug* I don't get it either. I spent $200+ on my Nvidia card, and I want it to work, no matter which OS I use.

---

### Post by ubuntu27 on 2007-05-01
Brief explanation: If you find any bungs in the proprietary driver, you will not be able to do anything, except wait for nVidia to release a new driver which could take years... just like Microsoft.
But if it were Open Source, we could help ourself.

---

### Post by TravisNewman on 2007-05-01
>  iam sure all users are happy with the proprietary drivers .
There are a lot of people who are unhappy with them actually. There are some significant bugs that haven't been worked out of the nvidia drivers. 

That said, I haven't seen any myself.

But I believe open source is always better than closed source. The development model just works better. If nvidia opened their source tomorrow, I almost guarantee that in a month most of the bugs that have been around for years would be taken care of.

---

### Post by Mateo on 2007-05-01
1) NVIDIA users have it to good if all they have to worry about is how long they have to wait for bug releases because it's not open source.  Us ATI users are deprived of basic features that are included with our card, but not with the driver.

2) Like someone else said, there are some zealots who think open source is a religion and it's their job to proselytize.  Like many real religions, if they encounter another "denomination", it's their responsibility to destroy it. ;)

---

### Post by justin whitaker on 2007-05-01
> **ubuntu27 said:**
> But if it were Open Source, we could help ourself.

You know, I question that. I don't want to drag this to the backyard, but just how many people have the knowledge to code video card drivers?

It cannot be that many people...my point is, for the bulk of users, they would be unable to fix the source even if they had it, and would still be dependent on some team with arcane knowledge to provide a fix. 

If there isn't one forthcoming, they will go back to Windows saying Linux sucks....in the end, would it not be better to support Nvidia and submit bugs to them?

---

### Post by hardyn on 2007-05-01
> **panickedthumb said:**
> There are a lot of people who are unhappy with them actually. There are some significant bugs that haven't been worked out of the nvidia drivers. 

That said, I haven't seen any myself.

But I believe open source is always better than closed source. The development model just works better. If nvidia opened their source tomorrow, I almost guarantee that in a month most of the bugs that have been around for years would be taken care of.


All my complaints come from the notebook implementation of the drivers.  thats not just nvidia, all of the drivers have little thought toward notebook use. most of the drivers do not suspend well, or offer GPU throttling.

On a desktop, you likely wouldn't notice any of the trouble.

---

### Post by John.Michael.Kane on 2007-05-01
> **Mateo said:**
> 1) NVIDIA users have it to good if all they have to worry about is how long they have to wait for bug releases because it's not open source.  Us ATI users are deprived of basic features that are included with our card, but not with the driver.

2) Like someone else said, there are some zealots who think open source is a religion and it's their job to proselytize.  Like many real religions, if they encounter another "denomination", it's their responsibility to destroy it. ;)

Please do not turn this thread into a ATI vs Nvidia debate. Both drivers have their shortcomings.

---

### Post by rsambuca on 2007-05-01
I am obviously not a purist, but I have always considered the driver issue to be more of a hardware related thing.  If nvidia makes a video card, then if they want linux users to buy it, then to me the onus is on them to make a driver that will work with the linux kernel.  If users aren't happy with that, then they can choose to not buy from that particular company.  There is an alternative - Intel has open sourced their drivers.

---

### Post by gnomeuser on 2007-05-01
1) Security, running megs of unvettable and unfixable code as root loaded into my kernel does appeal to me. They have already had one major security hole, who knows what else is going on.

2) Portability, people on any platforms outside of i386 and x86_64 are screwed, this means people with the older mac laptops e.g. Doesn't sound like a lot of people but you'd be surprised.. in this group we also count the people who want to run Linux on their PS3 since everything but the videocard runs perfectly under their supported Linux distro and there's not even a proprietary driver we can use.

3) Poor code, I know as a user you rarely see problems but try politely asking one of the kernel developers how that driver fares and you'll get stories of a whole new level of hurting. Silent oopses that look unrelated because of their strange use of stack e.g. I'd tried supporting this.. it defines unfunny.

4) Fixability, I can't fix the driver when it has broken functionality, and one just has to look at code like Beryl, they have odd switches to workaround problems in the drivers we can't fix because there's no source.

5) Long term support, nvidia retires cards from official support rather fast, this forces you to use an unsupported driver which is rarely updated, use the open 2d driver or buy a new card to continue to use your computer.. which is otherwise perfectly functional. With an open driver we could continue to let you have use out of the hardware you have and which hopefully works well for you.

And many more reasons, infact so many that I started the highly succesfully pledge drive for the nouveau driver. It's a hard job, it takes a lot of ground work before it's even remotely useable for general users but it's also a lot of fun - I think it's worth rewarding.

---

### Post by rajeev1204 on 2007-05-01
Hi

I dont think  this will turn into nvidia vs ati debate .I just read about the noveou? drivers and it bothers me .(scares me actually)

I just feel that by using good quality software or drivers we can help make more and more people choose ubuntu .

I tell this from my own user experience that i was relieved when my nvidia worked well for me. 


Also i do feel bad that people are having trouble with ATI and new users will get scared and may choose a different distro cos of the open source thing . Top priority is getting new users to ubuntu i feel .

This ubuntu thingy is so lovely i want more people to use it . :) 


If we all report more and more bugs to ATI/ NVIDIA i think they will pay heed ..Making drivers for their cards is their job right ?






regards

rajeev

---

### Post by kanem on 2007-05-01
The reason "us zealots" feel it's important for as much as possible to be open sourced is because we've been here a long time and know that in the long run, open source works better and lasts longer. Go see how good Nvidia's support is for some of their older cards.

If someone doesn't get it, maybe it's because they only care about now, and not the future. So "us zealots" often have to point out that if, ten years ago, Linux users were satisfied with closed source apps, Linux would not have many of the quality open source apps it does today. What web browser would you be using if no one had cared about open sourcing Netscape? It wouldn't be Firefox. And if no one cares about open source drivers today, we won't have any ten years from now.

[quote=justin whitaker]just how many people have the knowledge to code video card drivers?

It cannot be that many people...my point is, for the bulk of users, they would be unable to fix the source even if they had it, and would still be dependent on some team with arcane knowledge to provide a fix.[/quote]
Just because a person can't code doesn't mean they don't benefit from code being open source. I certainly don't have the knowledge to code video drivers, but the number of people who can is far larger than the number of Nvidia employees working on Linux drivers.

---

### Post by tseliot on 2007-05-01
> **gnomeuser said:**
> 5) Long term support, nvidia retires cards from official support rather fast, this forces you to use an unsupported driver which is rarely updated, use the open 2d driver or buy a new card to continue to use your computer.. which is otherwise perfectly functional. With an open driver we could continue to let you have use out of the hardware you have and which hopefully works well for you.
I think this is the main reason (from a common user's point of view).

What happens if Nvidia, ATI or whatever decide to drop the support for your card?

No one will ever be forced to use the open source driver. The proprietary driver will always be available (of course it depends on ATI and Nvidia).

---

### Post by EdThaSlayer on 2007-05-01
Nvidia drivers use more of the *juice* that is available in your graphics card. ATI drivers, on the other hand, give you 1/8 of the power you should be able to get.

---

### Post by macogw on 2007-05-01
Try using Beryl with nVidia's closed source drivers.  Sometimes your windows turn solid black for no good reason.  It's a bug in their drivers.  We need open ones so we can fix them.  Now, I can't code well enough (yet) to fix them, but there are certainly kernel devs who can.  As long as someone can look and fix them, that's a good thing.

ATI has some open 3D drivers.  NVidia doesn't have any.  NVidia's are all 2D if they're open.  ATI's open ones are 3D and better than their closed ones (though the newer cards don't have open drivers yet, all of the ones for which ATI dropped support are still available).

---

### Post by igknighted on 2007-05-01
> **EdThaSlayer said:**
> Nvidia drivers use more of the *juice* that is available in your graphics card. ATI drivers, on the other hand, give you 1/8 of the power you should be able to get.

??? I don't think this is true at all, my x800, which is in the same range as my geforce 6600gt, overpowers it significantly... While I see that nvidia drivers are better overall, the ATI ones do a nice job too.  Look at some differences: ATI drivers can install correctly from a nice GUI click through without killing X to do it from the CLI.  Also, if you update you kernel in a situation where the Nvidia drivers would crash X, the ATI drivers work fine for 2d and make you fix them only for 3d.  Much more user friendly there as well.  There are of course many flaws in ATI's drivers, and I think everyone knows them so I wont waste time listing them.

Also, ATI has great open source 3d drivers.  The community has done wonders with the ati/radeon drivers.  With my x800 it was all I used, and never had issues.  I think that having the option of a 3d capable nvidia driver for those who just want beryl to run ootb and don't game is a great idea, theres no reason they should suffer because Ubuntu will never include a binary driver like that in the distribution.  ATI users and Intel users can use beryl ootb, nvidia users should get the same courtesy (especially since everyone says nvidia is better, which they are right now... this could confuse many new users)

---

### Post by Syke on 2007-05-01
[QUOTE=justin whitaker]You know, I question that. I don't want to drag this to the backyard, but just how many people have the knowledge to code video card drivers?[/quote]

Hundreds, maybe thousands.

> It cannot be that many people...my point is, for the bulk of users, they would be unable to fix the source even if they had it, and would still be dependent on some team with arcane knowledge to provide a fix.

Open source works. Day in and day out. When the software is open source, that team of "arcane knowledge" is many times larger than when it is closed source.

I love Nvidia hardware. If their drivers were open source, I could love them too!

---

### Post by aysiu on 2007-05-01
If Nvidia suddenly decides to *stop* releasing their own Linux driver, the Linux Nvidia users are pretty much screwed... unless there's an open source alternative. Proprietary = lock-in.

---

### Post by rajeev1204 on 2007-05-01
> **aysiu said:**
> If Nvidia suddenly decides to *stop* releasing their own Linux driver, the Linux Nvidia users are pretty much screwed... unless there's an open source alternative. Proprietary = lock-in.


Quite a negative thought  he  :) 

Anyways  why that would happen i have no idea ,


Also in a previous post , someone said ATI open drivers are better  3D  than closed drivers .  

Well if thats true , i guess open source is the right way .


So does this mean people here are having trouble with ATI closed or open source drivers ??

Has this been fixed with feisty yet .? 



regards

rajeev

---

### Post by maniacmusician on 2007-05-01
ugh. How many times is this going to come up. A few points:

- Nvidia **doesn't mind the open source drivers**. In fact, they've expressed that they're perfectly fine with efforts to create open source drivers. If they could, nvidia may even  have released open source drivers themselves; but they dont hold the patents and copyrights to all the stuff in their drivers or cards, so they can't do that

- proprietary drivers can leave huge, exploitable bug that leave you at the mercy of the one providing the driver. While the nVidia drivers are pretty good, they've left some big vulnerabilities in the past, and probably will in the future. If the drivers were open source, it's almost a guarantee that a fix would be issued within a week of a critical bug being exposed.

So I dont see what's the problem. Open source drivers are good. Canonical think so, most users think so, even nVidia thinks so.

---

### Post by rajeev1204 on 2007-05-01
OK 

I get the picture .

But maniac musician i also want to add 

Nvidia thinks that their drivers are better than other open source ones ( they give that comparison in their website )

 . And iam familiar with the patent issue of nvidia .That means they will probably never be open sourced and so that means their proprietary driver will always be better IMHO.

---

### Post by Mateo on 2007-05-01
> **igknighted said:**
> 
Also, ATI has great open source 3d drivers.  The community has done wonders with the ati/radeon drivers.  With my x800 it was all I used, and never had issues.  I think that having the option of a 3d capable nvidia driver for those who just want beryl to run ootb and don't game is a great idea, theres no reason they should suffer because Ubuntu will never include a binary driver like that in the distribution.  ATI users and Intel users can use beryl ootb, nvidia users should get the same courtesy (especially since everyone says nvidia is better, which they are right now... this could confuse many new users)

Which driver?  The only ATI driver I've seen that's half-way decent is fglrx.  ATI doesn't even have 3d.  I'm never used Radeon but i've never heard a good thing said about it.

FGLRX is the best ATI driver and it's still not that good.  It doesn't even let you adjust tv-out overscan, a basic feature of the hardware.  NVIDIA users really don't know how good they have it.

---

### Post by maniacmusician on 2007-05-01
> **rajeev1204 said:**
> OK 

I get the picture .

But maniac musician i also want to add 

Nvidia thinks that their drivers are better than other open source ones ( they give that comparison in their website )

 . And iam familiar with the patent issue of nvidia .That means they will probably never be open sourced and so that means their proprietary driver will always be better IMHO.
possibly. and right now, their drivers **are** better than the open source ones...that's why noveau has been started. The open source nv drivers are awful right now...they don't provide direct acceleration at all.

Most users don't need incredible 3D accleration. they just want enough to be able to use Beryl and fool around with some games. If the open source drivers can provide that, it'll be a significant advantage

- Distros will be able to include 3D drivers out of the box and in the kernel
- Less vulnerabilities
- still get reasonable 3D acceleration

---

### Post by maniacmusician on 2007-05-01
> **Mateo said:**
> Which driver?  The only ATI driver I've seen that's half-way decent is fglrx.  ATI doesn't even have 3d.  I'm never used Radeon but i've never heard a good thing said about it.

FGLRX is the best ATI driver and it's still not that good.  It doesn't even let you adjust tv-out overscan, a basic feature of the hardware.  NVIDIA users really don't know how good they have it.
there is a driver called ati (it's also called radeon) that provides open source support for ATI cards. fglrx sucks; the open source ati driver actually provides 3D acceleration for more cards than fglrx.

---

### Post by Mateo on 2007-05-01
i have to say, I have no team in the whole "open source vs closed source" thing -- I consider computer use to be fun and not a religious experience -- but I don't see ANY advantage to open-source drivers.  Obviously there is no profit motivation for hobbyists to write drivers.  By the time a decent driver came out, the card would be ancient.

---

### Post by igknighted on 2007-05-01
> **Mateo said:**
> Which driver?  The only ATI driver I've seen that's half-way decent is fglrx.  ATI doesn't even have 3d.  I'm never used Radeon but i've never heard a good thing said about it.

FGLRX is the best ATI driver and it's still not that good.  It doesn't even let you adjust tv-out overscan, a basic feature of the hardware.  NVIDIA users really don't know how good they have it.

"ati" has 3d for all cards up to x850, but most work better with "radeon".  I ran beryl with the "radeon" driver on my x800GTO for a long time and never had issues.  There are lots of tweaks you can add to these drivers to improve performance, check out [help.ubuntu.com/community/RadeonDriver]("http://help.ubuntu.com/community/RadeonDriver").

---

### Post by Mateo on 2007-05-01
> **maniacmusician said:**
> there is a driver called ati (it's also called radeon) that provides open source support for ATI cards. fglrx sucks; the open source ati driver actually provides 3D acceleration for more cards than fglrx.

err.. not in my experience.  ATI even slows down WEB USE with things like flash **for me**.

---

### Post by Mateo on 2007-05-01
> **igknighted said:**
> "ati" has 3d for all cards up to x850, but most work better with "radeon".  I ran beryl with the "radeon" driver on my x800GTO for a long time and never had issues.  There are lots of tweaks you can add to these drivers to improve performance, check out [help.ubuntu.com/community/RadeonDriver]("http://help.ubuntu.com/community/RadeonDriver").

i don't have a problem with fglrx for 3D.  Does "radeon" even have tv-out support?

---

### Post by jamesstansell on 2007-05-01
> **Mateo said:**
> i have to say, I have no team in the whole "open source vs closed source" thing -- I consider computer use to be fun and not a religious experience -- but I don't see ANY advantage to open-source drivers.  Obviously there is no profit motivation for hobbyists to write drivers.  By the time a decent driver came out, the card would be ancient.
I've studied software now, both as a hobby and professionally for over 25 years.  I don't consider it a religous experience at all but I do strongly believe that open-source and free software has dramatic long-term benefits over proprietary software.

You expressed at least 2 erroneous assumptions.  Rather than restating them let me state the corrected version.

1) for software developers there are often far greater motivations than only profit.  The best software is often produced by people who have a sense of learning and accomplishment.  And free software provides a strong environment for this.

2) free software programmers are not only hobbyists.  Most driver maintainers, for example, are paid by companies like RedHat and Canonical.  LWN.net had an article about this earlier this year.

---

### Post by Adamant1988 on 2007-05-01
> **igknighted said:**
> **"ati" has 3d for all cards up to x850**, but most work better with "radeon".  I ran beryl with the "radeon" driver on my x800GTO for a long time and never had issues.  There are lots of tweaks you can add to these drivers to improve performance, check out [help.ubuntu.com/community/RadeonDriver]("http://help.ubuntu.com/community/RadeonDriver").

I beg to differ.  I have an ATi Radeon x600 card, and the 'ati' driver doesn't even approach giving me 3d acceleration for that.

---

### Post by jamespi on 2007-05-01
> **justin whitaker said:**
> You know, I question that. I don't want to drag this to the backyard, but just how many people have the knowledge to code video card drivers?



[these guys]("http://nouveau.freedesktop.org/wiki/"). everyday users don't fix their own bugs in open source software, that's a silly misconception. the everyday users report the problems to the devs, the devs proioritise them and sort them out. if one set of devs won't fix it, there may well be another group who have the know how to fix it.

So why not just report the bugs to Nvidia and let them fix it? Linux is such tiny percentage of nvidia's market that they dont care enough to prioritise bugs from linux users.

That having been said, their drivers are pretty good considering they arent a priority.

If nvidia released detailed specs or the source code to their drivers (which is tantamount to the same thing) then some group of devs could write totally open drivers for them, but then nvidia would be revealing all their trade secrets, and also it may be impossible for them to give those secrets away, as some of them may be licensed patents from other companies who dont want to give their secrets away.

there are reasons other than zealotry for wanting open source drivers. if nvidia went bust then their secrets would die with them. no more driver upgrades. also no one knows what the nvidia drivers do. there could be code in there that does things you dont want like DRM and there's nothing anyone can do to remove it.

that having been said, if you really want to be totally free of reliance on a single vendor to support your computer for the rest of it's days, there is [ this project which is rather exciting(if you're a nerd)]("http://hardware.newsforge.com/article.pl?sid=06/06/16/2110211&tid=87")

---

### Post by prizrak on 2007-05-01
This has been rehashed many times and the drivers aren't that great (at the very least not as good as Windows).
1) Black Windows on Compiz/Beryl - on a mobile card with TurboCache the driver has issues managing memory so the card runs out of RAM to hold the window that results in a window that is completely black. At this point I KNOW how many stand alone windows I can open so in effect I'm managing the memory. 

2) Power management - Windows driver provides GPU throttling, which is at least a 10 minute difference in power consumption. 

3) Suspend/Hibernate - basically forget about it, if you have the binary driver it won't work.

4) Updatability (is that a word?) - everyone time you change the kernel/xorg the driver has to be recompiled against them. This is a big pain for maintenairs because things can break quite easily and that in turn annoys us users. 

5) Out of the box - most distro's will not include binary drivers out of the box, they all have their own reason but to us users it translates into not having things like Beryl work out of the box. It might not be a huge deal but it would make life much easier. It could also enable Gnome/KDE to include certain compositing features without using a 3rd party application such as Compiz/Beryl. (Even if you don't want effects, expose, pane and alt-tab are quite good for productivity).

---

### Post by bastiegast on 2007-05-01
Had to respond to this thread as it drives me crazy people get mad over this issue. But since so many people already gave great reasons to have open source drivers I have nothing to add.

Nvidia doesn't mind, and we can support open source drivers better, they may provide more stability and less security issues. 

I hope people will for once and for all understand this and stop complaining about nothing.

---

### Post by klerfayt on 2007-05-01
> **rajeev1204 said:**
> Nvidia provides excellent support with new drivers etc and iam sure all users are happy with the proprietary drivers .I probably shouldn't whine here, but, [once you hit a bug you find critical and it won't  be fixed]("http://www.nvnews.net/vbulletin/showthread.php?t=84562") (9months now?) - you will approach differently the closed/open drivers situation

---

