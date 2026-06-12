---
title: "Ubuntu 19.04: Removal of python-vte causes remastersys based tools to fail to install"
date: 2019-02-22
forum: Ubuntu Development Version
---

### Post by bbogert24 on 2019-02-22
Folks,

       With the removal of python-vte from VTE in Ubuntu 19.04 all remastersys clone build tools will
       fail to install due to dependency on python-vte.

       Does anyone know where one would now get the python VTE functionality ?

       Any help would be appreciated.

       P.S. I emailed the Ubuntu VTE owner and hopefully he will be kind enough to enlighten me on
             what direction I need to take. I will provide any info that I get from him here so that all
             may be informed.

Thanks,
Brett "WolfMan" Bogert

---

### Post by jbicha on 2019-02-22
The only reason the old vte source package is in Debian and Ubuntu is for the debian-installer which hasn't switched to gtk3 yet.

remastersys appears to have abandoned several years ago. There is something called LinuxRespin but I've never used it.

Instead of using gtk2 and python-vte, apps should switch to using GObject Introspection and gtk3 using the gir1.2-vte-2.91 package provided by the vte2.91 source package.

---

### Post by bbogert24 on 2019-02-22
Thanks that's what I was looking for and expected.

For you information although remastersys is dead it's clones are not.

For example there is CustomLinux Creator(Sourceforge.net) as well
as PinguyBuilder(Sourceforge.net) and my clone WolfLandBuilder.

Is there any developer information available on how to use gir VTE or
do I need to glean what I need from the gir source code ?

Should I be also thinking about converting to python3 while I am at it ?
(e.g. I have have to do a substantial rewrite may as well do python3
while I am at it).

Thanks again for the info,
Brett "WolfMan" Bogert

---

### Post by jbicha on 2019-02-22
Yes, python3 is good but you can do that as a separate step after you get the gtk3 version working.

[https://pygobject.readthedocs.io/](https://pygobject.readthedocs.io/)
[https://lazka.github.io/pgi-docs/](https://lazka.github.io/pgi-docs/)
[https://pygobject.readthedocs.io/en/latest/guide/porting.html](https://pygobject.readthedocs.io/en/latest/guide/porting.html)

---

### Post by bbogert24 on 2019-02-23
Thanks for the info.. I have book marked them all. 

I was able to find a couple of actual VTE examples for Python3 and git1.2-vte-291
so I at least have an idea of what to do with python3.

How all I have to do is get python2 working with gtk-vte.

Thanks again,
Brett "WolfMan" Bogert

---

