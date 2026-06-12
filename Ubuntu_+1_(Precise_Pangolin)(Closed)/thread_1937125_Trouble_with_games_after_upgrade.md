---
title: "Trouble with games after upgrade"
date: 2012-03-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry.k on 2012-03-07
I've been using natty since may 2011, and games like FoF, Caster, WoG and Armagetronad worked fine. Recently i switched to precise alpha, and reinstalled all the above games. Armagetronad and frets on fire work fine, but World of goo and caster throw up errors.
Please help me out, coz I really am addicted to WoG and Caster.

wog shows:

```
harry@home-pc:~$ WorldOfGoo
Segmentation fault (core dumped)

It looks like World of Goo crashed! If you need support, please include the
contents of the log file in your problem report.
The log file is stored at: /home/harry/.WorldOfGoo/WorldOfGoo.log
```

the log is attached


Caster seems to have some trouble with libasound, which i tried reinstalling twice after purging. caster shows :


```
harry@home-pc:~/caster-demo$ ./caster-demo
Beginning Setup.
Pre SDL Setup.
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
Segmentation fault (core dumped)
harry@home-pc:~/caster-demo$ ./caster-demo.bin
Beginning Setup.
Pre SDL Setup.
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
Segmentation fault (core dumped)

```

Thanks in advance.

---

### Post by Harry.k on 2012-03-07
Oh, and i use an xorg.conf configured to recognise my intel brookdale graphics card in both natty and precise. The graphics driver i use is mesa glx

---

### Post by zuti on 2012-03-09
I seem to have the same problem with libasound when trying to run The Binding of Isaac. Would be nice to get some sound out of the game.

---

### Post by Harry.k on 2012-03-13
Experimental Libasound seems to be the problem. If someone could tell me how to downgrade

---

### Post by nothingspecial on 2012-03-13
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by Harry.k on 2012-03-14
Bump

---

### Post by madeinfamous on 2012-03-15
allo Harry.k!

for world of goo...

if it doesn&#8217;t start, error log files bla bla bla...

gksu gedit /opt/WorldOfGoo/properties/config.txt

@ line 56: 

<env name="SDL_AUDIODRIVER" value="auto" overwrite="true" />

change &#8220;auto&#8221; to &#8220;dsp&#8221;:

<env name="SDL_AUDIODRIVER" value="dsp" overwrite="true" />


the game launch and play fine, but with no sound, i&#8217;ve tried different option, but... it&#8217;s playable! 

have a nice gaming day!

[https://docs.google.com/document/d/1BMCkrz00376OXNR-tZ5s4Y8JB5gUDXzBxdcuo8ql1FU/edit](https://docs.google.com/document/d/1BMCkrz00376OXNR-tZ5s4Y8JB5gUDXzBxdcuo8ql1FU/edit)

---

### Post by Harry.k on 2012-03-15
Thank you, madeinfamus. Although, i found a workaround. Copy the pulse.conf.so thing from the libasound deb package to /etc/alsa32-lib and running sudo .//opt/WorldOfGoo/WorldOfGon.bin32 
the sudo is needed if you use multiple mice for multiplayer co-op. The worldofgoo command still doesnt work. I made a launcher for the .bin32 file. I'll post more clear instructions when i get back to my pc

---

### Post by madeinfamous on 2012-03-29
allo again!

World of Goo Ubuntu 12'04 amd64 (i386 also)

if it doesn’t start, error log files bla bla bla...

download these 3 files: 
[http://2dboy.com/TopSecretTransfer/linux-libs64/](http://2dboy.com/TopSecretTransfer/linux-libs64/)
or: 
[http://2dboy.com/TopSecretTransfer/linux-libs32/](http://2dboy.com/TopSecretTransfer/linux-libs32/)

and replace those in 

gksu nautilus /opt/WorldOfGoo/libs64/
or
gksu nautilus /opt/WorldOfGoo/libs32/

AND VOILÀ!!! BRAVO, BRAVO, ENCORE!!! : )

---

### Post by Harry.k on 2012-03-30
Aah, that is much easier than copying the files from the .deb package. Thanks, madeinfamous. Do you work for 2dboy?

---

