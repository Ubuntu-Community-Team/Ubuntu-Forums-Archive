---
title: "Firestarter and connection  monitor"
date: 2009-09-16
forum: Security
---

### Post by marticc on 2009-09-16
Hi, before I start I would loke to apologise for my poor English, I hope you understand what my question is.

I have read many times that using firestarter is not a very sensible thing because:

1) You need to start it using your "sudo account"

2) Once it has been configured, the IP tables protects the system.
 
3)It is no longer developed/supported (I don't understand why this is a problem, if the firestarter is just a Gui, and the actual firewall -iptables- is currently being supported).


Anyway, as far as the second point is concerned, I like using Firestarter just because of his connection monitor (I can always see which IPs are connected to my system), the Gufw (which is more popular among Ubuntu users) doesn't have this feature. So I'd like to know whether or not there is a connection monitor that doesn`t require a "sudo account" 


Finally, When I start Firestarter, I enter my "Sudo password", and when the firewall has started, I click ALT+F2, and enter sudo -k. After that I connect to the internet. I would like to know why this is "unsafe".

Thanks for your answers.

---

### Post by lvlint67 on 2009-09-16
> **marticc said:**
> Hi, before I start I would loke to apologise for my poor English, I hope you understand what my question is.

I have read many times that using firestarter is not a very sensible thing because:

1) You need to start it using your "sudo account"

2) Once it has been configured, the IP tables protects the system.
 
3)It is no longer developed/supported (I don't understand why this is a problem, if the firestarter is just a Gui, and the actual firewall -iptables- is currently being supported).


Anyway, as far as the second point is concerned, I like using Firestarter just because of his connection monitor (I can always see which IPs are connected to my system), the Gufw (which is more popular among Ubuntu users) doesn't have this feature. So I'd like to know whether or not there is a connection monitor that doesn`t require a "sudo account" 


Finally, When I start Firestarter, I enter my "Sudo password", and when the firewall has started, I click ALT+F2, and enter sudo -k. After that I connect to the internet. I would like to know why this is "unsafe".

Thanks for your answers.

First: You don't have to have firestarter running to be protected. Once firestarter has configured the firewall (when you input settings and stuff) you can close it and forget about it.

second: if you want  network monitor (show traffic/packets/anything else) they are available in the repos. It would hep if you could explain what you want the network monitor to be capable of.

If you just want to see the firewall activity there should be a log somewhere that you can either view or find a script to parse that should not require root privs.

---

### Post by marticc on 2009-09-16
Hi, thx for your answer:

I would like a network monitor program that doesn't require a sudo connection and that lets me know which IPs I am connected to, and how many data I have downloaded /upgraded in a single session. 

It would also be nice if that network monitor program (or any other program) could also cut a single connection (ie if I am connected to several IPs, and a  I don't want to be connecterd to one of these IPs becuase of any reason, I would like to be able to cut that single connection without turning off all my internet connection). This would be nice, but I will make do with a network connection with the features described in the first paragraph.

Finally I 'd like to ask a last question: You say that once I have configured th firestarter I can switch it off because my  settings are kept and working with actual fireweall (IPtables). My question is: How long do the new settings configured with firestarter last?. Ie, if right now I configure the firestarter to stop all the outbound connections but those going to port https (that is just an example), and I switch off the PC, will this new settting  be working when I turn on my PC the following day, or do I have to start the firestarter to make this new setting work.

Thanks again.

---

### Post by 3rdalbum on 2009-09-16
1. Any program that changes your IPtables configuration will require root. You don't need to start Firestarter whenever you turn on your computer; IPtables runs before X comes up.

2. Why do you want to see what IP addresses are connected to your computer? It sounds like a pretty pointless thing... "Oh wow, 68.57.109.234 is connected to me. I wonder who they are or where they are from?"

The Ntop package can show what IP addresses you are connected to - it's a little daemon that keeps track of statistics. You interact with it through your web browser.

Firestarter tends to scare newbies with its logging feature. It logs when it has denied a connection, but new users are often scared by the (perfectly normal) number of denied connections, or even believe that these connections have been allowed and that hackers are attacking their system.

Firestarter has a lack of visual feedback when you click the Start Firewall button. Is it on? Is it off? Is the button actually connected to anything? It doesn't feel like it.

Firestarter also scares new users by the following message on system startup:

```
[*]Starting Firestarter firewall...       [FAIL]
```

It doesn't mean anything, but it scares people.

---

### Post by lovinglinux on 2009-09-16
I'm not an expert, but I have been reading about Firestarter since I switched to Linux a year ago. It seems that there are some reported bugs in Firestarter that could allow an attacker to get access to other resources in your machine. I don't know if this is true or not, but since Firestarter requires root privileges to run, the attacker could gain access to your entire system. That makes some sense to me.

Anyway, when I just switched to Linux I used to defend Firestarter on some threads, because it made me feel very comfortable, due to the monitoring capabilities. I was a Comodo firewall user on Windows, which allowed me to monitor everything and also alert me about connection attempts.

Today I don't recommend it. In fact, I'm also questioning other users interested in Linux firewalls if they really need one, since I have learned some interesting things from other users experiences. For instance, if you don't have any server running, like ssh, samba, BitTorrent, then there are no applications listening to any ports, so any unrequested connection attempts on any port will be simply refused, even if you don't have any firewall rules. It's not even possible to hack a machine on this scenario. So, why do you do need a firewall? If you install a server like BitTorrent, then you will want to let other users to connect to it, so firewall rules are not necessary again. They are actually useful if you want for example to allow ssh access only to machines on your local network and block any access to the ssh port coming from the Internet. It this situation, a firewall would bring a real security benefit.

Besides, if you have a router, then incoming unrequested traffic is already blocked before even reaching your machine. No connections will reach your machine unless you intentionally forward a port to it.

I recommend reading the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial.

.

---

### Post by sopadeajo on 2009-09-16
I think Firestarter is a good app to learn about networks. Someone here said it scares newbies. Not if they are told that the Internet is full of machines scanning other machines for whatever reason. In my case,i am witnessing a bunch of attempts to connect on port 135 TCP
from machines belonging to my geographical area (this information,is looking at the IP adresses given by Firestarter). What i have learnt is these could be windows machines. But i still do not know if it is a legal scanning (machines in a network wanting to connect) or machines of hackers.
The thing is that it is better to know (scared or not) what is Internet (the attempts of attack) than feeling secure because you do not know nothing.
Does anybody here know what are these more than 100 attemps on port 135 from more than 40 different IP's ? Are they window machines or are they Linux machines? Does anybody here know it?

---

### Post by lovinglinux on 2009-09-16
> **sopadeajo said:**
> I think Firestarter is a good app to learn about networks. Someone here said it scares newbies. Not if they are told that the Internet is full of machines scanning other machines for whatever reason.

I agree with 3rdalbum on this. Most users that post questions on the forum regarding hacking attempts are using Firestarter and are afraid of blocked connections, that are perfectly normal. Besides, most of the time they are blocking a port that is already closed without the firewall. If the user does not have any server listening to ports, then Firestarter it's basically just feeding the paranoia, instead of adding security.

> **sopadeajo said:**
> The thing is that it is better to know (scared or not) what is Internet (the attempts of attack) than feeling secure because you do not know nothing.

You are missing the point here. Is not about feeling secure because you do not know who is trying to hack you, but feeling secure because you know they can't do it. For instance, I have a router with all ports closed, so no incoming connections will be reaching my machine. Do you believe I should monitor all connection attempts on the router level? Of course not. All router ports are closed, so why bother? Do you monitor your router?

Most of the time is actually Firestarter who will give a false sense of security. For example, an user installs it on a machine that does not have any server listening to ports and thus is not really necessary, since all ports are already closed. Then it installs Limewire, who will not only be listening to ports, but also allowing access to some of his folders. Since the user wants to download stuff, he opens the port required by Limewire on Firestarter. So at this point, the user is basically using a firewall to block ports that are already closed and opening the only one that could let an hacker comes in. So is Fireatrter protecting the machine? No. Not at all. But the user probably feels safe, because he has a firewall and don't realizes the only route available for a hacker to get in is the insecure p2p software his is using to connect to hundreds of other computers.

> **sopadeajo said:**
> Does anybody here know what are these more than 100 attemps on port 135 from more than 40 different IP's ?

Have you consider the possibility that you are using a dynamic IP and the previous user of that IP was doing something that accept connections on port 135? When you connect to your ISP you get a "new" IP that is actually not new, but was probably being used by someone else just a few minutes before you. So if that user was doing something that requires listening to port 135, you will probably get lots of connection attempts on that port that are actually "ghost packets". This means the computers trying to reach you are not necessarily hackers or bots scanning your ports, but regular machines that aren't aware yet that the IP you are using now was assigned to another machine by your ISP.

> **sopadeajo said:**
> Does anybody here know what are these more than 100 attemps on port 135 from more than 40 different IP's ? Are they window machines or are they Linux machines? Does anybody here know it?

I'm not sure, but it could be msn (messenger) related stuff, which would explain the number of different IP's trying to reach the same port.

---

### Post by marticc on 2009-09-16
Hi, thanks for your answers. I just want to say I completely disagree with many of the opinions I have read in this forum about security system. According to many people, you don't need a firewall because by default, Ubuntu opens zero ports, and in theory is impossible  get, for example a trojan able to run in Linux because it is a Unix OS system  and so it enjoys a user policy system that protects the system against this kind of attack

That my be true for the time being, but it might change in the near future (this article is pretty interesting: [http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)), and I find that as far as security is concerned many Linux experienced users are quite carefree. Despite the fact it might not be necesary at the moment, I am going to keep using a firewall, and to keep on scanning every file I get with an AV JUST IN CASE

---

### Post by cariboo on 2009-09-16
> That my be true for the time being, but it might change in the near future (this article is pretty interesting: [http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)), and I find that as far as security is concerned many Linux experienced users are quite carefree. Despite the fact it might not be necesary at the moment, I am going to keep using a firewall, and to keep on scanning every file I get with an AV JUST IN CASE

A firewall or av scanner is not going to stop social engineering. the article you just quoted really has nothing to do with viruses. It depends on the user installing the malware, in other words, you the user have to create the launcher yourself.

Quote from the article:

> **However, there is nothing fundamental about the architecture of Linux that prevents user stupidity or ignorance, which is of course the main ingredient in any attack vector like this.** 

I've bolded the most important part of the post.

The biggest security risk when running a Linux distribution is the user, especially a new user, as they really don't know what they are doing and mis-configure settings.

---

### Post by sopadeajo on 2009-09-16
"Have you consider the possibility that you are using a dynamic IP and the previous user of that IP was doing something that accept connections on port 135? When you connect to your ISP you get a "new" IP that is actually not new, but was probably being used by someone else just a few minutes before you. So if that user was doing something that requires listening to port 135, you will probably get lots of connection attempts on that port that are actually "ghost packets". This means the computers trying to reach you are not necessarily hackers or bots scanning your ports, but regular machines that aren't aware yet that the IP you are using now was assigned to another machine by your ISP."

No, you have all wrong, because i have a static IP (the same for more than 2 years)

And this found Googling: It seams that it is another of the bad Micro$oft legacy

"
DCOM-scm is the DCOM interface to the Service Control Manager, which
allows for the starting, stopping, etc. of the background services on a
Windows system.  Unfortunately, Microsoft didn't get the security quite
right in this subsystem.

This is an attempt by a compromised Windows box to compromise your Linux
system by scanning the local blueyonder IP address range, hoping it will
find another open Windows system."


Of course i am not scared because i know these are very probably windows machines blindly looking for a windows system and they do not know if they find or not a Linux system.

They are probably zombie-window$ machines: that is machines whose owner do not even know that they are being used for hacking purposes.

---

### Post by sopadeajo on 2009-10-08
LovingLinux in his non defense of Firestarter said that unless you install a server on your machine there is no open ports in Ubuntu. He forgot Stardict (a good program to view dictionaries databases downloaded or not) who opens port 2628 in local machine.Or i am wrong and it is on remote machine?
If it is so, since most of the dictionaries i use are downloaded ones (i think stardict is connected to dict only for one dic: The Chinese to English one, but i am not sure), what would be the simplest way to stop Stardict listening to remote computer?

---

### Post by cariboo on 2009-10-09
The best way to check if you have any open ports, is to use nmap, it is in the repositories.

```
nmap localhost
```

returns, on this computer:

```
nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2009-10-08 21:53 PDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 998 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
631/tcp open  ipp
```

As you can see I have two ports open, 631 only listens of 127.0.0.1, so there is nothing to worry about there. 22 is open, but it is only for use on my local network, as it is not forwarded through my router.

To check your router firewall there are many places on the internet that will scan it. One I just tried is located [here]("http:///www.auditmypc.com/firewall-test.asp").

---

### Post by sopadeajo on 2009-10-09
> **cariboo907 said:**
> The best way to check if you have any open ports, is to use nmap, it is in the repositories.

```
nmap localhost
```returns, on this computer:

```
nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2009-10-08 21:53 PDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 998 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
631/tcp open  ipp
```As you can see I have two ports open, 631 only listens of 127.0.0.1, so there is nothing to worry about there. 22 is open, but it is only for use on my local network, as it is not forwarded through my router.

To check your router firewall there are many places on the internet that will scan it. One I just tried is located [here]("http:///www.auditmypc.com/firewall-test.asp").

But if i do a port scan with Network Tools  to my own IP i get:
2628 open dict

---

