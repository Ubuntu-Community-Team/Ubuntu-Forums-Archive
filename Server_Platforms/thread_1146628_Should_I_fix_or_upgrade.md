---
title: "Should I fix or upgrade?"
date: 2009-05-02
forum: Server Platforms
---

### Post by prosonik on 2009-05-02
Should I reinstall or fix? Setting up my ubuntu 8.10 server based NAS, I only have 150Mb after OS install. My softRAID has 2Tb. I need 700m to upgrade to 9.04. Can i reinstall, using the existing raid? Should I start from scratch?


```

    sdd1        Boot        Primary   Linux ext2                         131.61
    sdd5                    Logical   Linux ext3                        1497.01
    sdd6                    Logical   Linux swap / Solaris              1003.49
    sdd7                    Logical   Linux raid autodetect           997570.19


```

---

### Post by cariboo on 2009-05-02
If you run:

```
sudo apt-get autoremove
```

and

```
sudo apt-get clean
```

does that give you enough empty space?

---

### Post by GolemdX on 2009-05-02
What about resizing the partition? Or are they on separate hard drives like my config?

---

### Post by prosonik on 2009-05-03
tried that first off. No dice. I'm wondering if there is any apps i could uninstall

> **cariboo907 said:**
> If you run:

```
sudo apt-get autoremove
```

and

```
sudo apt-get clean
```

does that give you enough empty space?

---

### Post by prosonik on 2009-05-03
Well, I could resize. I am not sure.. I guess I could take the drive out of the raid, take 2 gigs out of the raid partition, and then add it back into the array. It sounds dicey?




> **GolemdX said:**
> What about resizing the partition? Or are they on separate hard drives like my config?

---

