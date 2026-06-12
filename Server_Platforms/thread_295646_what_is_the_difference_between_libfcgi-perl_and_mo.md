---
title: "what is the difference between libfcgi-perl and mod_fastcgi?"
date: 2006-11-08
forum: Server Platforms
---

### Post by don7777 on 2006-11-08
I'm new to administering an apache2 server and I'm confused by these
two.

What is the difference between libfcgi-perl and mod_fastcgi?

Should I install both? Are they the same thing just provided by
different sources? Are the complementary?

thanks for any help,
Don

---

### Post by elst on 2006-11-09
I don't use Perl for Web applications, but I think that it works like this:

The old Apache module for FastCGI support is "mod_fastcgi". I think that this has been superceded by fcgid (the libapache2-mod-fcgid package).

For each programming language you also need to install a library that implements FastCGI support functions. I guess that the libfcgi-perl package provides the FastCGI support for Perl.

Hope that helps.

---

