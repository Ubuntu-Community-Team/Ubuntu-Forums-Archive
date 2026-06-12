---
title: "clamav-daemon install problem in Hardy"
date: 2009-11-12
forum: Server Platforms
---

### Post by rick@radiohospital.com on 2009-11-12
I am having trouble trying to install clamav-daemon in Hardy server, along
with amavisd-new, spamassassin, and supporting decompressors.  Trying to
follow the guide I found here:

[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

I ran into trouble real early on with the very first command line:

sudo apt-get install amavisd-new spamassassin clamav-daemon

Sounds easy, but this thing has fought me every inch of the way.  I've now fought
through the problems with amavisd-new and spamassassin and am stuck on
clamav-daemon.  When I execute the command:

sudo apt-get install clamav-daemon

after the usual apt information, it informs me that:

/var/lib/dpkg/info/clamav-daemon.postinst: 217: cannot create /var/lib/clamav/clamdrotate.debconf: Directory nonexistent
dpkg: error processing clamav-daemon (--configure):
 subprocess post-installation script returned error exit status 2

Well, of course the directory doesn't exist, and in looking at the post-install script,
I don't see anywhere where it made any attempt to create it.  Doesn't look like
there is any attempt to create a user or group for clamav, either.  Are there some
steps missing from the guide?  Problem with having root locked?  All the posts I've
been reading seem to assume this step "just works", but I am not finding it to be
so.  What am I missing?

- Rick

---

### Post by rick@radiohospital.com on 2009-11-24
Followup:  I've given up on this combination.  The deb packages from the universe repository don't seem to want to install properly in this version of the OS, and the backports had other, totally different problems.  I've abandonned Hardy and gone to Karmic and newer versions of amavis, spamassassin, clamav.  Having less trouble now,
and think I am close to making it work.

---

