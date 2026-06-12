---
title: "Ardour - stops all system sound"
date: 2011-08-28
forum: Ubuntu Studio
---

### Post by orrymr on 2011-08-28
Hi all,
I've got a problem with Ardour. My system's sound works just fine until I start up Ardour. As soon as I do, all my sound just disappears :confused:
If any one has any ideas why this could be happening, please let me know,
thanks

---

### Post by sgx on 2011-08-29
> **orrymr said:**
> Hi all,
I've got a problem with Ardour. My system's sound works just fine until I start up Ardour. As soon as I do, all my sound just disappears :confused:
If any one has any ideas why this could be happening, please let me know,
thanksHi, ardour is probably starting jackd when it starts up.
This can block other sound systems from starting. Some people have
pulseaudio in autostart, or a web browser that grabs system sound, and then have trouble starting jackd. You can run the command

ps ux 

to see what is running, and terminate the undesired process with the
killall command, followed by the exact name of the process

killall jackd 

This topic shows how to deal with an unwanted pulseaudio,
without removing it.

[http://rivendell.tryphon.org/wiki/Ubuntu_-_No_sound/sound_card_in_Rivendell_after_setup](http://rivendell.tryphon.org/wiki/Ubuntu_-_No_sound/sound_card_in_Rivendell_after_setup)

Cheers

---

### Post by orrymr on 2011-08-31
I tried killall jackd. Ardour still stops all sound. Also, that command seems to have corrupted Hydrogen or something like that. Not really sure what's going on.

---

### Post by sgx on 2011-08-31
> **orrymr said:**
> I tried killall jackd. Ardour still stops all sound. Also, that command seems to have corrupted Hydrogen or something like that. Not really sure what's going on.
Hi, hydrogen and many other audio apps use jackd, so if you stopped it, restart it to use them. Check each apps setting menus to see what
options show up.

The jackd gui, qjackctl, can do that automatically, if you mark the tick box in it's preferences.

qjackctl how-to page

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

Ardour probably starts jackd by default. If you want a music player that connects to jackd, try aqualung, or install the jackd modules for xmms, xine, or vlc. These may require manual connections in qjackctl, but can play audiofiles, while you
play instruments, and record them all in ardour or timemachine.

Cheers

---

