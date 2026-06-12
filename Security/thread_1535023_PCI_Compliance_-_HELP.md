---
title: "PCI Compliance - HELP"
date: 2010-07-20
forum: Security
---

### Post by Lloyd_mcse on 2010-07-20
Hi everyone,
I'll start by saying I am completely new to any form of *nix and have only been looking into PCI Complaince for about a week, so please be patient.

My company VPS is running on ubuntu 8.04 with Plesk 9.5.2 and I need to install the latest version of apache, openssl and mod_ssl to get up to get PCI Compliance.
Unfortunatly when I do apt-get install apache2 or apt-get update it says I am running the latest version but I am only running 2.2.8 I get the same kind of thing for php5.

I have managed to download httpd-2.2.15.tar.bz2 to my /root/ folder but I have no idea what to do with them so
My question are :-

1) How do I install it to update the old version - maybe keeping old settings? Or just install it.
2) Would installing it destroy all my settings?

Also how would I disable all weak ciphers in Ubuntu, is there a file I can edit through plesk or a command I can make in putty? 
I have done everything [here]("http://www.eukhost.com/forums/f29/achieving-pci-compliance-servers-managed-plesk-9-5-a-11496/") except the cipher file it refers to wasn't there (so I created it) I also ran the pci_compliance_resolver and everything else except when I ran the command for qmail I got an invalid command and those files were not there, where else would they be?

Thanks in advance for any help :)
Kind regards

Lloyd

---

### Post by cdenley on 2010-07-20
I'm not familiar with PCI compliance, but "vulnerability scanners" which warn you about outdated software never take into account that the "outdated" server software you're running has been maintained and patched by the ubuntu package maintainer to fix any known vulnerabilities which have been discovered since that version's official release.

Running apache 2.2.8 is not the same as running ubuntu's apache2 2.2.8-1ubuntu0.15 package.
[http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.8-1ubuntu0.15/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.8-1ubuntu0.15/changelog)

Compiling new server software from source will be difficult, and will be much harder to maintain. You need the compiler stuff (build-essential), you need to install all the developer headers and dependencies it relies on, then configure, compile, and install it. To maintain it, you will either have to install security patches yourself, or you will have to keep installing the latest source available. I think this might cause stability issues.

I don't know if PCI compliance requires you to do things the hard way, but I think you're safer sticking with the repositories. Not only does the package maintainer apply security patches for you, but it has been tested and supported to work on ubuntu.

---

### Post by Bachstelze on 2010-07-20
If you're going to have to constantly update Apache and others to the latest version, Ubuntu is definitely not the right choice of OS.  Also, no offense meant, but if you have to ask such basic questions, I don't think whatever you're planning to do is going to be very secure, PCI compliant or not.  Tell your boss to hire someone who knows.  These forums are for community support, not professional, especially for security matters.

---

### Post by Lloyd_mcse on 2010-07-21
Thanks for the advice guys.
I have managed to get rid of all the php and apache warnings - mainly hiding what versions they were. but I am still getting openssl warnings to do with version, I diabled all weak ciphers which got rid of a couple more warnings. I think the rest are becuase I have medium ciphers still enabled, any ideas how I can disable all medium ciphers too? Is there a command I can make?
I have attached a pic of what I got when i did **openssl ciphers -v** 
Thanks for the advice guys, much appreciated :D
Kind regards

Lloyd

---

### Post by Bachstelze on 2010-07-21
> **Lloyd_mcse said:**
> I think the rest are becuase I have medium ciphers still enabled, any ideas how I can disable all medium ciphers too? Is there a command I can make?
I have attached a pic of what I got when i did **openssl ciphers -v** 


You choose which ciphers you want (or do not want) to use in the application that uses OpenSSL, not in OpenSSL itself.  For Apache, you do that using the SSLCipherSuite directive in /etc/apache2/mods-available/ssl.conf.

---

### Post by yeleek on 2010-07-22
> **Lloyd_mcse said:**
> Hi everyone,
My company VPS is running on ubuntu 8.04 with Plesk 9.5.2 and I need to install the latest version of apache, openssl and mod_ssl to get up to get PCI Compliance.


Far more to PCI DSS compliance than running the latest versions of software... think network segregation, data security in transit and at rest, be able to prove vulnerability management processes exist and work, access control, authentication, etc, etc, etc... (the list does go on).

I don't have to comply with PCI DSS in my day job, I know people that do though and they have years of experience in it, and its not easy.

I agree with Bachstelze, get a professional in to direct your efforts.

---

### Post by Lloyd_mcse on 2010-11-01
Thanks for the help guys,
I found the cause - Plesk :( managed to report pretty much all of the fails as false positives
 
Failing on Port 8443 - apache and openssl running the plesk system.
 
It's all good now.
Your help is much appreciated, thanks

---

