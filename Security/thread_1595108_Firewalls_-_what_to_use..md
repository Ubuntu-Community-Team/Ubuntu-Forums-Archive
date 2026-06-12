---
title: "Firewalls - what to use."
date: 2010-10-12
forum: Security
---

### Post by Jonny87 on 2010-10-12
I'm currently using Firestarter and I really like it for its listing of events and ability to add policies in by right clicking events etc.

However, I've been wondering, is it the best?
I wanting to know from people what they prefer as a graphical firewall. I've used GUFW and while I liked it for its simplicity in use I found a little too simple. Thats why I like firestarter.

I'm looking for a firewall that is easy to use but has plenty of advance feature to fully secure the computer. I have read the security sticky thread but I like to get the opinion a wide rang people.

---

### Post by Machiavelli on 2010-10-13
[FONT="Trebuchet MS"]I believe that Firestarter has been discontinued. As far as I know there is NO need to use any firewall in Ubuntu. The only time you need a software firewall is when you do not trust the software you use or your ability to set it up. It is often easier to set up the software but to understand how the software works, and configurable firewall for this. You can trust the software that ubuntu itself provides. For ultimate security, use only the software source ubuntu provider and be sure to keep the software up to date with the Ubuntu Update Manager.  

[/FONT]

---

### Post by phredbull on 2010-10-13
I too thought that a Firewall is not needed unless your machine is set up for Remote Viewing or something.

---

### Post by Jonny87 on 2010-10-13
Yea while a firewall may not be needed for the average home user running linux, I think it would be a bold statement to say that its not needed altogether. And to reject the need for a firewall I would think is poor network security practice.

I do realize that the threats in Linux are far less than in Windows, that was one of the things that appealed to me when first looked into changing to Linux. Though as secure as it is, no OS is **100%** impervious from attacks.

---

### Post by HermanAB on 2010-10-13
Bear in mind that most firewall devices actually run Linux.  So, do you want to put a firewall in front of the firewall recursively?  It will be good business for Cisco...

So, no, most Linux systems do not need firewalls.  The Linux network stack is pretty strong by default.  Firewalls are only needed if you are doing unknown things, like hooking up Windows machines with unknown services running on them.

---

### Post by robert_pectol on 2010-10-13
Host-based firewalls on Linux are generally not useful unless you have specific reasons that warrant it.  Most users will find that they hinder more than they help.  So unless you are running any Internet facing daemons that provide services to external users, AND you need tighter access controls than the daemons themselves provide, perhaps a firewall could be useful.  It is somewhat situation dependent.   But under most circumstances, a host-based firewall is unnecessary.  To run a firewall just to say you have a firewall doesn't make too much sense but if it helps you sleep at night, go for it!  As you become more familiar with Linux and security, you'll come to the same conclusion.

---

### Post by wacky_sung on 2010-10-13
I totally disagree with people mention about running without firewall.If you think people cannot hack into your system but you can never stop people from crippling/hijacking your bandwidth by performing DDOS / brute force using dictionary attack.

---

### Post by uRock on 2010-10-13
A firewall is not needed unless server applications are installed or if there is no router between the host and cable/dsl modem.

IPTables are running by default. To configure IPTables using a GUI, then install GUFW via the Ubuntu Software Store.

I only enable the firewall on my netbook when I am connected to a public LAN, such as that at my school.

---

### Post by The Cog on 2010-10-13
> **wacky_sung said:**
> ... you can never stop people from crippling/hijacking your bandwidth by performing DDOS 
No. Nor will configuring firewall rules on your computer. The link is already flooded and unusable before the traffic even reaches you. For that kind of attack, you need your ISP to stop the flood of incoming traffic. > ...brute force using dictionary attack.To what service? A default Ubuntu doesn't have any listening services, doesn't accept incoming connections at all. So there's nothing to submit dictionary passwords to. 

What's more, if you do decide to install something like an SSH server and you had installed a firewall, you would then have to reconfigure the firewall to allow the connections in again anyway, otherwise installing the server would have been a complete waste of time.

The windows need for a firewall is to block connections to all those services that are running by default that you don't know about or don't know how to stop. That need is not there in Ubuntu Linux. Simply installing a firewall on Linux for the feel-good factor is a waste of time: you waste time installing it because there was nothing for it to block in the first place, and if you later install a service that you want then you waste further time reconfiguring it to let the connections into the service again. 

