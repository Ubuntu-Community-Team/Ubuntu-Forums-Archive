---
title: "X11 (can't open display)"
date: 2007-09-03
forum: Server Platforms
---

### Post by Mungo Hill on 2007-09-03
I've got a newly installed ubuntu machine (penguin) that is telling me this:

john@john-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:84:3A:B3:F4  
          inet addr:10.250.3.205  Bcast:10.250.3.255  Mask:255.255.255.0
 .
.
.
john@john-desktop:~$ xhost
access control disabled, clients can connect from any host
INET:devvo

And I'm ssh-ing onto a nearby linux box called devvo (not using -X) and seeing this on the remote machine:

john@devvo:evoenh[Evo ui dev]$ echo $DISPLAY
penguin:0.0
john@devvo:evoenh[Evo ui dev]$ xeyes
Error: Can't open display: penguin:0.0
john@devvo:evoenh[Evo ui dev]$ ping penguin
PING penguin (10.250.3.205) 56(84) bytes of data.
64 bytes from penguin (10.250.3.205): icmp_seq=1 ttl=64 time=0.420 ms

To me,  that looks like it should work,  but then I see people in forums saying that you need to fiddle with the X11 config files before it will even think about listening for incoming connections.  Is this right?  If so,  what is the nature of the arcane fiddling required?

---

### Post by Mungo Hill on 2007-09-04
Ok,  here's the answer.   By default (and I can't see anything to be proud about here) X doesn't listen for tcp connections.  Yes,  I know there's the ssh -X thing,  but that presupposes a level of intelligence in the X client that simply may not be there.  The issue was fairly thoroughly discussed in:

[http://ubuntuforums.org/archive/index.php/t-85582.html]("http://ubuntuforums.org/archive/index.php/t-85582.html")

but ended up in despair as the supposed fix (to roger /etc/X11/xinit/xserverrc so that it no longer specifies nolisten) either never did work or stopped working at one of the releases.  After changing this setting, X still comes up with 'nolisten'

If you look for the PPID of the X process,  you can see that it is launched by gdm so it seemed likely that it was a problem with the gdm setup.  Sure enough,  if you look at /etc/gdm/gdm.conf you can see a cunningly concealed setting DisallowTCP.  The value of this needs changing from true to false.

Yes,  disallowing X-connections is more secure,  but then so is yanking the RJ45 out of the hub.

---

