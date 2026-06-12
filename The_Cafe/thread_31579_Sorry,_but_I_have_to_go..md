---
title: "Sorry, but I have to go."
date: 2005-05-03
forum: The Cafe
---

### Post by KezzerDrix on 2005-05-03
Hello,

I recently switched from Gentoo to Ubuntu.  I was very impressed and thought I had found my new home.  The problem is that I like to play games, I know, I Know, I am thirty and I like ut2004, so what?  

With Ubuntu, I discovered some sound issues.  I asked in the forum for help and was told to open a console and type "sudo killall -9 esd" this fixed the problem but I generally forgot to do it.  This would cause either no sound or a system lock up.  You, might say this is my own fault, but I think that I shouldn't be forced to remember this every time I want to fire up a game of Unreal.  

Also, I never could get my tv card to work and even though I asked several times I never recieved any help.

So, I have moved on to Mepis, and amazingly everything works.  I didn't have to do anything but download some codecs and the accelerated nvidia drivers.  WOW!

However, Ubuntu has some features that I will miss.  Primarly the ability to update without reinstalling, the 6 month upgrade intervals, and the incremental security updates.  Perhaps Mepis will intergrate this in future releases. 

Perhaps, I will try Ubuntu again after the next release.

Anyway the reason I am posting is to state obivious dissapointment, to state that I gave Ubuntu an honest try, to show one users problems that made him move on, and to say thanks to those that did answer my posts, as well as to the developers, I think Ubuntu is world class, and will definitely soon be one of THE best Linux distributions.

Thanks
Kezz

---

### Post by cdhotfire on 2005-05-03
hey well thats fine man, as we all know ubuntu is not for everyone. As they say one persons trash is anothers persons treasure.  But good to see you found another that will fit your needs, take care.:smile:

---

### Post by jdong on 2005-05-03
Good luck wherever your computing takes you.


P.S. You know that you can turn off "esd" permanently by unchecking Sound Server Startup in GNOME's Sound preferences, right? ;)

---

### Post by KezzerDrix on 2005-05-03
Would've been nice to be told that a FEW WEEKS AGO! ARRRRRGHHHHH  Seriously, I asked for help and the above solution in post #1 was the one I was given.  I had Ubuntu up and running with everything I wanted, before installing ut2004.  I was quite irratated that it wouldn't work right.  

HMM, if I turned it off permantly what other functions would I have lost?

Since your here reading this HOW would I get my avertv studio tv card working?

I want one thing understood, I am in NO way bashing Ubuntu.  In fact I was figuring that in six months I would try it again and see if the problem was fixed.  I mean really, Nobody gives you everything Ubuntu does for FREE.

I just couldn't get these problems fixed and couldn't find help.  So I had to move on.

Kezz

---

### Post by jdong on 2005-05-03
Sorry, I didn't see your thread from a while back.

If you disable ESD permanently, the only functionality you loose are the cute little GNOME sounds when you log on and off ;)

At least Ubuntu is much faster to install than Gentoo ;) ;)


As far as your avertv card, have you googled? I found [http://www.linuxtv.org/v4lwiki/index.php/Saa7134_devices](http://www.linuxtv.org/v4lwiki/index.php/Saa7134_devices) , which may be related. I personally don't have a tuner card, so I don't know the specifics.

---

### Post by poofyhairguy on 2005-05-03
[QUOTE=KezzerDrix]
Since your here reading this HOW would I get my avertv studio tv card working?
[/QUOTE]

Did you try the program- XawTV? I think its in synaptic.

But whatever. MEPIS is excellent. If I was a KDE guy, I would really consider it...

---

### Post by Xerampelinae on 2005-05-03
The best solution I've found is to enable dmix in alsa, as shown in the link below.  This allows you to use esd along with other programs that use sound.  It maybe the ut2004 uses oss, but that's okay too since this link tells you to let esd quit after 2 seconds of it not being in use (and then start automatically if needed).

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)


As for your TV card, I would have suspected it would be supported out of the box.  Mine was, and I only needed to do "apt-get install tvtime" to allow me to watch stuff.

---

### Post by KezzerDrix on 2005-05-03
Yea, I tried xwantv, infact its the one I am currently using.  

DO NOT get me started on GENTOO, I will BASH them  :grin:   :grin: 

I tried installing that for 2 weeks got it up and running and destroyed it everytime I tried to update it.  You know after spending that much time learning to install it, I was vested in it.  I tried 3 or 4 times, install, compile, compile some more, compile a lot more, reboot, crash.  Reinstall, compile, compile some more, compile a lot more, reboot, crash. Reinstall --infinite loop--

Kezz

---

### Post by TravisNewman on 2005-05-03
You can also tell gnome to just use alsa and not use esd, and you'll still get your system sounds :) I did that just so that ESD wouldn't be one more unneeded process.

---

### Post by jdong on 2005-05-03
Ok:

1. Let's not get into a distro war here. That's not the point of this thread.

2. Panickedthumb: explain how to get GNOME to use direct alsa output.

---

### Post by crane on 2005-05-03
> **jdong]Sorry, I didn't see your thread from a while back.

If you disable ESD permanently, the only functionality you loose are the cute little GNOME sounds when you log on and off  said:**
> http://www.linuxtv.org/v4lwiki/index.php/Saa7134_devices[/url] , which may be related. I personally don't have a tuner card, so I don't know the specifics.

