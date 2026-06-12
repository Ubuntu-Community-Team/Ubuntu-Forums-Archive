---
title: "I need full gd2 Support (imagerotate) - Switch to Debian Server? recompiling php?"
date: 2009-11-13
forum: Server Platforms
---

### Post by cyaneo on 2009-11-13
I need full gd2 support (imagerotate), but ubuntu does not serve a fully php5-gd version.

On dotdeb.org there is a full gd supported "dotdeb-php5-gd2" package BUT for debian lenny. Found here: [http://drupal.org/node/540838](http://drupal.org/node/540838)

Questions:
- is it safe to use the lenny package on ubuntu 8.04 LTS?
- should I switch my (new) server to debian so I can use this?

Or should I recompile php5 as used here: [http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu](http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu)

What are the cons of these different methods?

Thank you + regards!

---

### Post by JonRohan on 2009-11-14
Both methods should yeild the same result. Php with GD2. Personally I'd go for the deb package first. Maybe try it on a test vm first and see what the result is? 

Jon

---

### Post by Vegan on 2009-11-14
I use GD with my forum for the CAPTCHA to keep those spesky spammers at bay. Works fine for me.

Is there a particular feature of GD you need?

---

### Post by cyaneo on 2009-11-15
> **Vegan said:**
> I use GD with my forum for the CAPTCHA to keep those spesky spammers at bay. Works fine for me.

Is there a particular feature of GD you need?

The basic GD functions (such as rouded corners etc.) also works fine for my needs.

But I need GD Image Filtering and GD Image Rotation a lot, but both are not supported with ubuntu php5-gd (why?).

---

### Post by Smartin on 2010-02-12
> **cyaneo said:**
> I need full gd2 support (imagerotate), but ubuntu does not serve a fully php5-gd version.

On dotdeb.org there is a full gd supported "dotdeb-php5-gd2" package BUT for debian lenny. Found here: [http://drupal.org/node/540838](http://drupal.org/node/540838)

Questions:
- is it safe to use the lenny package on ubuntu 8.04 LTS?
- should I switch my (new) server to debian so I can use this?

Or should I recompile php5 as used here: [http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu](http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu)

What are the cons of these different methods?

Thank you + regards!

cyaneo,

I'm now in the same spot you were a few months ago :-)

How did it go?
What did you decide to do?
Any side-effects, especially with updating your system? I have read that doing subsequent updates will make Ubuntu want to do weird things. Is this the case?

Thanks :-)

S

---

