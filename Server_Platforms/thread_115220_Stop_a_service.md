---
title: "Stop a service?"
date: 2006-01-10
forum: Server Platforms
---

### Post by bulldogzerofive on 2006-01-10
Hello all

netstat says that a service named hpiod is monitoring ports 32769 and 32770.  I am pretty sure this is hplip, which i believe is necessary for my hp printer.  I find this to be a security risk even though i have a firewall running.  How do I configure this to only monitory eth1, my internal network, rather than the internet on eth0?  Or, how can i configure it not to monitor the network at all?  

I could not find a man page or .conf file at all and the GUI does not seem to have any options for it.

Any help is deeply appreciated.

Thanks



PS: Sorry for the repost, but when I put this in Desktop Support only 12 people even looked at it.  Bad title, I guess.

---

### Post by LordHunter317 on 2006-01-10
Post your netstat output.

---

### Post by bulldogzerofive on 2006-01-10
The first three concern me.  (I am paraniod).  They all have to do with the printer.

Thanks

```
sysadmin@localhost:~$ sudo netstat -tulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost.localdo:32769 *:*                     LISTEN     8581/hpiod
tcp        0      0 localhost.localdo:32770 *:*                     LISTEN     8600/python
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     8551/cupsd
tcp        0      0 localhost.localdom:smtp *:*                     LISTEN     8716/exim4
udp        0      0 *:bootpc                *:*                                7683/dhclient3
sysadmin@localhost:~$
```

---

### Post by LordHunter317 on 2006-01-10
They're all listening locally and are of zero concern.

---

### Post by bulldogzerofive on 2006-01-11
How can I tell that?

---

### Post by LordHunter317 on 2006-01-11
The fact the listening host says 'localhost.localdomain', which is 127.0.0.1, the loopback interface.

---

### Post by bulldogzerofive on 2006-01-13
Hey, sorry to bug you, but I read the man page and I just don't get it.  I haven't been able to find a "netstat for idiots" page on the internet, either.

Could you explain again how you get that from this output?  I was under the impression that as long as a service is "LISTEN" according to netstat, it would listen for all network connections.  I presume that there are many things listening on a local level, such as the X server, but these do not show up in netstat's output.

What is the difference?  Is there a flag for netstat that will filter out locally listening services?

Thanks for your help.

---

### Post by LordHunter317 on 2006-01-13
[QUOTE=bulldogzerofive]Could you explain again how you get that from this output?  I was under the impression that as long as a service is "LISTEN" according to netstat, it would listen for all network connections.[/quote]No, that's never been the case.  Look at the column labeled 'Local Address'.  Only people who can reach taht addresss can talk to the service.  If you run 'netstat -an --inet', you'll see that address is 127.0.0.1, the loopback interface.  Only you can talk to that interface.

---

### Post by bulldogzerofive on 2006-01-17
what does Foreign Address *:* mean?

---

### Post by LordHunter317 on 2006-01-17
It means the kernel will accept any foreign address.  For a listening socket, that's all it'll ever show.

---

### Post by bulldogzerofive on 2006-01-18
Sorry about this, but if the kernel will accept any foreign address, doesn't that mean that this service is listening to the world?

---

### Post by LordHunter317 on 2006-01-18
[QUOTE=bulldogzerofive]Sorry about this, but if the kernel will accept any foreign address, doesn't that mean that this service is listening to the world?[/QUOTE]No, it means that the kernel wouldn't reject a connection based on foreign address.  The local address determines *where* it's listening, the foreign address determines *what* it'll accept.  Accepting any address locally doesn't change the fact only local addresses can talk to you.

---

### Post by bulldogzerofive on 2006-01-19
I understand now.  Thank you for your help.

---

