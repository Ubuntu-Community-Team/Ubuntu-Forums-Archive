---
title: "Hardy bad from the start..."
date: 2008-05-07
forum: Testimonials &amp; Experiences
---

### Post by ftaylor on 2008-05-07
I've had nothing but bad experiences from Hardy.  What's the deal?  Is everyone having problems or is it just me?

Current list of problems:
[LIST]
[*]FGLRX driver now broken, worked fine in Gutsy.
[*]Aptitude seems to be totally broken - terminal just hangs on any command with apt (eg sudo apt-get update).
[*]Pidgin messenger keeps randomly hanging - goes black and white, freezes, then comes back in.
[*]I now have 4 ubuntu listings in grub - because of the kernel update.
[*]Sound is not shared properly - if I am listening to music in Rhthymbox (or even have it open) nothing else can output sound.
[*]Openoffice takes ages to even think about starting. I have done all the optimization tricks, this only happens the first time I try to open it after login. (this is probably OO 2.4 rather than hardy)
[*]The locations still randomly crashes on me (maybe I haven't been able to update to the latest version?)
[*]Slower to install?
[*]Mounted volumes no longer remain mounted on restart of X.
[/LIST]

Improvements from Hardy:

[LIST]
[*]I see the Ubuntu splash loading screen now!
[/LIST]

What I really want is help for these issues, because I'm thinking about going back to Gutsy just now.

Cheers

Ftaylor

---

### Post by Bakon Jarser on 2008-05-07
From your grub entries it sounds like you did an upgrade.  Since you would have to do a clean install to go back to gutsy maybe you should try a clean install of hardy first.  I haven't experienced any of the problems you've encountered.  Open Office loads at a decent speed, apt works perfectly, and I only have two ubuntu entries in my grub menu (normal and recovery mode).

---

### Post by msutton86 on 2008-05-07
I upgraded from 7.10 and I noticed some craziness too.  I said F that tried to reinstall and it's worked great.  The only issue i've noticed is during shutdown sometimes.  After running updates as of today it's been smooth, and stable as can be.  Try it out.  You may be surprised!

---

### Post by Kingsley on 2008-05-07
The only major problem I've experienced with Hardy is my touchpad being turned on after every reboot.

---

### Post by swoll1980 on 2008-05-07
try a ```
sudo dpkg-reconfigure -a
``` to fix your apt problem

---

### Post by agim on 2008-05-07
Sorry you are having a bad experience. You asked if it was everyone... its not me. My only problems have been the occasional firefox/flash issue.

---

### Post by madjr on 2008-05-08
clean install is the best.

if you upgraded just because you didn't want to burn a CD then you're in luck.

just use **unetbootin** to install Ubuntu without the need to burn it.

---

### Post by p_quarles on 2008-05-08
Moved to Testimonials & Experiences.

---

### Post by wolfen69 on 2008-05-08
> **ftaylor said:**
> I've had nothing but bad experiences from Hardy.  What's the deal?  Is everyone having problems or is it just me?




sit happens. not every distro will work for every pc. hardy happens to run near perfect for me. ive even installed it on 3 windows customers pcs. they love it once they get used to it.

---

### Post by miciurin on 2008-05-08
It seems you have lots of problems. In my case it works flawlessly. Rock solid.

Regarding your fglrx issue. If you installed the ati driver with envy in Gutsy you should remove it before upgrading to hardy and then reinstall.

---

### Post by wolfen69 on 2008-05-08
better yet just clean install.

---

### Post by Tatty on 2008-05-08
Unfortunately there are always issues when it comes to new versions, and there are always some occasions where it really falls over.  But most of the time things go fairly smoothly.

Starting with my upgrade to hardy Ive decided to keep a separate /home and always install new versions to a separate partition, it certainly saved me when i ran into a couple of initial problems in hardy.  While those problems were ongoing I was able to reboot into gutsy to get things done.

As miciurin said, if you installed your fglrx driver via envy or any method other than via the repos (or restricted drivers manager) then you have to disable it before upgrading then re-install it after the upgrade - Thats why its always best to install from the repos before trying external scripts/manual installation, it keeps everything updated for you ;)

Although i am lead to believe that now envy is in the repos in hardy, that it will keep any drivers up to date as you upgrade.

Sound issues are due to the new pulseaudio sound server, have a look around to see if you can find some workarounds for your rythmbox problem.

I am just wondering, how much space do you have on your hardy root partition?  The slowness problems you are reporting sound slightly as if you are running out of space and files are getting fragmented - as you say that OO opens fine the second time you load it - which is when it will be cached into the ram.

---

