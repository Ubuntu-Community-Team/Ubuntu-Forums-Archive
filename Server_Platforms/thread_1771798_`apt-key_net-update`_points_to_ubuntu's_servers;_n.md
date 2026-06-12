---
title: "`apt-key net-update` points to ubuntu's servers; not my local repo"
date: 2011-05-30
forum: Server Platforms
---

### Post by cpt_power on 2011-05-30
I've got a local mirror of the Ubuntu repository (with several distros) set up and running smoothly on a 8.04LTS box. However, I was recently made aware of some traffic on a few internal boxes (10.04.2LTS mostly; can't see any others that are exhibiting this behaviour) that seems a bit odd.

The servers in question have absolutely zero port80 access to the Internet, and the /etc/apt/sources.list file correctly points to our local mirror. However, when a cron that runs daily to update the key signatures is executed, it tries to phone home to canonical's servers.

So, I guess my question here is two-fold:
1 - How can I have these servers ask the local mirror to update these keys instead of trying to hit canonical.com
2 - If I can't do that, is there any harm in turning this cron off completely? Will it end up silently failing when I try to run updates in the future?

---

### Post by cpt_power on 2011-05-31
Hmm.. now I'm starting to question if apt-key net-update really serves any purpose at all.

Digging through the documentation for [http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt), I read that the trusted keys are updated as part of the debian-archive-keyring (or for this situation, the ubuntu-keyring) package. So, if the gpg keys are updated here, then again I'm lead to believe that apt-key net-update isn't required.

Thoughts?

---

### Post by cpt_power on 2011-06-02
yeah, its seeming more and more like "apt-key net-update" performs the same functions of "apt-key update", only it does it over the interwebs as opposed to updating based on an already downloaded package.

From the recently updated apt-key manpage:

> update - Update the local keyring with the keyring of Debian archive keys and removes from the keyring the archive keys which are no longer valid.
net-update - Update the local keyring with the keys of a key server and removes from the keyring the archive keys which are no longer valid. This requires an installed wget and an APT build configured to have a server to fetch from. APT in Debian does not support this command, but Ubuntu's APT does.

---

