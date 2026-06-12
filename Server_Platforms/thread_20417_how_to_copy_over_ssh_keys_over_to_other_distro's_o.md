---
title: "how to copy over ssh keys over to other distro's on dualboot computer"
date: 2005-03-16
forum: Server Platforms
---

### Post by luna6 on 2005-03-16
hello,
I frequently ssh into my ubuntu box at home, thing is, I like try out other distro's as well, and have my computer enabled for booting multiple distro's. Since the ssh keys generated in each distro is different, it is a annoying to have to clear out the keys on my laptop everytime I try to ssh into my box (uses static ip) that may have been rebooted into another distro besides ubuntu. So basically I am wondering where the ssh key is stored in Ubuntu, and I would copy it over to all other distro's i have installed, so whatever distro is up at the moment, I can ssh in without deleting the current key for that ip address.

---

### Post by alastair on 2005-03-16
Keys are just text files - stick them on a USB disk/key and away you go. Or copy them to a mounted partition etc.

They are stored in ~/.ssh

See : man ssh

---

