---
title: "Enable Logging for attempted connection on a closed port"
date: 2013-11-27
forum: Security
---

### Post by termvrl on 2013-11-27
Hi all,

I would to know how we can set/enable a syslog logging for an attempted connection on a closed port.
I want to test for a port knocking. for e.g ; If received a attempted connection on higher port such as port 12345 three time it will start a sshd service.

Thanks for your reply.

---

### Post by Lars Noodén on 2013-11-27
You could enable logging of attempted connections on closed ports using iptables.  Add a rule at the end of your INPUT chain that logs anything that gets that far down the chain.  You'll of course want the earlier rules to jump out of the chain for cases you don't want to log.  However, if this is on a machine facing the public Internet, such logs will be *enormous* and 99.998% a waste of time.  Basically your machine gets scanned more or less continuously from the moment it gets connected.  

As to [port knocking](http://bsdly.blogspot.com/2012/04/why-not-use-port-knocking.html), it's not such a great idea.  I'm pretty sure it could be implemented in iptables, too, but again it's not such a great idea.  If you wish to increase the security of sshd, disable password login and require keys.  That's easy  to do.  Also disable remote root login.

---

### Post by bashiergui on 2013-11-27
This is intriguing. Why do you want to open a service after detecting knocking?

---

### Post by Doug S on 2013-11-27
> **Lars Noodén said:**
> You could enable logging of attempted connections on closed ports using iptables.  Add a rule at the end of your INPUT chain that logs anything that gets that far down the chain.  You'll of course want the earlier rules to jump out of the chain for cases you don't want to log.  However, if this is on a machine facing the public Internet, such logs will be *enormous* and 99.998% a waste of time.I do exactly what Lars described, and have been doing it for years. It actually isn't so bad in terms of log file size (I don't recall the last time I reset my iptables, but it is on the order of several days, and 7817 packets have hit my catch all rule at the end of the INPUT chain).

---

### Post by bashiergui on 2013-11-27
What do you do with the log Doug S?

---

### Post by Doug S on 2013-11-27
> **bashiergui said:**
> What do you do with the log Doug S?The first thing I need to say, is that I am a bit of a fanatic about this stuff. And yes, most of the time, the /var/log/syslog file just lapses without being looked at in detail. However, I often find myself investigating some network anomaly (both internal and/or external) or external attack, after it has occurred. Having good logs merely aids in going back and figuring out what happened. More in general, if I observe a spike in packets hitting the INPUT chain catch all rule, I'll dig deeper. Coincidentally, looking at my /var/log/syslog file just now I see something odd (but innocent) on my LAN that I will to look into.

OP: Sorry, for the slight digression on your thread.

---

### Post by clearski on 2013-11-27
> **Lars Noodén said:**
> As to [port knocking]("http://bsdly.blogspot.com/2012/04/why-not-use-port-knocking.html"), it's not such a great idea.  I'm pretty sure it could be implemented in iptables, too, but again it's not such a great idea.  If you wish to increase the security of sshd, disable password login and require keys. 

I know it's a little bit offtopic, but how hard is to crack a 64 characters long password like this one?

```
XcEsMi>Y+\kS}u(mB[7vlA!7o:YsL*C8NHUQ(Xt>]Uf#VUiS1F+/:,x(_
```

And, actually, what's the maximum length for a password on (Ubuntu) Linux, is it 255 characters?

I am asking because some people (including an author of a book about SSH) suggested having a *backup* user (so, it is strictly an exception, not a rule) with a Match term in sshd_config that would be allowed to use passwords, in case that, somehow, a user which usually uses passwordless logins would be unable to use this type of login (he is locked out because he forgot to upload a new version of the keys on the server before an exit, for example).

---

### Post by termvrl on 2013-11-27
Hi All,

Thanks for your reply.

First of all, what im trying to do is for a syslog analysis. i have a centralized syslog server that received logs from security devices, such as firewall, ids, waf and servers.
As im testing some perl script that can be used as a "port knocking", but the tutorial is on BSD system. 

Here below i paste the original tutorial,

