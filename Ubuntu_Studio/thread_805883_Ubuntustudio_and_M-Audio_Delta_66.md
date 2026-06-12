---
title: "Ubuntustudio and M-Audio Delta 66"
date: 2008-05-24
forum: Ubuntu Studio
---

### Post by Haferstroh on 2008-05-24
Hello
Does anyone knows how to get a M-Audio Delta 66 Rev.E Soundcard working in UbuntuStudio 8.04 ?? I'm a real noob with this :-) and it would be fine if someone could help me
Thanks

---

### Post by jondecker76 on 2008-05-25
I have a Delta 1010, and all I had to do was plug it in - I would figure that same would apply to the 66. Also, if you have an onboard sound card, disable it in the bios.

And if you haven't already, search synaptic for envy24control - its the mixer for these cards.

---

### Post by Haferstroh on 2008-05-26
Hello, 
I wish I could tell, this card would work out off the box. 
When playing a mp3 file envy24 pcm Monitor show that something happens but I hear nothing. In the Audioconfig I get no Testsignal, it only shows this error if I try to autofind the device :
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

If I select ICE1712 multi or ALSA there is no error. 

I dont know if the card is working at all, but I dont wanna reinstall windowsxp. But I think I need to, if I want to find out :( 
Does anyone has a clue ??
Thanks

---

### Post by Tuttermuts on 2008-07-24
> **Haferstroh said:**
> Hello, 
I wish I could tell, this card would work out off the box. 
When playing a mp3 file envy24 pcm Monitor show that something happens but I hear nothing. In the Audioconfig I get no Testsignal, it only shows this error if I try to autofind the device :
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

If I select ICE1712 multi or ALSA there is no error. 

I dont know if the card is working at all, but I dont wanna reinstall windowsxp. But I think I need to, if I want to find out :( 
Does anyone has a clue ??
Thanks

Hi there, I'm having the same error, but I don't even get any signal showing through the envy24control. I just did a fresh install with ubuntu studio, updated. Tried a few tutorials on jack and envy24. Where do I go from here? If the answer is compile, please also direct me in the right direction. Anyone? Thx

edit: I found a partial answer here
[http://ardour.org/node/1198](http://ardour.org/node/1198)

somewhere at the end of the topic someone replaced the driver with the driver from another card (1010lt) in a certain file. I did this too and now I have audio and midi, only need to figure out how to record.

---

### Post by solcore on 2008-08-04
Maybe this can help?
[http://www.nue.tu-berlin.de/wer/batke/Download/delta66howto.pdf](http://www.nue.tu-berlin.de/wer/batke/Download/delta66howto.pdf)

---

### Post by jocheem67 on 2008-08-04
i think I can be of help here:::

first of all, disable pulse and replace it with alsa, the "gconf-audio-testsink blah-the blah" error is probably based in pulse not working with the m-audio.
In alsa it should work fine though...

Secondly it might be a good idea to indeed disable the onboard sound chip in the bios, this way one only has one soundchip left, which will be referred to as "hw:0" . It will automatically be the default.
Upon reboot it should just work as this chip is loaded into the kernel already.
A useful tool is asoundconf:

> jochem@jochem-desktop:~$ asoundconf
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio

jochem@jochem-desktop:~$ asoundconf list
Names of available sound cards:
M1010LT
RMX
jochem@jochem-desktop:~$ 


With the command "asoundconf set-default-card RMX" I've been able to route all my audio through a hercules RMX dj console...of course I cannot really disable my delta1010lt in the bios cause it's a pci-card...this might not apply to you.

Hope this was of any assistance.

Reading bout your problem once again it seems that your m-audio is working but it's still muted.
Indeed choosing alsa ot ice1712 ( the chip on the m-audio ) is the right thing to do.
Next you need to check out your little "speaker" on the top-right". There's preferences there where you can play around with the playback setting, they should be unmuted. For my delta I have to turn up the volume for "DAC" and "DAC1"....
You can also do this with envy24control as stated earlier...

---

### Post by Miesco on 2008-08-05
I tried the M-Audio fast track ultra, but I took it back cause it wasn't being recognized as a sound card.  Could this be because I didn't disable the other one in my bios?

---

### Post by RadioMirchi on 2008-08-07
thankss for the information dude

---

### Post by nlz on 2008-08-21
So, did you get the M-Audio Delta 66 working, or not?

---

### Post by Tom Mann on 2008-11-07
Add this to /etc/modprobe.d/alsa-base:

```
options snd-ice1712 model=delta1010lt
```

then reboot.

---

### Post by sliding on 2008-11-12
> **Tom Mann said:**
> Add this to /etc/modprobe.d/alsa-base:

```
options snd-ice1712 model=delta1010lt
```

then reboot.
I have the Delta 66 with Ubuntu Studio, but so far no succes with getting it to output any sound. Bought it about a year ago, so probably it's the latest version that does not work as the model=delta66 with alsa.
So I tried this setting in alsa-base.
On some audio sliders in the Envy24 control I can see some input when using input 1+2, but I need to keep 3 sliders open to get signal from both at the same time.
How many channels are supposed to be visible in Envy24 when using delta1010lt as the model.
It looks all very inconsistent to me.
I see 8 H/W inputs on Monitor inputs tab
      8 PCM outputs 
      8 H/W Out (4L 4R alternating) + SPDIF L and SPDIF R on patchbay tab
      8 DAC +  8 ADC on the Analog tab
I guess that's far too many if compared to the manual's description for windows.
Should I better change to a Delta 44 to get anything going?? :confused:

---

### Post by Tom Mann on 2008-11-20
I considered trying model=delta44 but haven't had the chance to do so - please let me know if it works for you :KS

---

### Post by kamlapati on 2009-01-12
I used the workaround:

```
options snd-ice1712 model=delta1010lt
```

and it worked great on my Delta 66 rev. E.

So far I have tested stereo inputs and outputs in Audacity and Ardour (using jack) and all seems OK.

I'll be able to try the "delta44" option some time this week.

Thanks, all.

---

