---
title: "Tune-Up ubuntu server (Hardy 8.04 lts) for 100mbit seedbox"
date: 2010-03-16
forum: Server Platforms
---

### Post by AnotherNoob on 2010-03-16
Hi guys, i was searching for some improvement tips to make most of my ubuntu server with 100mbit dedi line, settings like

maximum open connection
RAM limits
Harddisk read/write tunning
Open file limits
all these kind of tuning tips 

i m running rtorrent, want to make it handle atleast 500 torrents with more than 10k open files

Thanks for help

---

### Post by KB1JWQ on 2010-03-16
I'd run it stock out of the box, and see where you start getting constrained, THEN tweak.

Changing a bunch of stuff you don't understand because some stranger on the internet told you to is a recipe for disaster; if something goes wrong you'll have no idea where to look.

---

### Post by AnotherNoob on 2010-03-16
well i already did some settings, so i was just asking if there are any others which can help or some series of tweaks

---

### Post by tgalati4 on 2010-03-16
man vmstat

Run vmstat for a while and collect some statistics.  Unless you provide some specific issues, it's hard to give advice.  What is the hardware?  How much RAM?  What kind of disks?  Real servers have dual gigabit cards (such as the Dell poweredge series).  Are you running dual network cards?

Sometimes software tuning doesn't do anything because you are limited by hardware.  The server scheduling parameters are optimized for most workloads.  And those workloads can be intense.

I'm not familiar with rtorrent, but userland applications tend to break way, way before the kernel gets loaded.

Run htop and watch what is happening when your machine is loaded:

sudo apt-get install htop

htop

---

### Post by KB1JWQ on 2010-03-16
Well said.  

As it stands today, Ubuntu ships out of the box in a pretty well optimized state for most workloads.

Show evidence of a bottleneck, and you'll have people jumping down your throat trying to help resolve / work around it-- but until that happens, you SHOULD be good to go.

---

### Post by AnotherNoob on 2010-03-24
okay, i m stuck with open file limits, my rutorrent cant open files more  than 10370 but i changed it to more than that at everywhere, i mean every  possible guide you can find on google :(

ulimit -a shows this 

core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 16120
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 65000
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 16120
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

---

