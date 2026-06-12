---
title: "cryptsetup problem"
date: 2010-10-01
forum: Security
---

### Post by bradhaack on 2010-10-01
I'm trying to encrypt an external hard drive.  When I tried it throught the GUI, Disk Utility that didn't work.  So I tried the instructions on 
[https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorageOnHardy](https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorageOnHardy)

When I run:
sudo modprobe dm-crypt
sudo modprobe sha256
sudo modprobe aes

I get no feedback

When I run 
sudo cryptsetup --verify-passphrase luksFormat /dev/sdh1
The 1st time i got an error msg, 
device-mapper: reload ioctl failed: Invalid argument
Failed to setup dm-crypt key mapping for device /dev/sdh1.
Check that kernel supports aes-cbc-essiv:sha256 cipher (check syslog for more info).

Where is syslog? 

Then I tried 
sudo cryptsetup --verify-passphrase luksFormat /dev/sdh1 -c aes -s 256 -h sha256
I get the 'are you sure' prompt then nothing.

---

### Post by bradhaack on 2010-10-01
Found syslog
Created alias file and aliases as shown in 
[https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorageOnHardy](https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorageOnHardy)

tried command line, still no effect

Went back to GUI and re-formatted drive w/ encryption option.  There is usually a mount button on the GUI but not this time.  Tried mount from the cmd line and get 
mount: unknown filesystem type 'crypto_LUKS'

power cycled drive.  got prompt asking for password, then this:

Error unlocking device: cryptsetup exited with exit code 239: Device udisks-luks-uuid-2af249c9-2d65-47ac-8349-69e790353b5e-uid1000 already exists.

---

### Post by FuturePilot on 2010-10-01
> **bradhaack said:**
> 

power cycled drive.  got prompt asking for password, then this:

Error unlocking device: cryptsetup exited with exit code 239: Device udisks-luks-uuid-2af249c9-2d65-47ac-8349-69e790353b5e-uid1000 already exists.

Try
```
sudo dmsetup remove /dev/mapper/udisks-luks-uuid-2af249c9-2d65-47ac-8349-69e790353b5e-uid1000
```

Then reconnect the drive.

---

### Post by bradhaack on 2010-10-01
thx, that seems to have worked.  I still got the error msg, but it seems to be working.

---

