---
title: "Mail server question"
date: 2006-09-29
forum: Server Platforms
---

### Post by xtek on 2006-09-29
Over the past few years I have aquired many email accounts, and more and more I find myself hating to check email because of spam.  Normally I would just close the account and get a new one, but now I have a problem that not everyone keeps up to date with my contact information.  I'm looking to try and put all that email in one place.

What I need is a setup that will provide the following.

[LIST]
[*]Check POP accounts  (fetchmail)
[*]MTA (Postfix)
[*]Spam checking (spamassassin)
[*]Anti-Virus (clamav(?))
[*]POP Server for serving local email to outside clients (?)
[*]Possible webmail (squirrelmail)
[*]Check Gmail account (?)
[*]A little direction on how to put it all together
[*]Use DynDNS service for ability to check from anywhere with webmail
[/LIST]

I've read many howto's in an attempt to piece together the above abilities, and have either ran into the problem where the different ways interfere with each other or will not work without a lot of tweaking because of distribution differences.

I am a linux newb, but I'm willing and eager to learn. Any suggestions on where to look, or changes to the setup will be much appreciated.

---

### Post by kidders on 2006-09-30
Hi there,

I have a setup quite similar to what you describe. Originally, I had it running on Gentoo, but I was pleasantly surprised at how much more quickly I got it off the ground with Ubuntu :-)

Since you're new to Linux, you should take things one step at a time. First off, install/configure Postfix. You should manually check that your configuration doesn't have massive security holes in it, by making sure that mail from non-local IPs to non-local addresses is refused, for example. I also suggest getting Postfix to store mail in the "maildir" format.

I would very strongly recommend using IMAP rather than POP. I use Courier-IMAP & Courier-IMAP-SSL for this (but that doesn't mean you have to too!). POP is an archaism from the internet's early days that simply doesn't cut it in the modern world. So, step two might be to install an IMAP server that either uses SSL for external connections only, or just uses it all the time.

Once that's working, it's time for webmail. SquirrelMail is fine ... it's a bit basic, but it's a snap to set up, and is very lightweight. A (far more advanced) alternative is Horde ... save playing with that for later!

Now you could install Fetchmail. Gmail addresses can be checked over POP, but try not to check them to regularly. Gmail seems to temporarily blacklist people who overload their servers.

To keep my dynDNS up-to-date, I use ddclient. If you want to, you can tweak your network configuration scripts to automatically sync the dynDNS servers to your new IP every time you bring up your external internet connection. Let me know if you intend to use your Postfix MTA to accept mail from remote MTAs though... there are potential problems with doing this.

From there, virus and spam protection is much more straightforward to set up. There are basically two strategies for setting these up ... the easy one and the safe one. Many HOWTOs fail to make the reasons behind the choice they're describing clear, which could be the source of your confusion. Basically, when dealing with spam & viruses, many people find it ridiculous to do so in a way that would leave your MTA open to DoS attacks.

The two basic options are (a) to have postfix pipe your mail through the virus & spam detectors and (b) to run multiple Postfixes in parallel. The latter is considerably safer, because of the degree to which the various stages of the mail delivery process are asynchronised. In either case, SpamAssassin and ClamAV are perfectly good choices, that are very widely used :-)

I'd be happy to offer more in-depth, detailed help with any part of the setup. Once you're done, there is no reason in the world why you can't have a high-performance, centralised source for all your email, with secure webmail & IMAP interfaces for easy external access.

---

### Post by xtek on 2006-09-30
Wow!!  /me bows in reverence and yells "All hail the king!"

I ended up doing some reading via another website ([http://workaround.org/articles/ispmail-sarge/#install_packages](http://workaround.org/articles/ispmail-sarge/#install_packages)) and followed the directions there.  Everything seems to work except for the webmail interface, and checking the email from an outside source (can't authenticate on either one).

I have also tried from another source on a different site [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) that seemed to work ok but I had the same problem with logging in, and the webserver part wasn't secured.

> Let me know if you intend to use your Postfix MTA to accept mail from remote MTAs though... there are potential problems with doing this.

Do you mean accepting mail from ourside sources? If someone sends an email to [email]me@mydomain.com[/email], it will be accepted by my machine?  If that is the case, I don't think that I want that quite yet.

I think the biggest problem is there isn't alot of reasoning behind the choices that the HOWTO's use when it comes to software.  The other is that there are alot of different packages that look the same but are different, e.g. mysql4 mysql5, and I don't know the difference.

> 
I'd be happy to offer more in-depth, detailed help with any part of the setup. 

I would greatly appreciate the help.  If there is anything that you would like to look at I would be happy to post code snippets to figure out the problems.

---

### Post by kidders on 2006-10-01
Oic, you went for a MySQL user database. The logic behind doing that has always escaped me. The smartest solution in my experience is to use a back-end that is well-known and commonly used (such as LDAP), so that more applications (including your operating system itself) can talk with it. On my network, I am running a Samba (Windows) domain, mail server, etc., all authenticating against the same source as Linux itself. I found LDAP the best way to achieve this.

To answer your specific question, MySQL 4 and MySQL 5 are the same but different. They're both the same application, but version 5 almost behaves more like Oracle than MySQL! There are huge numbers of SQL queries that will work in v4 and not in v5, and vice versa ... so you really need to use the one your other software choices recommend. (Of course, if it were me, I wouldn't be using MySQL at all, but that's down to personal choice, really.)

Anyhow, your problems are that you can't access the mail server remotely. This may be for a number of reasons.

[LIST]
[*]Your ISP is blocking you ... happens a lot in the US for some reason.
[*]You're using a router that doesn't know where to send incoming packets.
[*]Your servers aren't listening on externally accessible network interfaces.
[*]You have a firewall that hasn't been tweaked to let incoming traffic past.
[/LIST]

Depending on which one you've fallen victim to, the solution is different :-(

If you post your final software choices (Apache/Postfix/Courier/SquirrelMail/MySQL/OpenLDAP/FetchMail/etc.) and maybe something about how your mail server connects to the internet, I could give you more precise help.

When it comes to your software choices, don't rush a decision based on what looks easy. There are two really important factors:

[LIST]
[*]Is your choice (in the combination you've chosen) commonly used? If so, you'll have a wealth of troubleshooting info to hand if/when something goes pear-shaped.
[*]Is your choice extensible? In other words, should you decide in a few months that you want your sexy new mail server to do something new, will it be able for it?
[/LIST]

I'll happily rant at length about the pros and cons of a particular program if you like :???: but my opinion's as good as the next one, really!

---

### Post by xtek on 2006-10-09
Bah I hate vacations, no time to check up on posts.  :0

Hrmm.  It seems that there is alot more involved than what I bargined for in doing this.  Maybe it's time that I started over from the beginning.  I'll do a little reading on LDAP and see if that's the way to go with what I want the server to do.

I do appreciate your help.

---

