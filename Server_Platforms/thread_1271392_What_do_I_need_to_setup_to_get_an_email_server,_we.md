---
title: "What do I need to setup to get an email server, webmail + bonus"
date: 2009-09-20
forum: Server Platforms
---

### Post by SoftwareExplorer on 2009-09-20
Hi. I have done sudo tasksel install mail-server. I already have the LAMP task installed. I have a website that works from behind my router's NAT, and a dynamic dns service pointing to my router. I know about port forwarding, so I just need to know what ports for that part. So, what configuration do I have to do to set up an email server with POP3, IMAP and smtp? Also, once I get that, I'd like to try setting up webmail as a way to check the email on the accounts. 

Thank you very much in advance.

---

### Post by tlarkin on 2009-09-20
You need to set up some sort of database that will hold the user information, email account, password for authentication and so forth.

Do you have a product in mind you are looking to set up?

---

### Post by SoftwareExplorer on 2009-09-20
> **tlarkin said:**
> You need to set up some sort of database that will hold the user information, email account, password for authentication and so forth.

Do you have a product in mind you are looking to set up?

Does Mysql work? I already have the LAMP stack installed. For webmail, the ubuntu wiki mentioned OpenWebmail and Squirrel Mail. (Or something like that.)

---

### Post by tlarkin on 2009-09-20
> **SoftwareExplorer said:**
> Does Mysql work? I already have the LAMP stack installed. For webmail, the ubuntu wiki mentioned OpenWebmail and Squirrel Mail. (Or something like that.)

Yes, MySQL will work, or if the product has their own database you can use the in-house one.  Some of them support LDAP as well.

The only mail server I ever fussed with that wasn't Exchange, was this product here:

