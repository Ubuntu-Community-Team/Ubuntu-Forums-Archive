---
title: "OpenSSH version on Ubuntu 18.04.4 LTS"
date: 2020-03-16
forum: Security
---

### Post by omniware2 on 2020-03-16
Hi - I wanted to check whether OpenSSH 7.8 can safely be installed on Ubuntu 18.04.4 LTS? Does anyone have experience performing this upgrade and keeping the OpenSSH version as 7.8?

During my PCI-DSS vulnerability assessment, Qualys complains about the version of OpenSSH (7.6) that comes installed with Ubuntu 18.04.4 LTS by default - apparently there is a vulnerability in versions of OpenSSH prior to 7.8.

I wanted to know if anyone has tried this upgrade and if there would be compatibility issues or other problems. Is this upgrade recommended?

---

### Post by EuclideanCoffee on 2020-03-16
I don't recommend an upgrade.

I understand the feeling to want to simply check a box, but I want to implore you to not install 7.8 but keep the native 7.6 package with security updates. And here is why. If you update the package, you will need to continually update it specifically, and because you will need to update it specifically, it may cause issues.

Ubuntu already maintains security patches for openssh-server. There is not a compelling reason to upgrade to 7.8 that does not have security patches.

Here is 8.1 in the latest branch ready for 20.04 LTS release: [https://packages.ubuntu.com/focal/openssh-server](https://packages.ubuntu.com/focal/openssh-server)

What you would have to do from here is to download the deb package. It is located in the table below. Then from there use the following command to install it.

```

$ sudo dpkg -i *.deb
$ sudo apt install -f

```

I would do one of three things.

1. Inform management that the Qualys report is accurate, but there are security patches for various CVEs (demonstrate this with this change log [https://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_7.6p1-4ubuntu0.3/changelog](https://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_7.6p1-4ubuntu0.3/changelog)). OpenSSH says the version 7.6 but it has mitigations that 8 introduces (likely).
2. Notify management about the problems of maintaining one package version without apt and how it affects security operations. You'd need to ensure you're downloading the package and installing it regularly with checks for errors otherwise you're locked out.
3. Download and install the package with orchestration software, like Puppet or chef.

---

### Post by omniware2 on 2020-03-16
> **EuclideanCoffee said:**
> I don't recommend an upgrade.

I understand the feeling to want to simply check a box, but I want to implore you to not install 7.8 but keep the native 7.6 package with security updates. And here is why. If you update the package, you will need to continually update it specifically, and because you will need to update it specifically, it may cause issues.

Ubuntu already maintains security patches for openssh-server. There is not a compelling reason to upgrade to 7.8 that does not have security patches.

Here is 8.1 in the latest branch ready for 20.04 LTS release: [https://packages.ubuntu.com/focal/openssh-server](https://packages.ubuntu.com/focal/openssh-server)

What you would have to do from here is to download the deb package. It is located in the table below. Then from there use the following command to install it.

```

$ sudo dpkg -i *.deb
$ sudo apt install -f

```

I would do one of three things.

1. Inform management that the Qualys report is accurate, but there are security patches for various CVEs (demonstrate this with this change log [https://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_7.6p1-4ubuntu0.3/changelog](https://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_7.6p1-4ubuntu0.3/changelog)). OpenSSH says the version 7.6 but it has mitigations that 8 introduces (likely).
2. Notify management about the problems of maintaining one package version without apt and how it affects security operations. You'd need to ensure you're downloading the package and installing it regularly with checks for errors otherwise you're locked out.
3. Download and install the package with orchestration software, like Puppet or chef.

Thank you very much for your advise. We are going to report this to our PCI QSA as a false positive since Ubuntu has already patched OpenSSH with the relevant security patches.

---

