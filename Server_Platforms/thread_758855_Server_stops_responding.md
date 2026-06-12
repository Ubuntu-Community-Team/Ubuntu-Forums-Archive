---
title: "Server stops responding"
date: 2008-04-18
forum: Server Platforms
---

### Post by ElJefeRocks on 2008-04-18
Hello,

I just set up a new home LAMP server using 6.06LTS.  On this server I have a Jinzora music server running, Torrentflux torrents and webmin to control everything.  It is basically a way to have my music and movies with me wherever I am with an internet connection.  My only problem is that after a while (don't know exactly how long) the server stops responding to requests.  I can't access the page its on (using local ip address and the webaddress for it) nor can I SSH into the box from another computer on the network (No route to host).  This makes me believe that the computer stopped accepting requests completely.  I have the hard drives set to spin down after an hour of non-use using hdparm, but I believe it stopped responding without that as well.

If anybody has any ideas, it would be great!

Thanks!

---

### Post by Sam Lars on 2008-04-18
Can you access the server directly rather than over the network?  You could check to see if it's blocking ports or actually frozen.

---

### Post by ElJefeRocks on 2008-04-19
Hmm.  I don't know since the server doesn't actually have a monitor, but next time it does it I will plug one in and see where that goes.  Although, is there anything else it could be that somebody can think of?

---

### Post by ElJefeRocks on 2008-04-27
I figured out the problem.  My computer was having a kernel panic with my marvell ethernet on my motherboard.  I have since reinstalled to 6.06.2 due to some other problems with my audio I couldn't resolve.  I didn't keep any info on this kernel panic, but I do remember it was from the sky2 driver if it helps anybody in the future for searches.

---

