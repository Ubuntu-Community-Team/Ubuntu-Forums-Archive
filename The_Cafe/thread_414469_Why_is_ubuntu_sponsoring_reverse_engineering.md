---
title: "Why is ubuntu sponsoring reverse engineering?"
date: 2007-04-11
forum: The Cafe
---

### Post by neighborlee on 2007-04-11
> **cowlip said:**
> Nouveau have a new renouveau script out, it automatically packs up the results.

I installed the official Nvidia drivers on the Dapper Drake live cd using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") envy_0.8.2-0ubuntu1_all.deb.  Then I installed renouveau (it needed this: sudo apt-get install build-essential cvs mesa-common-dev libsdl1.2-dev libxvmc-dev nvidia-glx-dev )


I have a Riva TNT2 that came with my computer but I can't find it now--maybe some posters reading this post can help in that case.  It seems like they really need TNT2, NV1, 2  cards, among some others, for dumps- but I just did my Geforce Ti 4200.

I used it on a multi-monitor system with Twinview however--does anyone think that affected the results negatively?  And what's this about[ needing kernel, SLI, and Mmio traces (from the Nouveau Companion #16)]("http://nouveau.freedesktop.org/wiki/Nouveau_Companion_16")?  Is it easy to help out with?

why is ubuntu sponsoring RE'ing..I find it very distasteful..what vendor is next and is this going to cause linux to have black eye and get worse vendor support in future..is nouveau getting info that willl cause nvidia to lose its secrets if not could someone please provide proof of this..

I dont expect any flames on this because Im Asking in absense of undestanding the underlying principles involved here....but really aren't there other proprietary drivers being used by ubuntu, if so why aren't they being RE'd ? ;)

thx
nl

---

### Post by neighborlee on 2007-04-17
> **neighborlee said:**
> why is ubuntu sponsoring RE'ing..I find it very distasteful..what vendor is next and is this going to cause linux to have black eye and get worse vendor support in future..is nouveau getting info that willl cause nvidia to lose its secrets if not could someone please provide proof of this..

I dont expect any flames on this because Im Asking in absense of undestanding the underlying principles involved here....but really aren't there other proprietary drivers being used by ubuntu, if so why aren't they being RE'd ? ;)

thx
nl

BUMP, this is very important to me and it would be nice for someone that knows to comment..

cheers
nl

---

### Post by rai4shu2 on 2007-04-17
What part of this do you find distasteful?

> This is used to do clean room reverse engineering (this is not in violation with nvidia driver license). We do not disassemble binaries.

---

### Post by neighborlee on 2007-04-19
> **rai4shu2 said:**
> What part of this do you find distasteful?

 I find it distasteful , because I see no reason to do it in the first place. Isn't this also going to divulge info about their drivers that will make it difficult for them to compete fairly with  ati or other manufacturers ? Why do we need to do this, when all we'd have to do is ask nvidia  maybe for a NDA or something.even so we have decent drivers from them  already, so frankly what is this need ? Does windows have some special agreement with them that we dont making their drivers available to windows developers ?

If  not I"d love to know as I certainly have no idea regarding such high end drivers as these.

cheers
nl

---

### Post by jiminycricket on 2007-04-19
The only open source drivers nVidia has is the 2d 'nv' drivers.  And these were obfuscated in 1999, so much so that nouveau bases off of a BeOS/Haiku reverse engineered driver. 

NDA drivers are unmaintainable, much like the nv drivers, where only nVidia can maintain the driver.

