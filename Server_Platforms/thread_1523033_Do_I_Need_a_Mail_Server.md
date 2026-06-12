---
title: "Do I Need a Mail Server?"
date: 2010-07-03
forum: Server Platforms
---

### Post by ChurroLoco on 2010-07-03
Hi everyone,
I'm starting my own company and decided to setup my first company server using Ubuntu.  I need some advice.  Keep in mind I don't expect much traffic to this site.  It is mainly for my small team and maybe a few visitors.

I have setup a web server with wordpress and mantis bug tracking.  Static IP, registered domain.  The works!  Some of services allow them to send emails, and I would like to take advantage of it but I assume that it needs some setup.

Do I need to make it into a mail server also?  Can I just send emails from it, or do I need to register with some service.  

As a C/C++ programmer I always made fun of those IT people in college... now the jokes on me. :popcorn:

---

### Post by Bachstelze on 2010-07-03
> **ChurroLoco said:**
> 
Do I need to make it into a mail server also?  Can I just send emails from it, or do I need to register with some service.  


You can send email from it, just install a MTA like Postfix, the default config should work.

---

### Post by lisati on 2010-07-03
One advantage of having your own email server is that you have an extra options available to you that aren't generally available if you rely on servers run by other people. 

Like Bachstelze says, if you choose to install Postfix, the default settings are fairly sensible. 

I have been running my own private email server since the end of January, and enjoyed tinkering with the settings while learning about spam prevention measures. I use Postfix (the main MTA), amavis+spamassassin+clamav (help keep out the junk), Squirrelmail (basic Webmail) and a few other bells and whistles that I've gradually added as I've found my way around.

---

### Post by DJYoshaBYD on 2010-07-03
lets put it this way.. its always better to have your own for a small business, IF you can manage it..

I wouldnt use a server for production email without having some sort of experience running it.. really, a simple setup as mentioned above would work, but with the cost of having a fully managed email server from a company like SiteGround (thats who i went through.. great pricing, fast servers.. no issues), its not too bad.. you could probably get a full blown email server that is hosted by a webhost for around 50 bucks per year.. 

now, the MAIN advantage to this, is their actual internet connection.. Smaller companies will run a few T1's (1.5mbps).. This usually is very reliable, and has a great SLA, which means if it does go down, they will get it fixed pronto

most of the big guys use DS3 connections, which are ~45mbps... these companies will give you the most reliability..

now, i am NOT saying dont make your own server.. its sooooooooo nice to have.. i love mine.. 

but, im running consumer (but really fast.. 22mbps) cable service, and if it goes down, there is a chance it could be down for up to 24 hours or more.. not a good thing for an email server... :)

its up to you.. weigh cost vs production value... do what works for you.. your own server is great, but a hosted one is usually more reliable, in terms of the connection for them..

one VERY IMPORTANT TIP!! I see this allllllll the time in my field.. HAVE A BACKUP INTERNET CONNECTION IF YOU RUN YOUR OWN EMAIL SERVER..

If you order a T1 for your business, get a DIFFERENT technology as a backup..

like, if you have 2 T1s, then get a cable circuit that is as fast or faster.. DSL and T1s, if you are in the area, can be subject to the same issues, if there is an issue in the central office.. if you have a different technology as a backup, then if the CO for all the DSL and T1s is down, then chances are your cable circuit is still working.. :)

hope this helps

---

### Post by HermanAB on 2010-07-04
Hmm, use Postfix, Dovecot, Apache, Roundcube/Squirrel, Amavisdnew, Spamassassin, ClamAV if you have time to manage it.  Otherwise, install Citadel - it installs in about 20 minutes, just works and keeps working.

---

### Post by ChurroLoco on 2010-08-09
Thanks guys.  Sorry for the delayed response, but I have been away from civilization for a while.  I did install postfix and it seemed to work perfectly.  I don't know how it is working, but it is.  My drupal and mantis services can now send out username/password reminders.  So far that is all I needed.

Thanks again!

---

### Post by YesWeCan on 2010-08-09
FWIW you can now install 'logcheck' and have all root mail forwarded to you regular email by postfix. I find it handy to receive regular emails from my server notifying me of unusual log activity.

---

