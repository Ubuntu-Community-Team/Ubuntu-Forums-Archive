---
title: "Beryl Repository doesn't have Beryl??"
date: 2007-02-24
forum: Repositories &amp; Backports
---

### Post by Cyclops_ on 2007-02-24
So I added the Beryl repository to my sources.list... I already have the nvidia drivers for my ASUS card installed.

So, anyway, I added the repository, and I also added the gpg key... and now when I do an apt-cache search for beryl or emerald nothing at all comes up.

in sources.list:

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy

(of course I did a sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade)


And then:

me@compy:~#sudo apt-cache search beryl
me@compy:~#

(nothing)

Does anyone have a clue?

Thanks for any help.

---

### Post by Gerard Barberi on 2007-02-24
Not sure, but try formatting it 

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

then update.

---

