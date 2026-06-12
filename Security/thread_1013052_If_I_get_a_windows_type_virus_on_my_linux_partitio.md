---
title: "If I get a windows type virus on my linux partition can it infect my windows?"
date: 2008-12-16
forum: Security
---

### Post by Sadaiyappan on 2008-12-16
If I get a virus on my linux partition (assuming it is a windows type virus) can it infect my windows partition?

---

### Post by bodhi.zazen on 2008-12-16
There are no known "active" linux viruses that will do this. The known viruses have all been patched long ago.

---

### Post by Vantrax on 2008-12-17
I would note that if you have wine it should be theoretically possible for malware to cause a problem.

Otherwise there is no way that can happen unless you mount your linux partition from windows (and I wouldn't recommend it)

---

### Post by OrangeCrate on 2008-12-17
Just to add to what has already been said, here's a good read on Linux and viruses...

**The Truth About Linux and Viruses**

> If you dual boot Linux and Windows and get a virus-infected mail in Linux, it can NOT jump to your Windows partition. Nor can it spread over the local network to other systems. You can even store the attachment in your /home directory and open the zip or click the file, and it will be dead in the water. Windows executables won't run under Linux. Linux files need to be granted permission to become executable. And even then, it can't spread beyond the home folder. (This is also why Linux AV programs do not have a "live guard" module in them — the virus does not execute or move.) You could even leave a virus executable there as long as you wanted to without risk. Windows will not get infected, unless you deliberately copy the virus to your Windows partition.

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

