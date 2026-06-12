---
title: "Issues I got so far in Trusty"
date: 2013-11-13
forum: Ubuntu Development Version
---

### Post by pnarciso on 2013-11-13
Sporadic disappearing mouse cursor.

Ubuntu not logging in automatically, it boots to unity greeter, and I have to manually login. This also happens sporadically.

Plugin indicators crash, or won't show up (gear icon, time).

Sometimes, when login out and login in, I get on my upper left corner some error messages related to Xorg.

---

### Post by grahammechanical on 2013-11-13
Welcome to testing Ubuntu+1.

Have you not yet had a complete OS freeze? I have had it twice in recent days. Once when I was using Ubuntu Web Browser and once when I was using Chromium. Only the mouse was active. I have System Load Indicator running to watch if CPU or RAM is being maxed out but as everything has frozen they give no indication as to what is causing it. The top utility also freezes.

I have also had the missing power/cog icon and the missing mouse cursor but I found I could still click with the mouse although I could not see exactly where the cursor was. I have not had the other issues that you have had. And so we live.

Regards.

---

### Post by ventrical on 2013-11-13
I do know that one one the 'alerts'  is apport-gtk so have fun trying to send a bug report :)
 lol

---

### Post by OrangeCrate on 2013-11-13
> **pnarciso said:**
> Sporadic disappearing mouse cursor.

Ubuntu not logging in automatically, it boots to unity greeter, and I have to manually login. This also happens sporadically.

Plugin indicators crash, or won't show up (gear icon, time).

Sometimes, when login out and login in, I get on my upper left corner some error messages related to Xorg.

It's pre-alpha, don't be too surprised, if nothing works.

:)

---

### Post by pnarciso on 2013-11-13
What worries me is that all of this issues are present in 13.10 final :)

---

### Post by rrnbtter on 2013-11-13
Greetings,

> **pnarciso said:**
> Sporadic disappearing mouse cursor. Ubuntu not logging in automatically, it boots to unity greeter, and I have to manually login. This also happens sporadically. Plugin indicators crash, or won't show up (gear icon, time). Sometimes, when login out and login in, I get on my upper left corner some error messages related to Xorg.

These problems are transitional, the result of conflicting dependencies in a development version. Most should be corrected before 16.04 or 17.10. What is needed at this point is patience and reporting.

[LIST]
[*] 	 		 			:smile: 		

 	
[/LIST]

---

### Post by OrangeCrate on 2013-11-13
> **pnarciso said:**
> What worries me is that all of this issues are present in 13.10 final :)

Tis true, I suppose. Since this is an LTS version, the devs will pull from Debian testing, instead of Sid. That should make things a lot more stable right from the gitgo, but, as I teased you in my previous post, it's still pretty early to expect that everything (or maybe nothing) will work all of the time.

With the shortened nine month life cycle of the interim releases now (between the LTS versions), personally, I don't expect a lot of release specific bugs to be fixed. It seems that most of the energy is spent putting out a good LTS release (and it should be). The interim releases all point to the next LTS.

I have noticed in Xubuntu, that several small bugs have already been fixed in 14.04, that nagged at me in 13.10. Time will tell, but, I think this is going to be a great release.

I always use the dev releases, and I'll move on to the next one as soon as I can. I like playing with them, bugs or no. In fact, it's been so long since I've actually used a "stable" release, I'm not even sure how well they work any more.

My suggestion to all is...

If you like working with the dev releases, try not to sweat the small stuff. Just relax, and let it unfold in front of you. It's all good.

---

### Post by kevpan8152 on 2013-11-13
> **rrnbtter said:**
> Greetings,



These problems are transitional, the result of conflicting dependencies in a development version. Most should be corrected before 16.04 or 17.10. What is needed at this point is patience and reporting.

[LIST]
[*]                           :smile: 
[/LIST]


i believe you mean 14.04 LTS! After all 16.04 is April of 2016 AND 17.10 is October of 2017! Just FYI! :-)

---

### Post by kevpan8152 on 2013-11-13
Weird, so far the only problems that I have had in 14.04 is 1 instance of Broken Packages on Running Dist-Upgrade and 1 Instance of my WIFI NOT Working just now (The second problem was most likely due to installing Unity 8 earlier today).

---

### Post by rrnbtter on 2013-11-13
Greetings,

> **kevpan8152 said:**
> i believe you mean 14.04 LTS! After all 16.04 is April of 2016 AND 17.10 is October of 2017! Just FYI! :-)

