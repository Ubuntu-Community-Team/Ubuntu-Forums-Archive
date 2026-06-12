---
title: "Ubuntu shouldn't be this slow..."
date: 2007-05-07
forum: The Cafe
---

### Post by Mazza558 on 2007-05-07
This is meant as a follow-up to "Why is XP so much faster?". 

I started a new thread because this time I've got a video to show you what I mean:


[http://www.youtube.com/watch?v=FLasxEE-Ggo]("http://www.youtube.com/watch?v=FLasxEE-Ggo")


XP feels very much more responsive in just about everything I do. Ubuntu just gets me frustrated at waiting for things to happen.

Both installs are new and I haven't tweaked a thing for either (except change XP's theme). In fact, I've got more installed for XP than Ubuntu.

I'm finding that if I want to do something quickly, I'll boot into XP to save time. It shouldn't be like this, it really shouldn't. :( 

Hopefully you can help me with this. I'm using Compiz because Beryl is too slow (Why is it doing this, it was working fine before!)

---

### Post by karellen on 2007-05-07
I know what you mean...from what I've saw in your video your xp is a little faster than mine (which is more than a year old) but still ubuntu feels slower and less responsive. for example firefox loads faster in xp, word 2007 loads faster than openoffice in ubuntu, even outlook is as responsive as evolution...
I got used to it, but still annoys me from time to time. I haven't tried vista though...but I plan to buy a laptop (a dell I hope) with a core duo processor and at least 1 gb of ram and maybe I'll give vista a try...

---

### Post by rai4shu2 on 2007-05-07
Using a 32-bit OS on a 64-bit CPU?

---

### Post by Spr0k3t on 2007-05-07
Just wow.  I really don't know what to tell you here.  From the looks of it, there's possibly something with the way your system is configured.  The startup time alone is quite long.

I zoomed through your other post about why XP is faster than Ubuntu.  Have you installed the "nvidia-glx-new" package for the 7600GS?  That will give you the current stable drivers from the repositories.  Another thing you may be able to do is build a custom kernel removing features you have no need for (bluetooth, firewire).  Just some thought for food.

BTW - Love the Donny Darko avatar.  Listening to Gary Jules right now while I reply to your post.

---

### Post by [h2o] on 2007-05-07
> **rai4shu2 said:**
> Using a 32-bit OS on a 64-bit CPU?
Should not matter. I have a Turion64 and am running 32-bit Feisty, and I feel no sluggishness whatsoever. XP is way slower by comparison but I would give the honor for that to the nice people of Asus who thought that I actually wanted to start two million applications I don't use when I log in ;)

Actually, I saw nothing strange about the video. Disable compiz/beryl and see if that helps. I used to have one of them before, but I disabled them since it made some things a bit slower.

---

### Post by Mazza558 on 2007-05-07
> **rai4shu2 said:**
> Using a 32-bit OS on a 64-bit CPU?

It's supported better (in terms of hardware)


> **Spr0k3t said:**
> Just wow.  I really don't know what to tell you here.  From the looks of it, there's possibly something with the way your system is configured.  The startup time alone is quite long.

I zoomed through your other post about why XP is faster than Ubuntu.  Have you installed the "nvidia-glx-new" package for the 7600GS?  That will give you the current stable drivers from the repositories.  Another thing you may be able to do is build a custom kernel removing features you have no need for (bluetooth, firewire).  Just some thought for food.

BTW - Love the Donny Darko avatar.  Listening to Gary Jules right now while I reply to your post.

I assume the nvidia-glx-new driver is what is installed using Envy? I tried that and had to reinstall (Broken X-Server).

My system shares an Ext3 partition between the 2 OSs so that both get access to music, etc. 

Even the internet seems slower, though I blame that on the BCM linux drivers.

(And yes, my avatar is rather good :)  )

---

### Post by [h2o] on 2007-05-07
[QUOTE=Mazza558;2610027I assume the nvidia-glx-new driver is what is installed using Envy? I tried that and had to reinstall (Broken X-Server).[/QUOTE]
Make sure you are actually using 3d-accelerated drivers for your graphics card. That would make quite an improvement, especially since you run beryl.

---

### Post by Mazza558 on 2007-05-07
> **'[h2o] said:**
> Make sure you are actually using 3d-accelerated drivers for your graphics card. That would make quite an improvement, especially since you run beryl.

Well, if the restricted drivers manager says they're enabled, surely that means they're enabled? :)

