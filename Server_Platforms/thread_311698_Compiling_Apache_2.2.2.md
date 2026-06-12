---
title: "Compiling Apache 2.2.2"
date: 2006-12-03
forum: Server Platforms
---

### Post by mwells on 2006-12-03
Hi all,

I'm currently trying to compile apache 2.2.2 on edgy using [this]("http://doc.gwos.org/index.php/Latest_Apache_and_PHP") guide.

When I get to running checkinstall the program ends with;

```

cp: setting permissions for `/usr/local/apache2/modules/httpd.exp':
No such file or directory cp: preserving ACL for `/usr/local/apache2/modules/httpd.exp':
No such file or directory make[1]:
 *** [install] Error 1 make[1]:
Leaving directory `/home/matthew/Desktop/src/httpd-2.2.2/support' make: *** [install-recursive] Error 1 
**** Installation failed. Aborting package creation. 
Cleaning up...
OK Bye.

```

Anybody have any clues why it would be terminating here? I havnt tried running 'install' as I was ideally wanting to make the .deb. and I'm not entirely sure how I would go about removing it all easily with install

Many thanks indeed

~Matt

---

### Post by pay on 2006-12-03
Make sure that you have gcc installed```
sudo aptitude install build-essential
```

---

### Post by mwells on 2006-12-03
Hi,

Many thanks for the quick reply but I have definitely got build-essential installed. Would there be anything else I would need?

Cheers

~Matt

---

### Post by pay on 2006-12-03
If you have apache in the repository you can download the files needed```
sudo apt-get build-dep apache2
```

---

### Post by mwells on 2006-12-03
Hi,

Once again, thanks for the reply.

Exactly what would that command do.

I was really wanting the latest version of Apache (tho i'm sure there will be no real difference between the repo version and te latest), I was just really after the experience of building it from source.

Many thanks

~Matt

---

### Post by pay on 2006-12-03
that command would download all the dependencies of apache for building but it won't downlaod apache.

---

