---
title: "CVSNT migration locales"
date: 2011-11-28
forum: Server Platforms
---

### Post by prox2far on 2011-11-28
I have migrated a CVSNT server from a windows XP machine to Ubuntu 10.04 LTS and almost everything works.

Some files that are transferred to the clients in a CVS checkout are not recognised as being under version control.

I have tracked cause of the problem to being "locally" encoded file names containing the letters æøå, one example is bærbar_kvitterin.pdf, and I can see the CVSNT information for these files is broken on the server.

The CVSNT information shows a filename with broken text encoding for the different pieces of revision information, for example
filename        HP_b<E6>rbar_kvittering.pdf;

Can I somehow "fix" this under CVSNT, changing locale, converting filenames etc., or is the only solution to take the plunge and convert the repository to SVN?

I have tried looking at the locale for the PServer configuration, but this does not affect how the CVSNT information is read.

---

### Post by prox2far on 2011-12-21
Looks like this problem is related to the client used, as a client change fixed the problems.

---