A firewall is useful for filtering. If you have a list of IP addresses that you want to whitelist or blacklist rather than just allowing everything, then a firewall is useful. Or if you want to configure rules that block IP addresses that make too many connections too frequently (no use for a web server). But in either of these cases, you have a specific use for the firewall and **know** that you need it and know that you are going to configure it accordingly.

---

### Post by wacky_sung on 2010-10-14
> **The Cog said:**
> No. Nor will configuring firewall rules on your computer. The link is already flooded and unusable before the traffic even reaches you. For that kind of attack, you need your ISP to stop the flood of incoming traffic.

I do not think you really need a ISP to filter DDOS if the attack is small where iptables is able to handle it.The time you really seek ISP help when attack by botnet.

 > To what service? A default Ubuntu doesn't have any listening services, doesn't accept incoming connections at all. So there's nothing to submit dictionary passwords to.

You do not require a listening services to break into a system.What is need is using exploits or creating exploit to break into any default program used by ubuntu.Therefore firewall is still needed where it act as a barrier.You do not require to perform dictionary attack on SSH but you can do it by breaking the sudo password where you get root.

---

### Post by The Cog on 2010-10-14
> You do not require a listening services to break into a system.What is need is using exploits or creating exploit to break into any default program used by ubuntu.Therefore firewall is still needed where it act as a barrier.You do not require to perform dictionary attack on SSH but you can do it by breaking the sudo password where you get root.
Sorry, I don't understand what you mean. I don't see how you can exploit a system if it's not accepting connections. And a default Ubuntu doesn't accept connections, firewall or not.

---

### Post by wacky_sung on 2010-10-14
> **The Cog said:**
> Sorry, I don't understand what you mean. I don't see how you can exploit a system if it's not accepting connections. And a default Ubuntu doesn't accept connections, firewall or not.

You need not to have listening connection from your victim if you are using exploit to crack a system.If you do not believe me, try to compile an exploit to use it locally or remotely depending on the type of exploits in which you are using.

---

### Post by The Cog on 2010-10-14
I don't see how you can "use an exploit" to break into a system if you can't connect to it. But that's beside the point really - we were discussing whether firewalls are necessary. I still maintain that in general they are not necessary because they don't add anything: a default Ubuntu install doesn't accept incoming connections, and so doesn't need a firewall to block incoming connections.

If it is possible to "use an exploit" to break into a system without connecting to it then firewalls are useless, and so is the fact that Ubuntu doesn't accept incoming connections.

---

### Post by robert_pectol on 2010-10-15
> **wacky_sung said:**
> You need not to have listening connection from your victim if you are using exploit to crack a system.

Nope!  With no services listening, you have no entrance vector unless you can successfully attack the network stack.  Not gonna happen! :)

> **wacky_sung said:**
> If you do not believe me, try to compile an exploit to use it locally or remotely depending on the type of exploits in which you are using.

This doesn't support your case.  How does compiling an exploit prove your point, especially a local one?  It's either a distractor statement, or you're really confused!

---

### Post by amac777 on 2010-10-15
> **The Cog said:**
> If it is possible to "use an exploit" to break into a system without connecting to it then firewalls are useless, and so is the fact that Ubuntu doesn't accept incoming connections.

Maybe the OP means if you somehow got malware installed that acts like a server and listens for connections on some random port without your noticing then the firewall would prevent anyone from connecting to that port?

Of course, if you only use the trusted Ubuntu repositories to install software that would be highly unlikely to happen.

---

### Post by Jonny87 on 2010-10-15
> **amac777 said:**
> 
Of course, if you only use the trusted Ubuntu repositories to install software that would be highly unlikely to happen.
I agree with you there, though sometimes that isn't always possible when it comes to requiring additional drivers for a printer or some new PCI device that you've just brought. The not so technical person may not know exactly what to look for or what to trust.

Anyway back to the main topic, Firewalls, I must say that this thread has surprised me with the responses. While it goes against my training and what I've been taught on this matter, I'm willing look into it a bit more. Perhaps if someone could provide some references to support the idea that Linux doesn't need a firewall (something reasonably official preferably), I would be able to check it out.

---

### Post by The Cog on 2010-10-15
It's possible that's what he's thinking. But once the once malware is running on your system, it's Game Over. A firewall isn't going to help once the bad guy is inside the system. Look at all the millions of windows PCs that had the firewall enabled, and yet happily send your credit card details to strangers and stream spam.

The prime purpose of a firewall on windows is to block incoming connections to all the listening services that a default windows install opens. I have to say that the logic of making an OS with lots of services listening by default, and then installing a firewall by default to block them all again seems somewhat odd. But that's what makes so many people think that a firewall is always needed. On windows, it is.

