---
title: "Audacity 1.2.6"
date: 2009-11-02
forum: Ubuntu Studio
---

### Post by judge jankum on 2009-11-02
Is it possible to install Audacity 1.2.6 on Ubuntu 9.04?
And if so how?

---

### Post by Vigh on 2009-11-03
You should be able to just click on applications, click add remove, then search for audacity, and install through add/remove.

---

### Post by judge jankum on 2009-11-03
Yes i can but it keeps giving me 1.3.7....Someone told me to try 1.2.6, that it should work better with my old pieced together puter...

---

### Post by Vigh on 2009-11-03
[http://audacity.sourceforge.net/download/](http://audacity.sourceforge.net/download/)

uninstall audacity 1.3.7

download linux version 1.2.6

you should then be able to compile and install in the terminal by

./configure
make
sudo make install

---

### Post by judge jankum on 2009-11-03
Is this with the source code? If so what are the steps i need to use?

---

### Post by Vigh on 2010-09-19
LOL having the exact same problem now, the new version of audacity is nooo good!

---

### Post by Vigh on 2010-09-19
need to build python2.4 from source, then install 2.4widgets, then build audacity1.2.6 from source

---

### Post by sgx on 2010-09-22
> **judge jankum said:**
> Is this with the source code? If so what are the steps i need to use?
Hi, the windows 'stable' audacity is 1.2xx era, which is I think where the suggestion came from, as the windows current betas have been terribly buggy compared to the linux ones. Install the current audacity in your distro with synaptic.

For loading files, the preferences option to 'load a copy' should always be used. Make sure  you have 6 gig free diskspace, and save your work at the first inkling of a slowdown in audacity, then reload. You can build up lots of temp files using audacity, hence the need for ample disk space.

Cheers

---

