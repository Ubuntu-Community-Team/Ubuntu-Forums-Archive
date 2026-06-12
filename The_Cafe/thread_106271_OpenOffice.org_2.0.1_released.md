---
title: "OpenOffice.org 2.0.1 released"
date: 2005-12-20
forum: The Cafe
---

### Post by linbetwin on 2005-12-20
DistroWatch lists it in its "Latest Packages" section, but on openoffice.org it's still an RC.

---

### Post by earobinson on 2005-12-20
:)

NOTE: If this is not a support question it should be in the community chat. Could a mod pleas move it to the community chat.

---

### Post by linbetwin on 2005-12-20
[quote=earobinson]NOTE: If this is not a support question it should be in the community chat. Could a mod pleas move it to the community chat.[/quote]

Sorry! :oops:

---

### Post by earobinson on 2005-12-20
not a problem, It was not even ment to criticize you. Just to inform / remind you and everyone else.

Back on topic im super hyped about open office all the same.

---

### Post by esperantisto on 2005-12-21
Related to support: will there be .deb's to install OOo 2.0.1 under Ubuntu?

---

### Post by Juippisi on 2005-12-21
[QUOTE=esperantisto]Related to support: will there be .deb's to install OOo 2.0.1 under Ubuntu?[/QUOTE]

I bet that someone will at least make 'em. You just need a little patience my friend.

---

### Post by Juippisi on 2005-12-21
[ftp://ftp.sunet.se/pub/Office/OpenOffice.org/stable/](ftp://ftp.sunet.se/pub/Office/OpenOffice.org/stable/)

Released or not, it still haven't reach the mirrors.
... at least all of them

[http://mirrors.isc.org/pub/openoffice/stable/2.0.1/OOo_2.0.1_src.tar.gz](http://mirrors.isc.org/pub/openoffice/stable/2.0.1/OOo_2.0.1_src.tar.gz)

---

### Post by esperantisto on 2005-12-21
At least one mirror is reached:
[http://ftp.belnet.be/pub/mirror/ftp.openoffice.org/stable/2.0.1/OOo_2.0.1_LinuxIntel_install_wJRE.tar.gz](http://ftp.belnet.be/pub/mirror/ftp.openoffice.org/stable/2.0.1/OOo_2.0.1_LinuxIntel_install_wJRE.tar.gz)

&#8230;but RPM's, as usual&#8230;

---

### Post by Wes24 on 2005-12-21
Here is another mirror: [http://ftp.snt.utwente.nl/pub/software/openoffice/stable/2.0.1/]("http://ftp.snt.utwente.nl/pub/software/openoffice/stable/2.0.1/")

---

### Post by RikoW on 2005-12-21
Why don't you .... impatient .... guys just get the rpm, convert them to deb via alien and install them using dpkg:

```
gunzip OOo_2.0.1_LinuxIntel_install.tar.gz
tar -xvf OOo_2.0.1_LinuxIntel_install.tar
cd OOA680_m1_native_packed-1_en-US.8990/RPMS
sudo alien *.rpm
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg openoffice.org-debian-menus_2.0.1-1_all.deb
```

Worked fine for me, except that there was a problem with the base module. But after removing that with synaptic and then to a dpkg -i on the failed module, everything was fine.

Cheers,

            Riko

---

### Post by earobinson on 2005-12-21
nice improvments

---

### Post by Juippisi on 2005-12-22
[http://www.openoffice.org/](http://www.openoffice.org/) - so, there it is.

[quote="earobinson"]nice improvments[/quote]
Indeed -> [http://development.openoffice.org/releases/2.0.1.html](http://development.openoffice.org/releases/2.0.1.html)

---

### Post by Sebby on 2005-12-23
[QUOTE=RikoW]```
gunzip OOo_2.0.1_LinuxIntel_install.tar.gz
tar -xvf OOo_2.0.1_LinuxIntel_install.tar
cd OOA680_m1_native_packed-1_en-US.8990/RPMS
sudo alien *.rpm
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg openoffice.org-debian-menus_2.0.1-1_all.deb
```

Worked fine for me, except that there was a problem with the base module. But after removing that with synaptic and then to a dpkg -i on the failed module, everything was fine.[/QUOTE]
Work fine for me. To avoid any problems, I removed all traces of OpenOffice.org using Synaptic first.

In the last line of that guide, there's a *-i* missing. ;)

---

### Post by curuxz on 2005-12-23
What are the changes? worth the upgrade or wait till it is released as an autoupdate via synaptic?

---

### Post by Sebby on 2005-12-23
[QUOTE=curuxz]What are the changes? worth the upgrade or wait till it is released as an autoupdate via synaptic?[/QUOTE]
See post #12. :)

---

### Post by curuxz on 2005-12-23
lol but do the people HERE think its worth it, i mean Oo aint exactly going to say nah its rubish. Whats the honest verdict worth spending some time upgrading?

---

### Post by Sebby on 2005-12-23
Well, there's been some significant changes since 2.0 final. Being an ex-Windows (and thus Office) user, OpenOffice.org has been a bit buggy for me, and some how not quite as good. Upgrading from 1.9.5 (I think) to 2.0 final was a significant improvement, and I expect 2.0.1 to not disappoint. Having not had much of a chance to use it yet, I can't say much more than that. :p

---

### Post by bootleg on 2005-12-27
So fare it worked fine for me (german version).

Thanks. :smile:

---

### Post by BWF89 on 2005-12-27
I got OOo 2.0.1 a few days ago (Windows version). I wish they'd just update my current software rather than doing a complete reinstall everytime I update it. Especially for such a minor upgrade.

Still the best suite out there though.

---

