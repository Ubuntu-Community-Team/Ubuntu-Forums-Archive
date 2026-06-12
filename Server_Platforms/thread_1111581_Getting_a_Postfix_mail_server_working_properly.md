---
title: "Getting a Postfix mail server working properly"
date: 2009-03-30
forum: Server Platforms
---

### Post by realmadrid on 2009-03-30
Hi everyone, first post here.

I'm relatively new to Linux with some experience in UNIX (Darwin/OS X and Solaris) and I'm trying to get a mail server running to send out emails from my web apps. Right now my focus is on actually SENDING mail, I'll worry about receiving properly when that matters to me.

These apps in question (Rails apps) were on Solaris before, hosted on Joyent, and mail seemed to just work out of the box. Since I've never actually set up a mail server, I looked for a good guide and found one here: 

[https://help.ubuntu.com/8.04/serverguide/C/postfix.html](https://help.ubuntu.com/8.04/serverguide/C/postfix.html)

I followed it down to the letter, obviously only changing things like IP and domain names.

Doing checks with [http://www.mxtoolbox.com/](http://www.mxtoolbox.com/) shows there are no issues, I have MX setup, RDNS, etc.

The problem is I can't get any mail sent out. This is a quick snippet of the mail.info logs found in /var/log

```

Mar 30 10:21:31 vn1111 postfix/smtp[28169]: connect to iname-com.mr.outblaze.com[208.36.123.59]:25: Connection timed out
Mar 30 10:21:31 vn1111 postfix/smtp[28167]: connect to c.mx.mail.yahoo.com[216.39.53.2]:25: Connection timed out
Mar 30 10:21:31 vn1111 postfix/smtp[28165]: connect to e.mx.mail.yahoo.com[216.39.53.1]:25: Connection timed out
Mar 30 10:22:01 vn1111 postfix/smtp[28164]: connect to mx3.hotmail.com[65.54.245.72]:25: Connection timed out
Mar 30 10:22:01 vn1111 postfix/smtp[28169]: connect to iname-com.mr.outblaze.com[208.36.123.55]:25: Connection timed out

```

Lots of those, different domains, etc. If I do a telnet like the guide says and everything checks out fine. I can also send an email to [email]root@mydomain.com[/email] and receive that message, so I really don't think it's Postfix failing, it seems to be "fine."

This is on a dedicated server, not a home thing with an ISP that likes to block/filter SMTP ports so that's not the culprit..

Anyone have any ideas? Thanks in advance, I've been Googling for hours.

---

### Post by HermanAB on 2009-03-31
Mail problems are frequently due to DNS configuration errors.  You must have an A, PTR and MX record for the server otherwise everybody else will bounce your mail.

---

### Post by hyper_ch on 2009-03-31
also a static ip address or relaying your email through another server if you wnt to send email as most servers won't accept mailservers on a dynamic ip.

---

### Post by realmadrid on 2009-03-31
Thanks guys.

I'm on a static IP on a dedicated server in a datacenter. Also, the A, PTR, RDNS, and MX records are set. I used various tools to verify as well, such as [http://www.mxtoolbox.com](http://www.mxtoolbox.com)

No apparent problems detected. This is what has me stumped, everything "seems" to be on the up-and-up.

---

### Post by HermanAB on 2009-03-31
Do low level debugging with telnet.  Google for 'send manual email with telnet'.  That will show what is going on.

Look at the postfix queues to see were things get stuck - the manual is on the postfix web site.

When all else fails, install Citadel.  It only takes about 20 minutes to run the Easy install script and it will work.  It is a self contained solution, not Lego blocks, so there is less to go wrong in the configuration.

I have given up with postfix years ago - waste of time.

---

### Post by hyper_ch on 2009-03-31
have a look at the perfect howto from falko on [http://www.howtoforge.com](http://www.howtoforge.com) --> you'll get a step-by-step guide to setup postfix/courier

---

