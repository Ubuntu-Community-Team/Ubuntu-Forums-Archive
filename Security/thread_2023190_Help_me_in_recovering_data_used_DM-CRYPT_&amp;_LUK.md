---
title: "Help me in recovering data used DM-CRYPT &amp; LUKS"
date: 2012-07-12
forum: Security
---

### Post by newbie15 on 2012-07-12
Hi all,

I was just trying to familiarize the working of dm-crypt with LUKS. By mistake i've used the boot volume to do that. Now i've forgotten the password and trying to mount that partition as another disk on other VM. The below is the luksDump.

Can anyone let me know the procedure to get my data back...
I'm really clueless at this point...

root@ubuntu:~# cryptsetup luksDump /dev/sdb
LUKS header information for /dev/sdb

Version:        1
Cipher name:    aes
Cipher mode:    cbc-essiv:sha256
Hash spec:      sha1
Payload offset: 2056
MK bits:        256
MK digest:      49 ad c7 7d c1 97 a8 3a c8 56 41 a0 70 66 4d 98 34 ec f1 2c
MK salt:        2d 19 41 ef e3 dc 6c 1e c3 92 d4 6d ec 61 2f 28
                1d b7 44 e7 32 5a 1e fb e2 44 be 7e 8a d9 64 70
MK iterations:  37875
UUID:           30ea302a-4ceb-478f-8aa5-8a22685c66c3

Key Slot 0: DISABLED
Key Slot 1: DISABLED
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED

---

### Post by Cheesemill on 2012-07-12
If you don't have the password you can't get your data back.
 
Encryption would be pretty pointless if you could :)

---

### Post by newbie15 on 2012-07-12
Thank you CheeseMill,
 
one more query is my header looking good or has it became useless?

---

