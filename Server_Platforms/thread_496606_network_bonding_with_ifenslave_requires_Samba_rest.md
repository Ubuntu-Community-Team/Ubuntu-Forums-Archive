---
title: "network bonding with ifenslave requires Samba restart"
date: 2007-07-09
forum: Server Platforms
---

### Post by 2shanfernando on 2007-07-09
I've got two gigabit NICs in the system so i figured i'd bond them together, but now after loading the OS I have to manually restart the samba service for it to be accessible on windows boxes.

Is there away to load the samba share *after* it gets an IP from the ifenslave stuff?

I'm using this in my aliases for the bonding:

```


# Bonding
alias bond0 bonding
alias eth0 e100
alias eth1 e100
options bonding mode=5 miimon=100


```

Samba is setup with WINS support.
=======
FIXED/SOLVED

In the samba configuration file i was binding to the eth0, eth1 interfaces which were not valid. I simply changed the config to bind to bond0 and it works. Yes I feel very dumb right now.:(

---

