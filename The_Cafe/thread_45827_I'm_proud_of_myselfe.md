---
title: "I'm proud of myselfe"
date: 2005-07-01
forum: The Cafe
---

### Post by Kimm on 2005-07-01
ok, every linux user tend to screw their systems up once in a while (atleast the onse that tinker with things they shouldnt tinker with...). I was one of these people, even though it wasnt the first time, it was one of the most severe times.

It all started with me wanting the latest stable release of gimp (2.2.8), I downloaded the .deb and noticed that it needed some newer versions of some of the libraries I had installed. These libraries included libc6.
I figured "hey, installing a new version of that cant do any harm..." oh was I wrong... I downloaded the latest version of libc6 from a debian search thing and I installed it, the installation want smothly and I soon had gimp upp and running.

Then (as the gimp got errors when I first tried to install it), I ran "apt-get -f install" without a package name to see if it wanted to remove the gimp anyway, well... it didnt, instead it wanted to remove around 25 other packages... some more or less important to the system. After thinking for a while I figured I could remove all those packages, "I can just run apt-get install ubuntu-desktop afterwards" I though, but when I did that I ran into more trubble, aparently ubuntu-desktop relied on some packages that where not compatable with the version of libc6-dev that I had installed along with the newer libc6 (the dev package was older) and that got a bit messy... I finaly got around to download the latest version of libc6-dev aswell. now that package installed (lsb), but I still recuired locales, and the english language pack, the language packe also required locales.
so... I went and downloaded the latest version of that aswell... after doing that I managed to get everything upp and running again. I might not be using some standard packages for ubuntu but its still as usable as it ever was and I'm quite proud that I acctually managed to get things running again.

Usualy when something goers wrong with my Linux install it ends in a save of my most important files and then a fast reformat of the hdd and a fresh install. But today I defeated the beast! :grin:

---

### Post by benplaut on 2005-07-01
bravo!

if only i could defeat the wireless-tools beast  :roll:

---

### Post by sapo on 2005-07-01
i ve defeated one beast too.. i ve used a lot of package of marillat repositories when i installed my ubuntu.. then i had a lot of trouble to remove them... cause everything in the ubuntu became "uninstalable"... it took me more than a week to fix everything  ](*,)

---

### Post by N'Jal on 2005-07-02
I did this once, it resulted in the daemon child hoary warthog, not quite hedgehog but still partially warty. It was horrible, an abomination. I eliminated it as soon as i could from my system.

---

