---
title: "Time and timezone problem"
date: 2016-05-19
forum: Server Platforms
---

### Post by jrmymllr on 2016-05-19
I'm using Server 14.04 LTS to run a security camera system.  The client side of this system runs on Windows, and to determine what time to display on the video recordings, it compares the timezones of the server and client (it's a purchased software).  

Here's the problem: Linux says it's -5:00 offset (date +'%:z %Z'), and Windows 7 says -6:00.  However, both machines are set to Central time, and both have the correct time.  On Linux, 'date' reports the correct time and timestamps are correct, and Windows display the correct time in its usual spot.  But since the offsets don't match, it's causing problems with the video camera system.  It would appear to me that Linux is correctly using -5:00 since DST is now in effect, but Windows isn't, although the box for "Automatically adjust for DST" is checked.

This seemingly simple problem has plagued me for months, but I've just lived with it.  Now I want to fix it, but I'm not sure where to start.  Every other Windows machine exhibits the same problem, XP and 7.

The company that sells the software has basically pointed out the offset difference and said "there's the problem".

---

### Post by howefield on 2016-05-19
Thread moved to the "*Server Platforms*" forum.

---

### Post by jrmymllr on 2016-05-19
I previously posted about this issue, but want to take it from a different angle.

I'm using Server 14.04 LTS, and what I need is for the timezone behavior to be like Windows due to a client/server problem I'm having.  I figured it's easier to change Linux's behavior than Windows.

Ubuntu is apparently changing the timezone offset between -5:00GMT and -6:00GMT depending on if we're in DST or not.  Windows, on the other hand, appears to maintain the offset at -6, but applies a DST correction after, so there's a mismatch between the client and server's GMT timezone offset.

Is there a way to make Ubuntu keep the reported timezone offset the same regardless of whether DST is in effect or not, and still adjust for DST, similar to Windows?

---

### Post by QIII on 2016-05-20
Threads merged.

This is essentially the same as your previous thread.  Please don't create multiple threads regarding the same issue.  It dilutes the community's efforts and gets confusing for everyone.

Thanks!

---

