---
title: "ulsdtool"
date: 2010-10-04
forum: Ubuntu One (CLOSED)
---

### Post by dnhmd on 2010-10-04
I am trying to use the ulsdtool to stop a large folder from syncing, since it is taking a very long time.  I get the following error:
don@dnhmdcorp:~$ ulsdtool --current-transfers
No command 'ulsdtool' found, did you mean:
 Command 'u1sdtool' from package 'ubuntuone-client' (main)
ulsdtool: command not found
I have installed all ubuntuone tools from Synaptic.

---

### Post by Bill_ on 2010-10-04
You've made one small mistake there with the command you're trying to run, and if you look closely at the error that you got, it actually tells you that (although it might not be entirely obvious).

You are trying to run ulsdtool, but if you look closely at the error you got, it's actually u1sdtool. It's a very small difference - it's not the letter l in the command it's the number 1.

---

### Post by dnhmd on 2010-10-05
Thank you so much for pointing it out.  It was driving me crazy.:)

---

### Post by duanedesign on 2010-10-06
[Here is a good wiki page]("https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl#Accidentally%20added%20an%20UDF,%20how%20to%20remove%20it%20fast") that talks about how to remove a folder accidentally added to Ubuntu One. There is also some other good stuff on that page about u1sdtool.

~duanedesign

---

