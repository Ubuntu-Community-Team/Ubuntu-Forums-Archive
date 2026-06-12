---
title: "Problems compiling PHP 4"
date: 2006-07-02
forum: Server Platforms
---

### Post by mssever on 2006-07-02
Because my web development work requires me to support both PHP 4 and 5, I'm trying to install PHP4 on my development server. It appears that installing PHP4 with Synaptic/aptitude will remove PHP5. So, I'm trying to compile PHP4 from source. Unfortunately, Ubuntu doesn't come with compilation tools, and I'm getting errors:
```
./configure --prefix=/usr/local/php4 --with-mysql --with-apxs2
<snip>
checking whether ln -s works... yes
checking for gawk... no
checking for mawk... mawk
checking for bison... bison -y
checking bison version... configure: warning: You will need bison 1.28
2.1 (ok)
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 2540: lex: command not found
configure: error: cannot find output from lex; giving up
```
I haven't been able to find a package named "lex." What do I need in order to configure and compile PHP4?

Also, how important is apxs2? If the --with-apxs2 flag merely instructs PHP to make an Apache2 module, then I'm fine. However, if it really does need apxs2 in order to compile, than I need to know how to get it. It isn't part of the apache2 package, and the Apache2 tarball that I successfully compiled for my old Red Hat installation won't compile under Ubuntu.

---

### Post by mssever on 2006-07-02
Update: I've managed to convince Apache to compile by disabling everything (which is OK since I'm going to delete it as soon as I successfully compile PHP4). The point is that I now have apxs. I'm now using the following configure line for PHP4:
```
./configure --prefix=/usr/local/php4 --with-mysql --with-apxs2=/opt/apache2/bin/apxs
```

---

### Post by mssever on 2006-07-02
OK...I decided to see if I had flex--turns out that I didn't. When I installed flex, configure worked just fine. It would be nice if configure would complain about flex instead of lex.

---

