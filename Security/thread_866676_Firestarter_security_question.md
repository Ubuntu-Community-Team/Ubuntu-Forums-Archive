---
title: "Firestarter security question"
date: 2008-07-22
forum: Security
---

### Post by uberlube on 2008-07-22
I decided to install firestarter today for the first time and I must say Im happy with the added security. Within 5 min it blocked 6 intrusion attempts and logged them in the events tab. When I was checking them over I started wondering if there was a way to investigate them further as the only info given was their IP's and which ports they tried to penetrate....lol penetrate. Anyway is there a way I can check them out further to see if they were harmless connections or if they were indeed of a malicious nature. And also if there is a way of sending a signal to the offender which would make his monitor blow up in his face? Or at the very least a way of reporting repeat attacks?

Cheers :guitar:

---

### Post by hyper_ch on 2008-07-22
what added security?
What intrustion attempts?

---

### Post by uberlube on 2008-07-22
1) I started using an SSH server and i installed Firestarter to calm my paranoia.

2) If you read my whole post youd see that I am trying to find out if they were even intrusion attempts or harmless apps trying to make a connection and how to investigate them to find out where they came from and what they do. 

And are you trying to say that a Linux PC is 100% secure against people trying to randomly guess your passwords to gain access to your system. I know that to date Linux is impervious against malware but as of the last "pwn to own", even though the linux system was not able to be hacked, the guy said that he could have used the same method of gaining access through a weakness in Flash i think it was that he used to crack Windows and Mac. It is possible as unlikely as it seems. Unless Im completely mistaken.

---

### Post by Archmage on 2008-07-22
99,9999999999999999999% of the attacks are just maleware that use a random IP to use a known Windows security hole that has been patched, but not all the Windows PC are updating...

If you want to know what this is, just do a google-search for the port numbers and you'll know what security hole they did want to use.

---

### Post by uberlube on 2008-07-22
Thanks Arch. I did try googling the port after it happened but it didnt come up with anything conclusive. Ill keep trying though when it happens.

---

### Post by hyper_ch on 2008-07-22
> **uberlube said:**
> 1) I started using an SSH server and i installed Firestarter to calm my paranoia.
You know what firestarter is, right?

> **uberlube said:**
> 2) If you read my whole post youd see that I am trying to find out if they were even intrusion attempts or harmless apps trying to make a connection and how to investigate them to find out where they came from and what they do.
I did read it... but you had 6 events in your logs and you alraedy jumped to the conclusion that those were intrusion attempts...

> **uberlube said:**
> And are you trying to say that a Linux PC is 100% secure against people trying to randomly guess your passwords to gain access to your system.
Nothing is 100% secure but if you don't have a weak password it should not be easy to find out for them... they'd have to brute-force you and for that I'd rather install denyhosts or fail2ban instead of running firestart tht closes just about everything upon installation.

---

### Post by uberlube on 2008-07-22
Firestarter is a software firewall correct? I figured it would be a good proactive way to improve my security. And yes I am known to jump to conclusions when it comes to these things. I am mostly here to get advice about network security and I heard about Firestarter alot in this forum and figured it would be a good place to start. If you think fail3ban is a better bet than I will definitely check it out.

---

### Post by uberlube on 2008-07-22
Also, if Firestarter blocks all newly installed apps from making connections is it still worth keeping around after you have all your fav programs installed for extra security or is it not even worth it.

---

### Post by hyper_ch on 2008-07-22
there we go, Firestarter is NOT a firewall ;)

IMHO it's worse to take "security precautions" without actually knowing what you do than taking no security precautions at all.

---

### Post by Master Chief on 2008-07-22
For the record - here's the text from Synaptic Package Monitor:

"gtk program for managing and observing your firewall
Firestarter is a complete firewall tool for Linux machines. It
features an easy to use firewall wizard to quickly create a
firewall. Using the program you can then open and close ports
with a few clicks, or stealth your machine giving access only
to a select few. The real-time hit monitor shows attackers
probing your machine."

