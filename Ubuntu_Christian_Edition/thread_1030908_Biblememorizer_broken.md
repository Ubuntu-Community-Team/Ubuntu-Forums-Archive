---
title: "Biblememorizer broken"
date: 2009-01-04
forum: Ubuntu Christian Edition
---

### Post by cmckdub on 2009-01-04
I have recently updated my gnomesword to version 2.4.1. Now I find Biblememorizer does not work. As I open Biblememorizer, an error message comes up saying "The plugin could not be loaded. You may see further error messages". Other error messages that occur if I try to use it are:
"The plugin either could not be loaded properly, or it does not support querying whether it can load verse text".
"The plugin either could not be loaded properly, or does not allow its translation feature to be queried."
I am using Hardy.
Any suggestions?

---

### Post by cmckdub on 2009-01-06
All is OK now. Thanks to Jeremy, I have downloaded the new Biblememorizer (0.6.3). To install it I needed to:
[LIST=1]
[*]Download the update from sourceforge
[*]Use synaptic to get qt3-dev-tools
[*]Use synaptic to get libsword-dev
[*]Use synaptic to get libqt3-mt-dev
[*]Followed the instructions with Biblememorizer-0.6.3 to run ./configure from the downloaded folder
[*]Ran make
[*]Use sudo to copy the file biblememorizer-0.6.3/plugins/crosswire/libcrosswire.so to /usr/lib/biblememorizer/plugins (overwrite)
[/LIST]
I post this as reference in case someone else faces a similar issue.

Such a procedure is not really a common thing I would do. However, I am glad I upgraded Gnomesword as version 2.4.1 is much better than the version that I had from the Ubuntu repository, and I wanted Biblememorizer working again. It is a shame that both the updated Gnomesword and the updated Biblememorizer is not on the Ubuntu repository. (I do not even know how such could occur).

---

