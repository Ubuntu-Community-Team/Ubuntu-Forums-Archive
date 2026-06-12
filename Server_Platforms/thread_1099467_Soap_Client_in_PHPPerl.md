---
title: "Soap Client in PHP/Perl"
date: 2009-03-18
forum: Server Platforms
---

### Post by Johnsie on 2009-03-18
Hi, I need to write a Soap client for work and I'm trying to try some basic stuff before I write it.

Is there anything special I need to do do get the following code working?

> 

  #!perl -w

  use SOAP::Lite;

  my $soap = SOAP::Lite
    -> uri('http://www.soaplite.com/Temperatures')
    -> proxy('http://services.soaplite.com/temper.cgi');

  print $soap
    -> c2f(37.5)
    -> result;





The function on the server is a simple function to convert celsius to fahrenheit.

A php client would also be useful. Thanks to anyone who can help,

Johnsie

---

