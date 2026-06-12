---
title: "Simple one step security scanner for Ubuntu?"
date: 2012-01-07
forum: Security
---

### Post by mfpompadour on 2012-01-07
I recently purchased an Ubuntu VPS, and it came preinstalled with a lot of services I don't need (portmapd, sendmail, etc.).

Is this a simple one-step security scanning script for Ubuntu? I would like something that scans the system and makes a handful of security recommendations. This would be much easier than scanning the system manually.

---

### Post by HermanAB on 2012-01-07
Uhmmm, typing 'ps -e' then Googling the things you don't recognise is difficult?

---

### Post by Dangertux on 2012-01-07
There really isn't anything like that... Mostly for the reason that linux kind of expects you to know what you're doing, particularly if you're running a server.

Also... I wouldn't recommend disabling portmapd, it won't break anything but could cause issues with your VPS provider ;-)

---

### Post by mfpompadour on 2012-01-08
> **Dangertux said:**
> Also... I wouldn't recommend disabling portmapd, it won't break anything but could cause issues with your VPS provider ;-)

Why?

---

### Post by mfpompadour on 2012-01-08
> **HermanAB said:**
> Uhmmm, typing 'ps -e' then Googling the things you don't recognise is difficult?

This is time consuming, especially if you have multiple VPS providers each of whom like to install different default crap.

Plus, it gives no easily actionable proactive recommendations for improving security, like installing denyhosts or apparmor.

---

### Post by HermanAB on 2012-01-08
You are using Linux.  As opposed to that other OS, you don't need to add band-aids to improve security.  All you need to do to improve security is disable services you don't need to run.

---

### Post by Dangertux on 2012-01-08
> **mfpompadour said:**
> Why?

Some VPS providers use something like HA orother heartbeat systems that poll rpc portmap to determine if your system is functioning properly, and it could lead to unnecessary VM migration and or reboots to attempt to "fix" what they perceive to be a problem.

This is not the rule, but still something to consider.

Also if  you're just trying to determine what services are externally available on your system what's wrong with

```

sudo nmap -T4 -v -sS -sV -O -PN serverip

```

---

