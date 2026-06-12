---
title: "Can't find site hosted on localhost"
date: 2007-02-02
forum: Server Platforms
---

### Post by yaohui on 2007-02-02
Hi all,

I am trying to run a BOINC project and the project has by default, setup a website on url [http://localhost.localdomain/meme](http://localhost.localdomain/meme) where 'meme' is the project name.

These are some of the parameters:
yaohui@memeboinc:~$ hostname
memeboinc
yaohui@memeboinc:~$ hostname -f
localhost.localdomain
yaohui@memeboinc:~$

However, when i try to access the site that it has created, the browser tells me 
Bad Gateway
The following error occurred:

[code=DNS_HOST_NOT_FOUND] The host name was not found during the DNS lookup. Contact your system administrator if the problem is not found by retrying the URL. 

I have my apache2 running. Any idea why?

---

### Post by smdeep on 2007-02-04
Hi

Do you get the same error if you try to access the site like this:

[http://localhost/meme](http://localhost/meme)

---

### Post by yaohui on 2007-02-04
Yes I do.

I get 500 Server Error.
"[code=CANT_CONNECT_LOOPBACK] Cannot connect due to potential loopback problems"

---

### Post by smdeep on 2007-02-05
Hi
I am sure this has something to do with the BOINC setup. To check whether Apache is running:

[http://localhost](http://localhost)

If that shows u a page that means there is nothing wrong with the Apache configuration.

Hope this helps

---

### Post by yaohui on 2007-02-08
Hihi,

Thanks!
You are right, there's nothing wrong with apache. I have resolved the problem by twiching with BOINC itself.

yaohui

---

