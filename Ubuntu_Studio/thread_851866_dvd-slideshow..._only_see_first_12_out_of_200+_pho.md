---
title: "dvd-slideshow... only see first 12 out of 200+ photos"
date: 2008-07-07
forum: Ubuntu Studio
---

### Post by kngharv on 2008-07-07
Dear all:

I am new to dvd-slideshow.

I followed the example, and actually did a couple short script with about a dozen photos, no problem.

Once I spend the time did a full-blown dvd-slideshow file, I ran into problem

I am not using anything fancy.  I have a single music track, and 270+ photos without any special effect in between.

Despite the fact that my text file contains 270+ photos, dvd-slideshow can only see first 12 photos.

I am running ubuntu 8.04 with dvd-slideshow 0.75

Here are error messages I obtained:

/usr/bin/dvd-slideshow: line 623: myecho: command not found
wc: : No such file or directory

[dvd-slideshow] /usr/bin/dvd-slideshow: line 2310: [: too many arguments
####/usr/bin/dvd-slideshow: line 1145: 1000 * 0 + 080: value too great for base (error token is "080")
/usr/bin/dvd-slideshow: line 2387: 10812 +  : syntax error: operand expected (error token is " ")


then... after renders first 12 photos, it display

/usr/bin/dvd-slideshow: line 1145: 1000 * 0 + 080: value too great for base (error token is "080")
/usr/bin/dvd-slideshow: line 2652: 29970 *  / 1000 : syntax error: operand expected (error token is "/ 1000 ")
[dvd-slideshow] 13/12 /home/kngharv/Desktop/photo/a2/a2050DSC_9415.JPG [dvd-slideshow] Error in hms function


The strange things is that I *TRIED* to increase the debug level by turn the debug level to "3" in my ~/.dvd-slidshowrc
but apparently dvd-slideshow ignores that rc file.


I have attached my text file.  any idea?


Harv

---

### Post by kngharv on 2008-07-07
Dear all&#65306;

I fixed it.... by upgrading the dvd-slideshow to 0.8

Thanks all

---

