---
title: "Is it true? Hardware &amp; Software RAID - almost same performance?"
date: 2010-03-04
forum: Server Platforms
---

### Post by AlexanderDGreat on 2010-03-04
Hi! I bought / shelled out cash buying an entry level Adaptec Ultra320 SCSI Controller plus 2 Seagate 73GB's Cheetah hard disks, did Raid 1 Mirror on them, but I read here: 

1. [https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

2. [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

3. [http://www.howtoforge.com/install-ubuntu-with-software-raid-10]("http://www.howtoforge.com/install-ubuntu-with-software-raid-10")

that in benchmark, there's only a slight difference in performance in Ubuntu's Hardware and Software/Fake Raids - is this true?

Did I just waste money? Should I resell these Hardware Raid 1 Setup (anyway, buggy as hell, won't boot if 1 is down) and just use Software Raid?

Thanks for reading. :)

---

### Post by Jive Turkey on 2010-03-04
If I were you I would do some kind of benchmark with your current setup, take out the raid card or whatever and benchmark the alternative.  Then share what you learned.

Its entirely possible that the software raid is just as good for you using raid 1.  I would thing there would be a larger performance gap between striped arrays.

---

### Post by HermanAB on 2010-03-04
Yup, PCs are I/O restricted, meaning that the slight processing load of software RAID makes no difference.  Any advantage of HW RAID is mostly illusory.

---

### Post by Bachstelze on 2010-03-04
What HermanAB said. If you want a hardware RAID solution that performs better than software RAID, you'd need entreprise-class hardware with five or six zeroes on its price.

---

### Post by tgalati4 on 2010-03-04
Run some phoronix tests and post your results.

You might want to switch to SATA drives.

---

### Post by AlexanderDGreat on 2010-03-04
All right, thank you for all the replies. How do I benchmark, I'm practically a beginner, it might not be good for me doing this. Can I do this? Where do I start? :)

---

### Post by HermanAB on 2010-03-05
Something like this:
```
dd if=/dev/urandom of=bigfile bs=1000000 count=10000
date; cp bigfile /mnt/raiddisk/. ;date
xcalc
```

---

### Post by tgalati4 on 2010-03-05
sudo hdparm -tT /dev/sda

sudo apt-get install phoronix-test-suite

phoronix.com

---

### Post by AlexanderDGreat on 2010-03-06
Will definitely try all these. Thanks for your good inputs, and will post my results very soon.

---