Kezz, I have to mirror this post. I am sorry but I too missed the post about the sound problem. I myself have been playing ut2k4, q3, and a couple other games without problems, Hope the next time you try it you have better luck!

---

### Post by TravisNewman on 2005-05-03
Preferences->Multimedia Systems Selector. Switch to ALSA. 

At least I assume that's what it's doing. esd isn't running anymore

---

### Post by jdong on 2005-05-04
Thanks!

---

### Post by void_false on 2005-05-04
I could never understand how people that use guru-only distros (like Gentoo) can switch to simplier ones.

---

### Post by Stormy Eyes on 2005-05-04
[QUOTE=void_false]I could never understand how people that use guru-only distros (like Gentoo) can switch to simplier ones.[/QUOTE]

Being somebody who switched from Gentoo to Ubuntu: I didn't want to spend time constantly tinkering with my Gentoo setup; I suspected that if I kept Gentoo I'd pay more attention to my computer than to my wife -- which is a bad idea for a newlywed.

---

### Post by defkewl on 2005-05-04
It's okay. People come and people go :)

---

### Post by KezzerDrix on 2005-05-04
> void_false:
I could never understand how people that use guru-only distros (like Gentoo) can switch to simplier ones.

You should try Gentoo then you would understand. ;) If your not a guru do not apply. I am no guru -- that and compiling from source is time consuming no matter what any one tells you, the facts are it does.  I like Ubuntu and Mepis because they allow me to enjoy my computer, not just log on to do maintanence and watch nearly endless compiler messages scroll bye while I could be playing ut2004, um which doesn't run very well when trying to compile things at the same time.  Also, unlike Ubuntu system updates can and normally do cause system instability.  Read my previous post for an example of what I mean.  

[www.tuxmagazine.com](www.tuxmagazine.com) has an article by Mango Parfait in which she states that 

> Gentoo is not for beginners, or for people who want their desktop to be fast and responsive.  It is for people who like to watch their computer compile software for hours and hours and hours, which is what slows down the desktop.  I download the latest unstable Gentoo updates every day and watch my computer compile programs all night when I have insomnia.  You risk making Gentoo unstable when you update all the time.  The most thorough way to cure the problem is to recompile the entire system from scratch.  It takes days for Gentoo to compile everything.  I like to watch all the compiler messages croll off the screen day after day.  It is hypnotizing

If you haven't checked out Tuxmagazine.com you should it is great for beginners.

Also, next time I try ubuntu I am going to post my questions for help in this forum.  I actually get workable answers here :)

---

### Post by jimcooncat on 2005-05-04
I'm a Gentoo convert myself. I still have our main email server running with Gentoo, though it's quite out of date since I didn't upgrade yet to 2.6. Not much running on it anyway, just Qmail and some helper apps.

It took me a long time and three installs, being a noob at Linux, to get this first server going the way I wanted. I sure learned a hell of a lot while doing it.

I did another install of a full Gentoo KDE desktop later, and learned a lot more. But the time I had to put in learning how to do things properly was enormous. Compiling does take a while, and you can learn to do something else while that's going on, but the research and configuration is what took my time. 

I've switched to Ubuntu for desktop usage, and will be using it for almost all my installs from now on. It's just so easy. Now I only do deep research on what needs to be customized -- not every little app I just want to use.

One of the things Gentoo would be great for is to roll out custom distributions, especially if they're limited in functionality (just so a person can keep up with it). I want to start using it for this if I can ever get Xen installed.

I think each distro has it's own merits, and should be used accordingly. Competition is great, and a little needling spurs that along. But bashing just serves to show the basher's ignorance. 

By the way, I never did figure out Mepis, and that's how I wound up trying Ubuntu!

---

### Post by void_false on 2005-05-04
> You should try Gentoo then you would understand 
Already done. But I was too dumb to install it propertly and ended with kernel panic.

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=void_false]Already done. But I was too dumb to install it propertly and ended with kernel panic.[/QUOTE]

Thats not being dumb.

---

### Post by jdong on 2005-05-04
[QUOTE=void_false]I could never understand how people that use guru-only distros (like Gentoo) can switch to simplier ones.[/QUOTE]

Ok, with Gentoo, one spends a considerable amount of time tweaking and playing with the distribution -- messing around with USE flags, dealing with broken ebuilds, waiting forever for packages to build, etc etc etc.

Also, Gentoo ebuilds are known for frequent breakages. With desktop packages, it's somewhat acceptable for a Linux enthusiast.

However, when a MySQL security patch breaks MySQL and is marked STABLE, I have strong issues with that (happened around November 2004).


In the end, it's a matter of personal choice.

---

### Post by void_false on 2005-05-05
[QUOTE=poofyhairguy]Thats not being dumb.[/QUOTE]
I tryed to install it several times from different stages with and without genkernel. All what I got is highly unstable system or kernel panic.

---

### Post by Xerampelinae on 2005-05-05
I used to use Gentoo.. the reason I've been installing Ubuntu is that it saves considerable time.  With Gentoo it's more like you are the distribution maintainer.  With Ubuntu other people have put in work getting various things going, so that's less for me to worry about.

Plus apt-get is much faster than emerge... and I don't lose much in terms of flexibility to do what I want... so why not save some time and avoid solving some problems by using Ubuntu.

---

