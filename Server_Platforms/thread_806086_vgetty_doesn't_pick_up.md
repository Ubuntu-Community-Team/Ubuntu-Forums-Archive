---
title: "vgetty doesn't pick up"
date: 2008-05-24
forum: Server Platforms
---

### Post by elvinatom on 2008-05-24
Hello forum!
I have an ubuntu 7.1 i386 server with all kinds of stuff on it.  It runs hylafax on an external serial voice/data/fax modem (ttyS3) - the "Trendnet TFM-560X" to be precise. I don't know why the only serial port on the board was assigned as COM4, but anyways - who cares.

I lately decided to add voicemail to that box, got myself a PCI-serial-card (since I was out of COM ports), another modem (same one: TFM-560X) put it together. Turns out the new modem is on ttys0. Then I installed mgetty, mgetty-voice, mgetty-pvftools, configured the voice.conf and added the file "ttyS0" to /etc/event.d (exec /sbin/vgetty ttyS0). A greeting is present.

When both modems are idle, the voicemail modem has CS- and MR-LEDs on, the fax modem however has CS- RS- TR- and MR-LEDs on - so the voice-modem is off I believe. I can test it with minicom and it returns "ok" on AT command - then the RS- and TR-LED's come on as well as on the fax modem.

btw, there are no vgetty logs in /var/log

I googled around, but couldn't find any answers. Any suggestion would be awesome.

---

### Post by elvinatom on 2008-05-24
Update:
I checked my logs and found this:
```
05/24 23:05:38  vgetty: experimental test release 0.9.32 / with duplex patch
05/24 23:05:38  reading program vm configuration from config file /etc/mgetty/voice.conf
05/24 23:05:38  opening voice modem device
05/24 23:05:38  opened voice modem device /dev/ttyS0
05/24 23:05:38  reading port ttyS0 configuration from config file /etc/mgetty/voice.conf
05/24 23:05:38  detecting voice modem type
05/24 23:05:40  vm: Modem returned ERROR
05/24 23:05:41  no voice modem detected
```

Does my modem have problems returning the modem type or what does it mean?

---

### Post by oneir on 2008-08-08
I don't know how far this will help since I don't have such a modem and know very little about vgetty, but I just ran across a post through google that showed someone with the same modem trying to setup an answering machine and he couldn't get it working until someone suggested setting "forceV253 TRUE" in his voice.conf file (on my present system that is located in /etc/mgetty+sendfax

Here is the thread:

[http://www.meinews.net/vgetty-t126735.html?](http://www.meinews.net/vgetty-t126735.html?)
> **elvinatom said:**
> Hello forum!
I have an ubuntu 7.1 i386 server with all kinds of stuff on it.  It runs hylafax on an external serial voice/data/fax modem (ttyS3) - the "Trendnet TFM-560X" to be precise. I don't know why the only serial port on the board was assigned as COM4, but anyways - who cares.

I lately decided to add voicemail to that box, got myself a PCI-serial-card (since I was out of COM ports), another modem (same one: TFM-560X) put it together. Turns out the new modem is on ttys0. Then I installed mgetty, mgetty-voice, mgetty-pvftools, configured the voice.conf and added the file "ttyS0" to /etc/event.d (exec /sbin/vgetty ttyS0). A greeting is present.

When both modems are idle, the voicemail modem has CS- and MR-LEDs on, the fax modem however has CS- RS- TR- and MR-LEDs on - so the voice-modem is off I believe. I can test it with minicom and it returns "ok" on AT command - then the RS- and TR-LED's come on as well as on the fax modem.

btw, there are no vgetty logs in /var/log

I googled around, but couldn't find any answers. Any suggestion would be awesome.

---

