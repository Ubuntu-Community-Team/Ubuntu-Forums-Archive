---
title: "some special behavior desired with ebcryption"
date: 2021-03-17
forum: Security
---

### Post by Skaperen on 2021-03-17
my laptop has 3 storage devices.  i haven't decided what i want to have encrypted besides /home which will be the one partition on /dev/sdc.  encrypting root?  i don't want to enter the key at the beginning.  in fact i want to not be prompted for the key all.  i want a full Ubuntu to come up entirely in the clear, with my big clock display to start at first.  i want to look like it is an unencrypted system, unless someone noses around far enough and sees lots of stuff they can't get get to because it is encrypted.  then i wlll run some hidden software (maybe om a USB stick or SD card) that enables all the decryption.  this should include a 2nd root system that is being decrypted.  may i'll just load this 2nd root in tmpfs or ramfs (a timing test will tell me if i can tolerate that initial delay).  i want to be able to start this decryption setup at any arbitrary time after booting up is complete.

the storage devices i have are:
/dev/sda 1TB spin
.dev/sdb 120GB flash SSD mostly unused (it has a 16.04 rescue system on it that has not been used
/dev/sdc 1TB spin
3x 8GB USB  minne pinne
2x 32GB USB minne pinne
1x 63GB USB minne pinne
2X 32GB SDHC cards
sda and sdc are exactly identical in sector size.

my first thought is to encrypt sdb and sdc and have a normal system on sda with a fake /home.  a regular Xubuntu install should do what i need.  then a USB minne pinne with the right stuff on it, statically linked, will be attached.   a setup script will be run which will prompt for 2 keys (for sdb and sdc)  it will then run stage2 of the setup from somewhere on sdb and/or sdc.

i wonder if containers might help.  i wonder if i can unmount all of sda so it can then be run inside a VM.

"minne pinne" ==  Norwegian("memory stick")

---

