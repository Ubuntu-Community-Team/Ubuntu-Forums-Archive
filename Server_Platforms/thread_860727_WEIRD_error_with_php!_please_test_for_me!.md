---
title: "WEIRD error with php! please test for me!"
date: 2008-07-15
forum: Server Platforms
---

### Post by unebaguettesvp on 2008-07-15
hi- i'm getting this RIDICULOUS error with php that i can reproduce. i'm doing this with this VERY simple script:

```
<?php

echo(0.9 + 0.1 . "\n");
echo(0.09 + 0.01 . "\n");
echo(0.009 + 0.001 . "\n");
echo(0.0009 + 0.0001 . "\n");
echo(0.00009 + 0.00001 . "\n");
echo(0.000009 + 0.000001 . "\n");
echo(0.0000009 + 0.0000001 . "\n");
echo(0.00000009 + 0.00000001 . "\n");
echo(0.000000009 + 0.000000001 . "\n");
echo(0.0000000009 + 0.0000000001 . "\n");
echo(0.00000000009 + 0.00000000001 . "\n");

?>
```

this returns:

```
1
0.0:
0.01
0.001
0.0001
1.0E-5
:.0E-7
:.0E-8
1.0E-8
1.0E-9
1.0E-10

```

notice the colon on only some of the numbers! again, this is reproducible on my end. can you please test the same script? thanks!

some more background, i'm using ubuntu hardy heron, 32 bit with all of the updates. i am NOT using the server version. i only have php5-cli and php5-common installed. i'm not having any other problems with this.

another friend is using 5.2.3-1ubuntu6.3 on gutsy gibbon and he can NOT reproduce this error. so, i'm wondering if anyone else can or if anyone else has seen this before or if you anyone has any suggestions. i would really appreciate it. thank you so much for your time!

---

### Post by davidshq on 2008-07-15
wow. fascinating.

---

### Post by furlabs on 2008-07-19
Are you *sure* they are colons? Did you cut and paste the exact output? Because I'm just wondering if it is a problem with dead pixels on your monitor causing some of the 1s to appear to as :.

---

### Post by hyper_ch on 2008-07-19
output on debian etch

```

1 0.1 0.01 0.001 0.0001 1.0E-5 1.0E-6 1.0E-7 1.0E-8 1.0E-9 1.0E-10 

```

---

### Post by unebaguettesvp on 2008-07-19
> **furlabs said:**
> Are you *sure* they are colons? Did you cut and paste the exact output? Because I'm just wondering if it is a problem with dead pixels on your monitor causing some of the 1s to appear to as :.

yeah, they are definitely colons. i copied that straight from a terminal. i just did it again. i think i'm going to file a bug report. thanks to everyone for testing it out!

---

