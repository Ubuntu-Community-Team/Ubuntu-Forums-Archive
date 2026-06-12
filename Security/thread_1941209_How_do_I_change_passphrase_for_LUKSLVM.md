---
title: "How do I change passphrase for LUKS/LVM?"
date: 2012-03-15
forum: Security
---

### Post by tdn on 2012-03-15
I have encrypted rootfs with lvm/luks as chosen during install. How do I change the keys? I am aware that I can normally change luks keys with cryptsetup luksAddKey /dev/sdX, however, I am not sure whereto change the key, when using luks with LVM?

---

### Post by lovbuntu on 2012-03-15
Not something i'm familiar with but this link seems to provide information on how to do it. [http://askubuntu.com/questions/95137/how-to-change-luks-passphrase](http://askubuntu.com/questions/95137/how-to-change-luks-passphrase)

---

### Post by tdn on 2012-03-16
> **lovbuntu said:**
> Not something i'm familiar with but this link seems to provide information on how to do it. [http://askubuntu.com/questions/95137/how-to-change-luks-passphrase](http://askubuntu.com/questions/95137/how-to-change-luks-passphrase)

Yes, that page says: sudo cryptsetup -y luksAddKey ENCRYPTED_PARTITION

I know about this command, however, when I use LVM, I do not know what the value of "ENCRYPTED_PARTITION" should be. What is my LVM rootfs called? How do I check?

---

### Post by lovbuntu on 2012-03-16
To see the filesystem you would use ```
df
```

Sorry, I dont have an LVM partition to test this on.

---

### Post by Dangertux on 2012-03-16
Try lvdisplay or lgdisplay i  cant remember which but one lf those will give you the infk you need

---

### Post by tdn on 2012-03-18
lvdisplay and vgdisplay both gives a lot of output. Which one to use?

I am not sure if Ubuntu creates a LUKS device and puts lvm logical volumens inside it, or if it creates lvm on the disk and creates logical volumes each encrypted with LUKS. How do I find out?

Why does Ubuntu not provide an easy meachanism for a routine task such as changing the passphrase?

---

### Post by FuturePilot on 2012-03-18
If this is a desktop install, the Disk Utility can do this easily.

---

### Post by tdn on 2012-03-19
This is not a desktop install. 
I was not aware that Ubuntu Desktop installer could install with encrypted root?

---

### Post by FuturePilot on 2012-03-19
> **tdn said:**
> This is not a desktop install. 
I was not aware that Ubuntu Desktop installer could install with encrypted root?

No, unfortunately it can't.

---

### Post by tdn on 2012-03-20
Ok. So how do I get on with this problem?

---

### Post by Cheesemill on 2012-03-20
Your encrypted partition may be listed under /dev/mapper/lvm or something along those lines.
I don't use LVM on this system so can't tell you the exact path.

---

