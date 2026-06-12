---
title: "gpg/Seahorse help needed: find/repair/migrate keyring"
date: 2013-02-23
forum: Security
---

### Post by r_widell on 2013-02-23
I am currently running Ubuntu 10.04LTS on a a laptop that's used to connect to a number of different wifi APs. I'd like to upgrade to a more modern kernel but I'm not a fan of either Unity or Gnome3 so I want to move to KDE4.

The problem I'm having is that the WPA2 passwords (most of which I don't remember)  for many of those APs are actually passphrases (i.e. a lengthy string with one or more embedded whitespace characters) and clicking the "show password" box in Seahorse shows a string of hexadecimal digits which are neither ASCII nor utf-8. This leads me to believe that the passphrase has been subjected to an additional hashing algorithm.

Nevertheless, this machine will still connect to those APs, so the data is still recoverable, somehow. What I need to know is how.

Looking through the docs, I can't even figure out for sure where the database that Seahorse uses is even located.

ls -l ~/.gnupg returns this:
```
-rw------- 1 ron ron 38 2009-07-26 23:49 gpg.conf
-rw------- 1 ron ron  0 2008-12-19 17:02 pubring.gpg
-rw------- 1 ron ron  0 2008-12-19 17:02 secring.gpg
-rw------- 1 ron ron 40 2013-02-15 15:36 trustdb.gpg
```so it's not there.

I did find a file named login.keyring under ~/.gnome2/keyrings that looked promising, but invoking gpg with the -d, --list-keys, or --export options returned messages that essentially told me I was clueless (true).

So:
How can a discover what the non-obfuscated passphrases really are?

If that can't be done, can I migrate some files to the new system so I don't have to re-enter those passphrases? If so, which files and where do I put them under KDE?

FWIW, the first Ubuntu installation on this machine was (IIRC) 08.10. As new releases came out, I did in-place upgrades to the new releases until I got to the LTS release (and have been suffering with the broken intel video driver ever since). Current versions are:
kernel: 2.6.32-45-generic
gpg: gpg (GnuPG) 1.4.10
Seahorse: 2.30.0

TIA for any pertinent suggestions.

ron

---

### Post by r_widell on 2013-03-11
If this is the wrong forum or I didn't supply enough information, please let me know.

ron

---

