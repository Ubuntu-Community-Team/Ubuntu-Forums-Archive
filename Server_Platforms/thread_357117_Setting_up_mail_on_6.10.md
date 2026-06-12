---
title: "Setting up mail on 6.10"
date: 2007-02-09
forum: Server Platforms
---

### Post by scrupul0us on 2007-02-09
Ive been racking my brains trying to get mail working on my 6.10 setup

one of the things i need is sendmail, but eventhough i install it, when i try to use mail() within php nothing happens... mail is never sent... id also like to be able to manage my .com's mail on the server and have some form of a squirrelmail setup as well... when i tried using squirrelmail and logged in i got errors in every pane about not finding stuff... so ive reformatted and just installed:

apache 2
php 5.2
mysql
phpmyadmin

can someone please help me or point me in the direction of a good tutorial?

i was following the guide on how-to-forge for the "ultimate setup" but ive steered away freom it a little bit in light on some customization...

anyways... ive never handled mail before on a linux server so all the help is appreciated!

~Brian

---

### Post by elst on 2007-02-10
Sendmail is not very nice to use, and I can't think of any reason to recommend it these days. The supported SMTP server for Ubuntu is Postfix, which is generally popular and quite pleasant, going by my limited experience with it.

The trick to setting up mail services is to take each component one at a time, and get each one working before you go on to the next:

DNS (add MX records for SMTP server) > SMTP to local mailboxes (Postfix or Exim) > IMAP to access mail remotely (Dovecot) > Webmail interface for IMAP (SquirrelMail) > Spam and AV filtering to clean traffic (SpamAssassin, ClamAV)

It's quite an involved process, and I have to add my usual caveat - configuring and maintaining all this in-house rather than going with a provider probably isn't cost-effective for a small number of accounts. (I don't work for an email provider, I just used to be an in-house email maintainer).

---

### Post by scrupul0us on 2007-02-11
well regardless of practicality, im about learning... and right now im in the corner with the cap on... its one thing to install this stuff and another to actually configure it an get it working...

it perplexes me... for how much documentation there seems to be for everything on the web, something like this isnt very well documented... ive spend countless hours searching only to find that im brought to dead ends and ending up reformatting just to start fresh (luckily ubuntu installs fast)

now, u say sendmail isnt nice to use, yet PHP is setup to use that for its mail services... how do i adapt to using postfix instead?

as much as I HATE to say it, for things ive never used/touched/experienced i often find "hand holding" invaluable... once i get stuff working im able to toy with it and learn even more

that being said... any useful resources in this area would be greatly appreciate

---

### Post by chrisfay on 2007-02-11
Postfix is definately more user friendly, especially in comparison to Sendmail.  

> now, u say sendmail isnt nice to use, yet PHP is setup to use that for its mail services... how do i adapt to using postfix instead?

Not sure what you mean here, PHP does not require Sendmail; the language does not require any specific package be it Postfix, Sendmail, Exim etc nor does it require any custom configuration when you've made your choice.  You're probably thinking of the binary application located on the server (all unix/linux distros have it located at /usr/sbin/sendmail) that sends out mail. The confusing part of this is that Sendmail is obviously also an MTA and very well might be the MTA behind the SMTP connection.


> it perplexes me... for how much documentation there seems to be for everything on the web, something like this isnt very well documented... ive spend countless hours searching only to find that im brought to dead ends and ending up reformatting just to start fresh (luckily ubuntu installs fast)

There is actually quite a bit of documentation around for doing this. Start at [http://postfix.org](http://postfix.org) (if you plan to use that MTA) and get a feel for the directives. There are a bunch of how-to's noted directly on the site. Using Google I pulled up like 20 by typing 'how to install postfix ubuntu'. They're all over the place.

If you want to play around with Postfix virtual users and virtual domains, there's probably more documentation on doing that than just a standard install.  

Configuring a full blown mail system on Linux is no small task, it took me a couple weeks to have a complete virtual MySQL driven mail system with webmail in the format I wanted. I had to cherry pick information from different documents, create db scripts and whatever else to get what I wanted, but the benefit was a great understanding of how it all works. Unfortunately my ISP crushed it once they found all the services I was running. :)

---

### Post by elst on 2007-02-11
I haven't seen a really good document that takes the reader though the whole process (I'd love to be able to link to one). Postfix and Exim have pretty good documentation themselves, but an SMTP service is only one part of it. The Bongo project (formerly Hula) is developing a complete system that includes all of the pieces, but they won't have a beta for a while yet.

---

