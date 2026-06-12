---
title: "server not booting, endless [100.1234] ata1.00 error messages"
date: 2009-08-02
forum: Server Platforms
---

### Post by bluepowder7 on 2009-08-02
hi all,

my server isn't booting anymore (not sure why), and all i get is an endless stream of [ 100.1234 ] ata1.00: error messages.  i need to get it booted up at least once to recover my files that are on 3 hard drives, since those drives are set up using LVM.  i tried a fresh install (using 8.04-64) on a separate USB flash drive to access the data drives individually, but wasn't able to (i guess the LVM info is stored on the OS drive and not on the individual LVM drives?)

the only other maybe useful bit of info that i have is that during power-on self test, it tells me that the 3rd drive (a 750G SATA) is "BAD" and that i should replace it.  the 120G and 250G (both IDE) drives are "OK" even though they're much older.  obviously i can't just replace that drive since it has the bulk of my files on it.

should i boot up with the 750G drive disconnected?

are those errors caused by the 750G drive, or the very-old 4G IDE drive that the OS is residing on?

the errors are going up to [ 892.780332 ] and still going, don't seem to stop and no other info is there that i can even begin to understand.

help!?!?

------------

ok, i unplugged the 750G SATA drive, and quickly saw this message about my LVM stuff (see attached pic - notice the red FAIL line)

so, my 750G drive was causing issues?  i can try to plug it back in, wait for the long slew of errors, and see if i get the same FAIL message...

---

### Post by dirtrider1 on 2011-07-20
I'm getting the same issue?

---

