---
title: "acpi_pad using 100% cpu after turning off hyperthreading"
date: 2015-03-16
forum: Server Platforms
---

### Post by kmcclure on 2015-03-16
We new have a server with Ubuntu 14.04 on it.  After doing some testing, we turned off hyperthreading in the bios to see what impact on performance it will have.  No other changes were made.  However, after we turned off hyperthreading, acpi_pad is using 100% of all remaining cpus.  The motherboard is a supermicro X10DRW-i with dual E5-2680 V3 processors and 64 GB of ram.

EXAMPLE....
 ps -ef | grep acpi_pad
root      1708     2 95 16:08 ?        00:31:50 [acpi_pad/0]
root      1709     2 95 16:08 ?        00:31:50 [acpi_pad/1]
root      1710     2 95 16:08 ?        00:31:49 [acpi_pad/2]
root      1715     2 95 16:08 ?        00:31:49 [acpi_pad/3]
root      1717     2 95 16:08 ?        00:31:49 [acpi_pad/4]
root      1718     2 95 16:08 ?        00:31:49 [acpi_pad/5]
root      1719     2 95 16:08 ?        00:31:49 [acpi_pad/6]
~TRUNCATED~

Any ideas on how to solve this?

---

### Post by eraser4 on 2015-05-06
only 1-way i found for solve this problem. This is remove power cord from server and connect again. Reset power via IPMI do not solve this.

---

### Post by eraser4 on 2016-02-03
> **kmcclure said:**
> We new have a server with Ubuntu 14.04 on it.  After doing some testing, we turned off hyperthreading in the bios to see what impact on performance it will have.  No other changes were made.  However, after we turned off hyperthreading, acpi_pad is using 100% of all remaining cpus.  The motherboard is a supermicro X10DRW-i with dual E5-2680 V3 processors and 64 GB of ram.

EXAMPLE....
 ps -ef | grep acpi_pad
root      1708     2 95 16:08 ?        00:31:50 [acpi_pad/0]
root      1709     2 95 16:08 ?        00:31:50 [acpi_pad/1]
root      1710     2 95 16:08 ?        00:31:49 [acpi_pad/2]
root      1715     2 95 16:08 ?        00:31:49 [acpi_pad/3]
root      1717     2 95 16:08 ?        00:31:49 [acpi_pad/4]
root      1718     2 95 16:08 ?        00:31:49 [acpi_pad/5]
root      1719     2 95 16:08 ?        00:31:49 [acpi_pad/6]
~TRUNCATED~

Any ideas on how to solve this?

Update BIOS for X10DRW-i to version 1.1 or higher.

---

