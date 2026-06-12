---
title: "Ubuntu 16 (Xenial) enabling ESM Updates result in APT 401 Unauthorized"
date: 2022-08-01
forum: Security
---

### Post by gkaufmann on 2022-08-01
I'm trying to enable ESM Updates for my Ubuntu 16 Workstation. Currently having no time to upgrade the system to newer LTS I thought this would be a good idea. I've created the ESM Update-Token and executed the command given after that step:


```

sudo ua attach C6*********SH
sudo apt-get update
(works)

sudo apt upgrade
...
342 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
342 esm-infra security updates
Need to get 261 MB of archives.
After this operation, 44,9 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Err:1 https://esm.ubuntu.com/infra/ubuntu xenial-infra-security/main amd64 bash amd64 4.3-14ubuntu1.4+esm1
  401  Unauthorized
Err:2 https://esm.ubuntu.com/infra/ubuntu xenial-infra-security/main amd64 bsdutils amd64 1:2.27.1-6ubuntu3.10+esm2
  401  Unauthorized
Err:3 https://esm.ubuntu.com/infra/ubuntu xenial-infra-security/main amd64 libpam0g-dev amd64 1.1.8-3.2ubuntu2.3+esm1
...

```

All ESM Updates fail with 401 Unauthorized!

The file '/etc/apt/auth.conf.d/90ubuntu-advantage' is present and has a password/token in it. I also tried to delete this file and rerun the esm/ua enable 'sudo ua attach C6*********SH' which re-created this file. But problem persists with 401 Unauthorized.


I thought this would be a easy-doing, but that it's somehow broken is really annoying. Any tips to fix this?

---

### Post by deadflowr on 2022-08-01
See what ```
ua status
``` shows.

---

### Post by gkaufmann on 2022-08-09
Hey @deadflowr,

thanks for trying to help out.

ua status currently shows this, as I disabled ESM temporarely (to avoid the annoying 401 Unauthorized):

```

$ sudo ua status
SERVICE          ENTITLED  STATUS    DESCRIPTION
cc-eal           yes       disabled  Common Criteria EAL2 Provisioning Packages
cis              yes       disabled  Security compliance and audit tools
esm-infra        yes       disabled  UA Infra: Extended Security Maintenance (ESM)
fips             yes       disabled  NIST-certified core packages
fips-updates     yes       disabled  NIST-certified core packages with priority security updates
livepatch        yes       n/a       Canonical Livepatch service

```


Enabling ESM it shows this:

```

$ sudo ua enable esm-infra
One moment, checking your subscription first
Updating package lists
UA Infra: ESM enabled
A reboot is required to complete install.

$ sudo ua status
SERVICE          ENTITLED  STATUS    DESCRIPTION
cc-eal           yes       disabled  Common Criteria EAL2 Provisioning Packages
cis              yes       disabled  Security compliance and audit tools
esm-infra        yes       enabled   UA Infra: Extended Security Maintenance (ESM)
fips             yes       disabled  NIST-certified core packages
fips-updates     yes       disabled  NIST-certified core packages with priority security updates
livepatch        yes       n/a       Canonical Livepatch service


```

I already rebooted in the meantime on first try, but maybe it will work giving it another try?! Don't know why a reboot is mandatory to enable apt-repository at all.

---

### Post by gkaufmann on 2022-08-15
I restarted my workstation again today after making shure ESM is enabled.

Still having trouble with 'Unauthorized' Error trying to install ESM Updates which are shown after doing 'apt update' while downloading them fails!

---

