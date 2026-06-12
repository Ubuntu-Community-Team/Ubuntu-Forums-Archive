---
title: "Computer makes https connections after mail pull"
date: 2011-09-16
forum: Security
---

### Post by SparTacux on 2011-09-16
I have a separate user account titled mymail or something similar. It is used only for sending/receiving mail and storing work related documents. A few times over the last year or so I have done a mail pull using Evolution from my mail server and immediately I have had outgoing https connections to a number of sites including Ebay and Amazon.

The incoming mail is from work and I am using Evolution. I was using  POP3 and SMTP. Evolution was set-up to read plain text only and not view HTML documents. This happens when I first turn on my computer and log on to my mail account and do a send/receive. My computer does the usual DNS then NTP to get time then when I do a send receive the DNS and POP3 packets go out and DNS / SMTP then ' BANG' -- HTTPS packets to several sites. One thing to note here is that I do not use firefox or any browser from this user account nor under these circumstances have I used the browser for another user account before these events happen.

Rereading the email in my inbox does not cause any https connections and seems to only happen when I do a pull. It's possible something else causes this maybe on some sort of time setting such as a cron job but I have not set up any cron jobs to take place.

Baffled !

---

### Post by SparTacux on 2011-09-16
oh - forgot to mention - I wasn't using Apparmor - yeah I know !!!

---

### Post by emiller12345 on 2011-09-16
does the ip.addr of the encrypted data correspond to any of the dns queries? If so, what url's are they communicating with?

---

### Post by SparTacux on 2011-09-17
> **emiller12345 said:**
> does the ip.addr of the encrypted data correspond to any of the dns queries? If so, what url's are they communicating with?

I'm not too sure what you are asking here emiller. My modem actually blocked the the outgoing traffic on these occasions as I tend to put a squeeze on ongoing traffic on certain IP addresses - so no worries that any harm was caused. Even my POP and SMTP only allow outgoing traffic to my mail server and will block any other POP/SMTP to other mail servers. I did a whois on the IP's that were blocked and they returned Amazon and Ebay. I've done several re-installls since these events but would still like to get to the bottom of it. I've probably still got the modem logs showing some of this stuff but it would be a big exercise in trying to find it.

One thing I will note - is that even though I didn''t use a browser for this desktop user - I did use rythmbox to access an online radio station. However - on some of the occasions when these events happened I wasn't using rythmbox. I turned my modem on, turned my PC on, logged on, then did a mail pull.

---

### Post by SparTacux on 2011-09-18
Any possibility of a DNS vulnerability in Evolution? Is Thunderbird considered a more reliable alternative?

---

