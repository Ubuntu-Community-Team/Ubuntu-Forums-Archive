---
title: "Fake SSH?"
date: 2010-05-12
forum: Security
---

### Post by Penguin Guy on 2010-05-12
**NOTE:** This is not to do with securing SSH, it's just a trick to waste hackers' time.

Don't you just hate those spam phone calls you get? Most people just hang up, but my theory is to waste as much as their time as possible. Can I do something similar with SSH? Since I don't use SSH, I was wondering - is it possible to run a fake SSH server, so that any attackers who stumble across my IP will waste their time trying to crack my password? If so, how can I do it?

Solution (thanks to [cdenley]("http://ubuntuforums.org/showthread.php?p=9287065#post9287065")):
```
sudo apt-get install openssh-server && echo **DenyUsers *** | sudo tee -a /etc/ssh/sshd_config && sudo /etc/init.d/ssh restart && echo 'Fake SSH server setup complete!'
```

Standard system (ignore attacker):
```
attacker: login root 'password123'
you: ...
attacker: login root 'password456'
you: ...
**<attacker gets no response and leaves>**
```

Solution (say 'no' to everything):
```
attacker: login root 'password123'
you: Nope. :)
attacker: login root 'password456'
you: Nope. :)
attacker: login root 'password789'
you: Nope. :)
**<attacker keeps on guessing>**  *(and since login is blocked, they are wasting their time)*
```

Here's a short script to list IP addresses and number of failed logins so you can see if your fake SSH is doing any good (sadly it only works from when the computer was switched on):
```

#!/bin/sh
cat /var/log/auth.log | grep 'Failed password for' | sed 's_ invalid user _ _' |\
sed 's_[a-zA-Z]* [0-3][0-9] [0-9:]* [a-zA-Z]* sshd\[[0-9]*\]: Failed password for \([a-z]*\) from \([0-9:.]*\) port \([0-9]*\) [a-z0-9]*_\1\t\2_' |\
sort -nr | uniq -c | sed 's_^ *\([0-9]*\) _\1\t_'

```

---

### Post by cdenley on 2010-05-12
```

sudo apt-get install openssh-server
echo AllowUsers nobody|sudo tee -a /etc/ssh/sshd_config
sudo /etc/init.d/ssh restart

```
This installs an ssh server, but then allows only the user "nobody" to login. Since the "nobody" user is disabled, this is impossible.

---

### Post by almahtar on 2010-05-12
An easy way to do it would be to set up a bogus user (named "fakessh" or the like) and set up SSH to only allow that user to log in. Then set their shell (in /etc/hosts) to /bin/false so if it did manage to guess the password it wouldn't let them login.

---

### Post by cdenley on 2010-05-12
> **almahtar said:**
> An easy way to do it would be to set up a bogus user (named "fakessh" or the like) and set up SSH to only allow that user to log in. Then set their shell (in /etc/hosts) to /bin/false so if it did manage to guess the password it wouldn't let them login.

Even if they don't have a valid shell, they can still connect and use port forwarding to access the network. Better than hoping they don't guess the password would be to make it impossible by giving the user an invalid password hash.
```

sudo usermod -p ! fakessh

```
Or just use the "nobody" user like I suggested.

---

### Post by Penguin Guy on 2010-05-12
> **cdenley said:**
> ```

sudo apt-get install openssh-server
echo AllowUsers nobody|sudo tee -a /etc/ssh/sshd_config
sudo /etc/init.d/ssh restart

```
This installs an ssh server, but then allows only the user "nobody" to login. Since the "nobody" user is disabled, this is impossible.
It works! Thanks!

---

### Post by sedawk on 2010-05-12
An efficient network scanner will not care if one scan
hangs for a few seconds. After a timeout it will most likely
give up.

So the time you invest and the risk you might create are
not worth it (do not open ports you do not have to - the
software on that port is always a increased risk).

Otherwise check for "honeypot" - I think that is what
they call network services designed to detect intruders.

If you are annoyed by people trying to hack your ssh then
have a look at "knock" services. E.g. you can use
a "knock" client that knocks your PC on port 88. Only
if the correct knock-code is received will your computer
start (temporarily) a service like ssh.

