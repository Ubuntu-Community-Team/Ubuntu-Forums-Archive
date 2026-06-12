---
title: "How to start the firewall with gufw"
date: 2012-06-29
forum: Security
---

### Post by AlexBooton on 2012-06-29
I'm a little confused.  I added some rules to gufw but deliberately left one out (tcp 5901 for vncserver).  

The gui indicated the firewall was on.

I restarted the system and the firewall. When restarted, I was able to get to the vnc server on 5901???

Isn't gufw supposed to feed rules to iptables and make them permanent?

Thanks for the clarification,

AB

---

### Post by rai4shu2 on 2012-06-30
You can restart your system or not. It doesn't matter. The firewall is there because it's built in to the kernel. I'm guessing that when you "reset" your firewall, you also reset your ufw rules.

See [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by uRock on 2012-06-30
Moved to *Security Discussions*.

---

### Post by SparTacux on 2012-06-30
The default  rules for GUFW are DENY all incoming and ALLOW all outgoing traffic. Adding extra rules you can open ports to allow incoming traffic on various ports such as port 631 to allow IPP printer protocol to that machine. If the default outgoing rule is to ALLOW all outgoing traffic then you need to add extra rules to block outgoing traffic on the ports you want blocking.

You can change the default rules to a more restrictive set-up by setting GUFW to DENY all incoming traffic and DENY all outgoing traffic. Then start adding rules to open the ports you want opening such as DNS, HTTP, HTTPS, NTP, etc.

You might want to give more info on what rules you added and take note of the order you added the rules. The rules work from top to bottom. If the top rule says ALLOW all traffic then any further rules you add will be useless.

---

### Post by darkod on 2012-06-30
Also, explain little bit with details are you talking about the firewall on your desktop machine, or on some server (the machine that has vnc server running).

As already mentioned, the default is incoming DENY and outgoing ALLOW. Also, by default the traffic (connections) that originated from the machine in question is allowed back in even without particular rule in the firewall. This is because by default there are rules allowing back ESTABLISHED and RELATED traffic.

---

### Post by AlexBooton on 2012-06-30
Thank you all for your responses.

I'm going to do a bit more testing.

Thanks,

AB

P.S. I have to say I'm not crazy about gufw.  The interface is rather rough.  There doesn't appear to be a way to edit a rule once entered.  There is no ability to save a comment along with a rule.  And considering that the rules are followed in the order entered, shouldn't there be a way to reorder them?

It's really a shame that firestarter has been abandoned.  It did everything gufw does and more.  The only thing that seems to be missing from firestarter is IPv6 compatibility.


AB

---

### Post by darkod on 2012-06-30
I don't know how much you depend on the GUI, but you can control the firewall (ufw) with the command line also. GUFW is only a GUI for ufw anyway.

You can use ufw CLI commands or even better, enter rules in /etc/ufw/before.rules. If you enter them in the before.rules file then you can easily control in which order they are, and enter comments about each rule.

---

### Post by AlexBooton on 2012-06-30
> **darkod said:**
> I don't know how much you depend on the GUI, but you can control the firewall (ufw) with the command line also. GUFW is only a GUI for ufw anyway.

You can use ufw CLI commands or even better, enter rules in /etc/ufw/before.rules. If you enter them in the before.rules file then you can easily control in which order they are, and enter comments about each rule.


Sadly I depend heavily on the gui.  I'm not a console guru.

AB

---

### Post by SparTacux on 2012-06-30
I started off using Firestarter. The major problem I had with it is that people are encouraged to have it run all the time running as a sudo user which has to be a major security risk.   GUFW has some restrictions as you mentioned but it's not bad for a beginner's use. I still use it even though I should be moving on to UFW alone or even using IPTABLES.

---

### Post by AlexBooton on 2012-06-30
> **SparTacux said:**
> I started off using Firestarter. The major problem I had with it is that people are encouraged to have it run all the time running as a sudo user which has to be a major security risk.   GUFW has some restrictions as you mentioned but it's not bad for a beginner's use. I still use it even though I should be moving on to UFW alone or even using IPTABLES.

Hi,

I don't know where "people are encouraged to have it run all the time" comes from.

I've run FS for years and never kept it running all the time or got the impression that it should have been.  

Like gfw, once it sets up the rules it is no longer needed.  It can be run for the purpose of watching the log; but that's not necessary.

AB

---

### Post by cariboo on 2012-07-01
> **AlexBooton said:**
> Hi,

I don't know where "people are encouraged to have it run all the time" comes from.

I've run FS for years and never kept it running all the time or got the impression that it should have been.  

Like gfw, once it sets up the rules it is no longer needed.  It can be run for the purpose of watching the log; but that's not necessary.

AB

To answer your question, many ex-windows user have found that you can monitor connection while running Firestarter, although it has to be run as root in order to do so. This  info used to be readily available from almost any google search on monitoring network connections.

---

