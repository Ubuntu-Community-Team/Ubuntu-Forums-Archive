---
title: "n00b setup simple SMTP relay"
date: 2011-06-07
forum: Server Platforms
---

### Post by tseb on 2011-06-07
Hi all - 

Is the term a 'simple SMTP relay' a contradiction in terms?! It seems complicated to me!

I have an elderly Dell server on which I have just made a fresh install of 10.04 LTS server. I had 8.04 running on it for a long time, but I haven't tried an SMTP server before. It is a headless server with CLI (no GUI) and the latest version of Webmin installed.
I have a basic LAMP server installed for a few websites using PHPbb and Joomla, and also I run a Mediatomb server for our household. When I installed I also chose to install mail services, but these remain masked behind NAT at the moment

I now want to set up an SMTP relay server so when I am working away and using different wifi points or my notoriously unreliable 3G dongle I can always send emails through the home server (from my iPhone and my laptop) rather than having to look up the SMTP server for each ISP of the place where I am working.

What I want is an authenticated server which takes my email and redirects it to my home ISP's SMTP server. I need only 3 authenticated users to have access (myself, my wife and my son). I don't need (or want) any incoming mail services at all.

Useful modules installed are: Dovecot, Postfix, Procmail mail filter, PAM - but how do I set them up?

Is there any simple setup that I could do, preferably through Webmin, but I can handle CLI if necessary? 

I have looked at the Ubuntu help pages, but it looks so complicated to set up something that seems like it should be so simple to me!

Thank you anybody in advance for any help received, or pointers in the right direction...

Tseb.

---

### Post by HermanAB on 2011-06-08
Citadel.  It can do everything and anything email related and is configured via its own web server interface.  It takes about 20 minutes to run the Easy Install script.  There is nothing easier.

[http://citadel.org](http://citadel.org)

---

### Post by Lars Noodén on 2011-06-08
Citadel groupware is overkill in this setting. However one of its components might be useful here:  You can look at either postfix or exim for setting up a simple SMTP relay.

---

### Post by Lars Noodén on 2011-06-08
> **tseb said:**
> 
Useful modules installed are: Dovecot, Postfix, Procmail mail filter, PAM - but how do I set them up?

The relevant ones are dovecot and postfix.  PAM and Procmail are not mail servers.  Once you've chosen a mail server (dovecot, postfix, exim), you can find HOWTOs and tutorials on setting up relays.  IIRC, one of them even had that option during the initial setup.

---

### Post by brettg on 2011-06-08
Honestly, unless you are extremely paranoid about privacy, using gmail smtp is your easiest option. You can use it with your own domain if you want to.

I have my own domain, I have a sendmail server for my domain that inbound emails go to. The sendmail server simply forwards email to my gmail account. My gmail account is configured to send as my own private domain by default. 

My emails are available to me from anywhere on any device, it's easy and it has no drawbacks other than paranoia that google can scrape your emails as they pass through and then target ads at you later.

Frankly, I don't even notice the ads.

---

### Post by tseb on 2011-06-08
Brettg, 

I don't really understand about gmail, but I don't want any ads to go out with my emails, as I use them for work and they have to look professional...

Lars, 
Do you mean that both dovecot and postfix do the same things? Why did the Ubuntu setup install both of them for me? 

Which would you suggest I use in my situation, bearing in mind I want it as simple as possible but also I don't want it easy to get into, so I am not used as a mail relay by others. Would you be able to point me in the direction of a good tutorial please?

Thank you all for the replies

tseb.

---

### Post by Lars Noodén on 2011-06-08
Sorry, scratch dovecot.  Dovecot might only be needed if IMAP is needed.  Since the issue is about sending mail instead of receiving then it's not needed.

---

### Post by tseb on 2011-06-08
I have been looking at many tutorials for Postfix to set it up. A couple of questions:-

1. I am confused about SMTP AUTH. 
I need to set up my system so that I have to authenticate from my mail client on my laptop from outside my local home network (to my server inside my home network), but for my server to send to my ISP's SMTP server It doesn't need to authenticate (my ISP seems to assume that any email from the local home network is OK). So I need authentication coming into the server but not going out... I have seen all sorts of things such as sasl_passwd - is this for incoming mail to the system or outgoing to the next SMTP server down the line (my ISP)? Do I need SMTP AUTH? Do I need a Certificate?
My ISP states categorically that they don't block any ports at all.

2. Also on some tutorials there are mentions that Postfix changes the 'from' email domain in messages relayed through it. I don't want this to happen, as I send my business emails from one domain and my personal ones from another domain, and I don't host any of those domains - they are not mine at all... (e.g. my son uses tesco.net as his email provider, I use btinternet.com for business and a different one for personal use - I don't want the 'from' field to be changed at all)

I don't want to try all sorts of things on the server and mess about for a long time and then have something that works 'just by the skin of its teeth' but I would rather have a reliable system that works well.

Any help from anyone please?

Thank you 

tseb

_______________________

Some tutorials/forum posts I have looked at to get ideas from - please comment if you would recommend one or say another is not worth using...

[http://www.howtoforge.com/postfix_relaying_through_another_mailserver]("http://www.howtoforge.com/postfix_relaying_through_another_mailserver")

[http://www.gungeralv.org/notes/archives/2003/06/howto_configure_postfix_to_use_a_remote_smtp_relay_host.php]("http://www.gungeralv.org/notes/archives/2003/06/howto_configure_postfix_to_use_a_remote_smtp_relay_host.php")

[http://ubuntuforums.org/archive/index.php/t-586029.html]("http://ubuntuforums.org/archive/index.php/t-586029.html")

[http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html]("http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html")

[http://forums.fedoraforum.org/archive/index.php/t-105309.html]("http://forums.fedoraforum.org/archive/index.php/t-105309.html")

[http://www.postfix.org/BASIC_CONFIGURATION_README.html]("http://www.postfix.org/BASIC_CONFIGURATION_README.html")

---

### Post by brettg on 2011-06-09
"I don't really understand about gmail, but I don't want any ads to go out with my emails,"

Gmail doesn't stick ads on your mails like Hotmail does, you only see the ads when you are using the gmail web interface to read and write emails.

If you are using it as a simple email relay you wont see any ads and nor will your recipients.

[Instructions here]("http://tuxnetworks.blogspot.com/2009/03/mutt-to-remote-smtp-server.html") if you are interested. 

It takes about 3 minutes to setup.

---

### Post by tseb on 2011-06-25
Any more suggestions from people? I have looked into gmail, and I really would rather not use it. I don't want to be reliant on Google, and I am worried about security. I use a very good ISP, and I would prefer all mail to go through them. 

See my post (two above) for more details.

Thanks

tseb

---

### Post by Andrew_P on 2012-03-16
If you don't mind spending $1.50 to $2.50 per month, there are a number of inexpensive SMTP relay services that fill the bill for users on-the-go.  Take a look at SMTP2go.com, smtp-server.com, authsmtp.com, among others.  They manage the hardware and, you don't need to install any software on your devices to use the services, and they work anywhere in the world.  Moreover, since they manage the system, you don't need to worry about a homebrew server going down on your home network connection due to a power glitch or expired IP lease while you're on that 3-week European vacation.

---

