---
title: "LIve update of Automatix2"
date: 2007-03-16
forum: Tamil Team - India
---

### Post by jagannath on 2007-03-16
Hi Guys, Vanakkam!

This morning while running live update, I got a window with the message " Not Authenticated, Automatix 2"

Is it safe to go ahead and install the update. 

Uthavi vendum!

Mikka Nanri 

J

---

### Post by zvacet on 2007-03-16
Go ahead and install it.You will get massage that missing public key and number with it.Open terminal and 
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -
```
KEY=number after missing public key For example :missing public key123456
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 123456
gpg --export --armor 123456 | sudo apt-key add -

---

