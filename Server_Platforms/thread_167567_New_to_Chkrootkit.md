---
title: "New to Chkrootkit"
date: 2006-04-28
forum: Server Platforms
---

### Post by Hygelac on 2006-04-28
I just learned about 'Chkrootkit,' which I have downloaded and executed.  Most of its results came back in a way that was obviously good (i.e.: Searching for LOC rootkit... nothing found).  However, I noticed a few odd lines:
```
Searching for suspicious files and dirs, it may take a while...
/usr/lib/blender/.Blanguages /usr/lib/blender/.bfont.ttf /lib/modules/2.6.12-10-amd64-generic/volatile/.mounted
...
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/dhclient3[6305])
```
So, are those indications of a problem or is all well?  (I know essentially nothing about security at the moment, although I want to start.)

---

### Post by Zimmer on 2006-04-28
Looking at the Readme files for this :quote:
> 
the hidden processes problem *seems* to be a thing of the past.  mostly it
was due to the difference between how threads were reported under 2.4 and
2.6.

the hidden files issue continues to crop up now and again.  basically,
if chkrootkit sees a hidden file (a file that begins with .) under
/usr/lib, it flags it as suspicious.  there are various packages that
contain these hidden files and they are innocuous.  however, it appears
that arbitrary hidden files under /usr/lib is a sign of a rootkit, so,
again, it's the safe vs sorry argument.

the well known port issue also comes up frequently.  the problem is that
many well known ports are also used by rootkits (to get around firewalls
and as camouflage).  chkrootkit doesn't currently do any additional
checking when it finds a process listening on a port that's known to have
been used for a rootkit.

the sniffer check is just an informational check, it doesn't necessarily
mean that you've been rooted.  there are several legitimate sniffers out
there; however, you may still want to check that the sniffer is the one
that you think it is, etc.

below is a (non-exhaustive) list of packages that are known to cause false
positives.  before filing a bug report, please check this list.

listens on well known ports
  *radius: the Slapper worm listens on 1812
  postfix-tls: bindshell listens on port 465
  exim-tls: bindshell listens on port 465
  cfs: bindshell listens on port 3049.
  bitlbee: LDP worms listen on port 6667
  mldonkey-server: bindshell listens on port 4000
  portsentry: listens on several ports that chkrootkit sees as rootkit ports

legitimate sniffers
  pppoe
  dhcpd
  ethereal
  p0f
  tcpdump

hidden files
  r-cran-hmisc
  scilab
**  blender**
  geomview
  blackdown java
  kaffe
  obliq
  tiger
  twiki
  viewglob
  subversion

---

### Post by RavenOfOdin on 2006-04-29
I wouldn't concern myself with dhclient.

---

### Post by Hygelac on 2006-04-29
I am glad to know that dhclient is not a concern.  As for Blender, I know that it is itself a perfectly legitimate program; I just did not know why it bothered Chkrootkit.  Thanks for the help.

---

