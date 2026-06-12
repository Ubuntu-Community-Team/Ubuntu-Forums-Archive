---
title: "software recommendations?"
date: 2013-12-23
forum: Ubuntu, Linux and OS Chat
---

### Post by blukami on 2013-12-23
I am an app junkie on my phone always trying out new apps, would love to be able find interesting apps for ubuntu. The suggestion thing in ubuntu software center doesn't seem to do much recommending. 

TTFN

---

### Post by deadflowr on 2013-12-24
If you're someone who has an addiction to installing apps, then browse through the various categories in the software center and see which apps look interesting to you, and install them.
Use the search feature as well.
When you realize that the app you installed isn't what you want and want to remove it, go back into the software center and remove it.
Anyway, what kind of apps are you into?

---

### Post by monkeybrain20122 on 2013-12-24
How about trying to compile something interesting, stuffs not in the repo, and to make it more challenging, something that require non standard dependencies? :)

I am thinking of this [http://www.ballview.org/](http://www.ballview.org/) It was in Ubuntu's repo up to and including raring and then it is removed from saucy. I have been trying to compile it in saucy with no luck. 

First you need an older compiler (gcc 4.4 would probably work. gcc 4.6.3 in Precise works, but default gcc 4.8.1 in Saucy doesn't and 4.6.4 in Saucy's repo apparently doesn't work either, but maybe I did something wrong) and then other dependencies would have to be older too (python-sip in particular and some libboost libraries). So the idea is to use an alternative gcc (which is easy in Debian/Ubuntu as there are many in the repo and you can switch between them with update-alternatives which even has a gui called galteranatives,  but I have to build the compiler in Fedora and switching is not as smooth) and then probably build the relevant libraries locally,--don't have to install all of them that way, some system lib would work with appropriate symlinks, I think,-- and compile it against those. It is a pretty frustrating process, if you have too much time on your hands and like installing stuffs you may want to try building it in 13.10. :)

Edited: the deb from raring doesn't install in Saucy.

---

### Post by blukami on 2013-12-24
Mostly into games but I have found lots of other apps, gave clemintine a try on my netbook and I love it. But I would really like a lot of the tools you find on Kali. Etherape really saved me trying to figure out what was going on on my network.

---

