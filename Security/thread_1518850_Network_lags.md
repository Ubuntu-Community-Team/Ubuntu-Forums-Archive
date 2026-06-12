---
title: "Network lags"
date: 2010-06-27
forum: Security
---

### Post by noone123 on 2010-06-27
Hi!
I'm using Ubuntu Server x64-86.
```
uname -a
Linux home 2.6.31-21-server #59-Ubuntu SMP Wed Mar 24 08:26:06 UTC 2010 x86_64 GNU/Linux
```
There seem to be problems with network that goes trough iptables, but doesn't seem to cause problems to SSH, but only for such servers like HTTP, FTP, maybe DNS and some other servers like Half-Life.
All I have found is this error and a lot of it:
```
nf_conntrack: table full, dropping packet
```
I did increase the size of the table, but that didn't help, did reduce the time for timeout, but also didn't help.
What I think is that my server is under DoS (or some kind of other attack) attack or the server is lagged by a script/app.
What could I do to fix this problem?

---

### Post by CharlesA on 2010-06-27
We would need more information on how IP tables is set up. Does flushing the rules for iptables cause the delay to go away?

---

### Post by noone123 on 2010-06-27
Is there a way to disable all rules instead of deleting them?
I have many rules there that are used for NAT and other, but everything worked before, even after I added all those iptables rules.

---

### Post by CharlesA on 2010-06-27
Do you load them from a file?

You can use iptables-save to save them to a file so you won't have to type them all in again.

Just make sure that the default policy isn't set to deny when you flush the rules.

---

### Post by noone123 on 2010-06-27
I flushed them using this small tutorial: [http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html](http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html)
Still the same.
Actually it is now weird!
Few times HTTP server works fine and sometimes it doesn't.

---

### Post by CharlesA on 2010-06-27
It sounds like the problem lies elsewhere. Does the same thing happen on any other machines on the network?

---

### Post by noone123 on 2010-06-27
Actually there are no other computers on the network.
There is a virtual server on the computer that gets internet from iptables with NAT, but this virtual server works fine.
How could I check those 2 things that I mentioned, about app lagging the network or an attack.

---

### Post by CharlesA on 2010-06-27
Not sure about how to find out if something to hogging bandwidth. You can see if you are getting DoS by checking logs.

---

### Post by noone123 on 2010-06-27
Can you help me find the right log files?
I have many virtual hosts for HTTP and each one uses another log file.

---

### Post by CharlesA on 2010-06-27
I don't know what log files to check unfortunately.

---

### Post by noone123 on 2010-06-28
I found a solution.
Is KeepAlive needed?
It is now disabled, no more lags.

---

### Post by CharlesA on 2010-06-28
Not sure what it's used for, but I did find this:

[http://www.perlcode.org/tutorials/apache/tuning.html](http://www.perlcode.org/tutorials/apache/tuning.html)

---

### Post by cdenley on 2010-06-28
> **noone123 said:**
> I found a solution.
Is KeepAlive needed?
It is now disabled, no more lags.

Almost all web servers and web browsers use KeepAlive if available. It allows the browser to re-use the same TCP connection for many requests. With it disabled, the browser has to establish a new TCP connection for each image, style sheet, javascript file, etc. for each page the user visits.

If disabling KeepAlive fixes a problem, then perhaps someone keeps starting new KeepAlive connections to use up all of apache's threads. Check [http://servername/server-status](http://servername/server-status). If you can't browse that URL through localhost, you can grant permission by editing /etc/apache2/mods-enabled/status.conf, then restarting apache.

---

### Post by noone123 on 2010-06-28
Then it is best to keep it enabled.
The server doesn't lag with these settings:
```
MaxKeepAliveRequests 2
KeepAliveTimeout 3
```
But server-status does seem to have more then just 2, actually 47 each refresh, KeepAlive connections.
Is it normal that one IP has about 5 connections opened?
There are about 8 different IPs and they all use KeepAlive and is using the same page (currently doesn't even exist).

---

### Post by cdenley on 2010-06-28
> **noone123 said:**
> Then it is best to keep it enabled.
The server doesn't lag with these settings:
```
MaxKeepAliveRequests 2
KeepAliveTimeout 3
```
But server-status does seem to have more then just 2, actually 47 each refresh, KeepAlive connections.
Is it normal that one IP has about 5 connections opened?
There are about 8 different IPs and they all use KeepAlive and is using the same page (currently doesn't even exist).

I do not think it is normal for one IP to have 5 connections, unless that IP is shared by multiple systems which are using your site, or that user is downloading a few large files. Having 8 connections to your server isn't unusual if your site typically has 8 users browsing your site simultaneously. Were they idle? Was that after setting the 3 second timeout?

Limiting KeepAlive requests to 2 per connection kind of defeats the purpose of KeepAlive requests. I guess they only need half as many connections as without KeepAlive.

---

