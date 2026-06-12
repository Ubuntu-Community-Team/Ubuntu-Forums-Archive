---
title: "World of Warcraft crashes on startup"
date: 2011-02-09
forum: Wine
---

### Post by pedrozs on 2011-02-09
Hello
Firstly you should know that i am using:
Kubuntu 10.10 32 bit version.
And 2.6.35-25 Linux kernel version.

My machine is a MSI u100.

The problem is that when i launch WoW.exe or when i click "Play" on the launcher Wow crashes.

Here is an image of what i get: [http://img696.imageshack.us/img696/5839/wowuz.png](http://img696.imageshack.us/img696/5839/wowuz.png)

And here is the console output: [http://pastebin.com/raw.php?i=PEvmsB0J](http://pastebin.com/raw.php?i=PEvmsB0J)

I should mention that if i run it using DirectX I hear the sound of wow, using opengl i don't.
I've already tried with and without this on the WTF/Config.wtf: 

SET gxAPI "OpenGL"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"

Thanks!

---

### Post by pedrozs on 2011-02-11
Thanks for moving the thread. =)

---

### Post by gerowen on 2011-02-11
What kind of video card are you using?  I see in the error output from the console:
```

d3d_caps:select_card_intel_mesa **Card selection not handled for Mesa Intel driver**

```
This looks like you're using the default mesa drivers for your card(Maybe I'm mistaken, not used to dealing with Intel cards cause' both of my computers have ATI cards).  If they're available have you installed the proprietary drivers?  A lot of times if you have an active internet connection Ubuntu will let you do it automatically.  I'm not sure where it would be found in Kubuntu but look under your admin menus for an item called "Additional Drivers".  If it lists one for your video card you will need to "Activate" it, which will in effect download and install it, then you'll be required to restart.  Let me know what you find.

---

### Post by cwwilson721 on 2011-02-12
It has an Intel GMA 950.

Good luck.

A general rule of thumb: Netbook + I950 +WoW + wine = FAIL

---

### Post by pedrozs on 2011-03-04
First, thanks for replying
Gerowen: there are no drivers displayed where you say..[IMG]http://img191.imageshack.us/img191/4350/driversr.png[/IMG]

---

### Post by cwwilson721 on 2011-03-04
This EXACT question has been asked and answered MANY times before.

Search this forum for:
wine+wow+intel

Your card,if it works at all, will not work well enough to really run the game. Too slow FPS (unless you like a MAX of 12FPS..usually just 1-2), missing graphics, and many other issues. Most of the time, WoW won't even launch (as you have noticed). It has to do with both a poor OpenGL hardware in the Intel chip itself, *and* the drivers.

As I said before:
[COLOR="Red"]Older Intel Graphics Chip **_WILL NOT RUN WoW IN WINE[/COLOR]_**.

The VERY newest (Sandy Bridge) Intel graphics might be able to run WoW/wine, but since a shipping/working version of Sandy Bridge on a usable motherboard hasn't happened yet, we'll have to wait and see.

---

### Post by pedrozs on 2011-03-06
Ok, thanks and sorry for any problem i could cause.

---

### Post by cwwilson721 on 2011-03-06
It's no problem at all.

It just would have saved you ALOT of time if you do a search first, for ANY issue you may have with Ubuntu.

I personally use Google, and type in (in quotes) :
ubuntu+issuename+ubuntuversion

Example:

"ubuntu wine wow intel 10.10"

The first result I get is [http://ubuntuforums.org/showthread.php?t=1649577](http://ubuntuforums.org/showthread.php?t=1649577) 
Which happens to be right here in the forum.

If I had an issue with a mouse pointer, I'd search
"ubuntu mouse 10.10"

Makes life a ton easier. About the only time it won't help is if you have a very obscure, never-before-seen issue, which is extremely rare, or right after a major OS upgrade (Like 5 minutes after 11.04 comes out, as an example).

Google=Happy Linuxing!

---

