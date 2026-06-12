---
title: "Am I the only one whose flash crashes all the time?"
date: 2012-05-17
forum: The Cafe
---

### Post by Bazon on 2012-05-17
Is it only me, or has your flash also became significant more unstable?
I'm happy I always dualboot with a recent and a previous ubuntu version, so I got a old libflashplayer.so (Version 11,1,102,63) which really runs better.
What has happen?

---

### Post by IWantFroyo on 2012-05-17
I don't have this issue. It has gotten a bit more laggy for me, however.

---

### Post by cariboo on 2012-05-17
I'm running Quantal here, and don't have any flash problems.

---

### Post by Erik1984 on 2012-05-17
There seems to be an increase in reported Flash problems (both here and on my local forums) but I'm not sure what the cause is. I had the smurfs problem (blue people in videos :P) but that could be fixed by disabling hw acceleration (I doubt that even worked btw).  However other users can't even get to that option to disable it. Maybe it's the combination of (particular version of) flash with (particular version of drivers for) video card that causes trouble.

---

### Post by MisterGaribaldi on 2012-05-17
> **Bazon said:**
> **Am I the only one whos flashs crashes all the time?**

Yep, Bazon, you're the only one for whom flashs crashes.

Hey, that rhymes! :P

For the rest of us, flashs is perfectly stable, because Adobes writes excellent software.

---

### Post by rai4shu2 on 2012-05-17
Flash never crashes on me (mainly because I use Gnash instead).

---

### Post by wolfen69 on 2012-05-18
It's been perfect for me for years. No complaints.
> **rai4shu2 said:**
> Flash never crashes on me (mainly because I use Gnash instead).
Yeah, gnash is the way to go. :confused:

---

### Post by Bandit on 2012-05-18
No flash issues here either..

---

### Post by jmore9 on 2012-05-18
Works fine here in ubuntu but when running suse 12.1 kde it crashes every other time it is opened.

---

### Post by wolfen69 on 2012-05-18
> **jmore9 said:**
> Works fine here in ubuntu but when running suse 12.1 kde it crashes every other time it is opened.

Well it *is* opensuse. ;)
> **Bandit said:**
> No flash issues here either..
Funny how our experiences seem similar.

---

