---
title: "What firewall do you use?"
date: 2009-01-04
forum: Security
---

### Post by hyperyoda on 2009-01-04
I use iptables.

Zach

---

### Post by Vantrax on 2009-01-04
Built into ubuntu is ufw which is a simple but effective firewall, to enable it with defaults turned on just run sudo ufw enable. To learn more head to the stickies, and do man ufw.

Good luck

---

### Post by tuxxy on 2009-01-04
You shouldnt need to do much configuration unless you plan to run some specific services or apps and if you prefer a GUI to configure it try gufw

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by bodhi.zazen on 2009-01-05
As has been pointed out in other threads, everyone uses iptables. Do not confuse the configuration tools (ufw / firestarter / shorewall / guarddog / etc) as the firewall itself.

With that said, I would guess most people are using their router as a firewall.

---

### Post by hyper_ch on 2009-01-05
> **bodhi.zazen said:**
> with that said, i would guess most people are using their router as a firewall.
+1

---

### Post by HermanAB on 2009-01-05
"I use iptables."

Uhmmm... *Everybody* uses iptables.

---

### Post by Dave_Connor on 2009-01-05
Isn't ufw just a front end to make iptables quicker to use ?

---

### Post by cariboo on 2009-01-05
I use my linksys router, I haven't change the default iptables configuration.

Jim

---

### Post by theozzlives on 2009-01-05
> **bodhi.zazen said:**
> As has been pointed out in other threads, everyone uses iptables. Do not confuse the configuration tools (ufw / firestarter / shorewall / guarddog / etc) as the firewall itself.

With that said, I would guess most people are using their router as a firewall.

I got a bunch of stuff for Windows, but my router for Linux.

---

### Post by albinootje on 2009-01-05
> **bodhi.zazen said:**
> As has been pointed out in other threads, everyone uses iptables. Do not confuse the configuration tools (ufw / firestarter / shorewall / guarddog / etc) as the firewall itself.

With that said, I would guess most people are using their router as a firewall.

Then I suggest to also tell people that k3b is not burning software, it's only a GUI wrapper for wodim, mkisofs and growisofs. ;-)

---

### Post by ibutho on 2009-01-05
I use my router, but also run a firewall locally on each machine. On Ubuntu and Debian, I prefer using Shorewall to configure the firewall rules.

---

### Post by CoolHand on 2009-01-05
Obviously most systems are using iptables.  For the front end I have been using Firestarter for the last year or two.  I like the simplicity and that I can run the gui in the system tray and it will alert me when it blocks something.  On my server I installed ipkungfu as it is just a command line iptables config tool.  So far so good with it.

---

### Post by hyper_ch on 2009-01-05
constantly running firestarter is a security risk.

---

### Post by Chayak on 2009-01-07
Cisco ASA5505 Sec Plus, Vyatta vc5 beta load on my router, and yes iptables on my desktop and laptop.

---

### Post by albinootje on 2009-01-07
> **hyper_ch said:**
> constantly running firestarter is a security risk.

Why so ?

---

### Post by hyper_ch on 2009-01-07
because it runs as root and is not needed and hasn't been updated since 2005

---

### Post by joshh88 on 2009-01-07
Isn't that why you use firestarter to configure iptables and then disable firestarter itself. Not running it everytime you log on, just when you need to configure.

---

