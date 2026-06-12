---
title: "A server hardware question"
date: 2008-02-21
forum: Server Platforms
---

### Post by igknighted on 2008-02-21
I am building a server to replace a Netware4 server (yeah.. ipx... ew).  But I have a hardware question.  The ram that my boss purchased for the system is ECC error correcting and runs fine (I am using it now on a desktop machine to be sure), but when I try to boot the server (2x2.4ghz intel xeon) it wont even post.  I get a series of beeps.  We RMA'd the board and got a new one, same problem.  I suspect it is the memory, would running ECC (non-registered) memory in a system designed for registered memory cause a failure to post?  Or have I gotten two bad mobo's in a row?

---

### Post by InlawBiker on 2008-02-21
> **igknighted said:**
> I am building a server to replace a Netware4 server (yeah.. ipx... ew).  But I have a hardware question.  The ram that my boss purchased for the system is ECC error correcting and runs fine (I am using it now on a desktop machine to be sure), but when I try to boot the server (2x2.4ghz intel xeon) it wont even post.  I get a series of beeps.  We RMA'd the board and got a new one, same problem.  I suspect it is the memory, would running ECC (non-registered) memory in a system designed for registered memory cause a failure to post?  Or have I gotten two bad mobo's in a row?

Yes you probably have incorrect memory.  Most servers will require registered memory.  What is the beep pattern?   It's trying to tell you what's wrong.  Look up that beep pattern in the manual and it'll tell you what the problem is.

---

### Post by igknighted on 2008-02-21
> **InlawBiker said:**
> Yes you probably have incorrect memory.  Most servers will require registered memory.  What is the beep pattern?   It's trying to tell you what's wrong.  Look up that beep pattern in the manual and it'll tell you what the problem is.

It's 7 beeps (AMI BIOS).  We RMA'd the board the first time because that beep code seemed to indicate an error with the cpu or mobo (at least from what I could decifer from the cryptic results google turned up).  Thanks, we have registered memory on order now, hopefully that does the trick.  Worst comes to worst it'll go into our other server :)

---

### Post by astrotech226 on 2008-02-21
I know for a fact that won't work.  I've done that a few times...  Got in boxes to build multiple servers and every single ram stick was not registered.  No post and lots of beeps.  Sent them back, got registered ECC and everything was smooth sailing.

---

