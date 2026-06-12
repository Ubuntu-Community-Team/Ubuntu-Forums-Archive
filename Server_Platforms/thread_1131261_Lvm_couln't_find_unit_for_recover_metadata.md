---
title: "Lvm couln't find unit for recover metadata"
date: 2009-04-20
forum: Server Platforms
---

### Post by JDaRknight on 2009-04-20
```
root:~$ sudo vol_id /dev/sdc
ID_FS_USAGE=raid
ID_FS_TYPE=LVM2_member
ID_FS_VERSION=LVM2 001
ID_FS_UUID=u1tuW0-hHXG-hOkP-A3Eq-YtiV-YXRM-powgmE
ID_FS_UUID_ENC=u1tuW0-hHXG-hOkP-A3Eq-YtiV-YXRM-powgmE
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
root:~$ sudo pvcreate --uuid "u1tuW0-hHXG-hOkP-A3Eq-YtiV-YXRM-powgmE" --restorefile /home/+++/archive/descargas_00011.vg /dev/sdc
  Couldn't find device with uuid 'u1tuW0-hHXG-hOkP-A3Eq-YtiV-YXRM-powgmE'.
  Device /dev/sdc not found (or ignored by filtering).
```

The messages from console selfexplains the problems, I have overwriten the metadata of a volume by mistake and I am trying to restore an old backup of the metadata but the pvcreate throws two errors, it could`t find the disk wich is present in the system

---

### Post by JDaRknight on 2009-04-21
up

---

