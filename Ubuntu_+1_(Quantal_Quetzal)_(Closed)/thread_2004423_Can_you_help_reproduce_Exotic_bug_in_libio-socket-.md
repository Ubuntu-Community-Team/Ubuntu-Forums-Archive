---
title: "Can you help reproduce? Exotic bug in libio-socket-ssl-perl"
date: 2012-06-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-06-15
Have a look at this bug report. I believe there is a bug in the libio-socket-ssl-perl package that causes www::mechanize to fail for me. If I run libio-socket-ssl-perl version 1.53 (from precise) the script attached to that bug report works. If I upgrade to the quantal version (1.74), it times out and doesn't connect.

[https://bugs.launchpad.net/ubuntu/+source/libio-socket-ssl-perl/+bug/1013883](https://bugs.launchpad.net/ubuntu/+source/libio-socket-ssl-perl/+bug/1013883)

Can anyone install the packages needed and confirm my issues? 

sudo apt-get install libio-socket-ssl-perl libwww-mechanize-perl

Then run the script attached to the report. It should fail. Next downgrade libio-socket-ssl-perl to the precise version ([http://mirrors.us.kernel.org/ubuntu//pool/main/libi/libio-socket-ssl-perl/libio-socket-ssl-perl_1.53-1_all.deb](http://mirrors.us.kernel.org/ubuntu//pool/main/libi/libio-socket-ssl-perl/libio-socket-ssl-perl_1.53-1_all.deb)) and try again. It should work and print the contents of the site.

If you succeed or fail, marking the report would be helpful. I must say this is a crazy weird bug I stumbled across. I'm frankly surprised I was able to narrow it down.

---

### Post by balloons on 2012-06-15
Sweet, someone else confirmed it.. well, lol, not sweet I guess because I have to deal with the bug, but nice to know I'm not crazy!

---