Nope I mean what I said. I started with Karmic Koala and vaguely remember trying to get a windows driver working with ndiswrapper, everything else is long forgotten.  I have been running dev versions to this day. I expect that by 2016 or 2017 the OP will have forgotten what today's problems are and shortly thereafter reminiscing about how wonderful the Unity desktop was and how crappy the new offering is. FYI 

[LIST]
[*] 	 		 			:popcorn: 		
 	
[/LIST]

---

### Post by rrnbtter on 2013-11-13
Greetings,
Well! regarding OP's Log-in issue, I just got a unity-greeter update so perhaps that part is fixed..or not.

---

### Post by rrnbtter on 2013-11-13
Greetings,
Well the greeter still needs more work, more saucy than trusty.

---

### Post by kansasnoob on 2013-11-13
> **pnarciso said:**
> Sporadic disappearing mouse cursor.

Ubuntu not logging in automatically, it boots to unity greeter, and I have to manually login. This also happens sporadically.

Plugin indicators crash, or won't show up (gear icon, time).

Sometimes, when login out and login in, I get on my upper left corner some error messages related to Xorg.

I reported that login bug for Saucy:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1245915](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1245915)

I've added some Trusty info to the bug report.

But I see that lightdm's files have changed so I probably need to try a fresh install when the time feels right ;)

---

### Post by kevpan8152 on 2013-11-14
> **rrnbtter said:**
> Greetings,
Well! regarding OP's Log-in issue, I just got a unity-greeter update so perhaps that part is fixed..or not.

The reason why I have NOT had the Login Issue is most likely due to the fact that I always use Prompt for Password with Home Folder Encryption by the way just in case anyone is wondering why I have NOT had that problem.

---

### Post by kevpan8152 on 2013-11-14
> **kevpan8152 said:**
> The reason why I have NOT had the Login Issue is most likely due to the fact that I always use Prompt for Password with Home Folder Encryption by the way just in case anyone is wondering why I have NOT had that problem.

Whenever I use Windows 8.1 it Automaticly Requires a Password so I do the same with Ubuntu.

---

### Post by Chanath on 2013-11-14
> **OrangeCrate said:**
> I always use the dev releases, and I'll move on to the next one as soon as I can. I like playing with them, bugs or no. In fact, it's been so long since I've actually used a "stable" release, I'm not even sure how they work any more. 

Me too!:D
I don't have any hickups to report yet. I didn't have any in the 13.10 testing too, but got something in the final release. The, I moved to TT. Wiating to see what they going to do with Ubuntu Browser and Unity8. :D

---

### Post by rrnbtter on 2013-11-14
Greetings,

> **kevpan8152 said:**
> The reason why I have NOT had the Login Issue is most likely due to the fact that I always use Prompt for Password with Home Folder Encryption by the way just in case anyone is wondering why I have NOT had that problem.

I login with a PW also, hence I also don't have the problem. However there is a detectable double login page with a quick flash in between the two pages. I expect that this error is where the problem occurs. The PW request stops the script.

---

### Post by OrangeCrate on 2013-11-14
> **Chanath said:**
> Me too!:D
I don't have any hickups to report yet. I didn't have any in the 13.10 testing too, but got something in the final release. The, I moved to TT. Wiating to see what they going to do with Ubuntu Browser and Unity8. :D

Xubuntu has been pretty solid too.

To be clear, I need to add a word to my comment on using dev releases, and I'll edit my original post...

> I always use the dev releases, and I'll move on to the next one as soon as I can. I like playing with them, bugs or no. In fact, it's been so long since I've actually used a "stable" release, I'm not even sure how **well** they work any more.

I certainly know how they work, just not how bug free they are when they are released.

---

### Post by Elfy on 2013-11-14
> **OrangeCrate said:**
> Xubuntu has been pretty solid too....

Much the same here, though this morning I got a gpu lockup. Non responsive - then switches to a tty - with gpu lockup errors, then complete garbage, then reboot at wall ... nouveau

Seems I can't get apport to play ball yet, though that might be it's not switched on properly.

Need to install nvidia see if that deals with the gpu issue.

The gtk3 indicators appear to have stabilised in trusty, in saucy at times panle needed a restart.

---

### Post by OrangeCrate on 2013-11-14
> **Elfy said:**
> Much the same here, though this morning I got a gpu lockup. Non responsive - then switches to a tty - with gpu lockup errors, then complete garbage, then reboot at wall ... nouveau

Seems I can't get apport to play ball yet, though that might be it's not switched on properly.

Need to install nvidia see if that deals with the gpu issue.

