---
title: "Courier imapd file broken?"
date: 2009-03-08
forum: Server Platforms
---

### Post by stuart475898 on 2009-03-08
Firstly, I would like to apologize if this is the incorrect forum for this question, but it seems like the most appropriate and I feel so helpless because of this problem, and I think I am ready to commit suicide. My life is in your hands...

I have a VPS running with Courier mail used for IMAP. Now, everything was running fine the other day until I added more than 4 email accounts in Thunderbird, at which point it popped up with an error saying cannot connect, probably due to too many connections. So, a bit of googling confirms that this is probably due to a connection setting in imapd on the server. A number of sites all confirm the same thing, and so off I go and modify the MAXDAEMONS and MAXPERIP settings to 80 and 40 respectively. 

At this point, the plot thickens.

I try connecting again, however this time I am told that the connection is refused. Ok I think, Ill restart the daemon. No success. Instead, I get a LOAD of error messages about invalid lines. Hmm, strange I think to myself. At this point, I draw upon my experience of working in IT and on satellite, radio and telephone systems within the military...

I turn the server off and back on again.

Unfortunately, this did not alleviate the problem. At this point, it was time to investigate those errors. There were a huge number of them and I noticed that they were all appearing on the blank lines of the imapd file. I backup up the file, and then deleted all of the blank lines. Success! I now only have two errors. Both of these errors are within imapd.rc and imapd-ssl.rc, and are both on line 47. The error reads

invalid numberd /usr/lib/courier-imap/imapd.rc: line 47: ulimit: 65536

Once again, investigation takes me back to our petulant friend imapd. I decided to change the value of IMAP_ULIMITD to 32768. Unfortunately, the error persists.

And so, there you have it. I have looked on google for what this error might mean but I have had no luck. Could it be that when I edited the file using the Parallels Power Panel web interface, it changed the encoding of the file to something incompatible with Courier? This could certainly explain the problem.

---

### Post by hyper_ch on 2009-03-08
I have no clue what causes those errors. However you could remove courier-imap with the purge command and reinstall it. Then you should get the default configs again.

---

