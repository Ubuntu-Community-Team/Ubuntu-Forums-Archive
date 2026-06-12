---
title: "If I install TB via ubuntuzilla, will it install the latest version 12.0.1?"
date: 2012-05-02
forum: Ubuntuzilla
---

### Post by swarup on 2012-05-02
The default TB installed in Ubuntu 12.04 is 11.0.1. For me it runs terribly-- so slow! So I would like to install TB 12.0.1. I was thinking to use the instructions given here on the ubuntuzilla site.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

There the last step is to install:

```
sudo apt-get install thunderbird-mozilla-build

```

Now, will this command automatically select the latest version 12.0.1 to install? Or if not, how can I specify that this is the version I want?

---

### Post by nanotube on 2012-05-03
Yes, ubuntuzilla has the latest 12.0.1 in the repository, so that will indeed install 12.0.1.

---

### Post by swarup on 2012-05-03
Ok, thanks. And I see now that there are both the i386 and amd64 versions of 12.04 available via ubuntuzilla. Will it recognize that I have the 64bit version of Ubuntu 12.04 installed, and auto-select the amd64 version of TB 12.0.1 for download?

---

### Post by nanotube on 2012-05-03
yes, your system will automatically request packages for your achitecture, so if you're on 64bit, it'll request 64bit packages.

---

### Post by swarup on 2012-05-03
Thank you-- that is very helpful. :)

---

### Post by nanotube on 2012-05-04
glad to help. :)

---

