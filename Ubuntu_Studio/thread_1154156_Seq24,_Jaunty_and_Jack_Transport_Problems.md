---
title: "Seq24, Jaunty and Jack Transport Problems"
date: 2009-05-09
forum: Ubuntu Studio
---

### Post by theluddite on 2009-05-09
Whenever I try to set seq24 to use the jack transport so that I can sync it with Ardour, seq24 doesn't trigger my synth anymore.  

I updated to Jaunty and had the problem already reported on this forum with seq24 crashing whenever you create a new pattern.  I solved it by compiling the latest version (0.9.0).  I'm still getting this error on startup which I think is the source of the problem:
> theluddite@big-machine:~$ seq24
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Failed to connect to LASH.  Session management will not occur.
Reading [/home/theluddite/.seq24rc]
Reading [/home/theluddite/.seq24usr]
Error Reading [/home/theluddite/.seq24usr]

Maybe seq24 can't connect to the Jack Transport port?  Oddly, when I use the keyboard in seq24, I can trigger the synth, it's only when I try to use the midi sequencer that nothing happens.  I've tried enabling the transport from the command-line and no dice.

---

### Post by theluddite on 2009-05-19
Has anyone been able to use seq24 and ardour successfully?  Maybe I'm missing something obvious?

---

### Post by theluddite on 2009-05-22
This is definitely a seq24 problem and unrelated to Jaunty.  Hydrogen has no trouble syncing with Jack and the problem still persists even with no other apps open (i.e. Ardour).  I downgraded to Hardy and still have the same problem.  Can anyone share a working seq24rc file?  Maybe if I change the port seq24 syncs on (i.e. 14541)?

---

### Post by theluddite on 2009-05-23
I was waaay off.  It turns out I needed to enter one of my seq24 patterns in the song editor window.  I clicked on the button at the bottom right of the main window and used the tool to draw in one of my patterns.  I'm not clear on why this is necessary when using the Jack Transport as master, but this finally allowed me to sync seq24 with ardour.

---

