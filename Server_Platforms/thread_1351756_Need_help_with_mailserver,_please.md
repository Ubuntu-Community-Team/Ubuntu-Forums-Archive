---
title: "Need help with mailserver, please"
date: 2009-12-10
forum: Server Platforms
---

### Post by Jorsher on 2009-12-10
Hi guys,

I have successfully set up a LAMP without a problem, however setting it up to handle mail also is causing me problems.

The setup is multiple domains hosted by 1and1.com and forwarded to the IP address of my ovh.co.uk dedicated server.  The server has Ubuntu 9.10 Server installed.  I'm using the Drupal CMS to manage the sites and all the sites are accessible.

I used this guide:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

It is very VERY thorough and I'm very appreciative of the person that wrote it, however I've checked my configuration with the guide three times, everything matches (except obvious things like domains), and something is still wrong.  When I send an email it says the recipient doesn't exist, even when I send it from the server itself, and the recipient obviously exists.  After getting frustrated, I backed up the sites and reformatted the server to start from scratch.

I would like to be able to do the following:
- Send/receive/store email on my server from my domains

Some sort of web-administration for adding email accounts for the domains would be nice, however I'm comfortable with manually adding them into the MySQL database.

Webmail would be nice, but again isn't necessary.

Spam/virus protection isn't really necessary, as only a few people will be sending/receiving email from this server.

Could someone point me to a simple guide to meet the minimum send/receive/store email requirement, possibly with the other optional requests?

I would be more than willing to post back a simple guide for others to use.

Thanks

---

### Post by JonRohan on 2009-12-10
Have a good read of the postfix guides on the ubuntu wiki

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

I'd recommend postfix as your mta, dovecot (to connect via IMAP) and webmin for remote administration. 

IMO you don't need to store emails in a database if you are a low mail user. 

Postfix will allow you to send and receive pretty much by default. It is a matter of then adding virtual domains: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

I'd recommend testing on a vm at home first to avoid destorying a production server. :)

---

### Post by volkswagner on 2009-12-11
The Flurdy docs how-to does work, on 8.04.  As you know it is a very complex setup, with a lot of room for error.  What I don't know is if it works on 9.10.  One of the biggest challenges is finding up to date instructions for your particular install.

I have yet to try, but I may next time install Zimbra or Citadel as folks here highly recommend it for a quick setup.  If you are able to do a fresh install or try a VM, either of these packages may be the way to go.

PS:  I have spend days on the Flurdy install.....The only thing I was not able to accomplish is saslauth for relaying via my isp smtp server as I am on a static ip.  Again, there are so many ways to skin a cat, but sometimes it may be best to go the "butcher" for pre packaged (Citadel/Zimbra).

---

### Post by Jorsher on 2009-12-11
Thanks you two.

I hate to ask this sort of question because I know it's one many have asked and doesn't really have a simple answer.

Thanks JonRohan, I will check those links out.  And yes, I wish I had set it up at home first before trying it on the production server.  Fortunately, the site isn't "live" and accepting orders yet, so starting over was nothing more than backing up the site and database.

Volkswagoner - it definitely is a complex setup.  I just realized I'm on 9.04 and not 9.10, but yeah that may have something to do with it?  It could be so many things I just got frustrated and decided to start fresh.  I will check out Zimbra and Citadel.

As mentioned, it's not going to be a heavily-trafficked email system, and typically I prefer to work harder for a better performing system (thus usually stray away from prepackaged solutions), but I think I'll check into a prepackaged solution this time ;)

Hopefully, in the future, there will be a more streamlined installation for simple setups like my own.  I never expected setting up a system to handle email would be so much more difficult than setting up a webserver.

---

