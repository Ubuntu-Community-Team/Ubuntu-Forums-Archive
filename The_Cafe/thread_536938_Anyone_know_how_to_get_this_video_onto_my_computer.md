---
title: "Anyone know how to get this video onto my computer?"
date: 2007-08-28
forum: The Cafe
---

### Post by IgnacioMiller on 2007-08-28
Hey all,

I've been trying to somehow get this movie ([http://www.wfsb.com/video/13984822/index.html?taf=hart]("http://www.wfsb.com/video/13984822/index.html?taf=hart")) onto my computer. I succeeded in using the Firefox mplayer plugin to get a file ([mms://a92.v25576e.c25576.g.vm.akamaistream.net/7/92/25576/v0001/vod.ibsys.com/2007/0827/13984822.200k.wmv]("mms://a92.v25576e.c25576.g.vm.akamaistream.net/7/92/25576/v0001/vod.ibsys.com/2007/0827/13984822.200k.wmv")) from the server, however that file appears to just stream the video into totem. I also tried replacing the mms:// protocol with http:// but it did not change anything, I still got a file that streamed things in totem. Are there any programs (windows or Linux, I have access to both) that will allow me somehow either record what totem is playing or rip the video off of the site?

Thanks! I really want to have this special performance forever!
Dan
Ubuntu Linux User of 1 year

P.S. I apologize if this is in the wrong forum, it isn't quite a technical problem, I'm just searching for a method so I did not feel that it should be placed in the General Help or multimedia forum. I'm sorry if it should have been.

---

### Post by raijinsetsu on 2007-08-28
You'd have to do something which may be technically illegal(depends on your country)... However, there is a process called "stream-ripping".

---

### Post by christhemonkey on 2007-08-28
```
mplayer mms://a92.v25576e.c25576.g.vm.akamaistream.net/7/92/25576/v0001/vod.ibsys.com/2007/0827/13984822.200k.wmv -dumpstream -dumpfile test.wmv 
```

Something along those lines.

---

### Post by IgnacioMiller on 2007-08-28
Hey,

Thanks for the replies guys. After inputting that command into my terminal and running it, I received this message:

```
dan@dan-desktop:~$ mplayer mms://a92.v25576e.c25576.g.vm.akamaistream.net/7/92/25576/v0001/vod.ibsys.com/2007/0827/13984822.200k.wmv -dumpstream -dumpfile test.wmv
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3500+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://a92.v25576e.c25576.g.vm.akamaistream.net/7/92/25576/v0001/vod.ibsys.com/2007/0827/13984822.200k.wmv.
STREAM_ASF, URL: mms://a92.v25576e.c25576.g.vm.akamaistream.net/7/92/25576/v0001/vod.ibsys.com/2007/0827/13984822.200k.wmv
Resolving a92.v25576e.c25576.g.vm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a92.v25576e.c25576.g.vm.akamaistream.net
Resolving a92.v25576e.c25576.g.vm.akamaistream.net for AF_INET...
Connecting to server a92.v25576e.c25576.g.vm.akamaistream.net[72.215.224.54]: 1755...
Connected
unknown object
file object, packet length = 1200 (1200)
unknown object
unknown object
unknown object
stream object, stream ID: 1
stream object, stream ID: 2
unknown object
data object
mmst packet_length = 1200
Cache size set to 64 KBytes
Stream not seekable!


```

I'm to research stream-ripping and see what I can come up with.

Thanks again!
Dan

---

### Post by IgnacioMiller on 2007-08-28
Oops! Nevermind! It worked! Thanks so much christhemonkey! I owe ya one!

Dan

---

### Post by christhemonkey on 2007-08-28
No worries. I have a copy of that file as well now (tested that command) what a random video!!

---

