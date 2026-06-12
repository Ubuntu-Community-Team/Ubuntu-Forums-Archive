---
title: "how to upgrade libre office?"
date: 2013-04-09
forum: Ubuntu, Linux and OS Chat
---

### Post by sachinharle on 2013-04-09
I would like to have the latest version of libreoffice on ubuntu

---

### Post by ajgreeny on 2013-04-09
Use the ppa from [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa) but be aware of the caveats mentioned on that site.  In spite of those warnings, I have LO v4.02 on a test OS of Lubuntu on an old laptop and it seems to work faultlessly.

---

### Post by rrich1974 on 2013-04-09
i guess you must add a PPA and then:
> sudo apt-get update
add probably, you will see the update in "update manager" 
take this:
[https://launchpad.net/~libreoffice/+archive/libreoffice-4-0](https://launchpad.net/~libreoffice/+archive/libreoffice-4-0)

---

### Post by rewyllys on 2013-04-09
> **ajgreeny said:**
> Use the ppa from [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa) but be aware of the caveats mentioned on that site.  In spite of those warnings, I have LO v4.02 on a test OS of Lubuntu on an old laptop and it seems to work faultlessly.
I concur in the faultless operation of LibreOffice 4.0.2.  

I'm running it on my Thinkpad T420 laptop under LinuxMint Nadia (based on Ubuntu 12.10) and on my HP d4999t desktop under LinuxMint Maya (based on Ubuntu 12.04).  On both systems I find LO 4.02 fast and easy to use.

---

### Post by MadmanRB on 2013-04-09
The update to libreoffice is optional though, as its not really a security update or anything.

---

### Post by ka55o5 on 2013-04-09
> **rewyllys said:**
> [QUOTE=ajgreeny;12595241]In spite of those warnings, I have LO v4.02 on a test OS of Lubuntu on an old laptop and it seems to work faultlessly.I concur in the faultless operation of LibreOffice 4.0.2.[/QUOTE]
Right, but that can be subject to change at **any** time, literally. The *main* PPA is marked as:
> LibreOffice test builds and backports
.. and is updated constantly; for anyone looking to use the new LibreOffice, that [ppa:libreoffice/libreoffice-4-0]("https://launchpad.net/~libreoffice/+archive/libreoffice-4-0") PPA should be used, as suggested..:)

---

