---
title: "problem starting World of Warcraft on it's own X"
date: 2010-08-23
forum: Wine
---

### Post by Zirts on 2010-08-23
Hi,

I recently read this page here: WorldofWarcraft/Troubleshooting

And found this article:
> 
**ATI / AIGLX**
Please be aware that People using AIGLX may experience low framerates.

As a test, one can do this:
```

 /etc/init.d/gdm stop          # this will shutdown your X Server!
 startx `which wine` WoW.exe   # start X with WoW as "Desktop Manager" (might look funny :])

```
Running AIGLX and another X Server running wow will probably crash the box, so please dont try that or make sure you can ssh to the box.

My personal experience is ~5-10 FPS with wow inside aiglx, while 25-30 fps running on a "standalone X Server"
Now what I did: 
I made a executeable text file to /home/kaspar/Töölaud/
File name: lol
Contents:
```

startx `which wine` Wow.exe

```
Now I made a copy of the Wow.exe to wines system32 folder, otherwise the script didn't work.

Ok, now I start killing the X, Ctr + Alt + T, and I type in 
```

sudo /etc/init.d/gdm stop

```
It asks for my password, I give it to him, then it informs me that I can use that script in other way too but non-the-less, it kills the X, now I see a black screen with a lot of text on it as I'm using the "KMS with a Radeon card" function.

Ok seems cool, I managed to get here, now I press the combo: Ctrl + Alt + F2 and on that screen I log in with kaspar, enter my password and I'm ready to start Wow.exe with X.
```

cd /home/kaspar/Töölaud/

./lol

```
It loads shitload of stuff, gives a small error wich it says is NP for X, and moves on and now comes the part I need help with:

```

err:module: import.dll Library DivxDecoder.dll (Wich is needed by L"C:\\windows\\system32\\Wow.exe") not found

err:module: Initialize Thunk Main exe initialization for L"C:\\windows\\system32\\Wow.exe" failed, status c0000135

waiting for X server to shutdown ddxSigGiveUp: closing log

XIO: fatal IO error 25(Inappropriate ioctl for device) on X server ":0.0"

after 573 requests (520 known processed) with 0 events remaining

```
And this is the nice little error that is keeping me away from playing World of Warcraft.

Is there anyway to fix this?
Just tell if anymore information is needed about my PC and it's settings.

Regards,
Zirts

---

### Post by HeadHunter00 on 2010-08-23
I know that this is totally off topic, but how do I start firefox in its own X?

---

### Post by HeadHunter00 on 2010-08-23
actually, I figured it out. I have wow myself and tried that command, but it made things worse for me.  I have intel gma965.

---

### Post by Zirts on 2010-08-23
Ok, but I would still like to know what couses thoes errors and how can I fix them...

---

### Post by Zirts on 2010-08-25
Bump, anyone knows?

---

### Post by HeadHunter00 on 2010-08-28
why not just try```
sudo startx wine /home/[username]/.wine/drive_c/[wow_directory]
```

---

### Post by Zirts on 2010-08-28
That gives me a constant stream of errors: No protocol specified
After that I have to switch to another one of thoes text thingies and make a restart as the error wont stop.

---

### Post by VinisLentoje on 2010-09-01
Hmmmm... I might be able to help You there.

I some time ago, I found an utility to made to launch games on a separate X session. I used it a couple of times on games running natively on linux. But, after reading this post, I thought of trying it with games running on wine. Since the topic is about WoW, and I have it on my computer right now, I tried running it, and it worked like a charm. Also, I tested, if I could could run the game without turning GDM off. Yes, It works even like this, but if I switch back to the screen where the GDM is running, wine time-outs on that X screen it is running and crashes. But I guess It can be used if one does not want to turn off all the stuff that may be laying around open on the desktop.
I don't know, if I should just attach it, of link to one of the download sites, where it is available for download. I guess, I'll just do both.
Attachment: [ATTACH]168145[/ATTACH]
Download: [link]("http://linux.softpedia.com/get/Utilities/Xgame-19837.shtml")

Hope that helps

If You need any info in configuring, please ask, 'cause I'm too lazy to write it right now. And since You might possibly do everything correctly....

---

### Post by Zirts on 2010-09-01
Thanks alot VinisLentoje!!!   Worked like a charm.

---

