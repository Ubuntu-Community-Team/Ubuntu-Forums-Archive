---
title: "Bank website issues"
date: 2008-12-04
forum: Windows
---

### Post by Thelasko on 2008-12-04
My fiancee recently updated her web browser to Firefox 3 on her Windows XP machine.  Upon doing so, she noticed that she lost the ability to access her Capital One account.  I pointed out that it could be due to the fact that Capital One doesn't use extended validation certificates.  However, she added an exception, and still can't access her account.

She has been forced to use my Ubuntu machine to access her account.  Although this is more secure, I still wonder what the problem is.  Any thoughts?

---

### Post by Nxion on 2009-01-06
Can you give more info? Does she get an error? I have a Capital One card as well and it works fine in Firefox. Can you give a bit more detail to the issue at hand?

---

### Post by Thelasko on 2009-01-12
I figured it out.  The error said:

> Secure Connection Failed
xxx uses an invalid security certificate
Error Code: sec.error.expired certificate

I posted a while back about a broken clock on the same machine.  I never fixed the clock, and after a while the date was so far off that security certificates were showing up invalid.  Once the date was fixed, everything worked fine.

---

