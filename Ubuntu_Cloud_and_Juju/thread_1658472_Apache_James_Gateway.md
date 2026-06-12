---
title: "Apache James Gateway"
date: 2011-01-02
forum: Ubuntu Cloud and Juju
---

### Post by Ohm's Lawyer on 2011-01-02
Hello all,
Well, I've finally got my cloud up and running. Now I'm trying to get mail going. Is anyone here familiar with Apache James?

At this point, I have my primary and secondary WAN gateways, which do all of my filtering. They should forward to my local gateway, which should forward to my individual instances. I've so far had some trouble getting everyone to play nicely. Really, I'm having difficulty with the forwarding issues. 

Anyone have any ideas / experience?

---

### Post by raymdt on 2011-01-02
Do you have internet within the Instance?

---

### Post by Ohm's Lawyer on 2011-01-02
I do.

---

### Post by kim0 on 2011-01-03
Hi,
Could you please supply more information about your setup and what kind of errors you're see'ing. I'm not familiar with "James" so I may need some more explaining to be able to help.

@raymdt, awaiting your ping (kim0 on irc) :)

---

### Post by Ohm's Lawyer on 2011-01-03
Sure! Well, I've got a box that will be going to a hosting center. That box is running two separate machines (1 primary gateway, 1 redundant gateway) with maverick server, apache james, clamAV, cleanmail, and spamassasin. That box needs to filter, collect and cue up my emails in case my local gateway is down. If everything is working correctly, it should forward the email to my local gateway, which is only running maverick server, httpd, and james. This box is intended to dole out the emails to the appropriate instance on the cloud and cue up email if an instance is down. Finally, I have james running on each instance in order to receive emails for that particular group. I know it's all a little redundant, but from a business standpoint, people get a little peeved if you loose their mail.

As far as testing goes, it looks like everything is running fine. I'm not getting any error messages, but once the email reaches the first gateway, it just seems to hang up. I can cue up email there until my drives are full. For whatever reason, it's not forwarding to the next box. I've triple checked all of my conf files and the IPs and ports all look good, so I'm kind of at a loss.

Any ideas?

---

### Post by kim0 on 2011-01-04
Can't say it's too clear for me, however it's starting to sound like this is a smtp-server question, not directly related to cloud. As such, you have a higher chance of getting a better answer by directing that question to the Ubuntu server mailing list
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-server](https://lists.ubuntu.com/mailman/listinfo/ubuntu-server)
or perhaps the server forums over here (not too involved with that forum yet)

---

