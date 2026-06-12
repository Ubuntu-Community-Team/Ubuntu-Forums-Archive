---
title: "what is sniff-1?"
date: 2008-12-13
forum: Security
---

### Post by tonyB on 2008-12-13
I've been running the old LTC Ubuntu -- I don't even recall the version :) -- on this machine, and I am just starting to install the newest version.  Looking around before I start I stumbled across a file in /root:

-rw------- 1 root root 12505 2008-03-15 12:01 sniff-1


That's an odd name, so I looked in google, and one link suggests it is a malicious spying tool that should be removed.  Can anyone tell me if this is correct, or is it a tool used by the system?  I do not see it on my laptop, which is running a more up-to-date release.  If bad guys have gotten to me, any suggestions as to what I need to worry about other than changing all my passwords?

Thanks for your help.

tonyB

---

### Post by Gamma746 on 2008-12-13
If someone has compromised your machine, the only way that you can trust it again is by wiping the disks and reinstalling.  They could have left any number of rootkits or backdoors on your system; changing your passwords won't help.

---

### Post by tonyB on 2008-12-14
> **Gamma746 said:**
> If someone has compromised your machine, the only way that you can trust it again is by wiping the disks and reinstalling.  They could have left any number of rootkits or backdoors on your system; changing your passwords won't help.

thanks for the reply.  i've installed the latest LTS on a different disk, so that should address the possible infection problem.

the question remains as to what this software is.  i thought i had tracked it down when i recalled installing ethereal (WireShark) some time ago, and this looks like the kind of thing it would use.  but i also have it (ethereal) on my laptop, and /root/sniff-1 is not on that machine.  even so, perhaps that is the source.  i will pursue it further.

in the meantime, thanks again.

tonyB

---

### Post by x3roconf on 2008-12-14
> **tonyB said:**
> I've been running the old LTC Ubuntu -- I don't even recall the version :) -- on this machine, and I am just starting to install the newest version.  Looking around before I start I stumbled across a file in /root:

-rw------- 1 root root 12505 2008-03-15 12:01 sniff-1


That's an odd name, so I looked in google, and one link suggests it is a malicious spying tool that should be removed.  Can anyone tell me if this is correct, or is it a tool used by the system?  I do not see it on my laptop, which is running a more up-to-date release.  If bad guys have gotten to me, any suggestions as to what I need to worry about other than changing all my passwords?

Thanks for your help.

tonyB

What's the output of ```
file sniff-1
``` and ```
cat sniff-1
``` Were all updates applied(including latest kernel)? Was OpenSSH or Apache running?

---

### Post by tonyB on 2008-12-15
> **x3roconf said:**
> What's the output of ```
file sniff-1
``` and ```
cat sniff-1
``` Were all updates applied(including latest kernel)? Was OpenSSH or Apache running?


file sniff-1:
/root/sniff-1: tcpdump capture file (little-endian) - version 2.4 (Ethernet, capture length 65535)

<<pause while I check some stuff>>


Thanks for making me pause and think a bit.  I had checked this with a file command, but I had not done it with sudo, so all it said was, effectively, "binary file".  When I did it with sudo I got the more detailed info shown above about it being a tcpdump.  I used the strings command to look at it, and this is a file created when I was trying out ethereal right after I installed it.  If I knew ethereal created files in /root I had long since forgotten.  Vagaries of old age. :)

So, the alarm bells are now off.  And my thanks for the mental nudge.

tonyB

---

