---
title: "Best security config/flavor?"
date: 2014-03-25
forum: Security
---

### Post by Barkester on 2014-03-25
I'm studying network security (fast growing market now) and have a quandary :

   Which flavor in the Debian family can bring me good enough security to keep Coca-Cola's secret recipe (hypothetical) ?

   Which browzers are best?

   What configurations?

   I've already decided that all programs capable of net access should be issued containers. Anything else?

   Help my studies alot to have a good example to play with. No teachers here. Just me and some good books. An example would help alot.

   Thanks for any help.

---

### Post by grahammechanical on 2014-03-25
This is really a subject for discussion. It is not a support request.

The most secure operating system is the OS installed on a computer that is switched off. The next most secure is the OS this is installed on a machine that is never connected to the internet or any other kind of network in any way when it is switched on.

You need to define "network security." You need to identify areas at risk and then check if there are processes in place to reduce the risk if not eliminate it. Do not forget to include users as a security risk. 

What does this mean?

> [COLOR=#000000]I've already decided that all programs capable of net access should be issued containers.[/COLOR]

What do you do when the user wants to run a live video stream over from the internet. The web browser needs disk space to cache the file. How can the user have this freedom if it is in a container that prevents it from accessing the storage space? And once you give it access to storage space what is to stop the application from accessing what is already existing on the disk and from accessing system files?

Regards.

---

### Post by frankmorris2 on 2014-03-25
Hello,

I am not a security specialist, but a good start could be to look at the "Security Discussions" on the ubuntuforums.org.

Also, from my experience, security comes from good configuration: if you don't need a service, disable it. Especially true for web servers and other listening services.

I'm sure there are security veterans ready to help you on the forums :-)

---

### Post by JKyleOKC on 2014-03-25
> **Barkester said:**
> I'm studying network security (fast growing market now) and have a quandary :

   Which flavor in the Debian family can bring me good enough security to keep Coca-Cola's secret recipe (hypothetical) ?

   Which browzers are best?

   What configurations?

   I've already decided that all programs capable of net access should be issued containers. Anything else?

   Help my studies alot to have a good example to play with. No teachers here. Just me and some good books. An example would help alot.

   Thanks for any help.The first and most basic thing to understand is that security is a process, not a program. The process goes on without end; any interruption of it reduces security, quite possibly to a fatal degree.

This process includes, but isn't limited to, provision for disaster recovery, limiting user access tp critical areas, and in general avoiding known risky behavior.

The second and next most basic thing to keep in mind is that lack of security is **always** a people problem, not a purely technical situation. The most widespread security breach I even personally witnessed resulted from our little company's CEO and his penchant for getting pirated software and installing on the firm's network...

Beyond these two thoughts, I'll leave it to the true professionals to go into more detail...

---

### Post by vasa1 on 2014-03-25
> **grahammechanical said:**
> This is really a subject for discussion. It is not a support request.

+1.

---

### Post by sandyd on 2014-03-25
Moved to security Discussions

---

### Post by james114 on 2014-03-25
JKyleOKC +1
And don't forget to turn on and setup firewall with UFW on your Ubuntu.

---

### Post by JKyleOKC on 2014-03-25
> **james114 said:**
> JKyleOKC +1
And don't forget to turn on and setup firewall with UFW on your Ubuntu.Actually the firewall is useless until such time as you activate one or more servers, because (unlike many other operating systems that install invisible servers by default) without servers there won't be any ports listening to the outside world. Once you do activate one, however, then UFW, GUFW, or something similar would be needed. Note that **all** of these are simply front ends to help you **configure** "*iptables*" which is the real firewall built into the kernel code, and once you've done the configuration these front ends **don't** need to run any more.

---

### Post by ant2ne on 2014-03-26
> Actually the firewall is useless until such time as you activate one or more servers I disagree. Someone, even without root, could open a port running "service" in user space and allow more stuff in. If you close all incoming ports except those you want open then you are far more assured that there aren't any listeners.

---

### Post by JKyleOKC on 2014-03-26
> **ant2ne said:**
> I disagree. Someone, even without root, could open a port running "service" in user space and allow more stuff in. If you close all incoming ports except those you want open then you are far more assured that there aren't any listeners.Good point, in theory at least. If the system is open to anyone other than yourself, this might be possible. However getting anything installed **without** using root would limit the damage to only that user's area (including areas where he had write permission).

As it happens, I do use a minimum set of rules for *iptables* and run the *fail2ban* lockout utility since I do have a couple of servers open to the outside world. My major points were that the firewall isn't nearly so necessary here as it is with other systems that aren't so secure by design, and to note that all of the popular firewall utilities are tools to **configure**, not to implement, the actual protection. Far too many newcomers worry overmuch about getting GUFW to run automatically at all times! Once is enough; the configuration persists until it's explicitly changed again.

---

### Post by cogset on 2014-03-27
> **ant2ne said:**
> I disagree. Someone, even without root, could open a port running "service" in user space and allow more stuff in. If you close all incoming ports except those you want open then you are far more assured that there aren't any listeners.

I've never understood the "no need for a firewall" statement:come to that,I may still be misunderstanding it,but assuming that a typical desktop computer will have at least one web browser installed,and seeing how many unwanted and unnecessary connections from a number of servers around the world target every computer connected to the net,how would anyone not want to set at (very) least the base policy of allow outgoing/deny incoming?

---

### Post by ant2ne on 2014-03-27
The linux kernel disables/drops all incoming connections unless there is a server listening on that port. So that is the 'reason' for not having a firewall. And for most instances, that is a very good 'reason'. The only threat you might have is if someone installs or adds a "service" or runs an application that would be listening for a connection. 

Suppose I, NOT as root accidentally install a service, or malware that runs as a user and it that then wants to phone home. If my firewall is configured properly it WILL prevent that phone call. 

Suppose I, as root accidentally install a service, or malware that then wants to phone home. If my firewall is configured properly it should help prevent that phone call. The problem is most malware installed as root will root you anyway so it can easily modify the firewall too.

---

### Post by JKyleOKC on 2014-03-27
> **ant2ne said:**
> The linux kernel disables/drops all incoming connections unless there is a server listening on that port. So that is the 'reason' for not having a firewall. And for most instances, that is a very good 'reason'. The only threat you might have is if someone installs or adds a "service" or runs an application that would be listening for a connection. 

Suppose I, NOT as root accidentally install a service, or malware that runs as a user and it that then wants to phone home. If my firewall is configured properly it WILL prevent that phone call. 

Suppose I, as root accidentally install a service, or malware that then wants to phone home. If my firewall is configured properly it should help prevent that phone call. The problem is most malware installed as root will root you anyway so it can easily modify the firewall too.Very good points, and on the basis of your "phone home" scenario I herewith **retract** my earlier advice. While having a firewall monitoring **inbound** packets is necessary only if you have something listening on a port, which implies installation of a server of some sort whether deliberately or accidentally, having one monitoring **outbound** packets **is** an essential part of security if one makes **any** use at all of the internet. I should have remembered that the one and only time I ever got a true virus infection (in the days before I came to Linux) was detected **only** by my outgoing firewall!

---

### Post by cogset on 2014-04-01
> **ant2ne said:**
> The linux kernel disables/drops all incoming connections unless there is a server listening on that port. So that is the 'reason' for not having a firewall. And for most instances, that is a very good 'reason'. The only threat you might have is if someone installs or adds a "service" or runs an application that would be listening for a connection.


So,please excuse me if this sounds really naive,we can assume that as long as there are no servers/services listening,and there's only a web browser/mail client installed,having a firewall with _only_ the basic **allow outgoing/deny incoming** policy is actually the same as having no firewall at all?
Because,as you've explained above,the linux kernel will by default disable/drop anyways all incoming connections unless there is a server listening on that port.

If so,a firewall will make sense only when writing more specific rules,or as a tool to monitor outbound packets,although the latter could probably be better achieved with other network tools?

---

### Post by sandyd on 2014-04-01
> **cogset said:**
> So,please excuse me if this sounds really naive,we can assume that as long as there are no servers/services listening,and there's only a web browser/mail client installed,having a firewall with _only_ the basic **allow outgoing/deny incoming** policy is actually the same as having no firewall at all?
Because,as you've explained above,the linux kernel will by default disable/drop anyways all incoming connections unless there is a server listening on that port.

If so,a firewall will make sense only when writing more specific rules,or as a tool to monitor outbound packets,although the latter could probably be better achieved with other network tools?

Few things to note

a) Linux  Kernel will drop connections to ports that are not **open**
b) When you have a service that listens on a port (such as apache2), the port will then **be open and accept connections**. You can view ports in which a service is listening by running
```
lsof -i
```
or
```
netstat -tnulp
```
c) Some people (like me) add additional rules to increased security. For example, if someone hacked into my server, and started attempting to spam others, I have outgoing port 25 blocked (which prevents them from sending mail)

