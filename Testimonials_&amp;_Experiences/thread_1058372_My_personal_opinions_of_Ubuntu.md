---
title: "My personal opinions of Ubuntu"
date: 2009-02-02
forum: Testimonials &amp; Experiences
---

### Post by Sonadow on 2009-02-02
To be honest, i started out with a very bad impression of Linux. My first dive into the alternative OS was with RedHat in the late 1990s-early 2000s, which was essentially nothing short of a nightmare: nothing could work on it, but that's because like most people, I had been spoilt too much by the importance of the GUI. (and i still think that way as well)

I went back to Windows and stayed there until i heard of Ubuntu and decided to give Linux a try again. Edgy, Fiesty and Gutsy were, as usual, nothing short of nightmares: no WLAN, stuck on 800 x600 resolution, i again swore off Linux since the hardware supoort was technically nonexistant.

When i finally got Hardy, i dedcided to try and learn at least a few simple CLI commands. standard stuff like sudo displayconfig-gtk and how to work NDISwrapper (from CLI and NDISgtk, but NDISgtk was so easy to use i have forgotten completely on how to work NDISwrapper from CLI) And for once, i finally had a working WLAN connection with a suitable resolution. Although the installation did not last long as i had to go back to Windows to use Adobe CS3.

Now, i got my hands on Intrepid and Jaunty Alpha 3. And my biggest gratification is that the moment i booted the LiveCD, both Intrepid and Jaunty identified my WLAN USB sticks and booted up the WLAN connection instantly. I do not know whether this is due to a new Linux kernel by Torvalds which claims to offer support for WLAN devices (source: [http://www.internetnews.com/dev-news/article.php/3793371/Gifts+for+All+in+Linux+2628.htm](http://www.internetnews.com/dev-news/article.php/3793371/Gifts+for+All+in+Linux+2628.htm)), or whether it's because of the Ubuntu team's development. But needless to say, now that WLAN is auto-detected in my system. i dont really see myself going back to Windows for a long time, probably until an upcoming version of Ubuntu breaks the autodetection of WLAN.

The deprecation of displaycpnfog-gtk was a huge problem: it threw my desktop back into 800 x 600 again. Editing the xorg.conf was nightmarish and more often than not, it totally nuked X big time until some kind soul on Launchpad told me to add in just the following 2 lines into xorg, nothing more:

```
HorizSync 30-75
VertRefresh 50-110 
```

he also told me that using this minimalistic xorg.conf would always unlock a whole range of resolutions for the monitor. I tried it on Jaunty and Intrepid, and to my great surprise, he was 100% correct.

So now, here i am, typing this away on a LiveCD of Jaunty. If Ubuntu and Linux would continue to provide such easy WLAN support for most WLAN devices, i would say, Ubuntu has gotten a new loyal user.

---

### Post by solwic on 2009-02-02
> **Sonadow said:**
> To be honest, i started out with a very bad impression of Linux. My first dive into the alternative OS was with RedHat in the late 1990s-early 2000s, which was essentially nothing short of a nightmare: nothing could work on it, but that's because like most people, I had been spoilt too much by the importance of the GUI. (and i still think that way as well)

I went back to Windows and stayed there until i heard of Ubuntu and decided to give Linux a try again. Edgy, Fiesty and Gutsy were, as usual, nothing short of nightmares: no WLAN, stuck on 800 x600 resolution, i again swore off Linux since the hardware supoort was technically nonexistant.

When i finally got Hardy, i dedcided to try and learn at least a few simple CLI commands. standard stuff like sudo displayconfig-gtk and how to work NDISwrapper (from CLI and NDISgtk, but NDISgtk was so easy to use i have forgotten completely on how to work NDISwrapper from CLI) And for once, i finally had a working WLAN connection with a suitable resolution. Although the installation did not last long as i had to go back to Windows to use Adobe CS3.

Now, i got my hands on Intrepid and Jaunty Alpha 3. And my biggest gratification is that the moment i booted the LiveCD, both Intrepid and Jaunty identified my WLAN USB sticks and booted up the WLAN connection instantly. I do not know whether this is due to a new Linux kernel by Torvalds which claims to offer support for WLAN devices, or whether it's because of the Ubuntu team's development. But needless to say, now that WLAN is auto-detected in my system. i dont really see myself going back to Windows for a long time, probably until an upcoming version of Ubuntu breaks the autodetection of WLAN.

The deprecation of displaycpnfog-gtk was a huge problem: it threw my desktop back into 800 x 600 again. Editing the xorg.conf was nightmarish and more often than not, it totally nuked X big time until some kind soul on Launchpad told me to add in just the following 2 lines into xorg, nothing more:

```
HorizSync 30-75
VertRefresh 50-110 
```

he also told me that using this minimalistic xorg.conf would always unlock a whole range of resolutions for the monitor. I tried it on Jaunty and Intrepid, and to my great surprise, he was 100% correct.

So now, here i am, typing this away on a LiveCD of Jaunty. If Ubuntu and Linux would continue to provide such easy WLAN support for most WLAN devices, i would say, Ubuntu has gotten a new loyal user.

I know your pain.  I started with Ubuntu 6.06 and didn't even have the benefit of 800x600.  I had a black screen, and I had to learn to use the Text Installer because the Graphical one was borked on my system.  

Editing xorg.conf wasn't too hard for me; what sucked was tracking down the sync and refresh ranges.  

Not until 8.04 did the Graphical install work for me.  I've been mostly with Ubuntu since then.  

Anyway, glad you're enjoying your Ubuntu.  Once you get off the LiveCD and install it on your hard drive, you'll find Ubuntu is about 10 times faster than what you're experiencing now.  :)

Good luck, and welcome to the light!  :biggrin:

---

### Post by Sonadow on 2009-02-02
> **jrock612 said:**
> I know your pain.  I started with Ubuntu 6.06 and didn't even have the benefit of 800x600.  I had a black screen, and I had to learn to use the Text Installer because the Graphical one was borked on my system.  

Editing xorg.conf wasn't too hard for me; what sucked was tracking down the sync and refresh ranges.  

Not until 8.04 did the Graphical install work for me.  I've been mostly with Ubuntu since then.  

Anyway, glad you're enjoying your Ubuntu.  Once you get off the LiveCD and install it on your hard drive, you'll find Ubuntu is about 10 times faster than what you're experiencing now.  :)

Good luck, and welcome to the light!  :biggrin:

While i won't deny that i am enjoying the LiveCD now, I have concerns and reservations as to whether this sudden support for WLAN devices will be broken in the next release, or the next next release, or the xth release.

Still holding my breath on it, and as always, in the event of an emergency, my Vista Business DVD sits snugly in my drawer of software DVDs.

---

### Post by solwic on 2009-02-02
> **Sonadow said:**
> While i won't deny that i am enjoying the LiveCD now, I have concerns and reservations as to whether this sudden support for WLAN devices will be broken in the next release, or the next next release, or the xth release.

Still holding my breath on it, and as always, in the event of an emergency, my Vista Business DVD sits snugly in my drawer of software DVDs.

Well that's the beauty of it:  you don't have to upgrade.  :)  There are people on this forum still running Dapper Drake, which was like four releases ago.  If Ibex works for you, use it.  Stick with it.  :)

