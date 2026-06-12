---
title: "[SOLVED] encrypted filesystem password change?"
date: 2008-11-05
forum: Security
---

### Post by belfasttim on 2008-11-05
Hi-- I installed Ubuntu 8.1 from the alternate install CD and chose the encrypted filesystem route.

Can anyone point me to info on how to change the passphrase? Just curious, since there's no obvious way to do it and the info I've found via searches seems pretty complicated.

Thanks

---

### Post by belfasttim on 2008-11-05
Got it figured.

For anyone who finds this thread-- 
```
sudo cryptsetup -y luksAddKey /dev/sdaN
``` 

(where N is partition # of encrypted partition-- in my case /dev/sda1)

- type in your existing key when prompted for "any key"
- you'll be notified that slot 0 is unlocked and prompted for new passphrase
- retype new passphrase

```
sudo cryptsetup luksKillSlot /dev/sdaN 0
```

- you'll be prompted for the passphrase you just set up, and it'll delete the slot with your old passphrase (slot 0)

have fun.

---

