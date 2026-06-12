---
title: "Disable Ubuntu Pro on 22.04"
date: 2024-08-06
forum: Security
---

### Post by stsparks on 2024-08-06
I have enabled Ubuntu Pro on a system in order to enable FIPS encryption, only to learn that the application it hosts will not operate under FIPS encryption.  This is Greenbone Vulnerability Manager (GVM) Community edition built from source.  The GVM Community forum tells me to disable secure linux and if that doesn't work, rebuild the system.  I have tried to disable Ubuntu Pro from the Software & Updates app Ubuntu Pro tab, but continue to get "Failed to detach. Please try again" error.  Has anyone had experience detaching from Ubuntu Pro on a system?  Any pointers for this unlucky (careless) soul?

---

### Post by #&amp;thj^% on 2024-08-06
```
sudo pro detach
Are you sure? (y/N) y
This machine is now detached.

```
Check with:
```
pro status --all
SERVICE          AVAILABLE  DESCRIPTION
anbox-cloud      no         Scalable Android in the cloud
cc-eal           no         Common Criteria EAL2 Provisioning Packages
cis              no         Security compliance and audit tools
esm-apps         no         Expanded Security Maintenance for Applications
esm-infra        no         Expanded Security Maintenance for Infrastructure
fips             no         NIST-certified FIPS crypto packages
fips-preview     no         Preview of FIPS crypto packages undergoing certification with NIST
fips-updates     no         FIPS compliant crypto packages with stable security updates
landscape        no         Management and administration tool for Ubuntu
livepatch        no         Current kernel is not covered by livepatch
realtime-kernel  no         Ubuntu kernel with PREEMPT_RT patches integrated
ros              no         Security Updates for the Robot Operating System
ros-updates      no         All Updates for the Robot Operating System

This machine is not attached to an Ubuntu Pro subscription.
See https://ubuntu.com/pro

Kernels covered by livepatch are listed here: https://ubuntu.com/security/livepatch/docs/kernels

```

---

### Post by werewulf75 on 2024-08-14
> **1fallen said:**
> ```
sudo pro detach
are you sure? (y/n) y
this machine is now detached.

```
I very nearly did this here on an old Ubuntu VM some weeks ago. Thank goodness I checked one last time that I could copy from/to 'Shared Drives' - and Bingo! An Ubuntu Pro update must have fixed the issue that had prevented this and where any such attempts would result in instant loss of any 'Shared Drives'. Major PITA that had been. :( Darn lucky I checked and **didn't** detach from Pro.

---

