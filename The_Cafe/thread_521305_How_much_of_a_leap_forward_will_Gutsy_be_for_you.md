---
title: "How much of a leap forward will Gutsy be for you?"
date: 2007-08-09
forum: The Cafe
---

### Post by Mazza558 on 2007-08-09
With all the new support and features such as bulletproof X, how much do you think the amount of work you put in to set up Ubuntu initially will be reduced?

For me, with an Inspiron 1501, I'm hoping for out of the box wireless and compositing, which will solve all my current problems. For me, it'll probably be a huge leap.

---

### Post by LaRoza on 2007-08-09
I am going to get the next LTS version, so Gutsy is not what I will be using.

I am going to get it for my collection, but I will not use it as my primary OS.

---

### Post by sunexplodes on 2007-08-09
I've heard good things about the wireless support, but I can't really find any concrete info. 

I've become something of an NDISWrapper professional, but it'd be nice not to have to make the extra step.

---

### Post by hessiess on 2007-08-09
it has composoting enabled by defalt, witch is somthing extra to remove, so its a step back

---

### Post by igknighted on 2007-08-09
> **Mazza558 said:**
> With all the new support and features such as bulletproof X, how much do you think the amount of work you put in to set up Ubuntu initially will be reduced?

For me, with an Inspiron 1501, I'm hoping for out of the box wireless and compositing, which will solve all my current problems. For me, it'll probably be a huge leap.

Bulletproof X is a bit of a misnomer.  The X session that loads if the driver fails is not really usable (vesa driver with really low res).  At least this is according to the spec on launchpad.  What they should really try to do if they want this to be useful is make it like Fedora's.  If my nvidia driver fails in Fedora, it still tries to optimize my X session (as if I was booting a liveCD).  I still get 1280x1024 resolution and it uses the nv driver instead of vesa.  In the very least, you should be able to create a secondary xorg.conf so if one fails you can determine exactly what the fallback settings are.  Honestly, 800x600 or 640x480 are more worthless to me than just getting dumped in a terminal because you can't do anything at that res and you'd likely go to tty1 anyway to fix the problem.

As for wireless, don't hold your breathe.  I know kernel 2.6.22 rebuilt the wireless stack, but I haven't seen any improvements (in fact I've seen more complaints than ever... it could take a few kernel releases to iron out the bugs).

Not to sound pessimistic, but I think getting your hopes up for a huge change from Feisty to Gutsy is just unrealistic (unless you plan on migrating to KDE4, assuming it makes it into the repos).  There will certainly be improvements (after all, why else release a new version?), but I think on the whole the experience will be similar.

---

### Post by Sunflower1970 on 2007-08-09
I'm already using the 2.6.22.9 kernel in Feisty, and for me, on my laptop, suspend works flawlessly again. I don't think there'll be any big changes for the desktops, though..So, for me, with suspend, it's a big leap.

---

### Post by Old Pink on 2007-08-09
[CENTER][LIST]
[*]A pretty big leap, there are a few new features I like and a few problems that could be solved
[*]**--- I'm Here ---**
[*] I don't think it'll offer any improvement on my situation at all.[/LIST][LEFT]I don't think it'll solve anything, as such, there's nothing to be solved on my current two systems. (Although Direct Rendering on my old ATI card would be nice, but it still works perfectly as is.)

But I'm looking forward to some of the features, and the general upgrade. :)
[/LEFT]
[/CENTER]

---

### Post by mcurtiss1970 on 2007-08-09
my wireless just worked, so i'm wondering if i even need to upgrade when the time comes.  i'll make taht decision when the time comes and people review the changes and /or upgrade successes

---

### Post by Depressed Man on 2007-08-09
I don't think it'll change much. I tried the Gutsy kernal and I actually lost the ability to control my laptop's screen brightness.

So hopefully that'll be fixed with the work being done on Sony laptops.

---

### Post by wersdaluv on 2007-08-09
If I can sync my Pocket PC with Kontact on Gutsy.. Oooh...

That's a freaking HUGE leap!

:KS

---

### Post by a12ctic on 2007-08-09
I think every upgrade towards ubuntu has been a massive leap, and I've been using it sense 4.10 on and off. I think that 5.10 was the first version I could acctualy use and be happy with for my primary OS.

---

### Post by stimpack on 2007-08-09
I figure no change, if only because Fiesty works well for me. In fact Fiesty was the first to handle my Wireless WPA on Broadcom.

I will ofc immediately get Gutsy on release :o, I am sure benefits will come apparent even if Feisty seems fine at this time :).

---

