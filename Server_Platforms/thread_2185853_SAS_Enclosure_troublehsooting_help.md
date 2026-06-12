---
title: "SAS Enclosure troublehsooting help"
date: 2013-11-04
forum: Server Platforms
---

### Post by MakOwner on 2013-11-04
I have an LSI Logic SAS1068E quad port adapter with external SAS enclosures attached.
One of the enclosures, when running utilitities that walk the entire set of disks cause this error to show up in the system logs.
I have not noted any data loss or corruption yet, and I don't know if this a drive going, a port in the enclosure, a cable between the enclosure and the HBA, or even the HBA itself.

Much googlong has not given me any clues on the severity of the issue.


3.2.0-55 kernel and this is the HBA (from lshw)

```

  description: SCSI storage controller
  product: SAS1068E PCI-Express Fusion-MPT SAS
  vendor: LSI Logic / Symbios Logic

```

This is the error that shows up:

```

[ 9783.537726] mptbase: ioc1: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00) cb_idx mptbase_reply
[ 9783.555363] mptbase: ioc1: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00) cb_idx mptbase_reply
[ 9783.556073] mptbase: ioc1: LogInfo(0x31112000): Originator={PL}, Code={Reset}, SubCode(0x2000) cb_idx mptbase_reply
[ 9783.557733] mptbase: ioc1: LogInfo(0x31112000): Originator={PL}, Code={Reset}, SubCode(0x2000) cb_idx mptbase_reply
[ 9783.573546] mptbase: ioc1: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00) cb_idx mptbase_reply
[ 9785.321207] mptbase: ioc1: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00) cb_idx mptscsih_io_done
[ 9785.321257] mptbase: ioc1: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00) cb_idx mptscsih_io_done
[ 9785.321294] mptbase: ioc1: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00) cb_idx mptscsih_io_done
... Many lines of the same thing ...
[ 9785.322376] mptbase: ioc1: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00) cb_idx mptscsih_io_done
[ 9785.322410] mptbase: ioc1: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00) cb_idx mptscsih_io_done
[ 9785.322447] mptbase: ioc1: LogInfo(0x31110b00): Originator={PL}, Code={Reset}, SubCode(0x0b00) cb_idx mptscsih_io_done
[ 9793.688022] mptbase: ioc1: WARNING - IOC is in FAULT state (7810h)!!!
[ 9793.688026] mptbase: ioc1: WARNING - Issuing HardReset from mpt_fault_reset_work!!
[ 9793.688030] mptbase: ioc1: Initiating recovery
[ 9793.688033] mptbase: ioc1: WARNING - IOC is in FAULT state!!!
[ 9793.688036] mptbase: ioc1: WARNING -            FAULT code = 7810h
[ 9796.804022] mptbase: ioc1: Recovered from IOC FAULT
[ 9821.372020] mptbase: ioc1: WARNING - mpt_fault_reset_work: HardReset: success


```

---

