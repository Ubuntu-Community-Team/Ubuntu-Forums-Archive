---
title: "Gaming under VMWare"
date: 2007-03-31
forum: Ubuntu Gamers Arena
---

### Post by Kenja on 2007-03-31
VMWare has incorporated Directx support now, but it is classified as unstable.  I was wondering if anyone had any experience with it.  I'm figuring it to be a better way of playing games for windows than Cedega once all the bugs are worked out.

---

### Post by Majorix on 2007-03-31
I disagree. Because it shares the RAM and CPU and all other resources with the host OS, making it a weak machine. I never used or liked VMs. Go with Cedega instead, it's quite fine.

---

### Post by Perfect Storm on 2007-04-01
I doubt that VMWare will replace wine and cedega when it comes to gaming...

---

### Post by dthomasdigital on 2007-04-03
It worked great when playing Warcraft 3 I tried it last night. I have a pretty beefy system, so that might have had somthing to do with it working so well.

---

### Post by compiledkernel on 2007-04-03
Honestly, as long as your hardware can support it, gaming on a Vmware session isnt bad. Its certainly a lot better of a choice to dual booting. If you have a pumped up enough system, itll handle the load proper.

---

### Post by M$LOL on 2007-04-03
Is this VMWare Server or Workstation you guys are talking about?

---

### Post by compiledkernel on 2007-04-03
Workstation. 

Server doesnt apply the DirectX implementation infavor of remote vmware access. It might be nice to see both aspects into one product. 

Additionally Ive seen some work done with respect to VMGL - 

