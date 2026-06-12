---
title: "Long-term maintenance of a Dapper server (ie. what does &quot;LTS&quot; really mean?)"
date: 2006-05-29
forum: Server Platforms
---

### Post by mcbane on 2006-05-29
Hello everyone,

I just need a clarification. Does the 3/5-year LTS offered on Dapper refer to the paid support only, or does that mean that the package/security updates will be offered on Dapper repos for the full 5 year-period?

Or, to ask it differently, if I leave my Dapper LAMP server to update itself from repos and do not "dist-upgrade" in the meantime, how long will it stay up to date in terms of apache/MySQL/PHP versions and security updates?

Thanks for reading, I really need to know as I need a long-term solution to keep my departmental server as up to date as possible, for as long as possible (while trying to prevent upgrading the distro itself to avoid breakages). Any suggestions in terms of Ubuntu, or even other distros, would be helpful.

Thanks!

---

### Post by eentonig on 2006-05-29
doing the "apt-get update && apt-get upgrade" during five years would keep your system up to date concerning installed applications and security updates. While maintaining your base distro. No cost involved.

If you encounter a bug during these five years, I suppose *they* would do their best to solve it and get the patch distributed.

If you need other support like installing or new applications, I guess that would be a paying service.

---

### Post by az on 2006-05-29
[QUOTE=mcbane]Hello everyone,

I just need a clarification. Does the 3/5-year LTS offered on Dapper refer to the paid support only, or does that mean that the package/security updates will be offered on Dapper repos for the full 5 year-period?
[/QUOTE]

It refers to what they will support officially in the archives.  The packages will get security patches and bug fixes for that time.  You will not get newer versions of the apps, just security and bug fixes.

You probably can pay for support from them, or any other company that offers support to provide you with new packages, if you need.  

But no bug or security fix will be ignored - they will all go into the archive for the period of time it is supported.

---

### Post by mcbane on 2006-05-29
Thanks for the reply, guys. Much appreciated.

I'm a bit confused as to what will be considered a bug fix or a security patch. Does that include future "minimal" version upgrades, i.e. Apache going from 2.0.58 to 2.0.59, or PHP from 5.1.4 to 5.1.5, or MySQL from 5.0.22 to 5.0.23?

Or, will I be stuck with the specific Apache (et al.) version at the time of the Dapper release with custom Ubuntu fixes for that version only? Now that would be fairly stupid, so I hope not... So far I have been compiling everything from source, to keep up to date as possible. 

Oh, and why do the Debian/Ubuntu repos lag behind source releases for months at a time (at least for LAMP)? Considering it's server software, this probably isn't best practice.

Thanks again for clarifying this.

---

### Post by az on 2006-05-29
[QUOTE=mcbane]Thanks for the reply, guys. Much appreciated.

I'm a bit confused as to what will be considered a bug fix or a security patch. Does that include future "minimal" version upgrades, i.e. Apache going from 2.0.58 to 2.0.59, or PHP from 5.1.4 to 5.1.5, or MySQL from 5.0.22 to 5.0.23?

Or, will I be stuck with the specific Apache (et al.) version at the time of the Dapper release with custom Ubuntu fixes for that version only? .[/QUOTE]
Yes, you will.

[QUOTE=mcbane]
Now that would be fairly stupid, so I hope not... So far I have been compiling everything from source, to keep up to date as possible. 
.[/QUOTE]

That's a great way to break your box.  You should stay away from cutting-edge or newly-released stuff for a mission-crittical box.  You need tried-and-true, will-not-break software.


[QUOTE=mcbane]
Oh, and why do the Debian/Ubuntu repos lag behind source releases for months at a time (at least for LAMP)? Considering it's server software, this probably isn't best practice.
[/QUOTE]

Best practice means it will work.  It means you set it and forget it for a long time.  You want something to go on working without breaking for years at a time.  

People want a Dekstop to be cutting edge.  Not so for a server.  Five-year-old software running on a mission-critical server is not unusual.

---

