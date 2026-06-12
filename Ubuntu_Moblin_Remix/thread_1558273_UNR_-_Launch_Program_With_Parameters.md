---
title: "UNR - Launch Program With Parameters"
date: 2010-08-22
forum: Ubuntu Moblin Remix
---

### Post by mooreted on 2010-08-22
On my AcerOne, I have to launch Skype with parameters to get the microphone to work:

/bin/sh -c "PULSE_SERVER=127.0.0.1 skype"

How do you do this in UNR? None of the launchers seem to be configurable.

---

### Post by mooreted on 2010-08-22
Well, kind of a workaround. I don't think a "normal user" would figure it out.

I edited the skype.desktop file in /usr/share/applications with the line

Exec=/bin/sh -c "PULSE_SERVER=127.0.0.1 skype"

Now the mic is working.

---

