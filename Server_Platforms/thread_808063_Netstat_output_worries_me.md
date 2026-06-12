---
title: "Netstat output worries me"
date: 2008-05-26
forum: Server Platforms
---

### Post by Nicklas Overgaard on 2008-05-26
Hi everybody,

Today i ran the "netstat" command on my web / mysql server facing the web. It gave me the following output, which makes me wonder if the server has been compromized?

```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 ish-srv:mysql           137.164.143.114:12984   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:5984    TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:2107    TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:60068   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:8365    TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:20107   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:54553   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:21659   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:28801   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:58754   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:42746   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:56632   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:54470   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:61269   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:3518    TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:34292   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:53278   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:51474   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:23242   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:36452   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:39872   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:56052   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:65127   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:48184   TIME_WAIT  
tcp        0      0 ish-srv:mysql           137.164.143.114:57696   TIME_WAIT  

```

I've tracked the IP down, and it belongs to something called "CENIC" (Corporation for Education Network Initiatives in California). Why is MySQL waiting for connections from/to them?

[EDIT]
If i continue to execute netstat, some of the "TIME_WAIT" changes to "Establised" and "SYN_RECV". I have shut down MySQL for now. I would really appreciate any input on this matter.

Regards,

Nicklas

---

### Post by Monicker on 2008-05-26
I would run tcpdump or wireshark to see what is in the traffic between the remote ip and machine.  I would also see about contacting somebody with that organization for assistance.

