---
title: "Adobe Reader vulnerabilities"
date: 2006-09-15
forum: The Cafe
---

### Post by hizaguchi on 2006-09-15
In case you needed any more reason to avoid closed source binaries whenever possible, [Acrobat Reader has at least 7 vulnerabilities]("http://it.slashdot.org/it/06/09/15/239205.shtml").  I know open source software isn't completely 100% secure, but this is a simple reader!  I hope the open source ATI drivers support my card soon, because who knows what kind of nasties a kernel module could open me up to.

---

### Post by %hMa@?b&lt;C on 2006-09-15
reminds me of the ms word .doc vulnerabliites. Dont think they were ever patched.  All I can say o nthis is I am glad that I dont have acrobat reader installed.

---

### Post by jpkotta on 2006-09-16
Simple reader?  That thing is huge and slow.  But I'm a sucker - I still use it.  It renders better than the open source readers I've tried, and it has a browser plugin.

---

### Post by NiceGuy on 2006-09-16
It is worrying but my question is can it really effect us? I've only read about the first two of the 'backdoors' but neither of them (to my mind) can effect us.

The first one launches a browser window to initiate what is referred to as 'to launch drive-by malware downloads' but a) wouldn't firefox ask (and most browsers used on Linux) if we wanted to do this and b) even if we did foolishly click yes, then we would still need to change the permissions on the file and execute it (and probably as root to do any serious damage).

The second attack 'accesses the Windows ODBC (on localhost), enumerates available databases and then sends this information to 'localhost' via the Web service'

So again would that effect us? Could it changed to effect us? I'm not really experienced with data bases but don't most of them setup with a password by default?

If any one has any info about this then I'd be interested if we could be effected. I know we probably won't be (security because of obscurity) but CAN we be effected?

Mark

ps. anybody know what the other 5 backdoors are?

---

### Post by BillibibCogspinner on 2006-09-16
Simple reader?  I assume you are not familiar with PDF.  They aren't just pictures or text.  PDFs are complex programs that draw the document to the canvas.  Considering the complexity and the huge number of features involved in PDFs it is not surprising at all that there are many vulnerabilities.  By the same token xpdf (and libpoppler by extension) have a horrible security record.  This is no more shocking than a vulnerability in a Java VM.

---

### Post by Anduu on 2006-09-16
I can pretty much guarantee that any "hacks" exploiting these backdoors will target Windows machines...Linux is far to complex/secure for anyone to bother tryin to effect it.

---

### Post by banjobacon on 2006-09-16
> **jpkotta said:**
> It renders better than the open source readers I've tried

Ditto.

---