Why reverse engineer?
By using proprietary drivers, you can introduce unfixable root exploits (as the nVidia binary driver had, also madwifi), unsupportable kernels (don't expect bugs to be fixed by kernel.org developers), crappy drivers (compiz and beryl have unexplained glitches with nVidia's drivers, whereas Intel's and open source ATI's don't), unportable drivers, and eventually drivers that will not work when the kernel updates as they drop support.  Then the whole copyright infringment thing because the kernel is GPL'd, not LGPL'd.  That means distros can't include it out of the box for things like Beryl because then they would be distributing, under the GPL.

Maybe [nouveau]("http://nouveau.freedesktop.org/wiki/FAQ#head-f3ca7e2184d1bde940c8537735074ffc6476b5bf")  can answer better for [themselves]("http://www.skynet.ie/~airlied/talks/lca07/nouveau.odp") (ODP file):
> 1.9. Why are you doing this?

We can't give you the answer, as each of the project members has his own motivation. Just a few answers from our staff, we got when this question was raised: 
Don't like binary blobs 
Want to give back to the OSS community 
Want to learn driver programming 
Yes, we can develop our own drivers regardless of what people at NVidia may think 
Support for missing features 
Support for operating systems not supported by NVidia (any PowerPC based OS for example) 
Just for the fun of it 
Binary driver keeps crashing even in 2D 
Slow Xorg "nv" driver (slow in performance and slow to get new card support (Nvidia 8800 is currently not supported)) 

So pick the reasons you feel are important, chances are that quite a few project members will agree with you pick 

Anyways I'm not sure if maybe this specific discussion should be in another thread so people can focus on doing renouveau and their other tests..

---

### Post by The Noble on 2007-04-19
I think you are not exactly thinking of this correctly. There are no problems with using RE (for both them and us). It discloses no information that would hurt nVidia in ANY way, we are just seeing how the nvidia driver is doing certain operations and they copy it. No harm, no foul. I have no time right now to explain this in detail, so maybe someone will explain it in full.

---

### Post by justin whitaker on 2007-04-19
I don't get the outrage here. Maybe I'm missing something. Could someone explain to me why reverse engineering is so heinous?

---

### Post by the_darkside_986 on 2007-04-19
Yeah reverse engineering is perfectly legal if it is for the purpose of compatibility. I can't wait until they make more progress on the nvidia drivers so I can play Sauerbraten with pure open source drivers instead of the ugly proprietary thing that blows up X server all the time.  But I still have a wireless card, and we know how those are :(

I hope someday all the drivers for my hardware will be liberated. Who knows what kind of nasty things a vendor can put into their drivers if no one can see their code...

---

### Post by FuturePilot on 2007-04-19
The only way to get drivers from vendors that don't provide Linux drivers is to RE. I don't see anything wrong with this. Unless you would rather have no drivers at all? 

I look forward to the day when we have open source Nvidia drivers

---

### Post by AusIV4 on 2007-04-19
The current options for nvidia aren't very good. You can either choose the nv drivers, which are open source but obfuscated and difficult to maintain, or the binary drivers, which not only have licensing issues, but it's necessary to rely on nvidia for maintenance - this can result in bugs that don't get fixed, and incompatibilities with new versions of the kernel that only nvidia can resolve.

I believe the primary reason nvidia has not released open source drivers is that they are under contractual obligation due to code and firmware that they have licensed from other parties. As far as exposing trade secrets, there's nothing a clean room reverse engineer could expose that a company like ATI couldn't uncover by doing their own RE's.

I do have a few problems with reverse engineering device drivers, but it's not because it puts companies at unfair disadvantages. I spend my money with vendors who provide either provide open source drivers, or specifications for the creation of open source drivers. I have an Intel GMA graphics card and Intel wireless for that very reason. The open source community can spend a great deal of time and money making open source drivers for nvidia cards, and it seems to me that nvidia will profit from that. I think the open source community would be better off encouraging the use of devices with helpful manufacturers than creating drivers that boost the sales of manufacturers who don't do much for the open source community.

---

### Post by neighborlee on 2007-04-19
> **the_darkside_986 said:**
> Yeah reverse engineering is perfectly legal if it is for the purpose of compatibility. I can't wait until they make more progress on the nvidia drivers so I can play Sauerbraten with pure open source drivers instead of the ugly proprietary thing that blows up X server all the time.  But I still have a wireless card, and we know how those are :(

I hope someday all the drivers for my hardware will be liberated. Who knows what kind of nasty things a vendor can put into their drivers if no one can see their code...

well thats just it..I never have any problems with my  drivers , not in windows nor linux so I Dont know what you all are talking about...

mine work perfectly fine, so this 'it must be RE'd I find unjustified....

cheers
nl

---

### Post by neighborlee on 2007-04-19
> **jiminycricket said:**
> The only open source drivers nVidia has is the 2d 'nv' drivers.  And these were obfuscated in 1999, so much so that nouveau bases off of a BeOS/Haiku reverse engineered driver. 

NDA drivers are unmaintainable, much like the nv drivers, where only nVidia can maintain the driver.

Why reverse engineer?
By using proprietary drivers, you can introduce unfixable root exploits (as the nVidia binary driver had, also madwifi), unsupportable kernels (don't expect bugs to be fixed by kernel.org developers), crappy drivers (compiz and beryl have unexplained glitches with nVidia's drivers, whereas Intel's and open source ATI's don't), unportable drivers, and eventually drivers that will not work when the kernel updates as they drop support.  Then the whole copyright infringment thing because the kernel is GPL'd, not LGPL'd.  That means distros can't include it out of the box for things like Beryl because then they would be distributing, under the GPL.

Maybe [nouveau]("http://nouveau.freedesktop.org/wiki/FAQ#head-f3ca7e2184d1bde940c8537735074ffc6476b5bf")  can answer better for [themselves]("http://www.skynet.ie/~airlied/talks/lca07/nouveau.odp") (ODP file):


Anyways I'm not sure if maybe this specific discussion should be in another thread so people can focus on doing renouveau and their other tests..

this whole kernel thing is a sham and you know it quite well..the nvidia driver does nothing illegal, as proven by daniel here;

[http://www.funtoo.org/drobbins/blog/2007/02/push-to-remove-non-free-graphics.html](http://www.funtoo.org/drobbins/blog/2007/02/push-to-remove-non-free-graphics.html)

> By using proprietary drivers, you can introduce unfixable root exploits (as the nVidia binary driver had, also madwifi),

what is this ^ referring to btw ?

>  unsupportable kernels (don't expect bugs to be fixed by kernel.org developers), maybe if the kernel wasn't released every few months things could be a tad more stable ;) ( I recall that as a legitimate complaint by a certain mandriva employee, and it does make me wonder how windows pullls this whole thing off so well  )

> crappy drivers (compiz and beryl have unexplained glitches with nVidia's drivers, whereas Intel's and open source ATI's don't), again while I"ve never used it much in linux due to instability I admit, its neve caused much problems in windows when I tried it and that was a vista beta driver to boot..so again how exactly is windows pulling this off if indeed these drivers not being OS are so bad ?

I'm not disagreeing that software shouldnt be open source as yes that is very desireable for many  reasons, this just seems like the wrong way to go about getting there to me.

What do you mean unportable drivers ?

> That means distros can't include it out of the box for things like Beryl because then they would be distributing, under the GPL., no offense, but again refer to daniel's explantion , for why that is simply zealotry in action, and based on zero fact ;)

THings like this really make our community look pretty darn silly , and arrogant for not considering doing better homework ;)

cheers
nl

---

### Post by neighborlee on 2007-04-20
> **AusIV4 said:**
> The current options for nvidia aren't very good. You can either choose the nv drivers, which are open source but obfuscated and difficult to maintain, or the binary drivers, which not only have licensing issues, but it's necessary to rely on nvidia for maintenance - this can result in bugs that don't get fixed, and incompatibilities with new versions of the kernel that only nvidia can resolve.

I believe the primary reason nvidia has not released open source drivers is that they are under contractual obligation due to code and firmware that they have licensed from other parties. As far as exposing trade secrets, there's nothing a clean room reverse engineer could expose that a company like ATI couldn't uncover by doing their own RE's.

I do have a few problems with reverse engineering device drivers, but it's not because it puts companies at unfair disadvantages. I spend my money with vendors who provide either provide open source drivers, or specifications for the creation of open source drivers. I have an Intel GMA graphics card and Intel wireless for that very reason. The open source community can spend a great deal of time and money making open source drivers for nvidia cards, and it seems to me that nvidia will profit from that. I think the open source community would be better off encouraging the use of devices with helpful manufacturers than creating drivers that boost the sales of manufacturers who don't do much for the open source community.

who dont do much you gotta be kidding  ;)..how about providing stable drivers ( i've never had trouble with opengl apps i n linux , neither with gaming or other 3d apps ,but maybe ive been lucky ) for an opeating system no where near what could be considered a leader in t he market place for obvious reasons..I use linux frankly as its safer and free, not because I think its smart about utilizing the communities best efforts ; but thats a entirely different discussion, that frankly most zealots just dont get.

cheers
nl

---

### Post by Zuuswa on 2007-04-20
> **neighborlee said:**
> 
, maybe if the kernel wasn't released every few months things could be a tad more stable ;) ( I recall that as a legitimate complaint by a certain mandriva employee, and it does make me wonder how windows pullls this whole thing off so well  )

I havnt the energy to reply in earnest, but heres one point.

Kernel releases are designed to fix bugs, improve stability, patch security holes, and improve functionality.

Microsoft does this every 5 years or so.  Meaning if the kernel doesnt work with your setup, tough beans.  Buy a differant M$ operating system.

Linux kernels are released rather frequently, and are quite significant.  So, if one kernel doesnt work, not only can you wait a few weeks/months for a new one and try that, or use an older one, and you can still retain functionality with the computer.

If you dont like kernel upgrades, then dont upgrade.  I personally don't find anything wrong with them, and everytime a new one is released, I pray it adds more functionality (like maybe my 5-in-1 card reader will work)

And calling us zealots??  You seem to be transforming into a troll.

---

### Post by Polygon on 2007-04-20
its perfectly legal (if done correctly) and its not like they are doing anything bad. They are trying to create open source nvidia drivers that work.... on all linux variants. Because the nvidia drivers are not open source, we are literally on our knees begging nvidia to make it better, to port it to new architectures, to fix bugs, to not introduce any security exploits that might compromise our system

but the thing is, nvidia doesnt. the drivers are still closed source

maybe instead of fighting against a good cause to open source basically the one thing that is holding back a lot of linux users from going 100% open source, the gpu drivers, pressure nvidia to open source their drivers. that way we dont have to resort to reverse engineering to create stable, bug free drivers that are open source and wont screw over our computer.  Intel did it, why cant nvidia?

---

### Post by wmcbrine on 2007-04-20
Linux is pretty much built on reverse engineering. Not just drivers -- all of it. Of course, nowadays, there's more original development; but in the beginning, it was built off of reverse-engineering Unix. And there's nothing whatsoever wrong with that.

---

### Post by The Noble on 2007-04-20
Ah, I see what you are getting at neighborlee, and I do understand. I am guessing you are going at the "if it ain't broke, then don't fix it approach", which is usually valid, but not here. Nvidia has pretty good linux drivers, and I have been fairly happy with them, but there have been problems. You may not have them, but they are there. One big one is when AIGLX needed the render_from_pixmap call, but neither ati nor Nvidia had it at the time. We had to use a little hack to bypass this, but that was counter-productive and never would have happened in the first place if the driver was open source. ATI *Still* can't use aiglx with the fglrx drivers, but can with the open source radeon ones. In general, the open source nature of the drivers helps the overall cleanliness of the drivers and helps increase quality. Bugs could be fixed faster as well, so that would be a plus; if you want a reference point on that just look at the Nvidia 420/440 Go fiasco that appeared (hit me too). 

My favorite part will be that the size of the drivers will be much smaller (in theory...), so it will be easier to add to the CD.

---

### Post by darweth on 2007-04-20
I am not sure what you are talking about man.  Are you just a troll?  This is a pretty sad thread.

1) Reverse engineering is LEGAL.
2) Reverse engineering is OMNIPRESENT in the Linux world.  It has always gone on and will always go on.  How do you think we get things to work when the specs and drivers are not given to us?  This goes way beyond Nvidia!  If you are opposed to RE'ing, you would do best to not use Linux period.  lol.
3) Microsoft donated a Zune to the libmtp team for the EXPRESS PURPOSE of reverse engineering.  I think that is silly.  They could probably do more and provide some specs, but whatever.  Reverse engineering is 100% standard practice.

Whether or not we NEED open source nvidia drivers can be debated.  It is obvious you have made your position clear and are not a FOSS zombie, but that doesn't mean these types of endeavors should not continue.  There are many reasons people want 100% FREE and functional drivers.  

To call Ubuntu and the Linux world silly for going about a pretty standard and fundamental practice?  You need a clue, bro. ;)  Stop trolling.

---

### Post by The Noble on 2007-04-20
Guys, it sounds like he is a little confused, and maybe he is going about it in a misguided way, but that does not mean we need to start calling him a troll. Sort him out if you have the time; ignore if you don't. This is all a big misunderstanding in my mind, so would you mind restating what exactly you were wondering neighborlee?

---

