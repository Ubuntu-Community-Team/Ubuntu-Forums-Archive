---
title: "Security on Ubuntu 10.04-Lucid Lynx (LTS, 32 Bit Desktop)"
date: 2011-10-20
forum: Security
---

### Post by kerimatasoy on 2011-10-20
Hi guys...
I just would like to ask and learn about how to setup a secured environment on Ubuntu 10.04 32 Bit Desktop version. To tell the truth, I'm totally a newbie on Ubuntu...so, as you can understand that, I just couldn't figure out some basic concepts and features of Ubuntu and Linux systems... It would be so appreciated if you could help me some about on this...
I'd like to install some security features on my new Ubuntu system that I can surf, read, download or get other lots of benefits on Internet more securely... So far, I've noticed just a little bit about UFW and GUFW... How can I establish a security package or module to do so...?
Thank you so much...

---

### Post by blackbird34 on 2011-10-20
A new install can be used straight away, any normal user has no need for antivirus firewall or anything. If you want ROCK SOLID, nuclear blast-proof security, try this: 

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
by bodhi.zazen,
Ubuntu guru and forums admin

---

### Post by kerimatasoy on 2011-10-20
Thank you very much. I'm checking that title up right now...

---

### Post by Dangertux on 2011-10-20
The thread you linked is a great place to start. Though I wouldn't say it's nuclear blast proof ;-)

Start from the ground up. First secure yourself. Use common sense when doing anything.  

Otherwise the recommendations are pretty standard for a desktop install.

- Strong outbound firewall policies (as opposed to just a default drop all inbound policy)
- Use NoScript/NotScript while browsing
- Confine as many applications as you can stand to make profiles for with apparmor (your browser being the most important)
- Lock down your home directory 
- Use strong passwords
- Don't use weak services (like VNC)

THat should get you started , most of those topics if not all I believe are referenced in the thread you were already linked.

---

### Post by howefield on 2011-10-20
Thread moved to the "*Security Discussions*" forum.

---

