---
title: "Sound and Local Devices in Edubuntu LTSP"
date: 2006-06-15
forum: Server Platforms
---

### Post by DarkElf109 on 2006-06-15
Are there any ways to enable sound or local devices on an LTSP workstation running off of Edubuntu Dapper? If so, how would one go about implementing them?

---

### Post by Baum88 on 2006-06-15
Sound issue fixed by putting the following in /opt/ltsp/i386/etc/lts.conf:

```

[Default]
SOUND = True

```

Mounting local drives still doesn't work but I think it has something to do with ltspfs.

---

### Post by b4k4 on 2006-07-03
I have an Edubuntu Dapper server. I enabled sound for the clients, and it works at startup, and from Rythmbox. However, with XMMS and vlc, the sound comes out of the server instead of the client.

I installed xmms and vlc myself. What did I do wrong?

Thanks!

---

### Post by b4k4 on 2006-07-04
Found out what to do with xmms. In preferences I changed the output plugin to ESD instead of ALSA, and that fixed it.

Can't find any equivalent option for VLC, or for Gxine, which is also playing sound through the server.

---

### Post by prizrak on 2006-07-05
VLC has different plug ins. You need to go into Synaptic and make sure that VLC ESD plug in is installed and ALSA is uninstalled. Gxine I'm not sure about but you can install Totem-xine which will possibly fix your issue. I am also interested in local drive mounting as I got a laptop running off a desktop (saves on monitor/kbd/mouse) and it would be very nice not to have to plug USB drives into the server.

---

### Post by danieru on 2006-07-20
Hello,
Per instructions above I created:

/opt/ltsp/i386/etc/lts.conf

and added the following lines:

[Default]
SOUND = true

...but I'm still not getting any sound on the clients, say through RhythmBox like you mentioned.  The sound is still coming through on the server.

Am I missing something here?  Does anyone have any suggestions?  This is on Edubuntu Dapper 6.06.

cheers,
Daniel

---