### Post by rai4shu2 on 2007-04-20
> **neighborlee said:**
> who dont do much you gotta be kidding  ;)..how about providing stable drivers ( i've never had trouble with opengl apps i n linux , neither with gaming or other 3d apps ,but maybe ive been lucky ) for an opeating system no where near what could be considered a leader in t he market place for obvious reasons..I use linux frankly as its safer and free, not because I think its smart about utilizing the communities best efforts ; but thats a entirely different discussion, that frankly most zealots just dont get.

cheers
nl

Sorry, but this is flame baiting. Pure and simple.

---

### Post by hardyn on 2007-04-20
Try a notebook with either the fglrx or the nvidia drivers... the short comings become apparently pretty quickly.

i am really curious to see how neuvous works out!
the open graphics project is quite interesting, but looks like it is geared at for the professional, not the desktop at this time.

I guess we just have to find a way to let the hardware manufacturers know that there might be a future in the development of linux drivers.

cheers.

---

### Post by Jussi Kukkonen on 2007-04-20
> **neighborlee said:**
> well thats just it..I never have any problems with my  drivers , not in windows nor linux so I Dont know what you all are talking about...

mine work perfectly fine, so this 'it must be RE'd I find unjustified....
Neighborlee, how on earth do you think all of those drivers you are currently running became to exist? A few may be binary blobs, few may be written by the manufacturers. *Many, possibly most are reverse engineered.* If you don't like running drivers that are "unauthorized" by the manufacturer, I suggest you turn you computer off now :)

---

### Post by use a name on 2007-04-20
> **neighborlee said:**
> 
, maybe if the kernel wasn't released every few months things could be a tad more stable ;) ( I recall that as a legitimate complaint by a certain mandriva employee, and it does make me wonder how windows pullls this whole thing off so well  )

, again while I"ve never used it much in linux due to instability I admit, its neve caused much problems in windows when I tried it and that was a vista beta driver to boot..so again how exactly is windows pulling this off if indeed these drivers not being OS are so bad ?


You're missing a basic point here: nVidia and others give full support for Windows, because they would otherwise not sell a single piece of hardware. It's not MS building the drivers... And it happens that a Windows update breaks something too, but then there's always the hardware manufacturer trying to fix things, if the product is still for sale...

As to root exploits: with binary only drivers, there may be an exploit, just as there can be with open source drivers. But with open source drivers, it can be fixed as soon as it is discovered. With closed source, you are dependent on the manufacturer...

---

### Post by Rhapsody on 2007-04-20
> **neighborlee said:**
> this whole kernel thing is a sham and you know it quite well..the nvidia driver does nothing illegal, as proven by daniel here;

[http://www.funtoo.org/drobbins/blog/2007/02/push-to-remove-non-free-graphics.html](http://www.funtoo.org/drobbins/blog/2007/02/push-to-remove-non-free-graphics.html)

Again, I must correct someone.

The key to the [GNU General Public License](http://en.wikipedia.org/wiki/GNU_General_Public_License) is that it's a strong copyleft license. This means not only that any derivative works must stay under the GPL, but that any code that links with GPLed code must also be under a free software license (hence the characterization of the GPL as 'viral' and Steve Ballmer calling Linux a 'cancer', but please read [an article](http://pointlessness.freehostia.com/2006/december/gpl-misconceptions.php) I made on the subject before jumping to any more conclusions).

If the Linux kernel were under the LGPL, then the 'derivative work' argument would have force, since LGPLed code can link with proprietary code. But the Linux kernel is under the GPL, which forbids such things, which is exactly what's happening with the binary blobs. They're definitely illegal, but this is ignored as the functionality the binary blobs provide is essential to what many people use Linux for. The people behind nouveau obviously thought that they could use clean room reverse engineering (a legal and well-known practice) to make free/open source drivers of identical or similar functionality, and I hope they succeed in this.

---

### Post by mips on 2007-04-20
> **neighborlee said:**
> 
I dont expect any flames on this because Im Asking in absense of undestanding the underlying principles involved here....but really aren't there other proprietary drivers being used by ubuntu, if so why aren't they being RE'd ? ;)


Don't you think forming an opinion/distaste of something before you understand it is a bit, uhmm, cannot think of a word thats appropriate here.

Nothing wrong with RE if done in a clean room environment & I support them 100%.

Another great thing is that the results of this project won't even be under the GPL but the MIT license allowing more people to benefit from it.

---

### Post by prizrak on 2007-04-20
nVidia does quite a bit of RE on AMD cards, AMD does the same to nVidia. AMD and Intel RE each other's CPU's. RE is a legal and very useful process, pretty much all companies do it and there is nothing distasteful about it. No RE driver will be able to match the official one or give out any kind of information to the competitor that they couldn't obtain themselves. 

AMD cards have RE drivers in Ubuntu and many other distro's. In fact most people use the RE driver for them, you don't seem to find it distasteful.

---

### Post by dca on 2007-04-20
I dunno', it just sounds like a misunderstanding to me.  I think it may be from taking the words 'reverse engineering' literally or somehow getting confused and applying 'RE' to stealing?

---

### Post by eentonig on 2007-04-20
I actually have a problem with the titel this topic has.

How do you come to the conclusion that Ubuntu sponsors RE? As far as I can see, nouveau is a seperate project.

And this has nothing to do with the legality or morality of RE. But just with whom your pointing fingers to. This seems to me as if you're already biassed against Ubuntu (Linux?)

---

### Post by mips on 2007-04-20
> **eentonig said:**
> I actually have a problem with the titel this topic has.

How do you come to the conclusion that Ubuntu sponsors RE? As far as I can see, nouveau is a seperate project.


As far as I recall from a little while back Ubuntu is sponsoring this project, sabfl own words. I will try and find a link to it.

Edit: Here are the sources;
[http://www.markshuttleworth.com/archives/95](http://www.markshuttleworth.com/archives/95)
[http://www.digg.com/linux_unix/Ubuntu_to_actively_support_Nouveau_an_open_source_NVIDIA_graphic_driver](http://www.digg.com/linux_unix/Ubuntu_to_actively_support_Nouveau_an_open_source_NVIDIA_graphic_driver)
[http://news.com.com/8301-10784_3-6159340-7.html](http://news.com.com/8301-10784_3-6159340-7.html)

---

### Post by Spr0k3t on 2007-04-20
I'm just trying to figure out what's wrong with reverse engineering in the first place.  I see I'm not the only one scratching their head on this one. Who else is completely agreeing with neighborlee?  I mean, don't get me wrong, it just makes no sense.

---

### Post by JNowka on 2007-04-20
I am guessing that he is mixing up RE for disassembling.  There is a major difference between the two.  To Disassemble a program means to be able to make a binary or compiled file into code.  This is illegal.  On the other hand when you try to RE a program all you see is the general steps that a program make to get to its destination.  You then are able to have an educated guess at what code needs to be there and hope that it works.  This is legal.  I hope this helps

---

### Post by neighborlee on 2007-04-20
> **The Noble said:**
> Guys, it sounds like he is a little confused, and maybe he is going about it in a misguided way, but that does not mean we need to start calling him a troll. Sort him out if you have the time; ignore if you don't. This is all a big misunderstanding in my mind, so would you mind restating what exactly you were wondering neighborlee?

well..sure unix was R E'd as you say...but was it a paid, suppported OS at the time this was done, honeslty I dont recall..

If intel has opened its drivers entirely I guess sure thats kewl on many fronts and I surely applaud this and wish everyone did this...that to me IS the way things should be, but I feel badly for nvidia if we are trying to coerce them into this by RE'ing their drivers..why not just politely ask them in discussions centering around working together ?

I really dont understand this big deal..my 3d drivers have always worked very well since using ubuntu..the only time I had issues was when I had bad ram and when I fixed that all issues were gone basically..so I dont get this we NEED  OS drivers or else mentality at all...who is being harmed and why, for not having completely OS drivers from nvidia ?

and btw, ive been using linux/ubuntu since  it first started, so trust me when I say im not a flamer or a troll. I call things how they are and sorry if you can't take that kind of heat/reality ;)

BTW, on this issue of kernel and GPL, I am not the only one that feels this way, as I posted in a earlier post, the founder of Gentoo has this exact same outlook so dont go calling me a troll unless you want to include him in that effort as well ;)

cheers
nl

---

### Post by neighborlee on 2007-04-20
> **JNowka said:**
> I am guessing that he is mixing up RE for disassembling.  There is a major difference between the two.  To Disassemble a program means to be able to make a binary or compiled file into code.  This is illegal.  On the other hand when you try to RE a program all you see is the general steps that a program make to get to its destination.  You then are able to have an educated guess at what code needs to be there and hope that it works.  This is legal.  I hope this helps

thx for trying to make this more clear..I still think the whole kernel/gpl issue is a poignant issue, but I also have to wonder if what your saying isn't a bit of a grey area ? ..I stilll wish we could work with nvidia to slowly get this done instead of going in the backdoor and wasting alot of developer time when it could be spent most likely on better more productive things..to me its about ethics as much as anything I guesss :))

thx
nl

---

### Post by neighborlee on 2007-04-20
> **prizrak said:**
> nVidia does quite a bit of RE on AMD cards, AMD does the same to nVidia. AMD and Intel RE each other's CPU's. RE is a legal and very useful process, pretty much all companies do it and there is nothing distasteful about it. No RE driver will be able to match the official one or give out any kind of information to the competitor that they couldn't obtain themselves. 

AMD cards have RE drivers in Ubuntu and many other distro's. In fact most people use the RE driver for them, you don't seem to find it distasteful.

if its not possible to make a quality RE driver, then why are they bothering to do it...why  not engage nvidia in talks and try to make headway on that front ?

I fail to see logic here at all ..but ok if your right about this nvidia/amd thing then ok..on that point I had no idea...I was only coming at this from a moral stanadpoint, since my drivers have always seemed stable to me it seemed odd to be doing this at all..

cheers
nl

---

### Post by phrostbyte on 2007-04-20
Me != everybody.

---

### Post by bonzodog on 2007-04-20
> **neighborlee said:**
> if its not possible to make a quality RE driver, then why are they bothering to do it...why  not engage nvidia in talks and try to make headway on that front ?
nl

We have already tried that and failed. Nvidia will not Open source their drivers in the foreseeable future due to firmware patent problems. They are hiding code that they don't own, only license from other people in their drivers. If they were to Open Source the drivers, they could be sued for millions of dollars for opening proprietary code that does not belong to them. Also, they could be using methods and calls inside the drivers that might contravene other firms patents.

A lot of this kind of thing has gone on for years,and as long as the code is never published openly, then firms they kind of borrowed it off don't actually have a problem. The whole thing is tied up in a legal quagmire of software patenting and industrial espionage on rivals, borrowing designs and codes off others.

---

### Post by macogw on 2007-04-20
Since when is reverse engineering a BAD thing?  Even the DMCA (die!DIE!!!!) allows it if it's to provide interoperability (and I'm pretty sure this qualifies).  

Since it's "clean room" (something only required in the US, thanks to the DMCA,  mind you), that means that the people who write the new drivers never actually see the originals.  One team disassembles and analyzes the code and uses it to figure out how things work and provide specs to the a completely separate team who then implements a driver for the specifications the first team gave them.  This avoids any copyright violations by 1) making it not able to be copied on purpose 2) not possible for the driver writer to think "oh, I can implement that like this..." and not realize he's thinking of the original algorithm used.  If there is any similarity, it's in the same category as convergent evolution.

---

### Post by igknighted on 2007-04-20
@ the OP... you are missing the whole point.  Linux is based on principles first and foremost... free, open-source software.  We will do whatever it takes to not use ANY binary blobs in our OS.  If that comes at the expense of alienating a few would be users, that is a necessary loss.  We are not selling something, we are designing an idea, and that idea is free software for everyone.

---

### Post by macogw on 2007-04-20
> **JNowka said:**
> I am guessing that he is mixing up RE for disassembling.  There is a major difference between the two.  To Disassemble a program means to be able to make a binary or compiled file into code.  This is illegal.  On the other hand when you try to RE a program all you see is the general steps that a program make to get to its destination.  You then are able to have an educated guess at what code needs to be there and hope that it works.  This is legal.  I hope this helps

Well, disassembling is generally the first step in RE-ing, unless you intend to use a debugger and very slowly watch one step at a time.

---

### Post by justin whitaker on 2007-04-20
> **igknighted said:**
> @ the OP... you are missing the whole point.  Linux is based on principles first and foremost... free, open-source software.  We will do whatever it takes to not use ANY binary blobs in our OS.  If that comes at the expense of alienating a few would be users, that is a necessary loss.  We are not selling something, we are designing an idea, and that idea is free software for everyone.

I remember seeing Torvalds giving and interview for the BBC. The Linux kernel came from wanting to do work on Unix, but as a student, he was not able to afford a license. So he copied it as much as possible, and released it  for everyone to use because he wanted everyone to share. It wasn't freedom, then, that started Linux, but poverty and fairness. 

All the freedom and the collective commons stuff comes out of RMS and other Linux prophets after the fact. Over the years, Torvalds has repeatedly said that there is no ideology to Linux as he sees it, just a sense of fairness: if I build something, you can use it, and if you change it, you let me know. 

I fail to see how "blobs" get into that. Torvalds has always said that proprietary code can run on Linux without abridging anyone's "rights"....That seems like blackmail somehow: give us your proprietary code for free, or else! How is that fair or ethical?

---

### Post by macogw on 2007-04-20
> **justin whitaker said:**
> I remember seeing Torvalds giving and interview for the BBC. The Linux kernel came from wanting to do work on Unix, but as a student, he was not able to afford a license. So he copied it as much as possible, and released it  for everyone to use because he wanted everyone to share. It wasn't freedom, then, that started Linux, but poverty and fairness. 

All the freedom and the collective commons stuff comes out of RMS and other Linux prophets after the fact. Over the years, Torvalds has repeatedly said that there is no ideology to Linux as he sees it, just a sense of fairness: if I build something, you can use it, and if you change it, you let me know. 

I fail to see how "blobs" get into that. Torvalds has always said that proprietary code can run on Linux without abridging anyone's "rights"....That seems like blackmail somehow: give us your proprietary code for free, or else! How is that fair or ethical?

Uh, RMS is was before-the-fact.  GNU/FSF started in '82 I think.  The kernel was in '91 and originally licensed so that nobody else could use it, then he relicensed it with the GPL.

---

### Post by prizrak on 2007-04-20
> **neighborlee said:**
> if its not possible to make a quality RE driver, then why are they bothering to do it...why  not engage nvidia in talks and try to make headway on that front ?

I fail to see logic here at all ..but ok if your right about this nvidia/amd thing then ok..on that point I had no idea...I was only coming at this from a moral stanadpoint, since my drivers have always seemed stable to me it seemed odd to be doing this at all..

cheers
nl

It is not impossible to write quality drivers, the FOSS Radeon driver had better 2D performance than the proprietary one for years, it's not possible to gain enough understanding of the hardware to gain an edge. nVidia and AMD video cards are extremely complex devices with their own ASM code. The drivers are equally complex and have alot of very creative and near impossible to duplicate programming. The Nouveau project is aiming to create an operable basic 3D driver. That means that it likely won't have anti aliasing, anisotropic filtering and so on. It will however be able to give you the much loved wobbly windows. 

Another problem with proprietary drivers is the inability to fix them. nVidia driver on their mobile GPU's with TurboCache (steals system RAM as needed) have an issue with Beryl/Compiz when using nVidia's buil-in compositing. The issue is that basically memory isn't getting released and acquired correctly and you end up with black windows (well decorations are visible but nothing else). This issue has been around for two driver versions and is not going away. If the driver was FLOSS'ed someone could have created a patch. Hell any one of us could pay a programmer to do it. No such luck with nVidia have to wait until they do it.

---

### Post by macogw on 2007-04-21
> **prizrak said:**
> It is not impossible to write quality drivers, the FOSS Radeon driver had better 2D performance than the proprietary one for years, it's not possible to gain enough understanding of the hardware to gain an edge. nVidia and AMD video cards are extremely complex devices with their own ASM code. The drivers are equally complex and have alot of very creative and near impossible to duplicate programming. The Nouveau project is aiming to create an operable basic 3D driver. That means that it likely won't have anti aliasing, anisotropic filtering and so on. It will however be able to give you the much loved wobbly windows. 

Another problem with proprietary drivers is the inability to fix them. nVidia driver on their mobile GPU's with TurboCache (steals system RAM as needed) have an issue with Beryl/Compiz when using nVidia's buil-in compositing. The issue is that basically memory isn't getting released and acquired correctly and you end up with black windows (well decorations are visible but nothing else). This issue has been around for two driver versions and is not going away. If the driver was FLOSS'ed someone could have created a patch. Hell any one of us could pay a programmer to do it. No such luck with nVidia have to wait until they do it.
Isn't there something the bcm43xx driver has that the original didn't?  They GPL'd it instead of BSD specifically so Broadcom couldn't take the extra thing they added to it.  That's why the guys who did it got all in a tizzy about the BSD guys using the bcm43xx has a basis (well, that and if you replace line-by-line, that's not writing new code, that's gradually *deriving* new code, making theirs a GPL-code-derivative so they couldn't BSD license it anyway, though they intended to try)

---

### Post by jiminycricket on 2007-04-21
BTW, nl, it's not unheard of for companies to like the RE.  Even nVidia themselves.  They and ATI have both said they can't release open drivers nor specs because of patents and contracts (some conspiracies wonder if with Microsoft themselves for DirectX, but anyways..), so now they get shiny patent-fee, free drivers.  Probably better coded too, even if the performance isn't amazing, but they can be included in a X.org install OOB for a nice 3d desktop.  The problem is that right now, old ATI cards (and Intel's chips) work better than new crippled ATI cards (..xgl only) and easier than nVidia cards without Nouveau because they can be included.  They also don't have weird suspend and hibernate problems that the binary drivers have.

History--
nVidia used to provide binary drivers for part of thier nForce motherboard.  People RE'd these so they could have a free system.

Now nVidia contributes to the reverse engineered drivers.

---

### Post by DoctorMO on 2007-04-21
[http://thread.gmane.org/gmane.linux.kernel.wireless.general/1558](http://thread.gmane.org/gmane.linux.kernel.wireless.general/1558) - this is the RE violation thread as mentioned above.

jiminycricket, see that is the only power we really have here in the open source world. we either don't use our computers or we create code. and by creating good code we can convince the businesses to invest more resource into supporting the open source drivers that they should have produced in the first place.

There are a number of nvidia cards that are no longer supported by any of the new binary drivers or any of the free and working drivers. all hail to them poor sods.

---

### Post by Tundro Walker on 2007-04-21
In Linux-land, folks usually aren't reverse-engineering things so they can make their own to sell for profit.  They're usually reverse-engineering so they can get some driver to work with Linux, lest they have to take back their new piece of uber-cool $200 hardware they just bought, because the manufacturer was too cheap to support Linux with a driver (and even cheaper, because they won't simply print on the box "does not support Linux").

---

### Post by neighborlee on 2007-04-21
> **prizrak said:**
> It is not impossible to write quality drivers, the FOSS Radeon driver had better 2D performance than the proprietary one for years, it's not possible to gain enough understanding of the hardware to gain an edge. nVidia and AMD video cards are extremely complex devices with their own ASM code. The drivers are equally complex and have alot of very creative and near impossible to duplicate programming. The Nouveau project is aiming to create an operable basic 3D driver. That means that it likely won't have anti aliasing, anisotropic filtering and so on. It will however be able to give you the much loved wobbly windows. 

Another problem with proprietary drivers is the inability to fix them. nVidia driver on their mobile GPU's with TurboCache (steals system RAM as needed) have an issue with Beryl/Compiz when using nVidia's buil-in compositing. The issue is that basically memory isn't getting released and acquired correctly and you end up with black windows (well decorations are visible but nothing else). This issue has been around for two driver versions and is not going away. If the driver was FLOSS'ed someone could have created a patch. Hell any one of us could pay a programmer to do it. No such luck with nVidia have to wait until they do it.

well from your nouveau desscription, Id say its a lovely waste of time, yet full of ego driven wogglygook ;)

but hey its their time to waste I guess ;)

I appears at least Im not alone in this view of whats going on, with Justin chiming in on this...thats good a nice cross-section of opinions to even things out a bit  ;_)

cheers
nl

---

### Post by neighborlee on 2007-04-21
> **Tundro Walker said:**
> In Linux-land, folks usually aren't reverse-engineering things so they can make their own to sell for profit.  They're usually reverse-engineering so they can get some driver to work with Linux, lest they have to take back their new piece of uber-cool $200 hardware they just bought, because the manufacturer was too cheap to support Linux with a driver (and even cheaper, because they won't simply print on the box "does not support Linux").

IM sorry but you wont get much pity from me on that count..its partly linux  fault that vendors arent' paying us more attention..maybe if the linux world was a bit more 'cohesive' we might have better drivers/apps/games.....


I do hope ubuntu continues to take the lead, because imo if all the great open source comrads can agree to work on one code under one collective roof, like windows developer have done all these years imagine how much better linux would be by now and  how many more vendors would have signed onto linux . 

DId no one view that video on 'when  choice is bad' at youtube ?,,I can provide it for anyone wiling to glance through it, because I dont think overall , that we have anyone to blame but ourselves:

[http://video.google.com/videoplay?docid=6127548813950043200](http://video.google.com/videoplay?docid=6127548813950043200)

I know that is getting OT some, but it does apply at least on the front where we are talking about why companies aren't supporting us better..and lets not use the pauldry excuse of well M$ has more advertising dollars,,maybe so but that would be largely irrelevant if there were thousand of devs working on one codebase instead of split between a hundred or so ??..so we can't blame all this on poor ole m$ .

I love OSS as much as the next person for obvious reasons, and the OS's we love so much that dont break the bank for poor people ( linux and unix anyone ? ) because thats what its all about. I have a startrek mentality frankly where I think we should be focused on helping each other and working collecitvely and efficiently on one shared codebase that makes the product better yes , and I think working together should not be underestimated nor restricted to just the linux base.

I understand all the points that are being made about nvidia 'liking' the RE attempts and all, but if this code isn't going to produce anything useable beyond possibly wobbly windows, then what on earth does all this really mean ;))) ? ( assuming poster was correct in that assessment )  I put to you that alot of this is speculation so Im not willing  to get on that bandwagon atm. Has anyone considered that maybe the beryl stuff isn't primetime ready thusly maybe its not nvidia's fault, since its clear if we are RE'ing, that we really have no clue where the fault is atm ? ;)

IM not being a jerk about th is, im just trying to fully understand the entirety of this issue from every possibly perspective.

cheers
nl

---

### Post by BarfBag on 2007-04-21
For those who don't understand, reverse engineering is 100% legal.  The condition is - you can't steel the code.  You have to write it from scratch.

[http://en.wikipedia.org/wiki/Clean_room_design](http://en.wikipedia.org/wiki/Clean_room_design)

---

### Post by DoctorMO on 2007-04-21
> IM sorry but you wont get much pity from me on that count..its partly linux fault that vendors arent' paying us more attention..maybe if the linux world was a bit more 'cohesive' we might have better drivers/apps/games.....

I BEG your pardon sir but this is bull pats; Linux developers owe you nothing, you are no body to them; an ant who has decided to complain that people are busy serving them selves and their friends with good, clean and modifyable software. How DARE you say that you own view is shaded by the fault of Linux developers who indeed I think you owe a great debt and now an apology.

Some people have no respect what so ever, he might as well have just spat in my face and called my a pillok.

---

### Post by prizrak on 2007-04-21
> **neighborlee said:**
> well from your nouveau desscription, Id say its a lovely waste of time, yet full of ego driven wogglygook ;)

but hey its their time to waste I guess ;)

I appears at least Im not alone in this view of whats going on, with Justin chiming in on this...thats good a nice cross-section of opinions to even things out a bit  ;_)

