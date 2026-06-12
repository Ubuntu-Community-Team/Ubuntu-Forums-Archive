---
title: "[SOLVED] Tape drive problems"
date: 2008-10-23
forum: Server Platforms
---

### Post by seabra on 2008-10-23
Hello 

I have an HP DAT 72 USB drive model C7438A. 
I have followed the instructions provided by HP for configuring the  tape drive and everything ***seems*** to be in place. 
I say seems because flexbackup --test-tape-drive fails all the  time.After some debugging and losing quite a couple of hours i was  trying to write files by hand to the tape after which i would execute  the command: 
mt -f /dev/st0 tell 
and the result is allways: At block 0. 
No matter how many files I write or whatever I do the result i get is  allways At block 0. 
In the begginging in used to erase the tape but it took so many hours  (2h or so) that now i just rewind it but nevertheless the result was the  same. 
Any ideas how to solve this and finnaly start making some backups? 

Kind Regards, 

João Seabra

(Also posted in the flexbackup-help mailing list)

---

### Post by seabra on 2008-10-23
ARRRGGHHH
You must use /dev/nst0 instead of /dev/st0. Including this somewhere in a not so obscure documentation would be great...

---

