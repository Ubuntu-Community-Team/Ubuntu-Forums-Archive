---
title: "TWiki re-installation"
date: 2006-08-21
forum: Server Platforms
---

### Post by kmramki on 2006-08-21
I have been trying to re-install twiki, after first uninstalling it, using synaptic, and something seems terribly messed up here. I always get the error "E: twiki: subprocess post-installation script returned error exit status 1," and when I do the same using apt-get, I see that it complains, during re-install, that it is not able to see /etc/twiki/TWiki.cfg and /etc/twiki/apache.conf. ](*,) 

PLEASE, could someone help?! Thanks.

---

### Post by Cato2 on 2007-11-22
Sorry you didn't get this installed, but TWiki installs quite easily on Feisty and Gutsy from packages now - see [http://twiki.org/cgi-bin/view/Codev/TWikiOnUbuntu](http://twiki.org/cgi-bin/view/Codev/TWikiOnUbuntu) for a HOWTO.

It may be worth doing a 'full remove' (check the aptitude or Synaptic docs for details, can't remember command right now) to ensure the TWiki config files are removed, before you re-install.

---