cheers
nl

I'm not part of Nouveau and have a fairly limited understanding of driver development. I don't see it as being a waste of time. There are plenty of Linux users who don't need full 3D functionality of their video cards. I originally got this particular laptop (256MB GeForce Go) so I could play certain Windows video games and play around with XGL. Sometime after that AIGLX that works with Intel cards came out. Since I have a Wii I switched all the way to Ubuntu. Now all I use my fairly powerful (in mobile sense) video card for nothing more than Beryl/Compiz. Another issue with mobile GeForce cards I forgot to mention is the fact that it does not support ACPI. You can't suspend/hibernate the system with the binary driver, the GPU will not throttle down. All those things work on Windows because nVidia could not possibly leave them out there. Simple reason being that no one would buy them. However they don't want to spend time with fixing that on Linux as it's a small enough market. 

This is the thing, no one is telling nVidia open source or else.... We never even asked them for drivers (btw 3DFX the company nVidia bought used to provide 100% free 3D drivers). It's great that the drivers are provided but because of the closed source nature they don't work very well with the FLOSS development model. As many times before, when the manufacturer cannot or will not be able to keep up the community takes over. 

Nouveau's efforts are far from futile though, Radeon driver is RE'd and works pretty well. Quite a bit of drivers for other hardware are RE'd and also work pretty well. FLOSS drivers are much either to port and maintain. They can also be distributed with any distro without question. Whether the nVidia driver is legal to be distributed or not has not been determined yet. Founder of Gentoo is not a lawyer his a programmer and is very much not up to him to decide. The legality is questionable and will remain such until tested in the court of law. FLOSS driver would not have any such issue, it can be included without question.

