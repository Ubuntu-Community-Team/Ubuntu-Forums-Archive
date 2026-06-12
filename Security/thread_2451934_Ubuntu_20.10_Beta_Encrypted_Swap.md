---
title: "Ubuntu 20.10 Beta: Encrypted Swap?"
date: 2020-10-13
forum: Security
---

### Post by david509 on 2020-10-13
I'm testing Ubuntu 20.10 Beta with ZFS encryption (encrypted from the installer). Does the swap area get encrypted too? How do I check if swap is encrypted (or not)?

---

### Post by sudodus on 2020-10-13
I have not tested ZFS yet, but I suggest that you check if it works well also with ZFS with a swap file in the root partition (instead of a swap partition). Swap file is the default since a few years when using the standard ext4 file system.

If it works well, the swap will be protected by the encryption of the root file system.

---

### Post by EuclideanCoffee on 2020-10-13
You can check with this terminal command.

```

sudo blkid | grep swap

```

Return will look something like this.

```

/dev/mapper/cryptswap1: UUID="95f3d64d-6c46-411f-92f7-867e92991fd0" TYPE="swap" 

```

---

### Post by sudodus on 2020-10-13
@ EuclideanCoffee,

Thanks, this shows how it works with disk encryption. Not like in an unencrypted system :-)

---

### Post by david509 on 2020-10-13
> **EuclideanCoffee said:**
> You can check with this terminal command.

```

sudo blkid | grep swap

```

Return will look something like this.

```

/dev/mapper/cryptswap1: UUID="95f3d64d-6c46-411f-92f7-867e92991fd0" TYPE="swap" 

```

I'm seeing output similar to that, yes. I'm assuming that means encrypted swap within ZFS? :D

---

### Post by EuclideanCoffee on 2020-10-13
Yes, I believe it's working. ZFS is compatible with LUKS anyhow. :)

---

