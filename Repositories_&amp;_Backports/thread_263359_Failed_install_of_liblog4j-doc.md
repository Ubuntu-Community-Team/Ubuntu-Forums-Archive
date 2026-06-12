---
title: "Failed install of liblog4j-doc"
date: 2006-09-23
forum: Repositories &amp; Backports
---

### Post by Hikaru79 on 2006-09-23
I tried to install the liblog4j-doc package, but it constantly gives me this error:
```
adrian@adrian-desktop:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up liblog4j1.2-java-doc (1.2.12-1ubuntu2) ...
cannot create dhelp file '/usr/share/doc/liblog4j1.2-java-doc/docs/.dhelp': No such file or directory
dpkg: error processing liblog4j1.2-java-doc (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 liblog4j1.2-java-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I've searched the forums, nobody else has reported this problem, so it's unlikely this is a problem upstream. Anyone have any ideas? Thanks :)

---

### Post by daller on 2006-09-23
Run this command:

```
touch /usr/share/doc/liblog4j1.2-java-doc/docs/.dhelp
```

And try to install it again!

I can't find the package on my system! - Are you using special repos?

---

### Post by Hikaru79 on 2006-09-23
Thanks, daller :) Actually, I had to modify it a bit. First I had to create the liblog4j1.2-java-doc folder, then the docs folder, THEN I had to touch .dhelp. Then it installed fine. Thanks for the idea :)

Also, I think it's just in multiverse (like most Java-related packages); actually, I mis-transcribed its full name. The full name is liblog4j1.2-java-doc

---

