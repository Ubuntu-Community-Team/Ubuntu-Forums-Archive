---
title: "seahorse in 12.04?"
date: 2012-02-20
forum: Security
---

### Post by ottosykora on 2012-02-20
Does someone know if there will be seahorse or similar gui tools for gpg operations in 12.04?

---

### Post by Matt 6:27 on 2012-02-20
> **ottosykora said:**
> Does someone know if there will be seahorse or similar gui tools for gpg operations in 12.04?

It loooks like there may well be a seahorse derivative in the upcoming LTS.  I'm running 11.10 and am in the process of testing what comes up as "seahorse-plugins" once you add a PPA to your sources (see Launchpad link below for details).  So far, it's working perfectly.   Note, I did have to load gnupg-agent so I could put a 'timer' on the key password.

[https://bugs.launchpad.net/ubuntu/+source/seahorse-plugins/+bug/862609](https://bugs.launchpad.net/ubuntu/+source/seahorse-plugins/+bug/862609)

Thanks Marc!!

---

### Post by cariboo on 2012-02-20
Passwords & Keys (seahorse) is available in 12.04, what makes you think it wouldn't be?

---

### Post by Matt 6:27 on 2012-02-20
> **cariboo907 said:**
> Passwords & Keys (seahorse) is available in 12.04, what makes you think it wouldn't be?

You are correct.  I assumed the question related to the seahorse-plugins issue, which does appear to be on the way to a resolution.

---

### Post by ottosykora on 2012-02-21
> **cariboo907 said:**
> Passwords & Keys (seahorse) is available in 12.04, what makes you think it wouldn't be?

the situation that those thigs were missing in 11.10 ;-)

---

### Post by cariboo on 2012-02-21
> **ottosykora said:**
> the situation that those thigs were missing in 11.10 ;-)

They aren't missing in 11.10, there just isn't a menu option for seahorse. I f you are using Unity, just open the dash and type **sea** the icon should pop up.

---

### Post by ottosykora on 2012-02-22
Ahh , ok understand.

It is in fact more the right click menu item for encryption decryption what is needed, but will see.

When just seahorse selected as installed software, well this is not of big use, as I still have to go to terminal and use gpg 'by hand' to encrypt files and encryption and decryption of texts happens only in enigmail.

So what is needed is the file manager plugin to be actually also able to use it efficiently.

Will this plugin be then available? Also the addon to the text editor to encrypt , clearsign etc texts?

---

### Post by cariboo on 2012-02-22
With the way gnome is dropping functionality from many applications, other devs have stepped up to add what we've lost back. Have a look at this[ blog]("http://www.hecticgeek.com/2012/01/powerful-file-encrypting-script-nautilus-file-manager-turbo-secure/") post, it is about Turbo-Secure, it should do what you want.

---

### Post by ottosykora on 2012-02-23
> **cariboo907 said:**
> With the way gnome is dropping functionality from many applications, other devs have stepped up to add what we've lost back. Have a look at this[ blog]("http://www.hecticgeek.com/2012/01/powerful-file-encrypting-script-nautilus-file-manager-turbo-secure/") post, it is about Turbo-Secure, it should do what you want.

ok, but it looks that this is about some other encryption system then gpg, repectively it seems to do the symetric encryption in many algos, but it is not clear if this can use asymetric encryption of the keys then etc.

What I am looking for is some other way to use efficiently gpg/pgp encryption in ubuntu.
In 11.04 it is still all present, in 11.10 no trce of it and therefore curious if all thise functions will be back in 12.04 as otherwise I am not able to upgrade and have to use windows only.
We can be asked to use CLI for gpg in 2012 seriously.

So what my original Q was, if there will be the functionality of seahorse plugin for file encryption/decryption for the natilus back and the text encryption and clearsigning for text editor back in 12.04 and all this for gpg/pgp.

---

### Post by cariboo on 2012-02-23
To use gpg with nautilus, install seahorse-nautilus, reboot to start the seahorse daemon and you should be good to go.

---

### Post by ottosykora on 2012-04-22
> **cariboo907 said:**
> To use gpg with nautilus, install seahorse-nautilus, reboot to start the seahorse daemon and you should be good to go.

can you give us here some info as where you get all this seahorse-nautilus from exactly as it seems not to be part of any regular repo.

any info as where to get some useful former functionality of the seahorse in nautilus will be appreciated.


An operating system distro not having any useful handling of pgp/gpg on board is obsolete today.

---

### Post by kostkon on 2012-04-22
> **ottosykora said:**
> can you give us here some info as where you get all this seahorse-nautilus from exactly as it seems not to be part of any regular repo.
[It's in the universe repo]("http://packages.ubuntu.com/precise/seahorse-nautilus"), it seems.

---