---

### Post by JKyleOKC on 2014-04-01
> **cogset said:**
> If so,a firewall will make sense only when writing more specific rules,or as a tool to monitor outbound packets,although the latter could probably be better achieved with other network tools?I'm not at all sure that any "better" network tool than iptables exists. You are correct, though, that a properly configured rule set for the OUTPUT chain (that allows origination of http and https requests, and possibly a few more) to monitor and police outbound requests can definitely help should a hidden driveby attack (which are becoming more common) install something which then tries to call home.

---

### Post by 23dornot23d on 2014-04-03
A question ......... that I think I need to know ...........

Does using "etherape" open up a security risk ....... 

( I ask this because when I have run it in the past it scares the **** out of me as to how many connections there are )

Netstat -a seems to show who is listening and what might be a risk ....... but again without fully understanding how packets are being sent
back and forth - how can we really tell which are more dangerous to have connected ...... like there are ones for geoip now ..... that were not
originally there ....... on Ubuntu ......

Not my field at all security - but when I have looked at it in more detail - all it does is cause more confusions than clear answers.

As said .... the best and most secure is the computer that stays offline ..... having more than one computer for doing things seems to be the
normal thing nowadays to keep any sense of privacy and security.

Containers ...... Miro - seems good as you download once into a area and then watch the video - but it still needs the initial connection and download
over the net ..... so I guess the vulnerable time is in that time frame - then you need to disconnect afterwards not leaving it open - even shut it down and
go into the folder - run some other program to watch the video ..... rather than streaming .......