If you are unsure about how to proceed, you could ask for help from a group such as the following:  [http://isc.sans.org/]("http://isc.sans.org/")

---

### Post by Nicklas Overgaard on 2008-05-26
Thank you, I will try with wireshark at first, and see if I can find anyone to contact at CENIC.

---

### Post by Nicklas Overgaard on 2008-05-26
I have been sniffing with wireshark on the server now, and it seems that the CENIC server is brute force attacking MySQL. There is a lot of "MySQL response errors" in which it says "Access denied for user root (using password=yes)".

What would be the command to create an IPtable entry which would provide "anti hammering" on the MySQL port?

/Nicklas

---

### Post by Monicker on 2008-05-26
Here is a modification of a rule that was posted in another thread recently

```
iptables -I INPUT -p TCP -s 137.164.143.114 -m state --state NEW -m limit --limit 1/hour -j ACCEPT
```

This should limit that particular ip address to one connection attempt per hour.


For something more generic for all connections to mysql.

```
iptables -I INPUT -p TCP --dport 3306 -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

You may want to toy with the values and see what suits you best.


I would definitely preserve your current evidence and contact someone at CENIC, since they may not be aware of what is going on.

---

### Post by Nicklas Overgaard on 2008-05-26
Thanks a lot Monicker :)

I will play around with the IPtable commands. I have already written a mail to them, and I have MySQL logfiles in place with all the connection information etc (and of course the wireshark dump).

---

### Post by garethsimpsonuk on 2008-05-26
so someone's on to your server? sorry im a noob. is it a big business server? should I worry about this on a small family / home business / hobby server? sorry 4 jackin ur thread i just wanted to quickly ask!

---

### Post by Nicklas Overgaard on 2008-05-26
> **garethsimpsonuk said:**
> so someone's on to your server? sorry im a noob. is it a big business server? should I worry about this on a small family / home business / hobby server? sorry 4 jackin ur thread i just wanted to quickly ask!

Yeah, they are trying to gain access to MySQL. It is a "very small business server" - if you can say so :)

if your server is not accessible from the internet then i don't think that you should bother that much.

---

### Post by garethsimpsonuk on 2008-05-27
Thanks for your reply. So do you think it's just a kid with nothing better to do or could it actually be corporate sabotage? My server is accesible from the net and I have stuff like webmin & torrent flux. 
Have you heard back from that organisation? How are you gonna step up ur security now?

---

### Post by Nicklas Overgaard on 2008-05-27
> **garethsimpsonuk said:**
> Thanks for your reply. So do you think it's just a kid with nothing better to do or could it actually be corporate sabotage? My server is accesible from the net and I have stuff like webmin & torrent flux. 
Have you heard back from that organisation? How are you gonna step up ur security now?

I have had no response from the organization yet, but i really dont think that we are talking corporate sabotage.

The "iptables" commands that Monicker provided should yeld the protection, by preventing anyone to connect more than a few times pr hour. This is good, as the attack they are currently utilizing is connecting multiple times pr. second.

---

### Post by gtdaqua on 2008-05-27
sorry to hijack this thread - i have a concern on this issue too. One of our linux servers is directly facing the internet and I find rogue attempts to enter via ssh. One notorious IP 59.106.12.79 has been trying to logon via ssh2 all day today using several usernames - admin, root, oracle, cvuser, cvuser1. I had to deny this host on my internet edge router. 

where do you normally look for ssh events in linux server itself ("/var/log/")?

---

### Post by gtdaqua on 2008-05-27
> ]
The "iptables" commands that Monicker provided should yeld the protection, by preventing anyone to connect more than a few times pr hour. This is good, as the attack they are currently utilizing is connecting multiple times pr. second.


Dont u think u shud ban this IP across the network rather than just banning on one server?

---

### Post by garethsimpsonuk on 2008-05-27
is it possible that this organisation has nothing to do with it and someones using them as a proxy? or maybe it's a uni campus or something and someones sat in there dorm doing it.
I think it's a good idea for administrators to invite someone knowledgeaable here, to attack the server once it's set up just to see if it's vunerable.
Once mine is done I think I may try that

---

### Post by gtdaqua on 2008-05-27
> **garethsimpsonuk said:**
> is it possible that this organisation has nothing to do with it and someones using them as a proxy? or maybe it's a uni campus or something and someones sat in there dorm doing it.
I think it's a good idea for administrators to invite someone knowledgeaable here, to attack the server once it's set up just to see if it's vunerable.
Once mine is done I think I may try that

By default, Linux machines do not listen on any port unless a service  specifically runs on the background. You don't have to open or close anything manually. For e.g. Port 3306 is closed by default but once you install MySql, Ubuntu opens the port. The only thing you have to worry is all the unsolicited traffic knocking your closed ports. They can always knock but can never get in. What bothered me was there were several knocks by the same IP address and so thats been prevented from entering the network itself (not just the server).

But yes, by all means, conduct a controlled vulnerability analysis. It is those best practices but with Linux, its debatable if you need it.

---

### Post by Nicklas Overgaard on 2008-05-27
> **gtdaqua said:**
> Dont u think u shud ban this IP across the network rather than just banning on one server?

I have set the outer firewall to drop all connections from that specific IP. The iptable thing is just to slow down the process if other hosts launches an attack.

You can block the SSH attack with the follwing iptables command (found via google):

```

iptables -I INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -m recent --set --name DEFAULT --rsourc
iptables -I INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -m recent --update --seconds 180 --hitcount 4 --name DEFAULT --rsource -j DROP

```

This will allow 3 connections from one host, then it will block that specific host for 3 minutes.

---

### Post by gtdaqua on 2008-05-27
> **Nicklas Overgaard said:**
> I have set the outer firewall to drop all connections from that specific IP. The iptable thing is just to slow down the process if other hosts launches an attack.

You can block the SSH attack with the follwing iptables command (found via google):

```

iptables -I INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -m recent --set --name DEFAULT --rsourc
iptables -I INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -m recent --update --seconds 180 --hitcount 4 --name DEFAULT --rsource -j DROP

```

This will allow 3 connections from one host, then it will block that specific host for 3 minutes.

Thanks, Nicklas. I dont want to do IPTables. I would be happy to block the machines permanently and shut them out. You block ssh, the punter will try someother port. There is no reason why that machine shud access the server/network at all if its trying to guess gain access. 

But I do understand IPTables allow granular control.

---

### Post by gtdaqua on 2008-05-27
But I do want to know where the ssh failed attempts logs are stored. I know /var/log - but which file/folder exactly here?

---

### Post by Nicklas Overgaard on 2008-05-27
> **gtdaqua said:**
> But I do want to know where the ssh failed attempts logs are stored. I know /var/log - but which file/folder exactly here?

Okay. I think it's called "auth.log"-. But try to search the forums for DenyHosts, it traverses the logs automatically and adds offending hosts to your "hosts.deny". Here you can also setup syncing between multiple severs etc.

---

### Post by gtdaqua on 2008-05-27
Thanks! That reveals what I need.

---

### Post by windependence on 2008-05-27
> **gtdaqua said:**
> Thanks, Nicklas. I dont want to do IPTables. I would be happy to block the machines permanently and shut them out. You block ssh, the punter will try someother port. There is no reason why that machine shud access the server/network at all if its trying to guess gain access. 

But I do understand IPTables allow granular control.

Yep, there's no reason they should but they do, and they do it all day every day.


Go out to grc.com and at least do a port scan on yourself. Most people are not very security conscious especially when they are running Linux because they think they can't be hacked. The only secure computer is one that is turned OFF. If you really want good security, you should run something like OpenBSD for an OS. Linux is good, and certainly miles better than Windoze, but it does get hacked, and more often than you think. The best solution is to run a good hardware firewall in front of all your machines. If you run a software firewall, someone can still launch a DOS attack on you using a botnet or zombies and can saturate your machine with TCP/IP requests even though they can't get in. Your software firewall takes up CPU cycles and they will just hammer you until your machine is overlaoded. With a hardware firewall, all these packets are dropped at the firewall, and the untit is built to withstand this type of abuse.

-Tim

---

### Post by NateMan on 2008-05-27
I second the hardware firewall idea. An older pc would be a great one, using some sort of bsd based distribution. I prefer pfsense, but there are many out there. I have not been impressed with linux's security vs. bsd.

---

### Post by windependence on 2008-05-27
> **NateMan said:**
> I second the hardware firewall idea. An older pc would be a great one, using some sort of bsd based distribution. I prefer pfsense, but there are many out there. I have not been impressed with linux's security vs. bsd.

I run FreeBSD and OpenBSD on all of my webservers. Linux is only used as a host for VMware. I share your opinion about security.


-Tim

---

### Post by NateMan on 2008-05-27
Yeah I'm using linux for my servers, although they really don't do webpages, except for testing development. Plus everything is stuck behind a very secure bsd-based firewall. I've found most people just don't even bother to mess with the bsd box, and go about looking for less secure and more juicy targets.

---

### Post by dendrobates on 2008-05-27
> **windependence said:**
> I run FreeBSD and OpenBSD on all of my webservers. Linux is only used as a host for VMware. I share your opinion about security.


-Tim

I'm sorry, but this is absurd.  While OpenBSD is known for having few remote root exploits as shipped.  As soon as you run any package like apache or mysql and open it to the internet, there is essentially no difference.  FreeBSD is not known for security.  In fact, Linux and all UNIX-like OS's are vulnerable to the same sorts of attacks.  If you think running BSD is protecting you from anything more than Linux kernel exploits, you are wrong.

The real question that we should be asking the poster, is why he is running mysql listening on the Internet without TCP wrappers and ipchains configured to only allow specific hosts through.  In this configuration, there is no OS that can prevent brute force attacks. 

Rick Clark
Manager Ubuntu Server and Security Teams

---

### Post by NateMan on 2008-05-27
Yeah I don't think that bsd servers are any more secure, but I know that my bsd based firewall/router is more secure than similar linux varieties. That however is due to software not the os itself. And I don't believe it is due to the core of bsd being more secure, but just that the actual software used for it is better. But that's why I put my servers behind it.

---

### Post by windependence on 2008-05-27
> **dendrobates said:**
> I'm sorry, but this is absurd.  While OpenBSD is known for having few remote root exploits as shipped.  As soon as you run any package like apache or mysql and open it to the internet, there is essentially no difference.  FreeBSD is not known for security.  In fact, Linux and all UNIX-like OS's are vulnerable to the same sorts of attacks.  If you think running BSD is protecting you from anything more than Linux kernel exploits, you are wrong.

The real question that we should be asking the poster, is why he is running mysql listening on the Internet without TCP wrappers and ipchains configured to only allow specific hosts through.  In this configuration, there is no OS that can prevent brute force attacks. 

Rick Clark
Manager Ubuntu Server and Security Teams

While I share your opinion that once you open up to the web you are vulnerable, I don't think Nate and my point is absurd at all. First, all of the *BSDs come locked down and you have to open what you want. Second, unlike any flavor of Linux, one does not generally install third party packages on OBSD or FBSD, the packages are audited by the development team and built especially for the platform. I can run a Linuc package on *BSD, but I can't usually run a *BSD package on Linux because they are not binary compatible.

That all being said, I am not a purist at any rate and have been running Linux distros for various purposes for years. I applaud Canonical for making a server version that I have to do little to to make it do what I need without all the fluff of some distros. I am also very excited about JEOS since I run almost everytihng virtualized now.

I think we can all agree that security needs to be a proactive thing no matter what OS you are running.

-Tim

---

### Post by gtdaqua on 2008-05-28
Ok, I simply did:
```

sudo apt-get install denyhosts

```

And created an empty file: /etc/hosts.deny. Thats it. Restart your denyhosts daemon and brute force on ssh is automatically blocked. I just had to configure SMTP settings in the denyhosts config file.

This is the output of my /etc/hosts.deny file:

```

sshd: 59.106.12.179
sshd: 125.69.89.123
sshd: 202.102.245.121
sshd: 58.211.58.3
sshd: 222.234.3.202

```

I checked the /var/log/auth.log files for 'ssh2' attempts and found hundreds of brute force attempts from different IPs. With denyhosts, I am much safer now.

But blocking them at the hardware firewall level would be better. 

Tim, I agree that we need to be proactive irrelevant of the OS, but I can dare leave my linux server in the public domain. But not a windows box with a hundered firewalls running in it. Thats why linux admin can afford better sleep than windoze admins.

---

### Post by Nicklas Overgaard on 2008-05-28
> **dendrobates said:**
> I'm sorry, but this is absurd.  While OpenBSD is known for having few remote root exploits as shipped.  As soon as you run any package like apache or mysql and open it to the internet, there is essentially no difference.  FreeBSD is not known for security.  In fact, Linux and all UNIX-like OS's are vulnerable to the same sorts of attacks.  If you think running BSD is protecting you from anything more than Linux kernel exploits, you are wrong.

The real question that we should be asking the poster, is why he is running mysql listening on the Internet without TCP wrappers and ipchains configured to only allow specific hosts through.  In this configuration, there is no OS that can prevent brute force attacks. 

Rick Clark
Manager Ubuntu Server and Security Teams

The reason why we have opened MySQL to the internet was to be able to manage our databases from remote sites. I have very limitied knowledge about ipchains, and that would be why there is no rules in place to protect the server.

But i think that we would be better off with closing access to MySQL, and then use SSH instead.

Thanks for all the feedback everyone!

---

### Post by gtdaqua on 2008-05-28
> 
The reason why we have opened MySQL to the internet was to be able to manage our databases from remote sites. I have very limitied knowledge about ipchains, and that would be why there is no rules in place to protect the server.

But i think that we would be better off with closing access to MySQL, and then use SSH instead.

Thanks for all the feedback everyone!


Why would you want to try accessing 3306 over Public Internet??? Use a remote access VPN or administer the server via ssh. If you are opening SSH on the public domain, then its best to install 'denyhosts' as it will block bruteforce attempts on ssh by default. 

I think you can configure 'denyhosts' to block brute force attempts on port 3306 too. But its not a best practice to open your back-end environment to be accessed by all.

---

### Post by dendrobates on 2008-05-28
Look at the openvpn package.  It is pretty easy to use.  You should change mysql to listen on a socket or localhost.  

BTW, Ubuntu Server Edition, ships with no open ports by default, includes apparmor and has a easy firewall tool, UFW.  We have a similar security risk profile to OpenBSD, in my opinion. 

Rick
(dendrobates on FreeNode)

---

### Post by windependence on 2008-05-28
> **dendrobates said:**
> Look at the openvpn package.  It is pretty easy to use.  You should change mysql to listen on a socket or localhost.  

BTW, Ubuntu Server Edition, ships with no open ports by default, includes apparmor and has a easy firewall tool, UFW.  We have a similar security risk profile to OpenBSD, in my opinion. 

Rick
(dendrobates on FreeNode)

Hey, I LIKE Ubuntu server. I run it on my prod machines and I am standardizing it on all my client's machine also. I was speaking about Linux in general, sorry for the confusion.


-Tim

---

