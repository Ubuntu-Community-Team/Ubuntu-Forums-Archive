---
title: "Gutsy, Serval and the &quot;Restricted Package&quot;"
date: 2007-11-21
forum: System76 Support
---

### Post by Chibi-Tatsu on 2007-11-21
When I installed the last on the second (with the first build), which I got last night, a number of curious things happened:

* Totem (gstreamer version) threw up an error about the Media Keys plugin
* My battery indicator vanished from the top right
* My 'quit' default changed from a power icon to a running man.
* Appearance of my network connectivity indicator vanished.

When I removed the package, the changes undid themselves, but I would like to be able to utilize the package... so what happened?

EDIT: Oh yes, and I can't get a resolution above 1440 x 900.

---

### Post by thomasaaron on 2007-11-21
Not sure what happened. Are you running 32-bit Ubuntu?

Make sure your system is up to date and then run:
sudo apt-get install ubuntu-restricted-extras

---

