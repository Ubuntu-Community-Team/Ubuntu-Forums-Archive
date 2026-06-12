---
title: "Ubuntu 12.04.4 LTS Server - Security Question..."
date: 2014-06-16
forum: Security
---

### Post by John_G._Asmussen on 2014-06-16
Hello everyone,

I have a security question with regard to my home server and the number of failed SSH login attempts. What concerns me the most is that the fail2ban log files show a lot of unauthorized attempts to login. The suspect IP addresses appear to be rotating through sequential numbers - after one IP gets banned the next sequential IP tries again unsucessfully. Even though I am not aware of any successful intrusions to date I am considering blocking SSH login from all but a few IP addresses. Is this necessary or do I need to put away the tinfoil? Its not like I have intellectual property, trade secrets for my business, or other "valuable" data stored on this machine -BUT- I don't want to lose any of my personal files or have my system compromised either. What is your suggestion?

Thank you in advance,

John


For those that always want to know more specifics....I have a very basic server installed with only a few services running. I also followed this  step-by-step guide, [How to Secure an Ubuntu Server]("http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics").  I have SSH configured to use public/private key login and disabled root user logins. I also have fail2ban, UFW, iptables, and other security  programs installed and configured properly - and they are working fine. I  regulary install updates, check the fail2ban logs and other system log  files for suspicious activity, etc. etc. etc....

---

### Post by untrustytahr on 2014-06-17
Welcome to the forum.

It sounds like your system is reasonably secure if you've implemented the all the recommendations on that guide.  I wouldn't be overly concerned with the login attempts as they are the cost of being on the internet.  Of course, only you can evaluate the what the impact of a data breach would be to you in your circumstance.  A few points...

1) Disable Password Authentication

You said you setup ssh key logons and disabled root logons but you didn't mention if you disabled pw authentications altogether.  The downside of doing this is you can only logon from a machine that has your private key on it.  This means you wouldn't be able to logon from say, a friend's computer if you needed a file.

2) LImit SSH logins by time of day

You said this is a home server so you probably have a SOHO router/firewall.  Most give the ability to schedule when rules will be in effect so you could set up your forwarding rule to be active only during the hours that you (or whoever uses your server) would be awake.  If you router doesn't have that ability, you could achieve similar functionality by using a bash script and cron on the server. 

3) If you really do wear a tin-foil hat, you could always encrypt your data with GnuPG before sending it to the server.  If you did it asymmetrically, then even if someone did get the files somehow, they would still need the key on your computer to decrypt it.  The downside to this is... well, people can't figure out GnuPG to send an email let alone regular files/folders and who really wants to do it each time they upload/download a file to a server.

IMO, suggestion 1 is reasonable.  The other two are for you if you are a 'worrier'.  As I previously stated, your system is reasonably secure.  Hope it helps.

---

### Post by Gyokuro on 2014-06-17
Untrustytahr mentioning some valid points and concerning fail2ban I would change in 

[default]
bantime  = 3600
maxretry = 2

and as you mentioned ufw I would change in before/before6.rules all
# ok icmp codes to

-DROP

however you will be unable to ping your server (but as you know your system why should somebody else to do it - there are some corner cases why some of the settings should be enabled)

---

### Post by John_G._Asmussen on 2014-06-17
untrustytahr - Thank you for your reply!  I will check to make sure that password authentication is disabled - but I think I already did that. Also, I will look into setting up SSH logins by time of day - I hadn't considered this. I'm really not a 'worrier' but I really like the idea of not being owned or compromised. Thank you again for all of your help and I really like this forum - Lots of friendly people with good advice!

---

