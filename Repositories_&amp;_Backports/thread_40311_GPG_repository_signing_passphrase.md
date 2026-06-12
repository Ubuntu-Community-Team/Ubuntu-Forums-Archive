---
title: "GPG repository signing: passphrase?"
date: 2005-06-08
forum: Repositories &amp; Backports
---

### Post by simbaB on 2005-06-08
I recently set up an FTP archive behind my firewall to service my two boxes. It has packages that I have built myself--some newly debianized, some backported from debian testing or unstable, some converted from .RPM with alien. I configured GPG signing for the repository Release file. I would like to automate the process of building repository metadata; I would like to have it both manually invokable with a script (for when I build a new package) and on a schedule with cron. The way I understand it, this precludes me from having a passphrase on my repository-signing GPG key. Is this correct or is there some way to have a passphrase on that key? Would it be worth it given the fact that the passphrase would have to be cached somewhere? What is the practice of the Ubuntu and Debian ftpmasters? Do they have passphrases on their keys?

TIA,
Andrew

---

