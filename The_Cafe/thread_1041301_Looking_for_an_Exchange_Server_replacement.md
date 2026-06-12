---
title: "Looking for an Exchange Server replacement"
date: 2009-01-16
forum: The Cafe
---

### Post by technosinner on 2009-01-16
Hey-ho!

This is what I'm looking for, quite desperately, and not getting much luck.  I don't have an Exchange server right now, but I'm looking for something to what it's meant to do.

I already have an IMAP server setup and it works very well.  However I'm somewhat stuck with Outlook because I use a smartphone that's under Windows Mobile, and getting anything else than Outlook/Exchange with those things is a crossbreed-female.  Also I'd like to be able to sync all my calendars, contacts, etc with all my machines and phone but I fail to understand how to work it directly through IMAP.

So, in reality, I'd like a server backend that could support email, calendar, task and contact syncing with client machines AND smartphones.

I've found numerous open source server backends like Chandler and Zimbra but I've rummaged through the docs and none seem to support mobile devices, or do only through Gmail... if I wanted to use Gmail, I'd do just that.

Anyway, any suggestions would be greatly appreciated!
Thanks

~ts

---

### Post by amauk on 2009-01-16
Since MS was required to open up their server side protocols, there's been a few open source drop-in replacements for MS Exchange
and by drop-in replacement, meaning it uses the exact same protocols (MAPI) so clients "see" it as an exchange server

One dropin replacement is Postpath, which was recently bought by Cisco

Other mail, contact & calendaring systems do the same thing as exchange, but use other protocols (IMAP + LDAP + CalDav)

- Zimbra
- Citadel
- Scalix

It's up to you whether you want to use open standards, or MS's MAPI protocol
there's pros and cons to each

---

### Post by technosinner on 2009-01-16
Thanks amauk.  I'd much rather use open standards of course, but again my fear is that the mobile device won't be able to sync...  but if I understand correctly, if I use let's say Zimbra, it should let the device connect to it 'as if' it was connecting through MAPI?  Or did you mean only Postpath could do this?

Thanks, and sorry for the noobism, I'm only at my second cup of coffee today ;)

---

### Post by Carl Hamlin on 2009-01-16
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I've been using Citadel, and it's working great for me.

Caveat - many cable providers want you to route outgoing email through their servers, and enforce this policy by placing their IP ranges on the PBL list. If you want to get around this restriction, you might have to switch to DSL, which is usually friendlier.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklw2KAACgkQyLm4ydrABvd+uQCgye5Upie4zhJN5FUkb8KyUXoS
myAAoNrB7nRSL8qi83tX42DRpPNe1lGO
=/NbT
-----END PGP SIGNATURE-----

---

### Post by amauk on 2009-01-16
postpath is the only MAPI server I know of by name
but I'm sure there's others
the others I mentioned use IMAP+LDAP+CalDav

---

### Post by HermanAB on 2009-01-16
Citadel with the Bynari plugin for Outlook makes a good replacement - users won't know that they are not using Exchange.  Citadel is highly scalable, efficient and zero maintenance.  You can literally replace dozens of Exchange servers with a single Citadel server.

See this:
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

I run Citadel on my Eee PC 701 as a Demo:
[http://aeronetworks.ca/eeepc-mdv-howto.html](http://aeronetworks.ca/eeepc-mdv-howto.html)

Cheers,

Herman

---

### Post by technosinner on 2009-01-17
Thanks Herman.

I'll add a little complexity to this question: I realized I might not be able to go deep enough on my server to install (f.ex.) Citadelle.  I don't have root access to the server that hosts my IMAP server.  However I do have another server I have full access to.  Could I, you think, install Citadelle on this server while using the mail server from the outside?  In other words have two seperate servers communicating?

Thanks again

---

### Post by green91 on 2009-01-18
Im also looking for an exchange alternative. My only needs are interoffice messaging (local mail) and the ability to sync calenders. The catch is whatever solution i use must be outlook compatible.

---

### Post by veloce on 2009-01-25
I have been playing with Funambol ([www.funambol.com](www.funambol.com)).

This may meet the requirement some of you are asking for. (e.g. technosinner)

I have it syncing calendars & contacts etc between Thunderbird and Outlook both within the work network and externally.

I have yet to test the "push email" functionality.

Paired with an imap mail system it provides the majority of what I want from Exchange Server.  (The key thing missing is a Shared Calendar.)

Unfortunately, in NZ, Blackberries are locked down so they cannot communicate directly over the internet - this prevents me using funambol as a BES replacement.

---

### Post by HermanAB on 2009-01-26
Citadel is very efficient.  I have had it running on an Asus Eee PC 701 ([http://aeronetworks.ca/eeepc-mdv-howto.html](http://aeronetworks.ca/eeepc-mdv-howto.html))

Citadel is highly configurable and there are multiple ways to forward mail from one server to another.  However, it is best used as a complete standalone machine, since it will do everything you can possibly need.

Cheers,

Herman

---

