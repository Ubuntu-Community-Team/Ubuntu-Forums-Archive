---
title: "Using Apache::Request"
date: 2005-10-05
forum: Server Platforms
---

### Post by daveman on 2005-10-05
I'm having trouble using Apache::Request with perl 5.8.7 on Breezy, although also had this on Hoary.  When I start Apache, with a PerlRequire in my virtualhost that uses this library I get the following output and Apache will not start.

[error] Can't load '/usr/lib/perl5/auto/Apache/Request/Request.so' for module Apache::Request: libapreq.so: cannot open shared object file: No such file or directory at /usr/lib/perl/5.8/DynaLoader.pm line 225.\n at /usr/lib/perl5/mod_perl.pm line 14\nCompilation failed in require at /home/david/fb/lib/Apache/FotoBilder/WebUpload.pm line 8.\n <snip>

Anyone encountered this before or have a solution?  I've tried fully removing the libapache-request-perl package and reinstalling it with no luck.  The file exists on disk and permissions look alright.  Ideas?  Thanks.

---

