---
title: "Cannot install php-pear or php5-cli"
date: 2009-10-02
forum: Server Platforms
---

### Post by tribaldata on 2009-10-02
Hi, 

I'm having issues installing theses two packages php-pear and php5-cli

This is what i get when i try an apt-get install

```

sudo apt-get install php-pear php5-cli
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  php5-cli: Depends: php5-common (= 5.2.6.dfsg.1-3ubuntu4.2) but 5.2.11-0.dotdeb.1 is to be installed
E: Broken packages
```

The weirdest thing is that php5-commom is install and working....

```
sudo apt-get install php5-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
php5-common is already the newest version.
```

I also try to do the following ```
apt-get clean apt-get update 
```and then run my apt-get install again same result.. failure ](*,)

Anyone could help ?

---

### Post by scragar on 2009-10-02
You've updated php5 beyond the version it expects:
> Depends: php5-common (= 5.2.6.dfsg.1-3ubuntu4.2)
It needs version 5.2.6.dfsg.1-3ubuntu4.2 exactly, you've got 5.2.11-0.dotdeb.1

You can either install the packages manually, or try to force them and hope it doesn't cause any problems:
```
sudo apt-get -f install php-pear php5-cli

```

---

### Post by tribaldata on 2009-10-02
Tried the sudo apt-get -f install php-pear php5-cli but same result, I will try to do a manual install for the php-pear one and post results 

thanks

---

