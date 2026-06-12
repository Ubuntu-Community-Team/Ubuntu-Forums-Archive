---
title: "Multiples of a Byte prefixes"
date: 2017-03-04
forum: The Cafe
---

### Post by joelgsf on 2017-03-04
Why ubuntu does not unify the prefixes for multiples of a Byte, when in respect of stored data. As far as I know, since 1998 there is a IEC standard that established KiB for representing 2^10 = 1024 Bytes, MiB for representing 2^20 = 1,048,576 Bytes, and so on. And this only for stored data. Why only stored data, because addressing of stored data is done with an integer number of bits, and so memory capacity is better represented with a power of 2. Other measures, such as the speed of a network connection, should continue using the metric system (SI), which uses base 10, such that a 1 Mbps represents, effectively, 1,000,000 bits per second.
What I see in my Ubuntu 16.04 is that some utilities, such ls (list directory contents) will notify me, correctly, with a file of 4.9K (should be Ki) one that has 8,038 Bytes, but if I am looking at the files with Nautilus, it will show me the same file as having 8.0 KBytes.
Why not unify all views to the binary standard?

---

### Post by Perfect Storm on 2017-03-04
Moved to The Cafe.

---

### Post by The Cog on 2017-03-04
Two things:

Firstly, Ubuntu contains a large collection of utilities maintained by different authors, some use the correct prefixes, some don't. Some utility writers are being somewhat slow is adopting the correct prefixes when showing numbers (e.g. showing"MB" when actually showing mebibytes). But Ubuntu just incorporates these utilities, it doesn't attempt to correct them all.

Secondly, my opinion, why use a binary based standard that is so difficult to do maths with? All our number writing uses base 10. We think in base 10. Memory chips still tend to have sizes in powers of 2, but that's all. Hard disks, DVDs, flash drives etc. are not constrained to powers of 2. Even the memory available to the OS isn't normally a power of 2 after some has been used for I/O or video RAM mapping. So why insist on trying to quote figures multiples of 1048576 or 1073741824? That's just perverse. Why not just quote sizes in megabytes, gigabytes that don't need a calculator to work with? I would never consider quoting distances in kibimetres, or radio station frequencies in mebihertz. 

My root partition is 25668112384 bytes - 25.7 gigabytes. I challenge anyone to tell me how many gibibytes that is without a calculator. And who cares?

Edit: 
The **free** utility needs sending back to school for some basic maths tuition. Just looking at my figure for total memory:
```
steve@StevePC:~$ free -b
              total        used        free      shared  buff/cache   available
Mem:     8353525760   837775360  6265610240    28975104  1250140160  7185371136
Swap:   10485755904           0 10485755904
```
So I have 8353.52576 megabytes of memory in total.

**free --mebi** gives the correct result (rounded down): 8353525760 / 1024 / 1024 = 7966.54:
```
steve@StevePC:~$ free --mebi
              total        used        free      shared  buff/cache   available
Mem:           7966         891        5865          40        1209        6746
Swap:          9999           0        9999
```
**free --mega** gives the wrong answer. It's doing 8353525760 / 1024 / 1000 = 8157.74:
```
steve@StevePC:~$ free --mega
              total        used        free      shared  buff/cache   available
Mem:           8157         830        6105          28        1221        7004
Swap:         10239           0       10239

```
**free -h --si** also gives wrong answers. 
I suspect it's doing 8353525760 / 1000 / 1000 / 1024 = 8.15774 and rounding that result up to 8.2G:
```
steve@StevePC:~$ free -h --si
              total        used        free      shared  buff/cache   available
Mem:           8.2G        914M        6.0G         41M        1.2G        6.9G
Swap:           10G          0B         10G
```

Actually, I think it is using the free memory figure from /proc/meminfo  and sometimes treating this as kibibytes and sometimes as kilobytes. 

I think the contents of /proc/meminfo are probably actually in kibibytes (multiples of 1024, kiB) but displaying the wrong symbol (kB).  **man proc** doesn't actually state ether the values are kibi or kilo, so the confusion in **free** is partly understandable. However, Google did find this page for me: [https://kb.novaordis.com/index.php/Proc-meminfo](https://kb.novaordis.com/index.php/Proc-meminfo)

---

