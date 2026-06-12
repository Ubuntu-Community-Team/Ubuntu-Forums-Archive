---
title: "Security by obscurity and SSH"
date: 2010-02-08
forum: Security
---

### Post by Vunutus on 2010-02-08
Assuming the SSH server is configured to be as secure as possible, is it really worth it to use an obscure port for SSH?

I ask because I've noticed that on my home machine, I have hundreds of hits trying to guess my username with SSH running on port 22. At work, our SSH runs on an obscure high port (actually it's the numbers you would use to phone keypad-dial our acronym so I can remember it easily) and I have yet to see any malicious hits on it.

Since the server is configured to be as secure as possible anyway, is it really worth the extra hassle of specifying port numbers every time I want to connect or do any file transfers?

---

### Post by FuturePilot on 2010-02-08
My .02

Using a different port does not make it any more secure, however it will eliminate all the bot/script kiddie noise potentially exposing a legit attempt to crack the server. If someone was really trying to crack the server on the default port it would be obscured by a bunch of other noise. Whereas with all the other noise eliminated, it would be easy to spot something going on.

---

### Post by movieman on 2010-02-08
> **Vunutus said:**
> Assuming the SSH server is configured to be as secure as possible, is it really worth it to use an obscure port for SSH?

Yes. At the least, you're wasting bandwidth dealing with script kiddies continually trying to hack your server... at worst, if an ssh exploit was found, systems running ssh on the default port will be attacked much faster than systems with ssh on a random port.

I don't see any reason to run an externally-visible ssh server on the default port. You can always configure your router to forward port 19353 (or whatever you pick) to port 22 on your server so you don't need to change the internal port numbers.

---

### Post by OliW on 2010-02-08
High port + fail2ban

---

