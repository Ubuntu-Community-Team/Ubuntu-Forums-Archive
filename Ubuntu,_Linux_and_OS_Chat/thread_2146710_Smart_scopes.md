---
title: "Smart scopes"
date: 2013-05-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Dark_Horizon on 2013-05-19
I Installed the experimental Smart Scopes  the safe version of smart scopes if there is such a thing, requires experimental repositories.

before you start install PPA Purge you should really install this first (really) always; it unity reverts to its previous working configuration I've just used it when the experimental upgrade didn't work too well. I had a problem with some of the packages 

apt-get install ppa-purge  to install

sudo ppa-purge [the ppa you want to remove]

which in this case would be

sudo ppa-purge ppa:ubuntu-unity/experimental-certified

installing smart scopes the slightly more stable experimental version you may have better luck with it than me first install the repository.

sudo add-apt-repository ppa:ubuntu-unity/experimental-certified

sudo apt-get update && sudo apt-get dist-upgrade



I wanted to say something about SS but after trying it; at this time I can honestly say or recommend PPA Purge its a must have. it worked really well. and of course saved my configuration.



sudo add-apt-repository ppa:ubuntu-unity/experimental-certified

sudo apt-get update && sudo apt-get dist-upgrade



I wanted to say something about SS but after trying it; at this time I can honestly say or recomennd PPA Purge its a must have. it worked really well. and of course saved my configuration

---