### Post by vexorian on 2007-08-09
I think regardless of how usable the X session if driver fails would be, it is a major step forward, since the user might be able to use it for repair instead of freaking out.

And I also figure the laptop improvements are huge.

---

### Post by igknighted on 2007-08-09
> **vexorian said:**
> I think regardless of how usable the X session if driver fails would be, it is a major step forward, since the user might be able to use it for repair instead of freaking out.

And I also figure the laptop improvements are huge.

Oh it is a step forward, but it seems like they could have done so much more with it.  I mean, how hard would it be to have a failsafe xorg.conf file?  It'd be like a couple more lines of code (I don't know C, otherwise I'd try to add it and report back), but a simple catch should X fail to load and switch to the other file and try again... initially it could be a very low res thing, then after you had a stable setting and tried to change xorg.conf (like to enable nvidia drivers) it could ask you if you wanted to use your current file as the secondary, and you could just click OK and if the driver install went wrong it would go "oops" and you would go right back to where you were before with a little error message to tell you.

This doesn't belong in this thread (runs off to launchpad...)

---

### Post by zero244 on 2007-08-09
Hello; To be honest I have heard very little about Gutsy.
I have one machine running Edgy and one running Feisty.

I think Ubuntu at some point is going have problems with its own success. Sort of like Windows Vista. In my opinion Vistas biggest competitor is XP.
Ubuntu users will be doing the same thing. They will say my current Ubuntu does everything I need so why should I do a fresh install of the Latest release.
I personally think the release cycle is too short for Ubuntu. I think they should make it 1 year in between releases.
We've seen problems with Feisty in a variety of areas.
For one Network Manager in Feisty is still buggy.
I had the apic error problem in Feisty, which I fixed but it was crashing my machine till I found a workaround. I don't have the apic problem in Edgy.

Whats the rush? It almost seems like Ubuntu feels if it doesn't come out with a bigger better version every 6 months people will lose interest.
I think a year or even two years in between major releases would give time to make sure problems are fixed and new features work right.
I for one don't like the idea of doing fresh installs every 6 months.
I realize I don't have to do updates but when I do a major update I want to be fairly assured that the new release is stable and ready for prime time.

For a many people Feisty wasn't ready for prime time, and in a lot of cases these were first time users who were soured on Linux right from the beginning.
We know why MS rushes things out the door the almighty buck. Im not really sure why Ubuntu is rushing releases out to the general public.

Hopefully someone can clue me in on this.

---

### Post by vexorian on 2007-08-09
> 
Hello; To be honest I have heard very little about Gutsy.That's probably because it is still on alpha -.-

> I think Ubuntu at some point is going have problems with its own success. Sort of like Windows Vista. In my opinion Vistas biggest competitor is XP.Vista's biggest competitor is XP, not because XP is good, but because vista is terribly bad. So this won't happen to ubuntu because improvement and evolution is somethin inherent to open source.


> Ubuntu users will be doing the same thing. They will say my current Ubuntu does everything I need so why should I do a fresh install of the Latest release.But canonical doesn't sell stuff, so it wouldn't be a problem, even if that happens.


> I personally think the release cycle is too short for Ubuntu.
It isn't.

>  I think they should make it 1 year in between releases. They do, that's what an LTS is...

> Whats the rush? It almost seems like Ubuntu feels if it doesn't come out with a bigger better version every 6 months people will lose interest. Yes, they will. Not you and that's what the LTS is for, for you, but there are plenty of people that will really dislike not to have the latest versions of software.

> I for one don't like the idea of doing fresh installs every 6 months. Then don't install every 6 months.


> I realize I don't have to do updates but when I do a major update I want to be fairly assured that the new release is stable and ready for prime time. And you are.

> For a many people Feisty wasn't ready for prime time For me it was, and it was a huge improvement, like the difference between "nice hobby" and "I'll use this OS all the time".

But fesity was not an LTS, please understand that.

> We know why MS rushes things out the door the almighty buck For god's sake, they don't , they have delayed Vista like 2 years.

> Im not really sure why Ubuntu is rushing releases out to the general public. They aren't rushing it. And I can name a couple of key fixes in gutsy that will be very important, if instead we waiting 6 months it would be devastating...

---

### Post by Warren Watts on 2007-08-09
Feisty worked "right out of the sleeve" for me, and really hasn't given me any problems at all since I installed it better than 12 weeks ago.

However, when I read about all the problems folks had moving from Edgy to Feisty when Feisty was first released, I think I am going to take a "wait and see" attitude when Gutsy is released.

