---
title: "can't install postfix"
date: 2008-12-12
forum: Server Platforms
---

### Post by bandito40 on 2008-12-12
When installing postfix I get stuck on the following screen:

Package configuration


 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Postfix Configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; The "mail name" is the domain name used to "qualify" mail addresses       &#9474; 
 &#9474; without a domain name.                                                    &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; This name will also be used by other programs. It should be the single,   &#9474; 
 &#9474; fully qualified domain name (FQDN).                                       &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Thus, if a mail address on the local host is [email]foo@example.org[/email], the         &#9474; 
 &#9474; correct value for this option would be example.org.                       &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; System mail name:                                                         &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; localhost.com____________________________________________________________ &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                    <Ok>                        <Cancel>                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;


Neither <OK> or <Cancel> seam to work.  



I tried purging postfix but I get the following error:

dpkg: error processing postfix (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)




Then I tried:  sudo dpkg --reinstall postfix

which gave me the following error:

dpkg: error processing postfix (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 postfix


Anyone know what I can do about this error?

Thanks,

Bandito

---

### Post by asommer on 2008-12-16
You might try:

> apt-get -f install

To see if that will re-install postfix correctly.

---

