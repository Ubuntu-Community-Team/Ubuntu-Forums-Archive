---
title: "GnuCash 2.0 install successful: need docs"
date: 2006-08-09
forum: The Cafe
---

### Post by richbl on 2006-08-09
Hello all,

I'm running Dapper, and just installed GnuCash 2.0. So far, it appears to be working just fine. Much nicer UI than prior releases of GC.

However, I cannot seem to find the related gnucash-docs package for this 2.0 release. No Debian package seems to be available, nor can I find anything in the Dapper or Eft repos.

Has anyone succesfully installed the gnucash-docs 2.0 package, or compiled it under Ubuntu?

thanks,

rich

---

### Post by foxjwill on 2006-08-09
I found it on the debian packages site [here]("http://packages.debian.org/cgi-bin/search_packages.pl?keywords=gnucash&searchon=names&subword=1&version=stable&release=all").

---

### Post by richbl on 2006-08-09
> **foxjwill said:**
> I found it on the debian packages site [here]("http://packages.debian.org/cgi-bin/search_packages.pl?keywords=gnucash&searchon=names&subword=1&version=stable&release=all").

Thanks, but I am looking specifically for the GnuCash 2.0 docs, and not the older 1.8 docs.

rich

---

### Post by richbl on 2006-08-10
Well, after some creative thinking I managed to successfully install gnucash-docs-2.0.0 into Dapper.

The procedure that I followed was:

0) Download and extract gnucash-docs-2.0.0.tar.gz from gnucash.org (currently at [http://prdownloads.sourceforge.net/gnucash/gnucash-docs-2.0.0.tar.gz?download](http://prdownloads.sourceforge.net/gnucash/gnucash-docs-2.0.0.tar.gz?download))
1) CD into the directory created from the extraction, and open the INSTALL file
2) Read and follow the procedures therein, specifically, pay attention to the aptly-named "Basic Installation" (duh!)

And most importantly (and the real "a-ha!" moment)...

3) Move the installed folder created in the "Basic Installation" procedure

from:
```
/usr/local/share/gnome/help/gnucash
```

to:
```
/usr/share/gnome/help/gnucash
```

Optionally, and for EXTRA CREDIT, you could skip STEP 3 if you read the additional procedures in STEP 2 very carefully, as there appear to be some switches that can be used to redirect the build of gnucash-docs to a folder of your own location.

Of course, a real deb package would be a lot less time-consuming, but... half the fun of Linux is figuring out how stuff works.

rich

---

### Post by TravisNewman on 2006-08-10
I saw a deb for it somewhere on the forums. I'm sure that by breezy they'll be included in the repos

---

