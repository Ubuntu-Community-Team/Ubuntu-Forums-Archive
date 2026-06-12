---
title: "Basic hacker watching"
date: 2008-03-30
forum: Security Discussions
---

### Post by othsy2k on 2008-03-30
Okay, so I'm hidden behind various security measures, but I'm still paranoid about hackers. I've heard that tracking hacker activity in Linux is "easier" than in other OS's.

That's all well and good but, I ask my peers and gurus...how do I start locking down the servers and desktops I run and where to I start looking for malicious activity? 

I'm sure there's a log file somewhere that will tell me about hack attempts. Does someone know what these logs files are and what to look for?

---

### Post by Dr Small on 2008-03-30
Try reading /var/log/auth.log, and learn the normal. When something goes wrong, you will see warning in the log.

---

### Post by The Cog on 2008-03-30
Also look at ossec.
[http://en.wikipedia.org/wiki/OSSEC](http://en.wikipedia.org/wiki/OSSEC)
[http://www.ossec.net/](http://www.ossec.net/)

---

### Post by jba6511 on 2008-03-31
you can also look into snort for a network intrusion device to alert you to potential port scans, exploit attempts, etc. Just remember to deploy it appropriately within your network.

---

### Post by anantshri on 2008-03-31
well auth log file is good for system loging details and warning's

snort is good to find vulnerable positions for possible network access.

over all i would suggest you to check and recheck al kind of log's as well as snort test's should be executed periodically on your system to get the better view as well as asurance about the hacking attempts.

---

### Post by sbenson on 2008-03-31
Ossec Hids rocks and I suggest it if your really wanting to log that system permanently.
But it's kind of a bear to start with due to false positives that need to be worked out.

Is it a server, or are you using it as a workstation too?
For a server just to take a temporarily peek at the traffic:
Scans, brutes, tickles.

At the command line:

iptables -A INPUT -j LOG
iptables -A FORWARD -j LOG

tail -f /var/log/syslog

Reboot to clear it.
and remember to make sure your log doesn't overtake your var partition.

It'll scare the hell out of ya if you have no firewall and the systems been on awhile.

Be aware: if your using it as a workstation, you'll see all the traffic you generate.

---

### Post by othsy2k on 2008-03-31
Thanks everybody for the responses. One of my boxes is a "server" of sorts, but like all Linux boxes, it's built out of a desktop.

I'll give your suggestions a shot and report back here soon.

---

### Post by othsy2k on 2008-04-04
Along with your ideas I found this site:

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

he seems pretty on the ball about what he discusses.

---

### Post by brian_p on 2008-04-04
> **othsy2k said:**
> Along with your ideas I found this site:

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

he seems pretty on the ball about what he discusses.

Actually, he doesn't go in for much discussion or analysis at all. First he sets up an Aunt Sally by using 'ultra' to describe Ubuntu's security and then knocks it down with 'weaknesses' and 'common Ubuntu exploits'. That's what will stick in a beginner's head as they read the remainder of the article.

If we just take the section on modifying the default settings. What are the implications for tmpfs being rw? I confess to not knowing but he didn't enlighten me.

There is a good argument for PermitRootLogin being yes but it is not mentioned. The setting is not necessarily insecure. There is a Debian bug for this (#431627) and it will not be fixed any time soon.

Changing permissions on /bin/su seems to gain very little.

---

### Post by Chayak on 2008-04-05
Ok the big point to remember about network security is the phrase "Defense in depth" which means don't just use one firewall, that means have two preferably of different manufacturers so if there is a zero day for one then the other will still be there.  Yes, even high end commercial firewalls can be gotten around or through, but the better the equipment you have you greatly reduce the number of people capable of breaking through.  You have to make a realistic assessment of your threat profile.  Are you a home user with a home server that isn't worth the time of a skilled operator or do you run something with a high value target such as a database of credit card numbers.  The most common things you will see is just bots or scripts scanning networks for boxes that respond and they'll try an SSH bruteforce attack on logins.  I've seen linux boxes cracked and it's normally because of one of two reasons.  The first being weak passwords, the second being they didn't keep up with updates.  If you somehow get the attention of a skilled individual that's intent on breaking into your system it will only be a matter of time and most likely if they're that good then you won't see any logs at all or see anything in system scans because they'll have a kernel mode rootkit hooked so deep in your kernel that it will be talking on the network and you'll never see the activity even in Wireshark on the box.  You'll have to have something outside of the box watching the traffic and even then it'll probably be masked as something innocent looking such as a DNS request or HTTP packet and transmitted very rarely.  Those are the type of rootkits and malware that you don't read about on the net or find with scanners because they're written by a pro for his use only and they never brag on forums or let it get spammed around the net by script kiddies and get it detectable by scanners in short order.  No system has perfect security.  The best you can do is take appropriate measures for your security risk and hope for the best.

---

### Post by theDaveTheRave on 2008-04-06
Hello All.

I've read with interest this thread, and had a quick read of a couple of the links which seem interesting.

I may have missed the part that covers my concern so if so please just point me in the correct direction and I will read again.....

However here is my question.

I have Wireshark set up on my system, and I have been to friends places and used their internet connections and used Wireshark to show that there system isn't very secure - I generally advise using MAC address filtering, as far as I am aware you can't get a device to "pretend" to have a MAC address other than its own - am I correct on this??

Anyway I was at home and did the same thing and looked at the traffic when I downloaded my email..... I wasn't particularly surprised when my username and password for my email supplier was displayed in my Wireshark console as it went through - my questions is this....

Can I "hide" my username and password details so as they appear as ######### or ********* as they pass through the system??

Also are the passwords also sent for access to the router??

I guess I can stop this by setting up my old desktop as an email server and "locking" it down with encrypted passwords etc, but at some point It will need to download the information from my provider, which I guess will allways be visible... is that correct, or will it only be visible to "root" users with "root" access to the network?

Your help is much appreciated, and I hope I haven't aksed a really "stupid" question.

thanks all for creating a great forum.

Dave

---

### Post by kaivalagi on 2008-04-06
I have a googlemail account and have it setup in thunderbird via secure IMAP. No one should be able to see my username and password as they'll be encrypted.

Can you forward on emails from your existing email provider to a google account, that way you could still read all your emails through a secure means.

Would that suit your needs?

---

### Post by brian_p on 2008-04-06
> **theDaveTheRave said:**
> Anyway I was at home and did the same thing and looked at the traffic when I downloaded my email..... I wasn't particularly surprised when my username and password for my email supplier was displayed in my Wireshark console as it went through - my questions is this....

Can I "hide" my username and password details so as they appear as ######### or ********* as they pass through the system??

TLS/SSL can be used if you want POP3 access from the internet. The ISP's server has to support it. If you are on your ISP's network, it may not be needed.

> Also are the passwords also sent for access to the router??
Dave

No.

---

### Post by wormser on 2008-04-07
> **theDaveTheRave said:**
> I generally advise using MAC address filtering, as far as I am aware you can't get a device to "pretend" to have a MAC address other than its own - am I correct on this??

```
sudo apt-get install macchanger
```

---

### Post by jba6511 on 2008-04-07
as previous posters stated mac addresses can be changed and ssl/tls needs to be used to encrypt data. Also, are you using a hub? if so replace it with a switch. Hubs broadcast all traffic so a sniffer such as wireshark will see all traffic generated by everyone connected on that hub. A switch eliminates this program. Of course there are ways around this (arp cache poisoning, mitm attacks, etc), but as said before "defense in depth".

---

### Post by theDaveTheRave on 2008-04-07
Thanks all for that inormation.

I'm pleased I asked... I think..??

my system currently passes through a wireless router, but I keep toying with the idea setting up my old desktop as a "server" for mail, web and print services...

From what you have sad I assume that with this set up I can "block" any sniffing more effectively.

I'm interested by the macchanger software, I didn't even know that this existed!

Thanks again, and I now feel I need to try harder setting up a more secure home system.

Cheers guys.

Dave

---