(I'm using "nvidia-glx" as my drivers at the moment)

---

### Post by PatrickMay16 on 2007-05-07
I expect firefox 2 is the problem here. But I don't know. And the fade-out effects of beryl might cause things to appear slower.

---

### Post by Nikron on 2007-05-07
You could always try custom compiling a kernel if your system is that slow. Additionally, what's with the 1 character password >_<

---

### Post by plb on 2007-05-07
Gnome isn't exactly known to be a speed demon as well. For me, Feisty did however feel slower than Edgy.

---

### Post by Mazza558 on 2007-05-07
> **Nikron said:**
> You could always try custom compiling a kernel if your system is that slow. Additionally, what's with the 1 character password >_<

I'm the only user of this PC and I hate keyrings with a passion :)

---

### Post by Spr0k3t on 2007-05-07
Actually, the default install of the Feisty restricted drivers is "nvidia-glx" which has a generic driver instruction set covering 5 series up to 7 series nVidia cards.  The nvidia-glx-new is part of the repos with the driver for 7 series and 8 series cards.  This is different from Envy which I've used in the past... it also b0rk3d my system.  The use of nvidia-glx-new works fantastic and since it is a part of the repos, updating the kernel will not break the nvidia drivers.  If you build your own custom kernel, you will need to rebuild the kernel modules every time you want to update.

---

### Post by litemotiv on 2007-05-07
> **Nikron said:**
> Additionally, what's with the 1 character password >_<

:popcorn:

---

### Post by Mazza558 on 2007-05-07
> **Spr0k3t said:**
> Actually, the default install of the Feisty restricted drivers is "nvidia-glx" which has a generic driver instruction set covering 5 series up to 7 series nVidia cards.  The nvidia-glx-new is part of the repos with the driver for 7 series and 8 series cards.  This is different from Envy which I've used in the past... it also b0rk3d my system.  The use of nvidia-glx-new works fantastic and since it is a part of the repos, updating the kernel will not break the nvidia drivers.  If you build your own custom kernel, you will need to rebuild the kernel modules every time you want to update.

How do I go about installing these then? Do I have to remove the old driver first?

And using metacity makes a noticeable difference in speed, apart from the tearing on big windows. By tearing, I mean I can see the window being "constructed" when it opens.

---

### Post by RudolfMDLT on 2007-05-07
I find feisty faster than edgy but sine things in Windows do load faster. Just note on one thing: Word does load much faster, I agree but to help you out, in OpenOffice, click on tools, options. Under the first tab, OpenOffice.org click the memory drop down and tick openoffice quick starter. MS Office has a similar way of making office load quickly. The thing I find very quick in windows is when I do \\10.0.0.5, it's lightning quick at looking up and finding networked machines. Samaba sometimes takes a while.  

In general, Ubuntu does work faster for me than my XP with Norton AV, Spybot S&D, ZoneAlarm, GooglTalk, ICQ, Nvidia control panel ect...

---

### Post by Spr0k3t on 2007-05-07
To install that package```
sudo apt-get install nvidia-glx-new
```and you should be good... no need to remove the other.  Once you have tweaked Beryl, it should flat out fly.

---

### Post by deadlydeathcone on 2007-05-07
> **Mazza558 said:**
> Well, if the restricted drivers manager says they're enabled, surely that means they're enabled? :)

(I'm using "nvidia-glx" as my drivers at the moment)

Since you have Beryl running in the video I think it's safe to say that you have acceleration working properly :o

Here are a few things to try:

1) Turn off as many effects as you can in Beryl, or use Compiz. I have a Geforce 6100 so it might not apply as much to you, but Beryl can really slow things down for me.

2) Increase the refresh rate in Beryl/Compiz to 200, make sure "syncing to vblank" and "detect refresh rate" aren't enabled. In my experience this makes a HUGE difference with nvidia drivers.

