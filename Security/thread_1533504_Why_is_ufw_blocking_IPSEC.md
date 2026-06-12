---
title: "Why is ufw blocking IPSEC?"
date: 2010-07-18
forum: Security
---

### Post by movieman on 2010-07-18
I've been having problems with two systems not negotiating an IPSEC tunnel when they start up, and one thing I've noticed is messages showing ufw blocking AH packets between the two machines along the lines of:

Jul 18 01:20:23 nightmare kernel: [   17.670844] [UFW BLOCK] IN=eth0 OUT= MAC=xxxx SRC=xxxx DST=xxxx LEN=120 TOS=0x00 PREC=0x00 TTL=64 ID=6954 DF PROTO=AH SPI=0xbd5df15 

Why would ufw be blocking IPSEC packets? There's no option I can find to control IPSEC access in ufw and it's not uncommon to get these messages and then see the IPSEC link come up soon afterwards so it can't be blocking all of them.

Or does this mean that ufw is blocking whatever port the decrypted IPSEC packet is trying to connect to? In other cases it seems to display the decrypted connection instead.

---

### Post by wacky_sung on 2010-07-18
Check your ufw rules and verify what port does IPsec tunnel through for the incoming and outgoing.

[http://support.microsoft.com/kb/233256](http://support.microsoft.com/kb/233256)

---

### Post by movieman on 2010-07-18
500 is the only port that's required, and that's open. In addition, once they negotiate, they continue to work fine; it's just early on that I get these UFW BLOCK messages which don't appear to make any sense.

---

### Post by wacky_sung on 2010-07-18
Check this out below.

[http://ubuntuforums.org/showthread.php?t=1409860](http://ubuntuforums.org/showthread.php?t=1409860)

---