Also keep an eye on htop for any unusual activity going on ..... or keep the main process's popping up on a conky screen where you can monitor things.

---

### Post by JKyleOKC on 2014-04-03
Like wireshark, etherape is a sniffer and can show you everything that's hitting your system -- and also, whether your system responds to it.

Running either is **not** a security risk; they simply make you aware of just how great the risk at any moment actually **is**. Only if your system responds to this huge number of connection requests and lets any undesired ones in, is there a risk. And then, it's your system configuration at fault, not the program that lets you know about it.

---

### Post by 23dornot23d on 2014-04-04
Cheers for the reply ....

I might use etherape a little more now just to scan around ..... but seen some very odd names popping up on it ......

____________________________________________________________________

Its like being inside a fort and all the attackers are around the walls ..... sometimes better to just stay inside the fort

and not look out over the walls - I guess

---

### Post by JKyleOKC on 2014-04-04
> **23dornot23d said:**
> Its like being inside a fort and all the attackers are around the walls ..... sometimes better to just stay inside the fort

and not look out over the walls - I guessSeems to work pretty well for the ostrich -- until a hunter comes along while the bird's head is still in the sand.

Awareness is good. So is caution. Fear and avoidance, not so much so...

---

### Post by cogset on 2014-04-06
I've never heard before about Etherape,having quickly looked at its screenshots I have to say it looks indeed very interesting:the graphical representation of all network connections kinda reminds of Mozilla's extension Collusion (now revamped as  Lightbeam).
The only drawback to me seems that,unlike Wireshark,which can be set to capture packets when run by normal user,it apparently has to be run as superuser.Is there any workaround for this?

---

### Post by 23dornot23d on 2014-04-06
There is a discussion here about running it in a slightly different way ......

[http://forums.solydxk.com/viewtopic.php?f=8&t=2672](http://forums.solydxk.com/viewtopic.php?f=8&t=2672)

> 
Mozilla's extension Collusion (now revamped as  Lightbeam)


Interesting - did not realize this had been renamed/revamped.

---

### Post by cogset on 2014-04-06
Thanks a lot,I was kinda thinking something like that:after reading the link you've posted,as the discussion hinted to pretty much the same type of workaround,I've tried to apply the same guidelines for Wireshark  found here [http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)  to Etherape -and it worked.

---

