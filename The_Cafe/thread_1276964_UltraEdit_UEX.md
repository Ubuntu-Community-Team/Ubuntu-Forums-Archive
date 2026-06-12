---
title: "UltraEdit UEX"
date: 2009-09-27
forum: The Cafe
---

### Post by grturner on 2009-09-27
anyone else here tried the UEX beta? It's awesome and i'm looking forward to the release of it. I always liked ultraedit on windows and to have it here on linux makes it all the better. It offers text and hex editing, supports tag highlighting, project managment and filesystem browsing. It's basically an little tiny IDE that is broad spectrum. I probably don't bring it justice from what i say. From my understanding it close to being commercially released.  

Just thought i'de drop my two cents here. also a screenshot.

---

### Post by adad on 2010-02-28
I just wonder why Ubuntu repositories include non-free, trial-only versions of this software. I really like UltraEdit, the product is excellent, but I think that this inclusion does not follow Ubuntu's distribution criteria, since the product:

[LIST]
[*]is not free (as in free-beer)
[*]is not open source (but it is not declared as "restricted")
[/LIST]

Ubuntu Software Center is stating that:

License: unknown
Price: **[COLOR="Red"]free[/COLOR]** <<< This is not true

---

### Post by cimmx on 2010-03-21
I Just tried to intall UEX Version  **1.1.0.0**. on Ubunut 10.4 (beta) but it won't let my due the error:

cimmx@KnechtRuprecht:~$ sudo dpkg -i /home/cimmx/Desktop/uex_1.1.0.0_i386.deb 
(Lese Datenbank ... 141593 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von uex 1.1.0.0 (durch .../Desktop/uex_1.1.0.0_i386.deb) ...
Entpacke Ersatz für uex ...
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von uex:
 uex hängt ab von libboost-regex1.38.0 (>= 1.38.0-1); aber:
  Paket libboost-regex1.38.0 ist nicht installiert.
 uex hängt ab von libicu40 (>= 4.0-1); aber:
  Paket libicu40 istnicht installiert.

Where do I find these packages ?

Die folgenden Pakete haben nicht-erfüllte Abhängigkeiten:
  uex: Hängt ab: libboost-regex1.38.0 (>= 1.38.0-1) ist aber nicht installierbar
       Hängt ab: libicu40 (>= 4.0-1) ist aber nicht installierbar
E: Nicht-erfüllte Abhängigkeiten. Versuchen Sie, -f zu benutzen.

Ist that a beta version ubuntu problem or do I understand something wrong ?

Thanxs for your help
cimmx

---

### Post by arthpix on 2010-03-24
> **adad said:**
> I just wonder why Ubuntu repositories include non-free, trial-only versions of this software. I really like UltraEdit, the product is excellent, but I think that this inclusion does not follow Ubuntu's distribution criteria, since the product:

[LIST]
[*]is not free (as in free-beer)
[*]is not open source (but it is not declared as "restricted")
[/LIST]

Ubuntu Software Center is stating that:

License: unknown
Price: **[COLOR="Red"]free[/COLOR]** <<< This is not trueI wonder the same thing, just discovered today and have nothing against that inclusion, but to clarify the license.

---

### Post by RiceMonster on 2010-03-24
I know someone who uses this editor and loves it. It looks really nice, but I'm too cheap to pay for it.

---

### Post by cimmx on 2010-03-26
I used Ultra Edit on Windows for years, not extensively but at least once a day.

I tried Scite on Ubuntu and it fully satisfies my needs so I think it's worth a try. Still you have to learn and find everything from the beginning.

---

### Post by adad on 2010-10-24
I still see the same misleading information in Ubuntu 10.10. Theoretically free to install, but actually a 30-day trial version. The software costs $49.95. [http://www.ultraedit.com/products/uex.html](http://www.ultraedit.com/products/uex.html)
Canonical can freely include commercial software in their distro, but it should clearly stated that is commercial, not free.

---