The gtk3 indicators appear to have stabilised in trusty, in saucy at times panle needed a restart.

I can't help with any Nvidia testing. My test box is a T400 with an onboard Intel chip set.

I reloaded a couple of days ago, and haven't gotten around to add the GTK 3 indicators again, but, they were working fine up till then (as I indicated with a fairly recent post and screenshot).

Haven't had anything to report lately, but, when I do, I'll keep an eye on apport as a follow-up to your comment, though I'm pretty careful when and if I use apport. If I know that there have been a lot of comments, I generally don't pile on.

> During the development release we already collect thousands of crash reports, much more than we can ever fix.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

I have been occasionally getting some odd looking windows borders. This started back with 13.10. I have tried to take a screenshot to post and report, but, every time I open the screenshot program, it clears up the borders on the window that is affected.

---

### Post by NM5TF on 2013-11-14
my biggest issue is with missing decoders in Audacious for playing .wav
files....it used to work until latest apt-get update/upgrade....now Audacious
is unusable....running linux kernel 3.12.0-1

have already tried remove & re-install Audacious with no luck...

VLC still works correctly so pulse audio working correctly....

see occasional screen tearing/gpu lockup even after installing
nVidia-current....

---

### Post by mc4man on 2013-11-14
> **pnarciso said:**
> Sporadic disappearing mouse cursor.

Ubuntu not logging in automatically, it boots to unity greeter, and I have to manually login. This also happens sporadically.

Plugin indicators crash, or won't show up (gear icon, time).
.

The invisible cursor bug from 13.10 remains active in 14.04 though I didn't  see it as often, now never as i've disabled the g-s-d cursor plugin till it gets fixed, if ever (no real activity on bug report

The missing session & datetime indicators was fixed though ocaasionally am missing datetime, if that continues will need a new report
> **NM5TF said:**
> my biggest issue is with missing decoders in Audacious for playing .wav
files....it used to work until latest apt-get update/upgrade....now Audacious
is unusable....running linux kernel 3.12.0-1

have already tried remove & re-install Audacious with no luck...

VLC still works correctly so pulse audio working correctly....

see occasional screen tearing/gpu lockup even after installing
nVidia-current....

There should be new builds for some media players now that libav9 is in trusty (still in -proposed I believe
Here have no issue with audacious though am using Aud  3.4.2 based on libav9, though never have seen that any add. 'decoder' is needed for .wav

---

### Post by NM5TF on 2013-11-14
this is REALLY bizarre.....

Audacious is now working without any input or intervention on my part.....

FYI....this is Audacious v 3.4.1-1

Hard to believe something took over 4 hrs to affect Audacious since I
re-installed this morning.....very strange...but happy with result, at least
until next kernel upgrade...

Tommy

---

### Post by rrnbtter on 2013-11-14
Greetings,

> **NM5TF said:**
> this is REALLY bizarre.....
Audacious is now working without any input or intervention on my part.....
Hard to believe something took over 4 hrs to affect Audacious since I
re-installed this morning.....very strange...but happy with result, at least
until next kernel upgrade...
Tommy

Wednesday of last week I was trying to convert a video with Devede and was getting a missing decoder error message even though I wasn't working with an encrypted video.  I had to use DVDFab in Windows. Friday I got a Libav update and it has worked fine since. I suspect that same decoder was your problem given that Linux programs use much the same libraries. It's a fact though that VLC has its own decoders.

---

### Post by kevpan8152 on 2013-11-15
Keep in mind that this is an LTS (Long Term Support) Release so some changes to the OS are Deferred until 14.10. In reality, a NON-LTS Pre-Alpha is usually more Troublesome than a LTS Pre-Alpha.

---

### Post by kevpan8152 on 2013-11-15
> **NM5TF said:**
> my biggest issue is with missing decoders in Audacious for playing .wav
files....it used to work until latest apt-get update/upgrade....now Audacious
is unusable....running linux kernel 3.12.0-1

have already tried remove & re-install Audacious with no luck...

VLC still works correctly so pulse audio working correctly....

see occasional screen tearing/gpu lockup even after installing
nVidia-current....


Have you tried the Trusty PPA Mainline Kernel at [http://kernel.Ubuntu.com/kernel-ppa/mainline/](http://kernel.Ubuntu.com/kernel-ppa/mainline/) ?

To install it, download the 3 files for your system, put them in a Sub-Folder called kernel inside your home folder, open up Terminal, do a CD kernel, finally do a sudo dpkg -i *

---

