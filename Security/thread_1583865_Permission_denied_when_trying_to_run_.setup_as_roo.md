---
title: "Permission denied when trying to run ./setup as root"
date: 2010-09-28
forum: Security
---

### Post by rafaeluprm on 2010-09-28
Hello,

I am trying to install COMSOL 4a in Ubuntu 10.04 and when I try to run ./setup and I am already connected as root the command line gives me a permission denied error...

Thanks for the help!

---

### Post by lukeiamyourfather on 2010-09-28
Is the script executable? If not, then you'll need to make it executable.

```
chmod u+x filename
```

---

### Post by rafaeluprm on 2010-09-28
Thanks it worked! But now I get the following error when I run ./setup 

./setup: 497 /home/...../COMSOL4a/bin/glnx86/setuplauncher: Permission denied

I tried locating the setuplauncher and changing the permissions as with the setup but it did not work.

Thanks again!

---

### Post by lukeiamyourfather on 2010-09-28
A quick search revealed this.

[http://www.comsol.com/support/knowledgebase/1086/](http://www.comsol.com/support/knowledgebase/1086/)

If you don't find anything there I'd suggest getting in touch with their technical support.

---

### Post by uPEMFC on 2011-09-01
> **rafaeluprm said:**
> Hello,

I am trying to install COMSOL 4a in Ubuntu 10.04 and when I try to run ./setup and I am already connected as root the command line gives me a permission denied error...

Thanks for the help!


Hello 
Try to lunch the setup from the root (it's work for me)

sudo -i

(*path to the setup file*) sh setup

---

### Post by uPEMFC on 2011-09-01
Hi,

I have a problem, when I install Comsol 35a on Ubuntu 64 bit. everthing was fine 

when I run comsol I have the error message 

comsol: 2345: /COMSOL35/java/glnxa64/jre/bin/java: Permission denied

I try to change permission , but all the file remain with the same attributes
any idea to help

---

### Post by debd on 2011-09-02
> I try to change permission , but all the file remain with the same attributes

Are the files on an ntfs partition? if so, try moving them onto a ext partiton and then set the permissions.

---

