---
title: "sogo shared calender unmet dependences"
date: 2009-08-26
forum: Server Platforms
---

### Post by SlugSlug on 2009-08-26
Hi
I have a fresh 8.04 install and I am trying tio make it a shared calendar server to tie in with outlook.

1st road block:
I followed instruction here to add to the sources.list  [html]http://www.scalableogo.org/english/support/faq/article/how-to-install-sogo-on-ubuntu.html[/html]and added the sources.

now apt-get install sogo throws up..

```
 sudo apt-get install sogo
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  sogo: Depends: gnustep-back0.14 (>= 0.14.0) but it is not installable
        Depends: gnustep-base-runtime (>= 1.16.1) but 1.14.1-2ubuntu1 is to be installed
        Depends: gnustep-gpbs (>= 0.14.0) but it is not going to be installed
        Depends: gnustep-gui-runtime (>= 0.14.0) but 0.12.0-3ubuntu1 is to be installed
        Depends: libgnustep-base1.16 (>= 1.16.1) but it is not installable
        Depends: libgnustep-gui0.14 (>= 0.14.0) but it is not installable
        Depends: libsope-appserver4.9 (>= 4.9.r1660) but it is not going to be installed
        Depends: libsope-core4.9 (>= 4.9.r1660) but it is not going to be installed
        Depends: libsope-gdl1-4.9 (>= 4.9.r1660) but it is not going to be installed
        Depends: libsope-ldap4.9 (>= 4.9.r1660) but it is not going to be installed
        Depends: libsope-mime4.9 (>= 4.9.r1660) but it is not going to be installed
E: Broken packages
```

---

### Post by SlugSlug on 2009-08-26
I upgraded to 8.10 and that solved it

---

### Post by SlugSlug on 2009-08-27
has anyone managed to get this sogo working on ubuntu?

---

