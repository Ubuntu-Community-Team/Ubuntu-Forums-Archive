---
title: "Where are NetworkManager passwords for user-specific connections stored?"
date: 2012-05-19
forum: Security
---

### Post by v6ak on 2012-05-19
I've encrypted my home folder. I wonder how to protect Wi-Fi passwords. I've recognized that some passwords are stored in /etc/NetworkManager. (I've this directory unencrypted.)  But when I uncheck "Availble to all users", I don't know where it is stored. It does not seem to ve stored in /etc/NetworkManager. Is it stored in encrypted ~, or somewhere else?

---

### Post by 2F4U on 2012-05-19
My understanding is that passwords are stored in a keyring, either Gnome keyring or KDE Wallet.

[http://doc.opensuse.org/documentation/html/openSUSE/opensuse-reference/cha.nm.html#sec.nm.security](http://doc.opensuse.org/documentation/html/openSUSE/opensuse-reference/cha.nm.html#sec.nm.security)

---

### Post by v6ak on 2012-05-19
Thank you. It seems to be true: [http://blog.schmichael.com/2008/10/30/listing-all-passwords-stored-in-gnome-keyring/](http://blog.schmichael.com/2008/10/30/listing-all-passwords-stored-in-gnome-keyring/)

Since it is stored it in ~/.gnome2/keyrings/, it is encrypted and thus OK. Well, not 100% OK, because information in /etc/NetworkManager provide some information (what wifi hotspots I use => where I use notebook), but it is relatively OK.

---

