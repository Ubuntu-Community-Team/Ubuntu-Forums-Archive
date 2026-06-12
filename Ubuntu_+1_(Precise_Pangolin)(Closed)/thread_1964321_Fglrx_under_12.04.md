---
title: "Fglrx under 12.04"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Dans564 on 2012-04-23
For my machine I need the very most up-to-date drivers from AMD's website.  The install instructions located on this page [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29") just plain no longer works under 12.04 (worked fine under 11.10).  As far as I can tell its a problem with dependencies, something to do with gcc.  Although this is just a guess, my knowledge of this sort of stuff is mediocre compared to others.  Anyone have any better luck with fglrx under 12.04, and how?

---

### Post by jadtech on 2012-04-23
im running 12.04 ,Fglrx is running and working no problem ..

not sure if you did a clean install or upgraded, if you upgrade and  install (apt python-apt) before the upgrade and all runs fine from the start ..

---

### Post by jfernyhough on 2012-04-23
Use fglrx from the repo. It's Catalyst 12.4 beta.

---

### Post by Dans564 on 2012-04-23
jfernyhough thanks did not know that!  Which one the "post release driver"?

---

### Post by Dans564 on 2012-04-23
installation failed.  Jockey.log is here [http://pastebin.com/BtxPHH3S](http://pastebin.com/BtxPHH3S)

---

### Post by jfernyhough on 2012-04-23
At this point they are the same. You can check with either Synaptic (search for fglrx and compare fglrx with fglrx-updates) or with apt-cache policy:

$ apt-cache policy fglrx
fglrx:
  Installed: 2:8.960-0ubuntu1
  Candidate: 2:8.960-0ubuntu1
  Version table:
 *** 2:8.960-0ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/restricted amd64 Packages

$ apt-cache policy fglrx-updates
fglrx-updates:
  Installed: (none)
  Candidate: 2:8.960-0ubuntu1
  Version table:
     2:8.960-0ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/restricted amd64 Packages

--edit
How did you install from the AMD site? Did you uninstall them before trying Jockey?

This bit should tell more:```
Error! Bad return status for module build on kernel: 3.2.0-23-generic (x86_64)
Consult /var/lib/dkms/fglrx-updates/8.960/build/make.log for more information.
```

---

### Post by jadtech on 2012-04-23
the post release drive does not work  use the other option  it works fine has been for me for over a month now .

---

### Post by Dans564 on 2012-04-23
Tried post release with a fresh install... didn't work.  Retried using the non post release and it worked! Thanks for the help guys!  I'll mark as solved.

---

