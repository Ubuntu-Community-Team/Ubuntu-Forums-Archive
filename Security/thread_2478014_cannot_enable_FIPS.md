---
title: "cannot enable FIPS"
date: 2022-08-14
forum: Security
---

### Post by rouge24 on 2022-08-14
I followed the FIPS enable  procedures and only Livepatch is active

$ ua status
SERVICE          ENTITLED  STATUS    DESCRIPTION
cc-eal                        yes       n/a            Common Criteria EAL2 Provisioning Packages
esm-infra                   yes       disabled   UA Infra: Extended Security Maintenance (ESM)
fips                            yes       disabled   NIST-certified core packages
fips-updates              yes       disabled   NIST-certified core packages with priority security updates
livepatch                   yes       enabled    Canonical Livepatch service
usg                           yes       disabled   Security compliance and audit tools

Enable services with: ua enable <service>

The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810
Ign:14 [https://download.videolan.org/pub/debian/stable](https://download.videolan.org/pub/debian/stable) ./ Release.gpg
Reading package lists...

APT update failed.
APT update failed to read APT config for the following URLs:
- [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org)
- [https://download.videolan.org/pub/debian/stable](https://download.videolan.org/pub/debian/stable).

---

