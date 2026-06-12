---
title: "Gufw firewall connectivity help - firewall stops internet."
date: 2009-04-09
forum: Security
---

### Post by polkadotteapot on 2009-04-09
Hello,

I'd like to have my firewall up via Gufw, it has no problems with allowing the ports for torrents, but when on I can't browse the web in firefox. I allowed my IP address to no avail. What else would I need to do?

Is there something I've missed? I'm running 8.10 and tried to see if firefox needed a port freeing but couldn't find anything. I've had a look on the forums ans in the community documentation but can't find anything like this.

I use things online which I really need to be secure for.

---

### Post by bertolo on 2009-04-09
> **polkadotteapot said:**
> Hello,

I'd like to have my firewall up via Gufw, it has no problems with allowing the ports for torrents, but when on I can't browse the web in firefox. I allowed my IP address to no avail. What else would I need to do?

Is there something I've missed? I'm running 8.10 and tried to see if firefox needed a port freeing but couldn't find anything. I've had a look on the forums ans in the community documentation but can't find anything like this.

I use things online which I really need to be secure for.

just a little question. do you really need the firewall ?
firewall don't do any diference for a average user.

---

### Post by FrankT-Qc on 2009-04-09
Two things : First of all, Firefox needs port 80 to access most of the web, 443 for secured sites and a few more for some exotic multimedia streaming...

Two things : First, if you're not paranoid, you might want to consider allowing any connection that's outbound...

Second, what could help me is the output of

```
sudo iptables -L -vn
```

But if you really have to be secured, you might want to keep this a secret ;-P

Besides, yes, a firewall adds some security, but for what "you do online that needs to be secured" ... the firewall itself wont do much of a difference... All it does, is KEEPING stuff from going "online" and adds no security to the transactions that you let through...

Besides, if you're uncomfortable with firewalls, you might consider using firestarter... it makes things easier... Else, if you're a firewall enthousiast, "iptables" is the way to go...

---

### Post by hyper_ch on 2009-04-10
I agree with bertolo:

What makes you think that you need to alter iptables first place?

---

### Post by bertolo on 2009-04-10
thks
virus don't fly in the air looking some pc to infect.
you only will get one if you install too much things outside the repos.
hackers don't want to waste time on linux users (most of them).
they prefer to screw microsoft over or (like conficker) they are well paid engeneers.

:P

---

### Post by Nepherte on 2009-04-10
It's kinda odd because (g)ufw can only allow/disallow incoming connections. If you can't connect to the internet, it has to do with outgoing connections which (g)ufw leaves unaltered.

---

### Post by bertolo on 2009-04-10
perfect security it's impossible, because it's a always probability question.
but if you have a key with 10 alpha numeric caracters that changes every 2 minutes...

my computer connection accepted a conection for me without my agreement and now what ?
lol.

---

### Post by polkadotteapot on 2009-04-10
> **FrankT-Qc said:**
> Two things : First of all, Firefox needs port 80 to access most of the web, 443 for secured sites and a few more for some exotic multimedia streaming...

Two things : First, if you're not paranoid, you might want to consider allowing any connection that's outbound...

Second, what could help me is the output of

```
sudo iptables -L -vn
```

But if you really have to be secured, you might want to keep this a secret ;-P

Besides, yes, a firewall adds some security, but for what "you do online that needs to be secured" ... the firewall itself wont do much of a difference... All it does, is KEEPING stuff from going "online" and adds no security to the transactions that you let through...

Besides, if you're uncomfortable with firewalls, you might consider using firestarter... it makes things easier... Else, if you're a firewall enthousiast, "iptables" is the way to go...

Tried the ports, no help. How do you copy and paste from terminal? It doesn't seem to work.

To those questioning: why is there a firewall in the first place then? I do a lot of downloading and I'm new to linux so learning by clicking things then swearing a lot. So I'm probably going to fail somewhere. Do you have any better security suggestions? I'd rather be overcautious than buggered.

I don't know what that's about but my internet works without a hitch until I enable ufw.

---

### Post by bodhi.zazen on 2009-04-10
See :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

You probably do not need a firewall .

If you wish to use a firewall you will need to learn to configure it to allow traffic you wish to pass..

Even though we have GUI tools, you still need to know how to use them.

So ...

Open the ports you wish to allow. If you do not know what that statement means I suggest you install guard dog as it has very nice built in help and read about firewalls.

If you would like assistance we need more specific information on what ports you have opened / closed and how you configured your firwall.

---

### Post by brian_p on 2009-04-10
> **polkadotteapot said:**
> 

I don't know what that's about but my internet works without a hitch until I enable ufw.

If ufw is the problem, you will make little progress in getting solutions without posting your iptables rules.

---

### Post by polkadotteapot on 2009-04-10
Hello,

Right I've had a good read and am going to give it a fest for now as I've got bigger fights with this os. I'm new to this as I should have said so learning and don't claim to know much.

I did ask how to copy and paste from terminal to show my iptables - I haven't got round to finding out if it's normal to to be ably to copy from, and also sometimes paste into terminal yet.

Thanks to those who passed on advice and useful links.

---

### Post by bodhi.zazen on 2009-04-10
Highlight the text w/ mouse

move mouse to ff

press mouse wheel down

or 

hightlight text

in the terminal menu (at the top) file - > copy

paste text into ff.

---

### Post by jay404 on 2009-04-12
is ufw better than firestarter? does it let block outgoing connections also?

---

### Post by hyper_ch on 2009-04-12
do you even need any of that?

---

### Post by bodhi.zazen on 2009-04-12
> **jay404 said:**
> is ufw better than firestarter? does it let block outgoing connections also?

"Better" is subjective. Both are GUI front ends for iptables.

---

### Post by gaiterin on 2009-04-15
> **Nepherte said:**
> It's kinda odd because (g)ufw can only allow/disallow incoming connections. If you can't connect to the internet, it has to do with outgoing connections which (g)ufw leaves unaltered.

Correct ;)

---

