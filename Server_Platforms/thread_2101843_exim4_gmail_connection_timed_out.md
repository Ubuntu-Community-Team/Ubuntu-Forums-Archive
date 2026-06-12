---
title: "exim4 gmail connection timed out"
date: 2013-01-05
forum: Server Platforms
---

### Post by vv1984 on 2013-01-05
Hi, 
i'm trying to setup exim4 on my ubuntu server to send mail from scripts to my personal mail.

I think i'm almost done, but when i launch this command:
**echo testing | mail -s Bla [email]vv198@gmail.com[/email]**

I get the following inside the mainlog of exim4:
```
2013-01-05 18:26:20 1TrXVk-0003AG-Bw <= <> R=1TrXVP-0003AB-Cd U=Debian-exim P=local S=1403
2013-01-05 18:26:20 1TrXVP-0003AB-Cd Completed
2013-01-05 18:26:30 1TrXVk-0003AG-Bw => vveronico <root@srv-cucina> R=local_user T=mail_spool
2013-01-05 18:26:30 1TrXVk-0003AG-Bw Completed
2013-01-05 18:28:15 1TrXXb-0003AY-Fw <= vv1984@gmail.com U=vveronico P=local S=374
2013-01-05 18:29:28 1TrXXb-0003AY-Fw smtp.gmail.com [42.0.20.80] Connection timed out
2013-01-05 18:29:28 1TrXXb-0003AY-Fw == vv1984@gmail.com R=smarthost T=remote_smtp_smarthost defer (110): Connection timed out
2013-01-05 18:51:11 1TrXtn-0003N5-Ot <= vv1984@gmail.com U=vveronico P=local S=374
2013-01-05 18:51:21 1TrXtn-0003N5-Ot gmail-smtp-msa.l.google.com [2a00:1450:4013:c01::6c] Network is unreachable
2013-01-05 18:51:22 1TrXtn-0003N5-Ot ** vv1984@gmail.com R=smarthost T=remote_smtp_smarthost: SMTP error from remote mail server after MAIL FROM:<vv1984@gmail.com> SIZE=1409: host gmail-smtp-msa.l.google.com [74.125.136.108]: 530-5.5.1 Authentication Required. Learn more at\n530 5.5.1 http://support.google.com/mail/bin/answer.py?answer=14257 q44sm118821809eep.5
```

What could be missing?
What tests could i try to fix it?

---

### Post by markbl on 2013-01-06
I do this for my home ubuntu and debian server[s]. I just "sudo apt-get install exim4-daemon-light" and set my ISP mail server as my smarthost. My email is hosted at google also. Do a "sudo dpkg-reconfigure exim4-config" to change the settings again.

---

### Post by vv1984 on 2013-01-06
> **markbl said:**
> I do this for my home ubuntu and debian server[s]. I just "sudo apt-get install exim4-daemon-light" and set my ISP mail server as my smarthost. My email is hosted at google also. Do a "sudo dpkg-reconfigure exim4-config" to change the settings again.

Sorry, but I really can't understand how could your answer help me.

I already configured exim4 and it's not working. You are suggesting me to reconfigure exim4, i already figured out that there was something wrong with configuration. 

I need to know what could be wrong with it..

---

### Post by markbl on 2013-01-06
> **vv1984 said:**
> Sorry, but I really can't understand how could your answer help me.

I'm telling you it is probably easier to just to what most do and configure your smtp server to your ISP server.

The error message you listed explicitly tells you the problem is that you have not configured authentication for gmail smtp. You normally don't need to bother with authentication for your ISP smtp server (because you normally have to authenticate just to get your adsl/cable connection up).

However, if you really want to configure gmail smtp authentication then just follow one of the many guides Google offers, e.g. [http://islandlinux.org/howto/configure-exim-use-gmail-smtp-server](http://islandlinux.org/howto/configure-exim-use-gmail-smtp-server).

---

### Post by vv1984 on 2013-01-06
> **markbl said:**
> I'm telling you it is probably easier to just to what most do and configure your smtp server to your ISP server.

The error message you listed explicitly tells you the problem is that you have not configured authentication for gmail smtp. You normally don't need to bother with authentication for your ISP smtp server (because you normally have to authenticate just to get your adsl/cable connection up).

However, if you really want to configure gmail smtp authentication then just follow one of the many guides Google offers, e.g. [http://islandlinux.org/howto/configure-exim-use-gmail-smtp-server](http://islandlinux.org/howto/configure-exim-use-gmail-smtp-server).

Thank you this is clearer. I'm sorry, but i'm quite a noob. ;)
I'm going to try this now and let you know about.

---

### Post by vv1984 on 2013-01-06
> **vv1984 said:**
> Thank you this is clearer. I'm sorry, but i'm quite a noob. ;)
I'm going to try this now and let you know about.

Thank you very much indeed, this worked out great! \\:D/

The main difference from what i was doing is the **/etc/exim4/passwd.client** file:
other tutorials i found were not so precise on it.

Btw, i had to clear the exim4 queue with this command to make it work at first:
**root@localhost# exim -Mrm <message-id> [ <message-id> ... ]**

This site looks quite useful:
[http://bradthemad.org/tech/notes/exim_cheatsheet.php]("http://bradthemad.org/tech/notes/exim_cheatsheet.php")

---

