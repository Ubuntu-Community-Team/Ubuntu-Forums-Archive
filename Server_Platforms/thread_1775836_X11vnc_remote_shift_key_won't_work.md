---
title: "X11vnc remote shift key won't work"
date: 2011-06-05
forum: Server Platforms
---

### Post by Shobuz99 on 2011-06-05
I'm reposting this as a new thread. 
I'm using X11vnc between two machines on my home network.
Both machines are running X11vnc and their OS is Ubuntu 10.04 LTS. 
I'm connecting through the X11vnc SSL/SSH VNC Viewer. 
When I connect to one machine from the other, remotely,
I typically check my email through the Thunderbird email client (latest version).
When I reply to an email, and try to capitalize a letter 
using the "shift" key; it will not work. I have to press the "Caps Lock" key. 
If I want to use an '&' or any other "shift" key characters, I'm out of luck. It's a PITA.
I can't get it to work while in gEdit, either.
I've tried using the -sloppy_keys command and I've tried setting up my keyboard using keyboard shortcuts; but nothing has worked.

Can anyone tell me how to get this to work?

The two machines I'm using are a Desktop(OEM) and a Dell Inspiron 1300 laptop. I have the same problem either direction. 

Thank you for your help

Shobuz99

---

### Post by krunge on 2011-06-05
If you add the option "-dk" to x11vnc you will get debugging output on keystrokes. Watch it while you type. It will tell you which keysyms it received over the wire from the vnc viewer and what key(s) it is pressing to try to inject that keysym.

You can (at the same time if you want) run xev inside the X session being exported by x11vnc to watch what keycodes and keysyms it is receiving from the X server.

Be sure you Capslock isn't screwed up on the remote side (this is a common problem with VNC to get the capslock out of sync between the two sides...)

Also if you have an old version of x11vnc you may need to add the "-xkb" option.

BTW, -sloppy_keys wouldn't solve this problem, it solves a different problem.

---

### Post by Shobuz99 on 2011-06-05
> **krunge said:**
> If you add the option "-dk" to x11vnc you will get debugging output on keystrokes. Watch it while you type. It will tell you which keysyms it received over the wire from the vnc viewer and what key(s) it is pressing to try to inject that keysym.

You can (at the same time if you want) run xev inside the X session being exported by x11vnc to watch what keycodes and keysyms it is receiving from the X server.

Be sure you Capslock isn't screwed up on the remote side (this is a common problem with VNC to get the capslock out of sync between the two sides...)

Also if you have an old version of x11vnc you may need to add the "-xkb" option.

BTW, -sloppy_keys wouldn't solve this problem, it solves a different problem.

Karl,
Thank you very much. All I did was add -xkb to the command line
in my startup command for x11vnc, on both machines, and it works.
Must be I have an older version of x11vnc. 
Maybe I should upgrade :-). 
What is the latest version for x11vnc? The one I have installed is 0.9-9.1 and the ssvnc viewer is 1.0.24-1.
Again, thank you for solving this for me.
BTW.. I removed the -sloppy_keys command anyway. 
Thanks for that advice, too. :-)
Shobuz99

---

### Post by krunge on 2011-06-06
I believe the default behavior was changed in 0.9.10 to avoid the problem you encountered.  x11vnc 0.9.12 was released last year.

---

