---
title: "Http_requests, php and apache"
date: 2009-02-28
forum: Server Platforms
---

### Post by danharper on 2009-02-28
Hello,

I have a LAMP server sat behind a seperate proxy and I can't seem to find any information regarding directing php http_requests through the proxy.

For example I am hosting a local intranet on the server and would like to display news items from the bbc.co.uk on the main page using ther rss feeds but when I try and connect to the feed with a php script it always fails.

I can run all my ubuntu updates through the proxy no problem as I have set the http_proxy variable I can also peform wget etc.

Any help on troubleshooting this would be appreciated as I have been searching the net for ages about this one

Cheers Dan

---

### Post by JeppeM on 2009-02-28
Hey,

You can use the http request class to do this i think, you can read more here: [http://ca3.php.net/manual/en/http.request.options.php](http://ca3.php.net/manual/en/http.request.options.php)

But what i'm really interested in is why your server doesn't just defualt to using the proxy. How did you set the proxy for the system to use so that wget is able to access the feed? I'm thinking it might be a user-specific setting, and not system-wide, which would explain why PHP is not using it, since it runs on a different user (at least normally it does)

---

### Post by danharper on 2009-03-01
I see what you mean, I just did "export http_proxy=http://host: port/" while logged in as root.

Cheers Dan

---

### Post by danharper on 2009-03-04
I'm still having problems with this as, anybody any other ideas.

Cheers Dan

---

### Post by JeppeM on 2009-03-04
Ah, figured you knew how to fix it when you didn't ask anything in your latest reply :P

Anyways, try adding export http_proxy=http://host: port/ to /etc/profile and then restart apache and see if that helps... You might have to restart the whole system - Not sure though

---

### Post by danharper on 2009-03-05
Tried all of the above including a reboot, is it possible it is to do with the routing table?

Cheers Dan

---

### Post by JeppeM on 2009-03-06
Wierd... it should work... :S

Routing tables aint my strongest part, so i'll let someone else answer that for you - sorry i couldnt be of more help.

---

### Post by danharper on 2009-03-06
When I try to load an external xml file like a feed from the bbc in a php script I get this error message

[function.simplexml-load-file]: failed to open stream: Connection refused

I have tried reinstalling and compiling pecl_http and doing a whole range of other things.

Any more ideas would be helpful

Cheers Dan

---

### Post by danharper on 2009-07-10
Still having issues with this, anybody got any other ideas.

Cheers Dan

---

