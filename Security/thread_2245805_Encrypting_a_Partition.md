---
title: "Encrypting a Partition"
date: 2014-09-26
forum: Security
---

### Post by Quarkrad on 2014-09-26
I have a partiton (14.04, ext4) that contains all my private data - this partition is sda4 and called **homefiles**.  I have now formatted sda4 to be an encrypted partition and when I boot, in nautilus, I see an unmounted partition called **362 GB Encrypted**.  My private data includes a number of linked spreadsheets so the name of partition (homefiles) is key to everything working. I used Disk Utility to change the label of this encrypted partition to **homefiles** and now when I boot I see 362 GB Encrypted unmounted - I click on it and get asked for my PassPhrase, and when I enter it, the partition presents itself (in nautilus) as **homefiles** and mounted.  Great - this is what I want.  During my searching to get all this working I came across a page where somebody stated:** Do not label the encrypted partition (for example with gparted), else it loses its encryption !**  Is this correct (I've only seen this once)?  Although I have encrypted sda4 I think this statement infers that by mounting it via the PassPhrase and turning it into **homefiles** it now not encrypted.  A secondary question if I may.  With reference to this shellshock issue (and potentially other 'unknown' entry points) am I right in thinking encripting sda4 offers me a degree of protection (the data is encrypted) even if somebody gets access to my pc and is  creating a keyring, so that you do have to enter you passphrase at boot, a waste of time, encryption wise, because **a n other** could get access to the passphrase, and then use that to access the encrypted data?

---

