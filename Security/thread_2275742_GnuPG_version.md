---
title: "GnuPG version?"
date: 2015-04-28
forum: Security
---

### Post by Gordonbp531 on 2015-04-28
As the default mail application is now Thunderbird, installing the Enigmail add-in for encrypted mail tells me that the current version of Enigmail is the last version to use GnuPG 1.4.x - that the next version will only use GnuPG 2.x and to upgrade.
The latest GnuPG version (1.4.x) included in 14.04 was released in 2008 - that's SEVEN years ago. 
Why doesn't 15.04 include GnuPG 2.x by default instead of 1.4.x?

---

### Post by Lars Noodén on 2015-04-28
In 14.04, look to the package gnupg2 to provide a more recent version.

---

### Post by Gordonbp531 on 2015-04-28
> **Lars Noodén said:**
> In 14.04, look to the package gnupg2 to provide a more recent version.

Yes - I know that the User can do that.
My question is, why isn't v 2.x installed BY DEFAULT instead of one that's seven years old?

---

### Post by Lars Noodén on 2015-04-29
> **Gordonbp531 said:**
> My question is, why isn't v 2.x installed BY DEFAULT instead of one that's seven years old?

It probably has to do with reliance on upstream (Debian + various packages).  But I'm not privy to the decision process either.  In regards to Enigmail specifically there has been this long, sometimes offtopic, discussion which provides some background:
[https://admin.hostpoint.ch/pipermail/enigmail-users_enigmail.net/2015-February/thread.html#2383](https://admin.hostpoint.ch/pipermail/enigmail-users_enigmail.net/2015-February/thread.html#2383)

---

### Post by Klaster on 2015-06-09
I got the same message. The [GnuPG Ubuntuusers Page]("http://wiki.ubuntuusers.de/GnuPG") says that its recommendable to install both versions aside of each other. Do I have to reassign the version, Enigmail uses? Do I have to generate new keys? Couldn't find decent information on this... Or shall I open a new thread?

Thanks!

---

### Post by Lars Noodén on 2015-06-09
> **Klaster said:**
> I got the same message. The [GnuPG Ubuntuusers Page]("http://wiki.ubuntuusers.de/GnuPG") says that its recommendable to install both versions aside of each other. Do I have to reassign the version, Enigmail uses? Do I have to generate new keys? Couldn't find decent information on this... Or shall I open a new thread?

Thanks!

Best to open a new thread.

---

### Post by Klaster on 2015-06-09
Actually, googling a bit in English gave me this satisfying result: [https://www.enigmail.net/support/transition_to_gnupg2.php](https://www.enigmail.net/support/transition_to_gnupg2.php)

Thanks anyway, Lars! Cheers!

---

