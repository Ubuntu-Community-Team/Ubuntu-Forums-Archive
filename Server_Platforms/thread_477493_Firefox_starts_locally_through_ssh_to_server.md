---
title: "Firefox starts locally through ssh to server"
date: 2007-06-18
forum: Server Platforms
---

### Post by dAF2000 on 2007-06-18
This is my first post (although I'm not a newbie ;)) and I've got a problem I don't understand.

I have a server running 6.06 alternate edition and a laptop running 7.04 for normal daily use. I connect from the laptop to the server through ssh using X forwarding. This all works fine. I open the ssh connection to the server using "ssh 192.168.1.60" (which is IP of server).

However, if I have firefox running on the laptop and type "firefox" in the ssh terminal, firefox on the laptop starts instead of the firefox on the server. I can recognize it because it opens the Ubunu 7.04 welcome screen and the bookmarks are from the firefox on the laptop.

If I don't have firefox running on the laptop, typing firefox in the ssh terminal really starts up firefox on the server. This is really a strange problem which only appears with firefox. "xterm" for example, works fine, the server xterm is started and shown on the laptop. Why should firefox behave other than xterm for example?

---

### Post by anath3ma on 2007-06-23
yep, just ran into the same problem here.

¨firefox¨ is a shell script that runs firefox-bin after doing lots of random setup stuffs.  

from what ive read, apparently firefox does some x11 messaging to your display to try to determine if it should start up a new instance of firefox or just open a new window on an existing instance. obviously, if firefox is already started locally then the LOCAL binary gets the message to spawn a new window.  if not, then the message goes to the ssh X11 forward.

the answer seems to be in a firefox script rewrite.  this is something i have not found on sourceforge or through google (even tho many people have the problem).  i might do this myself if i have the time in the next few weeks.

adobe tools are said to have the same problem.
ive seen similar problems with evolution if you have an instance running on the remote host.

---

### Post by anath3ma on 2007-06-23
ok... just looked at the script... there is nothing of worth in there.
so, the aforementioned messaging is happening in the binary.
that is to say... we are screwed. (unless you feel like rewriting some c and getting it submitted to firefox)   

only place to look now is firefox lists to see if somebody maybe made a patch already.

---

### Post by anath3ma on 2007-06-23
found two ways to do it.both are total hacks....

first:
run a rootless xserver like xming or cygwin under wine and run firefox as the start app.

second:
run 
firefox -ProfileManager

this appears to skip the braindead code that cant distinguish between local and foreign instances of firefox running on the same x11 server. though this is another bug, it works in our favor.

e.x.
add a ¨custom application launcher¨ in your top panel with this as the commandline
ssh -X servername -f firefox -ProfileManager

---

### Post by dAF2000 on 2007-06-29
Thanks!
I couldn't find "strange" things in the startup script either. I will try your ProfileManager approach.

---

### Post by sas13 on 2007-07-04
another way to get firefox is to start on the the remote computer is to use the "-no-remote" option:
```
ssh -X <remotehost>
firefox -no-remote

```

---

### Post by dAF2000 on 2007-07-06
> **sas13 said:**
> another way to get firefox is to start on the the remote computer is to use the "-no-remote" option:
```
ssh -X <remotehost>
firefox -no-remote

```
That did the trick and is even easier \\:D/

---

### Post by devif0 on 2007-08-08
Thanks for the hint. It is a precious one.

---

