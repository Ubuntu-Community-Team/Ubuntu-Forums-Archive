---
title: "UFW log alerts"
date: 2011-04-07
forum: Security
---

### Post by Maintech on 2011-04-07
I have enabled UFW and removed Firestarter because I found several IP addresses that were having my computer send information to them. These addresses were not legitimate. I found firestarter would not block sending info to these addresses even though I manually entered the rule to block outgoing to that IP address. That worried me so I changed the IPTable interface and started with new IPTables.

My question is: Does UFW have a log reader/analyzer that can highlight the log or send alerts for attempted accesses? Or if my computer attempts to send info to an outside source.....especially if that IP has been manually blocked? That was the thing about firestarter that I liked (when it worked correctly). It had alerts that informed me of the IP and the protocol. I'm not sure why it stopped working correctly.

---

### Post by oklokl on 2011-04-08
[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)
Recommended

---

### Post by bodhi.zazen on 2011-04-08
Watching your firewall for dropped packets , or what you are calling and alert, is, IMO, an exercise in futility.

Dropped packets are exactly that, they are an annoyance, but not a threat.

If you are interested use something like snort. Snort will watch your network traffic and, based on the snort rule set, alert you to the activity that really is a threat. Be warned, snort is a bit complex and tends to give some false positives.

Alternates would be psad (psad will automate the process and block bad behaving IP addresses) or perhaps denyhosts or fail2ban.

If all that sounds too complex, 99.99 % of the time all you really need to do is:

```
sudo ufw enable
```

So it depends how much time you want to spend learning about security.

---

### Post by Maintech on 2011-04-08
> **bodhi.zazen said:**
> Watching your firewall for dropped packets , or what you are calling and alert, is, IMO, an exercise in futility.

Dropped packets are exactly that, they are an annoyance, but not a threat.

If you are interested use something like snort. Snort will watch your network traffic and, based on the snort rule set, alert you to the activity that really is a threat. Be warned, snort is a bit complex and tends to give some false positives.

Alternates would be psad (psad will automate the process and block bad behaving IP addresses) or perhaps denyhosts or fail2ban.

If all that sounds too complex, 99.99 % of the time all you really need to do is:

```
sudo ufw enable
```

So it depends how much time you want to spend learning about security.

I thank you so much for that wonderful reply. Snort is a bit much for a home computer and has it's own security issues according to the ubuntu forums. PSAD isn't bad and perhaps I will but again, but it presents issues of security too. I might populate denyhosts. I've never tried fail2ban. I thought of using logwatch but I don't like exim installed. **_[COLOR="Red"]I DO HAVE UFW ENABLED.[/COLOR]_** It is a bit late for all that. My system was compromised. I backed up important files and wiped my disk and re-installed. The point is that firestarter and GUFW all are just frontends for the iptables. I have had a firewall since installation. I just need to harden things a bit more on the new install and the firewall logs show when someone is either trying to compromise my system or that it has already been compromised (as was my case). All I was asking for was a nice program to read my ufw log files and extract only the ones that were suspicious. I did try IPBlocker and there were several on the list that my computer was trying to connect to. It was helpful by marking them advance instead of me having to check individually. I could not stop my computer from finding a way to connect to them. Chkrootkit and RKHunter could find nothing. I'm not an expert but neither am I new at this. However, there are new programs being written for Ubuntu almost daily and this was what I was inquiring about......new log analyzing programs......hopefully ones without security issues of their own. Meanwhile, I will continue to harden my system by setting policies and encrypting my /home directory.

---

### Post by bodhi.zazen on 2011-04-08
I understand, and I understand the complexities, but again, for what you are wanting, snort is IMO the best tool.

---

### Post by oklokl on 2011-04-09
Maintech Answer
 Sympathetic

---

