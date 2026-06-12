---
title: "jerky graphics playing World Of Warcraft Ubuntu 9.10 through Wine."
date: 2009-12-03
forum: Wine
---

### Post by scrypt on 2009-12-03
Hi All.

I have managed to get World of Warcraft running on my Dell Studio 1737 laptop with an ATI 3650HD graphics card.

I used this site as my main point of reference :

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I have a dual boot system with Windows 7 and ubuntu 9.10 (Karmic)
I have used Wine to play WoW by mounting my Windows 7 Partition in Ubuntu and then creating a link on my desktop to launch wow through wine.

I have 2 issues though...

The first is that I have slightly jerky graphics.

I have had a good read of various sites on how i might be able to rectify this but I have not been able to find the correct fix.

Is there a relatively simple way to fix this that anybody here knows of??

My second issue is I have NO sound.

Does anybody know of A fix for this issue too?

I have been using ubuntu for quite some time so i do have some experience of tweaking ubuntu and its settings.

I would appreciate if somebody could help e out with this?

---

### Post by zkriesse on 2009-12-04
[http://appdb.winehq.org/](http://appdb.winehq.org/) Check that out...might help you.

---

### Post by polpak on 2009-12-08
For jerky graphics, I'd double check that your video cards 3d drivers are installed properly, and that you're running WoW under it's openGL rendering engine.

For sound, you may need to configure WoW (and by that I mean wine) to use the pulseaudio wrapper for OSS. To do this, run winecfg after setting the appropriate WINEPREFIX env variable (if any) and enable the OSS sound engine under the Audio tab. Then when you run wow, prefix it with the padsp command.

e.g.

```
WINEPREFIX=/path/to/winedir padsp wine /path/to/winedir/drive_c/"Program Files"/"World of Warcraft"/Wow.exe
```

---

### Post by themusicalduck on 2009-12-08
The sound problem is strange. Does this happen for all wine programs?

Also have you disabled compiz? That can make the graphics run slowly.

---

### Post by falconindy on 2009-12-08
Jerky graphics? Yeah... that's just how a lot of people are in WoW.

During the month I played WoW on Linux I wrote a [guide]("http://www.aggarrosh.com/forums/viewtopic.php?f=33&t=140") which was essentially a compilation of everything I found on the web in order to get it running smoothly. It covers installation, graphics, sound, and Ventrilo. A lot of it you've likely already seen. Some, I'm not sure you have -- the sound bit in particular.

---

### Post by stpieraf on 2009-12-31
I just installed Ubuntu for the first time, and am also learning about how to get WoW working.

One thing I suggest for jerky graphics is, believe it or not, check your keyboard settings. I'm not at my machine now, but turning of the repeating key presses when holding down a button did wonders for me. I noticed when I started moving that my mount would "stutter" every so often. Turned that off, and it's gone.

Although, you now have to press every delete or backspace key, you can't just hold it down. However, movement with keys does work as long as you hold it down. It's confusing the heck out of me. 

Hope this helps!

---

