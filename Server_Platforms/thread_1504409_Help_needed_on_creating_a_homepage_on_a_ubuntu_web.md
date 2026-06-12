---
title: "Help needed on creating a homepage on a ubuntu web sever!"
date: 2010-06-08
forum: Server Platforms
---

### Post by gongbaifei on 2010-06-08
Hi guys,

I am trying to create a homepage on my lab server which is running ubuntu 10.04.
I though I just need to create an index.html in Public directory under my account to enable the link [http://xxx.yyy.edu/~zzz](http://xxx.yyy.edu/~zzz). It turns out this doesn't work at all.
Is my idea wrong or I still need more steps to make my homepage work?

Thank you very much!

Josh

---

### Post by Ryan Dwyer on 2010-06-08
You need to enable the userdir module for Apache to be able to do that.

sudo a2enmod userdir
sudo /etc/init.d/apache2 restart

---

### Post by HeirPixel on 2010-06-08
You may also need to check permissions. Manually creating an index.html file may end up with funny rights, so run **ls -l** and make sure you don't end up with anything like **-rwx------**

---

### Post by gongbaifei on 2010-06-08
Thank you very much guys, I'll try that.

---