[http://www.cs.toronto.edu/~andreslc/xen-gl/](http://www.cs.toronto.edu/~andreslc/xen-gl/)

It shows some interesting promise.

---

### Post by M$LOL on 2007-04-04
> **compiledkernel said:**
> 
Additionally Ive seen some work done with respect to VMGL - 

[http://www.cs.toronto.edu/~andreslc/xen-gl/](http://www.cs.toronto.edu/~andreslc/xen-gl/)

It shows some interesting promise.

Could this ever work with DX games?

---

### Post by compiledkernel on 2007-04-04
Im under the impression that its mainly an OpenGL layer for VMs, however I imagine there is some later of DX compatibility in it. 

*Grabs the magic 8 Ball* 

*Shakes* 

All signs point to yes. 

Ok, whos gonna try it?

---

### Post by M$LOL on 2007-04-05
Me. I can't get games to run at all ATM, so I'll try it soon.

---

### Post by compiledkernel on 2007-04-05
I understand that Cedega 6.0 is leaps and bounds beyond its predecessors, not sure if this is any comfort to anyone.

---

### Post by hikaricore on 2007-04-05
> **compiledkernel said:**
> I understand that Cedega 6.0 is leaps and bounds beyond its predecessors, not sure if this is any comfort to anyone.

They also named 6.0 "swordfish"...

/me vomits

---

### Post by M$LOL on 2007-04-08
Anyone tried the new VMWare beta for gaming yet? I'm installing now.

---

### Post by compiledkernel on 2007-04-08
M$LOL - Link to it?

---

### Post by justin whitaker on 2007-04-08
I've got Crossover working well with Steam and World of Warcraft, so I'm not sure if it is worth the expense of getting VMware. Who is going to do the write up and tell us if it is worth it?

---

### Post by M$LOL on 2007-04-08
> **compiledkernel said:**
> M$LOL - Link to it?

[http://www.vmware.com/products/beta/ws/]("http://www.vmware.com/products/beta/ws/")

It says it supports D3D 7 and 8. Does that mean that games with DX7 or 8 will work, but those with DX9 won't?

---

### Post by M$LOL on 2007-04-08
Not too impressed so far, the games I've tried both suffer from heavy graphics corruption, one is DX9.0b, the other is DX7.

I've been looking at Transgaming SwiftShader, could that possibly be used in a VM? I found this: [http://forum.parallels.com/showthread.php?t=812](http://forum.parallels.com/showthread.php?t=812)
Does that have any relevance to our situation?

---

### Post by compiledkernel on 2007-04-08
Again Ive heard that VMGL is a pretty solid way to go. Its openGL though. 

here look. 

[http://www.cs.toronto.edu/~andreslc/xen-gl/](http://www.cs.toronto.edu/~andreslc/xen-gl/)

It is possible to use VMGL aka Xen-GL in conjunction with VMware.

---

### Post by M$LOL on 2007-04-09
I downloaded the tarball, and it wants me to type "make install-guest" in my VMWare guest. How can I do that if the guest OS is Windows?

---

### Post by maddog39 on 2007-04-09
> Go with Cedega instead, it's quite fine.I heavily disagree. I got Cedega 5 with engine version 5.2.9 and absoulutely NONE of my Tripple A games work. No steam/half life 2/counter strike source/half life 2 EP 1 and no Battlefield 2. The latest engine is v5.2.10 and doesnt fix any of my problems.

---

### Post by M$LOL on 2007-04-10
===Update===
Since I haven't been able to figure out how to install VMGL on a Windows guest, I've tried SwiftShader. The game is now almost playable and is no longer suffering from graphics corruption. I still have no textures and the game is pathetically slow, despite my VM's specs being way above the minimum requirement of the game.

Perhaps Cedega will be the way to go... :(

---

### Post by Toadmund on 2007-04-10
How does this VM stuff work?
Does it use one's windows OS, or a virtual windows OS to play games or whatever?
I assume that VMware lets me use windows through Linux?

Fill me in, I don't even know what questions to ask?
This is a threat to Microsoft, eh?

---

### Post by compiledkernel on 2007-04-10
Ok here we go....

In computer science, a virtual machine is software that creates a virtualized environment between the computer platform and its operating system, so that the end user can operate software on an abstract machine. Where VMware is a software that emulates a valid envoirnment therein.

VMware Workstation and server software consists of a virtual-machine suite for Intel x86-compatible computers and x86_64 computers. This software suite allows users to set up multiple x86 and x86_64 virtual computers and to use one or more of these virtual machines simultaneously with the hosting operating system. Each virtual machine instance can execute its own guest operating system, such as (but not limited to) Windows, Linux, and BSD variants. In simple terms, VMware Workstation allows one physical machine to run two or more operating systems simultaneously. Other VMware products help manage or migrate VMware virtual machines across multiple host-machines.

---

### Post by M$LOL on 2007-04-10
Well explained :)

CK, have you got any advice on how to get VMGL working on a Windows guest?

---

### Post by compiledkernel on 2007-04-10
Im still working on it. Ive attempted to dialogue with the dev here and there to grasp whats going on with it. 

Ill let you know.

---

### Post by M$LOL on 2007-04-11
Wow, thanks CK. :)

---

### Post by kvonb on 2007-04-11
I was a cedega subscriber for a while, I stopped because all they were doing is releasing patches for World of Warcraft, not working on getting the thing actually working properly for ALL games.

Then you get a nice monthly e-letter telling how they spent the subscription money on trips to computer shows and great hotel rooms, rather than development.

They need to work on DX7 support and actually get that working before wasting time and resources on DX9 and stupid WOW!

If anyone manages to get "Age of Empires" working on ANY emulator, PLEASE let me know, I will be glad to support it.

---

### Post by fakie_flip on 2007-04-21
I was able to get the orginal Sims playing in VMware Server. It played very well. I had 756 mb of ram. On a machine that had 256 mb of ram. VMware could not even load xp. You need plenty of ram for VMware. Even if your cpu is not that fast, VMware will probably work, but you need plenty of ram.

---

### Post by rastilin on 2007-05-02
I've taken to using Vmware exclusively for all my gaming. I just had too many problems with wine and cedega. In the end it comes down to vmware being the only group to actually get "Rise of Nations" working. Also, in vmware stuff will either run or not run, it won't run up until a specific level then crash X like it might in wine. For that matter, it won't crash X at all, or write random files to your home directory.

So the status in the Beta appears to be as follows...

DirectX supports 7 and 8.1, it also runs DX9 applications that don't use too many DX9 functions, as in, you'll get graphical corruption if you try to run DX9 stuff, but it will run. So some DX9 stuff is usable. The main problem is there's no pixel shaders, if there was, you could even play stalker in DX8 mode. The speed is playable, however games can be a bit jerky. Although between two computers with nearly identical configurations, I suspect it's an issue in something else and not vmware.

In short, it works, well. So I'm going to stick with it.

---

### Post by fakie_flip on 2007-05-07
I wonder how good Windows 95 games would run under VMWare. I've tried Wine, Cedega, and Dosbox with no luck yet, so I either need to put Windows 95 in VMWare or find a small hard drive to put it on with a dual boot.

---

### Post by paradexes on 2007-07-05
With the people who say it will be weak gaming under a VM. You are partially right. Cedega and wine or crossover provide the API layer needed to run windows games under Linux....most of the time. Not all the games work. For the DX8.1 games (and there are many) that do not work under Cedega or Wine, a VM is not a bad idea provided it works there as well. Having both Wine and VMs for gaming is not a bad thing. It increases your overall chances at getting a game running. Although having wine run everything would be the best thing, at this time it is not a reality. But when it is then gaming under VMs will be less of a priority.

---

### Post by stafio on 2007-07-09
fakie_flip - For installing older games, try running winecfg and switching the Windows Version to Windows 95 and then installing the game(s). This was the only way I could get Need For Speed II SE installed and I suspect that it would be the same for some other games. Once it was installed I switched the Windows version to XP and it still ran fine.

---

### Post by Gruelius on 2007-07-11
Vmware Workstation was much slower than Virtualbox for me so i didnt even bother pulling through and testing it. Gaming on linux smells baaaad.

---

### Post by hikaricore on 2007-07-11
> **Gruelius said:**
> Gaming on linux smells baaaad.

ummm.... what??

---

### Post by compiledkernel on 2007-07-12
no kidding hika. 

Gaming on linux doesnt smell bad. If it did, Id software would never make any money. =)

---

### Post by darkmaster on 2007-07-13
Escuse me guys, I came upon this thread because I was looking for informations about VMGL. I've got questions and answers, or I think I have answers at least.
Questions:
1) How could you run a game in a virtual Machine, be it vmware or virtual box, if virtual machine cannot virtualize 3D hardware acceleration but only emulate a 2D videocard? Did I miss something? Are you saying that vmware managed to virtualize for real a 3D card? So it is no more emulated and it uses the real hardware on a PC? This is a really important thing to clarify. I saw months ago that vmware was experimenting directX support but I was wondering what could it be useful for if it was supposed to run with an emulated 3d rendering thrue software rendering....

2) From as much as I can understand, VMGL can only run on a guest using the X graphic server, a guest such as Linux, BSD, eetc., so you cannot run it on windows of course and you cannot use it to play Unreal tournament or any other windows thing. 

