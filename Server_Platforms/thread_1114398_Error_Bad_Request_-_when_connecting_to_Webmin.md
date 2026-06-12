---
title: "Error Bad Request - when connecting to Webmin"
date: 2009-04-02
forum: Server Platforms
---

### Post by redonwhite on 2009-04-02
Hello.  I have ubuntu server 8.10 installed.  I have installed webmin on my server box.  I have forwared port 10000 on my router.  But every time i type in [http://*ipaddress*:10000](http://*ipaddress*:10000) a page pops up that says 

**"Error Bad Request"**

 underneath that it says 

**"this web server is running in SSL mode try the URL https://*servername*.local:10000"** 

 When i click on that a page pops up saying 

[B]"media.local.10000 uses an invalid security certificate
The certificate is not trusted because it is self signed
(Error code: sec_error_untrusted_issuer)
- This could be a problem with the server's configuration, or it could be someone trying to impersonate the server.

- If you have connected to this server successfully in the past, the error may be temporary, and you can try again later.

Or you could add an exception..."[/B]

I clicked on "or you could add an exception to see what happened and then it said,
**"you should not add an exception if you are using an internet connection that you do not trust completely or if you are not used to seeing a warning for this server."**

Two buttons at buttom say **"get me out of here!"** and **"Add exception"**

Of course i hit get me out of here cause i got paranoid after reading all that haha.  Anyone know if this is normal or what i should do to get rid of a thing like this?  Thanks for your time.  I'm new to the server world.

---

### Post by bigbearomaha on 2009-04-02
Add the exception.

The browser is set to be hyper aware of self signed/unsigned certificates.

The certificate used by default in Webmin is a self signed one.

No need to panic.

Big Bear

---

### Post by redonwhite on 2009-04-02
> **bigbearomaha said:**
> Add the exception.

The browser is set to be hyper aware of self signed/unsigned certificates.

The certificate used by default in Webmin is a self signed one.

No need to panic.

Big Bear

Thank you sir.  That makes me feel better.

---

### Post by Psyrus on 2009-10-22
Hi. I'm having the same problem, only when I click on the link I end up with a 

"Server not found

Firefox can't find the server at (SERVERNAME)"

error.

Any advice? What can I check that might be missing?

---

### Post by terbor on 2009-11-28
I just fought with this for the last 30 min and it is late, kinda....make sure that your url is [https://[host]:port](https://[host]:port)

I was forgetting the S and getting this error.

---

