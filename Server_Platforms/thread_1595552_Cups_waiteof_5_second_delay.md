---
title: "Cups waiteof 5 second delay"
date: 2010-10-13
forum: Server Platforms
---

### Post by digitolx on 2010-10-13
I'm using Ubuntu Server 10.04.01 with cups 1.4.3 and am trying to use the waiteof=false command on the jet direct socket .. DeviceURI socket://100.100.115.72:9100?waiteof=false ... This causes the job to error out with "/usr/lib/cups/backend/socket failed".. 

My problem is that the print job is waiting 5 seconds between jobs I would like that behaviour print immediately 

This is causing an issue when printing multiple items.. Some users print 50 - 180 tickets at a time.. taking 100 for example as a mid number... With the 5 second delay between jobs thats 8-10 minutes.. Not acceptiple...

the waiteof option is supposed to fix this but when this is added the printer will not work... 

this is supposed to be fixed in cups v1.4.4 but it is not in the packages.. this is production server so I cannot take the chance or recompiling from scratch.. 

Any ideas on how to solve this?

---

### Post by schweini on 2010-11-03
Did you find a solution for this? I am getting 6 second delays when printing raw text from Ubuntu 10.10 to a Suse 10 CUPS server (which always used to work in split seconds with all other (older) distros i tried).

UPDATE: i forgot to mention that I am using the standard IPP protocol, and no 'nowait' option and all that. Just the most basic CUPS configuration. But because of the '5 second' bit, i hope that we are/were having the same problem.

---

### Post by digitolx on 2010-11-05
Hey friend, I did indeed fix my problem, I found out that the whole waitof was big joke and never worked to begin with even though it was in the documentation for cups..  I actually do not believe that you should be experiencing the issue since you are on version 10.10, I believe that that has cups version 1.4.4. 

Since you are experiencing this with a mix, I would verify that they are both running 1.4.4.. 

It was supposed to be fixed in cups version 1.4.4 and indeed as soon as I upgraded my issue went away. Any version from 1.4.3 - 1.3 has the 5 second delay that cannot be fixed as far as I could find..

---

