---
title: "I don't get it."
date: 2009-04-20
forum: The Cafe
---

### Post by ageaux on 2009-04-20
I've been running Linux since Redhat 4.2.  I've piddled with the internals over time but I'm not a hacker type and don't know very much compared to most others.  

I'm really wondering why we (the Linux community) still can't get multimedia running out of the box.  It seems the majority of distros make *changes* on a regular basis, but are we seeing improvements?  

I'll be completely honest with you -- I'd willingly pay the same price (or more) for a Linux distro as those other operating systems.  All I really want would be a system with multimedia that really worked out of the box.

Anyone else feel likewise?

---

### Post by SomeGuyDude on 2009-04-20
Um, what do you mean? The codecs?

If you've been using Linux for that long but "sudo apt-get ubuntu-restricted-extras" or whatever the appropriate command is for other distros is too much for you to handle... well, there's always Linux Mint.

---

### Post by MasterProg on 2009-04-20
Well, I don't think multimedia is that bad in Ubuntu. It is easy to install the needed codecs. Just think - it could be a way worse than it is now.

---

### Post by swoll1980 on 2009-04-20
There's 50 distros that come with multimedia "out of the box" the ones that don't are simply more law conscious than those that do. It has nothing to do with the fact that they can, or can't. If you want to you buy media support from Ubuntu.

.

---

### Post by bobbob1016 on 2009-04-20
Legal issues.  They can't legally bundle a wmv decoder, probably same for mov, without paying.  They make it easier to install codecs each release though.  As in when you open a wmv or mov in totem it says "I don't have the codecs, do you want me to find/install them?" or something.  A lot of the paid distros include codecs in their free versions, as in I know freespire includes/included codecs, not sure what other distros do though.

---

### Post by Skripka on 2009-04-20
It depend on the distros and the packagers.

My experience on Arch is that all the depends the necessary all necessary codecs witht he respective media players.  Thus you install VLC-and everything needed to play anything in VLC hitches a ride--no futzing around with libdvdcss or what have you.

---

### Post by SomeGuyDude on 2009-04-20
Not to mention in the Arch guide it tells you to install the "codecs" package which takes care of pretttttty much everything, then if you throw in VLC or something it'll add all the gstreamer stuff.

---

### Post by gnomeuser on 2009-04-20
> **bobbob1016 said:**
> Legal issues.  They can't legally bundle a wmv decoder, probably same for mov, without paying.  They make it easier to install codecs each release though.  As in when you open a wmv or mov in totem it says "I don't have the codecs, do you want me to find/install them?" or something.  A lot of the paid distros include codecs in their free versions, as in I know freespire includes/included codecs, not sure what other distros do though.

We can do that today with gstreamer and packagekit. Today if you have both installed it will pop up and ask if you want to search for packages that provide the required codecs. You would need to have Fluendo, who provides for pay codecs, to support a repo then it would just work. You could also add a bit of code to the pop up to add a button to open the Fluendo webshop (upstream doesn't do this since they don't want to play favorites with companies) this would be very codina like.

On a standard Ubuntu system since multiverse and universe are enabled this should just work, just confirm that you are not breaking the law.

---

