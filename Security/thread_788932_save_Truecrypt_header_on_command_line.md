---
title: "save Truecrypt header on command line"
date: 2008-05-10
forum: Security
---

### Post by mo0on on 2008-05-10
Hello,

I have a problem and all the searching throught the internet didn't even give me a hint how to solve the problem.

I have a command line system and a fully encryptet hdd. I'd like to backup the header of the encryptet hdd for security reasons but all I have found is how I can do it with a gui.
The only hint I get was to use "--backup-header" but truecrypt said that it doesn't know this long option.

So maybe anyone in this forum knows how I can backup the header with only the command line.

Any tips are welcome.

so long

---

### Post by niteshifter on 2008-05-11
Hi,

this works:
```
truecrypt --backup-headers headerdata.bin truecryptvolume
```

will get the header data for the file (or device) truecryptvolume and write it to the file headerdata.bin

---

### Post by mo0on on 2008-05-11
Hello,

I've tried this but all I get is a message which say's that this long option is unknown. 
I've tried "truecrypt --backup-headers /share/header.bin /dev/sdb1" 

I'm using the Version 5.1a of truecrypt together with Ubuntu 8.04 server.

---

### Post by niteshifter on 2008-05-11
Hi,

Ah, I'm using 4.3a. The option -backup-headers works in that version, I tried it just to be sure before posting. So I thought I'd get the sources to 5.1a and take a quick look ... wow, the folks at TC have been busy, the program's structure is very different from 4.x, it will take me a while to figure that out, it's a complete rewrite.

So I'm left with asking this: What does the man page on truecrypt state, or truecrypt -h given from the command line?

---

### Post by chewearn on 2008-05-11
There were some who find v5.1a not working well.  Personally, I find the write speed horribly slow.

I think v5.0 was missing the command line options.  Not sure if v5.1a has restored all command lines in v4.3a.  Maybe "--backup-headers" is still missing.  The truecrypt forum is offline at the moment, I can't get in to look for any report/bug/etc about this.

Unfortunately, there is no v4.3a deb file for Hardy.  You would need to compile the source code yourself, plus look for a patch for Hardy kernel:
[http://ubuntuforums.org/showthread.php?t=647339](http://ubuntuforums.org/showthread.php?t=647339)

---