In short it is a GUI front-end to control/monitor the firewall, and yes you got to start somewhere. Oh and despite what hyper_ch wrote; it is better to do something than to do absolutely nothing because there's no gain whatsoever from that approach.

---

### Post by uberlube on 2008-07-22
Undernieth the link to Firestarters page in google says this:
> A graphical interfaced Open Source firewall for Linux.

So that led me to assume that this was itself a FIREWALL or gives you a more PROACTIVE method of controlling your preexisting FIREWALL.

I guess once you pass 7000 posts in a forum people are more prone to CRITICIZE and PATRONIZE than GIVE ADVICE ;)

PS Im not trying to break your balls id just really like some advice on how to make my system more secure.

---

### Post by eentonig on 2008-07-22
I'll give you some basics.

- Ubuntu comes with a firewall by default, built into the kernel (iptables).
- This firewall is wide open (no panic, read the next line)
- Ubuntu listens to no ports by default. Thus, even if all connection attempts are accepted by the firewall, there is no program to pick them up.
- If you install an ssh-server, my guess is you want to have ssh access. So useless to block that port (tcp/22). Hence, still no need to install/activate a firewall.

- Firestarter is NOT a firewall. It's a GUI to manipulate the builtin FW.

So, in order to help you. What do you want to defend yourself against?

---

### Post by uberlube on 2008-07-22
There you go some advice I can use. Thank you. Also I installed fail2ban and it is exactly what I was looking for, protection from people trying to gain access to my server.

---

### Post by eentonig on 2008-07-22
You could have achieved the same, with iptables.

 It is possible to set up iptables rules to block ssh attacks. The following ruleset will allow at most 3 connections per minute from any host, and will block the host for another minute if this rate is exceeded.

> iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set \ 
 --name SSH -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -m recent --update --seconds 60 --hitcount 4 --rttl \
 --name SSH -j LOG --log-prefix "SSH_brute_force "
iptables -A INPUT -p tcp --dport 22 -m recent --update --seconds 60 \
 --hitcount 4 --rttl --name SSH -j DROP


Best advice I can give you. Read some docs on iptables, so you know what's possible. And then decide what you need or want.

---

### Post by uberlube on 2008-07-22
Thanks again for the advice and ill do just that.

---

### Post by hyper_ch on 2008-07-22
> **Master Chief said:**
> Oh and despite what hyper_ch wrote; it is better to do something than to do absolutely nothing because there's no gain whatsoever from that approach.
Not really, not knowing what you're doing and assuming you're safe is probably the worst thing you can do ;) If you however don't do anything then you know you have to be carfulle ;)

> **uberlube said:**
> I guess once you pass 7000 posts in a forum people are more prone to CRITICIZE and PATRONIZE than GIVE ADVICE ;)

PS Im not trying to break your balls id just really like some advice on how to make my system more secure.
You might think of me criticizing and patronizing you, however there are two ways how I can tell you something. Either I can give you just the solution upon which you don't have to think a tiny bit or I can challenge you to start thinking on your own. In the end, what do you think from which approach do you gain more? It is painful to think yourself, I know, but once you comprehend the workings behind you'll know a lot better to manage yourself.

---

### Post by eentonig on 2008-07-22
I must agree with hyper_ch. Allthough his comments might sound/feel harsh, his approach is actually a lot nicer in the long run.

It's also the only reason why I gave you those iptables commands. To show you that there's always another solution to any given problem. And that you need to think things through before jumping on a solution. Personally, I prefer not to install redundant applications if I can achieve the same with the standard setup and understanding. (Saves a lot of work when reinstalling or porting a setup to another client)

---

### Post by Archmage on 2008-07-22
Sorry, I didn't know that you want to secure SSH.

To know this, there are a lot of howtos out there.

Like changing the port, allowing only a specific IP-range, blocking IPs after a few attems or allowing only keys.

Firestarter is a start to get some level of security, but this shouldn't be the only step.

---

