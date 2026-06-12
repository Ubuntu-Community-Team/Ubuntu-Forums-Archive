---
title: "Ubuntu for local mail with ISP"
date: 2006-07-15
forum: Server Platforms
---

### Post by viking325i on 2006-07-15
Hi,

I've been looking thru readmes for mail servers but cant really find one to use with an ISP.

I'd like to have the server grab mail from ISP accounts and dump them to users, it doesnt need to sort, just grab one account worth and put it all to one user. Fetchmail seems to do that reasonably well, and I managed to get that working. What I'd like to do though is then serve it up via IMAP to the local network, and them smtp back out from the server to the ISP and then out onto the web. I cant get my head around any of the IMAP servers really, what are your thoughts on packages to use and pages to read?

---

### Post by bikeboy on 2006-07-15
I'm not too got at the details but I managed to get this setup happening. Fetchmail > Procmail (filter) > Spamassassin > Sendmail > Dovecot Pop3.
I would use Qmail or Postfix as they're a bit smaller and faster but I had trouble with Postfix while Sendmail worked with basically no config.

Dovecot has an IMAP version and seemed very easy to setup, so perhaps try that. Sendmail is the bit that delivers the ISP mail to a user on my machine after fetchmail gets it from the ISP's server, then Dovecot allows me to download the filtered mail in Thunderbird/Outlook on the desktops.

---

### Post by viking325i on 2006-07-16
installed dovecot, but I would like it to use the local unix database for users and passwords. Can you tell me what I need to put? I'm configuring it via webmin, but at set up with the local unix passwords and users I get the error "dovecotError: Error in configuration file /etc/dovecot/dovecot.conf line 647: Unknown setting: userdb"

What do I need to put for the userdb setting to use the local users?

---

### Post by bikeboy on 2006-07-16
I wish I could help but so far that problem hasn't presented itself to me, I'm using a very simple setup though.

If you don't get an answer here you could try the dovecot irc channel on freenode if you know what that means.

---