---

### Post by Penguin Guy on 2010-05-12
[sedawk]("http://ubuntuforums.org/showthread.php?p=9287297#post9287297") - You completely lost me with that post - you're saying this won't work?

---

### Post by bodhi.zazen on 2010-05-12
I think the best solution is to simply enable your firewall with a policy of DROP rather then REJECT.

Try it on a test server, if you set the Default policy to REJECT and then scan the box w/ nmap, it will take a short time.

Now set your policy to DROP and re-scan ...

If you wish to actually install a "fake" ssh server, I agree with the advice that you look into setting up a honeypot.

Edit: any policy in iptables seems to slow scanners down significantly.

iptables -A INPUT allowed_traffic ...
iptables -A INPUT allowed_traffic_2 ...
iptables -A INPUT -j DROP or REJECT

---

### Post by cdenley on 2010-05-12
> **Penguin Guy said:**
> [sedawk]("http://ubuntuforums.org/showthread.php?p=9287297#post9287297") - You completely lost me with that post - you're saying this won't work?

I'm not sure what he meant by a scan "hanging for a few seconds". I think he misunderstood what you were trying to accomplish. He has a point saying that running a server can increase the risk that you can get compromised. It is very, very unlikely that there will be a vulnerability in ssh that could be exploited without authenticating first, though. Your idea basically is a honeypot. A honeypot is a system which lures an attacker into thinking you are vulnerable so they can be identified or isolated.

---

### Post by Penguin Guy on 2010-05-12
> **bodhi.zazen said:**
> I think the best solution is to simply enable your firewall with a policy of DROP rather then REJECT.

Try it on a test server, if you set the Default policy to REJECT and then scan the box w/ nmap, it will take a short time.

Now set your policy to DROP and re-scan ...

