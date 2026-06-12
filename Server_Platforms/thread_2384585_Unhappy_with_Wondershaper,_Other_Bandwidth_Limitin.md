---
title: "Unhappy with Wondershaper, Other Bandwidth Limiting Options?"
date: 2018-02-08
forum: Server Platforms
---

### Post by mattlach on 2018-02-08
Hey all,

I have a storage server running Ubuntu Server Editition 16.05 LTS I am placing offsite for backups.   

The storage is in ZFS format using ZFS on Linux.   The intent is to do a ZFS Send / Recv via SSH to it every night during low traffic times.

Problem is this.  Occasionally there will be a lot of data, more than can be transferred overnight.   I'd like to control the bandwidth used by this server, so it doesn't keep running at full speed in the morning.

I added the following lines to my crontab:

0 1 * * * /sbin/wondershaper enp7s0f0 76800 7680 >/dev/null 2>&1
0 7 * * * /sbin/wondershaper enp7s0f0 7680 768 >/dev/null 2>&1

This way, at 1 am I allow it to use the majority (but not all) of the bandwidth, and by 7am, I throttle it back significantly.

The problem is, this didn't work at all as expected.   Wondershare throttled the interface WAY more than indicated by the arguments to the command.  I was getting  between 1 and 10% of the bandwidth I indicated.

Can anyone give me any advice here?  Are there better options than wondershare I can use?   I don't really care about any QoS, methods like FairQ, Codel or anything like that.   I just want a straight up customizeable global interface based bandwidth limitation that I can can change on the fly via cron without impacting current connections (other than to slow them down or speed them up)

Any thoughts?

Much obliged,
Matt

---

### Post by LHammonds on 2018-02-11
I've never used wondershaper before but I used some Google-Fu (tm) and came up with this for a command line syntax:

```
wondershaper NetworkInterfaceID DownloadSpeed UploadSpeed
```

The speed is in Kilobits per second (kbps)

Now, before you do anything, you HAVE TO know what your real, actual ISP speed and your interface ID.

To ensure I have the right interface ID, I simply type "route" into the command-line:

```

# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1    0.0.0.0         UG    0      0        0 eth0
192.168.0.0    *               255.255.255.0   U     0      0        0 eth0
```

I only have one interface and I can see it is called "eth0" from the above.

You have not said what your maximum speeds are or how you determined it.

One way to figure this out is with speedtest.net as follows:

```

sudo apt install speedtest-cli
speedtest-cli

```

Example output on my computer:
```
# speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from CenturyLink (8.8.8.8)...
Selecting best server based on latency...
Hosted by Sprint (North Pole, World) [77.16 km]: 57.869 ms
Testing download speed........................................
Download: 6.73 Mbit/s
Testing upload speed..................................................
Upload: 0.43 Mbit/s

```

Keep in mind that such a test is affected by other machines on your network and your network hardware or if you are running inside a VM, the host limitations / limiters.  If running on cable modem, your total speeds are also affected by your neighborhood's usage.  So this is "actual" speed for this particular computer at this particular time of day.

In order to use Wondershaper, convert the Mbit/s output to Kbit/s

6.73 Mbit/s = 6730 Kbit/s (download)
 0.43 Mbit/s = 430 Kbit/s (upload)

To be very specific, let's say I want to always limit this server to a maximum of 10% usage and allow it to have 80% usage at night.

80% of 6730 Kbit/s download speed is 5384 Kbit/s
80% of 430 Kbit/s upload speed is 344 Kbit/s

10% of 6730 Kbit/s download speed is 673 Kbit/s
10% of 430 Kbit/s upload speed is 43 Kbit/s

Here are the commands I would use based on what I discovered above:

```

0 1 * * * /sbin/wondershaper eth0 5384 344 >/dev/null 2>&1
0 7 * * * /sbin/wondershaper eth0 673 43 >/dev/null 2>&1

```

NOTE: It would be best to run the speed test multiple times throughout the day for the entire week to get a good set of actual performance results.  You might find that your max speeds vary considerably throughout the day and on the weekends.

LHammonds

PS - Don't laugh at my net connection...I know it sucks...I live in the country and have all of 1 option for Internet access.

