---
title: "Realtime Bandwidth Monitor 10.10"
date: 2011-04-14
forum: Server Platforms
---

### Post by AmericanSkin on 2011-04-14
I posted this in the Networking section, but should probably be over here. Couldn't move it.

I have a transparent proxy in place. I have Webmin installed on the server.

Is there an app that can monitor bandwidth in real time? Also run reports? I have SARG installed, but seems to only monitor HTTP traffic, I need to monitor all traffic.

I have a bridged connection, but monitoring the outside interface is fine too.

Thanks.

---

### Post by SeijiSensei on 2011-04-14
> **AmericanSkin said:**
> Is there an app that can monitor bandwidth in real time? Also run reports? I have SARG installed, but seems to only monitor HTTP traffic, I need to monitor all traffic.

I like [**ntop**]("http://www.ntop.org/overview.html").

---

### Post by AmericanSkin on 2011-04-14
I ran apt-get install ntop and set the user password.

When I browse to server:3000 i get the error:


Please enable make sure that the ntop html/ directory is properly installed

ERROR 400

Have you seen this? seems others using 10.10 get the same thing.

---

### Post by Doug S on 2011-04-14
I saw this thread and after reviewing the ntop web site, decided to try ntop.
I also did "sudo apt-get install ntop". There were a couple of odd notes during the process, but it seems to have installed O.K.  I set the password that it was asking for also. Upon launch, there was a complaint about RRD being unable to create /var/lib/ntop/rrd, but it seems to be working fine for me (Ubuntu server 10.10). I'll go back and look at the issues later. So far it is only monitoring my internal eth0 card, but I also want it to monitor my external network at eth1. Obviously, I still have some reading to do, I just mention now as reply to AmericanSkin's problems. SeijiSensi, thanks for the reference. By the way, I used "sudo ntop -w 3000 -W 0" to start.

---

### Post by ekool on 2011-04-14
If your looking for more of a graph type thing, nload works well.

---

### Post by R.Bucky on 2011-04-16
You have to first configure a password for ntop.

```
sudo ntop --set-admin-password
or
sudo /usr/sbin/ntop -A

```

[https://help.ubuntu.com/community/Ntop]("https://help.ubuntu.com/community/Ntop")

---

