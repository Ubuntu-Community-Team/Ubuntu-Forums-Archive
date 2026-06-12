---
title: "Managing the repositories"
date: 2005-08-02
forum: Ubuntu Backports
---

### Post by SithLord on 2005-08-02
Hi,

I don't know which tool(s) is(are) used to maintain and manage the backports repository. I also backport and/or create packages to Hoary for pure pleasure and experiment. As I wanted to use a real "pool" of packages (and not a simple directory updated via apt-ftparchive) I've tried every available tool to achieve my goal. So, I tested apt-ftparchive, mini-dinstall, debarchiver and debpool. The only one I did not test was of course Katie which is the tool used for real Debian repositories but it needs a PostgreSQL database which makes it way to big for simple repositories (less than 200 packages). I've even wrote a script to create and maintain a pool but it wasn't really managed like a real one :-)

None of these tools were fully satisfying. Some of them are close to be perfect (debpool) but lack some features (like removing a package from the pool), some involve too many dependencies for my taste and finally others are very difficult to setup correctly.

Finally, I found the pure jewel ! Reprepro ([http://mirrorer.alioth.debian.org/](http://mirrorer.alioth.debian.org/)) and testing it proved me good. This tool is amazing ! It's simple to setup, it's very efficient, very configurable, very strict on what it accepts in the repository and it's blazing fast !

I had a small problem when I tried to make my backports look like the backports one can find here (using the '~' char in the name) and reported the problem to the author (Bernhard R. Link) and one day later, I got a patch to fix it ! Bernhard was very helpful and very prompt to reply mails, which is very nice.

So, now I'm very happy with reprepro, I suggest UbuntuForums.org backport developpers and maintainers to have a look at this excellent tool. You'll have to apply a small patch to make it accept the '~' char in package names. Here is the patch:

```
Index: names.c
===================================================================
RCS file: /cvsroot/mirrorer/mirrorer/names.c,v
retrieving revision 1.38
diff -u -r1.38 names.c
--- names.c     8 Jun 2005 15:45:19 -0000       1.38
+++ names.c     2 Aug 2005 10:04:09 -0000
@@ -636,7 +636,7 @@
 //TODO: more corectly another check should be here to also look for a digit...
        }
        while( ( *n >= '0' && *n <= '9' ) || ( *n >= 'a' && *n <= 'z')
-                       || ( *n >= 'A' && *n <= 'Z' ) || *n == '.'
+                       || ( *n >= 'A' && *n <= 'Z' ) || *n == '.' || *n == '~'
                        || *n == '-' || *n == '+' || (hadepoch && *n == ':') )
                n++;
        *version = n;
```

---

