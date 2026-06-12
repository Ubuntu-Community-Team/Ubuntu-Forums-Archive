---
title: "Alternative to DeepFreeze"
date: 2009-01-26
forum: Security
---

### Post by ddixonr on 2009-01-26
I know a lot of schools that use DeepFreeze to protect their Windows machines. In case you're unfamiliar, it is a program that allows almost unlimited access to a os, but any and all changes are eliminated upon a restart. It is turned on and off with a simple password.

I am looking for something like this for ubuntu so that I can allow people to use my machine for testing and such. I've considered alternatives to this method such as live cds, but I have settled on this idea.

You see I know of plenty of ways to limit access to sensitive areas of the file system, but I would prefer to let them to break the machine if it happens that way. I think it is the best way to learn.

Anyway, any suggestions are welcomed. Thanks.

---

### Post by arvevans on 2009-01-26
Simplest way to do something like this might be the use of "bootp" which boots a UNIX or Linux system from a remote or local boot server.
[LIST]
[*][http://en.wikipedia.org/wiki/Bootstrap_Protocol]("http://en.wikipedia.org/wiki/Bootstrap_Protocol")
[*][http://www.tcpipguide.com/free/t_TCPIPBootstrapProtocolBOOTP.htm]("http://www.tcpipguide.com/free/t_TCPIPBootstrapProtocolBOOTP.htm")
[*][http://www.networksorcery.com/enp/protocol/bootp.htm]("http://www.networksorcery.com/enp/protocol/bootp.htm")
[/LIST]

Those URL's might help you decide if "bootp" is what you need, and get you started on some reference matreial.

Arv
_._

---

### Post by ddixonr on 2009-01-26
Could you save me the trouble and tell me if performance is an issue with this solution? The reason I don't use live cds is because of the performance factor.

---

### Post by albinootje on 2009-01-26
> **ddixonr said:**
> Could you save me the trouble and tell me if performance is an issue with this solution? The reason I don't use live cds is because of the performance factor.

You could do this (thin client setup) with Edubuntu.
The performance is, amongst others, limited to the network connection (traffic) and the resources on the remote machine.

---

### Post by Tubes6al4v on 2009-01-27
You could use Damn Small Linux as a live cd. It will load to RAM and run of there. Though it is not all that nice looking. There is also puppy linux, and maybe  you could load the os to ram in pen drive linux aswell. Just a thought.

---

### Post by adamlau on 2009-01-27
If a guest session is too limiting, consider virtualization with VirtualBox, or VMware under a restricted user.

---

### Post by cdenley on 2009-01-27
[http://ubuntuforums.org/showthread.php?t=1047248](http://ubuntuforums.org/showthread.php?t=1047248)

Either have changes to /home written to memory, or have changes to the entire filesystem written to memory, like with a livecd without the performance problem.

---

### Post by ddixonr on 2009-01-27
Looks good. Thanks for the tips

---

