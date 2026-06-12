---
title: "Extra users in passwd file - general question"
date: 2009-05-08
forum: Security
---

### Post by [pl]ice on 2009-05-08
Hello,

Just wondering why do I need users on a ubuntu server like:

irc , to run ircd; even if its not installed ...

proxy
games
news
uucp (what's that one for?)
saned( again i'm not sure what service is that...)
avahi ( DNS daemon ? ...)
polkituser (??)
hplip(??)


These ones come out of the box on the server version and desktop. Just wondering, what are they for, the older versions didn't have them. If they're not 'that' important, eg. irc / games /news/ then i'm happy to disable them...

thanks  :)

---

### Post by FarehamWeather on 2009-05-09
I was wondering the same thing. I think they could be deleted but if any other serivces rely on them (which I dont know) then it would stop the services working correctly. 

I want to delete them aswell but with a live server I dont want to cause problems. Anyone have any ideas?

Surely its a security risk or are they disabled/locked down?

---

### Post by [pl]ice on 2009-05-09
What is Avahi?

Avahi is a system which facilitates service discovery on a local network. This means that you can plug your laptop or computer into a network and instantly be able to view other people who you can chat with, find printers to print to or find files being shared. This kind of technology is already found in Apple MacOS X (branded Rendezvous, Bonjour and sometimes Zeroconf) and is very convenient. Avahi is mainly based on Lennart Poettering's flexmdns mDNS implementation for Linux which has been discontinued in favour of Avahi. 

hplip: Hewlett-Packard's Linux Imaging and Printing software (HPLIP)


gnats: GNU GNATS is a set of tools for tracking bugs reported by users to a central site. It allows problem report management and communication with users via various means. GNATS stores all the information about problem reports in its databases and provides tools for querying, editing, and maintenance of the databases.




list: (List Manager) Mailman is free software for managing electronic mail discussion and e-newsletter lists.

proxy: ?  is it proxy daemon sdbd?

news:x:9:9:news:/var/spool/news:/bin/sh  ??

lp: (lpd) line printer daemon ? correct?

games:  ? dunno, on  a server?


if, i'm not gonna use printer on this server, then i could disable:
avahi,hplip,grants(not sure),irc,lp, games.

How bout
proxy account? is it used to connect to local liblaries as well (like sdbd) or we're talking about something else.
list is a mailman yeh? if i got postfix/dovecot, then i don't need mailman daemon?...

news? not sure what's that for

and games? hahah

thanks guys.

---

