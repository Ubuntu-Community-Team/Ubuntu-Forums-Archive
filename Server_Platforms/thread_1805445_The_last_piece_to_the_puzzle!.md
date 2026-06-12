---
title: "The last piece to the puzzle!"
date: 2011-07-16
forum: Server Platforms
---

### Post by TimeDistort12 on 2011-07-16
I am in the process of designing my new dedicated internet server.

My current server runs Windows XP (O/S), Abyss Web Server (web server), and Mercury Mail (mail server).

My new server will run Linux (Ubuntu 10.04 LTS) (O/S), Apache 2.2 (web server), and now I am looking for a mail server.

So far I've checked out:

Postfix
Courier
Dovecot

I have found all of these to suck hard due to them being complex to configure, and they also lack proper documentation for someone who has better things to do than spend his day digging through 1000 pages to perform something which should be basic to perform.

I am not against configuration files or anything (I've chosen Apache!), but what I am looking for is something that is very straight forward to setup and will not require me to consult complex documentation every time I want to do something.

I have found something called MailSute Pro for Linux by AfterLogic, which has the qualities I am looking for, but the issue for me is that its a closed source application, which I do not feel comfortable using as its going to be for my private/business mail server.

Any suggestions?

---

### Post by volkswagner on 2011-07-16
You may be very happy running [Citadel]("http://www.citadel.org/doku.php").  For the record a mail server is complex, so in my opinion an easy setup bypasses the user needing to know what is going on under the hood.

You can easily setup Citadel, but may not learn much about the interal workings of mail server, because it just works... LOL.

Any way running Citadel along side apache requires you to setup a reverse proxy which is not difficult.

In the future you should consider listing your thread with a more specific title, as it may help get users with knowledge in the subject to look.  It should also help the search function for futures users looking for info on the same subject.

---

### Post by linuxnizer on 2011-07-16
interesting...I'm using Google Apps (Google Mail). It's easy to setup.

---

### Post by Gyokuro on 2011-07-16
Looking at your previous setup it seems that's a small setup. Maybe you have a look at [http://www.cherokee-project.com/](http://www.cherokee-project.com/) for a small web server. Postfix is not that hard to setup but maybe the suggested Citadel solution is something for you.

---

### Post by linuxnizer on 2011-07-16
to add my .02,
  Postfix is an MTA, Dovecot is POP3/IMAP server. You need both. If need easy management install webmin to manage both.

  Again, my advice is to forget both and use Google Mail for many reasons, you offload traffic to Google, you have better security running fewer servers on your box, also, you get 7G free mail box for each mailbox you create on Google mail, you can use your domain for sending/receiving emails,  plus Google mail is just awesome :).

---

### Post by TimeDistort12 on 2011-07-16
> **Gyokuro said:**
> Postfix is not that hard to setup but maybe the suggested Citadel solution is something for you.

I'd disagree, In comparison to Mercury Mail, its a nightmare. I had to read the manual for almost everything I wanted to do. It wasn't straight forward at all.

I checked out Citadel. Its not an MTA server.


> **linuxnizer said:**
> If need easy management install webmin to manage both.

Thanks so much! I'll check this out now.

> use Google Mail for many reasons, you offload traffic to Google, you have better security running fewer servers on your box, also, you get 7G free mail box for each mailbox you create on Google mail, you can use your domain for sending/receiving emails,  plus Google mail is just awesome :).

I would also be offloading the privacy of me, and the people that contact my domains.
I'll have 1TB of storage. :D

---

### Post by ian dobson on 2011-07-16
Hi,

Maybe have a look at xmail ([http://www.xmailserver.org](http://www.xmailserver.org)). Before I moved over to linux I was running xmail under windows, after upgrading to linux I stayed with xmail.

The configuration is all done through configuration files, abit like windows ini files. I've been running it under linux for about 3years now and am very happy with the performance and the configurability.

Regards
Ian Dobson

---

### Post by TimeDistort12 on 2011-07-17
Hey, I checked out XServer, but the source code is flawed. I followed the installation instructions, but it doesn't work.

---

### Post by ian dobson on 2011-07-17
> **TimeDistort12 said:**
> Hey, I checked out XServer, but the source code is flawed. I followed the installation instructions, but it doesn't work.

What do you mean "the source code is flawed" it needs several extra libs installed to be able to comile the source.

Regards
Ian Dobson

---

### Post by TimeDistort12 on 2011-07-17
The documentation said it only needed Libc6, which I have.

So, I did what it asked and then it gave me an error like "make -k Makefile.lnx" or something. So I trash the software.

---

### Post by ian dobson on 2011-07-17
Hi,

Thats not really an error message. But as I see your not willing to try, I'm not willing to help.

Regards
Ian Dobson

---

### Post by TimeDistort12 on 2011-07-17
It clearly was.

I love it when people tell others they are not willing to help. OH NOES!!!

---

### Post by volkswagner on 2011-07-17
> **TimeDistort12 said:**
> 

I checked out Citadel. Its not an MTA server.



I'm not really sure where this thread is headed.  You mention checking out Postfix, Courier, Dovecot. When using Postifix as an MTA you'll still need other components for a feature rich mail server.  If you want, webmail, IMAP/Pop3 this is where Dovecot or Courier come in.  For webmail you can select Horde, SquirrelMail, RoundCube, etc.

The statement Citadel is not an MTA may be technically correct, beause it is made of several components which include an MTA  aptly named, Citadel-MTA.

If you install the entire Citadel package you'll get Webmail, MTA, IMAP/Pop3, Calander, Instant messaging, a web based front end for admistration (no need for Webmin) and more.

You started this thread seeking an easy to use **mail server**.  Citadel certainly fits that bill.  Mail server is a very broad term.  If you are looking for Just an MTA, then Dovecot and Courier should not even be on the list, therefore I assumed you wanted a comprehensive Mail server with all the goodies.

You may want to add more requirements/detail to eliminate suggestions not meeting your criteria.

---

### Post by kgatan on 2011-07-17
There are plenty of guides for how to setup postfix and dovecot that are not hard to follow.

Check this one out,
[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto")

Also saying the software sucks because you cant set it up when its used my thousands of servers is kinda weird imo.

---

