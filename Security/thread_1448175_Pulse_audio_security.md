---
title: "Pulse audio security"
date: 2010-04-06
forum: Security
---

### Post by ubuchignome on 2010-04-06
Pulse audio causing DoS issues? Any ideas?

---

### Post by nerdy_kid on 2010-04-06
kill the multicast sender

(pulse device chooser, config local server, multicast tab.)

---

### Post by ubuchignome on 2010-04-06
I am also getting a connection request to connect to rssyslog.com Any Idea on what is going on ?
 
Thanks!!!

---

### Post by rookcifer on 2010-04-06
PulseAudio is a POS, so I recommend you just get rid of it all together and use OSS instead. Trust me, you will be glad you did.  [Go here]("https://help.ubuntu.com/community/OpenSound") and follow the directions.

---

### Post by nerdy_kid on 2010-04-06
if you want to disable pulse (dont recommend it if your using karmic) do
```

sudo chmod -x /usr/bin/pulseaudio

```

---

### Post by ubuchignome on 2010-04-06
I am looking for the pulse device chooser to disable the server. But I can not find it...lol

---

### Post by rookcifer on 2010-04-07
> **ubuchignome said:**
> I am looking for the pulse device chooser to disable the server. But I can not find it...lol

Go to the link I provided above.  It shows how to get rid of Pulse and install OSS.

---

### Post by cariboo on 2010-04-07
Telling someone to uninstall pulse is not helping, for the majority of us pulse works quite well.

To the op the package you're looking for is padevchooser, it is in the repositories.

---

### Post by ubuchignome on 2010-04-07
Thanks much my Ubuntu brothers.

Be well

---

### Post by ubuchignome on 2010-04-13
Having another issue, pulse audio. see log?
pr 12 04:52:55 tom-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Apr 12 05:04:31 tom-desktop pulseaudio[1825]: ratelimit.c: 1 events suppressed

---