---

### Post by neighborlee on 2007-04-21
> **DoctorMO said:**
> I BEG your pardon sir but this is bull pats; Linux developers owe you nothing, you are no body to them; an ant who has decided to complain that people are busy serving them selves and their friends with good, clean and modifyable software. How DARE you say that you own view is shaded by the fault of Linux developers who indeed I think you owe a great debt and now an apology. 

Linux is something that helps ( not everyone uses linux for this reason but hey..) those that might not have a golden cadillac in their driveway be able to utilize, so sorry your barking  up the wrong tree ;-) It sounds like you woke up on the wrong side of your ego today sir , because my statementes have been about bettering linux for everyone not just myself , so for you not to see that must mean your looking for something to criticize.  You  are the one that owes an apology, for striking out in ignorance without asking me to verify your concerns ;)

For you to have the audacity to say 'im nobody to them' strikes me as rather arrogant and presumptuous considering that  based on what linux stands for which is the share mentality, im everybit as important as anyone else..not to mention  that the bible ( and other well known holy books )  makes this abundantly clear too  ,, I know christianity the best so Ill speak on it..jesus was very clear about such things sir...love thy neighbor, treat others as you would be treated.....sounds to me we're equal in gods eyes so to presume that linux developers would cast  some den of inequity on me is blabergasting, so maybe you should let them speak for themselves ;)

