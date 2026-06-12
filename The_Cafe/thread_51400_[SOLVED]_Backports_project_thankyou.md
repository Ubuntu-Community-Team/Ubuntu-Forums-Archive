---
title: "[SOLVED] Backports project thankyou"
date: 2005-07-23
forum: The Cafe
---

### Post by manicka on 2005-07-23
I think that the recent problems associated with firefox and conflicting system upgrades, highlights what a  great job the backports project is doing to make Ubuntu the great distro that it is.

I'd encourage anyone who feels scared off by backports to give it a go. I have never had a problem with any package I've used and even the odd staging package I've installed, like Firefox 1.0.6, have worked flawlesssly (I usually just turn staging on and off as required in my apt sources).

Thanks again to all at backports :D

---

### Post by Omnios on 2005-07-23
I didn't fully understand Baclports till I actualy read up on it in the forum thats 3 months of not using backports. I thought backports was a unstable pre release of synaptic. As I understand it now Regular Synaptic locks the version of a release on Distro date and maintains sucurity updated for these packages. Backports offer new versions of these programs that are tested and install like regular synaptic packages. Minus a few problems it seems to work realy well. Actualy I was waiting there for months waiting for the latest versions of a lot of apps.

 Hats off to The Backports and staff you do amazing work.

---

### Post by jdong on 2005-07-23
Thanks. Backports has been a pleasure for me (and the rest of the team) to do, and is an ever-growing part of Ubuntu. In fact, hoary-backports is already on archive.ubuntu.com, though still not populated.

It's very possible that when Breezy ships, its sources.list will contain commented-out breezy-backports lines along with Universe and Multiverse, so just a checkbox in Synaptic will get you Backports.


P.S. Firefox 1.0.6 is a weird guy... even though Mozilla.org claims to have fixed the API problem, the Backports 1.0.6 package that I compiled still shows the same symptoms. As a result, I've removed it from the Staging tree to prevent future problems. 1.0.4 is still offered, which is more secure than the mainline 1.0.2 that shipped with Hoary (which the Ubuntu devs are recommending that you revert to), so Backports still has an advantage in the end.

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=jdong]Thanks. Backports has been a pleasure for me (and the rest of the team) to do, and is an ever-growing part of Ubuntu. In fact, hoary-backports is already on archive.ubuntu.com, though still not populated.

It's very possible that when Breezy ships, its sources.list will contain commented-out breezy-backports lines along with Universe and Multiverse, so just a checkbox in Synaptic will get you Backports.


P.S. Firefox 1.0.6 is a weird guy... even though Mozilla.org claims to have fixed the API problem, the Backports 1.0.6 package that I compiled still shows the same symptoms. As a result, I've removed it from the Staging tree to prevent future problems. 1.0.4 is still offered, which is more secure than the mainline 1.0.2 that shipped with Hoary (which the Ubuntu devs are recommending that you revert to), so Backports still has an advantage in the end.[/QUOTE]

Newest firefox on Windows sucks a bone. A rushed release I think.....I'll stick with 1.0.4....

And for the record, Ubuntu would suck without backports. Jdong saw the biggest problem with Ubuntu and fixed it himself.

---

### Post by Burgundavia on 2005-07-24
For the record, the 1.0.2 they are recommending you revert to is the one that does have 1.0.4 patches in it.

Corey

---

### Post by psoleko on 2005-07-24
I agree the Backports project has done an amazing job and is in no way responsible for buggy releases of code. keep up the good work jdong and others.

---

### Post by somuchfortheafter on 2005-07-25
yeap go backports

---

### Post by jdong on 2005-07-25
[QUOTE=Burgundavia]For the record, the 1.0.2 they are recommending you revert to is the one that does have 1.0.4 patches in it.

Corey[/QUOTE]

> 
2) Downgrade to the Hoary version:

   sudo apt-get install mozilla-firefox=1.0.2-0ubuntu5 mozilla-firefox-gnome-support=1.0.2-0ubuntu5

   However, this will expose you to a lot of vulnerabilities.


See [http://packages.ubuntu.com/changelogs/pool/main/m/mozilla-firefox/mozilla-firefox_1.0.2-0ubuntu5.4/changelog](http://packages.ubuntu.com/changelogs/pool/main/m/mozilla-firefox/mozilla-firefox_1.0.2-0ubuntu5.4/changelog)

0ubuntu5 is the version that shipped with Hoary, which is just plain 1.0.2. the point releases to 0ubuntu5 are what added the various security patches.


So unfortunately, they're asking for us to revert to the original 1.0.2.

---

