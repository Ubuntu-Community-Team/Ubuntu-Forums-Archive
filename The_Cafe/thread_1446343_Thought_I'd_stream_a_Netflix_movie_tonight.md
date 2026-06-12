---
title: "Thought I'd stream a Netflix movie tonight"
date: 2010-04-03
forum: The Cafe
---

### Post by bigsmitty64 on 2010-04-03
And then............... 

[COLOR=Blue][B]"our apologies — streaming is not supported for your operating system."

[/B][COLOR=Black]Go figure, I just stripped my machine of windows 2 days ago!  This is a problem for me.[/COLOR][/COLOR]

---

### Post by steveneddy on 2010-04-03
User Agent Switcher for Firefox

or

Use Windows in VirtualBox

---

### Post by Dayofswords on 2010-04-03
> **steveneddy said:**
> User Agent Switcher for Firefox

i'd like to know if that works :-k

i dont have netflix, but if i did, wont hurt to know

---

### Post by kblft on 2010-04-03
Take a look here [http://ubuntuforums.org/showthread.php?t=1442273&highlight=netflix](http://ubuntuforums.org/showthread.php?t=1442273&highlight=netflix)

apparently netflix don't support linux

---

### Post by gletob on 2010-04-03
[COUGH]I thought I'd Pirate Bay a movie, but that's illegal[/COUGH]

---

### Post by Chronon on 2010-04-03
Linux systems aren't able to deal with the DRM that Netflix uses.  Unless Microsoft steps up and provides us with Linux packages to decrypt the streams, or Netflix changes to a scheme that Linux systems can support, we won't be seeing anything anytime soon.

---

### Post by Ewingo401 on 2010-04-03
It seems like this comes up at least twice a week now.  The ONLY way to stream Netflix on a computer running a Linux OS is by running Windows in a virtual machine.  User agent switchers, moonlight, or none of the other "work arounds" work.  Also, Netflix has stated publicly that there are no plans to bring streaming to desktop Linux.

---

### Post by TheNerdAL on 2010-04-03
I heard somwhere(I think on this forum) that Netflix is going to be compatible with Linux soon. :D

---

### Post by TheNerdAL on 2010-04-03
> **Ewingo401 said:**
> It seems like this comes up at least twice a week now. The ONLY way to stream Netflix on a computer running a Linux OS is by running Windows in a virtual machine. User agent switchers, moonlight, or none of the other "work arounds" work. Also, Netflix has stated publicly that there are no plans to bring streaming to desktop Linux.
 Aww fudge!

---

### Post by swoll1980 on 2010-04-03
> **gletob said:**
> [COUGH]I thought I'd Pirate Bay a movie, but that's illegal[/COUGH]

You know they're sending out 50,000 letters to pirates requesting settlements? Good luck with that.

---

### Post by bigsmitty64 on 2010-04-03
Installed User Agent Switcher  and, Nope. it says I need to have active x installed now.

---

### Post by swoll1980 on 2010-04-03
> **bigsmitty64 said:**
> Installed User Agent Switcher  and, Nope. it says I need to have active x installed now.

User agent isn't going to help. drm is the problem. There is no Linux implementation of this. Look at the bright side, you still get to play with your cube.

---

### Post by wojox on 2010-04-03
> **bigsmitty64 said:**
> Installed User Agent Switcher  and, Nope. it says I need to have active x installed now.

What if you installed Moonlight?

---

### Post by Chronon on 2010-04-03
Moonlight doesn't contain DRM support from Microsoft.  You can get as far as launching the player.  Authenticating the streams fails.

---

### Post by 2hot6ft2 on 2010-04-04
[COUGH]http://stagevu.com/index[/COUGH]

And if you have any trouble playing them. Which you wouldn't try anyway, RIGHT?
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
You will have to enter your password which wont be displayed just type it in and hit Enter
Then install gecko media player:
```
sudo apt-get install gecko-mediaplayer
```
Then restart firefox and try it out.

---

### Post by snowpine on 2010-04-04
Always read the [system requirements]("http://www.netflix.com/HowItWorks"):

> What are the system requirements to watch movies instantly on my PC or Mac?
You must have a computer running Windows or Mac OS X and an active broadband connection to the Internet.

    * Windows requirements: Windows XP with Service Pack 2 or higher; Windows Vista; Windows 7; Internet Explorer 6.0 or higher or Firefox 2 or higher; 1.2 GHz processor; 512 MB RAM.
    * Mac OS X requirements: an Intel-based Mac with OS 10.4.8 or later; Safari 3 or higher; Firefox 2 or higher; 1 GB RAM.

---

### Post by Dayofswords on 2010-04-04
> **TheNerdAL said:**
> Aww fudge!

aww fudge indeed

---

### Post by bigsmitty64 on 2010-04-04
Oh well. Guess I found something I can do on Windows but not Linux.:p 

Time for :popcorn: and laptop with XP. I gotta go watch donnie brasco on netflix. Someone said it was good.

---

### Post by bigsmitty64 on 2010-04-04
> **swoll1980 said:**
>  Look at the bright side, you still get to play with your cube.


and it won't cost me $ 9.99 a month!

---

### Post by 2hot6ft2 on 2010-04-04
> **bigsmitty64 said:**
> Oh well. Guess I found something I can do on Windows but not Linux.:p 

Time for :popcorn: and laptop with XP. I gotta go watch donnie brasco on netflix. Someone said it was good.
I suppose if you have to OR
[http://stagevu.com/search?for=donnie+brasco&in=Videos](http://stagevu.com/search?for=donnie+brasco&in=Videos)

---

### Post by bigsmitty64 on 2010-04-04
Ya dude! Thanks :)

---

### Post by 2hot6ft2 on 2010-04-04
> **bigsmitty64 said:**
> Ya dude! Thanks :)
Welcome.
:-\"

