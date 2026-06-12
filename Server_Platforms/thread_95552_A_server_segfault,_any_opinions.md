---
title: "A server segfault, any opinions?"
date: 2005-11-26
forum: Server Platforms
---

### Post by joepotter on 2005-11-26
I am testing a new server box. It is a cube with a new Biostar board and a Sempron 64 2500 in it. I have a fresh install of amd-64 Breezy.

It was going well until I was playing with an old box acting as the client as I tested nfs.

The old test box was known to be flaky, and I was having trouble with it when it seemed to cause a segfault on the server. The server has not done it since --- but I have a different box as the test client since then.

Question. Can a client box segfault a sever via nfs? I have not read of this, but it might be true. 

Could it be a bug in the 64 bit OS? Or, was it a hardware problem?

---

### Post by LordHunter317 on 2005-11-26
Yes, NFS client issues can cause NFS server crashes.  This isn't new.  NFS is called the Nightmare Filesystem for a reason, afterall.

---

### Post by joepotter on 2005-11-26
[QUOTE=LordHunter317]Yes, NFS client issues can cause NFS server crashes.  This isn't new.  NFS is called the Nightmare Filesystem for a reason, afterall.[/QUOTE]

Thanks for the info. I set the nfs system up 5 years ago and it just worked since then. It was this replacement server that caused me to be doing all this testing. 

Thanks for saving me the time of looking this up.

---

### Post by LordHunter317 on 2005-11-26
FWIW, if it's repeatable under the exact same conditions, it's likely a kernel bug, and worth reporting.

---

### Post by joepotter on 2005-11-27
[QUOTE=LordHunter317]FWIW, if it's repeatable under the exact same conditions, it's likely a kernel bug, and worth reporting.[/QUOTE]



I think I could segfault the box again, but I do not want to try.

You see, I think it was a faulty IDE header together with a sorry cable that caused the trouble. I admit it is odd that a cable going to the CD (and the slave IDE header) could do it --- but I have known about this trouble for a while. What a chioce for a test client box, eh?

So I took the cable out and used the primary header and one cable to run the hard drive and cdrom. Now we have stability and i threw out the old cable. (I fear the IDE secondary header is still flaky)

Heck, this box will be taken out of service soon anyway.

---

