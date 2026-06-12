---
title: "sendmail and access.db - relaying denied"
date: 2005-11-23
forum: Server Platforms
---

### Post by drnoelkelly on 2005-11-23
Hi,

I have a Suse 9.1 server and a new Ubuntu 5.10 server.  These are both SMTP relays.

The Suse machine has been running for a couple of years no problem using the /etc/mail/access file to control relaying.  eg:

[email]joe@good.com[/email]     RELAY
[email]ray@good.com[/email]     RELAY
good.com                                     550 Sorry please call us on 123 for help

Using this same config on the new Ubuntu server I get a 'relaying denied' error for joe/ray.


If I change the ubuntu server's access.db to use this:

good.com                                     RELAY

then it relays no problem BUT it relays everyhting for this domain (which I don't want  - I get all the junk addressed to old/non-existant users).


I prove the access.db is up to date and being read like this:

echo '/map access [email]joey@good.com[/email]' | sendmail -bt

which gives me:

ADDRESS TEST MODE (ruleset 3 NOT automatically invoked)
Enter <ruleset> <address>
> map_lookup: access (joe@good.com) returns RELAY (0)


Does anyone have any ideas why the Ubuntu sendmail access setup seems to be different?  Or why it does not follow the material at sendmail.org for the access.db usage?  I have compared the config on both machines and to me they look identical.

MAny thanks for any insight,

Cheers
Noel

---

### Post by Glut on 2005-11-24
I've never seen an access database that accepts only a few users and rejects all, only vice versa. 
So here are my thoughts anyway:
The sendmail documentation only mentions RELAY in concert with domains, would using OK be an acceptable change?
Have you tried using the to: qualifier?
What are the sendmail versions? 
I'd be very interested in hearing how you go with this.

---

### Post by drnoelkelly on 2005-11-25
[QUOTE=Glut]I've never seen an access database that accepts only a few users and rejects all, only vice versa.

Glut - thanks for the reply.  I can absolutely assure you I have this running on a Suse 9.1 machine with Sendmail 8.12.10 - and it works very well :D.  Hence my wanting to replicate the setup to the second MX.


[QUOTE=Glut]The sendmail documentation only mentions RELAY in concert with domains, would using OK be an acceptable change?


Good point about OK actually.  I wonder if a combination of 

[email]joe@domain.com[/email]     OK  (access table)
domain.com             smtp:[111.111.111.111]  (mailer table)

and no mention of domain.com in local-host-names might do it?  I'll give that a try.


[QUOTE=Glut] Have you tried using the to: qualifier?

Yes no joy with that.


[QUOTE=Glut]What are the sendmail versions? 

Ubuntu is Sendmail 8.13.4
Suse is Sendmail 8.12.10

Cheers

---

### Post by drnoelkelly on 2005-11-25
No that OK plus mailertable idea did not work :(

---

### Post by Glut on 2005-11-29
Sorry for the late reply,
AFAIK it should be working. But that doesn't help very much. I think that your best bet would be to post on the sendmail mailing list.

---

