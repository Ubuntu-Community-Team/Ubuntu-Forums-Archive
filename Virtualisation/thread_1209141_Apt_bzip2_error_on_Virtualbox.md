---
title: "Apt bzip2 error on Virtualbox"
date: 2009-07-09
forum: Virtualisation
---

### Post by NeoFax on 2009-07-09
Everytime I re-enable the virtualbox pool, I get some error.  Now, it is a bzip2 error on the Package.bz2 file from deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free.  I also get a gpg error.  Here is the exact errors:

Get:4 [http://download.virtualbox.org](http://download.virtualbox.org) jaunty/non-free Packages [1247B]           
Packages                             
99% [4 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fo
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://download.virtualbox.org](http://download.virtualbox.org) jaunty/non-free Packages                     
  Sub-process bzip2 returned an error code (2)



W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>

---

### Post by livigagl on 2009-07-18
Exactly the same problem using Debian Lenny/Squeeze.

Does someone know how to fix that?

My VBox repo in sources.list is the following.

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny non-free

Googling I found a workaround changing it in:

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) gutsy non-free

Anyway I don't think that could be a good idea to use the repo for an older (and for me even different) version.

---

