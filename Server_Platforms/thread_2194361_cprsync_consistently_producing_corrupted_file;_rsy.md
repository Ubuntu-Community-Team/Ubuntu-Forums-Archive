---
title: "cp/rsync consistently producing corrupted file; rsync not updating; badblocks good."
date: 2013-12-18
forum: Server Platforms
---

### Post by DiagonalArg on 2013-12-18
I'm copying one 65GB file to a USB (mechanical) hard drive.  The copy has an error according to sha1sum, but mulitple rsync's refuse to update the file.  Repeated copy produces another error, but badblocks shows no errors.  (And - unrelated - badblocks finds a larger disk than parted??)

Ideas?


Details below.


/DA


**************


sha1sum file.a
05c6643c8a7377b91c353da742891054401330a2


rsync file.a /USB; sha1sum /USB/file.a
b094c5ab8c35b7f0bd3e7553087a6360b13eba44  /USB/file.a


rsync --checksum --inplace file.a /USB; sha1sum	/USB/file.a
sent 69594878143 bytes  received 31 bytes  11615601.80 bytes/sec
total size is 69586383601  speedup is 1.00
b094c5ab8c35b7f0bd3e7553087a6360b13eba44  /USB/file.a


# Did rsync just recopy the file rather than update it?
# Are file.a & /USB/file.a really different?


cat file.a | bar -s 65g | cmp -b - /USB/file.a
- file.a differ: byte 27648851969, line 102401004 is  41 !   0 ^@


# Yes, they're different.  Let's try rsync again:
touch file.a
rsync -iv --inplace --no-whole-file file.a /USB; sha1sum /USB/file.a
>f..T...... file.a
sent 10644162 bytes  received 4778149 bytes  2951.92 bytes/sec
total size is 69586383601  speedup is 4512.06
b094c5ab8c35b7f0bd3e7553087a6360b13eba44  /USB/file.a


# Well, that appeared to update the file, but neither time did the checksum change!


rm /USB/file.a
rsync file.a /USB; sha1sum /USB/file.a
1aaaf7ffbb499edb2d07fe1b712806daab83ca93

# Another corrupted file.  Let's make sure something didn't happen to the original.


sha1sum file.a
05c6643c8a7377b91c353da742891054401330a2

# Is it the disk??


sudo badblocks -svw -t random /dev/sdc
Checking for bad blocks in read-write mode
From block 0 to 117220823
Testing with random pattern: done
Reading and comparing: done
Pass completed, 0 bad blocks found. (0/0/0 errors)


# parted reports the disk as having sectors 0 - 234440703s
# that would be blocks 0 - 117220351.  Badblocks is finding more ??


WT#??? :-?

---

### Post by nerdtron on 2013-12-18
What is capacity of the external hard drive? What is the filesystem? Is there really enough space? Sometimes reported free space or reported file sizes are not very accurate so make sure you a enough headroom to accomodate the file.

---

### Post by DiagonalArg on 2013-12-18
Capacity: 120G.  Drive is empty (other than that 65G file).  Filesystem is ext4 with default settings (5% for journal).  So, there should be enough space.

---

