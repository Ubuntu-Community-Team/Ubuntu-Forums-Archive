---
title: "Email Server"
date: 2012-03-10
forum: Server Platforms
---

### Post by cesar98026 on 2012-03-10
I need to install a email server on Ubuntu 11.10, for development purposes. And I don't know how to do it.:confused:

---

### Post by lisati on 2012-03-10
What are your requirements? Simple MTA or something more?

Even installing a standalone MTA such as [Postfix]("https://help.ubuntu.com/community/Postfix") can take a little work while you finesse the settings.

---

### Post by codemaniac on 2012-03-10
There are ample of community how to tutorials floating around , you may find them helpful .
[https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer")

---

### Post by HermanAB on 2012-03-11
Howdy,

You can spend two weeks to install Postfix, or you can install Citadel in about 20 minutes.  Pick your poison.

---

### Post by kevdog on 2012-03-11
I just installed Postfix -- didn't once before many years ago so it was kind of like starting over.  Took me about 2-3 hours just to set up the smtp authentication.  This really wasn't postfix's fault -- it was because the documentation on the web was so crappy.

---

### Post by HermanAB on 2012-03-12
> it was because the documentation on the web was so crappy
Exactly.

The secret of Citadel is the Easy Install script which sets the whole thing up for you in a way that works out of the box.

---

### Post by cesar98026 on 2012-03-13
You guys are confusing me...:confused: All I want to do is make a email service. So I installed Postfix, Cyrus, a LAMP server, and something else. But I don't know how to make it work together, and also want to make my own Web based thing to view emails and stuff. I guess I'm a beginner or maybe not, because I know how to work in a terminal and stuff.

---

### Post by mruiz@ic-sa.com on 2012-03-14
> **cesar98026 said:**
> You guys are confusing me...:confused: All I want to do is make a email service. So I installed Postfix, Cyrus, a LAMP server, and something else. But I don't know how to make it work together, and also want to make my own Web based thing to view emails and stuff. I guess I'm a beginner or maybe not, because I know how to work in a terminal and stuff.

Personally I used Postfix for SMTP Relay.

I used this as a reference.  I hope that helps.

[http://www.comptechdoc.org/os/linux/manual4/mailpostfix.html](http://www.comptechdoc.org/os/linux/manual4/mailpostfix.html)

---

### Post by cesar98026 on 2012-03-14
Can you use a ip address for a domain name?

---

### Post by MSPdwalt on 2012-03-14
What is the purpose of this email server? Just to bounce messages off of for an app?

---

### Post by cesar98026 on 2012-03-15
What do mean? I just wanted to make something like Squirrellmail...

---

### Post by mikaelcrocker on 2012-03-15
If you just want to get email out, you can use Postifx, and I think you only need about 8 lines or so in the I wanna say main.cf file.  

You could always get a sendgrid acount and sent emails through there as well using posfix and the mail command.  It's not too terribly hard or time consuming to set up

---

### Post by Bradyhawke on 2012-03-15
> **cesar98026 said:**
> You guys are confusing me...:confused: All I want to do is make a email service. So I installed Postfix, Cyrus, a LAMP server, and something else. But I don't know how to make it work together, and also want to make my own Web based thing to view emails and stuff. I guess I'm a beginner or maybe not, because I know how to work in a terminal and stuff.

This is the most information you've provided so far.  I think the reason why you are getting limited replies is because of the lack of details and serious lack of knowledge.  I'm going to ask some questions that might help out a bit if you can take the time to provide some details with your answers, and then maybe other forum members can take the time out to help you out.

**1) What type of email service do you want to make?** *(examples would be a home server for yourself and maybe family, a server for a work environment for 5 / 10 / 20 / 50 / 100+ employees, an email service where you would provide webmail to the public - please don't just pick an example, take the time to detail what you want your service to provide.)*

**2) What software have you already installed?** *(its a very good idea to keep track of everything you've installed, saying "and something else" could be anything from windows 3.11 to porn, so you should know what you've installed.  even just keeping a list on a notepad can help - yes, its low-tech but installing software into a setup you've never done before can use all the help it can get.)*

**3) What is your experience with Linux / all software you've already installed?** *(its at this point that your experience matters.  If you know Linux like the back of your hand then the help can be detailed in the correct direction.  If your experience is more with windows or just more like "I know some stuff", then hopefully someone will be able to provide much more detailed help or point you to a really good guide.)*

Take out a few minutes and write out a nice explanation of what you need and you'll get the best answers you can.  Most people won't waste their time trying to help you if you can't take the time to research and detail what you want to do.


- Bradyhawke    :guitar:

---

### Post by cesar98026 on 2012-03-17
1. I want to provide webmail to the public. My service will provide email forwarding, a lot of space, the ability to send emails with attached files, and it will be fast. I want it to be free. With the capacity of multiple email addresses.

2.libauthen-sasl-perl, libsasl2-modules, libcyrus-imap-perl22, cyrus-admin-2.2, cyrus-common-2.2, cyrus-clients-2.2, sasl-bin, libsasl2-2, phpmyadmin, a lamp server, dovecot-imapd, dovecot-common, dovecot-pop3d, Postfix, ect.

3.Postfix, I need to learn some more. Dovecot I don't know. Little bit of experience with lamp server... I know Linux pretty well, the terminal can be frustrating sometimes.:KS

---

### Post by caseygibbs on 2012-04-03
I agree with HermanAB that Citadel is super super easy to set up and get working, but be advised that there is some sort of bug with easy install on 11.10, something to do with curl and ssl. If you can work around that, or install 10.04, Citadel is an excellent way to go. You can have fully functioning webmail (along with a truckload of additional communication functionality) in minutes.
C

---

### Post by Cheesemill on 2012-04-03
It's for Debian, not Ubuntu but I have found the following tutorials great for setting up a mail server. As well as telling you what to do, it also explains why you are doing it.

I've had this setup working on Ubuntu with no modifications to the guide.

[http://workaround.org/ispmail/squeeze](http://workaround.org/ispmail/squeeze)

---

### Post by cesar98026 on 2012-04-14
Im having a problem with Dovecot 2 the .conf file is not the same.

---

### Post by cesar98026 on 2012-11-25
Thank you everyone. I finally have a working mail server complete with everything using flurdy's guide.

---

