---
title: "Dansguardian GUI PPA"
date: 2012-09-14
forum: Ubuntu Christian Edition
---

### Post by Blunderbus on 2012-09-14
Thanks for the new Ubuntu CE. I would like to use Dansguardian GUI on other ubuntu distributions. Please can you supply with a PPA for this. Keep up the good work.

---

### Post by josephmills on 2012-09-14
Yes Very Soon. The Development team is working on setting up a ppa and some new cool features to Unity.
You can watch for it on launchpad here
[https://launchpad.net/~josephjamesmills/+archive/ubuntu-ce](https://launchpad.net/~josephjamesmills/+archive/ubuntu-ce)

---

### Post by stlsaint on 2012-09-15
You must be careful with the UCE DG Gui. It is being built for ubuntuce's firewall and privoxy+dansguardian. To use it on another distro you will need the same setup.

---

### Post by josephmills on 2012-09-15
> **stlsaint said:**
> You must be careful with the UCE DG Gui. It is being built for ubuntuce's firewall and privoxy+dansguardian. To use it on another distro you will need the same setup.

can you explain this more in detail ? thanks

---

### Post by stlsaint on 2012-09-15
> **josephmills said:**
> can you explain this more in detail ? thanks

Sure thing.
I have used UFW to handle all network traffic. Basically all network traffic passes through our proxy (privoxy) and is filtered by Dansguardian. The gui must be tailored to handle the firewall rules plus privoxy/dansguardian services. To use on another distro, that system will need to have dg,privoxy and have ufw rules. Now of course it would be possible to write the gui to maybe look for another proxy or see how net is being moved but that is not our focus right now as that will cause much more work than what we need for UCE. For our next release we are focusing on needed programs for UCE and not for other distros. First the gui will run with UCE and if devs want to keep working on it, then it can grow to aid other distros.

---

