---
title: "Easy server protection"
date: 2008-07-02
forum: Server Platforms
---

### Post by stringkarma on 2008-07-02
Hello all, I have a question about hacking attempts.

I have several computers. The two I am interested in we will call work and server.

work) Ubuntu hardy (with X) and openssh-server and vnc

server) Ubuntu hardy (without X) and openssh-server and LAMP server

I have noticed recently that there have been many attempts to access these computers (both have static IPs) via ssh. No one has gotten in, but I want to start now. I need to have ssh running on both but I want to up my level of knowledge and hopefully protection.

Questions:
1) Reading the logs is hard on cat or less. Is there some way for me to read the logs from the server in some graphical environment on another computer. A remote log viewer for example.

2) I have been reading about intrusion detection, such as snort. I wouldn't mind trying this if there are simple ways to setup and administer this but I do not have the time to learn complicated systems. This is a simple server and I only need remote access to work. Do you have any suggestions for something that is easy to use but effective.

3) I have seen some things about hardening my install. For example the package harden-environment. Much in the spirit of question 2, is this something that I want to do and will it be easy enough for me to implement?

Of course if there are any other thoughts feel free to share them.

Thanks in advance.

---

### Post by windependence on 2008-07-02
Couple of tips for you.

1. VNC can be insecure sometimes. Always use it through an encrypted tunnel:

[http://www.maths.utas.edu.au/People/Hill/vnc/vnc.html](http://www.maths.utas.edu.au/People/Hill/vnc/vnc.html)

2. Of course in Ubuntu root logins are not allowed if using sudo, but if you had enabled the root user, do not allow root logins over ssh. Script kiddies need user name and password. Make it hard for them and make them guess both. If you need root after you log on via ssh, you can always use sudo, or su (if root is enabled).

3. You should use a good hardware firewall. Software firewalls are fine but have several drawbacks. the worst problem is that they use the local machine's resources, so if someone tries a DDOS attack on you, your firewall will dutifully block all the packets, all the while consuming more and more CPU or memory until your box crashes. Your firewall worked just as it should, but you still sent down because of resource consumption. That should not happen on a hardware firewall, and IMHO they are easier to configure than IPtables anyway.

-Tim

---

### Post by stringkarma on 2008-07-02
Thanks for the tips. I wish I could spring for a hardware firewall. Truth is I can handle a denial of service, I just don't want the system hacked.

I know not to enable root. Hooray for Ubuntu giving us this power!

---

### Post by Growbag on 2008-07-02
I always set my ssh server to a high port number and rarely get attacks!

It's very simple to do (edit /etc/ssh/sshd_config) and change the port number.

It stops the kids with simple port 22 sniffers because they would have to do a high range scan first, which takes time.

Also if the attacks come from fixed IPs, simply send a complaint to their ISP, you'd be surprised how effective that can be (as long as they're not in China or Russia).

Try webmin, it opens a new port (10000 by default), but is great for log reading and other things too.

Plus you can simply ssh into your server using -X on the ssh command line to enable X-server forwarding.

```
eg: ssh -p 50998 -X -l yourusername 192.168.0.10
```

So if you are logging in from a Linux machine, simply run any X command as normal (from the ssh terminal).

That will launch a remote copy of the prog, ie nautilus/kwrite or whatever.

It's slow over an internet connection, but on a local LAN it is great.

Just ask if you need more detailed info :)

---

### Post by osjak on 2008-07-02
> **stringkarma said:**
> 
2) I have been reading about intrusion detection, such as snort. I wouldn't mind trying this if there are simple ways to setup and administer this but I do not have the time to learn complicated systems. This is a simple server and I only need remote access to work. Do you have any suggestions for something that is easy to use but effective.


An easy to setup package is DenyHosts. It basically looks at your SSHD logs and changes *deny.hosts* file to disallow connections from hosts that have multiple failed logins. It is very configurable, with many options on how you want it to count those logins, when to "forgive" them etc. this is not bullet proof protection for your system, but it definitely stops those annoying script kiddies from cluttering your logs. 

I used [this article]("http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts") to setup DenyHosts on my server. The only missing point there - make sure to [whitelist yourself first]("http://denyhosts.sourceforge.net/faq.html#3_7") (guess, why I'm saying this, ha-ha).

---

### Post by stringkarma on 2008-07-02
Thanks osjak and growbag. Those are the kind of thing I am looking for, thinking smarter not harder!

---

### Post by hyper_ch on 2008-07-02
moving ssh to another port won't make it any safer.

you might want to use a auto-ban tool like denyhosts or fail2ban - that will ban IPs that have too many failed login attempts within a given time

as for reading the log files, you could use sshfs to mount the remote server into your local filesystem... then yo could open the log files in a text editor of your choice.

---

### Post by stringkarma on 2008-07-02
Thanks for all the suggestions, I just installed denyhosts on both computers. I think that this should do for now.

Of course if anyone has anything to add, please do.

---

### Post by hyper_ch on 2008-07-02
moving ssh to a different port will just produce less log entries... but it's not a security measure ;)

---

### Post by Dr Small on 2008-07-02
Setup FWKNOP (Firewall KNock OPerator) on the server, and the client on the work computer, and unlock the ssh port befor you connect. This way absolutely no ssh ports are open until you send the packet with the correct key, and then after you connect, the port closes again.

Safe, Secure, Deadlock.

---

### Post by osjak on 2008-07-02
> **Dr Small said:**
> Setup FWKNOP (Firewall KNock OPerator) on the server, and the client on the work computer, and unlock the ssh port befor you connect. This way absolutely no ssh ports are open until you send the packet with the correct key, and then after you connect, the port closes again.

Safe, Secure, Deadlock.
I have never needed this sort of security, but thinking about it, one thing comes to mind - easy for someone to cut me off my server. For example, if some BadGuy knows my IP address, then he can setup his machine to constantly (every 5 sec, for example) send SYN packets with my IP as origin (can be just one port) to mess up my sequence and effectively cause iptables to ignore my login attempts. Therefore my connection to the server is based on secrecy of my desktop IP address. And all it takes to get it is looking into email header that came from me.

Am I missing something? Have you ever had to deal with something like this?

---

### Post by Dr Small on 2008-07-02
I've never had anything like that happen, then again, I don't have alot of enemies.

---

### Post by Growbag on 2008-07-03
> **hyper_ch said:**
> moving ssh to a different port will just produce less log entries... but it's not a security measure ;)


"producing less log entries" means that less people are attempting to get in, ie less people are finding the port in the first place.

It's the same in "real life", if a thief doesn't see an open door, he will not even attempt to enter it.

It's a simple common sense thing to do.

The standard "script kiddie" is a schoolkid who is simply using an easily downloaded programme to mass scan as many IPs as possible, these progs expect SSH to be at port 22.

Moving SSH to a high port shouldn't be dismissed, it is very effective as it reduces the likelyhood of an attack in the first place.

Plus it reduces the load on your server as hundreds of these attacks can occur each minute, and your server is busy dealing with them!

Sure it doesn't "make it more secure", but if it helps avoid 99% of the attacks in the first place, in my book that is a good measure.

---

### Post by hyper_ch on 2008-07-03
> **Growbag said:**
> It's the same in "real life", if a thief doesn't see an open door, he will not even attempt to enter it.
If a thief wants to get in he will check everything ;) no matter if the door is visible or not... security through obscurity does not work - take windows... it's obscure but would you call it secure?

