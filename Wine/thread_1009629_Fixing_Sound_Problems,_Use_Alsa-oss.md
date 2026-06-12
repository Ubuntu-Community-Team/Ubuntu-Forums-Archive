---
title: "Fixing Sound Problems, Use Alsa-oss"
date: 2008-12-12
forum: Wine
---

### Post by Ng Oon-Ee on 2008-12-12
Hi all,

I've seen a lot of posts on Audio problems, where everyone seems to recommend setting output to ALSA. Though this might work in *some* cases, it really depends on whether you have hardware-mixing for your soundcard, which a lot of people don't, seemingly (myself included, and this laptop is almost new).

This is the sort of problem pulseaudio was added to Ubuntu to solve (and ESD before it), however Pulse itself prefers ALSA output from apps such as Wine. Wine itself works much, much better with OSS output (no choppiness etc), but this is hard-coded (I think) to grab control of your sound device, hence it either fails if Pulse is currently playing or succeeds and blocks off access to sound from all other apps (Rhythmbox, Amarok, Firefox, etc.).

The solution is pretty simple, the alsa-oss package. Just search for it in synaptic, or install with:-
```
sudo apt-get install alsa-oss
```

Then, run your app using the following:-
```
aoss wine <executable_name>.exe <options>
```

Just add 'aoss' in front of wine. So, for example, if you use different bottles, you might use:-
```
env WINEPREFIX=/home/<your_name>/<folder_where_your_bottle_is_stored> aoss wine .....
```
where the .... indicates whatever other options you've used before.

Give it a try, works flawlessly for me.

If you're on 64-bit, wine is 32-bit, so instead you need to install the 32-bit aoss. Instructions have been posted in [this thread.]("http://ubuntuforums.org/showthread.php?t=983861")

---

### Post by jpkotta on 2008-12-12
PulseAudio provides a similar utility, padsp, found in the pulseaudio-utils package.  I haven't tested it with Wine though.

---

### Post by Ng Oon-Ee on 2008-12-12
> **jpkotta said:**
> PulseAudio provides a similar utility, padsp, found in the pulseaudio-utils package.  I haven't tested it with Wine though.

I'm aware of that utility, and probably should have mentioned it. It did not work with Wine somehow, when I tried it a month back. Which is why I looked at alsa-oss.

Thank you for your feedback.

---

### Post by networm1230 on 2008-12-12
this might be due to the bios (Input/Output System) not recognizing you sound card. you may wont to try up dating  your bios. in the bios there is a sitting plug/play mack that what this dos is any device that is plug in is would recognizing that sound card. if your motherboard and bios haves a onboarde video/audeo select you may wont to change this setting. 

for example: if you sound card is pci or agp you may want to change it to ypu card type all so look at the cable connections the hardware side all so try changing sound settings and test theme out when you are testing the sound you should hear a high pitched noise if you hear that that means that you sound is working right. after testing restart your computer and your sound should work

I hop this helps

note. update all drives

---

### Post by Ng Oon-Ee on 2008-12-12
I'm not exactly sure whether you're replying to my thread. I'm posting a solution, that works for me, and AFAICS I have not indicated that my sound card is in any way not working. Perhaps you posted in the wrong thread?

---

### Post by Konj on 2008-12-12
Hi, thanks for posting this. I'm trying to apply this to my Warcraft sound problem, but I don't understand what 'bottles' are, and I'm not sure how I should go about applying this solution.

My Warcraft III loader is in C:/Games/Warcraft III/w3l.exe

How would I load this in Wine with alsa-oss enabled? Thanks in advance.

---

### Post by Ng Oon-Ee on 2008-12-12
Okay, short Wine tutorial =).

Wine is kept in bottles, after all. So, 'bottles' in the computer-Wine context 'keep' a Wine installation. You can think of each bottle as containing a complete install of Windows (or, to be technical, of the Windows API). Actually, the bottle itself is just a folder in your file-system, which contains your drive_c, a dosdevices folder which contains symlinks which you've created, and your system and user registry files.

