---
title: "modsecurity"
date: 2008-11-14
forum: Server Platforms
---

### Post by daboroe on 2008-11-14
trying to install modsecurity for apache2. 

using this website

[http://www.debuntu.org/2006/08/13/86-secure-your-apache2-with-mod-security](http://www.debuntu.org/2006/08/13/86-secure-your-apache2-with-mod-security)

this command does not work:      $sudo apt-get install libapache2-mod-security


any suggestions.

---

### Post by MJN on 2008-11-14
libapache2-mod-security was removed from the repository due to licensing issues (incompatibilities between the Apache and GPL licences).
 
There is a replacement from [http://www.modsecurity.org/](http://www.modsecurity.org/) that may be of use and, given it addresses the licencsing issues, may well end up packaged for Ubuntu (perhaps it is already - I don't know as I don't use it).
 
Mathew

---

### Post by daboroe on 2008-11-15
> **MJN said:**
> libapache2-mod-security was removed from the repository due to licensing issues (incompatibilities between the Apache and GPL licences).
 
There is a replacement from [http://www.modsecurity.org/](http://www.modsecurity.org/) that may be of use and, given it addresses the licencsing issues, may well end up packaged for Ubuntu (perhaps it is already - I don't know as I don't use it).
 
Mathew

do you have a good tutorial on how to compile, create an install, etc and set it up on ubuntu?

---

### Post by MJN on 2008-11-15
Sorry, no. As I said, I don't use it.

Mathew

---

### Post by max_at_app on 2008-11-15
Hi, there is a tut on how to install modsecurity by source code but it need that you read the comment too.

[http://www.vinno.net/linux/server/how-to-install-mod-security-2]("http://www.vinno.net/linux/server/how-to-install-mod-security-2")

Also there is a difference in the procedure, you do not change the Makefile as he said, instead you simply execute ./configure and go on to compile and install.

example:
1 ) sudo apt-get install apache2
2 ) sudo apt-get install apache2-prefork-dev libxml++2.6-dev liblua5.1-0 liblua5.1-0-dev libcurl3-dev
3 ) cd /tmp
4 ) wget [http://www.modsecurity.org/download/modsecurity-apache_2.5.7.tar.gz](http://www.modsecurity.org/download/modsecurity-apache_2.5.7.tar.gz)
5 ) tar xfz modsecurity-apache_2.5.7.tar.gz
6 ) cd modsecurity-apache_2.5.7/apache2
7 ) ./configure
8 ) make
9 ) sudo make install
10 ) etc..

at this point follow the tutorial.

I stop all when I get some warning messages at make step and now I'm looking for a solution. If you go on and complete any of the tutorial step, please tell me if it work or if not.
Thanks

ps. the warnings are:

```
apache2_io.c: In function 'input_filter':
apache2_io.c:113: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c:113: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c:113: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c:125: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c:125: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c:125: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c: In function 'prepend_content_to_of_brigade':
apache2_io.c:439: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c:439: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c:439: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c: In function 'output_filter':
apache2_io.c:582: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c:582: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_io.c:582: warning: dereferencing type-punned pointer will break strict-aliasing rules
```

and 
```

apache2_util.c: In function 'send_error_bucket':
apache2_util.c:51: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_util.c:51: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_util.c:51: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_util.c:56: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_util.c:56: warning: dereferencing type-punned pointer will break strict-aliasing rules
apache2_util.c:56: warning: dereferencing type-punned pointer will break strict-aliasing rules
```

anyone can help us, Thanks again

---

### Post by daboroe on 2008-11-15
i followed your instructions and the tutorial you provided and i got everything running. The only thing i did was not edit the makefile like it said to do 


thanks

---

### Post by max_at_app on 2008-11-15
well, I'm happy for you!

Ubuntu 8.04 or 8.10 ?

Do you get any warning messages on the make execution ?

Thanks

---

### Post by Vinno on 2008-11-16
I will take a look at newest mod security release and do a write up.

---

### Post by max_at_app on 2008-11-16
Hi Vinno, it's a good news!

I greatly appreciate your help as your latest tut on mod-security.

It seems that the warning messages that I have during the compilation are due to incompatibility with the version of gcc. we should use the flag "-fno-strict-aliasing" but I do not know where. More information: [http://www.nabble.com/warning%3A-dereferencing-type-punned-pointer-will-break-strict-aliasing--rules-td11773414.html]("http://www.nabble.com/warning%3A-dereferencing-type-punned-pointer-will-break-strict-aliasing--rules-td11773414.html")

Let me know. Thanks

---

### Post by Vinno on 2008-11-16
I think you can safely ignore it until modsecurity team updates their code to reflect new changes. Seems like the later version of gcc will pick up on that will report it and the earlia builds didnt.

---

### Post by Vinno on 2008-11-16
Also updated the guide.

---

### Post by max_at_app on 2008-11-16
It seems that the Modsecurity Team still use an old version of gcc ( < v3.x ), obviously know that they have to change some parts of the code.

In any case, I do not trust those messages warning because I do not know if the functions to which they relate are affected or compromise in their excutions. For this reason, anyone, before using it in production environment, should do some tests and verify the proper functioning of all modsecurity rules used.

Many thanks Vinno

---

### Post by daboroe on 2008-11-19
> **Vinno said:**
> Also updated the guide.

thank you vinno! do those instructions work for 8.0.4 LTS as well?  that is what I am running. Also when I initially installed mod_security2 it would throw an Error 400 at me. Any reason why? I followed steps that were up  before to the letter.

Thank you

DaBoROE

---

### Post by Vinno on 2008-11-19
> **daboroe said:**
> thank you vinno! do those instructions work for 8.0.4 LTS as well?  that is what I am running. Also when I initially installed mod_security2 it would throw an Error 400 at me. Any reason why? I followed steps that were up  before to the letter.

Thank you

DaBoROE

Yeah it should, the only thing that has changed for gutsy < -- > intrepid was mod security make file regarding the instruction.

Post up some more info on the 400 error, check apache log + mod security 2 audit / debug log.

---

### Post by daboroe on 2008-11-19
> **Vinno said:**
> Yeah it should, the only thing that has changed for gutsy < -- > intrepid was mod security make file regarding the instruction.

Post up some more info on the 400 error, check apache log + mod security 2 audit / debug log.
I have to re install it but I can probably do that while I am at work today. 

thanks

---

### Post by 3DLover on 2009-02-18
I just wanted to re-awaken this thread and point out that the licensing issues that removed mod_security from Debian have been resolved according to the README on this site: 
[http://etc.inittab.org/~agi/debian/libapache-mod-security2](http://etc.inittab.org/~agi/debian/libapache-mod-security2)

**** NEWS NEWS NEWS NEWS NEWS NEWS *****
Tue, 13 Jan 2009 08:52:41 +0100

mod_security is back in the Debian Official Archive.
Sid users can don't need to use this repository.

For lenny users I'll keep this place as updated as time permits.
**** NEWS NEWS NEWS NEWS NEWS NEWS *****

I would really like to see mod_security added back to the apt repositories.  Please?

---

### Post by belfasttim on 2010-03-27
can anyone update this or point me to an update? It seems that it's been over a year and I don't think mod_security is available.
Thanks

---

