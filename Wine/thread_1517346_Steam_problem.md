---
title: "Steam problem"
date: 2010-06-24
forum: Wine
---

### Post by itsvan on 2010-06-24
Hi there guys,,, so i installed Wine, the necessary font, and finally steam,,,i think i did it fine,,,so i try to run Steam, and the steam icon appears on the bottom menu bar but the actual login screen or main menu doesnt appear at all,,,after countless trys steam wont pop up or anything,,what can i do??

---

### Post by itsvan on 2010-06-25
Actually now i got the Steam Menu to come out,,but now when i try to get on a server it closes and returns to my desktop,,,also i try to run the video stress test and it runs,,but some skins are in all white after a couple of seconds it closes again to desktop...

---

### Post by asdfoo on 2010-06-25
which version of Wine? wine-1.2-rc5 is the most recent.

which video card and drivers?

---

### Post by itsvan on 2010-06-26
I have the most recent one,,hwo can i check what do i have?? i have an Eee pC 900HD...dont know any other details,,,it seems to bee running fine on the video stress except for the mentioned problems,,,it keeps closing on me before going into a game,

---

### Post by asdfoo on 2010-06-26
> **itsvan said:**
> I have the most recent one,,hwo can i check what do i have?? i have an Eee pC 900HD...dont know any other details,,,it seems to bee running fine on the video stress except for the mentioned problems,,,it keeps closing on me before going into a game,

open a terminal and type

wine --version


I don't know the specs of your netbook but I suspect it's one of the ones that has an intel video card, seeking help to find the best drivers for that is probably dealt with in another subforum, people usually try ubuntu edgers.

To give us a better idea of what is happening can you post a log?

[http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

---

### Post by itsvan on 2010-06-26
wine-1.0.1

---

### Post by asdfoo on 2010-06-27
> **itsvan said:**
> wine-1.0.1

That version is about a year old, there have been probably 1000 bug fixes in that time.

Update to wine-1.2-rc5 and retry.

---

### Post by asdfoo on 2010-06-28
> **LinuxUser24 said:**
> Hi guys I also have a problem regarding Steam. I'm currently playing Left 4 Dead 2 and I always get an error message saying that if failed to load on steam. What do you think is the problem with this?

Not related to the original post in this thread.
You should update to the latest version of Wine which is 1.2-rc5, check the AppDB page for relevant information.

---

### Post by itsvan on 2010-06-28
Whats the easiest way to install the new wine or update it?? also will Steam be uninstaleld in the processed?

---

### Post by Loctrice on 2010-06-28
I personally got the repo added from wine. You can see how on the wine hq site. I play steam games on 1.2 . These guys can tell you more most likely about the prepackage from apt. I usually attempt to install a program that I like, after trying it out from apt, from source unless that place allows adding of the repo's.

Make sure you have the latest video drivers installed. You can do this by system -> administration -> hardware drivers. If you have nvidia, they are usually pretty good about having drivers for linux. Of coarse in either of those cases you have to deal with third party , closed source drivers. If you are a gamer though, and a nov like me, you might benefit from them.

so, check the video drivers, get the new wine, and you should be down to some solid exact questions at least.

---

### Post by itsvan on 2010-06-28
I check my video drivers and it says This system has no proprietaryy drivers..what does that mean

---

### Post by Loctrice on 2010-06-29
It means that you are best suited with the drivers that are installed. My other pc had this happen, it is an older video device. You still have options, you can find another linux driver for video if you like, or just keep the one that you have. As long as your hardware meets requirements for the game, then it shouldn't be an issue. 
 
I don't have left for dead, so I can't help much further. Make sure you have the latest stable wine, and start looking for any known bugs on the wine site. Usually people post work arounds for issues there. My problem with the killing floor (from what I understand they are similar) was the video programming they used. You can find it in your ini  and check. Some of the microshaft direct 3d  stuff doesnt have opengl or linux compatible stuff going on under the hood.
 
Good luck

---

### Post by itsvan on 2010-06-29
i whoudnt mind updating or installing a new video driver,,thing is it might be that my pc is to slow for it? its a little netbook thing is i dont know exactly what i have and what are the req for steam..i tried updating wine,and i got it up to ver 1.1.38, and it still has a lag issue.

---

### Post by Loctrice on 2010-06-29
go to wine hq , or do a search on google for a link. You want to add the wine repo if you are going in that direction. I just updated , from the package update manager, to wine 1.2 rc5. It's got alot of fixes. 

Regarding your graphics card. Just go to the manufacturer site and get the linux binaries if they offer them. It's usually an install script, but sometimes it's a little more in depth, but you can find a walkthrough to install. My advice on this would be to download links and figure out how to use it, that will let you use the web in the terminal if you need to google while x is down.


Steam itself has minimal requirements, it's the individual games that have system specs you need to watch for. It usually has alot to do with the graphics hardware capabilities.

---

### Post by triva911 on 2010-08-02
> **itsvan said:**
> Hi there guys,,, so i installed Wine, the necessary font, and finally steam,,,i think i did it fine,,,so i try to run Steam, and the steam icon appears on the bottom menu bar but the actual login screen or main menu doesnt appear at all,,,after countless trys steam wont pop up or anything,,what can i do??

I have same problem .... steam doesn't start ...

---

### Post by triva911 on 2010-08-02
SOLVED .... Problem is finaly fixed.... just update wine or download here a new version

[https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa")

[[IMG]http://dodaj-sliku.co.de/dt-1112807734235.png[/IMG]](http://dodaj-sliku.co.de/pt-1112807734235.png)

---

### Post by sgtrock on 2010-10-09
> **triva911 said:**
> SOLVED .... Problem is finaly fixed.... just update wine or download here a new version

[https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa")

[[IMG]http://dodaj-sliku.co.de/dt-1112807734235.png[/IMG]](http://dodaj-sliku.co.de/pt-1112807734235.png)

Please add a [SOLVED] tag to the thread so people can find solutions quicker.

Thanks

---

