---
title: "Nginx Security"
date: 2013-06-19
forum: Server Platforms
---

### Post by PierreRobiquet on 2013-06-19
Hello,

 I have an Ubuntu 12.04 server running Nginx serving pages just for me and a few friends, one thing I've noticed is that in the access logs it's filled with attempts to find folders like phpmyadmin (which doesn't exist) and also strange requests which I assume to be shell code. Here's a small example:

```

89.204.137.108 - - [19/Jun/2013:23:27:20 +0100] "\xC5(J5\xE3\x5Cr\xB3\x9C\x09Y\xE0\xBB\x92\xBD\xBDR\xA2\x92\xAFuMA>\xB2TQPm\xA4n!\xDE2I\xF4\xFB" 400 166 "-" "-"
94.197.127.32 - - [19/Jun/2013:23:28:39 +0100] "-" 400 0 "-" "-"
94.197.127.32 - - [19/Jun/2013:23:28:39 +0100] "~\xF0S\x19[q\x89F;\xD1\xEC\x85\xBF\xEE" 400 166 "-" "-"
41.254.5.3 - - [19/Jun/2013:23:35:10 +0100] "-" 400 0 "-" "-"
41.254.5.3 - - [19/Jun/2013:23:35:10 +0100] "-" 400 0 "-" "-"
41.254.5.3 - - [19/Jun/2013:23:35:59 +0100] "-" 400 0 "-" "-"
41.254.5.3 - - [19/Jun/2013:23:39:08 +0100] "-" 400 0 "-" "-"
41.254.5.3 - - [19/Jun/2013:23:39:11 +0100] "\xF8\xC3T\xEF\xFDqQ@G\xB6D\x89\x08V\xBA\xA6\xB3+g\xA6J.$\xF41\xCD\x80\xFA\x9D\xF7E\xFF\xF7\x92n^\xDB\x03]\x1Fx\x22<I\xFC~\x1A\x19" 400 166 "-" "-"
94.109.101.72 - - [19/Jun/2013:23:46:52 +0100] "-" 400 0 "-" "-"
94.109.101.72 - - [19/Jun/2013:23:46:52 +0100] "\x03\xAA\xC8M\xFEX\xE0\x9F\xC0\xB4 /\xCFq\x1CA\xF86\x06J\x84\xEA\xFD\x09\xE7%U:\xDB\x06\xE4L\xA7\x81\xF2\xAE\x09\xEB\x94n\x9A\xA5?:U\xA5\xF4\xF3\x1A\xE8\x01\xF9\x85\x80\x85\xDFy\x9A9\x8Bh\xEB_=\xCA\x02" 400 166 "-" "-"
197.32.73.36 - - [19/Jun/2013:23:49:09 +0100] "<\xFC<\xAC\xDB\xA9\x09\x16\xB3w \xA0\x06\x01,\x87*n:P\xFF\xA4\xA3\x9C\xE0\x10\xF6\x9B\xD8\xDF\xB7+'0\xB7\x8FE\xE1\xD6!\x80=\x00!\xEBk\xDA\xA2\xFAd\x1A\xA5\xBD\xEB\x17\xAE \x5C\x03[\xF2\xF4\x7Fz\xADi\x80\xE1\x13\xCD\xE2\xD4" 400 166 "-" "-"
197.32.73.36 - - [19/Jun/2013:23:49:09 +0100] "-" 400 0 "-" "-"
187.134.191.47 - - [19/Jun/2013:23:53:33 +0100] "I$\xEA.\xE1\xDA\xFE\xA1\x09\xFD\x1D\x07\xC0\xB7\xA3\x9E\xB3\xBBJ\xE4\xB4\xC1?\x1C\x1C\xC55S\xBD\xB1u8p\x00\x9B\xD0\xAB\xC6\x19\x83J8\xB3\x83\x8B\xABh\xD2\xBC\x8B" 400 166 "-" "-"
105.153.186.119 - - [19/Jun/2013:23:54:31 +0100] "-" 400 0 "-" "-"
105.153.186.119 - - [19/Jun/2013:23:54:32 +0100] "\xCB\xD1\xDB\x0B\xC6*[\xEA\xACw\xF0gfH\xE2iu\xAD\xE0;\xEA$~\xEE\xA8\x06\x83\xCFc21" 400 166 "-" "-"
86.133.107.220 - - [19/Jun/2013:23:56:33 +0100] "-" 400 0 "-" "-"
86.133.107.220 - - [19/Jun/2013:23:56:33 +0100] "\xC2m \xCB\xD8\xD1p\x85\xBF\xE7\x86\xE8_cy\xD2\x9E\x82\xB3\xEB\x5C\xEB\x87\x055\x9DqS\x1C\xFF\xFFY\xB1" 400 166 "-" "-"
```

 I know that it is expected to have this kind of malicious traffic, but the server is completely unknown. The only people that use it are me and a few other people and there are actually at least 10x more malicious requests than genuine ones with it sometimes having a constant stream for hours.

 Is there anything I can do to limit the amount of malicious requests? I can't use iptables to drop the IP addresses as it's from different IP addresses.

Any help will be appreciated, thanks.

---

### Post by sandyd on 2013-06-20
Just ignore them, it is just hex code that won't affect the server in any way. (It probably would if it was run in the shell though)

---

