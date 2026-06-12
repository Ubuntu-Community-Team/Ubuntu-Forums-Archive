---
title: "no sound drivers at all?"
date: 2009-03-01
forum: Wine
---

### Post by edgue on 2009-03-01
Hello,

I am using ubuntu 8.10 on my Lenovo T61p. Alsa sound seems to work fine; I can listen to youtube videos or play my MP3 songs ... but:

I installed wine (first 1.0.1; then I upgraded to 1.1.16) to run the Cisco IP Communicator software (for VoIP within my companies intranet). 
Problem is: this software comes up with a panel and asks me to select a sound device for headset, speaker, mic and so on. 
Strange thing: the only option it shows in the pull down list .. is "none".

I tried to enable all different sound drivers within winecfg, I tried "emulation" ... nothing seems to have an effect.

Any idea what I am missing?

regards,

---

### Post by Meow27 on 2009-03-02
please tell us which programs you are using

please try running those programs WITH NOTHING ELSE IN THE BACKGROUND

its probably cause OSS can only be used once at a time =.=

---

### Post by edgue on 2009-03-02
> **Meow27 said:**
> please tell us which programs you are using

please try running those programs WITH NOTHING ELSE IN THE BACKGROUND

its probably cause OSS can only be used once at a time =.=

Hi there,

I am not sure what I changed; but now I can get one step further ... the "audio config wizard" of the Cisco software shows me a
"Analog Devices AD1984" 

I can get the wizard to play its test signal to the speaker; but the software tells me it cant configure the device for recording. 

Basically i am running the same programs as before ... what isnt much -
i am logging in, start my browser and Lotus Notes ...

---

