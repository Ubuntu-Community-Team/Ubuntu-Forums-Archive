---
title: "flaw less 6.06 to 6.10 upgrade on a production server"
date: 2006-11-08
forum: Server Platforms
---

### Post by jaakan on 2006-11-08
I setup a JFFNMS+Ubuntu 6.06 server for the company I work for. 
We have been using this as a full production server even before Ubuntu 6.06 server was out of beta. Today during production hours I did an 6.06 to 6.10 dist-upgrade

sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude dist-upgrade
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a 

Rebooted and the server was back online in a few minutes without any problems. That old dell server is now even faster.

Is there a command line version of the Hardware database submit tool?

---

### Post by Royel on 2007-07-18
old thread an I found it useful..

I was really worried about upgrading a production 6.06 server, but was hoping to correct some issues with mysql by upgrading, this helped give me the courage to "press the button" so to speak.

---

