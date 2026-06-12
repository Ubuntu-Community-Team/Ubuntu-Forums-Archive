---
title: "Can I install and use Windows 7 or XP in VirtualBox?"
date: 2010-06-05
forum: Virtualisation
---

### Post by Isamtron on 2010-06-05
Hello,

If I install Ubuntu as the single operating system on my machine, will I be able to install VirtualBox and install Windows 7 or Windows XP to use it through Ubuntu?

Thanks.

---

### Post by irv on 2010-06-05
Yes you will be able to do this. In the last version of Ubuntu I did this and it work great, but I only ran WinXP. I believe Win7 will work also. The only reason I am not doing it now is when I ran WinXP in VirtualBox my movies over Netflix would run to slow and even stop.
I now dual boot with Win7 and Ubuntu 10.04 and this is better for me because my bootup time in both Win7 and Ubuntu is about 20 to 30 seconds. So when I want to watch or movie or use Win7 for some reason it only take a minute or so to switch. This  way I have the best of both worlds.
The only time I have a problem is when Win7 installs some updates and it take a long time to go down before I can use Ubuntu again. (By the way over all I think Ubuntu is a little faster booting and going down then Win7, but I have never really timed it).

---

### Post by Isamtron on 2010-06-05
Thanks for the info.

Could you please tell me which application did you use to make the video in your signature?

---

### Post by irv on 2010-06-05
> **Isamtron said:**
> Thanks for the info.

Could you please tell me which application did you use to make the video in your signature?

I thought the best way to tell you was to show you. Here is a little video:
[http://wabasha-server.net/Downloads/recordmydesktop.ogv]("http://wabasha-server.net/Downloads/recordmydesktop.ogv")

The output file from gtk-recordMyDesktop is a ogv file. If you are going to upload them to youtube you need to convert them to avi files to do this you can use a application called WinFF or just run this command in a terminal:
```
mencoder inputfile.ogv -o outputfile.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000

```
Make sure you are in the directory you ogv file is in and it will save the output file to the same place.
Also if it doesn't run make sure you have mencoder installed. The WinFF uses ffmpeg so you need this also. I had some issues with ffmpeg, but I got them fixed. see post 16 in this thread: [http://ubuntuforums.org/showthread.php?t=1500992&page=2]("http://ubuntuforums.org/showthread.php?t=1500992&page=2")
I find this a very useful thing to know and I can send videos to my family by recording my desktop while I have my webcam going, but my voice is not in sync with my lips. Oh well!

---

### Post by Isamtron on 2010-06-05
Thank you SO MUCH.

---

### Post by redcharlie on 2010-06-24
> ...when I ran WinXP in VirtualBox my movies over Netflix  would run to slow and even stop.

I had the same issue, not on a laptop but on a desktop:
Gigabyte ma78gpm-d2sh
Athlon X2 4450e (2.3 GHz dual core "Brisbane")
2GB DDR2 800

On the above hardware I have Ubuntu 9.04, with an XP virtual machine in Virtual Box, with 512MB base memory, 64MB video memory, and AMD-V extensions enabled,

Everything I read indicated I should be able to run Netflix in my VM without any problem.  But when I did playback was very poor, stuttering and stopping so often it was quite unwatchable.

Then I accidentally started up the VM with the "null" audio driver, and noticed that Netflix worked fine, no stuttering or dropping frames (although of course I had no sound).

Googling around, I read that pulseaudio has issues here:
[http://ubuntuforums.org/showthread.php?t=1168194](http://ubuntuforums.org/showthread.php?t=1168194)

Sure enough, switching from pulseaudio to OSS (system->preferences->sounds, change to OSS for "music and movies") did the trick, along with changing the sound driver in the VM to OSS.  Now netflix works great!:guitar:

---

### Post by Peter7K on 2010-06-24
With the latest Ubuntu, using Virtualbox I was able to install Window$ 7 literally flawlessly.  Very impressed, Virtualbox is great!

---

