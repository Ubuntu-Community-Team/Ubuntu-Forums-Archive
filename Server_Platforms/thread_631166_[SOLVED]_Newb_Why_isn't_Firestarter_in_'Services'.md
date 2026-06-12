---
title: "[SOLVED] Newb: Why isn't Firestarter in 'Services'?"
date: 2007-12-04
forum: Server Platforms
---

### Post by Smartin on 2007-12-04
Hi,

I'm running Dapper Server 6.06 LTS with the Ubuntu desktop.

How do I get Firestarter to *always* run on startup? It's not in the 'Services' list.

I looked at Prefs>Sessions>Startup items but
A) I couldn't understand what startup command to use (sudo Firestarter?)
and
B) It seems an odd place to go to get Firestarter to run at startup.

What am I missing, apart from a brain...?

Thanks

Simon

---

### Post by scxtt on 2007-12-04
it's not a "service" in that sense (like apache or sshd) ... "firestarted" is just a GUI frontend to iptables, so even if you don't see its icon in your taskbar, chances are your iptables has been config'd to use the rules firestarter created.

i'm sure you can add firestarter to the session startup, probably as easily as supplying the full-path to it ...

---

### Post by vishzilla on 2007-12-04
Firestarter is only a GUI, the real firewall is the Linux IP tables. Ubuntu has the IP tables enabled out of the box. Firestarter is only an apparatus to configure the IP tables. You can check if your Firewall is working at this website [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) Run the common ports test. If it shows as 'Stealth' then the firewall works. Cheers!

---

### Post by Luke111 on 2007-12-04
I've wondered whether the firewall is actually running also. Since there is nothing to be seen without running firestarter, that is. On grc.com I have three ports showing as stealth with the rest showing closed. At least they don't show as open.

---

### Post by scxtt on 2007-12-04
**sudo iptables -L** will show you the current rules in effect.

---

### Post by vishzilla on 2007-12-04
> **Luke111 said:**
> I've wondered whether the firewall is actually running also. Since there is nothing to be seen without running firestarter, that is. On grc.com I have three ports showing as stealth with the rest showing closed. At least they don't show as open.

Ubuntu can do away with Firestarter, its an added advantage to play it in our hands.

---

### Post by Brazen on 2007-12-04
> **scxtt said:**
> **sudo iptables -L** will show you the current rules in effect.

yeah, best thing to do is run "sudo iptables -L" and see if your firewall rules are being applied on startup.  Iptables is running all the time, no matter what, but whether or not it is loading the rules is another issue.  I don't use Firestarter, so I don't know if it saves the rules so iptables will load them on startup or not.  I use Webmin and it is an extra button click to save the rules to load at startup.

---

### Post by Smartin on 2007-12-04
Guys,

Thanks very much for your replies.

In a nutshell, the firewall is running all the time regardless. Firestarter is just a convenient way to control it. To check which rules are running do 'sudo iptables -L'.

Correct me if I have go this wrong.

Thanks again.

Simon

---

