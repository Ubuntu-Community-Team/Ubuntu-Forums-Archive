---
title: "Monitor Resolution Issue (Generic, not Ubuntu-specific)"
date: 2011-09-11
forum: The Cafe
---

### Post by navneeth on 2011-09-11
[I thought I would post this here since I didn't want register at some other tech forum for a single post.]

Hi there. I have a Samsung SyncMaster 933 which was running at 1360x768 resolution since installing Maverick, until yesterday. This is the case with both Ubuntu (10.10) and the XP installation in the dual-boot. This happened once before, maybe a couple of weeks ago, but it set itself right somehow almost immediately. 

The Monitor Preferences window does not recognise my monitor and is shown as unknown. Despite the fact that the correct resolution (1360x768(16:9)) and refresh rate (60 Hz) are shown, I still see one inch-wide black bars on either side of the display.

Yesterday, while searching for solutions, I came across the **xrandr** command in one of the threads here. Running it almost magically brought back the correct resolution, but after a restart of the computer this morning, things are back to square one.

I've update my graphics driver from the Intel site using their online driver update utility. (I did this while booted into XP; I suppose I won't need to this separately for each OS.)

Here are some other pertinent information that may be of use.

**[Driver details obtained after installing update]**

```
navneeth@home:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
```

```
navneeth@home:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9

```


I hope someone here can help bring this thing back to normal.

Regards,
Navneeth

---

### Post by Copper Bezel on 2011-09-11
Actually, Absolute Beginner Help isn't technically OS-specific, and this is specific enough in any case to post in a any of a handful of places in Support.

> I've update my graphics driver from the Intel site using their online driver update utility. (I did this while booted into XP; I suppose I won't need to this separately for each OS.)

The drivers are separate, but so is the way they're handled. On Ubuntu, they're going to be the current version anyway.

> Yesterday, while searching for solutions, I came across the xrandr command in one of the threads here. Running it almost magically brought back the correct resolution, but after a restart of the computer this morning, things are back to square one.
xrandr doesn't change your settings, just the display settings in the current session. If you got it working, it might be easiest to save what you did and put the xrandr command with those options in your Startup Applications.

---

### Post by navneeth on 2011-09-11
> **Copper Bezel said:**
> xrandr doesn't change your settings, just the display settings in the current session.

Okay, maybe I'm confusing co-incidence with causation, but it was almost instantaneous. And I think -- though I could be mistaken -- there was no output, it returned to the shell on the next line.

Anyway,

>  If you got it working, it might be easiest to save what you did and put the xrandr command with those options in your Startup Applications.

After restart, I tried the command again, and it didn't do anything apart from spit out the stuff I posted earlier. :(

---

### Post by navneeth on 2011-09-11
The weirdest thing just happened: For the 105,432nd time I opened Monitor Preferences, the screen went blank for a moment, but when it came back, my monitor was correctly identified, the resolution was wrongly set, but I changed it to the correct one and the display seems normal now! :confused: I'm confused. Happy, but confused nevertheless. Maybe it's a cable fault?

---

### Post by realzippy on 2011-09-11
> **navneeth said:**
> Maybe it's a cable fault?
+1,if it is platform independent,then error is on the monitor side.
Tighten screws,change cable...

---

### Post by navneeth on 2011-09-11
> **realzippy said:**
> +1,if it is platform independent,then error is on the monitor side.
Tighten screws,change cable...

I haven't tried changing cables, but the existing ones have been unplugged and plugged back in a few times without avail.

---

### Post by mips on 2011-09-12
Try this [http://ubuntuforums.org/showthread.php?t=1805674](http://ubuntuforums.org/showthread.php?t=1805674)

For windows install the Samsung monitor driver [http://www.samsung.com/africa_en/support/main/supportMain.do](http://www.samsung.com/africa_en/support/main/supportMain.do)

---

### Post by navneeth on 2011-09-12
> **mips said:**
> Try this [http://ubuntuforums.org/showthread.php?t=1805674](http://ubuntuforums.org/showthread.php?t=1805674)

For windows install the Samsung monitor driver [http://www.samsung.com/africa_en/support/main/supportMain.do](http://www.samsung.com/africa_en/support/main/supportMain.do)

Thanks, but that didn't help. :( Oh, and things are back to being ugly again. As I suspected, and as realzippy seconded, this is likely a purely monitor-based issue. Unlike most other problems of this type, this did not happen after a fresh install, but nearly a year after the OSs had been installed.

---

### Post by navneeth on 2011-09-13
Yup! It's a cable issue. A borrowed DVI cable has put the issue to rest. Both Ubuntu and Windoze displayed correctly when I used that.

Thanks for all the help.

---