---

### Post by K.J. on 2010-04-13
Just thought I'd add a quick correction. There are exactly THREE ways to stream Netflix to a Linux computer.  One is technically illegal in the U.S., and two require Windows (one of which costs $$).

1. Run the Wii Netflix streamer in Dolphin Emu. (Not sure how stable networking support is).
2. Like it was said before, run Netflix in a VirtualMachine. Needs a bit of speed, good bit of overhead. What I do, is my VirtualBox copy of XP runs off a physical partition that I can also boot natively. It just gets a bit annoying because you have to re-activate Windows each time you switch.
3. (What I use most often). Install PlayOn to a Windows machine. It can stream Netflix (as well as Hulu and others) to any upnp compatible device.  Costs $40, although if you wait until the end of the trial you get $10 off, and if you sign up for GameFly for another $8.95 you get an additional $20. You can cancel right away, so you can get it for $18.95.

Although, I've never been able to get upnp to work well in Ubuntu. It works flawlessly in XBMC on my Xbox, but I can't get XBMC to work at all in Ubuntu using upnp.  I couldn't get jmount to work and apparently it also does work in 64-bit. Boxee works well, but not everytime.  I finally got it working using Ubuntu 10.04 and installing the dependencies for Boxee from the karmic repository. Boxee has been working flawlessly.

---

### Post by forrestcupp on 2010-04-13
> **Ewingo401 said:**
> It seems like this comes up at least twice a week now.  The ONLY way to stream Netflix on a computer running a Linux OS is by running Windows in a virtual machine.  User agent switchers, moonlight, or none of the other "work arounds" work.  Also, Netflix has stated publicly that there are no plans to bring streaming to desktop Linux.

I haven't been a part of those discussions.  But has anyone tried running it through the Windows version of Firefox installed with Wine?  You can sometimes install the necessary addons this way.

A long time ago, Fox's videos weren't supported in Linux, but I was able to get them to work that way.

---

