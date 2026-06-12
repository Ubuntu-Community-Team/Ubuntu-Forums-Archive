---
title: "gtk-RecordMyDesktop won't recognize my sound card."
date: 2008-07-18
forum: Ubuntu Studio
---

### Post by penguindrive on 2008-07-18
When I try to record it returns this error:

RecordMyDeskTop has exited with satus: 768
Description:Could not open/configure sound card.

I made sure I had my sound device(a logitech USB mic) sellected.

---

### Post by penguindrive on 2008-07-27
Bump because I need help.

---

### Post by Creative2 on 2008-07-27
could your open  a terminal and test your mic with this command ?
```

rec /tmp/hello.wav ; play /tmp/hello.wav
```

*(press CTRL C to stop recording)

*(you need of sudo apt-get install sox libsox-fmt-all )

---

### Post by penguindrive on 2008-07-27
My mic is not the problem, audacity records it fine.

---

### Post by Creative2 on 2008-07-28
veryt well :

first install 

```
sudo apt-get install sox libsox-fmt-all
```

that should install every library for sox (even oss library very important when one wants record)


Could you write which settings you have used on gtk-record..?
could you use on a terminal only this? :

recordmydesktop 

*CTRL C to stop recording 


at the same time your should use this command in another terminal 
```

 lsof /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/* 
```


then try with audacity :

record your voice and at the same time in another terminal 


```
 lsof /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/* 
```


then report what  lsof /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*  give you 


if you have no time i suggest : xvidcap 

*for settings click with right button (on the name of the file  test000xxxxx on xvidcap interface..)

---

### Post by wingnux on 2008-07-30
"wingnux@wingnux-desktop ~ $ recordmydesktop 
Initial recording window is set to:
X:0   Y:0    Width:1152    Height:864
Adjusted recording window is set to:
X:0   Y:0    Width:1152    Height:864
Your window manager appears to be Metacity

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device."

"wingnux@wingnux-desktop ~ $ lsof /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*
lsof: status error on /dev/audio*: No such file or directory
lsof: status error on /dev/snd/*: No such file or directory
COMMAND    PID    USER   FD   TYPE DEVICE SIZE  NODE NAME
artsd     6534 wingnux   10r   CHR  252,1      13606 /dev/mixer
tvtime    8267 wingnux    5w   CHR  252,1      13606 /dev/mixer
banshee-1 8501 wingnux   25r   CHR  251,3      13613 /dev/oss/hdaudio0/pcm0"


I'm using OSS4.

---

### Post by Creative2 on 2008-07-31
well i don't know about OSS4 it's clear you have a settings problem 

my recordmydesktop uses oss emulation by alsa driver and it works fine you should search on OSS4 documentation or write to xvidcap forum (uses /dev/dsp so OSS)

anyway you should set your audio device but another time i don't know how OSS4 uses and which name OSS4 give to your audio card 

try to see if this could be to help you 
[http://www.jarre-de-the.net/computing/capture-sound.avi](http://www.jarre-de-the.net/computing/capture-sound.avi)

[NOTE ON GNOME-MIXER THERE IS OSS AND NOT ALSA...]

---

### Post by andr3w on 2009-01-27
> **Creative2 said:**
> well i don't know about OSS4 it's clear you have a settings problem 

my recordmydesktop uses oss emulation by alsa driver and it works fine you should search on OSS4 documentation or write to xvidcap forum (uses /dev/dsp so OSS)

anyway you should set your audio device but another time i don't know how OSS4 uses and which name OSS4 give to your audio card 

try to see if this could be to help you 
[http://www.jarre-de-the.net/computing/capture-sound.avi](http://www.jarre-de-the.net/computing/capture-sound.avi)

[NOTE ON GNOME-MIXER THERE IS OSS AND NOT ALSA...]

lol. Does ANYONE know how to do this????

---

### Post by robinPain on 2010-03-12
1. Click the Advanced button
2. Select the sound-tab
3. In "Device" change "DEFAULT" to "default"
4. It works!

(I am using a logitech USB on 64bit 9.10)

---

### Post by oldmankit on 2010-04-01
> **robinPain said:**
> 1. Click the Advanced button
2. Select the sound-tab
3. In "Device" change "DEFAULT" to "default"
4. It works!


+1
lol :P

---

### Post by pmowry911 on 2010-05-27
> **oldmankit said:**
> +1
lol :P

Wow, This solution works great for 10.04 64-bit as well ;)

---

### Post by kratib on 2010-10-30
The DEFAULT => default trick worked for me too! 
LOL is not strong enough.

---

### Post by TrippMan668 on 2013-02-15
**Solution still works in 2013! **

Thanks again Guys.

 Now I have** "istanbul" **and _**"gtk-recordMyDesktop 0.3.8"**_ Working! Nice.. :mrgreen:
> 
Originally Posted by **robinPain**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8955932#post8955932")                 
                 [I]1. Click the Advanced button
2. Select the sound-tab
3. In "Device" change "DEFAULT" to "default"
4. It works![/I]


---

