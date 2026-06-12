---
title: "About installing XAMPP"
date: 2015-04-21
forum: Server Platforms
---

### Post by satimis on 2015-04-21
Hi all,

Can I download the ISO of the server edition on;

Download Ubuntu Server
[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

and during its installation I can select the components of XAMPP?  If YES, please advise which items I have to select apart from LAMP ?

OR
I have to install Ubuntu server first.  Then down XAMPP on;
[https://www.apachefriends.org/index.html](https://www.apachefriends.org/index.html)

and install it on Ubuntu Server later?

Please advise.  Pointer would be appreciated.  Thanks

Regards
satimis

---

### Post by nerdtron on 2015-04-22
During the installation of Ubuntu server, there is a section where taskel will run and ask you choose package groups to install, like: OpenSSH Server, Email Server, DNS, etc. I don't choose any of those except of course Openssh server. All others are not checked. It's way better to install the packages you need after the installation where you can choose each and every package you really want to install.

---

### Post by satimis on 2015-04-22
> **nerdtron said:**
> During the installation of Ubuntu server, there is a section where taskel will run and ask you choose package groups to install, like: OpenSSH Server, Email Server, DNS, etc. I don't choose any of those except of course Openssh server. All others are not checked. It's way better to install the packages you need after the installation where you can choose each and every package you really want to install.
Hi,

During installing Ubuntu server apart from LAMP packages I have selected OpenSSH.

My aim of my original posting is to clarify whether it needs installing XAMPP in addition?

Regards
satimis

---

### Post by darkod on 2015-04-23
In XAMPP the X is for cross platform and the last P for Perl.
So, XAMP would be identical (or close) to LAMP that you already have installed. If you need Perl too you can install it now yourself.
That should be it. You don't need to install the whole XAMPP when you already have LAMP.

---

### Post by satimis on 2015-04-23
> **darkod said:**
> In XAMPP the X is for cross platform and the last P for Perl.
So, XAMP would be identical (or close) to LAMP that you already have installed. If you need Perl too you can install it now yourself.
That should be it. You don't need to install the whole XAMPP when you already have LAMP.
Hi,

Thanks for your advice.

I have LAMP server running on VM of Virtualbox.  I'm prepared installing WordPress on it.  According to following doc;
How to Clone Your Live WordPress Blog to a Local Server
[http://www.maketecheasier.com/clone-your-live-wordpress-blog-to-a-local-server/](http://www.maketecheasier.com/clone-your-live-wordpress-blog-to-a-local-server/)

it needs XAMPP.

$ apt-cache policy perl```

perl:
  Installed: 5.18.2-2ubuntu1
  Candidate: 5.18.2-2ubuntu1
  Version table:
 *** 5.18.2-2ubuntu1 0
        500 http://hk.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

Perl is already running.  Which other packages in addition are need?  Thanks

Regards
satimis

---

### Post by darkod on 2015-04-23
You have LAMP and Perl. I don't think you need anything else. Try setting up your website and see how it goes.
Also any tutorial you have to look in context. If it says xampp it means the components. If you have manually installed apache, mysql, php and perl for example, you have all components. You don't necessarily need to perform xampp installation again. Also you might need to adjust some steps depending if their procedure expects some username or password to be different from what you have. But thos are normal adjustments when following tutorials.

---

