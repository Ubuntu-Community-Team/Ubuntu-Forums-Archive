---
title: "making headless server beep on restart"
date: 2012-09-17
forum: Server Platforms
---

### Post by bobwdn on 2012-09-17
I have a headless 12.04LTS server that runs in my closet. When I do system changes and I need to restart sometimes I would like to know that it has finished restarting.

I was reading an older [***post***]("http://www.howtoforge.com/ubuntu-home-fileserver-p3") where users could turn on a beep in a version 7.10 server. I tried what was suggected in this article and it does not work with 12.04LTS. I did install beep and checked the /etc/modprobe/blacklist.conf file to uncomment the *pcspkr* blacklist and I could manually type beep in the command line and I could hear the server speaker beep. Ideally I would like to have the speaker 'beep' when rc has finished.

Has anyone every done this with 12.04LTS server addition?

---

### Post by HugoSerrano on 2012-09-17
Hello!

Add that beep command in the end of /etc/rc.local file, right before "exit 0"

Regards!

---

### Post by dargaud on 2012-09-17
Personally I've never managed to get 'beep' to work on Ubuntu. Something to do with the underlying sound system ? I thought the beep command used the internal speaker of the PC...

---

### Post by SlugSlug on 2012-09-17
Why stop with a single beep??

[http://ubuntuforums.org/showthread.php?t=1157670](http://ubuntuforums.org/showthread.php?t=1157670) :guitar:

---

### Post by thnewguy on 2012-09-17
The beep command doesn't work on my computers, maybe a sound system thing? But mplayer does. If you want you could install mplayer and have it play a short sound clip every time the machine boots. Putting the followint in /etc/rc.local should do the trick

mplayer /path/to/sound.wav

---

### Post by bobwdn on 2012-09-17
Currently I am not using a IPCop box or a Smoothwall box. But i have in the past. Both of these firewall programs create a beep tone emitted by the system speaker to indicate completion of the start up sequence.

(HughSerrano, your suggestion of the end of rc.local did not work. Sorry.)

I did some reading of the beep man file. I have now created a /etc/rcbeep.sh file. I have given it executable permissions. This file contians: ```
#!/bin/bash
beep -l 300 -f 329.6 -n -l 300 -f 370 -n -l 300 -f 523.2
```
This produces three tones when I type (in a command line) ```
rcbeep.sh
```

Now the question is where in the start up sequence do I insert a line calling the rcbeep.sh file?

---

### Post by SlugSlug on 2012-09-17
either in rc 5 i think or in cron like

```
@reboot /path/to/beep.sh
```

---

