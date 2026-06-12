---
title: "Configure ubuntu server to email with exchange?"
date: 2010-05-15
forum: Server Platforms
---

### Post by lazychris2000 on 2010-05-15
Little bit of a back story.  I work for a small computer repair company as a computer technician.  Recently, our network guy just up and quit, leaving us with a corrupted ubuntu server and me to figure out everything (he left no documentation at all).  The OS got hosed when 2 of the OS drives (it was a raid 5) got unrecoverable bad sectors.  We replaced the bad drives, but the server wouldnt boot anymore.  The server was setup as a web/email/file server, and now that it has crashed, the boss wanted to move over to exchange, which integrates into our ticketing system.  We just installed the exchange server and I was tasked with reinstalling the ubuntu server.  Now the exchange server handles email and website and the ubuntu server is a standalone file server.  Got a 10.04 x64 server edition disc, installed and was up and running within an hour.  The problem I am running into is that previously, the server was running zimbra for email/calendaring and would email me whenever there were problems with the raid using this script as a daily cronjob:
```
/usr/local/sbin/tw_cli alarms | mailx <my email address> -s "RAID Alarms"
```
This was really handy because it was what tipped me off that the server was having troubles and let me get everything backed up before it completely died.  Now that it is not a mail server, I am trying to find out if there is a way to configure mailx (or whatever mail client I have to use) to send mail using our exchange server.  I am a long-time ubuntu desktop user, but a n00b ubuntu server admin, so any help would be most appreciated (even if the answer is 'that is not possible')

Ubuntu server specs:
Supermicro X6DA8
Dual 3GHz Xeon (single core, HT enabled)
8GB PC2-3200 Registered, ECC
15x 750GB Seagate ES.2 (3 drive raid 5 for OS, 10 drive raid 10 for data, 2 hotswap spares)
3ware 9550sx-16ML
Ubuntu server edition 10.04 x64

Exchange server specs:
Dell Poweredge sc1435
Single Opteron 2210 (dual core 1.8GHz)
8GB PC2-3200 Registered, ECC
2x750GB Seagate ES.2--1 drive for OS, 1 for nightly backups (no raid yet because we were not expecting to deploy so soon, but a 3ware card is on order)
Windows SBS 2008, Exchange 2007

If there is any information I left out, please let me know

---

### Post by Agent ME on 2010-05-16
Does the exchange server support SMTP? This tutorial might help you then: [http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

---

### Post by lazychris2000 on 2010-05-16
```

akgeeks@ubuntu:~$ mail <email address>
Subject: test
test
.
EOT
/usr/lib/sendmail: No such file or directory
"/home/akgeeks/dead.letter" 9/213
. . . message not sent.

```
Thanks for the info, but this is what I get after following the directions from that link.  When I try to install sendmail, it wants me to remove exim4-config...not entirely sure what to do here since the walkthrough says to install the exim4-config package.

---

### Post by lazychris2000 on 2010-05-16
So, I decided to just install sendmail and see what happens.  Worst case scenario, I have to wipe the server.  No big deal.  Weird thing is that it works sending emails to my gmail account, but not to my work account.  Not a huge deal, but it is strange nonetheless.  Any ideas?

---

### Post by HermanAB on 2010-05-16
Multiple solutions:
Postfix
Citadel
Nullmailer

and a few others similar to nullmailer.

I would suggest nullmailer, since there is nothing easier.  It has only about 1 line to configure - the address of the Exchange server.  You'll find it with Google.

---

### Post by ezacon on 2010-05-16
I use email client.
[http://www.cleancode.org/projects/email](http://www.cleancode.org/projects/email)

---

### Post by lazychris2000 on 2010-06-03
Been meaning to get back to this thread for an update.
Not sure what happened, but before I got a chance to make any changes, it started working.  Its a mystery to me :confused:

---

