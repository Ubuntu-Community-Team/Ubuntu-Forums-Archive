---
title: "LTSP | Dans | TFTP issue"
date: 2007-06-12
forum: Ubuntu Christian Edition
---

### Post by boltorg on 2007-06-12
I have an Edubuntu LTSP (2 NIC) server. 

Installed Dansguardian w/ ubuntu ce's script.

Now my client's will get DHCP from the server...
but when TFTP comes up, it times out....

If I disable Dans, TFTP works and downloads image.

---

### Post by Kitheme on 2007-06-19
I'm trying to set up a community computer lab, and I've had the same problem with Edubuntu/LTSP and Dansguardian.  When installed and configured, at PXE boot the client computers lock up on TFTP.  Anyone with ideas?

---

### Post by jmar_a06 on 2008-01-10
I have also problem in the client. I've encountered an error that is TFTP Error.

PXE - T01: File not found
PXE - E3B: TFTP Error - File not found
Operating System not found

How do I correct this one?

thanx,
jmar

---

### Post by yemu on 2008-01-18
hi
i have a similar situation, but it's strange that it's not happening on all computers connected to the server. only on 2 of them. aha, and these two were working fine, when I had dapper on my system. now i have gutsy and they don't work
y

---

### Post by yemu on 2008-01-23
upgrading bios in my compaq deskpro thinclients helped, and now they boot!

---

