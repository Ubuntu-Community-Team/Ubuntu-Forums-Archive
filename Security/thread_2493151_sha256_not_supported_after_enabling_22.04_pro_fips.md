---
title: "sha256 not supported after enabling 22.04 pro fips-updates"
date: 2023-12-05
forum: Security
---

### Post by cschanzle2 on 2023-12-05
After 'pro attach' and ensuring  fips-updates is enabled, system rebooted, and ensuring /proc/sys/crypto/fips_enabled = 1, sha256 and sha512 are not supported hashes.  For example:

```
# cryptsetup -qv luksFormat /dev/vg0/test
Enter passphrase for /dev/vg0/test:
Requested hash sha256 is not supported.
Failed to set pbkdf parameters.
Command failed with code -1 (wrong or missing parameters).
```

(add -h sha512 and it complains about sha512 not being supported).

If I boot without 'fips=1' kernel argument, cryptsetup is fine.

Note /etc/ssl/openssl.cnf has everything related to FIPS commented.  There is no fipsmodule.cnf to load.  

This issue prevents booting from mostly-encrypted systems with "Device [device] is not a valid LUKS device."
 
I know the fips modules are new for 22.04, but I'm stumped.

Thanks!

---

### Post by #&amp;thj^% on 2023-12-05
Can you show us this as well please:
```
sudo pro status --all

```
Might help us to help you.
And you did see this I assume:
> NOTE: Switching the system to contain the FIPS certified packages cannot be easily undone. We recommend to use a testing system for experimentation before trying on production.

---

### Post by cschanzle2 on 2023-12-05
Sure:

```
# pro status --all
SERVICE          ENTITLED  STATUS       DESCRIPTION
anbox-cloud      yes                disabled              Scalable Android in the cloud
cc-eal           yes                n/a                   Common Criteria EAL2 Provisioning Packages
esm-apps         yes                enabled               Expanded Security Maintenance for Applications
esm-infra        yes                enabled               Expanded Security Maintenance for Infrastructure
fips             yes                n/a                   NIST-certified FIPS crypto packages
fips-preview     yes                n/a                   Preview of FIPS crypto packages undergoing certification with NIST
fips-updates     yes                enabled               FIPS compliant crypto packages with stable security updates
landscape        yes                n/a                   Management and administration tool for Ubuntu
livepatch        yes                disabled              Current kernel is not supported
realtime-kernel  yes                disabled              Ubuntu kernel with PREEMPT_RT patches integrated
&#9500; generic        yes                disabled              Generic version of the RT kernel (default)
&#9492; intel-iotg     yes                disabled              RT kernel optimized for Intel IOTG platform
ros              yes                n/a                   Security Updates for the Robot Operating System
ros-updates      yes                n/a                   All Updates for the Robot Operating System
usg              yes                disabled              Security compliance and audit tools


Enable services with: pro enable <service>


                Account: NIST
           Subscription: Ubuntu Pro Desktop
            Valid until: Thu Apr  4 19:59:59 2024 EDT
Technical support level: essential



```

---

### Post by #&amp;thj^% on 2023-12-05
Well then you may have to run it with a --debug flag for anyone to see what could be a issue: Bug here: [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1993944](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1993944)
For the debug run as:
```
sudo cryptsetup luksDump --debug /dev/your-drive here
```
Some have stated that this will allow cryptsetup to work. "comment out the two fips related line in the openssl config
and everything works now."
Good Luck though ;)

---

### Post by cschanzle2 on 2023-12-05
> **1fallen said:**
> Well then you may have to run it with a --debug flag for anyone to see what could be a issue: Bug here: [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1993944](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1993944)
For the debug run as:
```
sudo cryptsetup luksDump --debug /dev/your-drive here
```
Some have stated that this will allow cryptsetup to work. "comment out the two fips related line in the openssl config
and everything works now."
Good Luck though ;)

Yes, I read that bug, which is for a different problem where the openssl config files were trying to load/include non-existent files.  I briefly tried to explain that in my first post where I said, "Note /etc/ssl/openssl.cnf has everything related to FIPS commented."

There is no point to a luksDump, as I'm trying to explain the problem through luksFormat on a new device, but with --debug, there is little new insight:

```
# cryptsetup -q --debug luksFormat  /dev/vg0/test 
# cryptsetup 2.4.3 processing "cryptsetup -q --debug luksFormat /dev/vg0/test"
# Running command luksFormat.
# Locking memory.
# Installing SIGINT/SIGTERM handler.
# Unblocking interruption on signal.
# Allocating context for crypt device /dev/vg0/test.
# Trying to open and read device /dev/vg0/test with direct-io.
# Initialising device-mapper backend library.
# Interactive passphrase entry requested.
Enter passphrase for /dev/vg0/test: 
# Crypto backend (OpenSSL 3.0.2 15 Mar 2022 [default][legacy]) initialized in cryptsetup library version 2.4.3.
# Detected kernel Linux 5.15.0-73-fips x86_64.
Requested hash sha256 is not supported.
Failed to set pbkdf parameters.
# Releasing crypt device /dev/vg0/test context.
# Releasing device-mapper backend.
# Unlocking memory.
Command failed with code -1 (wrong or missing parameters).

```

Can anyone replicate this or have it working with FIPS modules loaded and enabled?

---

