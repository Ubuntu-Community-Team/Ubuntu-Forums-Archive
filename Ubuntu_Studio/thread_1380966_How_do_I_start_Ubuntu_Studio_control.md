---
title: "How do I start Ubuntu Studio control?"
date: 2010-01-14
forum: Ubuntu Studio
---

### Post by Bikeman2000 on 2010-01-14
I'm on a longer trip getting audio output on MIDI tracks in Rosegarden.

First I needed a running server from a program called "Jack". But starting the server only resulted in a error message (no connection as a client to the JACK-server possible - Overall operation failed).
After searching the web I got the information that I needed Ubuntustudio-control. 
I installed this program via the software center but I do not see any menu entry to start the program.
Could somebody tell me how to start ubuntustudio-control?

---

### Post by AutoStatic on 2010-01-14
Hello Bikeman2000, just untick the 'Realtime' option in QjackCtl, that will get you going right away. If you want to get some more out of your system: [https://help.ubuntu.com/community/UbuntuStudioPreparation#Real%20Time%20Kernel%20&%20Xruns](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real%20Time%20Kernel%20&%20Xruns)

And the Ubuntu Studio Controls are in System - Administration, but for Karmic it's currently a better option to do it manually as described on the help page.

---

### Post by Bikeman2000 on 2010-01-14
Thanks, now the jack server was running.

The next step i found out is getting an software synthesizer. 
So I downloaded Qsynth and one General MIDI soundfont file, But after starting Qsynth i ge the error message:> Failed to create the audio driver (jack). Cannot continue without it.
fluidsynth: warning: Failed to pin the sample data to RAM; swapping is possible.
cannot read response from jack server (No such file or directory)
fluidsynth: error: Jack server not running?"

---

