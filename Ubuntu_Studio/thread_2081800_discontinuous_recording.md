---
title: "discontinuous recording"
date: 2012-11-07
forum: Ubuntu Studio
---

### Post by maspis on 2012-11-07
Hi there,
i'm new in this forum and i hope some1 of you can help me.
I have installed ubuntu studio 12.04 on an acer aspire 1623LMi and i'm producing my music, but when i use ardour to record my guitar or my voice (or anything plugged on the line in plug) the record is discontinuous. I thought it was a problem of old hardware but sometimes in the past it worked well.
Sure of your interest,

tx in advance,
maspis

---

### Post by Sylos on 2012-11-09
Hello there.

Do you get any Xruns or odd output in the "messages" window of Qjackctl?

Also could you clarify what you mean by discontinuous? Does it stop all together or does it drop in and out?

Does it happen using other software?

Cheers

---

### Post by maspis on 2012-11-09
hi sylos.
tx for your reply.
My problem is, for instance, that when i record the voice i start recording and singing but ardour records for few seconds then it doesn't record anymore for some seconds, then it captures the voice again. It seems to me something about a record buffer...
anyway this happens with ardour with or without qjacktl. I have no xruns neither odd messages in qjacktl and if i try to record with audacity it works well...
Audio drivers to be updated or what?
I hope you can help me.

M

---

### Post by Sylos on 2012-11-10
Well if its working with Audacity then I would say that you can rule out hardware failure as the cause. 

I assume you have checked to make sure Ardour isnt set to Punch In/Punch Out? 

Also have you checked that your Jack settings are right for your soundcard (correct Periods/frames etc)?

You could try updating your Adrour - maybe even try the Ardour 3 Beta that is available from the website:

[http://ardour.org/node/5351](http://ardour.org/node/5351)

You should be able to install it from the file downloaded without removing your current ardour 2 build (they do say not to use the beta on old projects as you might loose work if it fails).

Could you post up some specs on your hardware and soundcard?

Cheers

---

### Post by maspis on 2012-11-11
hi sylos.

as i told you i have an acer aspire 1623LMi, pentium 4 3.2ghz, 3x256MB DDR333 SDRAM, HDD 60GB Ultra ATA/100 (half is for windows and 1GB is for the swap but i never see that ubuntu use it). 
about audio integrated card, if i use the command "sudo lshw"
i find:
        *-multimedia
             description: Multimedia audio controller
             product: IXP150 AC'97 Audio Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:d8004400-d80044ff

hope this can help you.
tx again

---

### Post by Sylos on 2012-11-12
> **maspis said:**
> hi sylos.

as i told you i have an acer aspire 1623LMi, pentium 4 3.2ghz, 3x256MB DDR333 SDRAM, HDD 60GB Ultra ATA/100 (half is for windows and 1GB is for the swap but i never see that ubuntu use it). 
about audio integrated card, if i use the command "sudo lshw"
i find:
        *-multimedia
             description: Multimedia audio controller
             product: IXP150 AC'97 Audio Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:d8004400-d80044ff

hope this can help you.
tx again

Cant see anything prohibitive in terms of your spec. Could you try the following:

Open a terminal and start ardour

```
ardour2
```

Then try and do your recording. When it drops in and out look at the terminal output and copy and paste it up here on the forum. You will need to leave ardour open whilst you do this (if you close ardour the terminal window will disappear). Hopefully the output will shed some light on the situation.

Cheers

---

### Post by maspis on 2012-11-13
hi sylos,
i did what you asked me. I have to say that i'm not home and i have not my guitar and my usual mic with me.
i tryed with a simple desk mic to record over a session that gave me problems at home and....it worked perfectly....three times...all along the song....without any interruption...i even tryed with rakarrack...everything was ok.
I can't understand. As i come back home i try with my usual hardware and i report the results to you.
tx and i write you asap,
M.

PS: if you like, listen to my works on
[http://www.jamendo.com/it/artist/426444/mas.pis](http://www.jamendo.com/it/artist/426444/mas.pis)

---

### Post by maspis on 2012-11-17
hi sylos.
this is what i read on terminal while my recording is discontinuous:
"massi@pc-massi:~$ ardour2
Ardour 2.8.12
   (built using 10144 and GCC version 4.6.1)
Copyright (C) 1999-2008 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
sto caricando il file predefinito di configurazione ui /etc/ardour2/ardour2_ui_default.conf
sto caricando il file di configurazione ui /home/massi/.ardour2/ardour2_ui.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
ardour: [INFO]: Ardour will be limited to 4096 open files
loading system configuration file /etc/ardour2/ardour_system.rc
loading user configuration file /home/massi/.ardour2/ardour.rc
ardour: [INFO]: No H/W specific optimizations in use
ardour: [INFO]: looking for control protocols in /home/massi/.ardour2/surfaces/:/usr/lib/ardour2/surfaces/
ardour: [INFO]: Control surface protocol discovered: "Generic MIDI"
ardour: [INFO]: Control protocol Tranzport not usable
powermate: Opening of powermate failed - File o directory non esistente
ardour: [INFO]: Control protocol powermate not usable
ardour: [INFO]: Control surface protocol discovered: "Mackie"
loading bindings from /etc/ardour2/mnemonic-us.bindings

(ardour-2.8.12:2428): Gtk-WARNING **: EnableTranslation: missing action EnableTranslation
Session writable based on /home/massi/Musica/Sessioni/wub/"
 
hope this can help...
M.

---

### Post by Sylos on 2012-11-30
Hello again - I have to say I thought this problem had fixed itself or you had given up - hence I stopped checking for replies.

Anyway - Im sorry to say I dont see anything there that shouts out at me a reason for your problem. My level of knowledge is relatively low.

You could try posting on the Linux Audio users mailing list. The guys there are pretty high level and may have a better chance of figuring the problem out. Otherwise I can only suggest trying a removal and reinstall of Ardour 2 OR trying Ardour 3.

Sorry I cant be of more help than that.

Good luck.
Cheers

---

### Post by maspis on 2012-12-06
Tx sylos for the answer.
Today i tried to connect audacity and rackarrak through jack and the result was a discontinuous recording. By the way i think the problem is in jack.
What do you think?

Anyway i follow your suggestion and i redirect my question to the other forum.
TX again,
m.

---

### Post by Sylos on 2012-12-08
Interesting that if affects more than one app. Can you post a screenshot of your Qjackctl settings?

Cheers

---

