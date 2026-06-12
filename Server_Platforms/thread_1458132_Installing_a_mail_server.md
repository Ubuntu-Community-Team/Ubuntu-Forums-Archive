---
title: "Installing a mail server"
date: 2010-04-19
forum: Server Platforms
---

### Post by Vegan on 2010-04-19
OK I have Webmin so I was wanting some help to install an email system. I like Postfix as IBM sponsors it, but I am not adverse to another title as long as the MX records work and that I can get to the mail with a reader of some kind. 

I like the idea of IMAP the way Google has theirs.

:popcorn:

---

### Post by cdenley on 2010-04-19
I recommend zimbra. It uses postfix.
[http://www.zimbra.com/downloads/os-downloads.html](http://www.zimbra.com/downloads/os-downloads.html)

---

### Post by dudumomo on 2010-04-19
Last month I did my mail server too.
Postfix + courier-imap + Spamassasin and co.
Then I wrote a tutorial:
[http://www.freelydifferent.com/self-hosting/setting-up-your-mail-server/](http://www.freelydifferent.com/self-hosting/setting-up-your-mail-server/)

I hope it's clear and can help you.

Furthermore, I'm using Roundcube as a web mail interface. (Love it actually !)

---

### Post by cdenley on 2010-04-19
Zimbra also uses spamassassin, but has its own IMAP server and webmail interface. I've never encountered a webmail interface I liked better, and it can't get much easier to install and configure.

---

### Post by Litachao on 2010-04-19
I used [http://www.iredmail.org/](http://www.iredmail.org/) to setup my mailserver. At first I tried to setup a mailserver "manually", configuring and tweaking all the various components myself. That didn't work so well and gave me quite a headache. 
Iredmail has a scripted setup of its various components, including postfix, dovecot, spamassasin, amavis, ClamAV and openLDAP for authentication. It includes a nice, although in its free version very limited, web interface for administration and roundcube for webmail.
I integrated Apache w/ modDav and Davical with Iredmails openLDAP configuration, so that when I make a webmail user, they automatically get calendaring and a webdav volume, too.

---

### Post by Vegan on 2010-04-19
So is there anything that is as powerful as Exchange Server?

---

### Post by cdenley on 2010-04-19
> **Vegan said:**
> So is there anything that is as powerful as Exchange Server?

I've never used exchange, but zimbra is probably the best alternative to exchange. I'm not sure if the open-source edition includes the Outlook connector. I use the network edition.

---

### Post by Vegan on 2010-04-19
I am only exploring options right now, I am looking at what is going to make the most sense.

If I can achieve basic mail, that is good, but I like some of the more advanced features too.

---

### Post by Vegan on 2010-04-19
I guess after thinking about it more, I wanted to have the following services....

smtp.contract-developer.tk
pop3.contract-developer.tk
imap.contract-developer.tk

others are not crucial, this is really all I need for e-mail.

Managing with a brower is a big plus, Webmin or separate is not a major problem as long as I can get into it.

I would like authentication for the email services.

---

### Post by Vegan on 2010-04-19
> **dudumomo said:**
> Last month I did my mail server too.
Postfix + courier-imap + Spamassasin and co.
Then I wrote a tutorial:
[http://www.freelydifferent.com/self-hosting/setting-up-your-mail-server/](http://www.freelydifferent.com/self-hosting/setting-up-your-mail-server/)

I hope it's clear and can help you.

Furthermore, I'm using Roundcube as a web mail interface. (Love it actually !)

I had postfix alread installed, so I need to configre it for procmail to see. Suggestions?

---

### Post by cdenley on 2010-04-19
> **Vegan said:**
> I guess after thinking about it more, I wanted to have the following services....

smtp.contract-developer.tk
pop3.contract-developer.tk
imap.contract-developer.tk

others are not crucial, this is really all I need for e-mail.

Managing with a brower is a big plus, Webmin or separate is not a major problem as long as I can get into it.

I would like authentication for the email services.

Once again, zimbra does all that, and is completely managed from the browser except for the installation and upgrades.

---

### Post by HermanAB on 2010-04-20
Hmmm, installing a mail system used to be a huge head-ache. You can go the Lego route and install Postfix, Apache, Squirrel and all the rest until you eventually have a working system with most of the features you need - or you can install Citadel and have a full featured working system in about 30 minutes:
[http://www.citadel.org](http://www.citadel.org)

You can even download a preconfigured VMware image and run that with just about zero effort.

---

### Post by dudumomo on 2010-04-20
Never try citadel. Seems interesting.

I've just configure directly postfix and co. Doesn't take that much time with a clear tuto. (The second time I've installed a mail server, it was quite easy actually as I wrote a tuto just before)

But I will try to get info about citadel then.

---

### Post by cdenley on 2010-04-20
> **HermanAB said:**
> Hmmm, installing a mail system used to be a huge head-ache. You can go the Lego route and install Postfix, Apache, Squirrel and all the rest until you eventually have a working system with most of the features you need - or you can install Citadel and have a full featured working system in about 30 minutes:
[http://www.citadel.org](http://www.citadel.org)

You can even download a preconfigured VMware image and run that with just about zero effort.

I agree about not going the "Lego" route, but once again I suggest zimbra. I tried Citadel, and my experience with it was horrible. It was one problem after another, and was completely unusable for me. I highly recommend zimbra. Just as easy to install. It shouldn't be difficult to find a VMware image, either, since VMware acquired Zimbra from Yahoo a few months ago.

---

### Post by Vegan on 2010-04-20
Well all I know is I would like to get procmail up if possible before I nuke it in favor of something else.

Clearly an easy to setup mail system is still a pipe-dream

---

### Post by cdenley on 2010-04-20
> **Vegan said:**
> Clearly an easy to setup mail system is still a pipe-dream

Did you read my posts? Zimbra is very easy to setup.

---

### Post by tbay007 on 2010-04-22
My biggest question with this, is i am also trying to setup a mail server.

I hear that Zimbra isn't compatible with Ubuntu 9.10 desktop.  Is this true?  Can anyone recommend any tutorials on it?  Should i use vmware and install ubuntu 8.04 and install zimbra?  Complete newb to mail servers and i am trying to learn what to do, but there is so much information!

Also Citadel says it supports 9.10 desktop.  Just was wondering, Hopefully I am not beating this thread to death.

---

### Post by cdenley on 2010-04-22
> **tbay007 said:**
> My biggest question with this, is i am also trying to setup a mail server.

I hear that Zimbra isn't compatible with Ubuntu 9.10 desktop.  Is this true?  Can anyone recommend any tutorials on it?  Should i use vmware and install ubuntu 8.04 and install zimbra?  Complete newb to mail servers and i am trying to learn what to do, but there is so much information!

Also Citadel says it supports 9.10 desktop.  Just was wondering, Hopefully I am not beating this thread to death.

Zimbra only supports LTS releases. I doubt there are many people who want support for non-LTS releases. Who wants to upgrade their server's OS every 6 months? It might take a couple months before 10.04 is supported. If I remember correctly, the open-source version was released for 8.04 a while before there was a paid network edition for 8.04. They wouldn't want to provide commercial support for a software suite unless it was thoroughly tested for compatibility. If they supported every ubuntu release, by the time it was tested for compatibility and considered stable, the next ubuntu release would probably be right around the corner.

I wouldn't be surprised if Citadel "supports" every ubuntu release. Considering the experience I had, they probably don't spend much time testing their product.

---

### Post by tbay007 on 2010-04-23
So I guess the best thing to do is use a Virtual Machine, and virtualize ubuntu 8.04....*sigh* i hope it doesn't take up much space.  I feel silly virtualizing ubuntu again inside an ubuntu desktop lol!

---

### Post by spynappels on 2010-04-23
Is there a specific reason you want to run from a Desktop version? If you want to run a VMWare image, it is probably easier and more resource efficient to set up a VMWare ESXi Host and place several VMs on it including your mail server image and whatever other servers and desktops you want. You do want it to be on permanently, don't you?

Desktops tend to get switched off at inopportune moments in my experience, having a headless box running somewhere out of the way might be a safer option.

---

### Post by HermanAB on 2010-04-23
Hmm, I've been running Citadel for many years, with several small businesses as customers.  Here are some guides in the Mail and Web section:
[http://www.aeronetworks.ca/linuxhowtos.html](http://www.aeronetworks.ca/linuxhowtos.html)

but honestly, installing it only takes about 20 to 30 minutes, so trying it out is very easy indeed.  If you don't like the default theme of the web interface, it can be changed and you can also use things like Roundcube or even Squirrel and it works with any and all mail clients including Outlook.  The Easy Install system does what it does, in order to make it easy...

---

### Post by ph3ar on 2012-06-04
Hi,
> **Litachao said:**
> I used [http://www.iredmail.org/](http://www.iredmail.org/) to setup my mailserver. At first I tried to setup a mailserver "manually", configuring and tweaking all the various components myself. That didn't work so well and gave me quite a headache. 
Iredmail has a scripted setup of its various components, including postfix, dovecot, spamassasin, amavis, ClamAV and openLDAP for authentication. It includes a nice, although in its free version very limited, web interface for administration and roundcube for webmail.
I integrated Apache w/ modDav and Davical with Iredmails openLDAP configuration, so that when I make a webmail user, they automatically get calendaring and a webdav volume, too.

Do you mind sharing your experience in seting up iRedMail with Davical?

Thanks.

---

### Post by nj_peeps on 2012-06-04
> **Vegan said:**
> I am only exploring options right now, I am looking at what is going to make the most sense.

If I can achieve basic mail, that is good, but I like some of the more advanced features too.

_[Open-Xchange]("http://www.open-xchange.com/home.html")_ has alot of advanced features, but I think you have to pay to get Outlook extender plug-in.  

I never used on a production box, but I have messed with it a bit, and the web UI is very nice.

Also, if you don't like spamassin for filtering, you can use _[ASSP]("http://www.magicvillage.de/%7EFritz_Borgstedt/assp/0003D91C-8000001C/")_ as an alternative. I have been using it for years, and it will work with *any* MTA. and it works very well.

---

