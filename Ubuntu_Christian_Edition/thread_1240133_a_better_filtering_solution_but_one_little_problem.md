---
title: "a better filtering solution but one little problem"
date: 2009-08-14
forum: Ubuntu Christian Edition
---

### Post by wildman4god on 2009-08-14
Has anyone here ever heard of opendns, if not the long and short of it is you replace your normal dns server address with theirs and sign up for a free account, and one of the things it lets you do is filter your web content, the only problem is it's very easy to set your dns address back to automatic, The idea I have is to write a program that allows you to password protect the ip config dialog box and the config file so once the dns is changed to opendns we won't change the settings again to by pass it when temptation strikes, I would write it my self except I know nothing about code, so can anyone out here in ubuntu land help?

---

### Post by osinghrathore on 2009-08-14
...but I think only root/sudoers can change the Network and DNS settings,so one solution can be that you dont give sudo permission to the users you don't want to change it.

---

### Post by wildman4god on 2009-08-14
> **osinghrathore said:**
> ...but I think only root/sudoers can change the Network and DNS settings,so one solution can be that you dont give sudo permission to the users you don't want to change it.

I am not familiar with permissions and user accounts in linux, what kind of user account would I give someone so they could still do some admin task like install new software but still lockout network settings?

---

### Post by david_kt on 2009-08-14
> **wildman4god said:**
> Has anyone here ever heard of opendns, if not the long and short of it is you replace your normal dns server address with theirs and sign up for a free account, and one of the things it lets you do is filter your web content, the only problem is it's very easy to set your dns address back to automatic, The idea I have is to write a program that allows you to password protect the ip config dialog box and the config file so once the dns is changed to opendns we won't change the settings again to by pass it when temptation strikes, I would write it my self except I know nothing about code, so can anyone out here in ubuntu land help?

Change dns on your router instead of your computer.

[https://www.opendns.com/start/router/](https://www.opendns.com/start/router/)

DK

---

### Post by Aronzak on 2009-08-21
I'd also add here that the file /etc/hosts acts on top of DNS. Linux mint included a small "filter" called mintnanny that is a small frontend to add listings to /etc/hosts, that bounce unwanted domain requests to 0.0.0.0

At one point I think I tried this with the big bad blacklist, using sed to add 0.0.0.0 to the adult domains. 

See here, under (4).
[http://aronzak.wordpress.com/2009/01/27/internet-content-filtering-in-linux/](http://aronzak.wordpress.com/2009/01/27/internet-content-filtering-in-linux/)

Obviously domain based filtering is less effective than dynamic content filtering.

---

