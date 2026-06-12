---
title: "Installing bugzilla in server 7.10"
date: 2007-11-30
forum: Server Platforms
---

### Post by cocotu on 2007-11-30
Downloaded bugzilla from the web and trying to install it following their instructions: [http://www.bugzilla.org/docs/tip/html/installation.html](http://www.bugzilla.org/docs/tip/html/installation.html)

and I get: (after running sudo perl -MCPAN -e 'install Email::Send')
the command runs for a little while and then:

WARNING: LICENSE is not a known parameter.
Checking if your kit is complete...
Looks good
'LICENSE' is not a known MakeMaker parameter name.
Writing Makefile for Email::Address
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for R/RJ/RJBS/Email-Send-2.192.tar.gz
  Is already unwrapped into directory /home/rg/.cpan/build/Email-Send-2.192

  CPAN.pm: Going to build R/RJ/RJBS/Email-Send-2.192.tar.gz

Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

Anybody have seen this? thanks

---

