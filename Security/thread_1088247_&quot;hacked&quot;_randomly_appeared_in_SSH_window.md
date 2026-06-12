---
title: "&quot;hacked&quot; randomly appeared in SSH window."
date: 2009-03-05
forum: Security
---

### Post by Gary13579 on 2009-03-05
I was SSH'd into my desktop from my notebook, both of which are running 8.10. The window was minimised, and when I maximised it, the word "hacked" was written in the terminal, like such:

> gary@snuggles:~$ hacked

I KNOW I did not type this, and can't think of anything that would cause this other than the box getting compromised. I'm using a hardware router running DD-WRT with all ports closed. I haven't installed much outside of the official repos, so I'm kinda stumped.

---

### Post by bodhi.zazen on 2009-03-05
Output of who ?

Check your logs.

Running VNC ?

Scan your IP (router) and box for open ports.

---

### Post by yther on 2009-03-05
I can think of two possibilities.

One, some person or script compromised your system and boasted of it by putting that there.  It's as if you had typed it, or you were in a shared **screen** session with someone else who typed it.

Two, somehow the word "hacked" got on your clipboard and was pasted into that window by an accidental middle-click, and you didn't notice until later.

Of course #1 is the scarier possibility, so naturally you'll want to check your system as thoroughly as you can.  :(

---

### Post by Gary13579 on 2009-03-05
> **bodhi.zazen said:**
> Output of who ?

Check your logs.

Running VNC ?

Scan your IP (router) and box for open ports.

PORT   STATE SERVICE
23/tcp open  telnet
53/tcp open  domain

Telnet is DD-WRT admin panel, which has a very secure password set. DNS is a server built into the router, which I could disable but I don't think they could do much through it.

On the box I was SSHing into, 

22/tcp    open  ssh
80/tcp    open  http
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
31416/tcp open  boinc

---

### Post by bodhi.zazen on 2009-03-05
Nothing much there.

What is 31416/tcp open  boinc ?

Logs ?

---

### Post by Gary13579 on 2009-03-05
> **bodhi.zazen said:**
> Nothing much there.

What is 31416/tcp open  boinc ?

Logs ?

[http://boinc.berkeley.edu/](http://boinc.berkeley.edu/)

Basically, a manager for distributed computing programs. The service listens on a port for the frontend to connect to it (it has a backend which the GUI connects to).

What logs should I check?

---

### Post by scottuss on 2009-03-05
Port 22 isn't open on the router. Could someone else on your local network be playing a prank / joke? Have you at any point copied and pasted the word hacked or viewed anything with that word in? I've made that mistake before, where words have been pasted that I didn't mean to. I agree with the guy who suggested that as a possibility.

If someone had really "hacked" you, there would probably have been commands run in order to maintain access / snoop around etc etc.

---

### Post by Gary13579 on 2009-03-05
> **scottuss said:**
> Port 22 isn't open on the router. Could someone else on your local network be playing a prank / joke? Have you at any point copied and pasted the word hacked or viewed anything with that word in? I've made that mistake before, where words have been pasted that I didn't mean to. I agree with the guy who suggested that as a possibility.

If someone had really "hacked" you, there would probably have been commands run in order to maintain access / snoop around etc etc.

I'm aware port 22 isn't open, for obvious reasons. When I need to SSH in from outside of the network I use a non standard port which my router forwards to my box on port 22. I disable it whenever I know I won't be using it (if I end up really needing it, that's why telnet is running on my router. I can enable it through there.)

The only other person on my network at the moment is my GF who is on the box I was SSHing into, but she barely knows what a terminal is, let alone SSH.

I've been looking through all my IRC logs/web pages and haven't found the word "hacked" yet. It's a possibility that I did copy/paste it, which puts my mind a bit at ease, but I really can't find the word.

---

### Post by HermanAB on 2009-03-05
Why are you running telnet if you have ssh?  That is most likely the source of the problem.  No matter how secure your password, with telnet the password is sent in clear over the net.

Cheers,

Herman

---

### Post by Mud.Knee.Havoc on 2009-03-05
> **HermanAB said:**
> Why are you running telnet if you have ssh?  That is most likely the source of the problem.  No matter how secure your password, with telnet the password is sent in clear over the net.

Cheers,

Herman

I agree with Herman.  If you've been using telnet, I'd stop immediately (that's why you've got ssh), change my passwords, and start doing damage control.

---

### Post by Gary13579 on 2009-03-05
> **HermanAB said:**
> Why are you running telnet if you have ssh?  That is most likely the source of the problem.  No matter how secure your password, with telnet the password is sent in clear over the net.

Cheers,

Herman

Telnet is running on the ROUTER, not my PC.

Unfortunately I have a newer version of the Linksys WRT54G, which is limited to 2mb of storage. DD-WRT had to cut out sshd to meet the 2mb requirement. (I'll never understand how Linksys puts out NEWER routers that have much lower specs, but charge more money...).

---

### Post by wirelessmonkey on 2009-03-06
Telneting to your router from outside is a huge risk.  Better to turn it off, and not remote administrate, unless you can set ACLs on your router.

---

### Post by scottuss on 2009-03-06
> **wirelessmonkey said:**
> Telneting to your router from outside is a huge risk.  Better to turn it off, and not remote administrate, unless you can set ACLs on your router.

I agree. I forgot to mention that in my previous post.

---

