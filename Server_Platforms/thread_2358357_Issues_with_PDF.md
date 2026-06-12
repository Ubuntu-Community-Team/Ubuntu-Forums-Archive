---
title: "Issues with PDF"
date: 2017-04-12
forum: Server Platforms
---

### Post by squeak24 on 2017-04-12
Hey Everyone

I am having issues with Ubuntu Server and exporting to PDF.

I have a MediaWiki on a localhost running Ubuntu Server. But when I try and export the Wiki Pages to PDF using PDF Books, it keeps failing.

I have tried to install GEVENT, Coro amongst others but it still fails.

I have Python and Cython installed.

Any help would be appreciated.

Harry

---

### Post by sed_faster on 2017-04-12
I don't know if this problem will be important to your question but recently I did test to convert pdf pages to images through this script:

```

##
echo "****************************************************">>log.c
echo "****************************************************">>log.c
sensors>>log.c
echo "****************************************************">>log.c
echo "****************************************************">>log.c
echo "convert -density 300 file.pdf -quality 100 first_test/file_final.jpg">>log.c
date>>log.c
convert -density 300 file.pdf -quality 100 first_test/file_final.jpg
date>>log.c
##
echo "****************************************************">>log.c
echo "****************************************************">>log.c
sensors>>log.c
echo "****************************************************">>log.c
echo "****************************************************">>log.c
echo "convert -density 150 file.pdf -quality 100 second_test/file_final.jpg">>log.c
date>>log.c
convert -density 150 file.pdf -quality 100 second_test/file_final.jpg
date>>log.c
##
echo "****************************************************">>log.c
echo "****************************************************">>log.c
sensors>>log.c
echo "****************************************************">>log.c
echo "****************************************************">>log.c
echo "convert -density 300 file.pdf -quality 50 third_test/file_final.jpg">>log.c
date>>log.c
convert -density 300 file.pdf -quality 50 third_test/file_final.jpg
date>>log.c
##

```

The result it was:
```

****************************************************
****************************************************
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +10.0 C  (crit = +100.0 C)

****************************************************
****************************************************
convert -density 300 file.pdf -quality 100 first_test/file_final.jpg
Tue Apr  4 11:10:22 WEST 2017
Tue Apr  4 12:42:57 WEST 2017
****************************************************
****************************************************
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +15.0 C  (crit = +100.0 C)

****************************************************
****************************************************
convert -density 150 file.pdf -quality 100 second_test/file_final.jpg
Tue Apr  4 12:42:58 WEST 2017
Tue Apr  4 13:09:00 WEST 2017
****************************************************
****************************************************
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +13.0 C  (crit = +100.0 C)

****************************************************
****************************************************
convert -density 300 file.pdf -quality 50 third_test/file_final.jpg
Tue Apr  4 13:09:00 WEST 2017
Tue Apr  4 14:47:53 WEST 2017

```

Maybe this experience will give you an any idea how resolve your problem!

---

### Post by squeak24 on 2017-04-28
Sorry for the delay, I have been away. I have done what was suggested but just got a load of errors. Still not sure what the issue is.

---

### Post by oldos2er on 2017-04-28
Please post the errors.

---

