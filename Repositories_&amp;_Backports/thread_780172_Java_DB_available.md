---
title: "Java DB available?"
date: 2008-05-03
forum: Repositories &amp; Backports
---

### Post by hencq on 2008-05-03
Hi,

I was looking for a Java DB (or Apache Derby) package in Hardy. I found two: sun-java6-javadb and sunwderby. However, they depend on sun-java6-jdk and sun-java5-jre respectively. I've installed openjdk and would prefer not to have to install another jdk just to use this package.

I am missing something and is there a Java DB package for openjdk also or is it not available for openjdk (yet)? What other options do I have?

---

### Post by elst on 2008-05-03
By coincidence, I was looking into this this morning. Java DB is now being provided by a new set of packages called sun-javadb-*, but the old packages (that you mentioned) are still in the repositories.

```

:~$ apt-cache search sun-javadb
sun-javadb-client - Java DB client
sun-javadb-common - Java DB common files
sun-javadb-core - Java DB core
sun-javadb-demo - Java DB demo
sun-javadb-doc - Java DB documentation
sun-javadb-javadoc - Java DB javadoc

```

---

### Post by hencq on 2008-05-03
Wow, thanks very much! Can't believe I missed those. :)

---

