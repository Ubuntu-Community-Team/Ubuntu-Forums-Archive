---
title: "VERY slow DNS address resolution"
date: 2011-05-08
forum: System76 Support
---

### Post by puddlejumper on 2011-05-08
I am having a problem with what appears to be VERY slow DNS address resolutions.  I have foung possible solutions that involve disabling IPV6 by editing ths alias files in /etc/modprobe.d.  Unfortunately my system(a Bonobo notebook) does not have any alias files in /etc/modprobe.d.  Does anyone have information on where the data that normally goes in these files would be on my system.  I have done a whole bunch of searches and can't find it.

Thanks.

---

### Post by jdb on 2011-05-08
> **puddlejumper said:**
> I am having a problem with what appears to be VERY slow DNS address resolutions.  I have foung possible solutions that involve disabling IPV6 by editing ths alias files in /etc/modprobe.d.  Unfortunately my system(a Bonobo notebook) does not have any alias files in /etc/modprobe.d.  Does anyone have information on where the data that normally goes in these files would be on my system.  I have done a whole bunch of searches and can't find it.

Thanks.
I had a similar problem once.

I had an extra entry in /etc/resolv.conf that was bogus.
It spent time looking for the bogus DNS (Domain Name Server) before it used the real one.

I don't know how it got there but when I removed it the sky turned blue.

jdb

---

### Post by puddlejumper on 2011-05-09
I finally just turned IPV6 off in Firefox.  All is now OK.

---

