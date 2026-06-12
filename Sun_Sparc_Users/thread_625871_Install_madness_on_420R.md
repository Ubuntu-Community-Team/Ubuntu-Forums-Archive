---
title: "Install madness on 420R"
date: 2007-11-28
forum: Sun Sparc Users
---

### Post by jrothlisberger on 2007-11-28
I have spent the past few days trying to install 7.10 on my 420R with a variety of issues.  Needless to say booting from CD did not work so I set off to load the OS via net boot.  The first time I ran through the install it was all ascii based, menu driven (not screen formatted) connected through the serial console.  I cannot get to the archives via http (proxy server blocking my request) but I can get the archives via ftp.  During the first install attempt I was prompted for either http or ftp.  (I wasn't able to get silo to work properly the first time around so I started over).  On the next and subsequent attempts to install the process has been "screen" driven (nice blue color and red failure screens).  When I get to the point of "Choose a mirror of the Ubuntu archive" I do not get an option to use ftp.  If I go through the http setup it eventually complains that it is a bad archive mirror (never connects).  On a single occasion, and I have no idea why, I was prompted for ftp or http unfortunately I recieved clock setup failures and could do nothing but start over.  So, here I am again trying to get to the archive via ftp and don't get prompted.  So, is there a secret to this?  Am I missing the magic key sequence?  Anyone know who I can force the install to do an ftp request and not an http request?

Thanks,
John

---

### Post by jrothlisberger on 2007-11-30
I didn't think this question was that tough... hmmm...

A little more information -

When the mirror is picked and the installer tries to load from the archive there are no requests going out on the net.  I've been running a snoop from another machine and there is no outbound traffic.  This machine has multiple interfaces - a qfe card which is unused with no connections and hme0 which is setup and does work.  Once I have setup the network information I can ping the box.

Since I can break into a shell is there something I can change to force an ftp request?  Can I do this with a preseed file from the tftpboot server - if so, how?

Thanks,
John

---

### Post by jrothlisberger on 2007-12-04
I was finally able to get ubuntu to work on the 420R!!!

I think the ultimate problem was we have a proxy server setup SCRIPT which apparently doesnt work during the install (no suprise now I guess).  I got a static address for the proxy server and the load worked fine.  Prior to doing the above I also removed the qfe card - I wasnt sure if that was somehow messing up the network settings.  Upon further review I am sure that had 0 effect.

Time to play...

John

---

### Post by jcastill on 2007-12-04
Thanks for your findings. Unfortunately I don't have any 420R so I was unable to help, yet maybe somebody will find this helpful.

Sincerely,

Jose

---

