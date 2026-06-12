---
title: "server hangs every few days for no apparent reason"
date: 2008-06-11
forum: Server Platforms
---

### Post by mayesjc on 2008-06-11
Previously, I used opensuse 10.3 as my server on a machine, with no issues whatsoever for months. For a bunch of reasons, both technical and philosophical, I decided to switch to a debian-based system for the server. The installation was done on Memorial Day, and with the exception of the typical issues (nvidia drivers), it was great. Since that time, I have had a recurring, and unpredictable problem where the system starts slowing and eventually freezes. It will also hang if I try to reboot from the command line, and I eventually use the SysRq keys to restart the system.

A few other facts that may be relevant:

I generally do not access the machine through the console, but through an ssh connection. The connections are made both from LAN clients and WAN clients. The are often made with a key, and often with a password. Generally, the connections are great. I will often notice the slowness first when editing a text file over ssh. I cannot imagine that this matters, however.

Also, once the slowing starts, I cannot use the "top" command, either over an ssh connection or at the console. Indeed, if I try to login at the server, Gnome will be very unresponsive, and even once I get out, and stop the X server, the system is still slow.

The system as 1.25gb RAM, and the swap is almost never necessary.

I thought about starting over with a fresh install, but this seems to be a very sloppy way to address the problem. I would much rather hang in there and find out what is going wrong, and otherwise the server is "dialed-in."

After the last reboot, I stopped the X server to see if that might be part of the problem.

Has anyone else had a similar problem and have suggestions on where to start?  Incidentally, the CPU temperature is always below 35 degrees Celcius.  Also, I am interested in whether the problem is more likely hardware or software related.

Thanks.

Jeff

---

### Post by cdenley on 2008-06-11
What kind of servers are you running? Are you using hardy, gutsy, or dapper? How did you disable X?
```

sudo update-rc.d -f gdm remove

```
Did you find anything useful in the logs? Did you ever notice any data loss when you were forced to reboot?

---

### Post by anindya_m on 2008-06-11
Is there any hard disk activity when the server begins to slow down?

---

### Post by molotov00 on 2008-06-11
> **cdenley said:**
> What kind of servers are you running? Are you using hardy, gutsy, or dapper? How did you disable X?
```

sudo update-rc.d -f gdm remove

```
Did you find anything useful in the logs? Did you ever notice any data loss when you were forced to reboot?

It's a question I'm sure he'll ask and if not, I'm curious. Which logs would you recommend looking at for an issue like this?

---

