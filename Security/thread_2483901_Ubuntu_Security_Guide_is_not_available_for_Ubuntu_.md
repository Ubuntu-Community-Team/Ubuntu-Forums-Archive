---
title: "Ubuntu Security Guide is not available for Ubuntu 22.04"
date: 2023-02-12
forum: Security
---

### Post by ant2ne on 2023-02-12
instructions from site titled "Comply with CIS or DISA STIG on Ubuntu 20.04 with Ubuntu Security Guide"
[HTML]https://ubuntu.com/tutorials/comply-with-cis-or-disa-stig-on-ubuntu#4-enabling-the-ubuntu-security-guide[/HTML]

```
root@sys1:/tmp# ua enable usg
One moment, checking your subscription first
Ubuntu Security Guide is not available for Ubuntu 22.04 LTS (Jammy Jellyfish).

```

And yes, I membered with ua attach {string}
ua status --all
```
Subscription: Ubuntu Pro - free personal subscription
root@sys1:/tmp# ua status --all
SERVICE          ENTITLED  STATUS    DESCRIPTION
cc-eal           yes       n/a       Common Criteria EAL2 Provisioning Packages
esm-apps         yes       enabled   Expanded Security Maintenance for Applications
esm-infra        yes       enabled   Expanded Security Maintenance for Infrastructure
fips             yes       n/a       NIST-certified core packages
fips-updates     yes       n/a       NIST-certified core packages with priority security updates
livepatch        yes       enabled   Canonical Livepatch service
realtime-kernel  yes       disabled  Ubuntu kernel with PREEMPT_RT patches integrated
ros              yes       n/a       Security Updates for the Robot Operating System
ros-updates      yes       n/a       All Updates for the Robot Operating System
usg              yes       n/a       Security compliance and audit tools

Enable services with: pro enable <service>

     Account: ant2ne@
Subscription: Ubuntu Pro - free personal subscription

```

---

### Post by QIII on 2023-02-12
Hello!

That is something you would need to take up with Canonical.  We don't work for Canonical, so we cannot affect any change.

---

### Post by ant2ne on 2023-02-12
I was thinking maybe someone here has ran into this issue.

---