cheers
nl

---

### Post by Jason_25 on 2007-04-21
> **neighborlee said:**
> IM sorry but you wont get much pity from me on that count..its partly linux  fault that vendors arent' paying us more attention..maybe if the linux world was a bit more 'cohesive' we might have better drivers/apps/games.....

I don't even know where to start here.  Look, Linux is where it is today from the result of internal competition and people having to "reinvent the wheel".  Sometimes, when the wheel is reinvented it comes out better or different.  I think that is a key point of GNU/Linux/FOSS software.
> 
I do hope ubuntu continues to take the lead, because imo if all the great open source comrads can agree to work on one code under one collective roof, like windows developer have done all these years imagine how much better linux would be by now and  how many more vendors would have signed onto linux . 

It wouldn't be better if they were all working "together".  See my first point above.
> 
DId no one view that video on 'when  choice is bad' at youtube ?,,I can provide it for anyone wiling to glance through it, because I dont think overall , that we have anyone to blame but ourselves:

[http://video.google.com/videoplay?docid=6127548813950043200](http://video.google.com/videoplay?docid=6127548813950043200)

I try to stay off Youtube as it's full of childish content, generally requires proprietary software and the video quality is marginal.
> 
I know that is getting OT some, but it does apply at least on the front where we are talking about why companies aren't supporting us better..and lets not use the pauldry excuse of well M$ has more advertising dollars,,maybe so but that would be largely irrelevant if there were thousand of devs working on one codebase instead of split between a hundred or so ??..so we can't blame all this on poor ole m$ .

I think only the people that buy hardware designed for windows are talking about companies not supporting them better.
> 
I love OSS as much as the next person for obvious reasons, and the OS's we love so much that dont break the bank for poor people ( linux and unix anyone ? ) because thats what its all about. I have a startrek mentality frankly where I think we should be focused on helping each other and working collecitvely and efficiently on one shared codebase that makes the product better yes , and I think working together should not be underestimated nor restricted to just the linux base.

It's not about "not breaking the bank". Free software is important because the SOURCE is free.  I.E. not proprietary like the nvidia drivers which you seem to love so much.  I would actually pay money for an open source nvidia driver.
> 
I understand all the points that are being made about nvidia 'liking' the RE attempts and all, but if this code isn't going to produce anything useable beyond possibly wobbly windows, then what on earth does all this really mean ;))) ? ( assuming poster was correct in that assessment )  I put to you that alot of this is speculation so Im not willing  to get on that bandwagon atm. Has anyone considered that maybe the beryl stuff isn't primetime ready thusly maybe its not nvidia's fault, since its clear if we are RE'ing, that we really have no clue where the fault is atm ? ;)

I assume you don't know much about linux gaming or linux in general then if you think the only use for opengl is "wobbly windows".  Please think and research before you post.

---

### Post by igknighted on 2007-04-21
> **neighborlee said:**
> Linux is something that helps ( not everyone uses linux for this reason but hey..) those that might not have a golden cadillac in their driveway be able to utilize, so sorry your barking  up the wrong tree ;-) It sounds like you woke up on the wrong side of your ego today sir , because my statementes have been about bettering linux for everyone not just myself , so for you not to see that must mean your looking for something to criticize.  You  are the one that owes an apology, for striking out in ignorance without asking me to verify your concerns ;)

cheers
nl

neighborlee, he's right... most of the developers (especially in a debian spinoff like this) are staunch supporters of FREE software (as in speech).  They would rather include a lesser 3d driver than a non-free one.  I agree, when I had an ATI x800 I could have used the binary and had better performace, but I chose to use the open driver on principle.  With my nvidia card I am very sad there is no workable 3d driver, and once the RE'd one is workable I plan to use it.  This software freedom is essential, and we need to show the manufacturers that we are serious about open-source and will accept nothing less.  Then when one cracks, the other will have no choice but to follow.  Intel started it, and I think ATI may soon follow, which will screw nvidia over unless they go too.

---

### Post by neighborlee on 2007-04-21
> **igknighted said:**
> neighborlee, he's right... most of the developers (especially in a debian spinoff like this) are staunch supporters of FREE software (as in speech).  They would rather include a lesser 3d driver than a non-free one.  I agree, when I had an ATI x800 I could have used the binary and had better performace, but I chose to use the open driver on principle.  With my nvidia card I am very sad there is no workable 3d driver, and once the RE'd one is workable I plan to use it.  This software freedom is essential, and we need to show the manufacturers that we are serious about open-source and will accept nothing less.  Then when one cracks, the other will have no choice but to follow.  Intel started it, and I think ATI may soon follow, which will screw nvidia over unless they go too.

THeir supposed 'concerns' are NOT in line with the creator of linux then.

So the idea is to force nvidia , rather than engage them in discussion.  Isn't that just a lovely sentiment, we should all be so proud ;)

You will never see me siding with cost vs free software especially when its better ( and proven stat wize ), but when the reverse may be true I see little reason to change,- though I  100% understand and respect your reasons for using said drivers as an end user.

I am all for the day when software is free everywhere for all people as yes this levels the playing field and allows anyone regardless of social class to do things ;-)

I brought up the startrek thing not to sound geeky ( OOPS too late ), but to make a point that its good to work together on common goals , and in so doing have basic ( and some not so basic maybe..)  needs met for everyone....that is why I brought up the  linux dev thing , NOT to accuse or belittle but to offer a viewpoint why I think linux isn't maybe as far as it could be now, and why maybe end users may 'see' this as a end negative. ( My friend is one of them that shares this concern , i'd be happy to  have her come here and voice that similar view if you like ; though I think ubuntu is far closing in on this goal , and kudos to them ;) - )

cheers
nl

---

### Post by macogw on 2007-04-21
> **neighborlee said:**
> Linux is something that helps ( not everyone uses linux for this reason but hey..) those that might not have a golden cadillac in their driveway be able to utilize, so sorry your barking  up the wrong tree ;-) It sounds like you woke up on the wrong side of your ego today sir , because my statementes have been about bettering linux for everyone not just myself , so for you not to see that must mean your looking for something to criticize.  You  are the one that owes an apology, for striking out in ignorance without asking me to verify your concerns ;)

For you to have the audacity to say 'im nobody to them' strikes me as rather arrogant and presumptuous considering that  based on what linux stands for which is the share mentality, im everybit as important as anyone else..not to mention  that the bible ( and other well known holy books )  makes this abundantly clear too  ,, I know christianity the best so Ill speak on it..jesus was very clear about such things sir...love thy neighbor, treat others as you would be treated.....sounds to me we're equal in gods eyes so to presume that linux developers would cast  some den of inequity on me is blabergasting, so maybe you should let them speak for themselves ;)

cheers
nl
Up until recently, every user was a developer.  To the developers who want those days back (or in some cases were simply around in those days), many of today's users are leeching.  As leechers, they have no room to criticize.  It's the old "well FINE, if you can do better, DO IT!"  Complaining doesn't help anything.  Either give real help, or keep your mouth shut.

---

### Post by aysiu on 2007-04-21
Here's something interesting.

