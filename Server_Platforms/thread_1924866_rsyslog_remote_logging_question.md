---
title: "rsyslog remote logging question"
date: 2012-02-13
forum: Server Platforms
---

### Post by azharahs on 2012-02-13
Here's my scenario.

I have an Ubuntu 11.10 firewall acting as my NAT/gateway, with rsyslog configured to log any entries from iptables to a seperate logfile.

Behind that gateway, I have an Ubuntu 10.10 server acting as a home file/media server and webserver.

I'm trying to figure out how to get rsyslog on the firewall machine to send only the iptables logging messages to the internal server.

I'm sure it's simple, and I'm just missing something somewhere.

Thanks in advance for any assistance.

---

### Post by ruffEdgz on 2012-02-14
My first question is:

Did you enable logging for iptables?

To do that, you just need to add this line near the end of the iptables list (just above your last iptables statement that might be about dropping). The way below is how I do it on my machines if I want to log information:
```

iptables -A INPUT -j LOG --log-level 4

```
This will log the iptables request into level 4 which happens to be WARNING.

So now we have logging setup on iptables, which logging module does it go to? Well, it happens to go through the kernel logging module. If you want to make sure the iptables logs are being recorded, you will need to make sure this line is appended to your /etc/rsyslog.d/50-default.conf file:
```

kern.warning	 /path/to/iptables.log

```
Make sure to change the **"/path/to/iptables.log"** to the location you want the logs to go to.

After that is added to rsyslog config file, you will need to restart the service: 
```

sudo service rsyslog restart

```

Now you should have iptables logging internally.

I found a reference that should help as well if there is any confusion about this here: [http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html](http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html)

---

### Post by azharahs on 2012-02-17
Thanks for the reply.  Sorry for taking so long to come back.

Yes, I have logging enabled for iptables, running locally on the firewall server.  The logs are currently being sent via rsyslogd, to /var/log/iptables.log

What I want to do is send those log entries to the internal server, for logging there.

Thanks again for your help.

---

### Post by ruffEdgz on 2012-02-17
When you say 'internal server', do you mean another server outside of the box that is collecting the iptables logs?

If so, you just need to add something like this to your rsyslog.conf file:
```

kernel.warning          @server1.example.com

```
The first column is for the type of logs while the second column is for which destination you want (the '@' sign is to help rsyslog know that you want to send it to a remote server).

To make sure your other box is ready to accept the rsyslog request, this site has a good tutorial on how to set it up: [http://techtots.blogspot.com/2011/12/rsyslog-enabling-remote-logging-service.html](http://techtots.blogspot.com/2011/12/rsyslog-enabling-remote-logging-service.html)

Hope this helps.

---

### Post by azharahs on 2012-02-28
That does what I need.  Thanks!

---