3) Try Epiphany instead of Firefox. Scrolling and switching tabs seems noticably faster.

Also, in my experience Windows XP is strictly faster than Ubuntu out of the box, but in a month or so the situation always seems to reverse. If you really wan't to "speed up" Ubuntu, just use Windows for a while :)

With that said, Windows is definitely faster when it comes to the responsiveness of the GUI, but Ubuntu holds up much better under heavy loads, so it's a bit of a trade off.

---

### Post by K.Mandla on 2007-05-07
Is it any faster for you with another desktop?

---

### Post by deadlydeathcone on 2007-05-07
> **Mazza558 said:**
> How do I go about installing these then? Do I have to remove the old driver first?

And using metacity makes a noticeable difference in speed, apart from the tearing on big windows. By tearing, I mean I can see the window being "constructed" when it opens.

Just open Synaptic and check "nvidia-glx-new". The old driver will be automatically removed, and when it's done just hit ctrl + alt + backspace and you're done.

Also, if metacity is much faster Bery is almost certainly the problem.

---

### Post by Mazza558 on 2007-05-07
> **K.Mandla said:**
> Is it any faster for you with another desktop?

Yes.                                                                                                                                                                                                

> **Spr0k3t said:**
> To install that package```
sudo apt-get install nvidia-glx-new
```and you should be good... no need to remove the other.  Once you have tweaked Beryl, it should flat out fly.

That just broke my X Server with "API MIsmatch" and "Failed to initialise Nvidia Kernel Module".

---

### Post by Mazza558 on 2007-05-07
> **deadlydeathcone said:**
> Also, if metacity is much faster Bery is almost certainly the problem.


I was using Compiz before. Beryl is extremely laggy.

---

### Post by Spr0k3t on 2007-05-07
Now that doesn't make any sense.  It works on the 7600 nvidia I have for my wifes computer.

---

### Post by Mazza558 on 2007-05-07
Does anyone else have any ideas on what's up?

---

### Post by esaym on 2007-05-07
I did not notice much of a difference in the video.  The only thing I saw was windows booted ridiculously fast.  I have never seen a windows machine boot that fast.  I am guessing you played with which services load at startup?  The same thing can be done with linux if you have the knowledge.  BUM works to some extent.

I did not notice any difference between the Web browser comparison minus some page loading differences that is probably related to cache. 


So I guess what is slow to you is normal to me?:-k

---

### Post by Mazza558 on 2007-05-07
> **esaym said:**
> I did not notice much of a difference in the video.  The only thing I saw was windows booted ridiculously fast.  I have never seen a windows machine boot that fast.  I am guessing you played with which services load at startup?  The same thing can be done with linux if you have the knowledge.  BUM works to some extent.

I did not notice any difference between the Web browser comparison minus some page loading differences that is probably related to cache. 


So I guess what is slow to you is normal to me?:-k

That desktop was installed a few days ago. I haven't changed any services/system settings at all on XP.


On a related note, I've managed to get the nvidia-glx-new driver installed. :) 

Performance seems a bit better, but Compiz and Beryl seem a bit slow (especially Beryl)

---

### Post by Sunflower1970 on 2007-05-07
They seemed similar to me, except that XP seemed to boot fast. Quite fast. Excpetionally fast. How do I get my XP to come up that fast (lol). But, it looked like once it made it to the desktop it still was loading a few items here and there. Also, XP looked faster to me because it didn't have any of the eye candy going on. XP's screens pop up, while Ubuntu's fade in. That may make it seem slower. A better judge of both systems would be if Ubuntu had Beryl/Compiz turned off, then compare how the windows pop in and out.

ETA:
If you go into Beryl's settings and turn off the blur effect, that may speed things up a bit, as well.

---

