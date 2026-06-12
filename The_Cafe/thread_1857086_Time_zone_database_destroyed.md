---
title: "Time zone database destroyed"
date: 2011-10-09
forum: The Cafe
---

### Post by ratcheer on 2011-10-09
"The internet's authoritative source for time-zone data has been shut  down after the volunteer programmer who maintained it was sued for  copyright infringement by a maker of astrology software."

&#8220;The impact of this is severe for anyone that uses it &#8211; whether via  Java, Unix or some other means,&#8221; Java developer Stephen Colebourne [blogged on Thursday]("http://blog.joda.org/2011/10/today-time-zone-database-was-closed.html").  &#8220;We all owe a debt of gratitude to the database maintainers who have  worked on this for many, many years at zero cost to the industry and for  zero financial gain.&#8221;

[http://www.theregister.co.uk/2011/10/07/unix_time_zone_database_destroyed/](http://www.theregister.co.uk/2011/10/07/unix_time_zone_database_destroyed/)

Tim

---

### Post by earthpigg on 2011-10-09
Being an essential component to the vast majority of the planet's servers at the heart of the Communication Revolution, this is more worthy of tears and candles than anyone or anything else that has passed away in the last few weeks.

RIP.

---

### Post by Dry Lips on 2011-10-09
I don't know if I'm going to laugh or cry. Yikes!

---

### Post by kvvv on 2011-10-09
Wait, so what's gonna happen now? There *needs* to be database that can handle timezones for the millions of devices out there.

---

### Post by ratcheer on 2011-10-09
> **kvvv said:**
> Wait, so what's gonna happen now? There *needs* to be database that can handle timezones for the millions of devices out there.

Exactly. See at the end of the article: “I hereby call on the industry leaders to help sort this out,”  Colebourne wrote. “IBM, Oracle, Apple, Google, RedHat I'm looking at  you.”

This is a very serious issue.

Tim

---

### Post by Bachstelze on 2011-10-09
Hey, the suit was only filed, and it is apparently pretty weak right now, so the RIPs are probably a bit hasty.

---

### Post by dniMretsaM on 2011-10-09
> **Bachstelze said:**
> Hey, the suit was only filed, and it is apparently pretty weak right now, so the RIPs are probably a bit hasty.

But the FTP server IS shut down currently (and probably will remain so at least until the suit is over). Anyway, this is a pretty serious issue in my opinion. The database was in extremely wide use. If thousands of people are suddenly not able to use it, it's going to cause problems.

---

### Post by Bachstelze on 2011-10-09
> **dniMretsaM said:**
> But the FTP server IS shut down currently (and probably will remain so at least until the suit is over). Anyway, this is a pretty serious issue in my opinion. The database was in extremely wide use. If thousands of people are suddenly not able to use it, it's going to cause problems.

There's plenty of places where to get it besides the main FTP, for example

[http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011f.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011f.orig.tar.gz)

It makes sense that he closed the FTP as a precaution, since if the lawsuit is successful, no matter how unlikely that is, the penalty will be larger for every day it stays on. I would be willing to bet that bringing it back up when the issue is settled will be a matter of running a handful of commands.

---

### Post by ratcheer on 2011-10-10
> **Bachstelze said:**
>  I would be willing to bet that bringing it back up when the issue is settled will be a matter of running a handful of commands.

Could be, but I also believe that Olson has maintained it for many years and he may just retire from continuing. Apparently, the legal disposition could take several years. The work Olson does is quite intricate and it would probably be difficult to prepare a replacement, who would have to be someone as dedicated as he has been. Unless one of the big companies decides to assume responsibility.

Tim

---

### Post by mmsmc on 2011-10-10
> **ratcheer said:**
> Could be, but I also believe that Olson has maintained it for many years and he may just retire from continuing. Apparently, the legal disposition could take several years. The work Olson does is quite intricate and it would probably be difficult to prepare a replacement, who would have to be someone as dedicated as he has been. Unless one of the [COLOR=Red]big companies decides to assume responsibility.[/COLOR]

Tim

[COLOR=Black]and of course they will require money to do that, this world is getting to be ridiculous[/COLOR]

---

