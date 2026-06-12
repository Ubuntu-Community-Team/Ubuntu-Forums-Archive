---
title: "low intensity distributed bruteforce"
date: 2008-12-03
forum: Security
---

### Post by whoop on 2008-12-03
Has anybody noticed this on there ssh severs late lee? [http://bsdly.blogspot.com/2008/12/low-intensity-distributed-bruteforce.html](http://bsdly.blogspot.com/2008/12/low-intensity-distributed-bruteforce.html)

What are your security measures?

denyhosts or ssh with key would be the only option if you ask me. As fail2ban won't do much here.

---

### Post by The Tronyx on 2008-12-03
Pretty cool article and thanks for the link. 

You might want to check out port knocking/SPA or fwknop.  I personally have never set this up but it sounds like it could be a nice security touch and if nothing else, a cool project.

[https://help.ubuntu.com/community/SinglePacketAuthorization](https://help.ubuntu.com/community/SinglePacketAuthorization)
[http://ubuntuforums.org/showthread.php?t=812573&highlight=fwknop](http://ubuntuforums.org/showthread.php?t=812573&highlight=fwknop)

---

### Post by cdenley on 2008-12-03
> **whoop said:**
> Has anybody noticed this on there ssh severs late lee? [http://bsdly.blogspot.com/2008/12/low-intensity-distributed-bruteforce.html](http://bsdly.blogspot.com/2008/12/low-intensity-distributed-bruteforce.html)

What are your security measures?

denyhosts or ssh with key would be the only option if you ask me. As fail2ban won't do much here.

The only way to protect from those kind of attacks would be to define the hosts which are allowed to connect, or configure fail2ban to block all ssh connections when there is an unusually high number of failed authentication attempts.

If you don't know where you may be connecting from, there is no way for the server to differentiate between a legitimate authentication attempt by you and an attempt from a computer which is part of a botnet. You can probably block all traffic on port 22 except from IP's in your geographical region. That would greatly reduce any attack, but might be a problem if you go on vacation or try using a proxy server.

---

### Post by HermanAB on 2008-12-03
You can simply use a one liner in iptables to rate limit new connections and thereby make any brute force attack infeasible.

I suspect that the originator of that article has such a rate limiter in his firewall and that is why the attacks seem slow to him!

---

### Post by stmurray on 2008-12-03
Another simple configuration that helps is to pick a random high port for ssh.  Now, please don't say that this is false security or "security through obscurity". Yes, a port scan will show the ssl running on the port and a motivated attacker would do the port scan first.  But most of these bot type attacks don't bother with the port scan.  They randomly try port 22.  

I run snort and OSSEC on the ssh server.  I have had this set up for about nine months never had a "user authentication failed" (that wasn't me mistyping my password ;)) whereas I have had 547 distinct IP addresses attempt to connect to port 22.  So, for the little effort that is involved in setting up ssh on a random high port, the fact that is makes me less of a target to the bot attacks is well worth it.

(BTW, I make sure I use a port that is not in nmap's list of known ports.  That way, someone who does an nmap scan without specifying specific ports will not scan my ssh port.  nmap scans it's list of known port NOT all ports, unless you tell it otherwise.  Again, not perfect but may keep a script-kiddie or two at bay...)

---

### Post by bodhi.zazen on 2008-12-03
Follow this guide :

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Basically :

1. Use keys.

2. Change the port.

3. Disallow root logins.

4. Use AllowUsers and AllowGroups (make a new group for ssh access like "dlsfjk").

These 4 simple steps will stop almost all attempts on your ssh server.

You can augment this with denyhosts, an iptables rule, or OSSEC.

---

### Post by hyper_ch on 2008-12-04
> **stmurray said:**
> Another simple configuration that helps is to pick a random high port for ssh.  Now, please don't say that this is false security or "security through obscurity". Yes, a port scan will show the ssl running on the port and a motivated attacker would do the port scan first.  But most of these bot type attacks don't bother with the port scan.  They randomly try port 22.
Problem is if it's low-level brute-forcing then they are not script-kiddies and will not just random target someone but first find out what port it runs on. IMHO it's then useless.

---

