---
title: "ALSA not showing in QjackCtl ??"
date: 2012-05-05
forum: Ubuntu Studio
---

### Post by teh1buck on 2012-05-05
Heads up, I've only been using ubuntu sparingly for the past year or two, so I am not entirely fluent yet and am still getting the hang of things, but learn quickly and will provide any information to get this fixed and will do what I need to.

I recently 'updated' Ubuntu 12.04 vanilla to Studio following [this]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu") tutorial. I then attempted to use [this]("https://help.ubuntu.com/community/HowToQjackCtlConnections") tutorial to get sound into jack so I can maybe start making some sounds and get a basic understanding of linking different applications together with QjackCtl, but when I get to this section:

[img]https://help.ubuntu.com/community/HowToQjackCtlConnections?action=AttachFile&do=get&target=TutQjackCtlConnections3.png[/img]

alsa_pcm does not show up under writable clients/input. i only get:

[img]http://i48.tinypic.com/inwm86.png[/img]

I'm entirely unsure about what to do since I followed both tutorials to the T I thought and there doesn't seem to be much information on what to do with pulseaudio? 

Any help or input would be greatly appreciated. I'd really like to get started using this software.

Note: If I click on the ALSA tab at the top of the above picture, and connect Virtual Board from under Readable Clients to ZynAddSubFx under Writable Clients, I get a response from ZynAddSubFx whenever I click a key on the Virtual Board. I see the volume meters jump within ZynAddSubFx whenever a key is pressed on Virtual Board, but no sound comes out.

---

### Post by jejeman on 2012-05-05
System is alsa_pcm.

I don't see anything wrong in the pictures.
It would be more useful if you had expanded connections.

Connecting ZynAddSubFx to system should give sound.

---

### Post by shimoda on 2012-05-05
If ZynAddSubFx is connected to System, it should sound... 

If I'm not wrong, I think that "Alsa" tab in qjackctrl is only for midi connections... Audio is all in first tab

---

### Post by sirriffsalot on 2012-05-05
In my humble experience, you're better off without pulseaudio when doing the studio thing... Either way, try uninstalling PulseAudio temporarily (uninstall everything related to pulseaudio as well, nothing "pulseaudio" should be running) and see if it shows up then. 

If not, after a while of trial and error, reinstall it and just try what you did before upgrading to 12.04 with connection trial and error. PulseAudio has it's uses, but is controversial for studio folks... Good luck!

---

### Post by jejeman on 2012-05-05
No need for uninstaling pulseaudio, it is sufficient just to turn it off.

---

