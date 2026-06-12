---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-02-14
forum: Ubuntu/Debian BASED
---

### Post by minerek on 2017-02-14
Helo. I have problem with install package base-layer in my company. 

```
Setting up openclient-about (1:0.3-5) ...
dpkg: dependency problems prevent configuration of security-layer:
 security-layer depends on openclient-savap-modules; however:
  Package openclient-savap-modules is not configured yet.
 security-layer depends on openclient-savap-config; however:
  Package openclient-savap-config is not configured yet.

dpkg: error processing package security-layer (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up ibm-cck (1:2.2.4-1) ...
Processing triggers for fontconfig (2.11.94-0ubuntu2) ...
Setting up libcairo2:i386 (1.14.6-1build1) ...
dpkg: dependency problems prevent configuration of base-layer:
 base-layer depends on security-layer; however:
  Package security-layer is not configured yet.

dpkg: error processing package base-layer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up ibm-config-anyconnect (0.1-5.2) ...
Setting up ibm-3270-emulator (0.7) ...
Setting up libharfbuzz0b:i386 (1.2.7-1) ...
Setting up libpangoft2-1.0-0:i386 (1.40.1-1ubuntu1) ...
Setting up libpangoxft-1.0-0:i386 (1.40.1-1ubuntu1) ...
Setting up libpangocairo-1.0-0:i386 (1.40.1-1ubuntu1) ...
Setting up libgtk2.0-0:i386 (2.24.30-4ubuntu3) ...
Setting up libpango1.0-0:i386 (1.40.1-1ubuntu1) ...
Setting up libgail18:i386 (2.24.30-4ubuntu3) ...
Setting up libgail-common:i386 (2.24.30-4ubuntu3) ...
Setting up agnclient:i386 (1.0~2.0.1.3003-16) ...
insserv: warning: script 'K01vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'ibm-wclient' missing LSB tags and overrides
insserv: Script ibm-wclient-autostart is broken: incomplete LSB comment.
insserv: missing `Provides:' entry: please add.
insserv: warning: script 'vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'K01vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'ibm-wclient' missing LSB tags and overrides
insserv: Script ibm-wclient-autostart is broken: incomplete LSB comment.
insserv: missing `Provides:' entry: please add.
insserv: warning: script 'vpnagentd_init' missing LSB tags and overrides
Setting up connectivity-layer (2.6) ...
Setting up openclient-agnclient-notifications (0.3-3.1) ...
Processing triggers for libc-bin (2.24-3ubuntu1) ...
Errors were encountered while processing:
 openclient-savap-modules
 openclient-savap-config
 security-layer
 base-layer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
after apt-get autoremove
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 225 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up openclient-savap-modules (1.0.14-13-08ocdc2) ...
Adding SAV AP Module to DKMS build system

Creating symlink /var/lib/dkms/openclient-savap-config/1.0.14/source ->
                 /usr/src/openclient-savap-config-1.0.14

DKMS: add completed.
Doing initial module build

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
./build.sh --kernel-dir /lib/modules/4.8.0-22-generic/build --kernel-rel dkms....(bad exit status: 1)
ERROR (dkms apport): binary package for openclient-savap-config: 1.0.14 not found
Error! Bad return status for module build on kernel: 4.8.0-22-generic (x86_64)
Consult /var/lib/dkms/openclient-savap-config/1.0.14/build/make.log for more information.
dpkg: error processing package openclient-savap-modules (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of openclient-savap-config:
 openclient-savap-config depends on openclient-savap-modules; however:
  Package openclient-savap-modules is not configured yet.

dpkg: error processing package openclient-savap-config (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of security-layer:
 security-layer depends on openclient-savap-modules; however:
  Package openclient-savap-modules is not configured yet.
 security-layer depends on openclient-savap-config; however:
  Package openclient-savap-config is not configured yet.

dpkg: error processing package security-layer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of base-layer:
 base-layer depends on security-layer; however:
  Package security-layer is not configured yet.

dpkg: error processing package base-layer (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
        No apport report written because MaxReports is reached already
                                                                      Errors were encountered while processing:
 openclient-savap-modules
 openclient-savap-config
 security-layer
 base-layer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
apt-get install -f
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 225 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up openclient-savap-modules (1.0.14-13-08ocdc2) ...
Adding SAV AP Module to DKMS build system

Creating symlink /var/lib/dkms/openclient-savap-config/1.0.14/source ->
                 /usr/src/openclient-savap-config-1.0.14

DKMS: add completed.
Doing initial module build

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
./build.sh --kernel-dir /lib/modules/4.8.0-22-generic/build --kernel-rel dkms....(bad exit status: 1)
ERROR (dkms apport): binary package for openclient-savap-config: 1.0.14 not found
Error! Bad return status for module build on kernel: 4.8.0-22-generic (x86_64)
Consult /var/lib/dkms/openclient-savap-config/1.0.14/build/make.log for more information.
dpkg: error processing package openclient-savap-modules (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of openclient-savap-config:
 openclient-savap-config depends on openclient-savap-modules; however:
  Package openclient-savap-modules is not configured yet.

dpkg: error processing package openclient-savap-config (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of security-layer:
 security-layer depends on openclient-savap-modules; however:
  Package openclient-savap-modules is not configured yet.
 security-layer depends on openclient-savap-config; however:
  Package openclient-savap-config is not configured yet.

dpkg: error processing package security-layer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of base-layer:
 base-layer depends on security-layer; however:
  Package security-layer is not configured yet.

dpkg: error processing package base-layer (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
        No apport report written because MaxReports is reached already
                                                                      Errors were encountered while processing:
 openclient-savap-modules
 openclient-savap-config
 security-layer
 base-layer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Ubuntu: 16.10 x64
Trying install base-layer on clean version (as root)
Please help me.

---