### Post by leandromartinez98 on 2009-04-20
I'm not sure if he is talking about codecs. From my experience there are still significant problems concerning Sound/Wecams/Microphones/Screens in Ubuntu and any other distro I've tried, many of them which I've not been able to solve. Although I don't like to give too much attention to this kind of thread that does not add anything to anyone, I think that these problems are the most important issues to a widespread adoption of Ubuntu. My mom (always our mom's), for instance, cannot use it all the time because her favorite radio decides to not play from time to time (although it does play from time to time, particularly after rebooting...). These are pulseaudio problems that are far from being solved.

---

### Post by SomeGuyDude on 2009-04-20
Just so we're all on the same page here, we DO all get that a big limiting factor is that none of the companies that own the various file formats and hardware have made their own drivers/codecs, so Linux devs are working furiously to find a way to get them to work?

---

### Post by leandromartinez98 on 2009-04-20
Probably we are, although I am not particularly the best person to ask about the technical problems of driver development. But, as other people has already posted in other threads, the most sound improvements of the last releases were not on that field (boot times, and "looks" for 9.10, for instance). I would better like to hear Schuttleworth sayng: for 9.10 we aim to solve most multimedia issues, rather than saying that the looks will be improved to beat the MacOS.

---

### Post by SomeGuyDude on 2009-04-20
> **leandromartinez98 said:**
> I would better like to hear Schuttleworth sayng: for 9.10 we aim to solve most multimedia issues, rather than saying that the looks will be improved to beat the MacOS.

Read the above posts.

The problem is not capability. The problem is legality.

---

### Post by gnomeuser on 2009-04-20
> **SomeGuyDude said:**
> Just so we're all on the same page here, we DO all get that a big limiting factor is that none of the companies that own the various file formats and hardware have made their own drivers/codecs, so Linux devs are working furiously to find a way to get them to work?

No, the biggest problem is that the companies that "invent" these codecs patent them making it legally some what a minefield to do any work there without being hit on the head by a lawyer.

There is naturally also the problem of manpower, with hundreds of codecs and only a few developers talented enough to do the work (codecs are tricky bits of code), considering the specifications very rarely are published. The process requires time consuming reverse engineering. Additionally this same limited developer pool has to support this code, the more users the nastier this bottleneck gets - each moment spend on a bug is not spend on the next big codec leaving us a bit behind.

If you want to help, vote for politicians that are against software patents, it will solve a lot of problems for the Free Software community if these simply didn't exist.

Even though we have countries without software patents it still hampers us since most big investers in Linux who pay for fulltime development are situated in places where they are valid. This puts them in the legal cross hairs of many parties, a risk not many companies are willing to take as they will with 99.999% certainty lose in a court of law. Having limited chances to pay for someone to do this work presents us further with a problem if available development time. It's also not just development, if you as a company distribute the code you can be sued for something called contributory patent infringement.. which will significantly lighten ones wallet.

So, say no to Software Patents, and get a working desktop. Till this problem is solved you can either wait for the patents to expire (in some cases it will happen soonish mp3 e.g. will have it's patents expire in 2012 or so) or you can use patent free codecs like Ogg Vorbis, Ogg Schrodinger, FLAC and Ogg Theora.

I know this sucks rather hard, but we are forced to work within a certain legal framework.

---

### Post by leandromartinez98 on 2009-04-20
> **SomeGuyDude said:**
> Read the above posts.

The problem is not capability. The problem is legality.

No, I don't think it is that simple. I and many others have problems such that the microphone starts to work and after an upgrade stops, sound that worked and stoped working, etc. Of course if all the companies collaborated for the development of the drivers for their own hardware things would be better, but this does not reduce the fact that the multimedia support is still not totally satisfactory. My webcam is one of this cases, it worked in Hardy, it doesn't now in Jaunty. If it worked, there have been a solution, a proper driver, which is now lost somewhere. This is because of an incomplete and probably not integrated multimedia solution for linux.

But we do agree that there is probably people working hard to solve that.

---

### Post by gnomeuser on 2009-04-20
> **leandromartinez98 said:**
> No, I don't think it is that simple. I and many others have problems such that the microphone starts to work and after an upgrade stops, sound that worked and stoped working, etc. Of course if all the companies collaborated for the development of the drivers for their own hardware things would be better, but this does not reduce the fact that the multimedia support is still not totally satisfactory. My webcam is one of this cases, it worked in Hardy, it doesn't now in Jaunty. If it worked, there have been a solution, a proper driver, which is now lost somewhere. This is because of an incomplete and probably not integrated multimedia solution for linux.

But we do agree that there is probably people working hard to solve that.

Yes, we do have problem to address as well. Mostly we are using ALSA today in ways not imagined. Pulseaudio gets a lot of flak but 90% of all the common flaws today are related to bugs in ALSA. These are being fixed, just the other day a very important set of bugs in ALSA that caused PA crashes on common Intel HDA hardware were fixed.

We are getting better, but this at least is a lawyer free zone of work. As such companies like Red Hat are investing heavily in getting the audio stack under Linux whipped into shape with all the entails. 

It is getting better day by day, and just looking at the situation now as compared to a year ago it is much nicer. we do still need to educate application developers better on how to write software that uses audio correctly, the rules are much stricter now since we live in a world of fast user switching where multiple devices can be hooked up and connected in all matters of ways. The policy for all of this much be right.

E.g. take my system. My machine has a built in Intel HDA card. When I am at my home I have it hooked up to my webcam which also has a USB mic in it as well as my USE external soundcard (for support for surround sound as well as digital output). What is the correct policy, which becomes my default input at what times.

Sound is just a whole lot more advanced now than it has been before and the stack needs to be whipped into shape, applications need to be fixed and policy needs to be polished.

They are two different problems though, it is one thing to get this right but if lawyers keep us from putting commonly used audio down these nice pipelines it all seems like suck to the user. This one we are actively fixing though.

---

### Post by leandromartinez98 on 2009-04-20
I am also a long-term linux USER (not developer), and I cannot agree more that things are getting better very quickly. When I first starting using Linux I couldn't imagine installing it on my home machines, and now we use Linux all the time, everywhere, and recently my brother, which is no computer-geek at all, installed and loved it, using it all the time as well. The only barrier for full adoption from people around me are those multimedia issues that are still present, so that's why I believe on their high priority for the desktop.

---

### Post by SomeGuyDude on 2009-04-20
> **leandromartinez98 said:**
> No, I don't think it is that simple. I and many others have problems such that the microphone starts to work and after an upgrade stops, sound that worked and stoped working, etc. Of course if all the companies collaborated for the development of the drivers for their own hardware things would be better, but this does not reduce the fact that the multimedia support is still not totally satisfactory. My webcam is one of this cases, it worked in Hardy, it doesn't now in Jaunty. If it worked, there have been a solution, a proper driver, which is now lost somewhere. This is because of an incomplete and probably not integrated multimedia solution for linux.

But we do agree that there is probably people working hard to solve that.

This a FUNCTION of what I described.

When whoever makes your webcam won't create a driver just for Linux, then the FOSS community has to fill in the gap, meaning designing a driver to work with someone else's hardware. This means massive potential for breakages during updates and new versions.

If hardware companies were more Linux-friendly we wouldn't have these duct-tape solution issues, and it's hard to blame "Linux" (as though it were one company) for not solving a problem that neither Apple nor Microsoft has to deal with.

---

### Post by MaxIBoy on 2009-04-20
Keep in mind that hardware manufacturers only have to support their own hardware, whereas Free Software driver makers often have to support *everyone*'s hardware.

They've done a fantastic job so far. 

They're getting more help these days, too. Intel has been really good about releasing source, ATI is beginning to release source and specs, and Creative Labs is off to a semi-decent start. 


I'm running Debian with the experimental repos, so I'm getting the latest Xorg and drivers, and they're light-years ahead of what's in the latest Ubuntu release. Better times are coming, I can tell you that.

---

