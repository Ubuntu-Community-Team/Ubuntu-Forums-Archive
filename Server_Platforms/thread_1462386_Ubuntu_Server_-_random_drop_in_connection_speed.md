---
title: "Ubuntu Server - random drop in connection speed"
date: 2010-04-25
forum: Server Platforms
---

### Post by BoxFace on 2010-04-25
Hi guys,

Me and my friends recently got our hands on a Linux server hosted by OVH, with the intention of hosting our game servers and other things. We're fairly new to Linux, but we're not new to computers so we generally know what we're doing, and we can figure things out through the power of Google.

Progress started slowly, but eventually we setup NX Machine, FTP, webmin and we can get a Left 4 Dead server going. Things were fine, until we noticed that the server would take about 2 minutes to change a map *sometimes* and occasionally it would change a map in 2 seconds.

We also noticed that eventually connecting to the server using NX and FTP became occasionally really slow. It would establish a connection, and then hang for about 2 minutes before it did anything. :confused:

The server itself should be able to cope with standard stress, it's a Quad Core 2.4ghz, 4gb RAM with 1TB HDD, but for some reason it just isn't performing well. We're on version 8.04.

My question is this - what's the best way of finding out what's actually causing a problem in Ubuntu? We may be forced to use just SSH through PuTTy, as I can't even connect using NX Machine to get a GUI properly anymore.



--------- UPDATE ---------

Just a small update on what's happening, we've used the company's service to check each of the components. The HDD, processor and RAM appears to be functioning fine. We then reinstalled the OS, thinking that we may have messed up a file.

It reinstalled fine, we installed mumble. It works fine, but we still get the occasoinal longer-than-neccessary wait to connect. We found that when you get the "hanging" when the server is unresponsive for a bit, the system monitor states that "mumble.x86" is uninterruptible.

Any ideas why the process would suddenly become uninterruptible?

---

### Post by NullHead on 2010-04-25
Honestly it sounds like an internet problem on the server's side. What I would do, is ping google from your side, and use the server to ping google. Compare pings, if yours is higher than the server's, then you know it's your own internet issue. If it the server's is higher than your own, then you know it's indeed the server. 

Generally speaking, I wouldn't think that any software would be causing this kind of issue unless you're on a shared CPU.

---

### Post by BoxFace on 2010-04-25
I've just run a ping on both machines as you recommended, my server got a better ping than my current machine.

The server seems to be able to connect to things fine, just not actually do anything very well.

---

### Post by NullHead on 2010-04-25
Then it sounds like you're on a shared host. Either your disk activity is slowing down because of the amount of data needing to be loaded for the L4d server, or somebody else is really stressing out the machine.

---

### Post by BoxFace on 2010-04-25
But that's the interesting thing, we're not on a shared host at all, I'm 100% sure of it.

I've just checked the resource monitor, all cores are fine and unstressed, and up and downstream aren't high.

We've installed Mumble on it recently (basically a VOIP chatroom like Ventrilo), even when the L4D server is not running sometimes joining the hosted room can take a minute, other times it's instant.

---

### Post by BoxFace on 2010-04-25
Also, you mentioned disk activity, how can we monitor the speed etc?

---

### Post by NullHead on 2010-04-25
> **BoxFace said:**
> Also, you mentioned disk activity, how can we monitor the speed etc?

You can use iotop to measure disk activity. ```
sudo apt-get install iotop
```

Then run "*iotop*" and take a looksee at what's being read/written at what speeds.

---

### Post by BoxFace on 2010-04-26
We just tried running iotop, we're getting the following error message -

```
Could not run iotop as some of the requirements are not met:
- Linux >= 2.6.20 with I/O accounting support (CONFIG_TASKSTATS, CONFIG_TASK_DELAY_ACCT, CONFIG_TASK_IO_ACCOUNTING): Not found
```

---

### Post by BobVila on 2010-04-26
if you want to measure your throughput, run iperf

You'll need a pair of publicly addressable IPs, but it'll be a helpful test to run.

On the "client" (I'd run this on the server, myself, but you can do it either way):
```
iperf -c [TARGET IP ADDRESS] -t 60 -i 5
```

On the "target":
```
iperf -s
```

You'll need to shut down the firewall on the target for the duration of the test to make sure the client can bind to port 5001.

The -t 60 option sets the time to 60 seconds. If you'd rather test for a longer period, set it to a higher number (in seconds, of course).

---

### Post by ghost_ryder35 on 2010-04-26
You should also install SAR if it is not already installed and then once it collects data you can view to see if you have any load trends happening that may be causing this performance issue.

```

sudo aptitude install sysstat
sudo vi /etc/default/sysstat

```
Change ENABLED="false" to true
```

# Should sadc collect system activity informations? Valid values
# are "true" and "false". Please do not put other values, they
# will be overwritten by debconf!
ENABLED="true"

```

You can use that data that it collects to create a baseline for you system (what it should look like under normal situations).  When you see the problem again look at sar and see if you can see if anything is not normal.

You can view that data with 
```

# To view current days data
sar 
# To view previous days data
sar -f /var/log/sysstat/<filename something like sa##>

```

---

### Post by BoxFace on 2010-04-26
Hi guys, thanks for all your responses, they've all been helpful.

Just a small update on what's happening, we've used the company's service to check each of the components, the HDD, processor and RAM appears to be functioning fine. We then reinstalled the OS, thinking that we may have messed up a file.

It reinstalled fine, we installed mumble. It works fine, but we still get the occasoinal longer-than-neccessary wait to connect. We found that when you get the "hanging" when the server is unresponsive for a bit, the system monitor states that "mumble.x86" is uninterruptible.

Any ideas why the process would suddenly become uninterruptible?

---

### Post by ghost_ryder35 on 2010-04-26
the process is waiting on something and wont respond to anything other than what it is waiting on.  I know that doesnt help, but perhaps you could strace it to see what system calls it is making/waiting on.  

Another idea is perhaps one of your DNS servers is not working?  Long shot

---

### Post by BoxFace on 2010-04-26
We've managed to do a strace on mumble when it does the hanging thing, but it spews up  at least 1000 lines, which none of us understand.

From what we can gather from the strace is that there is some form of looping looking messages, which don't happen normally.

Any tips on how we can understand these messages?

---

### Post by ghost_ryder35 on 2010-04-26
you could put the log on paste.ubuntu.com and everyone reading the thread can help us sift through them.

---

### Post by NullHead on 2010-04-26
> **ghost_ryder35 said:**
> you could put the log on paste.ubuntu.com and everyone reading the thread can help us sift through them.

+1 to that. 

I'll take a looksee.

---

### Post by BoxFace on 2010-04-26
Here's the strace from using Murmur (Mumble's server) of what we captured when it was doing the uninterruptible thing. See if you guys can make any sense of it. [http://paste.ubuntu.com/423087/](http://paste.ubuntu.com/423087/)

---

### Post by NullHead on 2010-04-26
That really doesn't do anything for me lol. 

Maybe it's SQlite lag?

---

