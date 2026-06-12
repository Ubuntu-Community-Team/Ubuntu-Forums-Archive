---
title: "Xapi in Ubuntu 12.04 - problem with LVM, ISCSI SR"
date: 2012-05-14
forum: Virtualisation
---

### Post by zulk on 2012-05-14
Hello

I instaled xapi-xcp on Ubuntu 12.04 and i have problems with some SR drivers, lvmohba and lvmoiscsi.

When i try add SR lvmohba i got this message
SR.probe R:9990667202eb|dispatcher] Server_helpers.exec exception_handler: Got exception SR_UNKNOWN_DRIVER: [ lvmohba ]

next i look in XCP 1.1 and add symlinks to this files

LVMoHBASR -> ./LVHDoHBASR.py
LVMoISCSISR -> ./LVHDoISCSISR.py
LVMSR -> ./LVHDSR.py

drivers after this operation are present, but i've got exception from python

[20120510T14:59:26.110Z|debug|vm05|243 INET 127.0.0.1:80|SR.probe R:0fb2353fd50a|dispatcher] Server_helpers.exec exception_handler: Got exception SR_BACKEND_FAILURE: [ non-zero exit; ; Traceback (most recent call last):
  File "/usr/lib/xcp/sm/LVMoHBASR", line 220, in <module>
    SRCommand.run(LVHDoHBASR, DRIVER_INFO)
  File "/usr/lib/xcp/sm/SRCommand.py", line 261, in run
    sr = driver(cmd, cmd.sr_uuid)
  File "/usr/lib/xcp/sm/SR.py", line 136, in __init__
    self.load(sr_uuid)
  File "/usr/lib/xcp/sm/LVMoHBASR", line 94, in load
    print >>sys.stderr,self.hbasr.print_devs()
  File "/usr/lib/xcp/sm/HBASR.py", line 224, in print_devs
    self._init_hbadict()
  File "/usr/lib/xcp/sm/HBASR.py", line 64, in _init_hbadict
    if len(self.hbas.iterkeys()):
TypeError: object of type 'dictionary-keyiterator' has no len()
 ]

This drivers are supported in Ubuntu 12.04 xapi version ?
If yes how to add lvmohba SR and lvmoiscsi SR.

thanks

---

