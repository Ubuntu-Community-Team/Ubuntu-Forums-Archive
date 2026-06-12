---
title: "Wireless router/card debugging ideas"
date: 2010-02-18
forum: The Cafe
---

### Post by hwttdz on 2010-02-18
Edit: I suppose there is no mark as solved in this forum, but this thread is solved.  Was posted here (as opposed to the hardware forum) as I thought it was a hardware problem unrelated to ubuntu.  Original post follows.

So my wireless connection seems to have flaked out.  I get a strong signal and a connection, but I cannot get any internet data.  I also cannot ssh to my local area network ip (i.e. 192.168.1.X).  This is somewhat confusing to me as the router is clearly broadcasting a signal and card is clearly picking up the routers signal, but something somewhere along the line is going wrong.  I'm currently leaning towards replacing the router. And I figure that this might be a good time to start moving towards an n network.  Anyways let me know if you have any thoughts on debugging, figuring out if this is a router problem or card problem or new hardware suggestions.

---

### Post by blueturtl on 2010-02-18
I just recently replaced a router (Linksys) that behaved this way. Apparently buggy software in the router.

Does resetting the router fix the issue temporarily? If it does the router firmware might need an update.

---

### Post by hwttdz on 2010-02-18
I have not done a reset to factory settings I will try that.  Apparently holding down the reset button for 45 seconds doesn't get you a reset to factory settings.

---

### Post by blueturtl on 2010-02-18
What exact router is this?

Factory settings should not be necessary, a simple restart should restore the router to functional status.

---

### Post by hwttdz on 2010-02-18
Amazingly a firmware upgrade seems to have fixed the problem (at least at the moment).  Which saves me from having to invest in a new card/router.  Thank you for prompting me to do that.

Also I learned that my router can do hardware compression before sending packets over the wlan.  Now it's possibly working better than it was before it crapped out.

---

### Post by blueturtl on 2010-02-18
Good for you. Hope it stays fixed. May the spirit Ubuntu haunt your house. :)

---