---

### Post by mattlach on 2018-02-11
> **LHammonds said:**
> I've never used wondershaper before but I used some Google-Fu (tm) and came up with this for a command line syntax:

```
wondershaper NetworkInterfaceID DownloadSpeed UploadSpeed
```

The speed is in Kilobits per second (kbps)

Now, before you do anything, you HAVE TO know what your real, actual ISP speed and your interface ID.

To ensure I have the right interface ID, I simply type "route" into the command-line:

```

# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1    0.0.0.0         UG    0      0        0 eth0
192.168.0.0    *               255.255.255.0   U     0      0        0 eth0
```

I only have one interface and I can see it is called "eth0" from the above.

You have not said what your maximum speeds are or how you determined it.

One way to figure this out is with speedtest.net as follows:

```

sudo apt install speedtest-cli
speedtest-cli

```

Example output on my computer:
```
# speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from CenturyLink (8.8.8.8)...
Selecting best server based on latency...
Hosted by Sprint (North Pole, World) [77.16 km]: 57.869 ms
Testing download speed........................................
Download: 6.73 Mbit/s
Testing upload speed..................................................
Upload: 0.43 Mbit/s

```

Keep in mind that such a test is affected by other machines on your network and your network hardware or if you are running inside a VM, the host limitations / limiters.  If running on cable modem, your total speeds are also affected by your neighborhood's usage.  So this is "actual" speed for this particular computer at this particular time of day.

In order to use Wondershaper, convert the Mbit/s output to Kbit/s

6.73 Mbit/s = 6730 Kbit/s (download)
 0.43 Mbit/s = 430 Kbit/s (upload)

To be very specific, let's say I want to always limit this server to a maximum of 10% usage and allow it to have 80% usage at night.

80% of 6730 Kbit/s download speed is 5384 Kbit/s
80% of 430 Kbit/s upload speed is 344 Kbit/s

10% of 6730 Kbit/s download speed is 673 Kbit/s
10% of 430 Kbit/s upload speed is 43 Kbit/s

Here are the commands I would use based on what I discovered above:

```

0 1 * * * /sbin/wondershaper eth0 5384 344 >/dev/null 2>&1
0 7 * * * /sbin/wondershaper eth0 673 43 >/dev/null 2>&1

```

NOTE: It would be best to run the speed test multiple times throughout the day for the entire week to get a good set of actual performance results.  You might find that your max speeds vary considerably throughout the day and on the weekends.

LHammonds

PS - Don't laugh at my net connection...I know it sucks...I live in the country and have all of 1 option for Internet access.


Thanks,

I understand how it works. 

Apparently the version of wonder shaper in the repositories for 16.04 and above is broken.   [See this bug report]("https://bugs.launchpad.net/ubuntu/+source/wondershaper/+bug/1739086").


There is - however - a newer version in [the git repository]("https://github.com/magnific0/wondershaper/").

The commands have changed a bit though, so it's not just a straight drop in replacement.

This newer 1.4 version from git is working exactly as expected for me.

---

### Post by LHammonds on 2018-02-12
> **mattlach said:**
> Apparently the version of wonder shaper in the repositories for 16.04 and above is broken.   [See this bug report]("https://bugs.launchpad.net/ubuntu/+source/wondershaper/+bug/1739086").

There is - however - a newer version in [the git repository]("https://github.com/magnific0/wondershaper/").
Awesome.  Thanks for the info and update.

There is a lot to be said about trial-n-error (you) over theoretical documentation (me). hehehe.

LHammonds

---

### Post by mattlach on 2018-02-14
> **LHammonds said:**
> Awesome.  Thanks for the info and update.

There is a lot to be said about trial-n-error (you) over theoretical documentation (me). hehehe.

LHammonds

Heh,

Well,  I am having problems with this version as well.

The new version works perfectly when issued from the command line as a super user, but when I run it from cron it fails with errors like this:

