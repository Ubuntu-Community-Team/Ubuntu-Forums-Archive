---
title: "VirtualBox 4.0 install unresolved dependencies"
date: 2010-12-31
forum: Virtualisation
---

### Post by penguin_crayons on 2010-12-31
Hi,

Running Ubuntu Studio 10.10.

I tried to install VirtualBox 4.0 from package manager and from command line following instructions on VB web site and I keep getting unresolved dependencies:

virtualbox-4.0:
  Depends: libqtcore4 (>=4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
  Depends: libqtgui4 (>=4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
  Depends: libssl0.9.8 (>=0.9.8m-1) but 0.9.8k-7ubuntu8.5 is to be installed

Tried the VB forums, but no response to my registration

Any assistance would be appreciated, thanks!

Brian

---

### Post by Joe of loath on 2010-12-31
Have you tried 

```
sudo apt-get update
sudo apt-get upgrade
```

first?

---

### Post by penguin_crayons on 2010-12-31
Yep, tried that as part of VB's online instructions and it did not resolve.

Thanks for the reply!

---

### Post by sdowney717 on 2010-12-31
I installed from here
and you need the extension pack too.

[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

---

