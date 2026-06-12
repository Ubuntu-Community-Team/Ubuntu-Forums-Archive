---
title: "Random lockups w/ Jaunty Studio 64"
date: 2009-09-30
forum: Ubuntu Studio
---

### Post by stolenbaby on 2009-09-30
Hey all,
Longtime lurker, first time poster.  I've been using vanilla Jaunty64 on a slower machine for a while with no problems, then I decided to build a studio workhorse with Core i7 architecture.
The install went fine (although I had to disconnect one of my internal drives for the installer to work?), and I've updated the BIOS and nvidia prop. driver (which was a PITA), but I seem to be getting random system lockups.

Sometimes they happen when downloading big files, sometimes while watching movies, and once while recording w/ Ardour.

I was wondering- is this a common problem with the Studio rt-kernel, or should I be pulling individual sticks of RAM for testing?  I ran Memtest and I got errors at the end of test #4, but I'm a noob- does that mean it's definitely a ram issue?

Thanks in advance.

---

### Post by jago25_98 on 2009-10-01
I had a lock up on my simple bog standard i386 dual core laptop. 
It was like an overheat because I couldn't do 

alt+sysRq+R,s,e,i,u,b

to reboot it; I had to hold the power button. 

I don't get this with the normal kernel.

This is with realtime kernel vmlinuz-2.6.28-3-rt - looks stable, but it's got that 3 in it...wouldn't expect these problems. 

We should try running it without the propietory NVidia drivers as I could imagine that causing a problem with a realtime kernel. Let me know if it crashes again or if it doesn't, thx

---

### Post by stolenbaby on 2009-10-01
> This is with realtime kernel vmlinuz-2.6.28-3-rt - looks stable, but it's got that 3 in it...wouldn't expect these problems. 

That's the one I'm running- I feel like the crashes have died down since I updated to the 185.18.36 Nvidia Driver (for 9000 series)- which open one should I try?  I may have mucked up my system getting the one I have to work- when I click Hardware Drivers, the system doesn't seem to know which one I'm using (asks if I want to turn on the one from the repository).

I REALLY hope I won't have to turn off Compiz to use the rt kernel... I just dropped all my savings on this machine, and it would be a bummer for it to not look good. :cool:

I haven't had a crash since my earlier post- I'll let you know if I do.  Thanks for chiming in!

---

### Post by trulan on 2009-10-01
The Jaunty RT kernel has been known to cause random lockups.  It works great on my desktop (occasionally X fails to start, NVidia issue, but once it is up and running everything is fine.) but my laptop barely made it five minutes.   I had rolled back to Hardy on that for this very reason.

I am currently testing Karmic and its RT kernel, which will be out in another month - looks like it's going to be worth upgrading.  So if you keep having lockups you may want to try rolling back to Hardy.  If you can live with Jaunty until Karmic is released, upgrade in a month and all should be well.

Of course upgrading now is possible but there's been a fair amount of breakage as things are being developed and I'd recommend waiting for the release unless you enjoy fixing your machine. ;)  The NVidia drivers don't work for me in Karmic so you wouldn't like it just yet.

---

### Post by jago25_98 on 2009-10-02
I'll try out that Karmis realtime kernel. It's probably best to avoid NVidia closed source anyway. I can always reboot if I need that.

---

### Post by stolenbaby on 2009-10-04
Well, I've had a couple of lockups since my last post, but I think I can live with it until Karmic is released (I don't have any recordings scheduled).  I'm still sort of fuzzy as to how Ubuntu Studio fits in to the big Ubuntu picture- will there be a Karmic Studio 64?  It seems like a lot of people tend to start with regular Ubuntu, load the rt-kernel, then download the studio meta packages with synaptic.  If a bunch of people need to do this to get recording to work, what are the advantages of Ubuntu Studio?  I mean, I like the theme and all, but what are the other major differences?

Also, I still haven't figured out how important passing Memtest (the one with the install disk, I think Memetest86+?) is.  I've read that all memory should pass with flying colors, and if it doesn't then you've got bad sticks.  But I've also read that if your system boots fine and sees all the memory, then it's not a big deal if your ram doesn't pass all the tests.

---

### Post by jago25_98 on 2009-10-04
I'd install the Karmic kernel now on Jaunty. Don't see why that package needs to wait if you can boot straight into the original kernel still

theme? why bother?

