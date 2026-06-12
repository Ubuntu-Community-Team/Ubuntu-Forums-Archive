---
title: "Cups-lpd, Cups, Samba, Printing"
date: 2010-04-13
forum: Server Platforms
---

### Post by janniel on 2010-04-13
Hi all, 

Just a little help please... for a newbie to Linux. 

At work we have 2 ubuntu print servers. The setup for printing is as follows: 

Applications run on a Solaris 10 server and passes print jobs via lpd/lpr to the Linux server. Cups-lpd receives the job and then passes it on to Cups and then finally to the Windows PC via Samba.

The following problem occurs sporadically. Print jobs get duplicated even though only one copy was requested. 

Then we also had pieces of spool data from 2 different jobs combine as one print job on the printer. This 2 me seems rather impossible.

Cups uses a raw printer driver for the shared printers on the windows machines as the data has already been formatted on the Solaris 10 box.

Does anyone here have a similar setup? Any of the problems sound familiar?
  Thanx

---