### Post by na5h on 2012-05-18
No, you are not the only one...many users have problems with flash these days. Google Chrome is probably the best option if you want your flash to be as crash-free as possible (if I'm not mistaking, Chrome will be the only browser to receive flash-updates on Linux in the future). As for youtube videos, the HTML5-option for viewing videos is quite nice!

---

### Post by carl4926 on 2012-05-18
From what I have read the bug in flash is affecting folks with nvidia cards.
It does me
But my Intel laptops are fine

Disabling HW Accel does seem to do the trick

Gnash is a wet paper bag, but I'd love to see the end of adobe flash.

---

### Post by wolfen69 on 2012-05-18
> **carl4926 said:**
> 

Gnash is a wet paper bag,

Funny, someone was bragging about using gnash to avoid problems by adobe. BUT, they didn't say that gnash completely sucks as an alternative. If you don't have plans to go to youtube or *most* websites, then by all means, use gnash. Have fun.

---

### Post by ubuntu27 on 2012-05-18
I don't have any problems with Adobe Flash 11.2.202.235ubuntu0.12.04.1 in Ubuntu 12.04 64 bit with Intel Integrated Graphics

On the other hand, **Flash keeps crashing frequently** on my sibling's laptop. That laptop has an nvidia card and it is running Ubuntu 11.04 (Natty). Flash is version 11.2.202.235 which was installed using Flash-Aid.

---

### Post by wolfen69 on 2012-05-18
> **ubuntu27 said:**
> **Flash keeps crashing frequently** on my sibling's laptop. That laptop has an nvidia card and it is running Ubuntu 11.04 (Natty). Flash is version 11.2.202.235 which was installed using Flash-Aid.

You're not a noob, figure it out. If not, ask for help. Most people here will be more than helpful.

---

### Post by Bazon on 2012-05-18
Great, I'm not the only on!

So what about solutions?

Against smurfs on youtube, I got this:
```
sudo mkdir /etc/adobe
sudo gedit /etc/adobe/mms.cfg
```

and add there these lines:

```
EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true
```

I can't use Gnash, cause some essential (flash based...) sites won't run on Gnash.

As even my old version isn't reliable stable, I ask:
Are there other solutions?

---

### Post by rc45164 on 2012-05-18
Had and did all the fixes noted in the forums... nothing help until I switched to the firefox **64bit** browser. ( Running ubuntu 12.04 64 bit and Nivdia ). 
Hope that helps...

---

### Post by Bazon on 2012-05-18
don't i get the 64bit version automatically vie the repos?
if not: where can i get it?
thanks!

---

### Post by rai4shu2 on 2012-05-18
> **wolfen69 said:**
> Funny, someone was bragging about using gnash to avoid problems by adobe. BUT, they didn't say that gnash completely sucks as an alternative. If you don't have plans to go to youtube or *most* websites, then by all means, use gnash. Have fun.

Gnash does suck, but not as much as Adobe. And I have absolutely no problem with Youtube or most websites. (It's just stuff like speedtest.net where I run into problems.)

---

### Post by Bazon on 2012-05-19
> **Bazon said:**
> Great, I'm not the only on!

So what about solutions?

Against smurfs on youtube, I got this:
```
sudo mkdir /etc/adobe
sudo gedit /etc/adobe/mms.cfg
```

and add there these lines:

```
EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true
```

I can't use Gnash, cause some essential (flash based...) sites won't run on Gnash.

As even my old version isn't reliable stable, I ask:
Are there other solutions?

I have to add:
```
EnableLinuxHWVideoDecode=1
```
leads to unskipable Youtube, but only ```
OverrideGPUValidation=true
```
removes Smurfs (blue skin color), too.

---

### Post by VinDSL on 2012-05-19
> **Bazon said:**
> Is it only me, or has your flash also became significant more unstable?
Flash has become wonky for me, recently, on both Ubuntu 12.10 and Peppermint OS Two (which are substantially different, albeit Ubu-based, distros)!

When it crashes, the error dialog indicates that Flash is running out of memory, even though monitoring apps indicate otherwise, e.g. I have plenty of free mem available.

Put another way, Flash *thinks* it is running out of memory...

---

### Post by Bazon on 2012-05-19
Hm.
I seem to have good news.
Since I stripped my /etc/adobe/mms.cfg from 
```
EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true
```
to 
```
OverrideGPUValidation=true
```
I had no flash-crashs anymore! So the smurf remove-trick with both lines seems to be false, just OverrideGPUValidation=true is enough! :-)

So spread the word if you hear the wrong two lines solution for the blue skin problem...

---

### Post by Bazon on 2012-05-19
And here is the reason for my problems:
[http://askubuntu.com/questions/117127/flash-video-appears-blue/](http://askubuntu.com/questions/117127/flash-video-appears-blue/)

I tried to edit the answer, let's hope it passes the review.

---

### Post by backman on 2012-05-27
Bazon I still need both lines for no smurf effect. When I have only
```
OverrideGPUValidation=true
``` the video has the blue effect. Do you have libvdpau1 installed? Have you done some other steps before this ? Thanks for any help

---

### Post by backman on 2012-06-07
Solved by deleting mms.cfg and using ```
sudo add-apt-repository ppa:tikhonov/misc
sudo apt-get update
sudo apt-get install libvdpau1  
```from [http://askubuntu.com/a/131040](http://askubuntu.com/a/131040)

Just if the solution with mms.cfg doesn't work for you.

---

### Post by Hari5g900 on 2012-06-07
Yeah then I am with you Bazon because mine also crashes. BUT NOT ALWAYS!!!!!!!!!

---

### Post by HansKisaragi on 2012-06-07
Flash have crashed for me but only when using chrome on windows box. never on a Linux box.

---

