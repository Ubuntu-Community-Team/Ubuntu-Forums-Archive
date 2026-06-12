---
title: "No sound from Hydrogen (setting up ubuntu studio)"
date: 2011-03-11
forum: Ubuntu Studio
---

### Post by duncanmaybury on 2011-03-11
Hello kind forum people,

What I am stuck with at the moment:
I can't get any sound out of Hydrogen, Jack is running. I am getting sound through my Audigy card when playing mp3s in the standard movie player. Any ideas please?  

Some background:
I have used standard ubuntu abit, have basic knowledge of terminal stuff (I know what it is and what sudo meens!). 
I have just installed a fresh Ubuntu studio 10.10.
I have a soundblaster Audigy card.

Mission:
To use programs such as Hydrogen to make small patterns, record them out into my Roland sp808, manipulate them in various ways, record them back into a sequencer such as Rosegarden, also use Rosegarden as a midi sequencer. I hope this will be doable. I used to use Reason, cubase vst and Windows XP for this.

---

### Post by sgx on 2011-03-11
These videos will help, the first for connecting Hydrogen
and the second for using it. There are many more linux audio videoss on youtube

[http://www.youtube.com/watch?v=n5BzyN95NfQ](http://www.youtube.com/watch?v=n5BzyN95NfQ)

[http://www.youtube.com/watch?v=TWy52u-szXA&feature=fvwrel](http://www.youtube.com/watch?v=TWy52u-szXA&feature=fvwrel)

Cheers

---

### Post by duncanmaybury on 2011-03-12
Hi sgx,

Thanks for the links. Unfortunatley There is nothing specific to my problem. 
When I start Hydrogen, Jack also starts. Should I be going into the patchbay/connections in jack and pluging stuff into each other to be getting sound out of my sound card from Hydrogen?

---

### Post by Pablo_F on 2011-03-12
First of all, you have to make sure that jack is running on the Audigy.

What is the terminal output of

arecord -l && aplay -l

ps aux | grep jackd

(while jack is running)

?

Cheers, Pablo

---

### Post by duncanmaybury on 2011-03-12
Thanks Pablo,

drmnaga@ubuntu:~$ arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0090]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Audigy [SB Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
drmnaga@ubuntu:~$ 
drmnaga@ubuntu:~$ ps aux | grep jackd
drmnaga   1722  2.5  8.8 106344 90400 ?        SLsl 22:08   0:00 /usr/bin/jackd -T -ndefault -dalsa -dhw:0 -r44100 -p1024 -n2
drmnaga   1768  0.0  0.0   4012   740 pts/0    S+   22:09   0:00 grep --color=auto jackd
drmnaga@ubuntu:~$

---

### Post by sgx on 2011-03-12
> **duncanmaybury said:**
> Hi sgx,

Thanks for the links. Unfortunatley There is nothing specific to my problem. 
When I start Hydrogen, Jack also starts. Should I be going into the patchbay/connections in jack and pluging stuff into each other to be getting sound out of my sound card from Hydrogen?

In the qjackctl setup page on the middle right side,

Input device  >
Output device  >

click the  > widgets to see your soundcards, and switch, and test all the possible outputs. Installing alsamixergui may help you find the sound, in case the default mixer jackd uses is off. I would consider using ubuntu studio 8.04 if things don't click into place. 

This assumes you have a kit and pattern loaded and running in hydrogen. The load demo menu does that. You can play more drum sounds from a midi device while the pattern plays if you connect Hydrogen in the Alsa tab, to a detected midi device. Your finished beats can be exported as midi files, triplets are a good option to turn on once you're all set up. 
Cheers

---

### Post by duncanmaybury on 2011-03-12
Just having a look at the output of the terminal, scatching my head, then looking at my hardware set up, I feel like a bit of a fool! When I got this old computer off a friend I keenly put my SB Card in, but didn't remove the card that was in there!!:o If I take the output from the other card I have sound from Hydrogen! I will try taking out that card and see if I have sound from Hydrogen through my SB Card.
Thanks for the help so far and the prompt to think a bit more.

---

### Post by Pablo_F on 2011-03-12
Hi, 

Look at this (skipping some lines):

```
**** List of CAPTURE Hardware Devices ****
card 2: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]

card 2: Audigy [SB Audigy 1 [SB0090]], device 1: emu10k1 mic [Mic Capture]

card 2: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]

**** List of PLAYBACK Hardware Devices ****

card 2: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]

card 2: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]

card 2: Audigy [SB Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
```


You see that the audigy is your card 2. It has several so-called "devices". For example, device 0 is duplex (it is a capture device and playback device at the same time). 

Now, your jackd command:

```
/usr/bin/jackd -T -ndefault -dalsa **-dhw:0** -r44100 -p1024 -n2
```

hw:0 means card0 (and it defaults to device 0 of card 0). 

Look at this again:

```
**** List of CAPTURE Hardware Devices ****

card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
Subdevices: 0/1

**** List of PLAYBACK Hardware Devices ****

card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
```

So, jack is running on your CMI8738, which I suppose is an onboard card.


Start Jack Control, Setup button. In the interface field, write down:

**hw:Audigy** (you don't see this in the drop down list but it is all right).

If you want multichannel playback, you need to specify input and output devices separately. So, again in duplex mode, 

Input Device: 
hw:Audigy,0

Output Device: 
hw:Audigy,3


You could use "2" instead of "Audigy" but it is strongly recommended that you call the card by name, not by number, as card index numbers tend to change at different reboots depending on the way the wind may blow.

Cheers, Pablo

---

### Post by duncanmaybury on 2011-03-12
Thanks Pablo,
I see what you are saying, it is helpful. I am unable to tinker now but will do tomorrow. Cheers.

---

### Post by duncanmaybury on 2011-03-13
Hi Pablo,

Thanks for your help so far.
I have removed C-Media card from my machine. Now I just have the Audigy and the on board sound card.
I have played around with the settings in the Jack setup. I tried renaming the input and out put as you said. It didn't work. I have set it to hw:1 as this is now the Audigy. The result of the query code as to what hardware jack is using is still hw:0, which is now the on board card.

```
drmnaga@ubuntu:~$ ps aux | grep jackd
drmnaga   1624  1.1  8.8 106352 90444 ?        SLsl 22:42   0:05 /usr/bin/jackd -T -ndefault -dalsa -dhw:0 -r44100 -p1024 -n2
drmnaga   1908  0.0  0.0   4012   744 pts/4    S+   22:50   0:00 grep --color=auto jackd

```Cheers

---

### Post by Pablo_F on 2011-03-14
Hi, 

The trick is starting the jack server by means of Jack Control (Start button) **before** launching hydrogen. Your first goal is getting jack up and running with no clients but the Audigy. 

On the other hand, (not related to jack) you will probably need to set up the Audigy's internal mixer. You use an alsa mixer for this such as gnome-alsamixer, gamix, alsamixer... (either of them).

Cheers, Pablo

---

### Post by duncanmaybury on 2011-03-15
Hi,

Just started my machine, Jack then Hydrogen, all working ok. The query as to what hardware jack is using is showing the Audigy hw:1.
If I stop the Jack server and close jack, close Hydrogen. Then open Hydrogen first it is all working well.

Thanks Pablo and sgx for your help.

Cheers,
Dunc

---

