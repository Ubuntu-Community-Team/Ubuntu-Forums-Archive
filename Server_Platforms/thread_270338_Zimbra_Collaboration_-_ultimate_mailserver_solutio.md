---
title: "Zimbra Collaboration - ultimate mailserver solution"
date: 2006-10-03
forum: Server Platforms
---

### Post by daimer77 on 2006-10-03
Hello there.

Does anyone here has any experience with the Zimbra mailserver solution: [www.zimbra.com](www.zimbra.com).

It's free, it's opensource and I think so far it is the best alternative to Microsoft Exchange ever !

Is it possible to apt-get the zimbra package or is anybody already working on it ?

I guess this software could also help making Ubuntu even more popular as Zimbra outnumber Microsoft Exchange, and hence eliminate the need for it.

Any links to "Zimbra on Ubuntu" higly appreciated.

Have a nice day folks, 

greeting from an ubuntu fan, Daniel Mersebak

---

### Post by paul.maddox on 2006-10-03
Zimbra have recently created packages for ubuntu for the Open Source version. You can download them from Zimbra's website.

To install it's just a case running the install.sh file.


They don't currently do a ubuntu version of the Network Edition which is a shame.

---

### Post by baastie on 2006-10-03
Hi,

As already mentioned there are ubuntu packages available
from the zimbra website.

I have it running at an customers site ( the oss version ). It's not running on ubuntu but on Opensuse 10 and it rock solid, does it's job and the features are great for a linux mailserver solution.

Cheers

---

### Post by btdown on 2006-10-04
I have been trying for three days to get it working on Ubuntu. It installs fine except for the dreaded "256" LDAP error once you apply the configuration. If someone were to do a complete installation howto for Ubuntu, I'd be eternally grateful.

Thanks!
BT

---

### Post by hkgonra on 2006-10-05
Have you looked around in the zimbra forums ? I am not trying to run you off from here as this is a great community but you might find better answers to zimbra specific questions there.

---

### Post by btdown on 2006-10-05
I've done a lot of searching on the Zimbra board there are a ton of issues reported related to the errors I'm experiencing (It seems like 90% of the install problems are related to ldap). Being that I'm running Edgy may contribute to the problems. I think I'll wait for their next release and try it again. It looks to be a great product, it just needs a few kinks worked out. 


BT

---

### Post by andlinux21 on 2006-10-05
I never thought about setting up a mail server but that Zimbra looks really sweet.  I would love to try that out.

---

### Post by daimer77 on 2006-10-06
I have personally suceeded installing on debain 3.1, but never on Ubuntu. although I have only tried once I also face some errors regarding LDAP issues. Well I will collect my experiences and discoveries in a textfile in order to start an unofficial documentation for Ubuntu.

As people dump info regarding installations and management of Zimbra mailserver I will try to catch it up.

Best regards, Daniel Mersebak

---

### Post by btdown on 2006-10-06
Daniel,

That would be very much appreciated!
BT

---

### Post by Macchi on 2006-10-06
I am also crazy to get some good and stable groupware running on an Ubuntu server. 

The demand for small business servers with groupware and an exchange server is increasing a lot. The big market leader is lowering prices for their licenses at a level that it is difficult to motivate the effort to set up and maintain such servers with open software. This is sad but true.

I hope to see a stable release for Zimbra. I have previoulsy tried Conflux, Hula, and OpenGroupware, but did not dare yet to install the Open version of OpenXchange. I will also investigate Scalix but their installer for Ubuntu was flagged as "very alpha". It is risky to be on this open edge of the market.

---

### Post by daimer77 on 2006-10-19
Check this link, another guy already kindly posted his experiences with Dapper and Zimbra mailserver: 
[http://www.zimbra.com/forums/showthread.php?p=27669#post27669](http://www.zimbra.com/forums/showthread.php?p=27669#post27669)

Now if we should integrate this into the official ubuntu documentation, how can we do this ?

Best regards, Daniel Mersebak

---

### Post by dickmorrell on 2007-02-26
Well if I can help let me know...

Richard

---

Dick Morrell, co-author / founder of SmoothWall, senior architect - Zimbra - [email]richard@zimbra.com[/email]

---

### Post by ViAo on 2007-03-07
> **daimer77 said:**
> Check this link, another guy already kindly posted his experiences with Dapper and Zimbra mailserver: 
[http://www.zimbra.com/forums/showthread.php?p=27669#post27669](http://www.zimbra.com/forums/showthread.php?p=27669#post27669)

Now if we should integrate this into the official ubuntu documentation, how can we do this ?

Best regards, Daniel Mersebak
Good find daimer77 


I ahve not had any success getting this running on my dapper machine yet but with this printed and in my pocket i hope to get it up and running tonight.

my current win2k3 / exchange server is dying a slow and painful death and i am looking forward to replacing with this linux box.

---

### Post by druhboruch on 2007-03-07
I have been running/testing Zimbra on Edgy since last November.
In order to install it I only had to update shell link.  This is a common problem with Ubuntu.
There is even Ubuntu howto in Zimbra forums.

I had no problems with setup, but I found data import to be very frustrating and time consuming.

I documented my migration woes in Zimbra forum.

I still don't have enough guts to deploy it at the client, because there is no backup and I found the server a bit too slow.

Zimbra is under heavy development and I am sure to take a plunge one fine day.  In the meantime I recommend sticking with Dovecot and LDAP.  There are very fine PHP web frontends available.

---

### Post by primski on 2007-03-08
[Here's](http://www.tickus.com/?q=node/15) one guide for zimbra on edgy installation. It's very simple and you can get zimbra up and running in no-time ;)

Zimbra truly is a great mailing solution, I am using it on 2 different environments, both production use, both opensource edition, though thinking of purchasing network edition.

Its stable as it gets and if you have a decent machine in terms of hardware, it runs very nice too, despite the fact it runs on java.

greetz,
P

---

