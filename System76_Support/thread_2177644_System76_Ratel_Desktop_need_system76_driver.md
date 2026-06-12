---
title: "System76 Ratel Desktop need system76 driver?"
date: 2013-09-29
forum: System76 Support
---

### Post by rpjohns on 2013-09-29
I had to reinstall ubuntu 13.04 image on my new System76 Ratel desktop. I've done that. I read here: [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System) that to compete the isntalltion I need to install the System76 Driver (I show how below). I do a little digging on whether I *reallly* need to do this for the Ratel desktop and I've come to the conclusion that this box doesn't need it. Obviously Im not 100% confident about this conclusion so I'm phoning a friend (so to speak) to sanity check this decision. Any one know?  Note I'm a little weary of installing software that isn't absolutely essential.  Thanks for any input.

sudo apt-add-repository ppa:system76-dev/stable
sudo apt-get update
sudo apt-get install system76-driver

---

### Post by rocky-oceans on 2013-10-12
I have the same question for a PanP6 (for 13.04 and 13.10).

For your Ratel, the following page
[http://knowledge76.com/index.php/RatP1](http://knowledge76.com/index.php/RatP1)
does not have an entry for 13.04. Perhaps that means it's not required (and everything was merged into the kernel used by 13.04?). Just a guess though

---

### Post by isantop on 2013-10-14
You should always have it installed, as it allows us to fix unforeseen future regressions and bugs. But no, it's not strictly necessary.

---

