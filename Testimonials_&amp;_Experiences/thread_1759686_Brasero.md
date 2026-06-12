---
title: "Brasero"
date: 2011-05-16
forum: Testimonials &amp; Experiences
---

### Post by shashanksingh on 2011-05-16
My experiences with brasero have been very bad. Almost wasted 3 DVD's while trying to burn them.

Sometimes, it just doesn't start burning, showing estimated time in thousands of hours.

Feels like it does only the checksum thing correct, cant trust it with anything after that.

Have never faced a problem with any other burning sofware, I have tried windows default image burning sofware and nero.

Apparently I have to log into my windows if I want to burn DVD's.

Any other trustworthy options??
I've heard of K3B

---

### Post by robert shearer on 2011-05-16
You're not alone.
Brasero must be the most unreliable, inconsistent app I have ever had the misfortune of using.

Why it continues to be the default burning app is beyond me.

K3b is good but installing it brings in a **whole lot** of KDE libraries and associated clutter.

Try Xfburn, this performs faultlessly for me and seems to have matured to the point that options and functionality are almost on par with the more recognised Gnome/KDE siblings.

---

### Post by arunb on 2011-05-16
on the other hand, Brasero works perfectly for me.

---

### Post by MartyBuntu on 2011-05-16
The only thing Brasero has ever done well for me is burn ISO's.

For everything else, I use K3B.

---

### Post by Megaptera on 2011-05-16
> **arunb said:**
> on the other hand, Brasero works perfectly for me.

+ 1   

 I try loads of live CDs/DVDs and have never had any problems burning the iso with Brasero.

---

### Post by Ad@m on 2011-05-16
I am another Brasero works great for me.

Out of curiosity, what CD/DVD drive do you have?

---

### Post by 3Miro on 2011-05-16
You guys can try "xfburn". It has fewer features than Brasero, but it I have never had issues with it in terms of stability.

---

### Post by stalkingwolf on 2011-05-16
I have never that i can remember used brasero.  I use K3B it is one of the first things i install.

---

### Post by linux phreak on 2011-05-16
I use gnomebaker.I find it better than brasero.

---

### Post by shashanksingh on 2011-05-16
> **Ad@m said:**
> I am another Brasero works great for me.

Out of curiosity, what CD/DVD drive do you have?

LG piece
*-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GSA-H20N
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc

---

### Post by el_koraco on 2011-05-16
k3b is literally the first thing I install.

---

### Post by FootySr on 2011-05-16
> **shashanksingh said:**
> My experiences with brasero have been very bad.

Are you sure you don't want to toss a Unity stinks line in there somewhere? Seems to be the trend! :)

Thanks for the new topic. :D

---

### Post by IWantFroyo on 2011-05-16
> **MartyBuntu said:**
> The only thing Brasero has ever done well for me is burn ISO's.

For everything else, I use K3B.

Yep. I only use Brasero for .iso's.
For everything else, I either use Google Docs or a USB stick.

---

### Post by shashanksingh on 2011-05-16
> **FootySr said:**
> Are you sure you don't want to toss a Unity stinks line in there somewhere? Seems to be the trend! :)

Thanks for the new topic. :D

Ive already done that somewhere else.
;)

I would rather start something related to banshee rather, even banshee isn't the most consistent of players..

---

### Post by shashanksingh on 2011-05-18
should I report this bug to launchpad??
I mean can anyone tell me if its relevant enough??

---

### Post by stchman on 2011-05-18
I've never had a moments problem with Brasero.  It's a simple app that gets the job done.

---

### Post by Nightstrike2009 on 2011-05-18
>  Originally Posted by shashanksingh
My experiences with brasero have been very bad.

First thing I do is install K3b and remove brasero, It also was an epic fail with my drive. Unity is also an Epic Fail FootySr its just some havent realised that yet! ;-)

---

### Post by shashanksingh on 2011-05-19
> **Nightstrike2009 said:**
> First thing I do is install K3b and remove brasero, It also was an epic fail with my drive. Unity is also an Epic Fail FootySr its just some havent realised that yet! ;-)

True, Im pretty sure brasero will screw something up in my drive.
As far as unity goes, didn't like it, didn't use it ;)

---

### Post by darkstaar on 2011-05-19
> **shashanksingh said:**
> Any other trustworthy options??
I've heard of K3B

I had a similar issue recently with Brasero. Cured it by simply removing the application and reinstalling it.


> **FootySr said:**
> Are you sure you don't want to toss a Unity stinks line in there somewhere?

Thanks for the reminder but Unity just has a bad odor. It's Gnome Shell that stinks [grin].

---

### Post by johnnybgoode83 on 2011-05-19
I have had issues with Brasero so I eventually caved and installed K3B which was not ideal as I didn't want the KDE libraries that come with it.  In my opinion gnome native CD/DVD burners are lacking quite badly.

---

### Post by FootySr on 2011-05-19
> **Nightstrike2009 said:**
> Unity is also an Epic Fail FootySr its just some havent realised that yet! ;-)
lol... Poor Unity taking a beating even in the non-Unity threads! :)

---

### Post by Tamlynmac on 2011-05-19
I believe Brasero started experiencing issues in 8.04. If memory serves me, there were numerous threads associated with the issue posted on the forums. At which time (upon the advice of other forum members) I switched to k3b. Since that time I never again had any issues with burning.

As others in this thread have indicated, it's one of the first apps that I install and when helping new users I always recommend it.

---

### Post by recluce on 2011-05-19
Both Brasero and K3B work fine for me, as long as I remove the underlying train-wrecks called "wodim" and "genisoimage" and replace with cdrecord and mkisofs from the cdrtools package.

PPA to be found here:

[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

cdrtools has been kicked by Debian for political reasons, the "new" packages (genisoimage, wodim) are outdated, buggy junk without proper maintenance. If you care for the whole, grisly story, google will turn up more than you care for.

That being said, I believe that K3B is a much better burn-suite than brasero and would always install it, even on a GNOME system.

---

### Post by 3rdalbum on 2011-05-20
I haven't experienced any problems with Brasero lately, although in the past it did seem to have highly-visible bugs. I wouldn't be surprised if it had less-visible bugs still hanging around.

K3B has always been fairly solid and dependable for me, so that's probably the best option to try next.

---

### Post by Arthur_D on 2011-05-21
I burn a lot of dual-layer DVD's for backup purposes (yes, a court ruling in Norway ruled it legal to backup your own DVD's), and AFAIK Brasero doesn't have the ability to burn DVD-DL discs. And even if it did, I still trust K3b a lot more than Brasero (had some crashes with Brasero in the past). Disc space is cheap nowadays, so some KDE libs doesn't do much of a difference, IMHO.

So if you want a feature-rich, reliable burning application, use K3b.
If you only burn ISO files, you might as well just use Brasero.

---

### Post by cgroza on 2011-05-21
I never had a coaster with Brasero. It works fine.

---

### Post by marl30 on 2011-05-21
I never fancied Brasero. In Gnome I always made sure I had K3B and Gnomebaker installed. They are both highly reliable. K3B is the best. Gnomebaker is a bit slow but is sure. I only use K3B these days since switching to KDE.

---

