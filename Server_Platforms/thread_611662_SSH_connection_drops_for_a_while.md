---
title: "SSH connection drops for a while"
date: 2007-11-13
forum: Server Platforms
---

### Post by nublaii on 2007-11-13
I have ubuntu-server 7.04

Every once in a while my ssh connection drops, and I can't connect for a while. Then it suddenly starts working again.

While that happens everything else works fine... I can access apache, and even webmin. SSH is the only thing affected.

I use shorewall, but I tried disabling it for a while and it still happens, so it's not my firewall.

From webmin I can see port 22 still responds as open.

syslog doesn't show anything out of the ordinary...

So the question is: how can I tell if the router is responsible for the disconnections or if it's my provider closing my access for a while?

---

### Post by meatpan on 2007-11-13
Just curious, are you SSH'ing to or from your ubuntu server?   Some ISP's will drop connections that do not respond after a certain time period.  My work-around/hack has been to run 'top' during the times I'm not actively using the connection.  This isn't a very good solution, especially because top can sometimes consume up a lot of system resources.

---

### Post by MJN on 2007-11-13
> **meatpan said:**
> My work-around/hack has been to run 'top' during the times I'm not actively using the connection.  This isn't a very good solution, especially because top can sometimes consume up a lot of system resources.

No need for that - just set **ClientAliveInterval <x>** to some value of x (in seconds) in your SSHD config file (/etc/ssh/sshd_config) and the server will send a request to the client every x seconds and expect a response back from it. This is done 'in band', i.e. within the encrypted channel, and hence is genuine client-server session traffic which will stop the ISP disconnecting you.

Mathew

---

### Post by doanut on 2007-11-13
Really shouldn't have a ssh connection sitting idle for so long. Its normal as no data is being sent to and from in a ssh connection and hence the session times out.

---

### Post by nublaii on 2007-11-14
I ssh TO the box. And it's not idling for too long... sometimes it happens after less than one minute... sometimes it takes a little longer, but never more than 5 minutes.

I added this line to my ssh_config

```
ServerAliveInterval 60
```

and this to my sshd_config

```
TCPKeepAlive yes
ClientAliveInterval 60
```

but it still happens.

What is strange is that the service then is unavailable for a while (I haven't been able to establish for how long). The ssh server is still running, and everything else (ftp, email) still works perfectly. It's just the ssh port that is closed...

---

### Post by MJN on 2007-11-14
Sorry, I should've been clearer with my response - my suggestion was to Meatpan as to how he can stop the automatic timeout of idle SSH connections by his ISP.
 
This won't be applicable to you as a cancelled TCP session wouldn't stop an immediate re-connection.
 
Assuming you have access to the server LAN, are SSH connections to the server from a LAN client via the WAN address of the router subject to these kind of dropouts? The purpose of this test is try and pinpoint the problem to either the server or the router (i.e. leaving the ISP and remote client out of the equation for now).
 
Mathew

---