```

  To start, consider the following syslog messages from a BSD based system: 

Jun 27 15:02:51 foohost /kernel: Connection attempt to TCP 127.0.0.1:7777 from 127.0.0.1:1806 flags:0x02
Jun 27 15:02:58 foohost /kernel: Connection attempt to TCP 127.0.0.1:5555 from 127.0.0.1:4356 flags:0x02
  
 These messages are sent to syslog by the kernel in response to an attempted connection on a closed port. 
 To see these message, two sysctl variables net.inet.tcp.blackhole and net.inet.udp.blackhole have to be set.  
 The required commands are:        
 $ sysctl  net.inet.tcp.blackhole=1         and         $ sysctl  net.inet.udp.blackhole=1

```

And the perl program use regex to match with the logs.
So i asking if ubuntu can provide the same or similar type of logs, so that i can manipulate the regex to match it.

And thanks to Lars and Doug for share the port knocking using iptables. i will consider to use iptables as alternative solution to generate the logs.

Thanks again.

---

### Post by Lars Noodén on 2013-11-27
How old is the FreeBSD tutorial you are looking at?

net.inet.tcp.blackhole seems to determine the same as iptables REJECT or DROP targets do.  If you have a choice, I would recommend REJECT over DROP.  Here are two commentaries on the topic:

[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)
[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)

For the OUTPUT chain, there's really only trouble from DROPping.  For INPUT, you have to add REJECT as the last rule in the chain because it's not an option for the default policy.

---

### Post by termvrl on 2013-11-27
Hi,
The tutorial was written on 2004.Is it outdated or irrelevant anymore?
It will try your suggestion on the iptables first. I will give a feedback on it.

---

### Post by Lars Noodén on 2013-11-27
I'd say it's pretty outdated.  

As far as the port-knocking goes, I'm pretty sure you can implement that purely in iptables.  There's probably an example somewhere or you can spend enough time looking at the options (see the manual page [iptables-extensions](http://manpages.ubuntu.com/manpages/saucy/en/man8/iptables-extensions.8.html))  Keys are the better way to go instead.

---

### Post by bashiergui on 2013-11-27
I'm with Lars Nooden on this. I would set up IPTables and then send the IPTables logs to your centralized log server. 
The method you described might work, but you're describing the function of a firewall so why not use a firewall to do it?

---

### Post by CharlesA on 2013-11-29
> **clearski said:**
> 
I am asking because some people (including an author of a book about SSH) suggested having a *backup* user (so, it is strictly an exception, not a rule) with a Match term in sshd_config that would be allowed to use passwords, in case that, somehow, a user which usually uses passwordless logins would be unable to use this type of login (he is locked out because he forgot to upload a new version of the keys on the server before an exit, for example).

As long as you are using a strong password, you should be fine.

I have my server set up to allow me to login via password from the local network, but that's only cuz I got sick of copying keys over to the VMs I would create and destroy while testing things.

With that being said, I prefer keys but I also login as a non root user and then su to root if I need to do admin tasks.

---

### Post by clearski on 2013-11-29
> **CharlesA said:**
> As long as you are using a strong password, you should be fine. 

Thanks for the reply, it's always good to know how far one should go with each option he got.

Sorry again for being off-topic.

---

### Post by ian-weisser on 2013-11-29
> **termvrl said:**
> I would to know how we can set/enable a syslog logging for an attempted connection on a closed port.
I want to test for a port knocking. for e.g ; If received a attempted connection on higher port such as port 12345 three time it will start a sshd service.

Perhaps I don't understand the question - knockd already logs both successes and failures.

---

### Post by termvrl on 2013-12-11
> **ian-weisser said:**
> Perhaps I don't understand the question - knockd already logs both successes and failures.


Hi all,

Thanks for the reply.
i not use knockd because what im trying to do here is basically, to write a program looking for an attempt on closed port based on syslog generated.
If the combination is correct than allow to open the port.

Thanks.

---

### Post by ian-weisser on 2013-12-11
Seems like you essentially want to duplicate the knockd functionality.
Nothing wrong with that, a good way to learn. Have you, by chance, looked at the knockd source code to see how that developer solved a very similar problem? Without duplicating it, his approach may give you good ideas.

You can monitor the log you use for dropped connections from IPTables
Or you can monitor failed connections in /var/auth/log

---

