---
title: "samba share, and CHAR encoding problem"
date: 2009-01-29
forum: Server Platforms
---

### Post by renebs on 2009-01-29
Hi,

I have my music on a ubuntu 8.10 server, shared using samba. Some of my music files have names like: João do Vale.mp3. Note the tilda over the letter a. 

This file can be seen in my wife's mac over the samba share. But once you click on it the file disappear. Moreover the file can't be added to iTunes database. Does anyone have any suggestion in solving this, I am (even) clueless in how to go about searching for a solution. Hence, I do apologize in advance if there is a thread with solution already posted. I just don't know how to search for it. If my problem isn't clear, please reply with what information is needed from me to make it so. 

Thanks for reading.

---

### Post by renebs on 2009-01-29
Please ignore this issue/thread (unless you can point me to other forum). I did a test (copied the folder with ã char music files to Desktop and even there the MAC can't see the files. So problem is not with samba configuration but with MAC OS X (10.5.6 in this case).

---

### Post by HermanAB on 2009-01-29
Hmm, you should only use POSIX portable characters in file names if you want to do cross platform things.  So I think that your only solution is to rename the files.

Cheers,

Herman

---

### Post by renebs on 2009-01-29
Thanks for the repply. 

The weird thing is that I DO HAVE other files on the iTunes database that have "accents" on letters as characters. 

I wonder if:
1) a file have a different CHARACTER SET regardless of the system it's in?? 2) the fact that I have encoded those mp3 using windows, whereas usually I encode in Ubuntu (UTf-8 by default, right?) makes a difference in this case.

---

