---
title: "JACK Sample Rate Stuck at 16000 Hz, no matter what setup # says..."
date: 2009-09-24
forum: Ubuntu Studio
---

### Post by Zoey.Marie on 2009-09-24
Can someone help me figure this one out, because I've been trying... 

I have the sample rate set at 48000 in the JACK setup, but when I run it, it says that it's 16000... any idea of where it's getting this override from, why it's not paying attention to the user-defined rate?

Thanks a bundle.

~Zoey

---

### Post by Zoey.Marie on 2009-09-24
(bump)

Ok, so... progress. Kind of... If I run "sudo jackd --realtime -d alsa -r 44100" and then run "sudo qjackctl", it'll run with a sample rate of 44100.

- But it will only do this if I run jackd first and specify parameters
- and it won't do realtime unless I run it from root.


Thoughts?

---

### Post by raboofje on 2009-09-25
> **Zoey.Marie said:**
> I have the sample rate set at 48000 in the JACK setup

Which jack setup do you mean? The QJackCtl one? What are the contents of ~/.jackdrc?

> but when I run it, it says that it's 16000

Which application claims that? Could you paste that output?

> Progress. Kind of... If I run "sudo jackd --realtime -d alsa -r 44100" and then run "sudo qjackctl"

Hmm, you really don't want to run jack as root, as that'd mean you'd have to run all your jack-enabled applications as root, too.

> won't do realtime unless I run it from root

What error do you get when you try to do realtime as non-root?

---

### Post by Zoey.Marie on 2009-09-25
> **raboofje said:**
> Which jack setup do you mean? The QJackCtl one? What are the contents of ~/.jackdrc? 

Yeah, when I set it up in QJackCtl, it will (usually) still come up as 16000. For some reason it fixed itself with all of my tinkering... not sure what I did, though.

~/.jackdrc says: /usr/bin/jackd -dalsa -dhw:0 -r44100 -p512 -n2 -S
-- but I don't know what the -S is for... Or where that file came from, or what it does, really. (Oh! It's the settings for how I'm running it, right? Can I edit the settings from there, too?)

>  Which application claims that? Could you paste that output? I don't think I can paste the output, because it's not doing it anymore, but it was doing it in the status menu in QJackCtl, as well as displaying it in the sample rate portion of QJackCtl.

> Hmm, you really don't want to run jack as root, as that'd mean you'd have to run all your jack-enabled applications as root, too.
... What error do you get when you try to do realtime as non-root?cannot use real-time scheduling (FIFO at priority 10) [for thread -1212250432, from thread -1212250432] (1: Operation not permitted)
 cannot create engine

but it goes away when I run it as root. (Though it is totally a pain to have to run the other applications as root, as well).


-- So now, I know that my original problem was spontaneously solved, but can we keep this thread open (I can edit the title, right?) so that the rest of the problems get solved, too?

---

### Post by raboofje on 2009-09-25
> **Zoey.Marie said:**
> ~/.jackdrc says: /usr/bin/jackd -dalsa -dhw:0 -r44100 -p512 -n2 -S -- but I don't know what the -S is for...

[quote=man jackd]      -S, --shorts
              Try to configure card for 16-bit samples first, only trying 32-bits if unsuccessful.  Default is to prefer 32-bit samples.[/quote]

Not sure why you'd want that.

> Or where that file came from, or what it does, really. (Oh! It's the settings for how I'm running it, right? Can I edit the settings from there, too?)

It's how jack will be started when started automatically - I requested a manpage for that file to be written ( [http://trac.jackaudio.org/ticket/137](http://trac.jackaudio.org/ticket/137) ), I'm not sure (but I think) qjackctl will also read/write that file.

> cannot use real-time scheduling (FIFO at priority 10) [for thread -1212250432, from thread -1212250432] (1: Operation not permitted)
 cannot create engine

You haven't given it permission to run with realtime privileges. I added some docs to [http://trac.jackaudio.org/wiki/Troubleshooting](http://trac.jackaudio.org/wiki/Troubleshooting)

> but it goes away when I run it as root. (Though it is totally a pain to have to run the other applications as root, as well).

