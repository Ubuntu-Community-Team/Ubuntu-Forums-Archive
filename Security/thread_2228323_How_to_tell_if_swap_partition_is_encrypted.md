---
title: "How to tell if swap partition is encrypted?"
date: 2014-06-06
forum: Security
---

### Post by Bao_Niu on 2014-06-06
I am a security newbie. I used the default full-disk encryption when install ubuntu 14.04, with a strong passphrase.
One thing remain unclear is that I have a swap partition about the same size of my RAM. Is it also encrypted by default? How can I check if it is? Thanks a lot.

---

### Post by varunendra on 2014-06-07
Use command -
```
swapon --summary
```
If you see something like -
```
/dev/mapper/cryptswap1 .....
```
..your swap is encrypted. If you see a partition, like -
```
/dev/sda2 ....
```
..it is unencrypted.

---

### Post by Bao_Niu on 2014-06-07
How about this:
> njh@njh:~$ swapon --summary
Filename                Type        Size    Used    Priority
/dev/mapper/ubuntu--vg-swap_1           partition    2035708    387288    -1
njh@njh:~$

It says mapper something, is it encrypted? Many thanks.

---

### Post by varunendra on 2014-06-08
Yes it seems so, although it doesn't look like a standard Ubuntu encryption (as per [this page]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap#Preparation")). But based on the name and some unrelated links, I guess it is named so because you have LVM partitions.

Regardless of the context, a general conception says any physical partition used as swap is unencrypted, while anything 'Mapped' to /dev/mapper.... and being used as swap is encrypted swap.

What does this tell us -
```
sudo cryptsetup status ubuntu--vg-swap_1
```?

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Bao_Niu on 2014-06-08
Thank you very much for this piece of knowledge!

Here is what I got from the terminal:
```
njh@njh:~$ sudo cryptsetup status ubuntu--vg-swap_1
[sudo] password for njh: 
njh@njh:~$ 


```

As we see, it presents nothing. No info after hitting ENTER. Does it mean something?

---

### Post by HermanAB on 2014-06-11
Well, it is a statistical problem.  You could copy a block from the swap partition to a file using dd and then check to see whether the file is compressible with gzip.  If it is, then it is not encrypted.  You could also do a Chi Square test and see whether a histogram of the data is flat.

---

### Post by varunendra on 2014-06-11
> **Bao_Niu said:**
> Thank you very much for this piece of knowledge!

Here is what I got from the terminal:
```
njh@njh:~$ sudo cryptsetup status ubuntu--vg-swap_1
[sudo] password for njh: 
njh@njh:~$ 


```

As we see, it presents nothing. No info after hitting ENTER. Does it mean something?

Nothing to me, my knowledge about encrypted swaps and the command ends as soon as it starts.. :p

---

### Post by HermanAB on 2014-06-12
Soooo...
# swapon
NAME      TYPE      SIZE   USED PRIO
/dev/dm-0 partition 3.8G 151.2M   -1

# dd if=/dev/dm- of=swaptest bs=1M count=1
1+0 records in
1+0 records out
1048576 bytes (1.0 MB) copied, 0.011246 s, 93.2 MB/s

# ls -al swaptest
-rw-r--r--. 1 root root 1048576 Jun 12 08:50 swaptest

# gzip -9 swaptest

# ls -al swaptest.gz
-rw-r--r--. 1 root root 1044778 Jun 12 08:50 swaptest.gz

Hmm, it actually compressed a little bit, so my swap encryption is suspect, probably due to some repeating headers, but if it reduced by half, then it would have been clear that there is no encryption at all.

BTW, you could also look at the swaptest file with hexedit or strings and see for yourself whether there is readable stuff in there:
# dd if=/dev/dm- of=swaptest bs=1M count=1

# hexedit swaptest

00000FB4   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ....................
00000FC8   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ....................
00000FDC   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ....................
00000FF0   00 00 00 00  00 00 53 57  41 50 53 50  41 43 45 32  42 B4 A7 26  ......SWAPSPACE2B..&
00001004   59 5F 1E FC  09 62 95 E2  DC A4 9D 5D  DE 08 5C 6D  96 06 A0 FD  Y_...b.....]..\m....
00001018   20 E3 62 AE  92 5B 7D A6  68 20 4E 43  72 84 6B E9  AE CF 7F F3   .b..[}.h NCr.k.....
0000102C   C9 98 4A 78  8D 84 B6 7E  44 93 43 86  C5 C7 B2 1A  CE A6 82 91  ..Jx...~D.C.........
00001040   50 CE 42 93  BD 22 F2 E7  C9 5A 37 21  62 4A 2E FD  6D A5 34 17  P.B.."...Z7!bJ..m.4.

OK, that explains it.  The first kilobyte is zeroes, which will compress nicely.

---

