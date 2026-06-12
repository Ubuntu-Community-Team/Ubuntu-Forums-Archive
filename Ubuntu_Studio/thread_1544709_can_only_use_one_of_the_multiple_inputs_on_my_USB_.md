---
title: "can only use one of the multiple inputs on my USB sound card"
date: 2010-08-02
forum: Ubuntu Studio
---

### Post by accoustika on 2010-08-02
Hello, i have a steingberg mi4 USB soundcard that has multiple inputs, both XLR and TRS 1/4" but for some reason, ubuntu studio only recognizes 1 input, which is the front instrument input. The back inputs don't seem to be read, although in Jack connections, 4 capture inputs appear on my screen. I'm sure i'm making the right connections on Jack, but for some reason, only capture 3 works, which is the front instrument input. However when i restart my pc, i can see the signal going through my sound card on my vu meters from both of my XLR inputs in the back, but as soon as ubuntu studio launches, the vu meters go dead along with the signal. I'm almost sure that ubuntu studio can't seem to see but 1 input. Could anyone help me fix this please? Thanks and God bless.

---

### Post by cchhrriiss121212 on 2010-08-03
Try opening alsamixer in a terminal window, press f4 and check your capture levels are high enough.

---

### Post by accoustika on 2010-08-03
hmmm could you tell me how i can do that coz im kinda new to ubuntu so m still trying to get familiar with the terminal. But im not sure i have the alsamixer coz i cant find it on the graphic interface.

---

### Post by accoustika on 2010-08-03
hey bro i found out how to open alsamixer, turned out to b very easy :p however when i press f6 to select my usb sound card, it says: this sound device does not have any controls. Any suggestion now? Am i doomed? :(

---

### Post by cchhrriiss121212 on 2010-08-03
It seems you may be: According to the ALSA database, your device is not supported so I doubt you will get any more functionality out of it. I have an unsupported USB interface and it will accept inputs but not send outputs which I suppose is better than nothing, I bought a supported card in the end.

But it is odd that alsamixer does not show anything when jack does. Could you put "arecord -l" into a terminal? That should show your available capture devices.

---

### Post by accoustika on 2010-08-04
i typed arecord -l into terminal. It seems that ubuntu is only recognizing 1 device from the usb sound card while it should be recognizing 4. However the internal sound card shows all of its devices. Do u think i may be allowed to a certain number of inputs and the internal sound card with its inputs has left me with one input allowed from the usb sound card? And another thing is that Steinberg is said to be supported on the alsa website. Maybe i should assign manually a certain number of input devices for the usb soundcard in the terminal, but the thing is that i have no clue how to do that!

---

### Post by cchhrriiss121212 on 2010-08-04
That is normal for an arecord -l output, it will only show the number of devices and not inputs (eg. I have one device showing for a card with 4 inputs).
The ALSA site shows only one card supported, which does not mean that other Steinberg cards will work as they will use different chipsets. If you want to see this change then I recommend you contact Steinberg and ask them to co-operate with FOSS, it is the only way they will take notice.
Like I said unsupported hardware will only ever work with patchy results, and spending time trying to get it going will not be a rewarding experience unless you are incredibly good at reverse engineering drivers form scratch. Sorry I couldn't be of more help.

---

### Post by accoustika on 2010-08-04
ok this is what i discovered today. all my inputs are working except the XLR inputs which only work before ubuntu launches. I discovered that today by accident when i decided to try the other inputs in the back, which i've never used so far :P so any idea now what might be the cause of that? thanks for being patient with me! Blessings...

---

