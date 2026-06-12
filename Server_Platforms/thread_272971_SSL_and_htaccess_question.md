---
title: "SSL and htaccess question"
date: 2006-10-07
forum: Server Platforms
---

### Post by Ronbo on 2006-10-07
I was wondering if someone might be able to answer a question.  I have an Apache2 server set up with SSL, one of the folders containing a PHP page is password protected with htaccess.  The question is when is the information passed between the client and server encrypted by SSL?  The reason I am asking is when someone tries to access the htaccess protected page they are asked if they accept the certificate.  If they accept they are immediatley asked for the Username and Password before being directed to the page, after entering that correctly they are granted access to the page.  My concern is whether the username and password are being sent over the network in plain text or if they are SSL encrypted at the point they are entered (which I hope is the case).  I was hoping someone here might be able to enlighten me.  Thanks.

---

