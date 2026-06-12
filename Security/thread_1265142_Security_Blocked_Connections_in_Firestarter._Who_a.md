---
title: "Security: Blocked Connections in Firestarter. Who are they? Am I really secure?"
date: 2009-09-13
forum: Security
---

### Post by SlimBiggins on 2009-09-13
I've been running Ubuntu for about three weeks now. Previously I was an XP user. I've read alot of threads, but this is the second one I've posted. From what I understand, there is no way to to install a firewall *(you can only configure your IPTABLES, which is the down right nitty-gritty on controlling inbound/outbound  services). Firestarter seems to be the name that I've read the most, and (from what I understand) it is "always running" because once you install it, the GUI is simply there for configuring the IPTABLES. Now, lets get to the point. I have been keeping the FireStarter GUI running as much as possible since yesterday (my final re-install) to see what it can do. In a little over an hour, it has blocked three connections. I looked up their hostnames for this thread, and was hoping someone could tell me about Linux security risks. 

Time / Port / Source / Protocol / Service:
Sep 12 23:56:55        / 31685        / 58-114-238-165.cable.dynamic.giga.net.tw      / UDP           / Unknown  
Sep 13 00:59:31       / 51413        / bas7-montreal02-1096626263.dsl.bell.ca         / TCP           / Unknown
Sep 13 01:14:14       / 31685        / 58-114-238-165.cable.dynamic.giga.net.tw      / UDP           / Unknown

I made the switch to Linux for security reasons mostly. I know the internet is full of all kinds of threats. My main concern is: How do I run the most secure system? Is Firestarter the best way to go? Is there a firewall better than the UCF??? I really do not want to run Windows EVER again (from now own I'll call it the "W" word). In the little time I've spent with this Ubuntu forum, I've found the users to be more than friendly. I just want to make a complete switch. 

MORE:

In the time I've been typing, FireStarter just blocked two more:

Sep 13 02:09:02 / 31685 / 89.121.210.3 / UDP / Unknown
Sep 13 02:14:30 / 31685 / 58-144-238-165.cable.dynamic.giga.net.tw / UPD / Unknown

Am I running a secure sytem??? Please Help...

-The New Guy

---

### Post by rookcifer on 2009-09-13
Unless you are running services to the Internet at large, you don't even need a firewall.  If you are paranoid and feel you need a firewall, then a hardware router is the best bet (flashed with Linux firmware, of course).

The best way to stay secure with Ubuntu is:

1) Make sure the software you install only comes from the official Ubuntu repos.

2) Check for updates daily (usually this is done automatically) and always update when prompted.

3) Do not run SSH or VNC unless you know how to secure them.

4) On any desktop machine, the biggest threat is usually the browser.  Since the browser in Ubuntu is always being ran with limited privileges (read up on the Unix DAC) there is not as much of a threat to your box as compared to a Windows machine.  However that's not to say that some Linux specific Firefox exploit does not exist which could potentially compromise your /home directory. Therefore, it is good practice to take the usual Windows precautions when it comes to securing Firefox (NoScript, Adblock etc.). 

5) I also recommend reading the AppArmor sticky at the top of this forum.  AppArmor is a very powerful mechanism for creating security policies that are much more fine grained than the default Linux model.  You can create policies per application which can often times prevent known and unknown security exploits in the application from being successful.  AppArmor is known as a Mandatory Access Control (google for it).  I suggest you start with the sticky at the top of this forum -- it covers all you should need to know about using it.

6) Do not waste your time with AV software.  It is useless on Linux for a couple of reasons that I am too lazy to expound upon, but you can take my word for it.

Again, see the stickies at the top of this page.  I am sure there are a few points I left out here (but the above info is really about all you need).

---

### Post by cariboo on 2009-09-13
Welcome to the internet. Shut down Firestarter and quite watching the logs. :) what you are seeing are blocked or dropped connections. This is perfectly noraml. It is normally caused by bot nets or if you have downloaded any torrents lately.

---

### Post by The Cog on 2009-09-13
I agree with both the above posts. Those connection attempts are to ports that Ubuntu doesn't even listen on, so even if the firewall hadn't stopped them, the OS would have rejected them. In fact, Ubuntu doesn't listen on any TCP ports by default - you have to install a server for the appropriate protocol first. So you don't actually need the firewall anyway. Stop looking at the logs, they'll drive you mad in the end. If it ever stops logging things, that's the time to wonder why not.

