---
title: "Kern Panic when installing on Fujitsu RX350S8"
date: 2014-08-14
forum: Server Platforms
---

### Post by Rdiger on 2014-08-14
Hello,
so far I never had troubles to run Ubuntu Server Editions on various Dell, Sun/Oracle and Fujitsu Servers. On our new Fujitsu RX350S8 however I get a Kernel Panic during the installation process (seems to occur at random at some point when apt is fetching packages). My last attempt was in February this year using Saucy. I had similar results with Debian. It works with CentOs. The Server contains a Fujitsi SAS RAID Controller D3116C and a FC HBA (QLE2562). I tried without the HBA but got a similar result.

The kernel panic message is:
Hardware error from EPEI Generic Hardware Error Source: 0
APEI generic hardware error status
severity: 1, fatal
flags: 0x01
primary
fru_text: UncorrectedErr
section_type: PCIe error
command: 0x0010, status: 0x0147
device_id: 0000:00:00.1
slot:0
...

On the support Matrix of Fujitsu Debuan/Ubuntu is marked as tested- but maybe without any PCIe cards installed.

Does any one have experience with Ubuntu on the RX350S8- or hints what I could try? I guess it's because of the RAID Controller- but with the HBA installed it complained about this one first. Without the HBA it is still complaining about the RAID Controller.

It works with CentOS but Iam not really willing to mix operating systems :-).

Best wishes,

Rüdiger

---

