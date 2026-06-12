---
title: "Problem with wine+foobar2000"
date: 2010-05-15
forum: Wine
---

### Post by IvoP123 on 2010-05-15
I got some really annoying problem with foobar running with wine. Sometimes music just  stops playing and when i want to play something it says that file cannot  be found (my music folder is on external drive). After that I can't  find my external drive in computer. I have to plug it out and plug in  again so that it can be seen. Anyone has any idea?

---

### Post by TheBlueCow on 2011-02-20
Sorry for the post necromancy, but I've been having this problem for a while as well. Using foobar2000 in Wine with an external hard drive will randomly cause the drive (sdc2) to become inaccessible. I haven't been able to reproduce this behavior using a native Linux media player (vlc). Any ideas what could be causing this?

dmesg:
```

sr0: CDROM not ready.  Make sure there is a disc in the drive.
usb 1-4: USB disconnect, address 7
sd 7:0:0:0: Device offlined - not ready after error recovery
sd 7:0:0:0: [sdc] Unhandled error code
sd 7:0:0:0: [sdc]  Result: hostbyte=0x05 driverbyte=0x00
sd 7:0:0:0: [sdc] CDB: cdb[0]=0x28: 28 00 0e d7 06 30 00 00 f0 00
end_request: I/O error, dev sdc, sector 248972848
Buffer I/O error on device sdc2, logical block 15120866
Buffer I/O error on device sdc2, logical block 15120867
Buffer I/O error on device sdc2, logical block 15120868
Buffer I/O error on device sdc2, logical block 15120869
Buffer I/O error on device sdc2, logical block 15120870
Buffer I/O error on device sdc2, logical block 15120871
Buffer I/O error on device sdc2, logical block 15120872
Buffer I/O error on device sdc2, logical block 15120873
Buffer I/O error on device sdc2, logical block 15120874
Buffer I/O error on device sdc2, logical block 15120875
sd 7:0:0:0: [sdc] Unhandled error code
sd 7:0:0:0: [sdc]  Result: hostbyte=0x01 driverbyte=0x00
sd 7:0:0:0: [sdc] CDB: cdb[0]=0x28: 28 00 0e d7 07 20 00 00 10 00
end_request: I/O error, dev sdc, sector 248973088
4:3:1: cannot get freq at ep 0x84

```

---