If after a period of time there don't seem to be any significant problems I'll migrate, and if there are problems, I'll wait until the problems have been resolved before migrating.

I'm not interested in being a bleeding edge user.  Ubuntu is my primary OS, and I need to have a stable OS.

Feisty has been without fault in this regard.
In the 12 weeks since I installed Feisty, know how many times Feisty has crashed?  **NONE**.
The only times I have rebooted have been after receiving an update that said I needed to, like after a kernel update.

---

### Post by jclmusic on 2007-08-09
as the one before an LTS release, it should be a step forward from feisty shich will be good :) unlike edgy being a step back from dapper because it was the 1st of a new release cycle. 

i am also looking forward to kde 4 and the new sand easier to configure version of xorg.

---

### Post by FuturePilot on 2007-08-09
For my laptop, no improvement since I haven't been able to run anything newer than Dapper because it just freezes.

On my desktop it will be an improvement though.

---

### Post by mcurtiss1970 on 2007-08-09
> **wersdaluv said:**
> If I can sync my Pocket PC with Kontact on Gutsy.. Oooh...

That's a freaking HUGE leap!

:KS

that's your wish, right, not what's actually coming? 

because then i'd update the day it came out! :)

---

### Post by Arathorn on 2007-08-09
> **jclmusic said:**
> as the one before an LTS release, it should be a step forward from feisty shich will be good :) unlike edgy being a step back from dapper because it was the 1st of a new release cycle. 

i am also looking forward to kde 4 and the new sand easier to configure version of xorg.
Meh, for me Dapper wasn't that stable at all, and the LiveCD install option was horrible. Edgy fixed a lot of this.
I'm actually rather annoyed by the fact that Gutsy + 1 will be LTS, since that means no KDE 4 by default, and the last LTS didn't leave me with the confidence that that's worth it.
As for Gutsy itself, I guess (and hope) it will fix some issues, but I'm not overly thrilled by the new features.

---

### Post by aysiu on 2007-08-09
> **Old Pink said:**
> [CENTER][LIST]
[*]A pretty big leap, there are a few new features I like and a few problems that could be solved
[*]**--- I'm Here ---**
[*] I don't think it'll offer any improvement on my situation at all.[/LIST][LEFT]I don't think it'll solve anything, as such, there's nothing to be solved on my current two systems. (Although Direct Rendering on my old ATI card would be nice, but it still works perfectly as is.)

But I'm looking forward to some of the features, and the general upgrade. :)
[/LEFT]
[/CENTER]
I'm with Old Pink here. I think you have a couple of poll options missing. It's either a pretty big leap or no improvement at all.

How about a small leap?

Everything basic is working for me right now, but I'd love to have an easy way to enable dual monitor support. Not a big leap, but still a leap.

---

### Post by PurposeOfReason on 2007-08-09
It'll help a small bit but I'm not super excited for it. I mean, the bulletproof X is cool and all but I'm now to the point where I never have to touch my xorg.conf file.

---

### Post by misfitpierce on 2007-08-09
Im sure itll improve a few things that make it run even smoother... New kernel shows promise and I just love newly released software :)

---

### Post by DoctorMO on 2007-08-09
> [QUOTE]If I can sync my Pocket PC with Kontact on Gutsy.. Oooh...
that's your wish, right, not what's actually coming? [/QUOTE]

I have no idea where you guys have been:

OpenSync 0.22 -> [http://www.opensync.org/wiki/download](http://www.opensync.org/wiki/download)
For Blackberries get barry and opensync-barry-sync,(I use this, still a few bugs)
For PocketPC use SynCE Plugin
For Palms use Palm Plugin

There's a nice Ubuntu feisty repository here:

[http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/)

Obviously it's all beta and even if it was included in gutsy by default your still going to have bugs; Although it's showing really great promise and in a year or two linux will have the best syncing of any platform (hell google to kde to blackberry rocks!).

---

### Post by jrusso2 on 2007-08-09
I don't know I am still using edgy cause feisty was so buggy.  I am hoping for a less buggy release this time

---

### Post by vexorian on 2007-08-10
tracker seems promising

---

### Post by regomodo on 2007-08-11
i have no opinion as i don't know what is supposed to be new/revolutionary in Gutsy other than better wifi support, i think. Personally i'm more interested in KDE4 in Ubuntu even though i'm not to big a KDE fan.

---

### Post by rax_m on 2007-08-11
I'm hoping that Gutsy sorts out the sound, suspend, hibernate issues on my Toshiba laptop. 

Except for those.. Feisty is great (works better for me then Edgy did).

---