3) Why are all of you talking about Virtual Machines and gaming using vmware wrkstation? VMware workstation costs something like 500$, Windows 200$.... are you telling me you bought VMWare workstation and Windows with an original license? Otherwise we're talking for nothing if you just are pirates. Look, wine may not work for many games but it is free software, opensource, gpl, call it as you wish. It is something anyone can download from a repository. So VMWare is not a choice for a Linux user. Unless he's a pirate. :confused:

So answer to this question, why are you considering it as an option? Could anyone ever consider spending 700$ only for playing at a very low speed into Linux? Isn't it better, at that point, to dualboot spending only 200$ for Windows? I don't get it. With 700$ you buy a new PC and you can use it for Windows only, at this point.

---

### Post by BatPenguin on 2007-08-14
> **darkmaster said:**
> VMware workstation costs something like 500$, Windows 200$.... are you telling me you bought VMWare workstation and Windows with an original license?

Just stumbled on this thread and figured might as well comment a bit: I have VMWare Server installed, and it's completely free. I'm pretty sure Workstation (which includes these experimental DirectX features) is free as well. As far as I know, they only charge for the corporate product types / support. 

As for Windows, most of us have once upon a day bought a machine with Windows so it's pretty rare NOT to own a legal copy of Windows (at least 98 or 2000...both fine for most gaming still). So I don't think many people have a need to pirate anything, just simply wipe your Windows install or dual boot and reinstall it as a VM. That's what I did (VmWare server). And dual booting really is not the same...I used to do it for a long time but I much prefer my current VmWare setup. Now I can use the few Windows programs I want to use while my mythtv etc. is still running in the background. Very nice. Hopefully DirectX games will work soon as well.

---

### Post by darkmaster on 2007-08-14
> **BatPenguin said:**
> Just stumbled on this thread and figured might as well comment a bit: I have VMWare Server installed, and it's completely free. I'm pretty sure Workstation (which includes these experimental DirectX features) is free as well. As far as I know, they only charge for the corporate product types / support. 