---

### Post by HermanAB on 2010-10-15
Exactly.

There is no magic in 'ports'.  A port is just a Berkeley number.  An open port has a service listening for that number.  A closed port has nothing listening.

A software firewall hooks itself in front of the network stack so that it listens on all ports and then drop packets on the closed ports, in case there is something stupid listening somewhere behind it.  This is the way Microsoft usually does things.  Whenever someone discovers a problem, they layer another band-aid on top, instead of fixing the problem.  So a firewall really is just a big box with 65,000 band-aids and on a properly configured Linux system, you don't need it, save the band-aids for Windows.

---

### Post by Jonny87 on 2010-10-15
Would still like to see some references to support these claims.

If Ubuntu does not require a firewall what so ever, why does it come with ufw installed and in response to the above post, why are all ports open by default? If you have it all closed of you would get internet access and you have basic users getting frustrated cause their applications wouldn't communicate out. 

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)

So if there is no need to have a firewall at all, why just not have ufw  and instead use the time and space into including something that explains why there isn't a firewall and why Ubuntu doesn't need one. One of the install slides perhaps.

---

### Post by Velnias on 2010-10-15
Firewall makes my Ubuntu box safer despite all possible my and linux errors. And its a lot easer and quicker to enable - no need to be an IT proffesional.

---

### Post by OpSecShellshock on 2010-10-15
> **Jonny87 said:**
> If Ubuntu does not require a firewall what so ever, why does it come with ufw installed and in response to the above post, why are all ports open by default? If you have it all closed of you would get internet access and you have basic users getting frustrated cause their applications wouldn't communicate out. 

It's not really a matter of open/closed. What's really going on is that user-controlled processes on the desktop side can always initiate outgoing connections themselves, but external hosts cannot initiate a connection if there is no listening service for them to connect to. External hosts *can* respond to connections initiated and established by the local desktop, so everything still works without the user having to specifically enable it.

So for example when users fire up a browser, POP/IMAP mail client, or IM client, they are the ones making that initial connection, and then as long as it's running they can get responses to HTTP requests, can get their mail from the servers, or can have their friends send IMs.

---

### Post by wacky_sung on 2010-10-15
> **The Cog said:**
> Sorry, I don't understand what you mean. I don't see how you can exploit a system if it's not accepting connections. And a default Ubuntu doesn't accept connections, firewall or not.
I do not wanna make a debate whether is it possible to connect a system in which it does not have a listening port in ubuntu.By default it still listen to 127.0.0.1.Of course the exploit in which you gonna use it specially written exploit the weakness of the application running in it.To crack into a system you need to know what type of OS and application use,then you find an unpatch application exploit to crack in or perform a buffer overflow on the application to test / find a weakness in it.If you persisted not,then you shall join the [blackhat conference]("http://www.blackhat.com/index.html") in which things are done beyond the normal way.

---

### Post by amac777 on 2010-10-15
> **Jonny87 said:**
> So if there is no need to have a firewall at all, why just not have ufw  and instead use the time and space into including something that explains why there isn't a firewall and why Ubuntu doesn't need one. One of the install slides perhaps.

I think there are situations where a firewall may be desired and therefore the firewall functionality (iptables) is built in to Ubuntu. What most people are saying in this thread is that, for the typical home user, configuring the firewall wouldn't really add any extra security - especially if the home computer is behind a router (ie, using NAT), which acts as a firewall itself. 

That said, if you know how to configure it, iptables can be used to provide various security and network related functions that some people may find useful for special situations. One example is a howto I wrote that shows how you can use iptables to run any program on your system without giving that program outgoing network access. This is useful to not allow a program to "call home" without your permission. Another example of where I have used iptables was when I shared residence with some other people and I didn't want some of them trying to use my computer (ie printing from my network shared printer). So I used the firewall to blocked all incoming connections that originated on our shared network that weren't on an exception list of IP addresses for computers that I used. The result was they wouldn't see my shared printer. There might be a way to do this without using a firewall but since I already knew how to configure the firewall it was easy and effective to do this blocking at the firewall level.

So there are definitely uses for a firewall and I'm glad that Ubuntu has it installed by default. But I do also agree with the general sentiment on this thread that, without having a specific reason, a firewall isn't necessary to make a default install of Ubuntu "safe".

---

### Post by The Cog on 2010-10-15
> **Jonny87 said:**
> If Ubuntu does not require a firewall what so ever, why does it come with ufw installed
It doesn't come with ufw installed. Ufw is in the repositories, and you have to install it separately after installing Ubuntu if you want it.

