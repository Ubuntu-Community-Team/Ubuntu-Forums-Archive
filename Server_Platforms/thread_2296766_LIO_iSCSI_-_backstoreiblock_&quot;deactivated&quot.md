---
title: "LIO iSCSI - backstore/iblock &quot;deactivated&quot;, with &quot;BROKEN STORAGE LINK&quot; on LUN"
date: 2015-09-28
forum: Server Platforms
---

### Post by dougti on 2015-09-28
Hey guys,
 I've recently started playing around with LIO iSCSI, with block devices on LVM. Now, after installing & configuring everything, all worked well & the initiators were able to access the LUN as normal, however after a reboot of the storage server, LIO seems to have trouble bringing it back up. I'm getting no errors in the logs, and can't for the life of me work out what's causing it. Everything was working previously, the config was saved & everything still seems to be configured correctly - so what's the issue? What's changed?
LVs activated & available & everything configured under targetcli.

Here's my targetcli root...

```
/> ls /
o- / ......................................................................................................................... [...]
  o- backstores .............................................................................................................. [...]
  | o- fileio ................................................................................................... [0 Storage Object]
  | o- iblock ................................................................................................... [1 Storage Object]
  | | o- stor00 ...................................................................................... [/dev/vg0/stor00 deactivated]
  | o- pscsi .................................................................................................... [0 Storage Object]
  | o- rd_dr .................................................................................................... [0 Storage Object]
  | o- rd_mcp ................................................................................................... [0 Storage Object]
  o- ib_srpt ........................................................................................................... [0 Targets]
  o- iscsi .............................................................................................................. [1 Target]
  | o- iqn.1995-01.com.example:dc0.stor00 ...................................................................................... [1 TPG]
  |   o- tpgt1 ........................................................................................................... [enabled]
  |     o- acls ............................................................................................................ [1 ACL]
  |     | o- iqn.1995-01.com.example:dc0 ................................................................................ [1 Mapped LUN]
  |     |   o- mapped_lun0 ....................................................................................... [BROKEN LUN LINK]
  |     o- luns ............................................................................................................ [1 LUN]
  |     | o- lun0 ............................................................................................ [BROKEN STORAGE LINK]
  |     o- portals ...................................................................................................... [1 Portal]
  |       o- 10.20.200.28:3260 ................................................................................ [OK, iser disabled]
  o- loopback .......................................................................................................... [0 Targets]
  o- qla2xxx ........................................................................................................... [0 Targets]
  o- tcm_fc ............................................................................................................ [0 Targets]
/>
```

...and to show that the LVs are activated:
```
root@stor0:/var/log# lvs
  LV                                       VG                                                 Attr      LSize   Pool Origin Data%  Move Log Copy%  Convert
  LV-0d9b082b-71c8-4999-8b5c-e479f7d61867  VG_XenStorage-a53629f8-dd21-5dcf-6fa0-8ebec213f2f8 -wi-a---- 256,00m
  LV-470c4026-a950-4860-9232-d6cf225198a2  VG_XenStorage-a53629f8-dd21-5dcf-6fa0-8ebec213f2f8 -wi-a----   4,00m
  MGT                                      VG_XenStorage-a53629f8-dd21-5dcf-6fa0-8ebec213f2f8 -wi-a----   4,00m
  VHD-1f276101-f6fb-4fb9-9b86-4537d2187421 VG_XenStorage-a53629f8-dd21-5dcf-6fa0-8ebec213f2f8 -wi-a----  20,05g
  VHD-e0028b47-0100-4f76-999c-133021eaf97f VG_XenStorage-a53629f8-dd21-5dcf-6fa0-8ebec213f2f8 -wi-a----  30,07g
  VHD-ee4f8685-2e75-452d-a1e8-2145a8730d25 VG_XenStorage-a53629f8-dd21-5dcf-6fa0-8ebec213f2f8 -wi-a----  15,04g
  root                                     vg0                                                -wi-ao---   9,31g
  stor00                                   vg0                                                -wi-ao---   1,32t
  swap                                     vg0                                                -wi-ao---   3,72g
  tmp                                      vg0                                                -wi-ao---   9,31g
  var                                      vg0                                                -wi-ao---   5,00g
root@stor0:/var/log#
```

Now reading around, I suspect the iblock is "deactivated" because the LUN is set as broken. But I can't understand what would have broken the LUN.
Any ideas?

Many thanks in advance!

---

### Post by craig_2 on 2015-10-27
I've hit the same problem with QLA2xxx adapter and fileio backstore. It happens for me after a reboot (of Ubuntu 14.04 LTS Desktop with all current updates applied).

Did you find a reason for this?

---

### Post by craig_2 on 2015-10-29
Hi
I switched to server and discovered the reason for this situation (in my case).

I had not defined the backstore mount point as a system wide mount. 

Once I defined the appropriate entry in /etc/fstab the configuration was ok after a reboot.

I hope this helps someone.

---