[http://www.dovecot.org/](http://www.dovecot.org/)

I don't have much experience with it, but if I recall it wasn't that hard to set up.  I just pissed off my ISP when they saw email traffic coming from a box I had on my DMZ and not behind NAT.  So, I turned it off, but I was only messing with it for test purposes.

---

### Post by SoftwareExplorer on 2009-09-20
> **tlarkin said:**
> Yes, MySQL will work, or if the product has their own database you can use the in-house one.  Some of them support LDAP as well.

The only mail server I ever fussed with that wasn't Exchange, was this product here:

[http://www.dovecot.org/](http://www.dovecot.org/)
I think the ubuntu mail-tasksel install uses dovecott and postfix, because when i did the tasksel thing, it said it was installing those. I just need to know what I need to set up for it to work. (I'm thinking accounts, domain name, etc)
> **tlarkin said:**
> I don't have much experience with it, but if I recall it wasn't that hard to set up.  I just pissed off my ISP when they saw email traffic coming from a box I had on my DMZ and not behind NAT.  So, I turned it off, but I was only messing with it for test purposes.
Now that would drive me nuts. What, are they afraid you would compete with their email service?

---

### Post by tlarkin on 2009-09-20
dovecot supports LDAP, that can be your database for users.  If you are using some sort of web based CMS (like drupal) they typically have their own database built into the CMS, and it is almost always MySQL.

You are going to need static IPs and DNS working.  Other than that, the install should be pretty straight forward.  Check out the tech documents on dovecot.

---

### Post by SoftwareExplorer on 2009-09-20
> **tlarkin said:**
> dovecot supports LDAP, that can be your database for users.  If you are using some sort of web based CMS (like drupal) they typically have their own database built into the CMS, and it is almost always MySQL.

You are going to need static IPs and DNS working.  Other than that, the install should be pretty straight forward.  Check out the tech documents on dovecot.

Do I really need a static IP? I got Dynamic DNS working, so my server would always be available at a domain name. I was thinking that I would have better luck with instructions that set up what ever needs to be changed from the ubuntu defaults, instead of the dovecot project's defaults.

---

### Post by tlarkin on 2009-09-20
> **SoftwareExplorer said:**
> Do I really need a static IP? I got Dynamic DNS working, so my server would always be available at a domain name. I was thinking that I would have better luck with instructions that set up what ever needs to be changed from the ubuntu defaults, instead of the dovecot project's defaults.

As long as DNS resolves, no I guess you don't *need* a static IP.  I just think it is a "best practice" to have all your servers with static IPs.

---

### Post by SoftwareExplorer on 2009-09-20
So, dovecott is talking about how to compile and stuff like that. Is there a howto (or instructions from someone) about howto set up a mail server? I just want to get a account working on it, figure out what ports to forward, and then, if I get that well enough, try to set up webmail. Any ubuntu specific help?

---

### Post by tlarkin on 2009-09-20
Ubuntu specific?  Other than the package manager I used to install it, no everything else is pretty standard.  As for ports, you can use standard ports that are typically used for email servers, but you will set that in the server config, not in the OS config.

here is a list of known ports and what they are typically assigned to.

[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

---

### Post by jonallport on 2009-09-21
If you want a complete mail server with webmail then you can't do much better than [Zimbra ]("http://www.zimbra.com")

---

### Post by badger_fruit on 2009-09-21
> **jonallport said:**
> If you want a complete mail server with webmail then you can't do much better than [Zimbra ]("http://www.zimbra.com")

Or Axigen [www.axigen.com](www.axigen.com)
For email you'll need to forward ports 110 and 25 to the email server.

Openexchange is also meant to be very rich in features but not sure as never used but a friend of mine keeps bleating on about it!  Oh I don't think it's free either.

[http://www.open-xchange.com/](http://www.open-xchange.com/)

---

### Post by SoftwareExplorer on 2009-09-25
> **tlarkin said:**
> Ubuntu specific?  Other than the package manager I used to install it, no everything else is pretty standard.  As for ports, you can use standard ports that are typically used for email servers, but you will set that in the server config, not in the OS config.

here is a list of known ports and what they are typically assigned to.

[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

I'm sorry if it seems I don't want to read the manual. It's just that I tried reading the ubuntu wiki and got lost. I couldn't even tell what pages I needed to actually do, and even when I did try to do them I got stuck. Not only that, it also sounded like the wiki pages were last updated for hardy, and I'm on jaunty, so I'm thinking I'll make a very messy configuration if I ever get it to work.

I've forwarded port 25.

Also, since you recommended that I check out the dovecott website, I tried their quick configuration page and got lost on setting up the data base. 

I'd like just to focus on getting postfix and dovecott to be configured to work together.

To all those suggesting other things, I'd prefer to stick with ubuntu default mail stack, if possible, because I figure the programs are more likely to be mostly configured to work together.

---

### Post by SoftwareExplorer on 2009-09-25
By the way, I'll probably be checking the mail on this install from localhost at first, so I don't need to forward things like IMAP or POP3 yet, right?

---

### Post by tlarkin on 2009-09-25
My HD crashed last week and I had to replace it.  It was actual hardware failure.  

The newest version of virtual box crashes constantly on my Windows machine.  If I can get it back up and running I will take a stab at setting up a mail server on my VM, and see if I can help you.  It has been a while since I have tried to set up one on a Linux box though so I can't tell you what to do off the top of my head.

The last few years I have only ran Linux as a VM really.

---

### Post by cariboo on 2009-09-26
I would suggest you have a look at [Citadel]("http://www.citadel.org/doku.php"), it is in the repositories, as of Jaunty(9.04)

You may have to get a static ip as many email servers do a reverse dns lookup, and if they can't find your ip address, your email may be sent to a black hole.

If you don't want to get a static ip address, you can use google, here is a [howto]("http://www.likoma.com/using-google-apps-and-gmail-for-youyourdomaincom/").

---

### Post by jdakhayman on 2009-09-26
I have a mail server setup using this tutorial: [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04)


My server also uses no-ip.org for DDNS. So no issues there having to use a static ip address. Just be sure your spf records and mx record are set right.

It uses squirrelmail for webmail access. Both imap and pop are installed if your users what to use something other then a webmail client. 

I have been very happy with this setup.

jda

---

### Post by SoftwareExplorer on 2009-09-27
It sounds like it should be really easy to set up dovecot and postfix by installing the dovecot-postfix package. 

[Ubuntu server team blog:]("http://ubuntuserver.wordpress.com/2009/02/13/an-improved-mail-server-stack-in-jaunty-dovecot-and-postfix-integration/")
[QUOTE=Ubuntu Server Team Blog]So if you&#8217;re interested in a integrated mail stack providing a combination of smtp, imap, pop3 and managesieve services the Jaunty Jackalope will suit you. Have a look at it, test it and with one simple command:

    apt-get install dovecot-postfix[/QUOTE]
They make it sound so easy! If everything is already configured when you install that package, then it must just be a matter of knowing the right settings to connect with a email client, right?

---

### Post by SoftwareExplorer on 2009-09-28
> **jdakhayman said:**
> I have a mail server setup using this tutorial: [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04)

OK, I looked at it, I might try it tomorrow if I have enough time.
> **jdakhayman said:**
> My server also uses no-ip.org for DDNS. So no issues there having to use a static ip address. Just be sure your spf records and mx record are set right.
I think I got the mx part set up. I read about spf records, and I don't think afraid.org supports them, unless you don't set them up at the same place as you would an A, CNAME, or MX record, are they necessary?
> **jdakhayman said:**
> It uses squirrelmail for webmail access. Both imap and pop are installed if your users what to use something other then a webmail client. 

I did some reading in the ubuntu wiki about squirrel mail, and even tried setting it up. It seems really easy to set up, but, of course, it didn't work because I didn't know what setting to set it to. But I'm not to worried about it, it's about as hard to set up as a mail client.

---

### Post by nandemonai on 2009-09-29
[https://help.ubuntu.com/8.04/serverguide/C/dovecot-server.html](https://help.ubuntu.com/8.04/serverguide/C/dovecot-server.html)

---

### Post by SoftwareExplorer on 2009-10-05
Thanks nandemonai, I got Thunderbird to sync via imap with the server. I can send emails to myself. The problem is that I can't seem to receive email or send it to other domains. I have port 25 forwarded because if I understand correctly that is what port mail transfer happens on. What can I do to trouble shoot this problem?

---

### Post by SoftwareExplorer on 2009-10-20
I got it working. My ISP was blocking port 25 outbound, but they let me use smarthost with their email server, so it works now.

So, a summary of what I did

installed dovecot-postfix package
forwarded port 25
connected for with an email client on port 25 and the default imap port
set relay= smtp.eoni.com

I did some other tweaks, but I don't think they were necessary.

Thanks Everyone!

---

