---
title: "Building WineX (Cedega) from source?"
date: 2008-08-22
forum: The Cafe
---

### Post by Dremora on 2008-08-22
Cedega keeps their WineX code in a Gzipped file here:

[http://www.cedega.com/downloads/source.mhtml](http://www.cedega.com/downloads/source.mhtml)

Unfortunately, I'm not certain it would be any use to me, as the documentation says:

"This repository includes everything required to build the LGPL components of 
TransGaming's Cedega and Cider products, including full source code for both

the LGPL portions as well as additional libraries required to allow those 

components to be built.  The repository does not contain the remaining source
 code for either product, and also does not include a loader component to 
allow EXE files to be launched.
"

Without an EXE loader it's useless, and automake fails with this message anyway:

/usr/bin/m4:configure.ac:5: cannot open `VERSION': No such file or directory

autom4te: /usr/bin/m4 failed with exit status: 1

------------------

Anyhow, there used to be all kinds of documentation on building from their now defunct CVS, but can anyone give me some pointers on what to do with this thing?

---

### Post by Canis familiaris on 2008-08-22
Well actually the CVSCedega is outdated and not maintained. I would recommend you to stick with WINE.

---

### Post by Dremora on 2008-08-22
> **Anurag_panda said:**
> Well actually the CVSCedega is outdated and not maintained. I would recommend you to stick with WINE.

This gzip file says June 2008.

---

