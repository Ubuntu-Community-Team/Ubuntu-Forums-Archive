---
title: "Need a ping script"
date: 2013-10-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Last_Ship on 2013-10-08
[COLOR=#000000][FONT=Verdana]I need to write (or acquire) a script that continuously pings a site (google will do), and then execute a sound file if my internet connection drops out. The reason for this is that I have an application that needs to be constantly connected to the internet and if that connection drops out, which it does, I need to know immediately so that I can reset the connection. Is such a script difficult to write? Any insight would be greatly appreciated. Thanks in advance. Also, I apologize if this topic is misplaced here. If so, I'll gladly take my request elsewhere.[/FONT][/COLOR]

---

### Post by Lars Noodén on 2013-10-08
You can use exit codes from programs like ping in conditional statements like "if".

This uses "play" from Sound eXchange

```

#!/bin/sh
while sleep 60;
do
  if ! ping -c 1 -w 1 8.8.8.8 > /dev/null; then
    /usr/bin/play /usr/share/sounds/freedesktop/stereo/camera-shutter.oga > /dev/null 2>&1
  fi
done

```

Edit: you can choose a target closer to you than 8.8.8.8, such as your gateway, and still verify connectivity.

---

### Post by Last_Ship on 2013-10-08
Great, thank you. This can be input in the gnome scheduler? I'd prefer to use to gui as opposed to the cron command line if possible.

---

### Post by Lars Noodén on 2013-10-08
It can be run from cron.  The GUI for cron is just that, a GUI.  So it goes to the same place as the text interface.  So you have a choice of  how you access cron but the finished product is the same.

---

### Post by Last_Ship on 2013-10-08
Thanks alot, I appreciate the help. So I can replace the 8.8.8.8 with any IP address that I'd like it to ping, correct? Also, I would simply replace [COLOR=#000000][FONT=Ubuntu Mono]/usr/bin/play /usr/share/sounds/freedesktop/stereo/camera-shutter.oga[/FONT][/COLOR] with the path to my sound file? Thanks again.

---

### Post by Lars Noodén on 2013-10-08
Also be sure to test it, maybe unplug the network cable or something, to make sure it plays sounds on your system.  I had to add "play" from the package "sox" on my system, but maybe it is there on yours.  As far as the notification sound goes, look around for files ending in .oga and give them a try to find one that is insistent without being too annoying.  

As an afterthought, the while loop should be discarded if you are running from cron.  Just use the "if" statement by itself.

---

### Post by Lars Noodén on 2013-10-08
> **matt2422 said:**
> Thanks alot, I appreciate the help. So I can replace the 8.8.8.8 with any IP address that I'd like it to ping, correct? Also, I would simply replace [COLOR=#000000][FONT=Ubuntu Mono]/usr/bin/play /usr/share/sounds/freedesktop/stereo/camera-shutter.oga[/FONT][/COLOR] with the path to my sound file? Thanks again.


Yes 8.8.8.8 can be replaced with any ip address.  The closer to the machine, the better.  

The sound file can be anything that you can find on your system that "play" can use.

Again, if you are running from cron, take out the while loop so you don't end up with dozens and dozens of the script running at the same time.  If you have only one copy running, then the loop is needed.  But if you are using cron to do the work, then the loop gets in the way.

---

### Post by mörgæs on 2013-10-08
> **Lars Noodén said:**
> The closer to the machine, the better. 

+1. People running a server somewhere might not be happy with receiving an infinite stream of pings.

---

### Post by Last_Ship on 2013-10-08
Good point. I'll set it to ping my gateway

---

### Post by Last_Ship on 2013-10-08
So here's what I've got. Doesn't seem to be working. I'm sure I must have done something wrong, anything blaringly obvious?[IMG]http://i.imgur.com/FeSsp8p.jpg[/IMG]

---

### Post by Erik1984 on 2013-10-08
I think it's easier to save the code in a file, make it executable and enter the full path of the file as the command. So if it's somewhere in your home folder /home/yourname/scriptfilename

---

### Post by Last_Ship on 2013-10-08
[INDENT] 					So here's what I've got. Doesn't seem to be working. I'm sure I must have done something wrong, anything blaringly obvious?
[/INDENT]

[IMG]http://i.imgur.com/FeSsp8p.jpg[/IMG]

---

### Post by Last_Ship on 2013-10-08
Good idea, thanks, I'll try that.

---

### Post by Last_Ship on 2013-10-08
Looks like it's working now. Thanks so much for your help! Just one more quick question. Is this written in python then? or is it a shell script? Sorry for my ignorance, just trying to learn.

---

### Post by Lars Noodén on 2013-10-09
Scripts always point to the interpreter in the first line.  Since we see **#!/bin/sh** at the beginning, we know it is a shell script.  Specifically it uses dash instead of bash.  That's smaller, faster and more portable.  Bash is more complex, slower and a superset of POSIX.

Perl, Python, and shell are the main interpreters used. 

```

#!/usr/bin/python
#!/usr/bin/perl
#!/bin/sh
#!/bin/bash
#!/usr/bin/mawk

```

and so on.

---

### Post by Lars Noodén on 2013-10-09
I just now noticed in your screen shot that you are pointing to an internal address (192.168.0.3) which will be local to your LAN.  So polling that address will only tell you if your LAN is working not your Internet connection.  If you take the next address out, that should be on the Internet and polling it will tell you if your Internet connection is up or not.  You can use [traceroute](http://linux.die.net/man/8/traceroute) to find the next steps in your network:

```

traceroute -n google.com

```

Look for the ip numbers outside of your LAN, they should usually be steps #2 or #3 and often end in .1   

You may have to install the package "traceroute" from the repository.  I'm kind of surprised it is no longer included by default.

---

### Post by Last_Ship on 2013-10-09
Got it, thank you.

---

### Post by Last_Ship on 2013-10-09
Other than that though, the way I entered the command into the scheduler without the interpreter line., as ```
 [COLOR=#000000][FONT=tahoma]if ! ping -c 1 -w 1 192.168.0.3 > /dev/null; then /usr/bin/play [/FONT][/COLOR][COLOR=#000000][FONT=tahoma]/usr/share/sounds/freedesktop/stereo/phone-outgoing-busy.oga > /dev/null [/FONT][/COLOR][COLOR=#000000][FONT=tahoma]2>&1 [/FONT][/COLOR]
``` 

looks correct?

---

### Post by Lars Noodén on 2013-10-09
It looks good, but the closing **fi** got cut off.  Each **if** needs a matching **fi**.  Put it at the very end of the line and it should be all set.  You can also try it by pasting it into the shell in a terminal and see for sure.   See the section "Compound Commands" in the manual page for  bash for the official explanation.

---

### Post by Last_Ship on 2013-10-09
So by using #2 or 3 on the traceroute, I'll be pinging my ISP correct?

---

### Post by Lars Noodén on 2013-10-10
If you've got the usually single layer of NAT, hops #2 or # should be what you want.  Your address in the screenshot was 192.168.0.3 which is on the 192.168.0.0/16 private network.  So you're looking for the first address off that network.   If you have the standard network arrangement then that next address will be a router at your ISP.

---

