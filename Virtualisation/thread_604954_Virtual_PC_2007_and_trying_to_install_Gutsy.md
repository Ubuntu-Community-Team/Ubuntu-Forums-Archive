---
title: "Virtual PC 2007 and trying to install Gutsy"
date: 2007-11-06
forum: Virtualisation
---

### Post by SyCo123 on 2007-11-06
Hi,
I'm running Vista Business and am able to run XP in virtual PC 2007, but I can't install Gutsy. I get to the install screen,  I choose 'Start or install' and a popup with /casper/vmlinz' appears I click OK and nothing!

Any ideas?

(I'm trying to impress my ex 'window app developer' boss here, LOL)

---

### Post by netbandit on 2007-11-06
Are you sure that you want to run VirtualPC?  Anecdotal reports are that VirtualPC 2007 is slow compared to VMWare.

Please consider VMWare... or better yet, put Ubuntu on the real hardware and virtualize Windows.

(sorry I had to say it)
-nb

---

### Post by Dark_X on 2007-11-06
Virtualbox is also very good.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by SyCo123 on 2007-11-06
I'm at work so the choice isn't mine even so I looked at both suggestions. Is VMWare commercial software? I see a free VMWare player but will that give the same functionality as virtual PC?

I installed Virtualbox but I've got to the same point. I can use the up/down keys to navigate the menu but when I hit enter it just locks up.

Where next? 

(Boss impressed level not too high right now, lol. )

---

### Post by netbandit on 2007-11-06
VMWare Server is free.  It is about as free as VirtualPC from my understanding, but you may have to check with your legal department to verify.  Odds are that if they read the VirtualPC license/EULA they won't like it any more than VMWare's.

-nb

---

### Post by SyCo123 on 2007-11-06
LOL, maybe so. I'm trying to convince the boss that spending 1000's of dollars on software isn't always necessary and this is how he want to see it running. We have enough boxes here to run a dedicated Linux box but you don't know how far I've brought him just getting him to agree to 'checking it out' in a virtual manager.

I have DSL running in virtual box but Ubuntu (my flavor of choice at home) will stubbornly not do anything past the first screen.

---

### Post by netbandit on 2007-11-06
If your boss insists on selecting your virtualization package, then he is setting you up for failure.  He's probably a Microsoft drone, and is trying to create a situation where you will do something to jeopardize your employment.  BE CAREFUL!
-nb

---

### Post by SyCo123 on 2007-11-06
Thanks for the concern but I'm safe as houses at this position, There's a shortage of quality PHP programmers in this neck of the woods. PHP is the one concession to OSS, but he sure is a fan of M$. 

Any ideas on my problem?

I can't get DSL to install as it see hda1 as 0 bytes. I don't care if I can't install DSL but was just trying to see if I could. Ubuntu would be nice though

---

### Post by netbandit on 2007-11-06
This is an Ubuntu forum and not Damn Small Linux... that being said I don't know why DSL is not able to detect your drive.  See if you can get an Ubuntu CD somewhere.  Never underestimate the bandwidth of a car full of CD's traveling down the highway at 70MPH.

-nb

---

### Post by sstusick on 2007-11-06
Go with Virtual Box.. I wouldn't use anything of M$'s.

---

### Post by SyCo123 on 2007-11-06
I'm using virtual box with Ubuntu 7.10  but it doesn't work either. I have a CD and have the ISO captured.

(I only tried DSL to see if it would run and posted the info to see if it would help solve my issue. )

The boss has gone home. Ah well even though there is no way to repeat a first impression there's always tomorrow!

It's be great to get this working, I just have no idea what the issue is. Does anyone?

---

### Post by SyCo123 on 2007-11-07
Would anyone be able to help with my issue today or would you have any ideas why the install won't start?

---

### Post by techstop on 2007-11-07
> **SyCo123 said:**
> Would anyone be able to help with my issue today or would you have any ideas why the install won't start?

VPC2007 is a legendary dud turd when it comes to virtualising Linux. Please use a better application. Both VMWare Server and VirtualBox are free and come highly recommended. You can see for yourself how bad VPC2007 is;

[http://www.google.com.au/search?q=vpc2007+ubuntu+install&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.com.au/search?q=vpc2007+ubuntu+install&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

But if you insist on polishing a turd, this might be of some help;

[http://arcanecode.wordpress.com/2007/02/26/installing-ubuntu-610-on-virtual-pc-2007-step-by-step/](http://arcanecode.wordpress.com/2007/02/26/installing-ubuntu-610-on-virtual-pc-2007-step-by-step/)

But please, use a better application!

---

### Post by SyCo123 on 2007-11-07
Whoa there fella,

Polishing a turd is a little harsh considering I have already installed virtual box (see my second post). :). I didn't install VMware as I though you had to pay. I've since seen you don't and have tried that too. Same result, no joy

So I tried what should have been a obvious thing and burned a CD and booted off it and it gave the same result too. Dodgy ISO arrgh!

I've since downloaded a new ISO burned it again and have tested it and all is good. In fact I'm typing this from the live CD!

I'll have to wait until tomorrowto try it in a VM.

For the record I think VirtualBox is the best of the bunch, clean and simple to use. Why VMWare is raved about so much I don't know. If I hadn't used the other 2 first I wouldn't have had a clue how to use it.

Thanks for  your attention to the thread, I'll let you know how it goes.

---

### Post by techstop on 2007-11-07
> **SyCo123 said:**
> Whoa there fella,

Polishing a turd is a little harsh considering I have already installed virtual box (see my second post). :). I didn't install VMware as I though you had to pay. I've since seen you don't and have tried that too. Same result, no joy

So I tried what should have been a obvious thing and burned a CD and booted off it and it gave the same result too. Dodgy ISO arrgh!

I've since downloaded a new ISO burned it again and have tested it and all is good. In fact I'm typing this from the live CD!

I'll have to wait until tomorrowto try it in a VM.

For the record I think VirtualBox is the best of the bunch, clean and simple to use. Why VMWare is raved about so much I don't know. If I hadn't used the other 2 first I wouldn't have had a clue how to use it.

Thanks for  your attention to the thread, I'll let you know how it goes.

Ahh, the old dogy ISO trick! Good luck with your virtualisation quest.

---

### Post by SyCo123 on 2007-11-08
I'm back at work and everything is going very well, with one problem. No sound.

When I test  sound in System>pref>sound I get this error (with Sound Events>Sound playback set to auto detect)
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

In the Device Manager I cant see a sound card. In Vista it's listed as a SoundMAX Integrated Digital HD.

Any ideas?

(As a fairly new member to the forums, I'm not sure if it would it be proper to close this thread and post elsewhere, start a new thread in Virtualization or continue this thread?)

---

### Post by erginemr on 2007-11-08
Hello there.

I am also using VirtualBox at work under Windows to virtualize Ubuntu 7.10.  (Missing it so badly up until the evening, if you know what I mean ;)) 
I also find VirtualBox a top-notch program, right up there with VMWare, and light years ahead of Virtual PC (after M$ bought Connectix, that is).

Anyway, the fact is VirtualBox does not emulate the sound card by default. You need to look at the various settings of your Virtual Computer and enable the emulation of the sound card from there.

---

### Post by SyCo123 on 2007-11-08
Hi erginemr and thanks, I've found the setting and enabled the sound card. So that means, I'm there

SWEET :)

Thanks everyone for the help!

---