EDIT:
Wrong! It does get installed by default, but it is not activated. My bad.>  and in response to the above post, why are all ports open by default?They are not. I invite you to try to connect to default Ubuntu install from another machine on the same network - for **example telnet 1.2.3.4 23** using the IP address of the Ubuntu machine, and any port number you choose. You will get connection refused. Or install nmap on another machine and scan the fresh Ubuntu install - you find all ports closed.

As amac777 says, there are times when a firewall is useful - when there are specific things that you want to permit or block. But the default Ubuntu install doesn't accept incoming connections and permits all outgoing connections, and that's what a default firewall install does for you.

---

### Post by cariboo on 2010-10-15
Just a slight correction, **ufw** is installed by default, it's **gufw** that needs to be installed if needed.

---

### Post by bodhi.zazen on 2010-10-15
See :

[https://wiki.ubuntu.com/ZeroConfPolicySpec](https://wiki.ubuntu.com/ZeroConfPolicySpec)

[https://wiki.ubuntu.com/SecurityTeam/FAQ](https://wiki.ubuntu.com/SecurityTeam/FAQ)

From the second link:

> ufw is available in all new installations of Ubuntu since 8.04 LTS, but is disabled by default. The standard Ubuntu installation has a no open service ports  policy, so enabling the firewall by default doesn't gain any extra security in the default installation, but could provide confusion for people new to Ubuntu when new software that is installed does not work because of restrictive firewall rules. As a result, when first adding ufw to Ubuntu it was decided that users must 'opt-in' to using the firewall. In Ubuntu 9.04 and later, you can enable ufw during installation using preseeding. See /usr/share/doc/ufw/README.Debian for details.

IMO, for the vast majority of Desktop users, if you still wish to enable your firewall, open a terminal and run:

```
sudo ufw enable
```

Done in one command.

---

### Post by MaxTesla on 2010-10-16
Lots of people here are fanatics and believe that there is no, and never will be any security threat what so ever in any possible way to any linux system ever
 

 So just ignore them, to answer the question if you open mozilla firefox and have the default page there in ubuntu then there is a link below the search field with says ubuntu help or something like that if you click that link a new window will open giving a list of different ubuntu version, click on the newest version then click on keeping your computer safe link and that page will list several firewalls for you to use

---

### Post by uRock on 2010-10-16
> **MaxTesla said:**
> Lots of people here are fanatics and believe that there is no, and never will be any security threat what so ever in any possible way to any linux system ever
 

 So just ignore them, to answer the question if you open mozilla firefox and have the default page there in ubuntu then there is a link below the search field with says ubuntu help or something like that if you click that link a new window will open giving a list of different ubuntu version, click on the newest version then click on keeping your computer safe link and that page will list several firewalls for you to use
Ubuntu is not Windows. A firewall is already in place in ubuntu. It just needs to be turned on with **sudo ufw enable **in a terminal to get it going.

---

### Post by CharlesA on 2010-10-16
> **uRock said:**
> Ubuntu is not Windows. A firewall is already in place in ubuntu. It just needs to be turned on with **sudo ufw enable **in a terminal to get it going.

+1.

You can also use gufw for a GUI.

You can even use plain iptables if you so desire.

Also take a look at the links that Bodhi posted.

---

### Post by OpSecShellshock on 2010-10-16
> **MaxTesla said:**
> Lots of people here are fanatics and believe that there is no, and never will be any security threat what so ever in any possible way to any linux system ever
 

 So just ignore them, to answer the question if you open mozilla firefox and have the default page there in ubuntu then there is a link below the search field with says ubuntu help or something like that if you click that link a new window will open giving a list of different ubuntu version, click on the newest version then click on keeping your computer safe link and that page will list several firewalls for you to use

This is hardly accurate. People here talk about threats to systems all the time. However, such threats can't be stopped by a firewall. A firewall also wouldn't stop malware, if there were any in active use. For that matter, AV software wouldn't stop malware either since it would initially be an "outside context problem" on Linux. It's impossible to mitigate a threat that is not yet defined, and therefore it's not possible to just bolt on and switch on an application that protects the system from anything real or imagined.

To a great extent what users can do is constrain web-aware applications with apparmor and script-prohibiting browser extensions, and they can also install software from trusted sources. User sessions are already running under limited permissions by default, and require conscious elevation for all system-level tasks. These things do far more than any firewall or AV software ever could.

---

