---
title: "Locking version..."
date: 2012-01-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-01-06
Today I've decided to lock version of one package in PP.
Neither aptitude nor apt-get do honor that request of mine. They acknowledge that I want it locked and in next upgrade cycle they offer to upgrade that package and (if I concur) they do upgrade it.
Synaptic works fine. Lock and obey my demand...

Update: After some tail-chasing ending with ```
echo "<package_name> hold" | sudo dpkg --set-selections
``` I've managed to retain my usage of aptitude and apt-get and keep this package not-upgraded for some time...

---

### Post by jbicha on 2012-01-06
I think it's the opposite. Synaptic doesn't work fine for locking packages because it doesn't actually lock them in apt. At least I've had problems in the past when I've tried.

---

### Post by zika on 2012-01-06
> **jbicha said:**
> I think it's the opposite. Synaptic doesn't work fine for locking packages because it doesn't actually lock them in apt. At least I've had problems in the past when I've tried.In my (today's) experience it works like this:

- if I lock version in Synaptic it honors that lock and (from within Synaptic) I can be sure it will not upgrade it...
- if I &#8222;put a package on hold&#8220; in aptitude or apt-get that means they will upgrade it the first time opportunity for that occurs... simply they will say &#8222;yes&#8220; and mean &#8222;whatever&#8220;... ;)
- if I use dpkg (as explained above) that will make aptitude and apt-get honor my wish and will not upgrade the package (merely because truly dpkg (that they use) will guard my wish)...
You can try it for yourself...

---

### Post by Harry33 on 2012-01-06
> **zika said:**
> In my (today's) experience it works like this:

- if I lock version in Synaptic it honors that lock and (from within Synaptic) I can be sure it will not upgrade it...
- if I „put a package on hold“ in aptitude or apt-get that means they will upgrade it the first time opportunity for that occurs... simply they will say „yes“ and mean „whatever“... ;)
- if I use dpkg (as explained above) that will make aptitude and apt-get honor my wish and will not upgrade the package (merely because truly dpkg (that they use) will guard my wish)...
You can try it for yourself...

Synaptic locks held packages OK, during common upgrading (= selecting "Reload" and "Apply").
However, selecting "Mark All Upgrades" also selects the locked ones.

---

### Post by dino99 on 2012-01-06
Confirm that it might warn about a package previously locked, but it dont if an update is available; not very secure. Wonder if this has been reported yet ?

---

### Post by zika on 2012-01-06
> **Harry33 said:**
> Synaptic locks held packages OK, during common upgrading (= selecting "Reload" and "Apply").
However, selecting "Mark All Upgrades" also selects the locked ones.
No. My locked package is holding on in Synaptic. Not showing either in Default or Smart Upgrade. Of course, newer version is available for weeks now...
Same is happening (now after dpkg intervention) in aptitude and apt-get... My version of that package is secure for now... ;)

Update: Right now this way of locking version passed litmus (lacmus) test: &#8222;apt-get dist-upgrade&#8220; with a lot of packages...

---

