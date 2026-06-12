---
title: "Utility for data transfer limits?"
date: 2008-11-20
forum: Unanswered Posts Team
---

### Post by nixscripter on 2008-11-20
Hey guys. Hopefully people still read this forum.

I've been running around answering posts on the networking forum for a while, and there are some questions which seem to come up over and over. One which I have been quite baffled by is something like this:

> 
I've got a really annoying ISP who charges me based on how much data I transfer over their connection. If I go over 1 GB in a month, they hit me with a huge bill! How can I make my internet connection disconnect after 1 GB?


The bottom line is a request for a program that would poll network interface(s), and store the total data transferred, including across reboots and disconnects. Then, when a specified limit is reached, at the very least warn the user.

I'm sure that several of us could hack together a shell script (maybe even a GTK application :)), but I'm wondering if there is a general-purpose networking package which could do this already with some tweaking.

---

### Post by iponeverything on 2008-11-20
> **nixscripter said:**
> Hey guys. Hopefully people still read this forum.

I've been running around answering posts on the networking forum for a while, and there are some questions which seem to come up over and over. One which I have been quite baffled by is something like this:



The bottom line is a request for a program that would poll network interface(s), and store the total data transferred, including across reboots and disconnects. Then, when a specified limit is reached, at the very least warn the user.

I'm sure that several of us could hack together a shell script (maybe even a GTK application :)), but I'm wondering if there is a general-purpose networking package which could do this already with some tweaking.

using the counters in iptables works quite well for keeping a running tally, but the it starts over after a reboot. Cacti, does a good job as well -- one of the templates keeps totals and would it would keep the data across reboots.  I have not heard of anything that does what is described though..  

It seems like it would be a cool app though. It could project when it thinks that your going to hit the 1G wall and if it's before the end of the billing cycle -- it could throttle your bandwith through the stretch.

---

### Post by nixscripter on 2008-11-21
About half an hour of spare time got me this (sorry for the length):
```

#!/usr/bin/env python

#
# ifmon.py
#
# ifmon.py -- a prototype network throughput monitor for Linux
# Copyright (C) 2008 nixscripter@gmail.com
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# version 2 as published by the Free Software Foundation (not any
# later version).
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
# 02110-1301, USA
#

import re, os, sys

# default statistics file: $HOME/.ifpoll/stats
sf=os.path.join(os.environ['HOME'],".ifpoll"+os.path.sep+"stats")

ifaces = {}
def init(statfile): # reads data from previous boots, called first thing
    if os.path.exists(statfile):
      for line in file(statfile):
        iface, nbytes = line.strip().split(":")
        iface = iface.strip()
        nbytes = nbytes.strip()
        ifaces[iface] = int(nbytes)
    assert os.path.exists("/proc/net/dev")
    for line in file("/proc/net/dev"):
        line = line.strip()
        m = re.search(r"^(\w+):\s*(\d+)", line)
        if not m: continue
        iface = m.groups()[0]
        if iface not in ifaces.keys(): ifaces[iface] = 0

def save_data(statfile): # writes data collected, called by signal handlers
    for line in file("/proc/net/dev"):
        line = line.strip()
        m = re.search(r"^(\w+):\s*(\d+)", line)
        if not m: continue
        iface, nbytes = m.groups()
        if iface not in ifaces.keys(): ifaces[iface] = 0
        ifaces[iface] += int(nbytes)
    if not os.path.exists(os.path.dirname(statfile)):
        os.mkdir(os.path.dirname(statfile))
    f = file(statfile, 'w')
    for iface in ifaces.keys():
        f.write("%s:%d\n" % (iface, ifaces[iface]))
    f.close()

def since_last_reboot(interface):
    assert os.path.exists("/proc/net/dev")
    for line in file("/proc/net/dev", 'r'):
        line = line.strip()
        m = re.search(r"^(\w+):\s*(\d+)", line)
        if not m: continue
        iface, nbytes = m.groups()
        if iface == interface: return int(nbytes)
    return 0

def main(args):
    if len(args) < 1:
        print "Expected arguments"
        return False
    cmd = args.pop(0)
    if cmd == 'reset':
        save_data(sf)
        print "data saved (in preparation for reboot)"
        return True

    if len(args) < 1:
        print "Expected arguments"
        return False
    iface = args.pop(0)
    if not iface in ifaces.keys():
        print "Unknown interface '%s'" % iface
        return False
 
    if cmd == 'last':
        l = since_last_reboot(iface)
        print "interface has recieved ",l,"bytes of data since last reboot"
    elif cmd == 'total':
        t = ifaces[iface]
        l = since_last_reboot(iface)
        if not t or not l:
            print "Unknown interface '%s'" % iface
            return False
        print "interface has recieved ",(t+l),"bytes of data"
    else:
        print "Invalid command"
        return False
    return True

init(sf)
if not main(sys.argv[1:]):
    print "Usage: %s { reset | last | total } interface" % \
        os.path.basename(sys.argv[0])
    sys.exit(1)
else:
    sys.exit(0)

```

Python is one of my good languages, and has GTK+ bindings.

My assumption is that the kernel stats are saved forever until the interface disappears. Then someone has to use the "reset" function to save the totals and consider the ones it gets next time as new.

---

### Post by ajmorris on 2008-11-26
very nice nix...
I dont think anyone uses, or are even aware of the canned responses on the tracker... But, realistically, it is a spot on the tracker, to which any team member can add a reply, that will appear in an RSS feed, should you subscribe to the canned responses via the firefox RSS function... You might consider adding it :)


AJ

---

### Post by nixscripter on 2008-11-27
Well, that script was a start. I just wanted to make sure the idea would work in terms of tracking across reboots. Two big things are missing:

1. Checking a limit.
2. Providing a mechanism to do something when you hit that limit.

Also, the usage is somewhat awkward: someone would have to write an init script on shut down (or start up) through some other mechanism.

As for the GUI, I might enjoy designing one, but I don't know if it would be a good idea. I fear it would lull a less-than-astute user into a false sense of security. PyGTK, for example, swallows assertions and exceptions generated by callbacks, which could cause all sorts of strange behavior.

---

