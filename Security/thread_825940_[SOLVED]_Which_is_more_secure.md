---
title: "[SOLVED] Which is more secure?"
date: 2008-06-11
forum: Security
---

### Post by ene_dene on 2008-06-11
I share some files for everyone to download and I'm running vsftpd for the job. I could do the same with Apache. Which is the more secure method?

---

### Post by HermanAB on 2008-06-11
Everyone == Anonymous FTP?

Set FTP to read only and security is same as Apache.

An FTP server is however more efficient than an Apache server, so for large values of everyone, FTP is better.

Hope that helps.

Herman

---

### Post by cdenley on 2008-06-11
> **HermanAB said:**
> Everyone == Anonymous FTP?

Set FTP to read only and security is same as Apache.

An FTP server is however more efficient than an Apache server, so for large values of everyone, FTP is better.

Hope that helps.

Herman
How is it more efficient? I've heard this before, but never understood why.

---

### Post by ene_dene on 2008-06-11
> **HermanAB said:**
> Everyone == Anonymous FTP?Yes.
> **HermanAB said:**
> Set FTP to read only and security is same as Apache.It's set that way. So in this case it is equally secure. 

> **HermanAB said:**
> An FTP server is however more efficient than an Apache server, so for large values of everyone, FTP is better.

Hope that helps.

HermanYes, thanks.

---

