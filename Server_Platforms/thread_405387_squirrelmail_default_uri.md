---
title: "squirrelmail default uri"
date: 2007-04-09
forum: Server Platforms
---

### Post by frisket on 2007-04-09
I need to run a web-based mailer on my Edgy desktop, and I'm away from base. I can ssh into it, so I installed squirrelmail using apt-get, plus suggested dependencies (pear, php, dovecot-imap, etc: I already had apache2 running). 

Everything has gone fine, so I went through the config script in tty mode. The only thing it doesn't tell me is what URI I should used to access squirrelmail. I've tried the obvious [http://myhostname.myorg.com/squirrelmail](http://myhostname.myorg.com/squirrelmail), but that's a 404. 

a) Where on earth does squirrelmail hide itself? 
b) Is there some additional thing I need to do under Ubuntu to bring it up?
c) Is this piece of information documented somewhere. It's not in the SQM docs (which is why I thought this might be a Debian/Ubuntu variation).

---

### Post by bernied on 2007-04-09
I don't know where it's documented but I used a link:
```
/var/www # ls -alh mail
lrwxrwxrwx  1 root root   24 Mar 24 21:24 mail -> /usr/share/squirrelmail/
```
Then it is at [http://mywebsite.co.uk/mail](http://mywebsite.co.uk/mail)

Does that help?

EDIT: that's not my website, BTW, and it's the pesky forum that automatically added the hyperlink

---

### Post by frisket on 2007-04-09
Duuh. Thanks...I had assumed that the installation would either install squirrelmail under the document root, or link it in automatically. So much for installation transparency. Now it's complaining that IMAP isn't on port 111 (the portmapper/sunrpc port) instead of port 143.

---

### Post by MJN on 2007-04-10
You might find it easier to just download Squirrelmail from their site and install it yourself. I say install but in reality it's just a big bunch of php pages that need to sit somewhere in your webspace (e.g. domain.com/mail etc). Not only do you then know where everything is but you'll also get the latest version.
 
Mathew

---

### Post by bernied on 2007-04-10
> **frisket said:**
> Now it's complaining that IMAP isn't on port 111 (the portmapper/sunrpc port) instead of port 143.
There's a perl configuration script to sort all this stuff out.
```
squirrelmail-configure
```

---