```
wondershaper: line 124: tc: command not found
wondershaper: line 133: tc: command not found
wondershaper: line 139: tc: command not found
wondershaper: line 146: tc: command not found
wondershaper: line 152: tc: command not found
wondershaper: line 157: tc: command not found
wondershaper: line 158: tc: command not found
wondershaper: line 159: tc: command not found
wondershaper: line 163: tc: command not found
wondershaper: line 168: tc: command not found
wondershaper: line 173: tc: command not found
wondershaper: line 195: tc: command not found
wondershaper: line 207: tc: command not found
wondershaper: line 222: modprobe: command not found
wondershaper: line 226: tc: command not found
wondershaper: line 227: tc: command not found
wondershaper: line 230: tc: command not found
wondershaper: line 231: tc: command not found
wondershaper: line 234: tc: command not found
```

I figured this had to do with the PATH variable not being present when lauching scripts from cron, so I edited the wondershaper script ad added the following line near the beginning:

source /etc/profile

This has worked for me when I have had environment problems in cron in the past, but this time it had no effect.

Any suggestions?

Much obliged,
Matt

---

### Post by LHammonds on 2018-02-14
> **mattlach said:**
> 
Any suggestions?

I put the following at the top of my root's crontab:
```
SHELL=/bin/sh PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Crontab SYNTAX:
# minute(0-59) hour(0-23) day-of-month(1-31) month(1-12) day-of-week(0-6) command-to-execute
```Since your error log was actually running wondershaper, that means crontab was at least able to kick it off (probably because you used the full path to the executable).

But if that is a script in itself that calls other scripts, then problems can arise if that script does not use full paths...unless you have the environment path set beforehand...such as at the top of crontab.

LHammonds

---

### Post by mattlach on 2018-02-14
> **LHammonds said:**
> I put the following at the top of my root's crontab:
```
SHELL=/bin/sh PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Crontab SYNTAX:
# minute(0-59) hour(0-23) day-of-month(1-31) month(1-12) day-of-week(0-6) command-to-execute
```Since your error log was actually running wondershaper, that means crontab was at least able to kick it off (probably because you used the full path to the executable).

But if that is a script in itself that calls other scripts, then problems can arise if that script does not use full paths...unless you have the environment path set beforehand...such as at the top of crontab.

LHammonds

Much obliged.   

Yes, I always use the full path when dealing with cron, as I have been down this path before (no pun intended)

I was under the impression that setting the profile as I did would accomplish the goal of applying all the paths, but I will try your method instead and see how that goes.

Thanks again,
Matt

---

### Post by mattlach on 2018-02-18
> **LHammonds said:**
> I put the following at the top of my root's crontab:
```
SHELL=/bin/sh PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Crontab SYNTAX:
# minute(0-59) hour(0-23) day-of-month(1-31) month(1-12) day-of-week(0-6) command-to-execute
```Since your error log was actually running wondershaper, that means crontab was at least able to kick it off (probably because you used the full path to the executable).

But if that is a script in itself that calls other scripts, then problems can arise if that script does not use full paths...unless you have the environment path set beforehand...such as at the top of crontab.

LHammonds

Well,,

I am completely stuck.

Even with your recommended SHELL and PATH line at the top of my crontab (and a reboot just to make sure) wondershaper still errors out with the same error messages when run from cron, unable to find tc and modprobe:

```
wondershaper: line 124: tc: command not found
wondershaper: line 133: tc: command not found
wondershaper: line 139: tc: command not found
wondershaper: line 146: tc: command not found
wondershaper: line 152: tc: command not found
wondershaper: line 157: tc: command not found
wondershaper: line 158: tc: command not found
wondershaper: line 159: tc: command not found
wondershaper: line 163: tc: command not found
wondershaper: line 168: tc: command not found
wondershaper: line 173: tc: command not found
wondershaper: line 195: tc: command not found
wondershaper: line 207: tc: command not found
wondershaper: line 222: modprobe: command not found
```

Yet, it still works just fine from command line....

This makes no sense...

---

### Post by LHammonds on 2018-02-18
Type the following at the prompt:

```
which tc
```

```
which modprobe
```

That should tell you where the files are located.

Then look at the wondershaper script (assuming it is a script) and find out how it is calling those two commands.

No idea why it would work at the prompt and fail in crontab if the environment is set the same.  Maybe your shell has an extra path to those files that is not being set in the crontab.

LHammonds

---

