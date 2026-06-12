---
title: "had port 22 open and have openssh-server installed, is this risky???"
date: 2016-06-08
forum: Security
---

### Post by a-you on 2016-06-08
Somehow openssh-server and openssh-client were installed more than a month ago. Perhaps it was installed either by lxd or by x2go client, when I was trying containers. I have since deleted all the containers, lxd and x2go.

Now I see that for all that time I've had port 22 open in both directions. Other than that I had the firewall set to it's stock "home" configuration so "in" was denied and "out" was allowed. I guess it was pretty dumb but I thought all this time that  openssh-server was not installed.

This is a laptop with a DSL connection to the internet, in Germany if that matters. I'm using ubuntu studio 16.04 xenial 64 bit. I've been keeping up with installing updates.

I didn't change any openssh-server settings in my "host" computer (the laptop).

Is the default configuration for openssh-server safe enough to have protected my laptop even though openssh-server was running AND listening on port 22??

And what can I do to investigate whether I might have been hacked?? I have read the auth.log files and they don't seem to have anything odd in them, but I'm far from being an expert.

Any advice, thoughts, help would be much appreciated! Thank you in advance!

---

### Post by TheFu on 2016-06-08
Never use password-based authentication over the internet. Always use ssh-keys.  Password ssh logins shouldn´t be allowed, IMHO.

[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) provides some tips to securing ssh.  Every machine I run has ssh-server installed and available. I usually have the router move the port to non-22/tcp.  UDP doesn´t matter, ssh is tcp.

x2go uses ssh. That is a good thing.  Just follow the link above and do what it says to do.

---

### Post by a-you on 2016-06-09
Thanks @TheFu. I'll go read your link now.

But I want to point out that I explicitly enabled password authentication ONLY inside the containers I was trying out, never on the laptop----but I wonder if password authentication is enabled by default???

What I was trying to ask was whether or not I had opened my laptop to attack by just having openssh-server running and port 22 open??

By the way I've uninstalled openssh-server and openssh-sftp-server. I  don't know what caused those to be installed but it seems to me I don't  need them.

Reading your link now. I see that in my /etc/ssh/sshd_config it says:
```
LoginGraceTime 120
PermitRootLogin prohibit-password
```

```
#AuthorizedKeysFile    %h/.ssh/authorized_keys
```

```
ChallengeResponseAuthentication no
```

It has "prohibit-password" and the AuthorizedKeysFile line is commented out. Hopefully that's good news.

But I also had:
```
UsePAM yes
```

And I see that I do have a ~/.ssh folder but that the file "authorized_keys" inside of it has 0 bytes. It's empty. But similar files exist and they're not empty in /etc.

Also in the sshd_config man page it says "**PasswordAuthentication**
Specifies whether password authentication is allowed. The default is ``yes''
Why yes??!
In my config file that line was commented out. Does this mean that it was by default enabled??!

I've read through all of the auth.log files (I only installed xenial from scratch a couple of months ago) and there are *many* entries like:
```
Received SIGHUP; restarting.
Server listening on 0.0.0.0 port 22.
Server listening on :: port 22.
```
and lines just saying it's listening, ie the "SIGHUP" line isn't there. There's also occasionally:
```
Received signal 15; terminating.
```

And back when I was playing with containers, when I guess I must have unwittingly installed openssh-server there are entries saying things like "Connection closed by 127.0.0.1..." and "Invalid user..." and related lines.

Any additional comments would be MUCH appreciated (from you or others) since I'm very noob. Many thanks in advance.

---

### Post by TheFu on 2016-06-09
My signature has links to security pages here and elsewhere.

IMHO, containers are not understood sufficiently to be used on the internet ... except for cat photos and only on infrastructure you don't care about (like a hosting company wouldn't). Lots and lots of people are making claims about the security of containers ... but claims are useless.  Only time in the wild, defeating attackers, counts. Plus lots of noobs are pushing containers because of all the features listed with less overhead.  Developers (not system admins) are the most dangerous.  They don't usually have a clue about the OS or security.  I was a professional developer for over a decade. I thought every issue was solvable by reading 2 hrs on it.  That isn't how things work anymore. It has been a different world for attacks for the last 20 yrs.

In theory, containers sound great, wonderful, and I'm hopeful that the 1,000+ bugs still in that code has minimal security impact. Hope is not a plan.  We though HMV was secure for about a decade (including me) then they found an old floppy disk driver that was included in almost all VMs provided a back door to the hostOS. **If you loose the hostOS, you've lost the war.**  With containers, the host's kernel is shared!  Be afraid. Be very afraid, for now.  We just need more time, more attacks defended, and more announcements about failures before I'll start to trust containers on the internet.

Containers inside a network, firewalled off from the outside (in AND out) - sure.  I'd use them for development and for testing. Don't think I'd use them for production systems inside a company yet. Sometimes the "bad guys" come from the inside. We don't need to make it any easier.

Openssh is a way of life for all Unix admins. Period.  This is the primary way that Unix systems administration is performed globally.  I have over 20 ssh connections up right now to other systems being managed through various means.  ssh is the best of the options BY FAR.  But there are risks with running it.  Every service/daemon that listens on a port is a potential attack vector.  Many of my systems only have 1 port available, ssh.  ssh runs on the physical systems, virtual machines, everywhere that isn't single purpose without an OS at all.  If I were using containers for 1 purpose - without access to a shell, then I wouldn't have ssh loaded inside it.  If all a container can do is run 1 program and ABSOLUTELY NOTHING ELSE, that would certainly help security.  I've run postfix and bind that way for decades.  Sorta boring if an attacker gets in - they can't actually do anything but run the single program inside that chroot. I imagine it is frustrating for them. ;)  Management of setups like that is harder, but containers (which are similar to chroot, but with more protections) can be run that way too. Learn to do that - no shells, no extra programs, no other tools INSIDE the container.  That is where I'd begin with security there. Then you wouldn't have a shell and the only way to manage the container would be from outside.

