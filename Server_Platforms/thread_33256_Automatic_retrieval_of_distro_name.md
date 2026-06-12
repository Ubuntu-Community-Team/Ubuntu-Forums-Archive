---
title: "Automatic retrieval of distro name"
date: 2005-05-10
forum: Server Platforms
---

### Post by saltydog on 2005-05-10
I was playing with some coding which needs to retrieve automatically the distro name, and I am wondering why ubuntu doesn't have his own distro name in the system. All applications retrieve distro name from a special file in /etc directory. For ubuntu we have /etc/debian_version which returns 3.1, so every program looking for distro name on an ubuntu machine will tell you that you are running "Debian 3.1"...

Any way to get rid of it?

---

### Post by lt_kije on 2005-05-10
[QUOTE=saltydog]Any way to get rid of it?[/QUOTE]

You could probably just delete its contents; I don't know if it has any real purpose. In my experience, however, a better way to find the distro running on a particular machine is to check /etc/issue. In Ubuntu, this reads as follows:

Ubuntu 5.04 "Hoary Hedgehog" 

Which (I think) is what you're looking for.

HTH,

lt_kije

---