From [nouveau's FAQ](http://nouveau.freedesktop.org/wiki/FAQ#head-3a2ff93379b25fe4a7ab81855881004bde5c9059): > **Do you violate NVidias EULA with renouveau?**
No. We don't touch NVidia's binary blob at all, we just observe what the driver changes in memory. All config data we have, is exposed in some /proc or /dev files. And running OpenGL is the main reason why you would use the driver. That is no violation. From Nvidia's [software license for the Linux Display Driver](http://www.nvidia.com/object/nv_swlicense.html): > **Limitations.**
No Reverse Engineering. Customer may not reverse engineer, decompile, or disassemble the SOFTWARE, nor attempt in any other manner to obtain the source code. So I guess it really depends on what you consider *reverse engineer*. Nouveau is very clear about explaining how they create their own code--by observing what the driver does. Nvidia's license agreement seems to imply that reverse engineering is an attempt to obtain the source code. Presumably, reverse engineering doesn't replicate source code but recreates the same functionality with a different source code. Is my understanding of this correct?

I do remember reading an article in *Linux Format* wherein Microsoft accused (sued?) ReactOS of stealing actual Windows code, and ReactOS had to do a full audit on their code to prove Microsoft wrong... or something like that. Maybe I'm remembering that wrong.

Could a programmer confirm this? When you reverse engineer something, are you trying to replicate the source code? Or are you trying to replicate the functionality with different source code?

---

### Post by neighborlee on 2007-04-21
> **macogw said:**
> Up until recently, every user was a developer.  To the developers who want those days back (or in some cases were simply around in those days), many of today's users are leeching.  As leechers, they have no room to criticize.  It's the old "well FINE, if you can do better, DO IT!"  Complaining doesn't help anything.  Either give real help, or keep your mouth shut.

I have been 'trying' to help, but its not always 'easy' to do so.some distros make it harder than others, not to mention that its been 'rough' trying to decide WHICH distro has the best intentions to make linux easy to use for even windows users ( my sister ) , because in the end IMO that is the only way we're going to see increased marketshare and thusly better support all the way around ;)

I will continue to use ubuntu, not because of your hateful remarks but at the end  but because of what it stands for, although im still not sure about all this RE,- and as we've seen its NOT Just me. ;-) [ though sure its clear we are a minority ]

cheers
nl

---

### Post by macogw on 2007-04-21
> **aysiu said:**
> Presumably, reverse engineering doesn't replicate source code but recreates the same functionality with a different source code. Is my understanding of this correct?

Could a programmer confirm this? When you reverse engineer something, are you trying to replicate the source code? Or are you trying to replicate the functionality with different source code?
Usually you just want to replicate the functionality.  I'm sure there are cases where you want the actual code, but that's probably more for finding errors which you can exploit.

---

### Post by jiminycricket on 2007-04-21
[quote=neighborlee]well M$ has more advertising dollars,,maybe so but that would be largely irrelevant if there were thousand of devs working on one codebase instead of split between a hundred or so [/quote]

That's the funny thing, I know you meant advertising in a different way but-- they give "marketing" money to OEMs who pre-install Windows, so in essence they get paid for being all Windows, vs Linux...or something like that.

BTW I don't think anyone's being "hateful"-- it's just an interesting debate.

---

### Post by macogw on 2007-04-21
> **neighborlee said:**
> I have been 'trying' to help, but its not always 'easy' to do so.some distros make it harder than others, not to mention that its been 'rough' trying to decide WHICH distro has the best intentions to make linux easy to use for even windows users ( my sister ) , because in the end IMO that is the only way we're going to see increased marketshare and thusly better support all the way around ;)

I will continue to use ubuntu, not because of your hateful remarks but at the end  but because of what it stands for, although im still not sure about all this RE,- and as we've seen its NOT Just me. ;-) [ though sure its clear we are a minority ]

cheers
nl
How much does "which distro" matter?  Work on a distro-independent project, and they all benefit.  Simple enough.  I still don't get this "Linux isn't easy for Windows users yet" thing.  It's easier than Windows.  You just go.  With Windows you have to figure out how to not have your computer die from viruses.  That's a lot harder than doing whatever the heck you want and knowing nothing bad will happen.

And that wasn't hateful.  That was pragmatic.  Whining is *never* helpful.  Constructive criticism with clear explanations of what needs to be done can be, assuming that the person is even going in the right direction.  If you want to do that, go on Launchpad and give specific blueprints for what you want to see implemented.  We've been doing just fine for over 15 years RE-ing and rewriting.  Oh, and as any hacker will tell you, "you can't do this" just makes you want to do it more.  "You can't have 3d acceleration."  "Oh yes I can, and I'll prove it."

---

### Post by jiminycricket on 2007-04-21
> **neighborlee said:**
> THeir supposed 'concerns' are NOT in line with the creator of linux then.

So the idea is to force nvidia , rather than engage them in discussion.  Isn't that just a lovely sentiment, we should all be so proud ;)
cheers
nl

But they WON'T release open source drivers or specs; it's been asked so many times.  What's to discuss?  Developers are wasting time I guess you could say, but only because nVidia is "forcing" them, I don't think it's the other way around as you've stated.  Only nVidia can fix the bugs in their drivers that many people have mentioned-- they're not really responsive in that realm.  So amongst other things, another plus side of a free 3d driver is that anyone can fix them.

---

### Post by aysiu on 2007-04-21
It couldn't be *more* in line with the creator of Linux, actually.

Linus Torvalds created Linux as a Minix replacement because he didn't have enough money to buy Unix. Should he have "engaged [the Unix creators] in discussion" instead? No. He created a free kernel because there wasn't one of that kind.

That's how almost all Linux/open source development happens. Adobe won't release Photoshop code? Well, we'll create GIMP, then. Microsoft won't release Microsoft Office code? We'll work on OpenOffice, then. 

When companies *do* cooperate with open source developers, the open source developers are only too happy to cooperate and engage in discussion. Look what happened when Netscape open sourced its browser and started the Mozilla project! Now we have Firefox, IceWeasel, Camino, and Swiftfox.

If Nvidia says, "Hey, we're opening up our driver code. Go ahead and integrate it into the kernel," it's not like Linux developers are going to say, "Screw you. We're making Nouveau!" Nouveau exists only because Nvidia is not cooperating.

neighborlee, can you offer any evidence that Nvidia is interested in open sourcing its driver code? If not, then you've confirmed that Nouveau's existence is valid.

---

### Post by qamelian on 2007-04-21
> **neighborlee said:**
> BTW, on this issue of kernel and GPL, I am not the only one that feels this way, as I posted in a earlier post, the founder of Gentoo has this exact same outlook so dont go calling me a troll unless you want to include him in that effort as well ;)

cheers
nl

Good for him. Many of the actual kernel developers say otherwise.

---

### Post by Tomosaur on 2007-04-21
> **neighborlee said:**
> I find it distasteful , because I see no reason to do it in the first place. Isn't this also going to divulge info about their drivers that will make it difficult for them to compete fairly with  ati or other manufacturers ? Why do we need to do this, when all we'd have to do is ask nvidia  maybe for a NDA or something.even so we have decent drivers from them  already, so frankly what is this need ? Does windows have some special agreement with them that we dont making their drivers available to windows developers ?

If  not I"d love to know as I certainly have no idea regarding such high end drivers as these.

cheers
nl

Relying on binary, closed source drivers is not ideal. It is better if the stuff which makes your computer work is open, easily modified etc etc. What happens if nVidia goes bust, but someone discovers a massive security flaw in their drivers? You're screwed, basically.

It is not anti-nVidia to reverse engineer their drivers - and no, it doesn't disclose any information to competitors. nVidia do not charge for their drivers - so they're not losing any revenue, and the drivers do not contain the specification for the hardware for which it was written. If anything - open source drivers could make nVidia more money in the long run, by broadening the market and allowing nVidia cards to work on platforms which they currently do not. The user still has to acquire an nVidia card - but there's no reason why they shouldn't use an alternative driver, if that driver works better for them. All the drivers do is say 'this graphics card recognises this command', and allows the operating system to 'talk' to the device. Besides which - reverse engineering does not mean 'stealing nVidia's code'. All these developers are doing is monitoring the behaviour of nVidia's drivers, then making their OWN code mimic it (this is not EXACTLY the case, it's far more complicated, but you get the idea). To illustrate:

You paint a picture. You use a canvas and some paint, and a brush.
I copy your picture, but I use coloured pencils on a sheet of paper.

The resulting pictures look identical, but the methods by which they were drawn are completely different.

In the same way, the two drivers (nVidia's driver, and the open-source driver), act the same. They perform the same functionality (roughly), but the underlying code may not be all that similar. In the world of software development - standards and restrictions mean that there are a limited number of ways to perform a task.

It is possible that there are portions of code which are identical in each of the drivers, but it is not an intentional theft, and should not be treated as such. If, for example, I say '**My dad is called** John', and you say '**My dad is called** Fred', I'm not going to sue you for intellectual property theft (which is roughly the kind of thing big software companies like to sue each other for). The current situation is absolutely ridiculous, stems from a misunderstanding in how software is written and works, and is allowed to continue by private lobbyists and underhanded deal-making.

The whole area is far more extensive than people can discuss on here, and, frankly, it's been done to death. The nature of software development means that the majority of people do not understand how it affects them - yet the licences people agree to on a daily basis - generally without reading them - go so far as to forbid people to use competitor's products, or to remove all rights of ownership from the user.

===================================================

**I want to make a special post to commemorate this fine quote**.

> **neighborlee said:**
> Linux is something that helps ( not everyone uses linux for this reason but hey..) those that might not have a golden cadillac in their driveway be able to utilize, so sorry your barking  up the wrong tree ;-) It sounds like you woke up on the wrong side of your ego today sir , because my statementes have been about bettering linux for everyone not just myself , so for you not to see that must mean your looking for something to criticize.  You  are the one that owes an apology, for striking out in ignorance without asking me to verify your concerns ;)

