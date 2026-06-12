---
title: "upgrading old server (intrepid) to lucid"
date: 2010-11-29
forum: Server Platforms
---

### Post by danneh3826 on 2010-11-29
hi,
i'm currently running ubuntu 8.10 intrepid on my server and have been for some time. i'm trying to upgrade it 10.04.1 LTS via aptitude/apt-get, but as this server also runs a hosting stack powered by directadmin, they've suggested to make apt never upgrade hosting applications (apache/exim/bind etc).

now, i've got the old-releases in my sources.list file, but have read a couple of times that there may be an issue upgrading it even to 9.04 jaunty. apt wants to run an upgrade path 8.10 -> 9.04 -> 9.10 -> 10.04 (and possibly from there to 10.04.1).

i suppose my question really is this: does this have the remotest of possibility of working? i only have remote (not physical) access to this server, since it's in a DC on the other side of the atlantic, so i'd prefer everything to be done via command line and hope for the best. and if this is possible, how do i make apt ignore things like apache, exim, bind, dovecot, etc so that i can upgrade them later using directadmin's own upgrader scripts?

thanks a million,

dan

---

### Post by danneh3826 on 2010-12-05
*bump*

anyone? :(

---

### Post by Groodles on 2010-12-07
[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

---

### Post by danneh3826 on 2010-12-07
hi,
thanks. that page doesn't explain anything about leaving certain software intact across upgrades (i.e; NOT to upgrade things such as apache, exim, bind, dovecot, etc..) as this software is all managed by the hosting software (directadmin) and they've strongly advised me to not allow the system upgrader to update these applications. just, i'm not seeing how that can be done?
dan

---

### Post by CharlesA on 2010-12-07
I don't really think it's possible to load certain packages at a "pre-upgrade" state, while still upgrading the rest of the OS.

Did the hosting company tell you exactly why running newer versions of software is not a good idea?

---

### Post by danneh3826 on 2010-12-07
> **CharlesA said:**
> I don't really think it's possible to load certain packages at a "pre-upgrade" state, while still upgrading the rest of the OS.

Did the hosting company tell you exactly why running newer versions of software is not a good idea?

it's to do with the idea that the hosting software (directadmin) has it's own software installation/upgrade scripts (known as "custombuild"). it grabs specific versions from their servers known to work with the distribution that is being used and compiles from scratch rather than installing from deb/rpm's.

i suppose though that if the ubuntu upgrade script upgrades the hosting stack along with the o/s, then i imagine that running their custombuild script once i've got to the target ubuntu versiono should, in theory, overwrite what the upgrader installed with it's own versions. hmm... i'll ask them that question.

Dan

---

### Post by CharlesA on 2010-12-07
That'll probably be the best thing to do.

Is that a VPS or something?

---

### Post by danneh3826 on 2010-12-07
it's a dedicated box. had it a couple of years now. didn't realise they didn't install an LTS version (that i asked for). went to apt-get a handful of packages a week or 2 ago and just got a bunch of 404's instead since 8.10's been EOL'd for a while now.

---

### Post by CharlesA on 2010-12-07
Ah I see.

Definitely have a good back up before you do anything.

Personally, I'd do a full reinstall, but I don't see how that's possible if they are using custom packages.

---

