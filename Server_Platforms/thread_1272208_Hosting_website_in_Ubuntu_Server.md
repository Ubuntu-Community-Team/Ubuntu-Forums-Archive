---
title: "Hosting website in Ubuntu Server"
date: 2009-09-21
forum: Server Platforms
---

### Post by MC707 on 2009-09-21
I was wondering... is it possible to setup a website in a Ubuntu server box? I know you can use the [HFS ~ Http File Server]("http://www.rejetto.com/hfs/") with WINE on a Ubuntu machine that has a GUI. However, I have no idea how that could be a possibility in a server installation. Any help is appreciated (tutorial, link to tutorial, etc). Thanks in advance.

---

### Post by bear24rw on 2009-09-21
for webserver install apache search forums or google for ubuntu apache tutorial

---

### Post by stlsaint on 2009-09-21
> **MC707 said:**
> I was wondering... is it possible to setup a website in a Ubuntu server box? I know you can use the [HFS ~ Http File Server]("http://www.rejetto.com/hfs/") with WINE on a Ubuntu machine that has a GUI. However, I have no idea how that could be a possibility in a server installation. Any help is appreciated (tutorial, link to tutorial, etc). Thanks in advance.

yes you can do what it is you are asking....
see here  [UbuntServerGuide]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

---

### Post by MC707 on 2009-09-21
> **bear24rw said:**
> for webserver install apache search forums or google for ubuntu apache tutorial

hmmm would that be it? how would I set up the server itself, would the apache tutorial help too? I found [this]("http://howtoforge.com/perfect_setup_ubuntu_5.10") and [this]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") awhile back, though I really didn't think it addressed the problem, or that it was recent enough (5.10? 8.04?). Do you think these are right and/or do you know one that is more recent (jaunty, 9.04)?

---

### Post by bear24rw on 2009-09-21
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

---

### Post by stlsaint on 2009-09-21
ok...if you are setting up a server than yes you will need apache2.
sudo apt-get install apache2...ubuntu server will come with this.
then depending on what you are using the server for you will download other applications. You will need to learn about port forwarding also.

---

### Post by MC707 on 2009-09-21
> **stlsaint said:**
> yes you can do what it is you are asking....
see here  [UbuntServerGuide]("https://help.ubuntu.com/8.04/serverguide/C/index.html")
Whahaha awesome I think that's what I was looking for. For this purpose, what would I need? Apache only, or mysql and php + others? Also, for this purpose I'm guessing I will only need to check the chapter 9 - web servers, right? Thanks for pointing to that page mate!

> **stlsaint said:**
> ok...if you are setting up a server than yes you will need apache2.
sudo apt-get install apache2...ubuntu server will come with this.
then depending on what you are using the server for you will download other applications. You will need to learn about port forwarding also.

Oh I see, thanks.

---

