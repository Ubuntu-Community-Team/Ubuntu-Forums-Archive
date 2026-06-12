---
title: "Can't play the guitar and listen to a youtube video"
date: 2013-06-24
forum: Ubuntu Studio
---

### Post by rva1945 on 2013-06-24
Hi:

While running Rakarrack or Guitarix in U 12.04 (and having tweaked /etc/pulse/default.pa file to allow for Alsa and Jack runnnig together), I can listen to a mp3 being played in VLC or Movie Player, provided I don't move the mouse and there is no read/write disk activity, otherwise the sound "breaks", as if the processor can't cope with both tasks (processing the guitar sound and running other processes); but if I want to play the guitar while watching a youtube video, it's impossible. I don't think the problem is related to youtube, but with processing a video while downloading the browser cache at the same time.

Do I have any way to fix this issue? The (old) PC has 1GB of RAM, do you think that by having 4GB things will improve?

Thanks

---

### Post by jejeman on 2013-06-24
RAM is not the issue, the CPU power is. Adobe flash eats CPU time - just like that, and JACK also...

Download the video first, and watch it in VLC via JACK.

To play guitar you need RT and lower latency. Both are not good for watching flash video, simply it is not made for that, adobr flash is not JACK compatible.

Setting the PA config to  "allow for Alsa and Jack runnnig together", (besides the fact that ALSA is already runing all the time), is not the way to go - too much layers --> bad performance. Skip the PA to strip off the layers. Configure directly ALSA in .asoundrc, something like
```
pcm.rawjack {
    type jack
    playback_ports {
        0 system:playback_1
        1 system:playback_2
    }
    capture_ports {
        0 system:capture_1
        1 system:capture_2
    }
}

pcm.jack {
    type plug
    slave { pcm "rawjack" }
    hint {
        description "JACK Audio Connection Kit"
    }
}

pcm.!default {
    type plug
    slave { pcm "rawjack" }
}
```But again, adobe flash is not made for RT. And this configuration needs JACK to be running non-stop.

And 
"Can't play the guitar and listen to a youtube video "
of course you can't, that is normal. ;)

---

### Post by rva1945 on 2013-06-24
OK, lets forget about watching the video online, in fact I tried downloading it first to the cache and then opening it in VLC but the problem remains. Anyway I found the mp3 so no need for the video, but again, there are noises, like clicks, as if any load in the CPU puts noise in the line, which Rakarrack "does a good job" in amplifying it.

Where is [COLOR=#000000].asoundrc? Is it a folder? I didn't find it!

Thanks[/COLOR]

---

### Post by jejeman on 2013-06-25
What is your CPU?
What is your JACK configuration?
What is your kernel?
give
```
cat /proc/cpuinfo | grep name
```
```
cat .jackdrc
```
```
uname -r
```
About .*rc files

In case of 99.90% dot files are in your $HOME directory. 
In case of 99.90% *rc files are in your $HOME directory.
In case of 99.90% when absolute path is not given it is in your $HOME directory.
"rc"(runcom) (in a doted) file name means that it is some kind of configuration file. Dot file is hidden file, the dot hides it. Sometimes they exists, sometimes the user needs to create it.

Let's leave the .asoundrc file for now, and try to make JACK work better.

---

### Post by rva1945 on 2013-06-25
I went to Home directory, ctrl+h to see hidden files but to no avail. In fact I tried 
cd ..
(then once in Home directory)
sudo gedit .[COLOR=#000000].asoundrc
and a new empty file was created in gedit (I closed without saving, anyway).

Tonight at home I will pass you the data about the hardware. As for the noises, I'm using a plug adapter for connecting the guitar to the line-in, I think I should use the normally shielded cable from the guitar and and adapter just at the line-line-in.

[/COLOR]

---

### Post by jejeman on 2013-06-25
Never use "sudo" with GUI applications, for GUI always use "gksudo".
No reason to use sudo for files in $HOME directory, it is USER directory NOT system directory. All files in it has to be USER's.
It is not ..asoundrc, but .asoundrc.
As I said, the file does not exists, it needs to be created.

---

### Post by rva1945 on 2013-06-25
Here goes the requested information:

robert@rvalinuxdesktop:~$ cat /proc/cpuinfo | grep name
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz

robert@rvalinuxdesktop:~$ cat .jackdrc
/usr/bin/jackd -P1 -dalsa -dhw:0 -r22050 -p16 -n2

robert@rvalinuxdesktop:~$ uname -r
3.2.0-48-generic-pae

Now I don't know what is going on, but I can't listen to a mp3 decently, it slows down, "breaks" (sorry, English is not my mother's language so maybe I can't find the exact words or phrase to describe this problem), and when running Rakarrack there is a lot of background noise (no guitar connected) when turning the DistBand on.

---

### Post by jejeman on 2013-06-26
Well, not that bad CPU
but
JACK command is strange.
why 22050 sample rate? To low period, just 16.
Try something more conventional, like
```
/usr/bin/jackd -dalsa -dhw:0 -r48000 -p256 -n2
```

Why generic kernel? You don't have Ubuntu Studio installed, just plain Ubuntu?

---

### Post by rva1945 on 2013-06-27
I tried reducing the sample rate to improve the performance, but it didn't work.

Tonight I will add another GB of RAM for a total memory of 2GB.

As for the operating system, I'm using Ubuntu 12.04 32 bits.

---

### Post by jejeman on 2013-06-27
More RAM will not help you.
You need lowlatency kernel, also check if you are in audio group
give
```
groups
```

---

### Post by rva1945 on 2013-06-27
OK, I will give that information later at home, but I can tell you now that it has been working ok and with just 1.5 msec of latency, and things suddenly turned into a nightmare.

---

### Post by jejeman on 2013-06-27
Well, with that kind of CPU and without lowlatency kernel, I doubt about 1.5ms latency. That is too low.
I'm on 4ms latency, but with i5 CPU and lowlatency kernel. I don't remembre if I tried to go lower, but I don't really need any lower than that.

---

### Post by rva1945 on 2013-06-27
"Playing" with Qjackctl parameters (Setup) I reduced the latency to around that value. I don't note any difference (I mean, no delay) comparing to playing with the "real" amplifier (a 10W Fender Frontman).

---

### Post by cub on 2013-06-27
Maybe a longshot, but wasn't there an update of Firefox recently? Did the issue begin after that update perhaps?

---

### Post by rva1945 on 2013-06-27
My problems began last Monday, do I have any way to see if there was an updateduring the Sunday-Monday period?

---

### Post by cub on 2013-06-27
You should be able to see that in Ubuntu Software Center and under History. I got my Firefox update yesterday, but that might be just that I didn't run apt-get update before that this week.

---

### Post by rva1945 on 2013-06-29
groups:

robert adm cdrom sudo dip plugdev lpadmin sambashare

The guitar (and with the same cable) works fine plugged to the laptop, but with the desktop PC, when I strum the strings it sounds as if there is a Geiger counter detecting radiation. I tried installing a 64-bit Ubuntu 12.04 and adding RAM, thinking that the problem was related to performance but no, seems as if there is something wrong with the audio circuitry.

---

### Post by jejeman on 2013-06-30
> groups:
```

robert adm cdrom sudo dip plugdev lpadmin sambashare
```You are not the member of "audio" group. In order to have RT audio you need to be. Add your self to audio group.

---

