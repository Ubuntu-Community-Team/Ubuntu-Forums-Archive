---
title: "Snort error"
date: 2017-03-28
forum: Security
---

### Post by sniper8752 on 2017-03-28
I am getting this error:

```
sudo ./pulledpork.pl -c /etc/pulledpork/pulledpork.conf

    https://github.com/shirkdog/pulledpork
      _____ ____
     `----,\    )
      `--==\\  /    PulledPork v0.7.3 - Making signature updates great again!
       `--==\\/
     .-~~~~-.Y|\\_  Copyright (C) 2009-2016 JJ Cummings
  @_/        /  66\_  cummingsj@gmail.com
    |    \   \   _(")
     \   /-| ||'--'  Rules give me wings!
      \_\  \_\\
 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Checking latest MD5 for snortrules-snapshot-2970.tar.gz....
        Error 422 when fetching https://www.snort.org/reg-rules/snortrules-snapshot-2970.tar.gz.md5 at ./pulledpork.pl line 534.
        main::md5file("xxxx", "snortrules-snapshot-2970.tar.gz", "/tmp/", "https://www.snort.org/reg-rules/") called at ./pulledpork.pl line 2007



pulledpork-master$ snort -V


   ,,_     -*> Snort! <*-
  o"  )~   Version 2.9.7.0 GRE (Build 149)
   ''''    By Martin Roesch & The Snort Team: http://www.snort.org/contact#team
           Copyright (C) 2014 Cisco and/or its affiliates. All rights reserved.
           Copyright (C) 1998-2013 Sourcefire, Inc., et al.
           Using libpcap version 1.7.4
           Using PCRE version: 8.38 2015-11-23
           Using ZLIB version: 1.2.8



```

How do I fix this?

---

### Post by Buntu Bunny on 2017-03-31
Perhaps because the version has reached it's end of life (see [https://www.snort.org/]("https://www.snort.org/")) in which case there is no fix except to upgrade.

---

