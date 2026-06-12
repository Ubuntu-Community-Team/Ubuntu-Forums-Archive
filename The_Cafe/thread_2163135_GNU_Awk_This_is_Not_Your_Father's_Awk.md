---
title: "GNU Awk: This is Not Your Father's Awk"
date: 2013-07-17
forum: The Cafe
---

### Post by Lars Noodén on 2013-07-17
Here is a nice article about gawk:

[http://www.drdobbs.com/open-source/gnu-awk-this-is-not-your-fathers-awk/240158351](http://www.drdobbs.com/open-source/gnu-awk-this-is-not-your-fathers-awk/240158351)

Ubuntu seems to run mawk, I would have expected it to  include gawk instead.

---

### Post by markbl on 2013-07-17
I've been around a while and long ago did a lot of awk programming but I can't see the point of it anymore with languages like python available.

I still do a lot of shell programming (i.e. including sed etc) but for anything getting beyond that I jump straight to python.

---

### Post by papibe on 2013-07-17
Hi  Lars Noodén.

Great article. Thanks!

Just to be a little more precise (without knowing the actual packaging decisions), Ubuntu used to use gawk: 10.04 did, and 10.04 Server Edition still actually does.

Server 10.04:
```
**$ lsb_release -a**
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

**$ awk --version**
GNU Awk 3.1.6
Copyright (C) 1989, 1991-2007 Free Software Foundation.
...
```
Desktop 12.04:
```
**$ lsb_release -a**
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

**$ awk -W version**
mawk 1.3.3 Nov 1996, Copyright (C) Michael D. Brennan

compiled limits:
max NF             32767
sprintf buffer      2040

```
In any case, the mighty gawk is available for installation packaged as '**gawk**'. Version 3.1.8 is available on the repositories, and there's a couple of ppa for 4+ versions ([https://launchpad.net/~dns/+archive/gnu](https://launchpad.net/~dns/+archive/gnu) and [https://launchpad.net/~schot/+archive/gawk](https://launchpad.net/~schot/+archive/gawk)).

Thanks again for the heads up :)
Kind Regards.

---

### Post by cortman on 2013-07-18
How mawkish. :P

---

### Post by CharlesA on 2013-07-18
Heh, Wheezy uses GNU Awk 4.0.1

---

