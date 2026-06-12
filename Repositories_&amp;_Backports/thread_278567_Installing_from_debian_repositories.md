---
title: "Installing from debian repositories"
date: 2006-10-16
forum: Repositories &amp; Backports
---

### Post by prototype_angel on 2006-10-16
I want to install from a debian repository (because it's on my local network and updates are extremely fast) I changed source.list to include the appropriate packages (nonfree/unoffical/official/contrib/unstable) and commented out the remaining, but whenever I try to upgrade or install, it downloads the exttensive package list but gives me an error whenever I try to upgrade claiming packages are broken or gives some dependancies. If anyone else uses debian mirrors, please tell me. thanks.

---

### Post by sitedesign on 2006-10-16
I am not sure if debian sources will work for ubuntu since ubuntu has diffrences. I know it is based on debian but more up to date however some of the packages are modified.

You could try mounting the place where the packages are then using the gdebi package manager to install them.

Just in case what are you adding as your sources line for the repository (local network one).

I will try to monitor this thread for a while to see how you get on. I have built repositories in the past my self for quick installs but that was for all ubuntu pc's not a mix of debian and ubuntu.

---

### Post by kerry_s on 2006-10-16
I've used a few deb's but never the all the repo's. I think your just asking for trouble there. But it's your system and if you want to try, make sure you back up the stuff you want to keep.

What is the exact error your getting can you paste it here for us to look at?

What the heck, is wh-o-l-e blocked or something? Typing it with out dashes h-o-l-e get's replaced with ****.

---

### Post by SpEcIeS on 2006-10-19
Sometimes you can have success with uninstallable [COLOR="Red"]**Debian**[/COLOR] packages by compiling the sources yourself. Use the **apt-get source -b** option, but remember to remove your [COLOR="Red"]**Debian**[/COLOR] lines in the *sources.list* when done.

---

### Post by az on 2006-10-19
To reiterate, Debian and Ubuntu are not binary-compatible.  Avoid mixing repositories.

---