But in the end you have to do whatever is right for you.  :)

Cheers, whatever you decide.  :)

---

### Post by Crafty Kisses on 2009-02-02
> **jrock612 said:**
> Well that's the beauty of it:  you don't have to upgrade.  :)  There are people on this forum still running Dapper Drake, which was like four releases ago.  If Ibex works for you, use it.  Stick with it.  :)

But in the end you have to do whatever is right for you.  :)

Cheers, whatever you decide.  :)

I still run Dapper on one of my HD's, it's the most stable release in my opinion.

---

### Post by cjnkns on 2009-02-02
> 
So now, here i am, typing this away on a LiveCD of Jaunty. If Ubuntu and Linux would continue to provide such easy WLAN support for most WLAN devices, i would say, Ubuntu has gotten a new loyal user.


I realize every users experience can and probably will be different. But, I just wanted to add that I have never had a problem with WLAN on Ubuntu. Interestingly enough about a month ago I was going through one of my "I hate linux phases".

Well, I tried to install XP on my laptop and it simply would NOT connect to my WLAN. So, in my frustration I came back to Ubuntu like a puppy with his/her tail between my legs :-).

---

### Post by Crafty Kisses on 2009-02-02
> **cjnkns said:**
> I realize every users experience can and probably will be different. But, I just wanted to add that I have never had a problem with WLAN on Ubuntu. Interestingly enough about a month ago I was going through one of my "I hate linux phases".

Well, I tried to install XP on my laptop and it simply would NOT connect to my WLAN. So, in my frustration I came back to Ubuntu like a puppy with his/her tail between my legs :-).

Haha, nice read there my friend. :)

---

### Post by Sonadow on 2009-02-02
> **cjnkns said:**
> I realize every users experience can and probably will be different. But, I just wanted to add that I have never had a problem with WLAN on Ubuntu. Interestingly enough about a month ago I was going through one of my "I hate linux phases".

Well, I tried to install XP on my laptop and it simply would NOT connect to my WLAN. So, in my frustration I came back to Ubuntu like a puppy with his/her tail between my legs :-).

you have to install the wireless hardware driver first. Usually it's available from the laptop vendor's website. XP has few built-in drivers.

Once you install the driver, which takes only a few seconds, Windows will hook up the WLAN and you are good to go.

You can also see the difference between Windows and Linux here: In the Windows world, nobody is content with using the bundled drivers in Windows: they always rather take the trip down to the vendor's website and download the official hardware driver.

In Linux, driver support is usually integrated into the kernel (i think?). Both methods have their own pros and cons. Personally, i would love to install my own driver from an automated executable file, but ONLY IF it was easily obtainable from the vendor's website. Have always been somewhat weary of bundled drivers in the kernel.

---

### Post by cardinals_fan on 2009-02-02
> **jrock612 said:**
> Well that's the beauty of it:  you don't have to upgrade.  :)  There are people on this forum still running Dapper Drake, which was like four releases ago.  If Ibex works for you, use it.  Stick with it.  :)

But in the end you have to do whatever is right for you.  :)

Cheers, whatever you decide.  :)
I ran Dapper until one month ago, when I moved my old box over to NetBSD for good.  Edgy was a touch better for me, but I loved both.

---

