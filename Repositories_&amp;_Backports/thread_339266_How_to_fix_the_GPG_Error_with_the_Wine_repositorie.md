---
title: "How to fix the GPG Error with the Wine repositories"
date: 2007-01-15
forum: Repositories &amp; Backports
---

### Post by YokoZar on 2007-01-15
If you use the WineHQ APT repository [here](http://winehq.org/site/download-deb), lately you've likely noticed you're getting errors about a missing key like this:

*W: GPG error: http://wine.budgetdedicated.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263*

I've just started signing the repository (which is why this error has replaced the warning about packages being unable to be authenticated), and the instructions page will be updated momentarily.

To make it go away forever, you need to add my key into your list of keys that APT will use.  Just put the following into a terminal:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by bapoumba on 2007-01-15
@ YokoZar : your "here" link is broken ;)

---

### Post by YokoZar on 2007-01-15
> **bapoumba said:**
> @ YokoZar : your "here" link is broken ;)
Haha oops.

At any rate, this page: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) needs a through redoing.  I'm thinking of killing the images entirely and replacing them with console commands similar to [Medibuntu's instructions](http://medibuntu.sos-sts.com/repository.php).  Any thoughts?

---

### Post by bapoumba on 2007-01-16
Hello,

I used the other method [http://medibuntu.sos-sts.com/fr/repository-old.php]("http://medibuntu.sos-sts.com/fr/repository-old.php") to modify my sources.list. I have actually never used the wget method to update the file. So no particular thoughts about it.
Having screenshots, you have to update them every new Ubuntu release. May be easier to just remove them, and link to a general tutorial on how to update the sources.list file.

---

### Post by YokoZar on 2007-01-22
I've sent a patch in to update the instructions at winehq, on this page: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb), however as of January 21st the instructions haven't been updated yet.

---

### Post by loserboy on 2007-01-26
ok cool that fixed it for me this round, so your'e saying thats a permanent fix? cuz it seems to happen every couple updates.

---

### Post by glabouni on 2007-01-27
here's what I did to fix this problem with edgy eft:

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
gpg --export --armor 58403026387EE263 | sudo apt-key add -
```

found it in [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Applications_in_Linux_.28Wine.29")

---

### Post by dumbbeatnix on 2007-04-15
Seems to work.  :popcorn: 

Cheers
dumbbeatnix  :)

---

### Post by kostkon on 2007-04-19
Thanks it worked!

---

### Post by raydar on 2007-04-20
Hi--

I just did this . . . and it worked . . . but who the heck is Scott Ritchie, and did I just give some stranger some kind of access to my machine?

I've been using Ubuntu for a year, but I'm definitely still new enough to it that I don't know for sure what these commands precisely do.

Thanks for any reassurance or warning, and if the latter, especially any info on how to undo what I shouldn't have done. 




gpg: directory `/home/rmc/.gnupg' created
gpg: new configuration file `/home/rmc/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/rmc/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/rmc/.gnupg/secring.gpg' created
gpg: keyring `/home/rmc/.gnupg/pubring.gpg' created
gpg: requesting key 387EE263 from hkp server subkeys.pgp.net
gpg: /home/rmc/.gnupg/trustdb.gpg: trustdb created
gpg: key 387EE263: public key "Scott Ritchie <scott@open-vote.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

---

