---
title: "Is Dazuko included in Hardy?"
date: 2008-05-10
forum: Security
---

### Post by Robbyx on 2008-05-10
I am in the process of installing AVG's Anti virus. Can I presume that the dazuko kernel module is included in the standard Hardy H. It is needed for the on access scanner.

---

### Post by brian_p on 2008-05-10
> **Robbyx said:**
> I am in the process of installing AVG's Anti virus. Can I presume that the dazuko kernel module is included in the standard Hardy H. It is needed for the on access scanner.

```
locate dazuko
```

```
apt-cache search dazuko
```

and then the FAQ at [www.dazuko.org](www.dazuko.org)

---

### Post by Vadi on 2008-05-10
You can always use packages.ubuntu.com to search, but here's what I get:

> vadi@ubuntu-laptop:~$ apt-cache search dazuko
klamav - KDE frontend for ClamAV
vadi@ubuntu-laptop:~$

---

### Post by gilbert27 on 2008-05-13
Hi !!

Dazuko is not included in Hardy!!
check here !! 
[http://packages.ubuntu.com/search?keywords=dazuko&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=dazuko&searchon=names&suite=all&section=all)

Hardy is using kernel 2.6.24 and dazuko don't compile fine under kernel 2.6.24, 2.6.25! 

see more about this here :: Dazuko site::
[http://lists.gnu.org/archive/html/dazuko-help/](http://lists.gnu.org/archive/html/dazuko-help/)

---

### Post by Robbyx on 2008-05-13
> **gilbert27 said:**
> Hi !!

Dazuko is not included in Hardy!!
check here !! 
[http://packages.ubuntu.com/search?keywords=dazuko&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=dazuko&searchon=names&suite=all&section=all)

Hardy is using kernel 2.6.24 and dazuko don't compile fine under kernel 2.6.24, 2.6.25! 

see more about this here :: Dazuko site::
[http://lists.gnu.org/archive/html/dazuko-help/](http://lists.gnu.org/archive/html/dazuko-help/)

When I ran the test set out by Vadi ie

> vadi@ubuntu-laptop:~$ apt-cache search dazuko
klamav - KDE frontend for ClamAV
vadi@ubuntu-laptop:~$ 

I also had the same response. I assumed that if a search for dazuko produces some response it must be connected with finding dazuko. In the circumstances what does the following mean?

> klamav - KDE frontend for ClamAV

Robin

---

### Post by brian_p on 2008-05-13
> **Robbyx said:**
>  I assumed that if a search for dazuko produces some response it must be connected with finding dazuko. In the circumstances what does the following mean?

klamav - KDE frontend for ClamAV

Robin

```
man apt-cache
```

What does 'search' do? Then

```
apt-cache show klamav
```

---

### Post by jim-meech on 2008-06-10
I have made a suggestion on brain storm that a pre compiled dazuko module & compatible kernel are included in the repos.
Please vote for it if would help you.

[http://brainstorm.ubuntu.com/idea/9687/]("http://brainstorm.ubuntu.com/idea/9687/")

---

### Post by Eleceirvando on 2008-06-11
No, Dazuko is not included in Hardy... But you can easly install.
Follow the steps on [http://www.archivum.info/dazuko-help@nongnu.org/2008-06/msg00004.html](http://www.archivum.info/dazuko-help@nongnu.org/2008-06/msg00004.html) and be aware about the problem with shutdown.

Hope I've helped.

---

