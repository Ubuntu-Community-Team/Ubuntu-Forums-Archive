---
title: "Difference between Ubuntu and Mint, Under the Hood"
date: 2013-04-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Rikeshar on 2013-04-07
Hey everyone, not sure if this is the right place to ask, but I'm not sure where to. I was wondering what the "under the hood" differences between Ubuntu and Mint are. Stuff other than the Desktop Environment, default programs and what not that can be interchanged between the two.

---

### Post by CaptainMark on 2013-04-07
Nothing really. unless you count the project goals and target user base

---

### Post by Rikeshar on 2013-04-07
That's what I thought. Thanks.

---

### Post by breezypt on 2013-04-07
Mint is more Windows looking than Ubuntu, with the start menu on the left side. I guess that it is geared toward the windows users to get them to come over to the bright side

I removed the rest of this post because I realized the rest of my response was highjacking your thread, and I apologize for that, didn't mean to.

---

### Post by Perfect Storm on 2013-04-07
Moved to Ubuntu, Linux and OS Chat.

---

### Post by MadmanRB on 2013-04-08
In a word, nothing.
Unless you are talking about LMDE

---

### Post by carl4926 on 2013-04-08
kernel updates > Mint updates will not upgrade the kernel

Mint codecs > Mint comes mp3 etc..ready with it's own mutimedia prep. You don't install ubuntu-restricred-extras in Mint

Mint flash-plugin > Mint also packages it's own preparation of the adobe plugin - But you can switch to the official Adobe one

---

### Post by mamamia88 on 2013-04-08
Is the mint flash plugin any better at all?  Heck I use an app called minitube just so I don't have to use flash.

---

### Post by GameX2 on 2013-04-08
Mint is probably my second favorite Linux distribution, following Ubuntu; I would probably switch to Mint, if one day, I prefer to quit Ubuntu (Who know, Ubuntu changed a lot in a short amont of time with Unity, for example).

