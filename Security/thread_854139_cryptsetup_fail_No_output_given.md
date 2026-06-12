---
title: "cryptsetup fail: No output given"
date: 2008-07-09
forum: Security
---

### Post by goldfish2 on 2008-07-09
I get the following when I run the cryptsetup command I run every day:
```
# cryptsetup -c twofish-cbc-essiv:sha256 reload TowerRaid /dev/md0 
Command failed.
```
(no password prompt, no error message, just "Commmand failed")

I have twofish running:
```
# lsmod|grep twofish
twofish                 7680  0 
twofish_common         38528  1 twofish
```

and the raid device looks like it is working properly:
```
# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[0] sde1[2] sdc1[1]
      1464967040 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
```

So what could be causing such an error?

Thanks,
GoldFish2

---

### Post by goldfish2 on 2008-07-25
I have no idea what this issue could be.  Anyone have any ideas?

---

### Post by hyper_ch on 2008-07-26
how about "sudo"?

---

### Post by goldfish2 on 2008-07-26
Slight break of Ubuntu security protocols there... I typed
```
$sudo su
```
before entering those commands, hence the # which by the default bash prompt represents super user permissions.

Just to confirm I tried the same commands as a user using sudo giving me the exact same results.

These error messages only occur sometimes... haven't figured exactly what I'm doing to make it not work... though I did recently comment out my crypttab line for this device of
```
TowerRaid /dev/md0 none cipher=twofish
```
because this prompts for my password during boot and is entered in as plaintext (I can see the password I'm typing) and even if I type in the correct password, it doesn't work (unknown fs when I try to mount it) so I have to run cryptsetup when my computer finishes booting anyway.

Thanks in advance for any tips you may have,
GoldFish2

---

