---
title: "Have I been breached, or is this normal?"
date: 2009-01-11
forum: Security
---

### Post by Superdude_123 on 2009-01-11
Here's the thing. I'm running DSL on a remote box, and I wanted to install fail2ban. To do so, I needed to install python, so I found a way to install python by uploading to the box a unc (and a uci). Now I ran an install command (reminder, this is all done through terminal, thus not graphically), and then I lose all connections with the box. Since I'm running the box at a remote location, I called up, and learned that the box went in to Hault. My question is, when installing new software, is this normal that the system shuts down, and needs to be rebooted, or could it have crashed? (its only a 200 MHz) Or is it breached/hacked?

It should be noted that the passwords involve ##, letters, and characters. Minimum length of over 10 characters, root has been disabled as a SSH log in, SSHd is not on port 22, and the logs showed 0 signs of failed foreign attempts.

---

### Post by Dr Small on 2009-01-11
Sounds like a hardware problem to me.

---

### Post by Superdude_123 on 2009-01-11
Even if it said " DSL is Haulted" ?

---

### Post by HermanAB on 2009-01-11
Hmm, don't install fail2ban on a remote machine.  Sooner or later you will lock yourself out.  Rather use an iptables rate limiter to prevent all kinds of abuse:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

BTW, Linux machines are very robust.  Most problems are due to the use of bad passwords and with a 10 char password, you should be OK.

---
Working on a Remote Server

Maintenance of a remote server deserves special mention. How do you safely make modifications to a remote server, without running the risk of locking yourself out?

The problem being that you can easily make a mistake and cause iptables to block all network traffic, with the result that your remote SSH or Webmin session dies. You then have to phone the Server Farm support desk with your tail between your legs and ask them to please go and fix it...

The solution is to create a safety net using the 'at' daemon. At allows you to enter a bunch of commands for later execution. This is very convenient for construction of a safety net. A simple safety, is to flush all iptables rules, then set the default policies to ACCEPT:

# at now + 20 min [Enter]
at> iptables -F
at> iptables -P INPUT ACCEPT
at> iptables -P OUTPUT ACCEPT
at> iptables -P FORWARD ACCEPT
at> [CTRL-D]
#

After entering the above, you have twenty minutes to fix the firewall and delete the at job, otherwise it will trigger and flush netfilter for you, so you can recover from your booboo.

You can see the queued jobs with 'atq' and remove a job with 'atrm jobnumber'.

As you can gather, I did lock myself out of a machine on the other side of the world once. Fortunately I had the foresight to talk to the server farm help desk before I started, so when I had to make the inevitable call for help, they could get me going again very quickly. However, the experience made me think how to prevent that from happening again and the at (or cron) daemon has saved me on numerous occasions since!
---


Cheers,

Herman

---

### Post by osjak on 2009-01-11
Herman, that's an excelent advice! I just want to add that this is how you remove scheduled at jobs:
```
[ian@lyrebird ~]$ atq
16      Wed Jul 11 02:00:00 2007 a ian
17      Sat Jul 14 02:00:00 2007 a ian
14      Sun Jul  8 22:00:00 2007 a ian
15      Tue Jul 10 02:00:00 2007 a ian
[ian@lyrebird ~]$ atrm 16 14 15
[ian@lyrebird ~]$ atq
17      Sat Jul 14 02:00:00 2007 a ian
```
Source: [http://www.ibm.com/developerworks/linux/library/l-job-scheduling.html](http://www.ibm.com/developerworks/linux/library/l-job-scheduling.html)

---

