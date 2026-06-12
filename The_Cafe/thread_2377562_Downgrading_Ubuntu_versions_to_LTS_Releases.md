---
title: "Downgrading Ubuntu versions to LTS Releases"
date: 2017-11-14
forum: The Cafe
---

### Post by sports fan Matt on 2017-11-14
After running Artful for a bit of time, I felt like I needed the stability of the LTS releases. Artful in my opinion is stable, but I do not have the time anymore to upgrade every six months.  Anyone else have this approach, or are there other reasons why you will not update?

---

### Post by mastablasta on 2017-11-15
you are only one upgrade away form the new LTS (it comes out next year in April).

there is no downgrade option, only fresh install.

---

### Post by sports fan Matt on 2017-11-15
You are right, it was late when I made my post.  But has anyone only used LTS'S after downloading the latest thus going back (with a reformat) to the earlier version)?

---

### Post by mastablasta on 2017-11-16
i did so once, because the new release failed to use the drivers. so i moved back to LTS, when i fixed it once and the fix held. this was still at time when LTS was supported for 3 years. now it is i 5 years of support and we are still on 14.04. i plan to move next year (or maybe already by the end of this year) to 16.04.

---

### Post by irv on 2017-11-21
When new releases come out, I always download and make a live USB and give it a test run without installing. In most cases, I end up staying with the LTS. But come April or May I most likely do another clean Install of the new LTS even though there are still four years left in the release I am using. 
I don't upgrade anymore because I find it easier to install the programs I use, and all my data is in the cloud and on a large SD card.

---

### Post by cc1984 on 2017-11-23
I used to use new releases. However, now I use Ubuntu as my work laptop and need the stability of an LTS. My organization also maintains its own repository with all the software that we develop and use which is all built on LTSs.

---

### Post by WinEunuchs2Unix on 2018-08-27
I have 1 TB HDD with Windows 10 installed using maybe 100 MB of it? I have a 512 GB NVMe SSD with Windows 10 using 400 GB of it.

So when 18.04 came out in April 2018, I shrunk Windows by 25 GB and used this script:[(Bash script to clone Ubuntu to new partition for testing 18.04 LTS upgrade)[https://askubuntu.com/questions/1028604/bash-script-to-clone-ubuntu-to-new-partition-for-testing-18-04-lts-upgrade]]("https://askubuntu.com/questions/1028604/bash-script-to-clone-ubuntu-to-new-partition-for-testing-18-04-lts-upgrade")
] to clone my 16.04 and ran 18.04 upgrade on the clone. Now I can triple boot Windows 10, Ubuntu 16.04 and Ubuntu 18.04. Periodically I reclone the 16.04 over the 18.04 partition and upgrade it all over again to see if 18.04 what improvements have been made in 18.04 upgrade process.

Now that 18.04.1 is out a lot of 16.04 users are getting sucked into automatic upgrades and regretting it. So I'm toying around with the idea of a 16.04 LTS downgrade bash script from 18.04. This thread came up on the radar whilst googling.

---

### Post by caberry9 on 2018-08-28
Is it possible to keep data on separate disk (partition) than OS? then 1) data 2) LTS 3) newest and work on the same 1) ?

---

### Post by Frogs Hair on 2018-08-30
> **caberry9 said:**
> Is it possible to keep data on separate disk (partition) than OS? then 1) data 2) LTS 3) newest and work on the same 1) ?


[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I have never tried creating or using a separate home partition though I do recall some users having difficulty with upgrades even with a separate partition. I compress files and use a removable drive to store files while performing upgrades or clean installations. It's still wise to backup your files prior to upgrade or installations  even if you have a home partition. The removable drive option works best for me and I don't have to deal with creating any partitions for data.

---