### Post by Mazza558 on 2007-05-07
Gah, compiz just makes firefox painfully laggy. I really want to use these effects :(

---

### Post by Mazza558 on 2007-05-07
Is there any way to force frame rates, because I think my desktop is stuck at 50hz :(

---

### Post by Whiffle on 2007-05-07
Do "glxinfo | grep direct", it sounds to me like direct rendering is not on...

---

### Post by kelvin spratt on 2007-05-07
i agree with massa xp is the fastest os on the planet i only have to think about booting up and walla in a split second its booted up and played a 3hr DVD and rebooted into Fiesty now that is what you call ultra fast
but you see fiesty loads and is usable in under 1 min for me and i'm not really interested if xp is faster as i don't have to run the virus scan every day or two clean all the adware 2 or 3 times a day run reg tools every day
defrag on a daily basis because i use it for processing then of course after all that my computer runs virtual continuous 24 hrs a day after a few hours xp has to be rebooted due to memory leaks linux users tell me
that linux can run continuous for years on end so reilly this thread is just ego tripping is it not the speed of your
boot up is not the speed of your work rate nor your security nor stability these are what counts and as far as games u should use a games consul for them as they wreck hardrives.

---

### Post by Mazza558 on 2007-05-07
> **Whiffle said:**
> Do "glxinfo | grep direct", it sounds to me like direct rendering is not on...

```
direct rendering: Yes
```

---

### Post by use a name on 2007-05-07
This is not a comparisson... Does XP run Beryl?

EDIT:  uhm, ok, compiz. But still not on XP.

---

### Post by Whiffle on 2007-05-07
Ok next thought on my list, do things load slowly?  Like do you open a program and it takes forever to pop up?  My theory here is that the hard drives aren't setup correctly.  

if you do 

'sudo hdparm -tT /dev/hda' (or sda or whatever your hard drive is), it will run somewhat of a short hard drive speed test.  
```

root@blacktop:/home/andy# sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1270 MB in  2.00 seconds = 635.64 MB/sec
 Timing buffered disk reads:  116 MB in  3.04 seconds =  38.11 MB/sec

```

Thats sitting on my lap running off battery.  My desktop is plenty quick and this laptop is running nothing special as far as speed goes.  Ill even go so far as to say that ubuntu runs circles around XP on this computer.

---

### Post by Mazza558 on 2007-05-07
> **Whiffle said:**
> Ok next thought on my list, do things load slowly?  Like do you open a program and it takes forever to pop up?  My theory here is that the hard drives aren't setup correctly.  

if you do 

'sudo hdparm -tT /dev/hda' (or sda or whatever your hard drive is), it will run somewhat of a short hard drive speed test.  
```

root@blacktop:/home/andy# sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1270 MB in  2.00 seconds = 635.64 MB/sec
 Timing buffered disk reads:  116 MB in  3.04 seconds =  38.11 MB/sec

```

Thats sitting on my lap running off battery.  My desktop is plenty quick and this laptop is running nothing special as far as speed goes.  Ill even go so far as to say that ubuntu runs circles around XP on this computer.

The output of that is:

```
/dev/sda1:
 Timing cached reads:   1266 MB in  2.00 seconds = 632.38 MB/sec
 Timing buffered disk reads:  134 MB in  3.03 seconds =  44.24 MB/sec
```

---

### Post by Whiffle on 2007-05-07
While that seems a tad on the slow side for your hardware, I don't think its the problem.  I can't think of anything else to check at the moment except for maybe 'top', if you run top in a terminal you may find that a program has crashed and is sucking up your resources, which will bog down just about anything.  I doubt that is the problem but I'll keep thinking about it.

---

### Post by deadguy87 on 2007-05-07
I have no advice. I have two laptops that used to have XP. ON both of them Ubuntu is faster. Maybe because they are low end and windows has never been any good on low end computers. I'm sure that whatever the problem is is you give all these nice people the information they need they can help you out.

---

### Post by Ateo on 2007-05-07
Hmm. Other than XP booting much quicker, Ubuntu is just as responsive for me. Even using Beryl and every . Must be my kick-booty laptop which has 2GB of ram and a core 2 duo. I upgraded my RAM specifically for eye candy. I found that with 1GB of RAM, my laptop was a bit slower but not enough to frustrate me (given that I *MUST* have my laptop for work)...

---

### Post by jiminycricket on 2007-05-08
It's probably options in your xorg.conf.  nVidia has a bunch of odd options.  If you search my post history you should find an nVidia thread about good flags for beryl.

---

### Post by Mazza558 on 2007-05-08
Well, I've pretty much fixed the problem. I turned off "Detect Refresh Rate" in the Beryl Options. Everything is great now :)

---

### Post by Kayne on 2007-05-08
I just found this thread now and I agreed with the threadstarter. I have a nvidia 5900xt card.
And to my surprise, through disabling "detect fresh rates" and "sync to vblank" it is indeed much faster!

---

### Post by phinn on 2007-05-08
The fact is that Windows XP is actually a pretty damn fast OS.   The downsides is its old, has no graphical frills, and is extremely insecure (with spyware and viruses). Also it _costs money_.

I have been using Kubuntu because I have found that KDE (and QT) seems more snappy and responsive than Gnome (GTK)

---

### Post by deadlydeathcone on 2007-05-08
> **Mazza558 said:**
> Well, I've pretty much fixed the problem. I turned off "Detect Refresh Rate" in the Beryl Options. Everything is great now :)

Glad it worked! Did the other two tweaks I mentioned do anything for you?

---

### Post by B. Gates on 2007-05-08
> **phinn said:**
> The fact is that Windows XP is actually a pretty damn fast OS.
Why thank you!

> The downsides is its old,
I believe the term is "mature", which is a good thing when you think about it.

> has no graphical frills,
There are plenty of ways to improve on this (eg. WindowsBlinds). Ubuntu looks fairly crap by default too, you have to stick Beryl on yourself for the extra eye-candy.

> and is extremely insecure (with spyware and viruses).
Only if the users are dumb, and/or aren't ready to upgrade to **ULTIMATE-POWER!** which is Vista.

> Also it _costs money_.
Eh, to be honest, I'd much prefer people pirate my OS than use the competition, which is fine for home users. Business can afford to pony up the cash.

---

### Post by litemotiv on 2007-05-09
> **deadlydeathcone said:**
> 
Here are a few things to try:

2) Increase the refresh rate in Beryl/Compiz to 200, make sure "syncing to vblank" and "detect refresh rate" aren't enabled. In my experience this makes a HUGE difference with nvidia drivers.

up much better under heavy loads, so it's a bit of a trade off.

yea that speeds up things for me too, good one :)

