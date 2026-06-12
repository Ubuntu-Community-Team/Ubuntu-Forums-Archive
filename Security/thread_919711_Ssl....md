---
title: "Ssl...?"
date: 2008-09-14
forum: Security
---

### Post by Thomas.Kast on 2008-09-14
Is there a tutorial or something on how to install and run an ssl encryption using ubuntu? I read some of the posts and they said something about apache. Is this what i need or something?

---

### Post by tubezninja on 2008-09-14
Here you go:

[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

There's also this tutorial on configuring Apache for SSL:

[https://help.ubuntu.com/7.10/server/C/httpd.html#https-configuration](https://help.ubuntu.com/7.10/server/C/httpd.html#https-configuration)


Just a question, are you trying to run a website that requires SSL?

---

### Post by Thomas.Kast on 2008-09-14
It says that openssl is all ready installed on my version of ubuntu. So, would the only thing i have to do is work on the apache2 web server?

---

### Post by Thomas.Kast on 2008-09-14
> **scaredpoet said:**
> Just a question, are you trying to run a website that requires SSL?

No. I am just trying to figure out how to browse websites using an ssl encryption.

I am very new to this, and i am basically shooting in the dark with this. I heard this is how you do it, but im not totally convinced. Does anyone have a cule as to what i am talkin about?

---

### Post by Thomas.Kast on 2008-09-15
Nevermind...i am just an idiot new user to ubuntu.

---

### Post by Dave_Connor on 2008-09-15
SSL is just for encrypting the connections made on the web sever. You might want Tor since it will connect your computer to a proxy and then another with encrypting and decrypting your requests but it is slow which is why sometimes it doesn't work the best.

---

### Post by jerome1232 on 2008-09-15
> **Thomas.Kast said:**
> No. I am just trying to figure out how to browse websites using an ssl encryption.

I am very new to this, and i am basically shooting in the dark with this. I heard this is how you do it, but im not totally convinced. Does anyone have a cule as to what i am talkin about?

Well there is no setup for this on your end, the webserver is what must be configured to encrypt the connection. 

For example you goto your bank website and hit login, you should be directed to an [https://yourbank.com](https://yourbank.com) indicating that the connection is now encrypted from your computer to the banks webserver.

As was previously mentioned you can setup a proxy which encrypts traffic between your computer and the proxy computer, but if the webserver isn't using some form of encryption then information is still exchanged unencrypted from the proxy to the webserver.

---

### Post by SSVegito888 on 2008-09-15
I think he is talking about forwarding ports and tunneling over SSL.


I thought about doing the same thing, only with OpenSSH.

---