See [http://trac.jackaudio.org/wiki/Troubleshooting](http://trac.jackaudio.org/wiki/Troubleshooting) on how to allow your non-root user to use it.

---

### Post by Zoey.Marie on 2009-09-25
> **raboofje said:**
> 


You haven't given it permission to run with realtime privileges. I added some docs to [http://trac.jackaudio.org/wiki/Troubleshooting](http://trac.jackaudio.org/wiki/Troubleshooting)

See [http://trac.jackaudio.org/wiki/Troubleshooting](http://trac.jackaudio.org/wiki/Troubleshooting) on how to allow your non-root user to use it.

I checked out that doc, and I had already updated the limits.conf file to list those values... It still doesn't work. Maybe Jack isn't in the Audio group? (not sure how I'd do that one. I couldn't fine the .pl thing that the Troubleshooting guide recommended)

---

### Post by raboofje on 2009-09-25
> **Zoey.Marie said:**
> I had already updated the limits.conf file to list those values...

Did you log out and back in again?

> Maybe Jack isn't in the Audio group? not sure how I'd do that one

Try running 'groups' on the commandline, it should show which groups you're in.

> I couldn't fine the .pl thing that the Troubleshooting guide recommended

Fixing the link now, moment.

---

### Post by Zoey.Marie on 2009-09-25
[quote=raboofje] Lots of helpful stuff [/quote]

I added myself to the audio group (I never even thought of that until I read the link that you sent). I figured out where to get, and how to run, the .pl script, and it's definitely helping... though it's a little hard to figure out. I'm following all the links that it lists, but here's the problems that it has:

[quote=.pl file]
zoey@zoey-laptop:~/Desktop$ perl realTimeConfigQuickScan.pl
...
Checking for Generic PCI bus-master DMA support... not found.
** Kernel without Generic PCI bus-master DMA support
   For more information, see:
   - [http://lowlatency.linuxaudio.org](http://lowlatency.linuxaudio.org)
...
Checking filesystem types... 
** Warning: do not use /windows for audio files.
   fuseblk is not a good filesystem type for realtime use and large files.
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems)
Checking tmpfs mounted on /tmp..  not found.
** Warning: no tmpfs partition mounted on /tmp
   For more information, see:
   - [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs)
   - [http://lowlatency.linuxaudio.org](http://lowlatency.linuxaudio.org)
Checking filesystem 'noatime' parameter... 
** Warning: / does not have the 'noatime' parameter set
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems)
** Warning: /windows does not have the 'noatime' parameter set
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems)
** Warning: /media/disk does not have the 'noatime' parameter set
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems)
** Set $SOUND_CARD_IRQ to the IRQ of your soundcard to enable more checks.
   Find your sound card's IRQ by looking at '/proc/interrupts' and lspci.
Checking the ability to prioritize processes with (re)nice... yes - good.
Checking the ability to prioritize processes with rtprio...  unknown.
** rtprio command-line tool  not found - install it for improved feedback
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#priorities](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#priorities)
...
Checking access to the real-time clock... not readable.
** Warning: /dev/rtc found, but not readable.
** make /dev/rtc readable by the 'audio' group
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#real-time_clock](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#real-time_clock)
Checking sysctl settings:
- checking inotify max_user_watches... too small.
** /proc/sys/fs/inotify/max_user_watches is smaller than 524288
** increase it by adding 'fs.inotify.max_user_watches = 524288' to /etc/sysctl.conf and rebooting
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#sysctl.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#sysctl.conf)
...
[/quote]

Those are the ones that it looks like I'm having trouble with... I'm searching through the recommended docs, and I'll post here when I finish, but it does seem pretty daunting. :/

---

### Post by raboofje on 2009-09-25
> **Zoey.Marie said:**
> I added myself to the audio group (I never even thought of that until I read the link that you sent). I figured out where to get, and how to run, the .pl script, and it's definitely helping... though it's a little hard to figure out.

Please, don't hesitate to ask (or update/clarify the documentation yourself once you figure it out :) ). Together we can make all this more straightforward.

> Checking for Generic PCI bus-master DMA support... not found.
** Kernel without Generic PCI bus-master DMA support
For more information, see:
- [http://lowlatency.linuxaudio.org](http://lowlatency.linuxaudio.org)

Which kernel is that? (you can check with 'uname -a')

> ** rtprio command-line tool not found - install it for improved feedback

Please ignore this one for now - I should update the script to use chrt instead of rtprio.

> Those are the ones that it looks like I'm having trouble with... I'm searching through the recommended docs, and I'll post here when I finish, but it does seem pretty daunting. :/

With yourself in the audio group and limits.conf set up right, you should be in pretty good shape already. Much of the rest is just fine-tuning and tweaking.

---

### Post by Zoey.Marie on 2009-09-25
> **raboofje said:**
> Please, don't hesitate to ask (or update/clarify the documentation yourself once you figure it out :) ). Together we can make all this more straightforward.  definitely! 


>  Which kernel is that? (you can check with 'uname -a') 

It's the Real time one (Linux zoey-laptop 2.6.28-3-rt)


>  With yourself in the audio group and limits.conf set up right, you should be in pretty good shape already. Much of the rest is just fine-tuning and tweaking.

Yeah... I think I'm ignoring the rest right now. I barely have any idea what they mean, and I certainly don't have the energy to figure it out now that I've spent so much time on other stuff. I feel really accomplished just getting these few things working. Haha.

---

