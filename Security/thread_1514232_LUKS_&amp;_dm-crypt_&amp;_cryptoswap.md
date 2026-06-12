---
title: "LUKS &amp; dm-crypt &amp; cryptoswap"
date: 2010-06-20
forum: Security
---

### Post by koba101 on 2010-06-20
I've been successful of encrypting my H/D using LUKS and dm-crypt by following [this]("https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid").

But the problem is I couldn't manage to successfully encrypt the swap and the hibernate is not functioning 

funny part is for **swapon -s** I see this```

Filename				Type		Size	Used	Priority
/dev/mapper/cryptoswap                  partition	8393920	5480	-1
akhalfan@khalfan-laptop:~$ 


```


yet for _blkid_  I see this:
```
/dev/sda3: LABEL="System Reserved" UUID="EEBEBD02BEBCC47D" TYPE="ntfs" 
/dev/sda4: UUID="DCDCBF92DCBF6604" TYPE="ntfs" 
/dev/sda5: UUID="da8b9c96-b45f-4df2-a648-6203c8294ff3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="423519f3-af90-411e-8273-2897151cb822" TYPE="crypto_LUKS" 
/dev/mapper/cryptoroot: UUID="d3b79ee5-0685-4ee2-9fed-a66e15ed72b4" TYPE="ext4" 
akhalfan@khalfan-laptop:~$ 


```

It's not even there.....

Is there anything else that I need to be done to figure this out?

---

### Post by rookcifer on 2010-06-21
Why not just use the alternate install CD and do it from there?

---

### Post by koba101 on 2010-06-21
I don't think the alt. CD let's you create an encrypted swap and I already have a swap, but I just want it encrypted

---

### Post by rookcifer on 2010-06-21
> **koba101 said:**
> I don't think the alt. CD let's you create an encrypted swap and I already have a swap, but I just want it encrypted

Yes it does.  It lets you encrypt the whole disk or parts of the disk.  It lets you do LVM, which will allow you to encrypt multiple partitions using only one password.

---

### Post by GrantStoner on 2010-06-21
Does LUKS allow you to encrypt an entire drive/partition (except /boot)?

---

### Post by rookcifer on 2010-06-21
> **GrantStoner said:**
> Does LUKS allow you to encrypt an entire drive/partition (except /boot)?

Yes.

---

### Post by GrantStoner on 2010-06-21
Where do I get it from? How do I use it? I'm looking for a way other than using the Alternate CD.

---

### Post by koba101 on 2010-06-22
ok...problem with the alt cd is that it seems I need to install the entire OS again (didn't look clearly into it) but I tried to just partition and back out and didn't see any changes....I managed to change a few details in /etc/crypttab so now I got /dev/mapper/cryptoswap appearing in the blkid but I still can't hibernate

funny part is that even if i don't hibernate when i startup the computer I get the message **"cannot resume stat /dev/mapper/cryptoswap**

Seems there's something else I need to look into

GrantStoner:  I followed the tutorials (mainly this one [https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid) )

---

