---
title: "wordpress installation problem"
date: 2016-10-20
forum: Server Platforms
---

### Post by caravaggio971 on 2016-10-20
Hello, I've messed up my Ubuntu Server. Im trying to install Wordpress but when  running the followin command 
```
curl -O https://wordpress.org/latest.tar.gz
```
i get this error 
```
curl: error while loading shared libraries: libgcc_s.so.1libc.so.6: cannot open shared object file: No such file or directory
```

Any help?

Thank you!

---

### Post by Zero_Bytes on 2016-10-21
Have you tried the alternative, wget ?

If you want to fix curl, try removing or repairing with apt-get or check out 5.8 in this curl FAQ [https://curl.haxx.se/docs/faq.html#5.8](https://curl.haxx.se/docs/faq.html#5.8)

---

### Post by Habitual on 2016-10-21
```
wget https://wordpress.org/latest.tar.gz
```
does work also.

---

### Post by Vegan on 2016-10-22
do not forget to unpack the package

[COLOR="#FF0000"]tar -xvf latest.tar.gz[/COLOR]

---

### Post by SeijiSensei on 2016-10-22
> curl: error while loading shared libraries: libgcc_s.so.1libc.so.6: cannot open shared object file: No such file or directory
If that is literally the error, and not a typo, something very strange is going on with the libraries curl thinks it's using.  If it's really looking for "libgcc_s.so.1libc.so.6" that has to be a bug in coding or packaging curl.

---