Sorry, I made a mistake. VMWare Workstation costs now $189 so, yes, I was wrong but you are too. If you want 3D then you pay for it. The Mac Version, VMWare Fusion (Which I'm going to buy as soon as I buy a new IMac) only costs $59.99

---

### Post by darkmaster on 2007-08-22
eheh, batpenguin....
a user replyed admitting that he is a pirate, that he pirates everyday software, Vista, etc... not telng the name here... the moderators, aniway, already deleted the post. i was going to report it immediately aniway. SO a lot of this people ARE actually pirates for sure as I told you. Switching to Linux should mean using opensource software for as much as is possible. Otherwise, no real meaning in switching. If one has got to be a pirate, a criminal (Because that is the real meaning and implication of copying and using counterfacted software), then there's no reason why he shouldn't use OSX or Windows :D
I'm also sad to see that I was right. Very sad, but that's just reality these days. That "smarT" criminal user who replyed concluded the sentence with "welcome to internet". Wel, I must say, he understood nothing of this all. So, please, pirate user, go home, use your pirate software on Vista and don't come here anymore. Linux is not for you. Read the GNU guideline and philosophy please... :mad:

---

### Post by hikaricore on 2007-08-22
Eh, I removed his post.  Sorry folks.

What it comes down to is that there will always be people who steal things, software or otherwise.
Which is fine by me personally.  If you're stealing/pirating things, then you obviously have your reasons, and I respect that.

**Keep it off the forums.**

_The ignorance of someone_ coming right out and saying it on a public Linux forum (that automatically tags your posts with your IP address) and describing the specifics of which software they have pirated lately/stolen in the past just blows my mind.  We're not here to tell you what you can/can't do, and can/can't talk about, however on such a forum as this it's not appropriate in the least, and can be damaging to the community.

Everyone knows that it's out there, hell it's the Internet.  [COLOR="DarkRed"]But don't be a moron about it.
[/COLOR]
^_^

---

### Post by BatPenguin on 2007-08-22
> **darkmaster said:**
> eheh, batpenguin....
a user replyed admitting that he is a pirate, that he pirates everyday software, Vista, etc...

OK, I see  - my bad, sorry. Didn't understand that stuff like that had been said, I didn't see it as it had been deleted.

And as for Workstation, yeah, you're right: $ 189. I must've just seen the 30 day free trial download links when I was on their page last time. Anyways, I'm using the VMWare Server now but will certainly upgrade to Workstation the moment it truly supports DirectX well enough to play games like Oblivion, Battlefields etc. Does it now, by the way? Can anybody say whether Battlefield 2 & 2142, Oblivion and LOTRO are playable with Workstation now?

About the price, sure $189 is pretty high still, but for me personally, I don't think it's too high to pay for the benefit of gaming not interrupting the stuff I normally do on my Linux box. It'd be worth it to me if I'd be able to game without a dual-boot for that price (around the price of maybe 4 games) so I'm personally very excited about this technology and having the option of still gaming but not dual-booting. One of the features the Mac Fusion (as far as I know) has that I'd love to have on Linux is having the Windows programs truly intergrated into the OSX so that you don't even have to see Windows's Teletubbies background or Start button :). That sounds great.

---

### Post by darkmaster on 2007-08-22
> **hikaricore said:**
> Eh, I removed his post.  Sorry folks.

What it comes down to is that there will always be people who steal things, software or otherwise.
Which is fine by me personally.  If you're stealing/pirating things, then you obviously have your reasons, and I respect that.

**Keep it off the forums.**

_The ignorance of someone_ coming right out and saying it on a public Linux forum (that automatically tags your posts with your IP address) and describing the specifics of which software they have pirated lately/stolen in the past just blows my mind.  We're not here to tell you what you can/can't do, and can/can't talk about, however on such a forum as this it's not appropriate in the least, and can be damaging to the community.

Everyone knows that it's out there, hell it's the Internet.  [COLOR="DarkRed"]But don't be a moron about it.
[/COLOR]
^_^

thanks hikari for the good work. All we ABSOLUTELY do NOT need in this foruma nd in the entire Linux community is beying addressed by big companies such as MS as a community full of criminals and pirates. they already say this lie enough for my tastes. Let's not give them something to use against single persons and the entire community too.

