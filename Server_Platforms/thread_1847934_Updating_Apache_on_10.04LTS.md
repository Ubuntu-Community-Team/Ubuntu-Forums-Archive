---
title: "Updating Apache on 10.04LTS"
date: 2011-09-21
forum: Server Platforms
---

### Post by yakatz on 2011-09-21
I have Apache 2.2.14 installed through apt-get running on 10.04LTS and I wanted to upgrade to 2.2.21.
I see that the default sources for apt in 10.04 do not have 2.2.21.
What is the best way to upgrade? 
Is there an apt source that will have 2.2.21 and not have other packages that will cause trouble (i.e. not just setting apt to look in the 11.04/11.10 sources)?
Or should I install manually from the source (I would prefer not to since then dependencies will not be tracked).

---

### Post by JonRohan on 2011-09-21
What repo's do you have? Do you have only stable releases?

---

### Post by yakatz on 2011-09-21
> **JonRohan said:**
> What repo's do you have? Do you have only stable releases?

Is this what you mean?

```
root@server-01:~# apt-get update
Hit http://download.webmin.com sarge Release.gpg
Hit http://security.ubuntu.com lucid-updates Release.gpg
Hit http://security.ubuntu.com lucid-security Release.gpg
Hit http://mirrors.xmission.com lucid Release.gpg
Hit http://mirrors.xmission.com lucid Release.gpg
Hit http://us.archive.ubuntu.com lucid Release.gpg
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Hit http://security.ubuntu.com lucid-updates Release
Hit http://mirrors.xmission.com lucid Release
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge Release.gpg
Hit http://us.archive.ubuntu.com lucid Release
Hit http://download.webmin.com sarge Release
Hit http://mirrors.xmission.com lucid Release
Hit http://security.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge Release
Ign http://mirrors.xmission.com lucid/main Packages
Ign http://mirrors.xmission.com lucid/main Sources
Hit http://security.ubuntu.com lucid-updates/main Packages
Hit http://security.ubuntu.com lucid-updates/restricted Packages
Hit http://security.ubuntu.com lucid-updates/main Sources
Hit http://security.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Ign http://download.webmin.com sarge/contrib Packages
Ign http://mirrors.xmission.com lucid/main Packages
Ign http://mirrors.xmission.com lucid/main Sources
Ign http://mirrors.xmission.com lucid/main Packages
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Ign http://mirrors.xmission.com lucid/main Sources
Ign http://mirrors.xmission.com lucid/main Packages
Ign http://mirrors.xmission.com lucid/main Sources
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib Packages
Ign http://download.webmin.com sarge/contrib Packages
Hit http://mirrors.xmission.com lucid/main Packages
Hit http://mirrors.xmission.com lucid/main Sources
Hit http://mirrors.xmission.com lucid/main Packages
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib Packages
Hit http://download.webmin.com sarge/contrib Packages
Hit http://mirrors.xmission.com lucid/main Sources

```

I don't mind adding other repos as long as it won't mess with other installed programs (postfix, openssh, MariaDB, iptables/fail2ban, Xen drivers)

---

### Post by DanielDan on 2011-10-02
I'm in the same boat as Yakatz.  Do we need to do a manual upgrade?

---

### Post by SeijiSensei on 2011-10-02
If you're concerned about a patch for the "range" exploit, it's been backported to the 2.2.14 package at [https://launchpad.net/ubuntu/+source/apache2/2.2.14-5ubuntu8.6](https://launchpad.net/ubuntu/+source/apache2/2.2.14-5ubuntu8.6).

---

