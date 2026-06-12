---
title: "launchpad is acting funny"
date: 2016-06-08
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-06-08
I have been trying to file bugs and there seems to be a delay to logging into launchpad. When I click on a bug (and I am already logged in) it will bring me to  nowhere launchpad page sometimes and it hangs temporarily. Then I will go to another tab for a minute and then go back to bug and the info is there and says I am logged in. So it is a combination of SSO login and launchpad not bringing me directly to bug.

regards..

---

### Post by dino99 on 2016-06-08
Yesterday, checking for orphans with gtkorphan, i've purged python-cffi-backend (which was listed as an orphan). That also set a lot (~20) of other python-* packages as orphans, as well as two ubuntu-sso-client* packages.
A reboot later, loging with launchpad goes well; no trouble.

---

### Post by ventrical on 2016-06-08
I have a tendency to push my firefox tab limit with open instances of LP and other ubuntu pages.

thanks for replying.

---

### Post by grahammechanical on 2016-06-08
Yesterday "snap find" on yakkety & xenial was not accessing its repository. Then after a few hours it was working again. I think that there may have been issues with a server or two.

Probably Jorge Castro experimenting with up scaling the Ubuntu servers with Juju. :)

Regards

---

### Post by ventrical on 2016-06-08
> **grahammechanical said:**
> Yesterday "snap find" on yakkety & xenial was not accessing its repository. Then after a few hours it was working again. I think that there may have been issues with a server or two.

Probably Jorge Castro experimenting with up scaling the Ubuntu servers with Juju. :)

Regards

Yeah .. it sort of seemed like this. uh .. as like with the x11-apps freezing up .. it looked to be a server issue.

Regards..

---

