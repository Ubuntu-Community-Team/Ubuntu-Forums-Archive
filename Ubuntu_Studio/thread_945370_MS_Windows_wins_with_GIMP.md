---
title: "MS Windows wins with GIMP"
date: 2008-10-12
forum: Ubuntu Studio
---

### Post by beerem on 2008-10-12
[www.gimp.org](www.gimp.org) says simply use apt-get install gimp, well this installs the latest stable version 2.4.5.

GIMP 2.6.1 is out and MS Windows has a 2.6 download which reveals GIMP as a really cool package with many improvements. 

Shame about UBUNTU, trying to compile the source involves you in so many extra packages which have to be downloaded and compiled, then you find that there are obscure errors in some of the dependent packages. Sigh!!

Guess that I must stick with MS Windows if I want to use this Linux package.

Has anyone out there managed to install a binary version in UBUNTU of the latest GIMP?

---

### Post by Idefix82 on 2008-10-12
Have you tried specifying the version by hand?

```
sudo apt-get install gimp=2.6
```
or alternatively
```
sudo apt-get install gimp/testing
```

---

### Post by lukjad on 2008-10-12
[http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

I think this is what you are looking for. It has the .deb files needed to install GIMP. I installed from this and it works well.

If you are using the 32 bit Ubuntu:
[http://www.getdeb.net/release/3257](http://www.getdeb.net/release/3257)

If you are using the 64 bit Ubuntu:
[http://www.getdeb.net/release/3258](http://www.getdeb.net/release/3258)

---

### Post by hyper_ch on 2008-10-12
> **beerem said:**
> Guess that I must stick with MS Windows if I want to use this Linux package.

When only that minor version change is the main reason for you to stick with windows... well, then you should do it.

---

### Post by Stochastic on 2008-10-13
> **hyper_ch said:**
> When only that minor version change is the main reason for you to stick with windows... well, then you should do it.

Agreed.



GIMP 2.6 was released on Oct.1st '08, Hardy's repos were frozen in April '08 (maybe even march).  When you upgrade to Intrepid at the end of this month, GIMP will be 2.6.1 by default.  Constantly updating the repos is not a healthy development model as it makes bug fixing nearly impossible to track, and creates unwanted instability.

MS Windows has no package downloadable for GIMP anywhere.  Jernej Simon&#269;i&#269; has created an auto-installer for 2.6 for windows and you should thank him for his hard work on that, not rag on the entire ubuntu community for being slower to release their auto-installer.  Go back to MS Windows if this is how you want to act around here.

---

### Post by beerem on 2008-10-13
> **lukjad007 said:**
> [http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

I think this is what you are looking for. It has the .deb files needed to install GIMP. I installed from this and it works well.

If you are using the 32 bit Ubuntu:
[http://www.getdeb.net/release/3257](http://www.getdeb.net/release/3257)


Thanks for the link, I downloaded the .deb files and managed to install the GIMP 2.6.1 which works fine. My faith in Ubuntu is re-established. I shall look forward to the next release where it is standard.

(Looking forward to the day when I can ditch MS Windows entirely):popcorn:

---

### Post by lukjad on 2008-10-13
Great! See you around.

---

