---
title: "windows hosts file 2 iptables"
date: 2009-11-12
forum: Security
---

### Post by Yoast on 2009-11-12
Hi there.  I know this qquestion has been asked a good number of times, but I have not seen a satisfactory answer, so far.  I am new to Ubuntu (kubuntu) and I'm impressed. I have a simple home LAN (shared printer and hard-disk in windows workgroup. Nothing exceptional). I recently installled Ubuntu 9.10 (to try on an old desktop) and was pleasantly surprised.  On Windows I used windows hosts managed by spybot S&D and it worked like a charm.   The basic conceptof hosts files is that a whole lot of people keep a list of "bad" hosts (known malware, bots, hackers etc) and that the list is distributed to various computers to allow a series of measures to counter these threats. These lists also useful in that should someoone break into your computer, or socaial engineer a way into access that it will be quite hard to communicate home, copy code tpo other computers etc. because the risk of it getting blocked are great.  Opendns offers this blocking, BT/Yahoo offers this blocking, Netgear has routers that can use these lists, windows hosts lists are created/maintained by several people who use the same lists.   In general I think it is a great idea to have this standard protection and I would like to see it available in iptables in linux. The reason being that It will be safer to work with this extra protection and it is relatively simple to implement.   I'm not interested in discussions on whether I really need it because Linux is safer than windows etc. If I take my laptop to the University-library, the local library or McDonalds or just stay at home and behave relatively safely (only to find a teenage nephew with a CD with ganmes has tried to boot and install his games, for example) is immaterial to the implementation of the relatibveely simple technical means that will increase my security a bit.  So much for my rave/rant. I have come accross people wha had created scripts to implement Hosts files in home-routers. Is it possible to implement something like this in Linux/Iptables? I can only imagine that someone is already converting hosts files for firewalls somewhere that would have the right structure.  Thanks

---

### Post by cdenley on 2009-11-12
All linux or unix based operating systems have a hosts file, as far as I know.
```

gedit /etc/hosts

```
It works the same as in windows. I know some ubuntu users use lists such as what you describe to prevent your computer from resolving blacklisted domains to their correct IP addresses. I can't remember the name(s). I would be cautious about implementing any scripts which update your hosts file based on lists obtained through the internet. You wouldn't want to end up using a compromised list which tricks you into resolving well-known, legitimate domains to malicious IP's spoofing the domain's server.

The hosts file is about name resolution, and is unrelated to iptables.

---

### Post by Yoast on 2009-11-12
Thank you for this information.

 would tend to seek safety in numbers. Basically: if MVPS's hosts file (I used to auto-download this with Hostman) or the one that comes with Spybot Search and Destroy) gets millions of downloads you would hoope that someone would notice if there was a serious problem with it.

I'm still looking for a list that I can automatically copy and use. 

I hope someone can help me further.

THanks.

---

### Post by cdenley on 2009-11-12
> **Yoast said:**
> would tend to seek safety in numbers. Basically: if MVPS's hosts file (I used to auto-download this with Hostman) or the one that comes with Spybot Search and Destroy) gets millions of downloads you would hoope that someone would notice if there was a serious problem with it.

How are you verifying that the hosts file update is coming from the correct server, and isn't being spoofed?

---

### Post by Yoast on 2009-11-12
Any attack would have to get past opendns. So if known hackers sites are the "new" resolved targets they could get blocked. On the router's firewall the DNS requests are blocked or redirected over the opendns IP's. 

On a PC (Windows) I would rely on Hostsman (Abelhadigital) which collects zipped versions. It is widely used. Serious re-direction through hosts through these downloads would affect serious numbers of people.
On a PC (Windows) I would also rely on Spybot search and destroy. If you follow its downloading of most recent versions it will use a new definitions file for spyware, but also a new Hosts file. Spybot will also do lookups in the Winhosts file to see if things are wrong. 

For home-use I think these are quite good.  But I am open for better suggestions.

---

