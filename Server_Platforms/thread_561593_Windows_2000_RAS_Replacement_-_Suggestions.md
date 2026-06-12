---
title: "Windows 2000 RAS Replacement - Suggestions?"
date: 2007-09-27
forum: Server Platforms
---

### Post by ericdegen on 2007-09-27
Hello all!

I need some advice. I've been using Ubuntu (6.06 Server x64) for a while now as a platfrom for VMware hosting and I'm very pleased with how its worked out. So much so, that I would like to retire an old W2K server that has been doing FTP and RAS.

So FTP is a no brainer, but I have never setup a modem on Ubuntu, much less a dial-in solution. What should I be looking for? what is the name of the Linux Service that is comperable to RAS so I can bridge the External Modem as part of the TCP/IP local network?

Thanks in advance!

---

### Post by rennen01 on 2007-09-28
Looking in Synaptic Package Manager, I searched for remote access and found the radiusd-livingston package.  Not sure if this was the package you were referring to.

---

### Post by netlogic on 2007-09-28
[http://www.howtoforge.com/linux_dialin_server](http://www.howtoforge.com/linux_dialin_server)

---

### Post by ericdegen on 2007-10-02
Nice help there Netlogic! Looked at the post looks spot on.

My project has been put on hold for a bit, but I'll try it in a few weeks when I get the bandwidth to work on that.

---