Regards memory, I beg to differ on that one! Having a memory fault can lead to no end of bother. I used to work in hardware repair. You definitely don't want to complicate your life with dodgy memory. Swap it out, probably only gonna cost £10 or £20. 
The problems you get from bad memory are weird. You can run everything fine for ages and then only get a problem when loading a game for example (perhaps that's the only thing that tends to use the memory address higher up where the problem is for example). You can then get a crash at any point if any program decides to use that odd bit of memory. This could actually be the source of your crashes, especially as music software tends to use more memory. You can't rule that problem out until you remove the bad memory from the equation.

---

### Post by c00kie55 on 2009-10-04
i got thoes random lockups in jaunty to.. but not in hardy or karmic 
i think karmic is the best yet.. but i realy hope there soon will be a (easy)fix for the nvidia realtime thing..

---

### Post by trulan on 2009-10-05
There is a patch out now that makes the NVidia drivers work with the Karmic RT kernel.  It's not installed by default just yet but the driver should be updated before too long.  Hang in there, the release date is coming!

As far as the difference between Ubuntu Studio and Ubuntu with the studio Packages added, there's not much.  You can pick and choose what you want a little more starting with plain Ubuntu, but then it's a little more to do.

There's also a distro called 64 Studio that is based on a variant of Ubuntu, different than 64 bit Ubuntu Studio or 32 bit Ubunto Studio.  64 Studio carries a reputation of being rock-solid, but Ubuntu gets a lot more developer attention, which is why I stick with it.

---

### Post by Xomm on 2009-10-06
If you -have to- stay with jaunty, I would recommend installing the normal Ubuntu 9.04, and installing the ubuntu studio packages (Synaptic > Search "ubuntustudio" without quotes and mark all you see for installation)

That solves the rt kernel lockups for me. (Other updates and applications -should- be installed after installing the ubu-stu packages, but it's not mandatory)

Eventually I got fed up with the various Jaunty problems not including ubu-stu problems and switched to Hardy (8.04.3)

I don't know about Karmic, so you might want to check out the Karmic solutions if you want a new distro.

(I'm going to test the DVD install for Karmic once it comes out instead of installing via packages)

---

### Post by stolenbaby on 2009-10-10
Cool guys, thanks for all the suggestions.  As it turns out, I think I had bad ram all along- we'll see once I get my replacements sticks in the mail.
Just for testing (I promise!), I loaded Windows 7 onto the machine, and immediately started getting blue screens.
Once I get the machine back up, I plan on trying Karmic, then building from there (instead of ubuntu studio).  I feel like I have a better sense of the default permissions, settings, and programs in the plain ubuntu distros than in ubuntu studio.  Does anyone else feel that way?
Thanks again for the comments!

---

### Post by trulan on 2009-10-10
A word on Karmic:  Users and groups permissions has changed a bit.  Instead of creating an audio group and a video group and making yourself a member, you will need to edit your username's properties and check the boxes labeled 'use audio devices' and 'use video devices'.  It's easier, IMO, but it is a change.  Just a heads-up.

---

### Post by Arcturus691 on 2009-10-11
Just a tip regarding the RAM.  You should make sure your ram has been tested for compatibility by the main-board manufacturer.  I have had errors with Memtest in the past and the problem ended up being a setting/ timing issue with the RAM on the main-board.  Most manufacturers can automatically get the settings from the RAM using SPD.  This is not always the correct or optimal setting.  I have Crucial Ballistics and my ABIT (never again) MB detected the settings incorrectly.  If you want to learn about these settings in depth, there is a wiki on what each timing setting does.  Try doing a search for you MB and memory settings, hopefully someone has already figured out the settings for you.

---

### Post by stolenbaby on 2009-10-20
Joy!  My new RAM passed memtest completely.
> Most manufacturers can automatically get the settings from the RAM using SPD. This is not always the correct or optimal setting.
Yeah, I had to google it and manually change the timings- first time I'd ever had to do that.  But I was getting a ton of errors before and after the change.  It seems to be flying now w/ regular Jaunty.
> We should try running it without the propietory NVidia drivers as I could imagine that causing a problem with a realtime kernel. Let me know if it crashes again or if it doesn't, thx
Yeah, I have a choice when booting whether to start the generic or rt kernel.  If I go RT, I get tons of errors w/ the Nvidia drivers, but it's nice enough to turn them off instead of blow up the system.  I'm looking forward to trying Karmic.
Thanks again everyone for your input!

---