### Post by cdenley on 2009-11-12
> **Yoast said:**
> Any attack would have to get past opendns. So if known hackers sites are the "new" resolved targets they could get blocked. On the router's firewall the DNS requests are blocked or redirected over the opendns IP's. 

Are you arguing that you are protected from the server which provides hosts file updates from being spoofed by OpenDNS? There are other ways to spoof a server besides DNS poisoning. Also, if the DNS server for the domain is compromised for a short period of time, it could only push the malicious hosts file to a handful of users. You need the hosts file update to be verified with some kind of cryptography signature, or to retrieve it using a CA-signed SSL certificate. I'm not sure what spybot does.

Verifying that the updates are authentic may be a little paranoid, but so is blocking a list of domains for fear you might unwittingly browse to one which can actually somehow compromise your computer is even more paranoid, in my opinion. If you don't verify the updates, even if you trust the server providing the updates itself wouldn't be compromised because "someone would notice", then you're probably safer leaving the hosts file alone.

---

### Post by Yoast on 2009-11-12
I am arguing that should anybody maliciously replace a hosts-file on a client-PC the chances are the redirected IP's on the client would be pointing to malicious sites that are known. In this case they would not get past opendns (or if you have a router that can use a list of known bad sites it might nnot make it past your router.). 

I am not so certain that there would be more certainty in a unique solution where I would personally be monitoring more. This can get complex and people make mistakes. If Spybot is used on many computers that does provide extra security. 

I am not so much concerned about browsing to a wrong page. There are lots of ways, other than just a browser, that malware could try to "phone home", download additional bad stuff, copy itself etc.. Connections to "bad" IPs  could be blocked by a correct Hosts file and/or a well protected DNS. 

