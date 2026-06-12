---
title: "Hulu Desktop for Linux!"
date: 2012-07-14
forum: The Cafe
---

### Post by Zerocool Djx on 2012-07-14
[http://www.hulu.com/labs/hulu-desktop](http://www.hulu.com/labs/hulu-desktop)

Ubuntu supported! :popcorn:

---

### Post by phosphide on 2012-07-14
This is awesome!

Except it doesn't work. It doesn't seem to like the Chrome flash player.

Edit: Tried to download the flash plugin for Mozilla and run. Program still doesn't run for some reason.

---

### Post by papibe on 2012-07-14
Thanks for the heads up!

Even thou I find the browser experience satisfactory, from the couch (10-foot-interface), it is difficult to use (even with nosquint pluggin).

Downloading it...

Regards.

---

### Post by Copper Bezel on 2012-07-14
Yeah, that's been there for a bit. I was using it on my Ubuntu HTPC (which was great, given there aren't many other services available to an Ubuntu HTPC) in 2009.

---

### Post by phosphide on 2012-07-14
Some of you might need to see the thread titled "huludesktop linux fail"

[http://www.hulu.com/discussions/19](http://www.hulu.com/discussions/19)

I'm in the process of reverting back my flash plugin, hopefully then it works.

Edit: Yup, follow the instructions in that thread and it works. I'm using 12.04.

---

### Post by papibe on 2012-07-14
It works, but on a small screen :mad:

... and it crashes repeatedly. 

I submitted a bug report:
> Either maximize window, or trying to go fullscreen (Ctrl+F) crashes Hulu Desktop.

No browser or other flash application open.

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

$ uname -a
Linux vaughan 2.6.32-41-generic-pae #91-Ubuntu SMP Wed Jun 13 12:00:09 UTC 2012 i686 GNU/Linux
Regards.

---

### Post by phosphide on 2012-07-14
The video quality isn't perfect, but the fact they are even trying suggests they will be getting my money.

---

### Post by Copper Bezel on 2012-07-15
I don't think the companies that do support Linux understand how Linux works - aside from Google and (almost incidentally) Dropbox, of course. This seems like the same situation with Amazon's mp3 downloader - they expect to release the software once and never have to maintain it for changes in the underlying OS. 

Then again, they were both released in Ubuntu's first brush with popularity during the netbook phase, too. Maybe they felt they were planning ahead in case Ubuntu went somewhere and ultimately decided it hadn't.

---

### Post by phosphide on 2012-07-15
Whats wrong with the software Hulu created?

---

### Post by mr john on 2012-07-15
Only available in the United States = Fail. What part of WORLD WIDE Web do they not understand?

---

### Post by Copper Bezel on 2012-07-15
[QUOTE=phosphide]Whats wrong with the software Hulu created?[/QUOTE]
Well, it used to take a hack to point it to the Flash player in the first place, and now it apparently can't do full-screen. Which, to be fair, is also broken in Google's packaging of the Flash plugin on Linux, but that's unrelated.

---

### Post by helpdeskdan on 2012-07-28
In the sincere hopes that this helps somebody:  (Not trying to hijack) 

I'm using huludesktop successfully on 12.04 Xubuntu.  It used to use it on 10.04, where it was pretty solid.  (Well, sometimes it would not update thumbnails and you had to restart, but it never crashed)   I may recommend the following suggestions:

For starters, I’m told you need an older flash: 11.1.  You can get it here:
[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

But more specifically, get this:
[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip)

Large download, you one want one file out o fit.  Open it up - in the 32 or 64 bit (depending on your OS) folder look for the tar file and open that.  Grab the libflashplayer.so file and save it to your home dir. 

edit .huludesktop and add this:
[flash]
flash_location = /home/helpdeskdan/libflashplayer.so

substituting your user for helpdeskdan.  Should run now.  (Does not seem to on flash 11.2)

On the subject, a couple other suggestions.  First, 640x480 - plays much better on my ancient jalopy.  Second, unclutter - hide that pesky mouse that shows up from time to time.  Third, set the alsa sound level  - but that's completely optional.  I launch huludesktop with a bash script, as such:

/usr/bin/xrandr -s 640x480
/usr/bin/unclutter -visible -root -idle 1 -jitter 3 & 
# /sbin/alsactl -f /home/dan/asound.state restore
/usr/bin/huludesktop
/usr/bin/killall unclutter
/usr/bin/xrandr -s 1600x1200

I then edited my .huludesktop to look as such:
[display]
fullscreen = TRUE
width = 637 
height = 478 
pos_x = 0 
pos_y = 22

Cheap $10 generic “PC remote” from Amazon, and I was good to go.  Hulu runs, and it runs much better than before.

---

### Post by donkyhotay on 2012-07-28
> **mr john said:**
> Only available in the United States = Fail. What part of WORLD WIDE Web do they not understand?

They understand, but it's the same thing that causes them to use DRM.

---

### Post by upjeeper on 2012-07-28
can anyone comment on features as compared to Windows?

---

### Post by Warpnow on 2012-07-28
> **upjeeper said:**
> can anyone comment on features as compared to Windows?

Its adobe air. Its the same on Linux and Windows, but runs smoother on windows due to flash.

---