Protection of ssh isn't hard. The link previously provided will keep all the riff-raff out for years - unless there is an unknown bug in the server AND in the system firewall AND in the router providing the first layer of protection.  If you aren't using 3 DIFFERENT levels of protection for all your services, I think you've failed in securing a service.  But if you are hosting cat videos on someone else's computer and their network, I wouldn't worry too much. What do you have to loose that good backups don't solve?  If you are hosting it on YOUR network, I'd expect folks to break out of the container and have free reign over your network.  If that doesn't happen, count yourself lucky.  Of course, the chance of this happening is unknown - until you see it.

My blog has lots of "learning linux" ideas and links.  Also has lots of security-related articles - many link back to Ubuntu.com wiki and articles.  I was hacked when I was a noob about 20 yrs ago. It was scary AND great.  That converted me from **security is nice**, but not useful to **SECURITY IS VERY IMPORTANT.**

You get to choose how you feel about security, containers, etc.

Why have IPv6 enabled at all if it isn't used?  It is another attack vector for every connection used.

I've never found either of those root kit detection tools to be useful.  Versioned backups are the tool I put most of my trust in.  Versioned backups have 1001 uses.

Of course, I could be completely wrong.

---

### Post by a-you on 2016-06-09
Thanks again @TheFu, but I've removed all the lxd stuff. Not interested in containers. I'm not asking about them at all.

What I'm trying to understand is whether or not the *default* settings for openssh-server are sufficient to have protected my laptop, in spite of my having had port 22 open and openssh-server listening.

The laptop is connected via an "Alice Modem WLAN 1421" with firmware "1.00.16" in Germany via DSL.

I've managed to access this modem box in a browser and it looks like "PPPoE Pass Through" is enabled. Anyway so far I've not been able to learn whether port 22 would be blocked by its firewall, assuming that was even functioning.

This is hard for those of use that aren't working in your field :-( so if you don't mind commenting specifically on whether the default settings for openssh-server are enough to have protected me in spite of my having had port 22 open and the daemon listening I'd MUCH appreciate it. Many thanks in advance.

And too if you have any tips on how I can investigate whether there may have been attacks directed at my laptop, I mean how can I check if that happened?? As I mentioned, I did read the auth.log files but don't know what else to do.

Thanks again!

---

### Post by deadflowr on 2016-06-09
*Thread moved to **Security**.*

---

### Post by a-you on 2016-06-09
Hmm @deadflowr I guess you deleted the newer thread. I can understand why but tbh I'd prefer that one to this because this gives the wrong impression that I'm asking about containers when I don't care about that. Maybe I can edit to fix it...

---

### Post by TheFu on 2016-06-10
Does the default openssh-server settings come pre-configured for a secure system?

¨NO¨, is the safe answer. ¨It depends¨, is the real answer.  It depends on your network, router, edge router, and other systems on the same subnet whether this is secure enough or not.

Use the information on securing ssh connections already provided.  I use a few layers of protection on systems with ssh-server running (which is all of them).
a) edge router blocking (firewall there) with port translation
b) system firewall blocking (iptables)
c) fail2ban which recognizes brute force attacks
d) don´t use passwords for login authentication. Keys are both more secure AND more convenient. ** This is one of the few times when being more secure is actually easier.**  Using ssh-keys makes life 1000x easier.

ssh is a way of life and I feel it should be part of every user´s tools.  Why?  Sometimes a computer will seem to be locked up, but that is often just the GUI, not the OS, so being able to ssh into the machine from another will let us gather facts from the log files.  It is also handy for network-based backups.  ssh is the swiss-army-knife of Unix networking.  A remote desktop like x2go working over ssh as well.  That can turn a $100 chromebook (running linux native or in crouton) into a cheap remote access device. Great for travel.

If all you do to secure ssh/sftp is to load fail2ban, that is likely sufficient, provided passwords are prevented for remote connections as well.  IMHO.

**Update:**
Currently at a conference and I´ve been learning a bunch about containers and docker.  A security-centric guy from Redhat just gave a talk about Docker security where he recommends AGAINST running ssh inside a docker container for a number of reasons.  Docker is about running an isolated, container, for a single application. It is not supposed to be used to run a general purpose OS.  That´s what I heard, not necessarily what he said.  Videos from this conference should be posted to youtube in about 1-2 months, so be certain to check *from the horses mouth.*

---

### Post by a-you on 2016-06-11
Thanks again. Unfortunately I don't know if the ISP (which would in my case be the router I would guess) is blocking attempts from outside to port 22. I sort of think they are, just from reading the auth.log files and there being no mention of any attempts. But I don't know enough to be sure of that. I do now have an OS firewall, but because I had opened port 22 before when trying containers that port had been open---big mistake it would seem. I'll install fail2ban even though atm I have removed openssh-server. If I decide to install the server again I'll be sure to study the configuration options, especially disabling password authentication and also probably using a different port.

---

### Post by Doug S on 2016-06-11
> **TheFu said:**
> ssh is a way of life and I feel it should be part of every user´s tools.  Why?  Sometimes a computer will seem to be locked up, but that is often just the GUI, not the OS, so being able to ssh into the machine from another will let us gather facts from the log files.  It is also handy for network-based backups.  ssh is the swiss-army-knife of Unix networking.+1. Very well said.

---