Spybot: when you "update" with spybot, it will look for new definition files (just like antivirus programs do) and it will download new hosts definitions (There is an option to disable/enable the hostfile management by spybot). Simply put. There is a regular flow of new definitions that will overwrite the old.  [http://forums.spybot.info/showthread.php?t=20053](http://forums.spybot.info/showthread.php?t=20053). 

If you do not want to use a construction like it. Fine. I respect that. However. I think I do want to use a way to automatically update a list of known bad IPs that can be used on an ubuntu client. 

Can anybody help me further with this?

Thanks.

---

### Post by cdenley on 2009-11-12
> **Yoast said:**
> I am arguing that should anybody maliciously replace a hosts-file on a client-PC the chances are the redirected IP's on the client would be pointing to malicious sites that are known. In this case they would not get past opendns (or if you have a router that can use a list of known bad sites it might nnot make it past your router.). 

If there is an entry in your hosts file for a domain, OpenDNS would not be queried.

> **Yoast said:**
> 
I am not so much concerned about browsing to a wrong page. There are lots of ways, other than just a browser, that malware could try to "phone home", download additional bad stuff, copy itself etc.. Connections to "bad" IPs  could be blocked by a correct Hosts file and/or a well protected DNS. 

Your hosts file WILL NOT block any IP's, only domains. Hypothetical malware can still phone home.

> **Yoast said:**
> 
Spybot: when you "update" with spybot, it will look for new definition files (just like antivirus programs do) and it will download new hosts definitions (There is an option to disable/enable the hostfile management by spybot). Simply put. There is a regular flow of new definitions that will overwrite the old.  [http://forums.spybot.info/showthread.php?t=20053](http://forums.spybot.info/showthread.php?t=20053). 

What I meant was I don't know if/how they protect from spoofing.
> **Yoast said:**
> 
If you do not want to use a construction like it. Fine. I respect that. However. I think I do want to use a way to automatically update a list of known bad IPs that can be used on an ubuntu client. 


I would suggest abandoning your hosts file idea. If you do use a blacklist solution, make it IP-based, not hostname-based, and use iptables. I don't think it would be worth the trouble, though.

---

### Post by bodhi.zazen on 2009-11-12
> **Yoast said:**
> I am arguing that should anybody maliciously replace a hosts-file on a client-PC the chances are the redirected IP's on the client would be pointing to malicious sites that are known. In this case they would not get past opendns (or if you have a router that can use a list of known bad sites it might nnot make it past your router.). 

Well, this is wrong thinking =)

your hosts file, both on linux and windows, are like an address book and match a domain name with an IP address. 

This is easily circumvented by specifying an ipaddress directly and your hosts file is not a firewall.

```
# Ping ubuntuforums.org
root@ufbt:~#ping -c 1 ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=41 time=175 ms


# Add ubuntuforums to hosts file
root@ufbt:~#echo "127.0.0.1 ubuntuforums.org" >> /etc/hosts

# Ping redirected, as expected
root@ufbt:~#ping -c 1 ubuntuforums.org
PING ubuntuforums.org (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.053 ms

**[COLOR=red]# ping by IP[/COLOR]**
root@ufbt:~#ping -c 1 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_seq=1 ttl=41 time=172 ms

**[COLOR=red]# OH NO, HOSTS FILE == TOTAL FAILURE[/COLOR]**

[COLOR=blue]**#block ubuntufourms via iptables (firewall)**[/COLOR]
root@ufbt:~#iptables -A OUTPUT -d 91.189.94.12 -j DROP
[COLOR=blue]**#Remove ubuntuforums.org form /etc/hosts (edit not shown)**[/COLOR]

root@ufbt:~#ping -c 1 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

root@ufbt:~#ping -c 1 ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

[COLOR=blue]**#do you see , you need to use a firewwall ?**[/COLOR]
```> I am not so certain that there would be more certainty in a unique solution where I would personally be monitoring more. This can get complex and people make mistakes. If Spybot is used on many computers that does provide extra security. 

I am not so much concerned about browsing to a wrong page. There are lots of ways, other than just a browser, that malware could try to "phone home", download additional bad stuff, copy itself etc.. Connections to "bad" IPs  could be blocked by a correct Hosts file and/or a well protected DNS. 

Spybot: when you "update" with spybot, it will look for new definition files (just like antivirus programs do) and it will download new hosts definitions (There is an option to disable/enable the hostfile management by spybot). Simply put. There is a regular flow of new definitions that will overwrite the old.  [http://forums.spybot.info/showthread.php?t=20053](http://forums.spybot.info/showthread.php?t=20053). 

If you do not want to use a construction like it. Fine. I respect that. However. I think I do want to use a way to automatically update a list of known bad IPs that can be used on an ubuntu client. 

Can anybody help me further with this?

Thanks.Linux is not windows and "Sypbot" either is not working the way you think or is ineffective (I am not sure which).

Honestly, I suggest you start with : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

If you wish to simply use a blacklist with yoru firewall I suggest :

1. There is no known spy ware in Linux that will "phone home", this isn not windows.

2. The only way software that can phone home can be installed is either if you install it yourself (do not install applications outside the Ubuntu repositories) or if you  are already cracked.

3. [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

4. If you want an easy to use gui, take a look at [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

But you really are going about this the wrong way, you are applying a windows mentality to Linux and therefore spinning your wheels.

---

### Post by __p1n__ on 2009-11-12
The "domain blacklisting" that spybot does includes:

1. Adding a 127.0.0.1 address to each of 100,000+ domains in your /etc/hosts file (nice way to slow down routing.)
2. Adding all those domains to your restricted sites (registry)

Like bodhi.zazen said, this won't stop an ip-address based call and you don't really need to block those sites anyways if you're surfing from a linux platform.

---

### Post by Yoast on 2009-11-12
Let me start by thanking all of you for your help and advice and your time. It is nice and reassuring to see the help you volunteer to a newbie like me.  I have so far come accross ipblock, Moblock/Peerguardian and Bluetack as potential sources for more info on using a blocklist.   I'll probably digest the information a bit and then look for a solution that  strikes the balance between having to know all ins-and nnouts of configuring avarything and having some added security that will allow me to use the laptop in various places (i.e. not require too much configuration for one specific environment) and still offer the blocking of as much traffic to known bad sites as possible.  It is not the begin and end all of security, but it can help.

---

