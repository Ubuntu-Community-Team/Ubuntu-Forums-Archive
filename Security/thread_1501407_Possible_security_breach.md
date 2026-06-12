---
title: "Possible security breach"
date: 2010-06-04
forum: Security
---

### Post by Jimtuv on 2010-06-04
System specs Ubuntu 10.04 on pentium 4 ht. 2.5g ram wireless netgear router Samba share

I had something odd happen yesterday. My printer started on its own and printed out a sheet of colors. I immediately shut off the router and changed the wireless passphrase. I also changed the password of everyone that was on at the time. I also ran virus checks as well.

What should I do next?

---

### Post by sgosnell on 2010-06-04
What security are you running on the router?  WEP?  WPA2?  WEP is almost as weak as no security at all.  Script kiddies running aircrack can crack a WEP password in minutes.  You can also disable the SSD broadcast and use MAC address filtering.  These certainly aren't foolproof, but can discourage casual intruders.  It's also possible that one of the users on your network printed a test page somehow.

---

### Post by Jimtuv on 2010-06-04
I am using WPA2 with a 63 character passphrase. I am certain no one did a test page print. I was the only one on the network. I checked the router log and it said

[DoS attack: ACK Scan] attack packets in last 20 sec from ip
[205.188.159.89], Thursday, Jun 03,2010 15:16:19
[DoS attack: ACK Scan] attack packets in last 20 sec from ip
[205.188.0.55],  Thursday, Jun 03,2010 15:17:42

I checked these and it says the address is from aol.com so I sent them an abuse notification and blocked the above addresses in the router. I am thinking it may have come from firefox as I was on firefox at the time.

---

### Post by tgalati4 on 2010-06-04
Do you have port 631 open on your router?  If so, it's possible a random character stream triggered a test page to print.

---

### Post by Jimtuv on 2010-06-04
> **tgalati4 said:**
> Do you have port 631 open on your router?  If so, it's possible a random character stream triggered a test page to print.

how do I check that??

---

### Post by sgosnell on 2010-06-04
Open the router with Firefox and see what ports are forwarded.  Port forwarding is usually done for games, and that can result in security problems.  I have two ports forwarded to my server for ftp and ssh, nothing else, and they go only to my file server.  To be really secure, you should have all ports closed, and then nothing should be able to get to your network.

---

### Post by Jimtuv on 2010-06-04
No ports are forwarded I double checked. I still don't understand how they could have broken my passphrase it's gigantic and very random using every oddball combination of characters I could come up with. I think it must have come from the Internet. I still think it was firefox not the wireless that gave them access. I am going to set up  Apparmor for firefox to limit it ability to see my files.

---

### Post by tgalati4 on 2010-06-04
You could have also had a slight power outage causing the printer to reset and print a test page.

---

### Post by sgosnell on 2010-06-04
If you have no ports forwarded, and you're using WPA2 with a strong password, my bet is that it was a glitch of some kind inside your network, maybe in the printer.  I wouldn't worry about it.  Defecation occurs.

---

### Post by Jimtuv on 2010-06-04
I have to agree with you. I have poured over the logs and nothing odd is turning up. I even ran rkhunter and chkrootkit to make sure I had no compromises. They both show clean. So I am chalking this up to a glitch. Just a really odd one. I hardened all my directories and encrypted important folders that would hold passwords or financial data. So if anyone gets in they wont get very far. I also removed everyones sudo rights other then my admin and gave him a max length password. Don't have a clue what else could be done to protect the network. I think I have done everything possible.

---

### Post by tgalati4 on 2010-06-05
Wrap your wires with tin foil.

Make a hat as well.

Post a picture.

---

### Post by Jimtuv on 2010-06-05
> **tgalati4 said:**
> Wrap your wires with tin foil.

Make a hat as well.

Post a picture.


[IMG]http://anothershittyblogbysomedouche.files.wordpress.com/2009/06/tin-foil-hat.jpg[/IMG]

---

### Post by sgosnell on 2010-06-05
Now that is an unhappy-looking cat.  The tinfoil must be reflecting the unhappy cat thoughts back into its head.   Its human, OTOH, looks pretty normal for a cat slave.

---

### Post by tgalati4 on 2010-06-06
This thread is moving towards epic.

+1 for protection.

---

