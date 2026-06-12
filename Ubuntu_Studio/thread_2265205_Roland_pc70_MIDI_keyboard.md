---
title: "Roland pc70 MIDI keyboard"
date: 2015-02-13
forum: Ubuntu Studio
---

### Post by linuxguy8 on 2015-02-13
I have a Roland pc70 midid keyboard with a midi out port hooked to a m-audio uno midi controller goin into a USB port. I'm running the latest version of ubuntustudio(14.04.1). I used to connect everything in the patchbay and would get it rolling with zynaddsubfx. I'm using yohimi which is a fork of zyn, but it is not working like it used to?

---

### Post by bhilmers2 on 2015-02-13
Did you [FONT=courier new]sudo apt-get install midisport-firmware[/FONT]? This package has always helped me get my M-Audio gear working.

---

### Post by linuxguy8 on 2015-02-14
Yes, i am doing that already. I'm not able to connect the items in patchay together, also tried patchage no go !

---

### Post by linuxguy8 on 2015-02-14
Thanks anyway, any other ideas?

---

### Post by CrocoDuck on 2015-02-15
Hi! How are you connecting the controller to yoshimi? If I don't remember wrong ZynAddSubFX had a writable ALSA client you could use directly, while yoshimi provides a MIDI writable client. I don't think that MIDI clients are evident on patchage. Use Qjackctl to make the connections. Click on connect on the Qjackctl interface. You should see yoshimi in the MIDI tab. To reach it from the ALSA tab you need something like a2jmidid. Install it and then run

```
a2jmidid
```

in a terminal. In the ALSA tab connect the controller to Midi Through. In the MIDI tab connect a2j to yoshimi. This is what I am used to do.

---

### Post by marseille2 on 2015-02-15
I agree with Crocoduc, but if [**[COLOR=#000000]linuxguy8[/COLOR]**]("http://ubuntuforums.org/member.php?u=45129") has the firmware installed, and still can't fire up the keyboard, then it's possible that a reset is in order. (I use to deal with the same issue ... but no more!). This is what I learned to do to stop the madness, and still use pulseaudio while I'm doing audio (it's a summary of solutions from good threads, manual instructions, and advice from #ubuntustudio IRC):

First make sure that your Qjacktl settings are the way you want, i.e. -- whether to use realtime, ALSA, etc. When you're done, close up the app, then turn off jackd *if it's on*...

Kill jackd and jackdbus (sometimes I have to issue the command more than once if their stubborn)

> $ killall jackdbus jackd

Stop pulseaudio from autospawning (if you let it keep going, it has the potential to give you endless headaches).

> [COLOR=#333333][FONT=Arial]**$ echo autospawn = no > $HOME/.config/pulse/client.conf**[/FONT][/COLOR]

Then delete these files* and/or* folders:


[LIST]
[*][COLOR=#333333][FONT=Arial]delete *all files* in .config/jackd[/FONT][/COLOR] 
[*][COLOR=#333333][FONT=Arial]delete *qjacktl* file in .config/rnbc.org[/FONT][/COLOR] 
[*][COLOR=#333333][FONT=Arial]delete .config/pulse *folder* 
[/FONT][/COLOR] 
[/LIST]
Reboot

Open the terminal and find your sound card:

> [COLOR=#000000][FONT=Arial]**$ cat /proc/asound/cards**[/FONT][/COLOR]

You should see your sound card(s) and your midi devices. This is an example output:

>  0 [UA700]: USB-Audio - EDIROL UA-700
               Roland EDIROL UA-700 at usb-0000:03:07.0-1, full speed

               1 [L61]: USB-Audio - Launchkey 61
               Focusrite A.E. Ltd Launchkey 61 at usb-0000:00:12.0-1, full speed

Then fire up jackd and tell it to use your sound card.[INDENT](Note that in the example here, I've already got Qjacktl to agree with settings of this command, hence the first direction. This seems to help later on when I need to follow this reset procedure. But see that I'm using realtime settings and alsa. 

My sound card is the Edirol >> "hw:0" ... replace the "hw:0", with the number of yours, from the output of $ cat /proc/asound/cards ... You can tweak this setting for multiple soundcards. *See [Ted's Linux Midi Guide]("http://tedfelix.com/linux/linux-midi.html")*)
[/INDENT]
 
> $ jackd --realtime -d alsa -C hw:0 -P hw:0

Keep the terminal running and open up a tab to issue the midi bridge command:

> [COLOR=#000000][FONT=Arial]$ a2jmidid -e[/FONT][/COLOR]

Play music, and when you're ready to stop jackd... kill it from the terminal.

> $ killall jackdbus jackd

Caveat... sometimes I want to use an alsa application but the pulseaudio module for it, gets flaky. See this thread to [load the module]("http://ubuntuforums.org/showthread.php?t=2261067").

---

