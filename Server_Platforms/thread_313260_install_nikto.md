---
title: "install nikto"
date: 2006-12-05
forum: Server Platforms
---

### Post by JELO on 2006-12-05
Ok, so i'm trying to install nikto and i'm having trouble.  Went to install Net_SSLeay first, ran into 

Checking for OpenSSL-0.9.6j or 0.9.7b or newer...
You have OpenSSL-0.9.8a installed in /usr
That's is newer than what this module was tested with (0.9.6j
or 0.9.7b). You should
consider checking if there is a newer release of this module
available. Everything will probably work OK, though.
*** Could not figure out which C compiler was used to compile /usr/bin/openssl. It is essentiall that OpenSSL, perl, and Net::SSLeay are compiled with the same compiler and flags. Mixing and matching compilers is not supported. at Makefile.PL line 140.
Writing Makefile for Net::SSLeay::Handle
Writing Makefile for Net::SSLeay

and of course going to the next step make, gives back missing header files and what not.  So i'm thinking it's something with openssl because of this output 

SSLeay.xs:102:25: error: openssl/err.h: No such file or directory
SSLeay.xs:103:27: error: openssl/lhash.h: No such file or directory
SSLeay.xs:104:26: error: openssl/rand.h: No such file or directory
SSLeay.xs:105:28: error: openssl/buffer.h: No such file or directory
SSLeay.xs:106:25: error: openssl/ssl.h: No such file or directory
SSLeay.xs:107:74: error: openssl/comp.h: No such file or directory
SSLeay.xs:108:93: error: openssl/md5.h: No such file or directory
SSLeay.xs:109:26: error: openssl/x509.h: No such file or directory
SSLeay.xs:110:28: error: openssl/x509v3.h: No such file or directory

(it goes on for a good while with errors).
So I check to see if openssl is installed.  
sudo apt-get install openssl
says it's installed.  So I do the sudo dpkg -I openssl and it doesn't know what i'm talking about.  So I say ok, I go remove openssl with dpkg -r and --purge.  Then I go to the openssl website download the latest release.  Try to compile that and get more errors.
So what should I do?  I'm basically just going through a book on securing Apache and would like to get Nikto running in some fashion.  Looks like it might be a long road though, or maybe i just don't have something installed that I need to have installed.  Anywho help is appreciated.
Here is the link i'm using and they even mention the book that i'm using as well.
[http://www.howtoforge.com/apache_security_testing_with_nikto](http://www.howtoforge.com/apache_security_testing_with_nikto)
I am indeed using Ubuntu 6.06, the server version, no LAMP install.  Apache compiled and went on OK.
I did notice the compiler message, not sure if that's the trouble, but I don't know how to specify what compiler or tell what compiler compiled openssl.
Thanks

---

