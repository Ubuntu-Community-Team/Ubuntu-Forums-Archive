---
title: "Is this possible?"
date: 2009-05-27
forum: The Cafe
---

### Post by hanzomon4 on 2009-05-27
I want to take a file, say a jpeg, and look at it in binary 1s and 0s. Is there a program or command that would allow me to do this?

---

### Post by Paqman on 2009-05-27
Why not just randomly put a few thousand 1's and 0's into a text file? The effect will be the same ;)

---

### Post by hanzomon4 on 2009-05-27
No it needs t be authentic... it's a part of some conceptual art tom foolery

---

### Post by burvowski on 2009-05-27
> **Paqman said:**
> Why not just randomly put a few thousand 1's and 0's into a text file? The effect will be the same ;)

hahaha this made me laugh out loud really hard for some reason

---

### Post by Sinkingships7 on 2009-05-27
> **hanzomon4 said:**
> I want to take a file, say a jpeg, and look at it in binary 1s and 0s. Is there a program or command that would allow me to do this?

A picture file would generate a LOT of those 1's and 0's you seem so fond of. I may be wrong here, but let's say you have a 50 kilobyte jpeg -- not very large at all; pretty standard. We know that each binary digit is one bit, so let's break this down.

50 kilobytes == 50 * 1000 (approx. # of bytes in a kilobyte) == 50,000 bytes.

50,000 * 8 (bits in a byte) == 400,000 bits.


So the real question here is: what could possibly come of reading 400,000 1's and 0's? May I ask what this is for? As for whether or not it's possible, I'm sure it is. However, I don't know of any ready-made programs that do this.

---

### Post by clonne4crw on 2009-05-27
Bleh. I think it would be easier to covert it to hex, then to binary. Or I would just leave it in hex. Looks prettier that way IMO.

---

### Post by boof1988 on 2009-05-27
I have heard of ways to do a hex-dump (I think this is an output of the raw data in hex) using dd [here](http://users.bigpond.net.au/hermanzone/p6.htm#What_does_an_MBR_really_look_like).  If that is possible than it should not be too difficult to either binary-dump or just convert the hex to binary.

*dunno*

Edit:
I guess hexdump is a command in itself.  Maybe there is some sort of binary dump application.

See...

```
man hexdump
```

---

### Post by Muffinabus on 2009-05-27
I wonder if you mean turning a picture into ASCII?  I can't see how thousands of 1's and 0's would classify as art, it won't look like anything.

---

### Post by Sub101 on 2009-05-27
The program ```
okteta
``` has this facility.

---

### Post by boof1988 on 2009-05-27
If you use GNOME...

ghex may be useful.

[http://linux.softpedia.com/get/Utilities/GHex-29594.shtml](http://linux.softpedia.com/get/Utilities/GHex-29594.shtml)
[http://en.wikipedia.org/wiki/Comparison_of_hex_editors](http://en.wikipedia.org/wiki/Comparison_of_hex_editors)

---

### Post by hanzomon4 on 2009-05-27
Umm.. Hex might be cool to. Basically I'm working with the idea of documentation; how the medium one choses can dramatically effect the way a particular "thing" is experienced and what can be considered a documentation. For example I performed and recorded a composition by Steve Reich (Pendulum Music) on to photo sensitive paper. The print was no less legitimate then a recording on tape but the medium I chose for "recording" transformed it from a time-based sonic experience to a very striking visual one that's completely silent.      

But yeah, I realize that it would be a lot of 1s and 0s but thats ok

---

### Post by clonne4crw on 2009-05-27
AAhhhhhh. Interesting. I'm gonna try that.

---

