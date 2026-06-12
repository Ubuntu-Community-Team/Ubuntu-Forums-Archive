---
title: "pam_unix(cron:session): session opened for user root by (uid=0)"
date: 2018-01-28
forum: Security
---

### Post by grhayes on 2018-01-28
Ok, just upgraded to 17.10 
Started getting an issue where webmin could no longer connect to the server ever so often.
Checked the logs and I am getting tons of these repeatedly. pam_unix(cron:session): session opened for user root by (uid=0)
So I am wondering what they changed in this update exactly that caused this?

The point is everything worked perfectly then the update messed it up. In my book that is a bug.
I get I am left at present going through cron and so on myself to fix it.

---

### Post by TheFu on 2018-01-30
That message just says that cron is running a job as root.  That is expected on most systems a few times an hour.  "tons" is a little subjective. What tasks is it doing?

I wouldn't expect upgrade processes to handle any needed modifications for anything outside the core OS. Breakage happens all the time with webapps as parts of the stack are updated.  The way I try to fix those sorts of issues is to follow the new instructions from the project team for installing onto the new OS.  It usually becomes clear that something in Apache or nginx changed or the project decided to move shared files to a different location.  So, I can only recommend visiting the webmin project website and working through their guides.

---

### Post by cariboo on 2018-02-01
One other thing to consider is that 17.10 end-of-life is in July 2018. I'd suggest upgrading to 18.04, after it is released in April, and stick with it, as it will be supported until 2023.

---

