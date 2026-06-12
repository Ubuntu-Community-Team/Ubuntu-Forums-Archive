---
title: "Port 80,443 and 25 closed?"
date: 2014-05-04
forum: Security
---

### Post by cogset on 2014-05-04
There will be a logical explanation for this,which however I can't find,so I have to ask:I use ufw as a firewall front end (iptables is just too hard for me as of now),having  most default services disabled or removed altogether as I don't need them (think ssh,samba) nmap finds all ports  closed when scanning the computer from itself using ```
nmap -sTU  -vv  --reason  -p 1-65535
nmap -A  -vv  --reason  -p 1-65535
```however I can actually browse the web and use a mail client with no issues.
Shouldn't I find port 80,443 and 25 open when scanning?

Furthermore,using the **--top-ports** option with nmap I get this

```
25/tcp    closed smtp         conn-refused
53/tcp    closed domain       conn-refused
80/tcp    closed http         conn-refused
443/tcp   closed https        conn-refused
```

so,what gives?

Is there something wrong with my firewall,or am I definitely missing something here?

---

### Post by steeldriver on 2014-05-04
I think what you're missing is the distinction between incoming and outgoing (or more precisely, *established*) connections. Ports like 25, 443, 80 are only required to be open for incoming connections to mail and web *servers *- your regular web traffic and emails are usually on random high-numbered ports which allow incoming packets once the connection has been established.

See [https://en.wikipedia.org/wiki/Stateful_firewall#Description](https://en.wikipedia.org/wiki/Stateful_firewall#Description)

---

### Post by Lars Noodén on 2014-05-04
You can see your current connections with [netstat](http://manpages.ubuntu.com/manpages/trusty/en/man8/netstat.8.html)

```

netstat -ntup

```

iptables, via UFW, is set to allow 'established' and 'related' connections back in.  All connections are allowed out.  So if you make an outgoing connection, the response is allowed back in.  If you look carefully at the ip numbers and port numbers you can see what is connecting to what.  You can see that you are connecting to ports 80 and 443 on the remote machines, not your own.

---

### Post by cogset on 2014-05-05
Thanks,that is starting to make more sense to me:looking more carefully at netstat,I can now clearly see that ports 80 and 443 are indeed accessed on the source of the connections,whereas on my end those same connections do actually terminate  on random high-numbered ports.
There are however still a couple of points that escape me:
[LIST]
[*]if I scan my computer *while* browsing the web,shouldn't I see those exact high-numbered ports matching the active connections listed as open? Or are those connections too random to be considered by nmap?
[*]looking at Thunderbird's settings,I can see port 110 pop listed for incoming mail and 25 smtp for the outgoing server,are those still the ports meant to be used on the actual mail server I'm connecting to,and not on my own computer?
[/LIST]

---

