---
title: "recordmydesktop and Jack won't work together.."
date: 2009-11-22
forum: Ubuntu Studio
---

### Post by produnis on 2009-11-22
Hi folks,

I would like to produce some screencasts with recordmydesktop on my 9.10 Karmic 64bit MacbookPro4,1

If I run recordmydesktop, the sound is not captured very well, the sound is not synchron and every 1 or 2 seconds the sound is missing.

If I run "top" while recording, the CPU-usage is about 18%.... so that should not be the problem...

I read, that using JACK might solve this issue...

so I installed JACK and it starts up without problems....


Now, in recordmydesktop I selected "Use Jack for audio..." and marked the two "capture"-sources showing up...

The problem is, that JACK won't recognize these settings...
The JACK "Connect"-Window does only show the system in- and -outputs, there is no entry for recordmydesktop showing up...

so there is no way to manualy connect the capture-device with recordmydesktop



If I try to start the screencast, recordmydesktop exits by saying "Error 256" (which means, that there is no audio-input-device found)...

Does anyone know how to solve this?

EDIT: I just figured out, that no programm is found in the JACK-Connection-Window... I tried it with audacity, and there is no audacity-device showing up in jack... there are the "system"-entries only.... :(


Btw:  this is the Jack-Message, if I try to set recordmydesktop to use JACK:
load = 0.5898 max usecs: 147.000, spare = 21186.000
> server thread back from poll
new client: lsp, id = 8 type 2 @ 0x7fed7ad44000 fd = 17
start poll on 5 fd's
server thread back from poll
new client lsp using 18 for events
start poll on 5 fd's
14:48:06.887 Schaubild der JACK-Verbindungen geändert.
server thread back from poll
marking client lsp with SOCKET error state = Not triggered errors = 0
trying to lock graph to remove 1 problems
we have problem clients (problems = 1
++ Removing failed clients ...
client lsp error status 10000000
removing failed client lsp state = Not triggered errors = 10000000
removing client "lsp"
removing client "lsp" from the processing chain
+++ deactivate lsp
client alsa_pcm error status 0
client qjackctl error status 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
+++ client is now qjackctl active ? 1
client qjackctl: start_fd=7, execution_order=0.
client event poll on 15 for qjackctl starts at 13212100483
lock-driven null cycle
back from client event poll after 5985 usecs
client qjackctl: wait_fd=9, execution_order=1 (last client).
-- jack_rechain_graph()
-- jack_sort_graph
-- Removing failed clients ...
after removing clients, problems = 0
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
server thread back from poll
start poll on 4 fd's
load = 0.5925 max usecs: 127.000, spare = 21206.000

---

### Post by produnis on 2009-11-22
I just noticed, that in Karmic  recordmydesktop is built WITHOUT Jack-support:

```

produnis@Smeargol:~$ recordmydesktop --print-config

recordMyDesktop was compiled with the following options:

Jack            :Disabled
Default Audio Backend    :ALSA


```

there is a bug-report at [https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/448027](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/448027)

---

### Post by mocha on 2009-12-01
Thanks for this info.

---

### Post by neu2buntu on 2009-12-02
i too was having the same problem as the O.P, but resolved it by downloading the latest source of "recordmydesktop" (same as the 1 i was using , and leaving all my RMD packages installed) and built it by running 
```
./configure --prefix=/usr --enable-jack=yes LIBS=-ljack CFLAGS=-DHAVE_LIBJACK
 
``` and ```
make
``` and ```
sudo make install
```  *note that gtk-recordmydesktop is only the frontend/gui

---