it does trigger my 7600GT's fan a bit more often, but overall it's a nice improvement.

---

### Post by NJC on 2007-05-28
I'd be LEAPING FOR JOY if I saw Ubuntu perform that fast!! OK, at home I'm using (ahem) older hardware and dialup ... but both of your OS'es seemed very snappy and I did not detect much speed difference between them. I'm even comparing their speed with my work P4/2.8Ghz W2K work PC.

---

### Post by Mazza558 on 2007-05-28
> **NJC said:**
> I'd be LEAPING FOR JOY if I saw Ubuntu perform that fast!! OK, at home I'm using (ahem) older hardware and dialup ... but both of your OS'es seemed very snappy and I did not detect much speed difference between them. I'm even comparing their speed with my work P4/2.8Ghz W2K work PC.

That's the problem with even slightly new PCs with only slightly above average hardware - when you have to use a system other people think is the norm, you really notice how slow it is in comparison. A good example of this is when I went round my friend's house. I was getting really frustrated as XP, with Norton on, took 5 minutes+ to boot up. Gah!

Another tip I've learnt if using Beryl:

Don't use closing animations! If you think about it, the lag there is caused by Ubuntu trying to close the thing, get rid of the process in memory, AND fire up the graphics card to render the animation. Things will appear more snappy this way.

A final insight: I just realised that on my XP box, I have no antivirus, no snappy effects, nothing other than a boring interface. I'm sure if there was a way to enable all of these things on XP, it'd be slower than Ubuntu.

EDIT: I think an Ubuntu Speed Tips thread looks in order ....

---

### Post by BrokeBody on 2007-05-28
I had exactly the same problem. So that's why I moved to Fedora, which is running incredibly fast. ;)

---

### Post by frodon on 2007-05-28
XP is surely faster than ubuntu on a fresh install but after just 2 weeks of use it's another story, while XP performances decrease with the time, linux performances don't move, i think the big difference is here IMO.
After that it's sure that a well configured system will run faster.

---

