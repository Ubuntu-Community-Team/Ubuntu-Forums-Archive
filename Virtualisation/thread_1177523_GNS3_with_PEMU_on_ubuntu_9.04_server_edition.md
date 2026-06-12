---
title: "GNS3 with PEMU on ubuntu 9.04 server edition"
date: 2009-06-03
forum: Virtualisation
---

### Post by bagseed on 2009-06-03
I am needing a cisco lab with pix emulation support "pemu". I installed gns3 via apt-get install gns3 and everything works except pemu. Apparently the ubuntu 9.04 does not install pemu or the wrapper. The documentation found thus far shows installing gns3 manually in /opt and not using the apt package manager. On my install there is nothing in /opt and therefore the only gns3 directories are in ones home /home/foo/.gns3. When you open pemu in gns3 it shows the default wrapper being in /home/foo/pemu but it's not nor anywhere on the disk. I downloaded the src for gns3 and untar'ed it and it does have the pemu wrapper so I copied it over to my home dir where gns3 is looking /home/foo/pemu/pemuwrapper.py. I also downloaded pemu and compiled it and put the pemu executable in /usr/bin/pemu. When trying to move a pix over to the setup gns3 says it cannot connect to pemu or pemuwrapper.py @ localhost. I am lost as how to get pemu working on ubuntu ...does anyone have experience with this and if so could you please advise what to do?

Thanks

---

