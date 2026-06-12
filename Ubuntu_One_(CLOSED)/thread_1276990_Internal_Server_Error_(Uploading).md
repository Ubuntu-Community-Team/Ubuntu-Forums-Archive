---
title: "Internal Server Error (Uploading)"
date: 2009-09-27
forum: Ubuntu One (CLOSED)
---

### Post by XDevHald on 2009-09-27
Getting an Internal Server Error during upload on the server. Need a note if this is world wide or user side issue.

Thanks.

---

### Post by dr_dred5 on 2009-09-27
I'm having the same problem. New account.

---

### Post by joshuahoover on 2009-09-29
> **XDevHald said:**
> Getting an Internal Server Error during upload on the server. Need a note if this is world wide or user side issue.

Thanks.

Apologies for the upload issues. We were having some issues with our servers during this time. Things should all be fixed now.

Thank you,

Joshua

---

### Post by waterpot on 2009-10-08
sorry, i don't know

---

### Post by kurocan on 2009-10-09
I dont now

---

### Post by coronacolada on 2009-10-26
I too am getting this issue.

---

### Post by manoriax on 2009-10-26
Sometimes it works, other times it doesn't. Just got the same error, again.

---

### Post by joshuahoover on 2009-10-27
> **manoriax said:**
> Sometimes it works, other times it doesn't. Just got the same error, again.

We think we've identified the root cause of this problem and are rolling out a deployment on our servers today. If you still experience this issue after about four hours from now, please file a bug here: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug)

---

### Post by GalloLight on 2009-10-27
It works now.

---

### Post by manoriax on 2009-10-27
What was the problem if I may ask?

---

### Post by GalloLight on 2009-10-27
> **manoriax said:**
> What was the problem if I may ask?

At  the begining of upload the error appears, described below.
[FONT=Times New Roman]**Internal Server Error**

 The server encountered an internal error or misconfiguration and was unable to complete your request.
Please contact the server administrator, [EMAIL="webmaster@ubuntuone.com"]webmaster@ubuntuone.com[/EMAIL] and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.
Apache/2.2.8 (Ubuntu) mod_python/3.3.1 Python/2.5.2 mod_ssl/2.2.8 OpenSSL/0.9.8g Server at [u1files.ubuntu.com]("http://u1files.ubuntu.com/") Port 443[/FONT]

---

### Post by manoriax on 2009-10-28
Yeah, I encountered this, too. Then I should specify my question: Was it a coding mistake, or was it a httpd mistake and what have you Ubuntu One guys done to fix it? ^^

---

### Post by joshuahoover on 2009-10-28
> **manoriax said:**
> Yeah, I encountered this, too. Then I should specify my question: Was it a coding mistake, or was it a httpd mistake and what have you Ubuntu One guys done to fix it? ^^

OK, we believe this should be fixed for all users. The problem seemed to be with cookies and the different domains we use for different parts of the system. We made our upload/download servers use the same domain as the rest of the site and that appears to fix the issue. If you're still having problems, please let me know.

Thank you,

Joshua

---

