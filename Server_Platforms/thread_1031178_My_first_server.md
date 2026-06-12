---
title: "My first server"
date: 2009-01-05
forum: Server Platforms
---

### Post by jharadie on 2009-01-05
I'm finally in a position to setup a small home server.  Yay!  I want to use 8.04LTS text-only.  I'll probably be putting it on an old laptop (Dell Inspiron 2150, 256M RAM, 18G HD), though there is the danger that I might have to resort to a very very old Compaq that has only 192M RAM.  I mainly want to use it to act as an email-to-fax gateway for [www.tpc.int](www.tpc.int).  Here are my questions:

I don't need MySQL, but I should go ahead and install LAMP, then sudo apt-get remove MySQL?  Isn't there another apt-get command to remove leftover MySQL files?

Same as above for Postfix.  tpc.int really prefers sendmail, though I need to find a way to get it to use my Comcast account for outbound mail.  All HOWTOs, suggestions, links would be appreciated.  I would install Dovecot and Mutt, for local delivery and also now that Yahoo lets me POP3 other accounts.

I'm guessing I need Putty on the server as well as my main machine for management.  Also Open SSL?  Input on that would be appreciated, too.

At least I know how to do Samba.  No problem there.

I'll also have to download and install HylaFax, but that's a separate issue from this forum.

When LAMP installs PHP5, does it also install the PEAR module so "mail" in a php script works?  If not, how do I install that module?

The server will primarily function as an email-to-fax gateway, second, there will be a couple of php scripts (and possibly a cgi script) that gather info and mail to me on a daily basis.  To have a HOWTO to get sendmail to get around the Comcast port 25 block and send the emails directly to my Yahoo account would be a tremendous help (so I don't have to POP3 everytime I login to my Yahoo account).  I looked at the Postfix and Exim HOWTOs and they are just way too overwhelming for this noob.

I don't plan to put up webpages (other than one that says Hello), or do other fancy stuff.

All suggestions, comments, links to HOWTOs, etc., would be greatly apprecaited.  Thank you.

:)

---

### Post by kamaji792 on 2009-01-05
I prefer to install the most basic system and then add packages as I need them (it is so simple with apt-get).  That way you get the latest version.

I just use the ubuntu server guide for install information:
[https://help.ubuntu.com/8.04/serverguide/C/index.html]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

and when I want to find a package use:
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

I don't think you will need Putty on your server but you will need OpenSSH on the server.

For pear I guess you will need to:
```

sudo apt-get install php-pear

```

All the best

---

### Post by Iowan on 2009-01-05
[howtoforge.com]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") has a "Perfect Server" article that includes a mail server.

---

