---
title: "Time oddities"
date: 2006-09-25
forum: Server Platforms
---

### Post by mikl on 2006-09-25
I have a problem with my new Ubuntu server. It insists on beeing two hours ahead of time. I've tried changing the UTC value in ```
/etc/default/rcS
```, but to no avail. How do I fix it?

running ntptime gives me this:
```
ntp_gettime() returns code 0 (OK)
  time c8c256ff.40f43000  Mon, Sep 25 2006 15:24:15.253, (.253726),
  maximum error 1089552 us, estimated error 16 us
ntp_adjtime() returns code 0 (OK)
  modes 0x0 (),
  offset 0.000 us, frequency 0.000 ppm, interval 4 s,
  maximum error 1089552 us, estimated error 16 us,
  status 0x1 (PLL),
  time constant 0, precision 1.000 us, tolerance 512 ppm,
  pps frequency 0.000 ppm, stability 512.000 ppm, jitter 200.000 us,
  intervals 0, jitter exceeded 0, stability exceeded 0, errors 0.

```

---

### Post by Iowan on 2006-09-25
Is it adjusting for your timezone?
IIRC, there's a timezone setting (file) to adjust the offset.

On my server, the **/etc/timezone** file contains Etc/GMT.

---

