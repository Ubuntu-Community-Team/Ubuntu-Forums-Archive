---
title: "Thumping and whining noise in headphones when sound card is idle Panp9 + Ubuntu 12.04"
date: 2012-07-05
forum: System76 Support
---

### Post by zat0ich1 on 2012-07-05
I just recently got a new panp9 that came with Ubuntu 12.04 preinstalled. For some reason, when the sound card is idle sometimes, my headphones (or my speakers connected through the headphone jack) produce a high pitched whining noise and a loud thumping noise at seemingly random intervals. I'm not sure what the cause is and I haven't found any predictability, although it does seem to occur frequently after pausing a flash video or other streaming media. The noise never occurs when the sound card is active.

I tried using outrec to record the sound card output, but as soon as I start recording, the noise stops.

Has anyone else had any similar problems? Does anyone have any suggestions as to what might be causing the noise or how to fix it?

---

### Post by Carborundum on 2012-07-06
I'm seeing something similar on my gazp7. The noise is easy to trigger on my machine; it occurs whenever anything is drawing anything. For example, scrolling through documents, switching workspaces, Alt-tabbing between windows, that sort of thing.

I also can't hear the noise when actual audio of some kind is playing. I'm not sure if that's because it goes away, or if it's just too low to hear. It doesn't appear to affect the internal speakers or speakers connected to the HDMI output.

---

### Post by ufugu on 2012-11-26
> **Carborundum said:**
> I'm seeing something similar on my gazp7. The noise is easy to trigger on my machine; it occurs whenever anything is drawing anything. For example, scrolling through documents, switching workspaces, Alt-tabbing between windows, that sort of thing.

I also can't hear the noise when actual audio of some kind is playing. I'm not sure if that's because it goes away, or if it's just too low to hear. It doesn't appear to affect the internal speakers or speakers connected to the HDMI output.

I am having EXACTLY this issue on my gazp7 as well.  My external USB sound card is OK, but if that's not connected I get static and hissing directly related to all those same actions.

(In an unrelated note, I'm getting physical noise issues as well that System 76 suggests is my SSD, which makes zero sense to me.  I'm going to try booting with another drive to troubleshoot that one. To think I was looking for a quiet laptop!)

---

### Post by Claus7 on 2013-07-13
Hello,

I 'm facing the same problem while:

i) both usb & heaphone and microphone jacks are connected to my pc
ii) I'm not listening on any music 

if usb is removed, the noise ceases and everything is ok. I can listen to music, can use the microphone, yet I cannot use the advanced options of my headphones.

Some indications:
There is a hissing noise while browsing.
Sound stops if I open pulse volume control and starts anew if it is closed...

Any idea will be more than welcome,
Regards!

---

### Post by isantop on 2013-07-15
Which model is your system, and which version of Ubuntu are you running? We haven't had reports of this for a while.

---

### Post by Claus7 on 2013-07-16
Hello,

thank you for your response. I have an EOL 10.10 maverick version and while searching for a solution to this problem, I saw that this was happening in 12.04 as well. 
Since this stops while I'm opening the sound menu, I think that it might be something trivial. I hadn't faced such a problem before, since I bought some new headphones that combine both usb ports and jacks.

If the solution is an update, then this is really good news. If someone has found out something else, I will be more than glad to hear. For the time being, just the jacks are working pretty nicely.

Thanks,
Regards!

---

### Post by isantop on 2013-07-17
What model computer do you have?

---

### Post by Claus7 on 2013-07-19
Hello,

> **isantop said:**
> What model computer do you have?

I guess that you are asking about the audio configuration, so:

```
lspci | grep Audio
```

> 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]

Thanks for the interest,
Regards!

---

### Post by isantop on 2013-07-19
No, I need to know the model number of your computer. It should be something like "panp7" or "ratp1".

---

### Post by Claus7 on 2013-07-20
Hello,

> **isantop said:**
> No, I need to know the model number of your computer. It should be something like "panp7" or "ratp1".

I do have a desktop... I searched on the internet about computer model and the ones you propose, and the results were about system76 models.
lshw do not provide me such information and I do not have an option: system->preferences->system76 driver

Am I missing something here? I do not think that I have a system76 model...
Any insight here would be helpful.

Regards!

---

