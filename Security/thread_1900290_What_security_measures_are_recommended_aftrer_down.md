---
title: "What security measures are recommended aftrer downloading a software?"
date: 2011-12-25
forum: Security
---

### Post by newhere_m on 2011-12-25
Suppose someone had downloaded and installed a software in Ubuntu (say 10.04 LTS). Before starting to use it, what security precautions should he/she take? From my limited experience I think the most important is to check the  default "preferences" and modify as needed. Are there other steps to be taken?  Another issue is, I am looking for a check-list of security measures (not lengthy discussions on security) which every user should follow after installing ubuntu and before connecting to internet. I am sure such discussions exist in this forum, so can anybody please point me to that? (If not, then can anybody please list here? assume a typical desktop user, not for running server.) Thanks.

---

### Post by Ms. Daisy on 2011-12-26
This is a basic security wiki for desktop Ubuntu users:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Unfortunately, any useful list of security measures is going to be a bit lengthy.  IMO the wiki is a good checklist to get you started in the right direction.

---

### Post by Dangertux on 2011-12-26
Checklist post install before connection in three lines.

- Strong Credentials
- Decent Firewall Configuration
- Apparmor profiles (at very least for browser)

After connection

- Updates
- NoScript (or similar)

That would be (is) my checklist.

---

### Post by SeijiSensei on 2011-12-27
> **newhere_m said:**
> Suppose someone had downloaded and installed a software in Ubuntu (say 10.04 LTS). Before starting to use it, what security precautions should he/she take?

The answer to this question depends greatly on where the software you downloaded came from.

Software installed from the official Ubuntu repositories should be safe to use "out-of-the-box."  Ubuntu's (and Debian's) developers will have vetted the software for you already.

Software installed from a "personal package archive" or "PPA" repository is only as trustworthy as the person who uploaded the package.  I use at most half-a-dozen PPAs for software that tends to be in rapid development like [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases") or [mplayer2]("https://launchpad.net/~ripps818/+archive/coreavc").  If someone plausibly recommends a PPA here on ubuntuforums, I might trust his or her suggestion after considering the person making the recommendation.  I might do a bit of investigation as well.

Software downloaded as source code and compiled by you again depends on how much you can trust the developers.  I compile the occasional program from source and have never had any problems, but most of these are arcane network utilities ([Obtuse smtpd]("http://smtpd.sourcearchive.com/") is one I've used for years) or similar programs that have never made it to the repositories.  In some cases I'll compile an application from scratch like mplayer or GIMP if there's some feature in a recent release that's not yet available in the Ubuntu repositories. 

Software downloaded as binaries from random locations should be avoided unless you really have no other option.  Most any open-source program you might desire should be available from the official repositories, a PPA, or the developers themselves.  Commercial, closed-source programs for Linux are exceedingly rare.  If they come from a respectable company, I might choose to try one.  Binaries from random people and locations should *never* be trusted.

---

