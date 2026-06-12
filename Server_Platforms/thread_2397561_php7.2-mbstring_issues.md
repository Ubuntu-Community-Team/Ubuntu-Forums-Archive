---
title: "php7.2-mbstring issues"
date: 2018-07-31
forum: Server Platforms
---

### Post by bcurtis-rsu3 on 2018-07-31
php7.2-mbstring : Depends: php7.2-common (= 7.2.3-1ubuntu1) but 7.2.7-0ubuntu0.18.04.2 is to be installed

I am trying to get php7.2-mbstring installed, because wordpress is saying ```
User/Customer CSV Import Export requires the function mb_detect_encoding to import and export CSV files. Please ask your hosting provider to enable this function.
``` 

Ubuntu 18.04 installed. 

Thank you for any advice

---

### Post by thelatinist2 on 2018-07-31
I'm having the same issue with both this package and php7.2-imap.  It appears that these two packages in the Universe repository depend on an earlier version of php7.2-common than is in the main repository.  I have no idea how to fix this.

---

### Post by jstn128 on 2018-08-02
> **bcurtis-rsu3 said:**
> php7.2-mbstring : Depends: php7.2-common (= 7.2.3-1ubuntu1) but 7.2.7-0ubuntu0.18.04.2 is to be installed

I am trying to get php7.2-mbstring installed, because wordpress is saying ```
User/Customer CSV Import Export requires the function mb_detect_encoding to import and export CSV files. Please ask your hosting provider to enable this function.
``` 

Ubuntu 18.04 installed. 

Thank you for any advice

You have to enable universe in security and updates in your /etc/apt/sources.list file. 

```

deb http://archive.ubuntu.com/ubuntu bionic main universe
deb http://archive.ubuntu.com/ubuntu bionic-security main universe
deb http://archive.ubuntu.com/ubuntu bionic-updates main universe

```

---

