---
title: "Failed to fetch / 302 Redirect"
date: 2008-05-14
forum: Server Platforms
---

### Post by letrappe on 2008-05-14
I have replied to a few posts already, but have received no answers as of yet and I am looking to resolve this.  With reluctance in posting because I don't want to inundate the forums, I have no other choice but to post a new thread.

I am running:

Ubuntu 7.10 Gutsy server
LAMP install
ssh
static IP
OpenDNS
sources.list verified as correct


Any time that I try to install a new application, software program, or updates, I am shot in the foot by a bunch of "Failed to fetch" and "302 Redirect" texts after executing "apt-get".  I have verified that I am able to reach all of the sites by ping, but I am still unable to update.  I have tried updating the PGP encryption code by using "wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update", but returns a "gpg: no valid OpenPGP data found.".  :confused:

If anyone is able to assist with suggestions or magic or voodoo or chant, please feel free.

Thank you.

---

### Post by lonepie on 2009-03-31
Same problem here, I've narrowed it down to OpenDNS causing this problem. I had to turn it off for the time being.

---