Then again, but that's a personal opinion, I really consider aberrant pirates in general. That's because they don't understand how much damage can piracy cause to Linuc and Opensource community in general. If commercial softwares continues to be popular and used because of piracy (Cracks, etc.) then ther'es no reason why someone should use, let's say, The Gimp, nevertheless there's no reson why one should switch from Vista to linux. It's the same. If they continue to consider piracy something normal and usual, then everyone will keep running pirates OSes with pirated software only.... and that's really sad. Something like a big silent mafia.

Sorry, not here to make sermons. Like you, I only stay astonished when I see people of that big ignorance in the net, specially in a Linux community Forum (You'd think most Linux users are at least informatics amateurs)...

I'd like to see if there was really no way of cracking Photoshop what would happen. Surely nodoby would buy it for fun only: who can afford more than $1500 ? In that case surely a mass of people would use softwares like Gimp or Krita, etc, and they would have an enormous sprint forward to become better than now. That's for SURE.

---

### Post by darkmaster on 2007-08-22
> **BatPenguin said:**
> 

And as for Workstation, yeah, you're right: $ 189. I must've just seen the 30 day free trial download links when I was on their page last time. 

No problem, afterall I was wrong with the price too :)

> **BatPenguin said:**
> Anyways, I'm using the VMWare Server now but will certainly upgrade to Workstation the moment it truly supports DirectX well enough to play games like Oblivion, Battlefields etc. Does it now, by the way? Can anybody say whether Battlefield 2 & 2142, Oblivion and LOTRO are playable with Workstation now?

Look, in the vmware page there should be a page with a list of popular games supported. Look in the Fusion page (Workstatiuon is the same afterall). You may also want to consider parallels desktop, another great program of that kind.

In the Opensource community something's moving too. look for VMGL, it now works only for *nix systems, and that's bad, I even think it is useless that way. Maybe in the future things will change, but for now...

> **BatPenguin said:**
> About the price, sure $189 is pretty high still, but for me personally, I don't think it's too high to pay for the benefit of gaming not interrupting the stuff I normally do on my Linux box. It'd be worth it to me if I'd be able to game without a dual-boot for that price (around the price of maybe 4 games) so I'm personally very excited about this technology and having the option of still gaming but not dual-booting. 

Yeah, sure, what I was saying is that if somebody actually buys a program it's all ok with that, as long as it is not pirated!!
Also, you do buy vmware but then need a windows license too. And sure, you say about the laptops and things, so ok, you own one but... it is not sure if it is legal. Because they say that the license is only linked to that particular system, not a virtual one, so issues may come with this too (bundle software). I own a bundle free old copy of XP bought from ebay for that reason, infact :) cause it's hardware free. As long as you use it on only one pC at a time, sure.
So, the moment I'll buy my new Imac, sure I'll consider buying vmware fusion or parallels desktop too, for the 3D hardware acceleration.

> **BatPenguin said:**
> One of the features the Mac Fusion (as far as I know) has that I'd love to have on Linux is having the Windows programs truly intergrated into the OSX so that you don't even have to see Windows's Teletubbies background or Start button :). That sounds great.

Every system has it already, even the opensource ones. Look at this link, it isn't difficult to set up, vmware makes it automatically but it's not a feature it only has :) by the way, parallels makes it automatically too!

[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

---

### Post by vexorian on 2007-08-23
> I disagree. Because it shares the RAM and CPU and all other resources with the host OS, making it a weak machine. I never used or liked VMs. Go with Cedega instead, it's quite fine.
Yes and no.

In many ways, computers these days are exceeding in performance, so much that running 2 OSes at once is not that bad.

It is also worth noticing that if directx was implemented fine it wouldn't hurt performance as much as it looks like initially, afterall you are not running 2 games at the same time...

---

### Post by Eddie Hung on 2007-08-26
Uhm.. excuse me for butting in, but are some of you aware that the VMWare free products (Server/Player) should both include experimental 3d acceleration support?

I can definitely confirm with the server version, as I've had Joost running under a WinXP VM with it enabled.

Can't remember the command off the top of my head, but the big G will tell you - it requires editing the vmx file yourself.

I'm also not sure the state of the Server/Player experimental support (but I am aware that the latest Player version was released after the Server version - the Player is the same one as is bundled with Workstation, so maybe a little further down the line) - and how the support on them both, and Workstation, compare to the Fusion product - seeing as support is still claimed to be experimental in the these three, but in Fusion it is a selling point.

Eddie

---

