---
title: "USB audio device not in jack"
date: 2013-02-19
forum: Ubuntu Studio
---

### Post by Ansible on 2013-02-19
I have a cheapo usb guitar cable that I've been using for audio in with a program that uses openal for audio stuff.  The way I use it there is to go into the 'sound' control panel in ubuntu settings and switch the input from Internal Microphone (the default) to "Microphone USB Pnp Sound Device".  From there no problems.

Now, I want to use this input with sooperlooper, which requires Jack.  

But, in Jack I don't get an additional sound device under "Readable Clients/Output Ports".  There is only 'system', which delivers the internal laptop microphone only.  Changing the audio source settings in the ubuntu sound control panel has no apparent effect - only the internal microphone comes through.  

Suggestions?

---

### Post by jejeman on 2013-02-19
You need to specify in JACK settings to use the USB card.
Readable ports will always be "System" - that is normal.

---

### Post by Ansible on 2013-02-20
Thx!  Been a while since I dug around in jack... didn't think about it.  Working good now.

---