For you to have the audacity to say 'im nobody to them' strikes me as rather arrogant and presumptuous considering that  based on what linux stands for which is the share mentality, im everybit as important as anyone else..not to mention  that the bible ( and other well known holy books )  makes this abundantly clear too  ,, I know christianity the best so Ill speak on it..jesus was very clear about such things sir...love thy neighbor, treat others as you would be treated.....sounds to me we're equal in gods eyes so to presume that linux developers would cast  some den of inequity on me is blabergasting, so maybe you should let them speak for themselves ;)

cheers
nl

**I shall now dissect it and respond to each bit I find interesting**:

> 
Linux is something that helps ( not everyone uses linux for this reason but hey..) those that might not have a golden cadillac in their driveway be able to utilize, so sorry your barking  up the wrong tree ;-)
This is not, nor has it ever been, the reason for Linux' existence. Linux was created as a learning exercise, and grew because it was good. Many people and businesses pay for their Linux distribution not because it is cheaper than the alternatives (some distributions are not), but because it is simply the best of the bunch.

> 
It sounds like you woke up on the wrong side of your ego today sir , because my statementes have been about bettering linux for everyone not just myself , so for you not to see that must mean your looking for something to criticize.  You  are the one that owes an apology, for striking out in ignorance without asking me to verify your concerns ;)
I'll remember to submit my opinion to you for 'verification' before I open my mouth in the future.

> 
For you to have the audacity to say 'im nobody to them' strikes me as rather arrogant and presumptuous considering that  based on what linux stands for which is the share mentality, im everybit as important as anyone else..
Not to me, you're not. I suspect the kernel developers, as human beings with family and friends who hold much more importance in their lives than you do, believe the same. Also, Linux does not stand for 'the share mentality'. You can argue that it exists in its current form BECAUSE of the share mentality, but you only exist because your parents had sex. You'd be pretty offended, I assume, if I said you must stand for 'the sex mentality', right? Don't pretend to know the guiding principles of something you evidently don't understand. The FSF / Gnu project are closer to what you're talking about, and neither of those are Linux.

> 
not to mention  that the bible ( and other well known holy books )  makes this abundantly clear too  ,, I know christianity the best so Ill speak on it..jesus was very clear about such things sir...love thy neighbor, treat others as you would be treated.....sounds to me we're equal in gods eyes so to presume that linux developers would cast  some den of inequity on me is blabergasting, so maybe you should let them speak for themselves ;)
Many holy books also advocate the murder of woman for adultery, preach sexism and racial/religious hatred, and demand unwavering allegiance to a mythical creature, but I guess that's all ok because it also has some 'reel purdy sturf' in it, right? What if the kernel developers don't subscribe to your religion (or any, for that matter) - and actually do **not** care one iota what becomes of you? What if they do, in fact, want to 'cast a den of inequity' on you (even though this is both figuratively and literally impossible, because it makes no sense). You may want to take your own advice and let people speak for themselves - you cannot hope to know the myriad of religions and belief systems that any of the kernel developers subscribe to - regardless of the fact that in my experience, computer-science related areas tend to attract atheists and agnostics more than they do religious people.

I would, however, like to thank you for being such a delusional egotist, and the word 'blabergasting', which I'll be sure to use more often than I do at the moment (currently standing at 0) :)

---

### Post by spockrock on 2007-04-21
> **aysiu said:**
> It couldn't be *more* in line with the creator of Linux, actually.

Linus Torvalds created Linux as a Minix replacement because he didn't have enough money to buy Unix. Should he have "engaged [the Unix creators] in discussion" instead? No. He created a free kernel because there wasn't one of that kind.

That's how almost all Linux/open source development happens. Adobe won't release Photoshop code? Well, we'll create GIMP, then. Microsoft won't release Microsoft Office code? We'll work on OpenOffice, then. 

When companies *do* cooperate with open source developers, the open source developers are only too happy to cooperate and engage in discussion. Look what happened when Netscape open sourced its browser and started the Mozilla project! Now we have Firefox, IceWeasel, Camino, and Swiftfox.

If Nvidia says, "Hey, we're opening up our driver code. Go ahead and integrate it into the kernel," it's not like Linux developers are going to say, "Screw you. We're making Nouveau!" Nouveau exists only because Nvidia is not cooperating.

neighborlee, can you offer any evidence that Nvidia is interested in open sourcing its driver code? If not, then you've confirmed that Nouveau's existence is valid.

Umm side note, about open office, basically most of the code is written by paid programmers who are paid to work on OO.org........... just thought I would point it out because a few companies do see the importance of being locked into closed standards.

I dunno if its  a matter of not cooperating, I think the problem here is open drivers do mean that you gain access to how the hardware works, when you are in direct competition with ATI this means instead of ATI RE'ing your hardware, they can just grab your Open source drivers and get your secrets right away.  Though from what I hear the money spent on corporate espionage, is much, much, much greater then the money spent on say countries spying on each other..... so I guess they ways ATI and Nvidia look at is this; if they are gonna get our secrets they better pay $$ for it, instead of getting it for free.....

And Intel opening up their drivers did not out of cooperation or open source, they did it because they can, their gpus are slower and neither ATI or Nvidia really want Intels GPU secrets, there really is nothing to protect on their side, and side benefit is that now instead of Intel making Linux drivers they have a bunch people who will do it for free.

---

### Post by hardyn on 2007-04-21
> **spockrock said:**
> 
And Intel opening up their drivers did not out of cooperation or open source, they did it because they can, their gpus are slower and neither ATI or Nvidia really want Intels GPU secrets, there really is nothing to protect on their side, and side benefit is that now instead of Intel making Linux drivers they have a bunch people who will do it for free.

That said, if intel does get this GPU off the ground, and it does turn out to be a heavy hitter, i wonder what the driver code license will be?

---

### Post by DoctorMO on 2007-04-21
> because my statementes have been about bettering linux for everyone not just myself 

Ah yes sorry, you must simply misunderstand the position of free software and of developers. me being on of them. it's a fact that when I write code I don't care what you think; when you offer your 'advice' I will happily ignore it since your credibility is so low with me personally (simply through your views against free software and my own works) 

When programmers create things they're not really doing it for the good of mankind or for the good of you; they're doing it for the good of them selves. who are you to interject with your own views on what they should do for them selves when they break no laws and hurt no people (meaning it's NOT immoral to do so).

So for you to care about the user community is a bit rich considering with the same breath you dismiss many people who have non supported hardware thanks to the efforts of companies to lock out information about our own hardware; I put to you that you are only for your own view point, an arrogant stuck up position that won't see any reason to mediate on why thousands of programmers choose certain actions which you find distasteful in order to provide themselves and their friends with functionality that they would have otherwise not have access to.

And as for 'blabergasting',, great word keep up the good work.

---

### Post by rai4shu2 on 2007-04-21
> **neighborlee said:**
> ..not to mention  that the bible ( and other well known holy books )  makes this abundantly clear too  ,, I know christianity the best so Ill speak on it..jesus was very clear about such things sir...love thy neighbor, treat others as you would be treated.....sounds to me we're equal in gods eyes so to presume that linux developers would cast  some den of inequity on me is blabergasting, so maybe you should let them speak for themselves ;)

So, you're really George W. Bush in disguise? Have you actually read the bible? "Den of inequity"?

Would a mod here please PLEASE lock this thread? This guy is obviously a troll.

---

### Post by matthew on 2007-04-21
I think this discussion is getting a bit heated. I'm going to close the thread. If I get a few PM's with good arguments (positively worded, not angry rants) as to why it needs to be reopened, I'll consider doing so in a day or two.

---

