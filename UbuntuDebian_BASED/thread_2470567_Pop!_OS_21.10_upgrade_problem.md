---
title: "Pop! OS 21.10 upgrade problem"
date: 2022-01-04
forum: Ubuntu/Debian BASED
---

### Post by larrygregory on 2022-01-04
Have done a lot of research on this the last couple of days and have  not been able to find a solution. Hoping someone here will point me in  the right direction. Thanks in advance for any assistance. Please advise if I'm not in the right forum for this.
My version is - 
Distributor ID: Pop 
Description:    Pop!_OS 21.10 
Release:    21.10 
Codename:   impish

 
Since the upgrade to 21.10 any efforts to apt-get update / upgrade,  install, or remove anything results in the following output -

 Do you want to continue? [Y/n] y Setting up rtl8821ce-dkms (5.5.2.1-0ubuntu7) ... Removing old rtl8821ce-5.5.2.1 DKMS files...
 [HR][/HR] **Deleting module version: 5.5.2.1 completely from the DKMS tree.**

 Done. Loading new rtl8821ce-5.5.2.1 DKMS files... Building for 5.15.8-76051508-generic 
Building initial module for 5.15.8-76051508-generic ERROR (dkms apport): kernel package linux-headers-5.15.8-76051508-generic is not supported 
Error! Bad return status for module build on kernel: 5.15.8-76051508-generic (x86_64) Consult /var/lib/dkms/rtl8821ce/5.5.2.1/build/make.log for more information. dpkg: error processing package rtl8821ce-dkms (--configure): installed rtl8821ce-dkms package post-installation script subprocess returned error exit status 10 
Errors were encountered while processing: rtl8821ce-dkms E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by spinnekop62 on 2022-01-04
Is there a particular reason for using that kernel when 21.10 ubuntu is on [FONT=monospace][COLOR=#000000]5.13.0-19-generic?[/COLOR]
[/FONT]

---

### Post by larrygregory on 2022-01-04
No. There is no particular reason. That is the kernel that attempts to get used when I "Update / Upgrade".

---