If you wish to actually install a "fake" ssh server, I agree with the advice that you look into setting up a honeypot.
But if you drop the connection then surely the attacker will soon realize that they are getting no response and leave? And what is the advantage of a honeypot (as I understand it, it's a bit like a [FONT="Courier New"]chroot[/FONT])?

---

### Post by cdenley on 2010-05-12
> **Penguin Guy said:**
> But if you drop the connection then surely the attacker will soon realize that they are getting no response and leave? And what is the advantage of a honeypot (as I understand it, it's a bit like a [FONT="Courier New"]chroot[/FONT])?

Don't use a chroot environment as a honeypot. I thought about doing this once by allowing attackers to login as root to my chroot environment using a weak password. This is a horrible idea, though, since if the attacker realized they were confined to a chroot, they can very easily break out and root your actual system. I ended up creating an actual fake ssh server which emulated output from a handful of commands, but nobody ever tried to use it. If you try running a honeypot, you have to be very careful.

---

### Post by Penguin Guy on 2010-05-12
[cdenly]("http://ubuntuforums.org/showthread.php?p=9287598#post9287598"): Why would you want a honeypot though? What's the obsession with letting your attackers into a fake version of your system? Is it just for fun?

---

### Post by bodhi.zazen on 2010-05-12
> **Penguin Guy said:**
> But if you drop the connection then surely the attacker will soon realize that they are getting no response and leave? And what is the advantage of a honeypot (as I understand it, it's a bit like a [FONT=Courier New]chroot[/FONT])?

Sounds as if you are interested in a honey pot.

Honeyposts are much more secure then a chroot jail.

---

### Post by cdenley on 2010-05-12
> **Penguin Guy said:**
> [cdenly]("http://ubuntuforums.org/showthread.php?p=9287598#post9287598"): Why would you want a honeypot though? What's the obsession with letting your attackers into a fake version of your system? Is it just for fun?

As I said, so you can identify attackers. Also, the logic is that if they are looking to attack you, they will see your honeypot, and attack that since it appears to be your weak point. It could theoretically deflect attacks on your real servers. If you're asking why I did it, it was because I had too much time on my hands, I was curious about what attackers would attempt to do on a system they gain access to, and I thought it would be a good programming exercise. I also setup FTP and SSH honeypots which would refuse and log all usernames and passwords tried to determine what a typical attacker's dictionaries look like.

As I said, your fake ssh setup you're after is basically a honeypot, so why do YOU want a honeypot?

---

### Post by CharlesA on 2010-05-12
A Honeypot would be a bit more secure then trying to set up a "fake SSH" server.

---

### Post by Penguin Guy on 2010-05-12
> **bodhi.zazen said:**
> Sounds as if you are interested in a honey pot.

Honeyposts are much more secure then a chroot jail.
[LIST]
[*]I don't see the point in honeypots, chroots or BSD jails
[*]I know chroot is not a secure way of trapping attackers
[*]My network is secure - this is not a diversion, I just want to waste the attacker's time
[/LIST]

> **CharlesA said:**
> A Honeypot would be a bit more secure then trying to set up a "fake SSH" server.
I believe my solution is full-proof against automated attacks.

[cdenley]("http://ubuntuforums.org/showthread.php?p=9287729#post9287729"): I guess your answer is basically that honeypots are used either as a diversion or for fun - that's my question answered. As for why I want to set up a honeypot, I just want to waste hackers' time as I do with spam phone callers.

---

### Post by cdenley on 2010-05-12
> **CharlesA said:**
> A Honeypot would be a bit more secure then trying to set up a "fake SSH" server.

I could be wrong, but I think a honeypot can be any server or service meant to be perceived as a vulnerability without actually being one. I think a service which appears to allow authentications but actually doesn't would qualify.

---

### Post by cdenley on 2010-05-12
> **Penguin Guy said:**
> 
I don't see the point in honeypots, chroots or BSD jails

Chroots and BSD jails are useful tools for confining/isolating users or processes, though not always fool-proof.

> **Penguin Guy said:**
> 
This is not a diversion, I just want to waste hackers' time

Sounds like you just found a use for a honeypot!

---

### Post by Penguin Guy on 2010-05-12
> **cdenley said:**
> I could be wrong, but I think a honeypot can be any server or service meant to be perceived as a vulnerability without actually being one. I think a service which appears to allow authentications but actually doesn't would qualify.
Most honeypots allow the attacker to log into a fake system, although my system may technically be a honeypot, it is unusual in many ways.

---

### Post by renkinjutsu on 2010-05-12
You can set your SSH server to only accept keys, and then go ahead and delete all the "authorized_keys" files on your machine. :P


They'll keep trying and trying with brute force but your fortress remains impenetrable!

---

### Post by cdenley on 2010-05-12
> **renkinjutsu said:**
> You can set your SSH server to only accept keys, and then go ahead and delete all the "authorized_keys" files on your machine. :P


They'll keep trying and trying with brute force but your fortress remains impenetrable!

They probably wouldn't keep trying to brute force if password authentication isn't allowed, which would defeat the purpose.

---

### Post by bodhi.zazen on 2010-05-12
I have never seen brute force attempts on any ssh server configured for keys only (passwords disabled), even on the dreaded port 22.

They come, they scan, they leave.

---

### Post by noway2 on 2010-05-12
Every once in a while, perhaps every couple of months, I have seen what appears to be an attempt to dictionary my key-only server.  I figure it is an automated script that is doing it.  What happens is that I get about 3 Ossec notifications about rapid fire invalid login attempts before they get cutoff.  Normally it only takes a couple of password attempts before the server responds by blocking them, but occasionally they do something that manages to get about 15 attempts in a few seconds.

---

### Post by almahtar on 2010-05-12
cdenley - I didn't know that! Thanks, your idea is much better.

On a side note if you're going to be setting up something like this Penguin Guy, you may want to also set up Snort to let you know when someone has tried to fuzz your SSH.  It's gratifying sometimes looking in your logs and seeing millions of futile attempts. :)

---

### Post by Penguin Guy on 2010-05-13
> **almahtar said:**
> On a side note if you're going to be setting up something like this Penguin Guy, you may want to also set up Snort to let you know when someone has tried to fuzz your SSH.  It's gratifying sometimes looking in your logs and seeing millions of futile attempts. :)
Snort is way too complicated for something small like this, I've wrote a script that should extract information about login failures.

---

