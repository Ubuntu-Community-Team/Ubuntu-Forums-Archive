---
title: "gpg and multiple email addresses [solved]"
date: 2006-07-21
forum: Server Platforms
---

### Post by matthew on 2006-07-21
I have an openPGP key created with gpg in the manner described in [this wiki page]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto"). It was created using one email address, however I have a second email address that I would like to add to that key rather than creating a second key. 

I noticed the wiki page says this is possible (didn't know that) near the end of the "Using GnuPG" part.> You can add extra e-mailaddresses to the key later. 
How would I go about doing that?

---

### Post by lotusleaf on 2006-07-21
[http://www.gnupg.org/gph/en/manual.html](http://www.gnupg.org/gph/en/manual.html)
See: "Adding and deleting key components"

[http://www.gentoo.org/doc/en/gnupg-user.xml](http://www.gentoo.org/doc/en/gnupg-user.xml)
"If you have several email addresses that you would like to use with this key, you can run gpg --edit-key YOUR_ID and then use the adduid command. It will ask you for the name, email and comment of the second ID you will be using."

---

### Post by matthew on 2006-07-21
Thank you. That was very helpful!

---

