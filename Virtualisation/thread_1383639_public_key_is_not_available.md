---
title: "public key is not available"
date: 2010-01-17
forum: Virtualisation
---

### Post by hyburn on 2010-01-17
hey folks,

im running sun_vbox. its working, but I cant update

my last line in sudo apt-get update reads as follows:

W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE

how do I fix this issue?

---

### Post by drs305 on 2010-01-17
Run this to import the key:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 6DFBCBAE && gpg --export --armor 6DFBCBAE | sudo apt-key add -
```

---

### Post by hyburn on 2010-01-17
this is my response

gpg: requesting key 6DFBCBAE from hkp server keyserver.ubuntu.com
gpgkeys: key 6DFBCBAE not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

### Post by drs305 on 2010-01-17
The code I posted just worked for me, but you can try this one as an alternative:
```
gpg --keyserver subkeys.pgp.net --recv 6DFBCBAE
```

---

### Post by hyburn on 2010-01-17
still nothing, anybody else?

thanks anyways DRS

---

### Post by wojox on 2010-01-18
Try the whole number:

```
gpg --keyserver subkeys.pgp.net --recv DCF9F87B6DFBCBAE
```

---

### Post by hyburn on 2010-01-18
ahhhh, its requesting a key. ill let you know how it works

this is my response

```
gpg: requesting key 6DFBCBAE from hkp server subkeys.pgp.net
gpgkeys: key DCF9F87B6DFBCBAE not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

---

### Post by plucky on 2010-01-18
Try ```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

Then ```
sudo apt-get update
```

And see what that gives.

Good Luck

---

### Post by hyburn on 2010-01-18
plucky my response was as follows:
gpg: no valid OpenPGP data found.

---

### Post by plucky on 2010-01-18
> **hyburn said:**
> plucky my response was as follows:
gpg: no valid OpenPGP data found.

You have no internet connection.That is the response I get when I turn off my internet connection.

The wget command loads the sun-box.asc file from the virtualbox website and adds it to your authorisation key list.

---

### Post by drs305 on 2010-01-18
hyburn,

Have you visited the Sun page which describes how to add the repository and key? One of the commands is the one plucky provided, but the entire page is here: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

Before following any of the instructions on that page, you might want to open Synaptic, Settings, Repositories and untick any Third Party/Other software entries for VirtualBox. Also remove any Authentication keys for same. Then press "Reload" and start fresh following the instructions on the VirtualBox page.

---

### Post by hyburn on 2010-01-18
ok so heres how it done,

special thanks to kobalt for this.

gotta save the key as a text file, then import it in my authentification of my software sources. BOOYA thanks kobalt

---

