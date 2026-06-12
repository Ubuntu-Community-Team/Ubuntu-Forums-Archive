---
title: "code 5.50 from a postmaster."
date: 2008-01-11
forum: Server Platforms
---

### Post by sergio gioia on 2008-01-11
when I receive from a postmaster code 5.50, then I resend the same e-mail does this mean the e-mail went trough this time?

---

### Post by MJN on 2008-01-11
The answer is, unfortunately, 'it depends'...
 
- SMTP status/error codes are completely under the control of the recipient MTA hence what could be a permanent error at their end may give rise to only a temporary code, and vice versa
- SMTP status/error codes, whilst specified in the RFCs, are not absolute - you are better off reading the 'human readable' explanation that likely accompanied the code - post the whole error if you need further info
- A 550 is usually 'mailbox unavailable' - this could be either temporary or permanent. The only certainty is that the original message did **not** get delivered.
- Your subsequent message may, or may not, have been delivered. The lack of a response code may merely mean it has yet to be processed yet, or is sat in a message queue following a temporary problem, or some other reason e.g. mail server accepted the message then fell over. It largely depends on what the explanation given with the initial delivery failure was.
 
The bottom line is that you cannot tell with certainty if a message has been successfully delivered, not without telephoning the recipient and asking them.. ;)
 
Mathew

---

### Post by envygeeks on 2008-01-11
You've been blocked mate. :( Time for the WTF Call. Or at least the last time I saw that error that was the case :p

You should see something like "#5.50 smtp; 550 Blocked".

That could simply also relate to the above and it being rejected.

---

