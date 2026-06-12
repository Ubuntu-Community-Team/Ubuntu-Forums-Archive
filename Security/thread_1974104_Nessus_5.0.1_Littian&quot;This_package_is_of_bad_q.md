---
title: "Nessus 5.0.1: Littian:&quot;This package is of bad quality&quot;"
date: 2012-05-05
forum: Security
---

### Post by OtagoHarbour on 2012-05-05
I am using Ubuntu 11.10.  I downloaded Nessus 5.0.1 and tried to install it through the Ubuntu Software Center.  I got the message

This package is of bad quality.

The installation of a package which violates the quality standards isn't allowed.  This could cause serious problems on your computer.  Please contact the person of organisation who provided this package and include the details beneath.

Lintian check results for /home/peter/Nessus-5.0.1-ubuntu1110_i386.deb:
Use of uninitialized value $ENV{"HOME"} in concatenation (.) or string at /usr/bin/lintian line 112.
E: Nessus: package-not-lowercase

I have the options of OK and "Ignore and install"

Could anyone tell me whether I should choose the latter option and what does this error message/warning mean?

Many thanks in advance,
Peter.

---

### Post by ubuntu27 on 2012-05-05
I recommend to use gdebi to install Deb packages manually.

```
sudo apt-get instal gdebi
```
[URL="http://www.webupd8.org/2011/04/how-to-install-deb-files-when-getting.html"]
How To Install .Deb Files When Getting "The package is of bad quality" Error In Ubuntu Software Center[/URL]

---

### Post by OtagoHarbour on 2012-05-05
> **ubuntu27 said:**
> I recommend to use gdebi to install Deb packages manually.

```
sudo apt-get instal gdebi
```[URL="http://www.webupd8.org/2011/04/how-to-install-deb-files-when-getting.html"]
How To Install .Deb Files When Getting "The package is of bad quality" Error In Ubuntu Software Center[/URL]

Thanks for the info.  It works.

---

