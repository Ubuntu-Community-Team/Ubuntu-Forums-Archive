---
title: "chkrootkit Suspicious File?"
date: 2011-04-28
forum: Security
---

### Post by GreenRaccoon on 2011-04-28
Just for reference, I have Natty Narwhal.

I ran chkrootkit, and it listed /usr/lib/pymodules/python2.7/.path as suspicious.  I looked at the file and it says:

/usr/lib/pymodules/python2.7
ubuntuone-control-panel
/usr/lib/pymodules/python2.7/ubuntuone-control-panel
ubuntuone-storage-protocol
/usr/lib/pymodules/python2.7/ubuntuone-storage-protocol
ubuntuone-client
/usr/lib/pymodules/python2.7/ubuntuone-client

Should I be worried about this?

---

### Post by cariboo on 2011-04-28
Check the file versions to see if they are the same as what's listed in Synaptic.

---

### Post by brian_p on 2011-04-28
> **GreenGuitar1 said:**
> 

Should I be worried about this?

No, but I am. Why anyone should expect to obtain any useful information from chkrootkit is beyond my understanding. When you have followed the advice already given to you purge it from your system. You'll not miss it.

---

### Post by Soul-Sing on 2011-04-28
> **brian_p said:**
> No, but I am. Why anyone should expect to obtain any useful information from chkrootkit is beyond my understanding. When you have followed the advice already given to you purge it from your system. You'll not miss it.

lol, it seems "scare" ware, as i read your comment.
in some degree i agree with you. "Howto obtain useful information" from the logs/warings.....

---