What bother me, is that Compiz does not seem compatible with it. :(
Yes, it's unstable and will be dropped ( :( ), but it's just cool, and CCSM remain extremely useful to manage all my windows.

---

### Post by teacher.japan on 2013-04-09
They are both the same if you are a general user.  
If you are a developer, it doesn't make one bit of difference. If you are comfy with the shell, it doesn't matter what you use.

It's little tiny things that usually dictate what distro one uses, things that are mostly aesthetic in nature, and sometimes more practical, for example centOS not working for me without major dinking around with drivers etc.  I don't worry about flashy stuff like COMPIZ etc first, I first check if everything that I NEED works, then I move on to UI.

Ubuntu is a great starter distro that keeps getting more mature as time progresses and has a solid community.

P.S: By starter i mean documentation,support etc.

---

### Post by teacher.japan on 2013-04-09
@mamamia
I've had no issues with it at all.  Works perfectly fine.

---

### Post by Moose on 2013-04-09
> **mamamia88 said:**
> Is the mint flash plugin any better at all?  Heck I use an app called minitube just so I don't have to use flash.
Thank god I'm not the only person who uses Minitube just for that. &#9829;

---

### Post by carl4926 on 2013-04-09
> **mamamia88 said:**
> Is the mint flash plugin any better at all?  Heck I use an app called minitube just so I don't have to use flash.
No
Possibly less so.

Chrome is most likely to work (Not chromium unless your distro pushes the chromium-pepper-flash, ubuntu/mint don't).

If you still have trouble. It could be be a problem with your CPU if it's fairly old model.
In which case only an older flash (10.3) might work

---

### Post by vasa1 on 2013-04-09
> **carl4926 said:**
> ... the chromium-pepper-flash ...
What is that? Do you have a link to share about Pepper Flash for Chromium?
I know there's Pepper Flash for Chrome that possibly can be copied over.

---

### Post by carl4926 on 2013-04-09
> **vasa1 said:**
> What is that? Do you have a link to share about Pepper Flash for Chromium?
I know there's Pepper Flash for Chrome that possibly can be copied over.

I use openSUSE too and packman have packaged it
[http://packman.links2linux.de/package/chromium-pepper-flash](http://packman.links2linux.de/package/chromium-pepper-flash)

Maybe someone could get it built to Medibuntu?

---

### Post by vasa1 on 2013-04-09
> **carl4926 said:**
> I use openSUSE too and packman have packaged it
[http://packman.links2linux.de/package/chromium-pepper-flash](http://packman.links2linux.de/package/chromium-pepper-flash)
...
Very interesting! And can you share how they handle Chromium itself? The Ubuntu one generally lags Chrome stable.

Edit: but this link, [http://packman.links2linux.de/package/chromium](http://packman.links2linux.de/package/chromium), is quite old!

---

### Post by carl4926 on 2013-04-09
> **vasa1 said:**
> Very interesting! And can you share how they handle Chromium itself? The Ubuntu one generally lags Chrome stable.

Edit: but this link, [http://packman.links2linux.de/package/chromium](http://packman.links2linux.de/package/chromium), is quite old!
I'm in Ub ATM
I'll check the stats and get back. But I know chromium way ahead of Ub

---

### Post by carl4926 on 2013-04-09
Here we are

```
chromium-pepper-flash-11.6.602.177-9.1.x86_64
chromium-27.0.1425.0-1.1.1.x86_64
```

---

### Post by vasa1 on 2013-04-09
> **carl4926 said:**
> Here we are

```
chromium-pepper-flash-11.6.602.177-9.1.x86_64
chromium-27.0.1425.0-1.1.1.x86_64
```

apt-cache show chromium-browser >>> Version: 25.0.1364.160-0ubuntu0.12.10.1

---

### Post by mamamia88 on 2013-04-09
> **vasa1 said:**
> apt-cache show chromium-browser >>> Version: 25.0.1364.160-0ubuntu0.12.10.1

Oh and btw if you install chrome from the deb file it adds a file it /etc/apt/sources.list.d which makes it so that you always have the latest version.  Pretty sure you can just extract a chrome deb file and copy the pepper flash plugin to the plugins folder for chromium as well.

---

### Post by vasa1 on 2013-04-09
> **mamamia88 said:**
> Oh and btw if you install chrome from the deb file it adds a file it /etc/apt/sources.list.d which makes it so that you always have the latest version.  Pretty sure you can just extract a chrome deb file and copy the pepper flash plugin to the plugins folder for chromium as well.
I use Chrome but I was curious about the mention of Chromium Pepper Flash. (I don't use Chromium.)

---

### Post by mamamia88 on 2013-04-09
> **vasa1 said:**
> I use Chrome but I was curious about the mention of Chromium Pepper Flash. (I don't use Chromium.)

ah pepper flash is just the name of the built in flash player for  chrome.

---

### Post by craig10x on 2013-04-09
Exactly, "pepper flash" is Chrome's plug in flash...which it comes with (and with Chromium has to be added in if you want it)...When you run chrome, you are using pepper, unless you disable it in the chrome plug ins settings...if you did that, you'd be running the old adobe flash which is what ubuntu installs with the restricted extras package and is on everyone's hard drive...

The linux version of that old adobe flash only gets security updates, not newer versions because adobe isn't supporting it in linux anymore...However, they do have an agreement with Chrome for it's pepperflash, so pepper does gets all the latest versions of adobe flash...and that is why it is better to run it then the old version...

---

### Post by leclerc65 on 2013-04-09
I cannot live without Nautilus on my main desktop because I use to shuffle, archive lots of files. Thunar, Pcmanfm are deal breakers unless used on 
secondary computers. Mint gives me Caja; plus, Mate is rock stable while overidden Unity with LXDE is not.
Actually I prefer something like Total Commander with option 'Overwrite all older...' but there is no equivalent in Linux.:(

---

### Post by CaptainMark on 2013-04-09
> **mamamia88 said:**
> Is the mint flash plugin any better at all?
No, the built in one in mint is actually worse. Mint is my main os now and I always install the package flashplugin-installer

---

### Post by VietCanada on 2013-04-11
Seperate x-screens works in Mint 13. It doesn't work in Ubuntu 11 or anything higher as far as I can tell. It doesn't work in Mint 14 either. Or MS higher than XP. That was the deal breaker for me. I have been watching rented or dl'd movies and TV shows on one monitor while playing a game on the other for 13 years. I have an Nvidia card. I'm not sure which 'under the hood' component is responsible for this difference. But there is definitely a difference in functionality between the two. Don't even get me started on the retardedness of making a touch screen OS for PCs. Whoever the touch screen or McDonalds cash register pitchman was that sold that idea to the OS writing world deserves a 'Barnum and Bailey' award. Judging by the press reports and the MS8 fail I should think that is pretty common knowledge by now. Fortunately there is Mint Mate for me and recurring LTS versions for all the others. That seems to be pretty much all of the PC owning world. I see there is a thread here about this topic. I'll vent there if anyone cares. Meanwhile I'll keep my eyes open for a fully functioning PC OS.

---

### Post by moonport on 2013-04-11
In a few words, Ubuntu uses Unity (you can choose for Gnome too), Mint uses either MATE or Cinnamon as shell, has a different selection of default applications, but the core system is pretty much the same.

---