> **Growbag said:**
> The standard "script kiddie" is a schoolkid who is simply using an easily downloaded programme to mass scan as many IPs as possible, these progs expect SSH to be at port 22.
Yeah, but those are the kind of "attacks" that you don't even have to worry about ;) use an auto-ban tool ;)

> **Growbag said:**
> Moving SSH to a high port shouldn't be dismissed, it is very effective as it reduces the likelyhood of an attack in the first place.
It doesn't... I don't even call the script kiddies attempts as attacks... he who attacks, knows what he wants and he will not just try port 22 ;)... he'll nmap first and then start working ;)

> **Growbag said:**
> Plus it reduces the load on your server as hundreds of these attacks can occur each minute, and your server is busy dealing with them!
Doesn't put much load on any decent server... as said, auto-ban service will immediately drop connection then...

> **Growbag said:**
> Sure it doesn't "make it more secure", but if it helps avoid 99% of the attacks in the first place, in my book that is a good measure.
If you call a script kiddie attempt an attack, then it will avoid it... but IMHO you don't really call it an attack...
But I'm glad to see that you agree that it doesn't make it more secure ;) as said, it will just generate less log entries.

---

### Post by MJN on 2008-07-03
> **hyper_ch said:**
> security through obscurity does not work

What do you think passwords are...? ;)

I think what you really meant to say is that there are limits to security through obscurity. However there are limits to any security strategy hence why a combination of measures is usually your best bet.

Mathew

---

### Post by koenn on 2008-07-03
> **MJN said:**
> What do you think passwords are...? ;)

I think what you really meant to say is that there are limits to security through obscurity. However there are limits to any security strategy hence why a combination of measures is usually your best bet.

Mathew
OK, passwords work by "obscurity".
So If my password is simply 'A' (literally, without the quotes), I'm secure, because noone knows my password. 


=> obscurity doesn't count as a security strategy. The security of passwords is not so much in the password itself, but in the password policy.

---

### Post by Dr Small on 2008-07-03
If I ran John against a password hash (and that password was 'A') it would finish in probably less than 30 seconds. Having a strong password is essential.

---

### Post by ayenack on 2008-07-03
I have to say that I think that moving SSH to higher port is a good idea.

If for some reason a small network draws the attention of a professional cracker then she/he has good reason to be there, most certainly, would not bother with a home network based on GNU/Linux they may go for a Microsoft home network but that's doubtful also IMP.

The script kiddies out there will mostly attack on the standard port 22. If you get an attack on a port other than 22 then it's time to be worried.

---

### Post by Brazen on 2008-07-03
I can't believe this hasn't been brought up yet, but if you want to secure ssh, the best thing to do is to require Public/Private key authentication.  It's really easy to do.  Here is a guide to get you started: [http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

I didn't read the whole guide, but you'll want to be sure to edit the sshd-config to not allow keyless logins.

---

### Post by Kolipoki on 2008-07-03
> **osjak said:**
> ... make sure to [whitelist yourself first]("http://denyhosts.sourceforge.net/faq.html#3_7") (guess, why I'm saying this, ha-ha).

Ouch... it happened to me on my first attempt last week. Obviously couldn't Putty after that. Luckily it was a fresh install and the server was in the next room :lolflag: Otherwise would still be wiping my tears.

K.

---

### Post by windependence on 2008-07-03
I agree, moving ssh to another unexpected port is a good idea. In reality, most of the attacks I see are aimed at common apps on common ports where they expect to find the door open. Unless you have something valuable on your server, eg. you are a credit card company, most hackers are not that tenacious when trying to break in to a home network.

-Tim

---

### Post by Dr Small on 2008-07-03
> **Brazen said:**
> I can't believe this hasn't been brought up yet, but if you want to secure ssh, the best thing to do is to require Public/Private key authentication.  It's really easy to do.  Here is a guide to get you started: [http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

I didn't read the whole guide, but you'll want to be sure to edit the sshd-config to not allow keyless logins.
Yes, Keybased Authentication is another great security measure, which I use on all of my systems.

---