Probably the biggest improvement in security you can make is to install the no-script add-on to firefox. That and don't download and run software from web sites on the internet - use the Ubuntu repositories.

---

### Post by bodhi.zazen on 2009-09-13
> **SlimBiggins said:**
>  Am I running a secure sytem??? Please Help...

-The New Guy

Ubuntu out of the box is more secure then hardened Windows.

If you wish to learn why you will need to do some reading. Ubuntu is not windows so you will need to learn new information.

There is a sticky that should get you started :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by lovinglinux on 2009-09-13
I agree with previous replies.

> **SlimBiggins said:**
> From what I understand, there is no way to to install a firewall *(you can only configure your IPTABLES, which is the down right nitty-gritty on controlling inbound/outbound  services). 

Not exactly. There is already a firewall running on your machine, but it comes without any rules, so all traffic is accepted. The firewall is called netfilter, although I usually says it is the iptables to simplify. Iptables is a tool that allows you to create rules for the netfilter, using commands. Firestarter is a tool that allows you to create the same rules, without knowing the iptable commands, so it is called firewall manager.

> **SlimBiggins said:**
> Firestarter seems to be the name that I've read the most, and (from what I understand) it is "always running" because once you install it, the GUI is simply there for configuring the IPTABLES. 

Firestarter doesn't need to be running all the time, because it's netfilter and iptables that does the job, not Firestarter. In fact, it should be closed as soon as you create the rules, due to security reasons. Besides, Firestarter is becoming old and problems are starting to show up. Firestarter is popular among recent Windows converts, due to the monitoring capabilities, which can be done with other tools or from command-line or simply by investigating the logs.

> **SlimBiggins said:**
> INow, lets get to the point. I have been keeping the FireStarter GUI running as much as possible since yesterday (my final re-install) to see what it can do. In a little over an hour, it has blocked three connections. 

I agree with previous posts, about not monitoring connections. If you are worried about that, learn what can allow an intrusion and what cannot. Running a firewall is not necessary if you have a router or if you don't install any applications that listen to ports. Even if you do, like for example when using a torrent client, you want to allow people to connect to your server application, so there is no point of using a firewall. Unless of course you want to limit the access to certain ports. For example, you might want to use a ssh server to connect two computers in your local network. Then you could use the firewall to block all connections to port 22, except from those originating from local machines. Besides, three connection attempts is nothing, really. Imagine how paranoid you could become if there are thousands of connection attempts, from hundreds of IP addresses? That's normal if you use torrent or if you get an IP from your ISP that was previously used by someone using torrent.

> **SlimBiggins said:**
> I made the switch to Linux for security reasons mostly. I know the internet is full of all kinds of threats. My main concern is: How do I run the most secure system?

[Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial is a very good start.

> **SlimBiggins said:**
> Is Firestarter the best way to go? 

Definitely not. If you want a modern firewall manager, then [gufw](apt:gufw) [apt-get] is the way to go. If you really need a firewall and need to have total control of your network, then learn iptables.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

> **SlimBiggins said:**
> MORE:

In the time I've been typing, FireStarter just blocked two more:

Sep 13 02:09:02 / 31685 / 89.121.210.3 / UDP / Unknown
Sep 13 02:14:30 / 31685 / 58-144-238-165.cable.dynamic.giga.net.tw / UPD / Unknown

Am I running a secure sytem??? Please Help...

You have made me remember a Harry Potter scene in which his uncle is trying to grab a letter from his hand, while hundreds of them are coming through the fireplace and the cousin says: "Daddy has gone mad, hasn't he?" :) 

Don't waste your time and good sleep monitoring those connections. As others already pointed out, they were blocked and even if they weren't, as long as you don't have any application listen to the port they are trying to reach, these connections are simply refused.


> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

### Post by SlimBiggins on 2009-09-14
I love this forum. I'm new to the whole forum thing, but still amazed at all the responses I get in such a short amount of time. I definitely will take this thread to heart and read up on everything. Its funny, I just got off the phone with a friend of mine back in my hometown (who has his Bachelor Degree in Computer Science). He was telling me about using apparmor. I know you guys know what your talking about for sure, as he brought up alot off the issues mentioned here.

Once again:

Thank you guys so much for all your help!!!

---

