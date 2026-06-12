---
title: "apt-get or aptitude problem"
date: 2011-05-21
forum: Server Platforms
---

### Post by jmsgz on 2011-05-21
hi folks
got a simple ssh server install with 10XX ubuntu server on my hp dl360 server. Just noticed after some time that i cannot apt-get or aptitude any upgrades or program downloads. Get the message that it cannot connect to the ubuntu servers. Am able to ssh into it just fine from other machines. It is connected via DHCP

Can you point me what to do, maybe a config file needs adjusting.

---

### Post by mikewhatever on 2011-05-21
There are over 300 Ubuntu mirrors all over the world, and perhaps the one you are using is down temporarily. What you can do is either wait or use another mirror.

---

### Post by jmsgz on 2011-05-21
problem spread out over several days so i dont think its the selected mirror.

---

### Post by wojox on 2011-05-21
I've seen them anywhere from up to date to one week behind.

What's one of your links?

---

### Post by jmsgz on 2011-05-21
looks like i never "upgdated package list" in Aptitude following install about a year ago,,,,DUH
following this action updated "security files" and logged out. 
things seem to be working ok now in apt-get and aptitude.

thanks for the info
jeff

---

