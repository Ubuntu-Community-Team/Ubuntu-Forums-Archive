---
title: "DOCUMENT_ROOT path changes depending on current directory"
date: 2008-11-11
forum: Server Platforms
---

### Post by Dashman01 on 2008-11-11
Hi guys,

I am currently moving a load of sites over from a Red Hat server to an Ubuntu server. Both dedicated servers.

I am now having problems on the new server with $_SERVER['DOCUMENT_ROOT'].

Basically, I usually include all of my files like so:
```
include $_SERVER['DOCUMENT_ROOT']."/inc/config.php";
```
This worked like a charm on all the Red Hat server, but breaks on the Ubuntu server.

If the server doc root is:
```
/domains/m/y/mydomain.co.uk/public_html
``` then the include code above works fine if called from a file within the *public_html* folder (test.php).

Thats all good, but, now say I put test.php in a subdir name, say, mysubdir:
```
/domains/m/y/mydomain.co.uk/public_html/mysubdir
``` then the same nclude code fails, with the error:
```
Warning: include(/domains/m/y/mydomain.co.uk/public_html**/mysubdir/inc/config.php**) [function.include]: failed to open stream: No such file or directory in /home/i/c/icodiscover/public_html/mysubdir/test.php on line 7
```
Notice how the path has now changed to include the subdirectory, and it is now looking for config.php in  /subdir/inc/

This is a huge pain, as it means I am going to need to change every instance of include $_SERVER['DOCUMENT_ROOT'] to relative paths throughout all my sites I am needing to migrate.

Can somebody please advise as to why this path changes? Is there anything I can do to change it? eg, in the default file etc?

Many thanks,

Dave

---

