---
title: "Strange traffic in nginx logs"
date: 2013-08-26
forum: Server Platforms
---

### Post by ConcreteDonkey on 2013-08-26
Hello,

I have a personal web server that is basically unknown to anyone but me and a few friends, as it is used to share files and such. However I've been noticing in the nginx that there are some very weird entries:

```

83.170.101.179 - - [26/Aug/2013:18:28:32 +0100] "FT\xAAb\x13\xC3\xD6\xA9\x1BP\xB0Tw\x87\xF0+G'<\xFD\x9D.T\xF0[\x05\xE5L\x94\xF0*" 400 166 "-" "-"
83.170.101.179 - - [26/Aug/2013:18:28:33 +0100] "-" 400 0 "-" "-"
82.68.74.213 - - [26/Aug/2013:18:28:56 +0100] "3\xF9\xE4_\xC4K:a\x80qj2\xA2\x98\x14\xCC(\xBAPqT%~\x06\x07\xB6t\xEAh\x1A\xBD)\xFC\xA4m\xD8\x9A\x19\xE8\xA5\x05 \x11\x8D_\x11y\x10lE\x9C\xA3\xCC\xF3+\xAC\xE0" 400 166 "-" "-"
82.68.74.213 - - [26/Aug/2013:18:28:56 +0100] "-" 400 0 "-" "-"
46.16.33.98 - - [26/Aug/2013:18:42:03 +0100] "-" 400 0 "-" "-"
182.187.94.99 - - [26/Aug/2013:18:42:04 +0100] "-" 400 0 "-" "-"
188.30.58.16 - - [26/Aug/2013:18:43:21 +0100] "-" 400 0 "-" "-"
188.30.58.16 - - [26/Aug/2013:18:43:21 +0100] "-" 400 0 "-" "-"
213.171.205.131 - - [26/Aug/2013:18:46:40 +0100] "-" 400 0 "-" "-"
213.171.205.131 - - [26/Aug/2013:18:46:42 +0100] "M\xE82\x15\x81A\xC7W\xFD\xE8\x14#\x04\x80\xAA\x00G\xA6\x93n\x98\xAE^\x00\xC0\xC8\xF6\x09!\x0F\xEC\xD17\xA7\x92#\x1D_" 400 166 "-" "-"
213.171.205.131 - - [26/Aug/2013:18:49:40 +0100] "-" 400 0 "-" "-"
213.171.205.131 - - [26/Aug/2013:18:49:41 +0100] "\xF9\xD3v\x0CI\x14\xD5\xB1\x15\xD8\xEFjm4\x1E\x1A\xD6i|_P\x0E\xE8\xC57\x03S\xBESg\x1B\x0Fv\xD4\xD5\x9E\xB6\x1E\xEE\xF8a1\xA5h.\x1B\xB3\x02\x80\x8DZWM\x05\x18z" 400 166 "-" "-"
5.185.247.23 - - [26/Aug/2013:18:56:41 +0100] "\xD3\x81\x95\x9C\xE7\x06q\xC4@d\xB6\xA8b\xB6TX\xA2\xAC\xF9\xF39\x5C\xB7\xBB\x04\x97\xAA\x1Au%f\xB7\x8Cq\xD8@f\xCF\x1C-l\x1A" 400 166 "-" "-"
5.185.247.23 - - [26/Aug/2013:18:56:43 +0100] "-" 400 0 "-" "-"
197.6.21.13 - - [26/Aug/2013:19:00:34 +0100] "-" 400 0 "-" "-"
197.6.21.13 - - [26/Aug/2013:19:00:34 +0100] "<L\x96\x9F:?B/\x9C\xCA$\xF5\xE5\x82\x81\xF8\x104\x8C\x8AZ\xA2\xF9\x5C\x1E\xB8" 400 166 "-" "-"
46.16.33.76 - - [26/Aug/2013:19:04:12 +0100] "-" 400 0 "-" "-"
46.16.33.76 - - [26/Aug/2013:19:04:19 +0100] "-" 400 0 "-" "-"
176.45.224.155 - - [26/Aug/2013:19:06:37 +0100] "-" 400 0 "-" "-"
189.13.200.94 - - [26/Aug/2013:19:07:16 +0100] "-" 400 0 "-" "-"
189.13.200.94 - - [26/Aug/2013:19:07:17 +0100] "\xB7t\x95\x1C\xAF\x8AM\xCB\xB7\xD2\x97\xCA\xEC\xFA\xF3T\x1E#\x8E\xC5\x98\xBE\xB9w\x97\x8B\xA5\x5C\x99\xF8s]V\x0C\xC8A{\xDF\xC5\x91\xC3\x86\xD6\xE0]\x8C\xC6\xE4\xB8\x09\x81\x19\xF7\x11H\x8B\xDA\xBC\x16" 400 166 "-" "-"
46.16.33.76 - - [26/Aug/2013:19:21:14 +0100] "-" 400 0 "-" "-"
82.68.74.213 - - [26/Aug/2013:19:46:21 +0100] "\x04,\xC9\xFF" 400 166 "-" "-"
82.68.74.213 - - [26/Aug/2013:19:46:21 +0100] "-" 400 0 "-" "-"
84.131.60.235 - - [26/Aug/2013:19:53:03 +0100] "\xE36\xEE?\xC2\x1FF\x19\xF1\xF7\x05n\xD7/\x98\xF84\xA2\xC1\x17\x9B\x99\xEB]\xC5\x98\xD2\x86\xB5?h\xDC6wX\xFF\xEF\xC3\xE1\xEF)\x97J5\xD5\x86\xEC\xED\xC1\xAFI\xA9\x98\xFA\xF8*'m\x9C\xDCO/" 400 166 "-" "-"
83.149.38.217 - - [26/Aug/2013:19:53:06 +0100] "-" 400 0 "-" "-"
41.182.81.35 - - [26/Aug/2013:20:01:22 +0100] "-" 400 0 "-" "-"
41.182.81.35 - - [26/Aug/2013:20:01:23 +0100] "-" 400 0 "-" "-"
82.68.74.213 - - [26/Aug/2013:20:03:44 +0100] "\xCA~\x06j\xB3\xCBA\x8C%\x18\xB7E\x85|{\x9Bx\x9A*m\xE2\xC7\x0E\xBFn/\xC2\xBD\x8A\xD2\x01\xAB\x198j\x1C\x95\xF5\xE3\xCD\x8E\x08]\xA0\xFB\xEASN2 *\x92\xB8" 400 166 "-" "-"
82.68.74.213 - - [26/Aug/2013:20:03:44 +0100] "-" 400 0 "-" "-"
83.149.38.217 - - [26/Aug/2013:20:05:26 +0100] "-" 400 0 "-" "-"
82.0.45.155 - - [26/Aug/2013:20:11:59 +0100] "-" 400 0 "-" "-"
82.0.45.155 - - [26/Aug/2013:20:11:59 +0100] "\xEFG\xB7}\xC4\x05@,@On$\x83\xDCy\x8CH\xF5v\xE1\xFA\xD1!\xF8l1,4f\x1C\xB8h\xBC}\x07S\x09\x94\xCB\xB7\x1F\xEAD" 400 166 "-" "-"
41.182.81.35 - - [26/Aug/2013:20:16:10 +0100] "-" 400 0 "-" "-"
41.182.81.35 - - [26/Aug/2013:20:16:11 +0100] "-" 400 0 "-" "-"
82.68.74.213 - - [26/Aug/2013:20:16:49 +0100] "\x8C2m" 400 166 "-" "-"
82.68.74.213 - - [26/Aug/2013:20:16:49 +0100] "-" 400 0 "-" "-"
80.229.166.77 - - [26/Aug/2013:20:17:29 +0100] "=\xAE\xB0)\x13\x13\x9D\x12\xE6N\xD8\x047\x9DNV\xB9WT\xB4\xA8%\xE9\xA5\xBE\xF1n\xE4\xE8\xA0\xAB\x1F,\xB0\x81\x0C\xD8\xA0=" 400 166 "-" "-"
213.48.25.189 - - [26/Aug/2013:20:18:45 +0100] "-" 400 0 "-" "-"
213.48.25.189 - - [26/Aug/2013:20:18:45 +0100] "5\xBD\xF1\xA9\x98\x966\xDCh4\xED\xF1}X\xE8S\x92\x19ZN\x1DP#\xE0\xB8}N\x80\x82\xAA\x9A,\xF8\xB3\xE0\xC5\xE4\xAA_\xEE\xDF\xFF\xCA\x7F=\x8D\xDF\x22\xFEJi\x10\x03\x00\xCB\x01\x9C\xF1V<\xA2\x06\x15A\xA5^>~\x93\x8A\x97$\x89" 400 166 "-" "-"

```

On this specific day there was no legitimate traffic and although there is hardly anything contained on my website as it's completely unknown and it seems that this is happening multiple times a day, everyday.

I assume it's some form of attack (I assume it's shell code), should I be worried about it? Also is there anything I can do to prevent it from happening in the first place?

---

### Post by CharlesA on 2013-08-26
Doesn't matter if your site is "unknown" or not. There will still be bots that will try to exploit it.

As far as I can tell the lines with "-" 400 0 "-" "-" are empty HTTP requests and I'm not sure what the others are.

---

