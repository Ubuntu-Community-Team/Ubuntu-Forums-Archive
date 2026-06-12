---
title: "qemu and .daa files"
date: 2007-12-11
forum: Virtualisation
---

### Post by skymera on 2007-12-11
i know .daa is a type of CD image like .iso.

but can qemu boot into it? into a virtual machine?

---

### Post by ruibernardo on 2007-12-11
> **skymera said:**
> i know .daa is a type of CD image like .iso.

but can qemu boot into it? into a virtual machine?

Hi skymera,

.daa is CD image file like ISO, but it's a propriety one.  You need to convert it to ISO, so QEMU can  use it. One  program I know that can convert .daa files into .iso is [actoneiso]("http://www.kde-apps.org/content/show.php?content=44805") (another is [poweriso]("http://poweriso.com/poweriso-1.1.tar.gz"), but not as good and easy as acetoneiso2, and maybe outdated).

To install acetoneiso 2 in Ubuntu 7.10 Gutsy from the developers deb package (in previous versions it's a little bit more complicated) read [this README]("http://www.acetoneteam.org/gutsy-readme.txt") and download the package [from here]("http://www.acetoneteam.org/download.html").

Convert it and try again. Good luck.

---

### Post by skymera on 2007-12-11
w00t

thanks you.

---