The reason Wine does it this way is that you may want to set up your installations differently. For example, say app A needs a particular version of Windows (95 for instance) but App B needs Windows Vista. With separate bottles, each has its own set of settings, so this is not a problem. Heck of a lot easier than running winecfg to change the windows version everytime you want to run either app.

This is most useful (IMO) for keeping separate apps that you already have working, so that installing your fourth App won't mess with the configuration for your earlier working apps.

Anyway, the default bottle is in "/home/<your_username>/.wine". If you didn't understand what I just typed, its 99% certain that you're using that. If you don't specify a bottle, that is where wine will by default execute. So, I'd recommend you do this:-

```
aoss wine "C:/Games/Warcraft III/w3l.exe" -opengl
```

The opengl is because unless you have a very good rig, trying to run WC3 in directX mode will drop your FPS below playable. You can add WINEDEBUG=-all before aoss for a bit of a speed boost (just turns off debug information, not a big deal though).

---

### Post by Konj on 2008-12-13
Ah okay, thanks for that. It's just the env WINEPREFIX... thing that threw me off. Well it didn't seem to fix the choppy sound but thanks anyway.

---

### Post by networm1230 on 2008-12-13
yes ops sorry for that mistake sorry if i confused anyone wrong post

---

### Post by Ng Oon-Ee on 2008-12-13
> **Konj said:**
> Ah okay, thanks for that. It's just the env WINEPREFIX... thing that threw me off. Well it didn't seem to fix the choppy sound but thanks anyway.
Sorry to hear that didn't work out for you. You may want to consider the possibility that its a problem with your Pulse setup. Search these forums for a couple of guides on setting up Pulse properly, markbuntu's one is particularly good, for example. One quick way to find out if pulse is screwing you over is to:-
```
killall pulseaudio
```
and then run your app. If it works fine, then try to fix your Pulse settings.

@networm1230 - no problem, thanks for clearing it up.

---

### Post by networm1230 on 2008-12-13
> **Ng Oon-Ee said:**
> Hi all,

I've seen a lot of posts on Audio problems, where everyone seems to recommend setting output to ALSA. Though this might work in *some* cases, it really depends on whether you have hardware-mixing for your soundcard, which a lot of people don't, seemingly (myself included, and this laptop is almost new).

This is the sort of problem pulseaudio was added to Ubuntu to solve (and ESD before it), however Pulse itself prefers ALSA output from apps such as Wine. Wine itself works much, much better with OSS output (no choppiness etc), but this is hard-coded (I think) to grab control of your sound device, hence it either fails if Pulse is currently playing or succeeds and blocks off access to sound from all other apps (Rhythmbox, Amarok, Firefox, etc.).

The solution is pretty simple, the alsa-oss package. Just search for it in synaptic, or install with:-
```
sudo apt-get install alsa-oss
```

Then, run your app using the following:-
```
aoss wine <executable_name>.exe <options>
```

Just add 'aoss' in front of wine. So, for example, if you use different bottles, you might use:-
```
env WINEPREFIX=/home/<your_name>/<folder_where_your_bottle_is_stored> aoss wine .....
```
where the .... indicates whatever other options you've used before.

Give it a try, works flawlessly for me.

If you're on 64-bit, wine is 32-bit, so instead you need to install the 32-bit aoss. Instructions have been posted in [this thread.]("http://ubuntuforums.org/showthread.php?t=983861")

I have that problem to when i am running two audio/video progerm it cuts off my sound completely and i have to re start my computer go get sound back

---

### Post by Ng Oon-Ee on 2008-12-13
I'd suggest looking for HOWTOs on setting up Pulse properly. That should fix the issues. There are 2 good ones here on ubuntuforums that I'm aware off.

---

### Post by networm1230 on 2008-12-13
Ng Oon-Ee = thanks for ed vis on fixing me sound problem. It alive!! um.. I mean the sound work thanks

---

### Post by Ng Oon-Ee on 2008-12-13
> **networm1230 said:**
> Ng Oon-Ee = thanks for ed vis on fixing me sound problem. It alive!! um.. I mean the sound work thanks
You're welcome. Use this forum for all its worth, I've solved almost all my problems here (Ubuntu-related of course, doubt relationship and job problems are dealt with)

---

