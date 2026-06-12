---
title: "Already in keyring problem imprting GPG from old computer to new"
date: 2017-02-06
forum: Security
---

### Post by opprobrium on 2017-02-06
I've been moving from an old computer (running 14.04) to a new one (running 16.04).

I've managed to move most things, but am now struggling with moving my GPG keys.

I've exported the key and put it on the file other (as a gpg and asc file - people suggest both approaches elsehwere).

When I g to import the key I can see the file and the details of the key, but when I go to import I get a message "Import failed: already in secret keyring".

I suspect this is a root issue, but don't understand enough to know what to do.

---

### Post by Habitual on 2017-02-06
If you copied ~/.gpg correctly from original to new, there is no need for import.

---

### Post by opprobrium on 2017-02-08
Thanks. Unfortunately, I can't copy the gpg file into the relevant directory (/bin). Presumably this is a permissions issue (as I'm not logged in as root).

Probably I'm missing something which will become obvious when I have a little more time to look at it.

---

### Post by oldos2er on 2017-02-08
The folder Habitual is referring to is /home/user/.gpg/, not /bin. As far as I know no gpg keys normally live in /bin.

---

### Post by Habitual on 2017-02-08
> **opprobrium said:**
> Thanks. Unfortunately, I can't copy the gpg file into the relevant directory (/bin). Presumably this is a permissions issue (as I'm not logged in as root).

Probably I'm missing something which will become obvious when I have a little more time to look at it.

The /home/user/.gpg/ directory from the original server should be copied to the new server in the same location on the new system.
This does not include binaries, pgpgpg doesn't even have to be installed.

As long as the permissions remain the same on the new directory, when the gpgpgp binary gets (or is already) installed, it just reads 
that new directory.

gpggpg has the additional benefit of needing the keyphrase to unlock the physical. but permissions are very important.

Found some links for ya:
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto) and 
[Beginners Guide to GnuPG]("https://ubuntuforums.org/showthread.php?t=680292")

---

### Post by opprobrium on 2017-02-11
Thanks both. I got this working, but had to move ~/.gnupg rather than ~/.gpg (I could never find the latter).

I can now see my key and have got it working in Enigmail.

---

### Post by oldos2er on 2017-02-11
Great! Would you please mark your thread 'Solved' from Thread Tools at the top of the page?

---

### Post by Habitual on 2017-02-11
woot! Glad it worked out!

---

