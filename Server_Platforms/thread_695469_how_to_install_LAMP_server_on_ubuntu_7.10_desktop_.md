---
title: "how to install LAMP server on ubuntu 7.10 desktop edition"
date: 2008-02-13
forum: Server Platforms
---

### Post by deepblue_tiano on 2008-02-13
Im using ubuntu 7.10 desktop edition for almost 3 days..i want to install a LAMP sever(apache, mysql, and php)which  Ive already downloaded, but i dont know how to install it offline coz i dont have internet connection at home..please help me step by step procedure..thanks

---

### Post by crouton on 2008-02-13
Your 7.10 desktop CD should have the necessary packages to create a 'LAMP server'.  I don't believe there is a 'fake package' that does it automatically, but I haven't checked.

'sudo apt-get install apache2 mysql5-server php5' should get you on your way.  It may complain or suggest other packages - go with whatever it recommends.

---

### Post by torgrot on 2008-02-13
Under synaptic package manager Edit-> Mark Packages by Task.  That will open a window and you can select Lamp Server.  There is a tutorial in this forum, but I haven't had much luck using it.

torgrot

---

### Post by deepblue_tiano on 2008-02-15
I dont have internet connection to do an installation..My only option is to download apache, mysql, and php in another computer w/c is connected to internet and save it to my flash disk.. But.. how can i install those things they are in tarball formats..

---

### Post by crouton on 2008-02-15
You can download .deb files and install them using 'sudo dpkg -i <file.deb>'.  [http://packages.ubuntu.com](http://packages.ubuntu.com) will let you search/download those .deb files.  Alternately, if you still have the installation CD, you can use that as a package source.

---

### Post by jmccabe on 2008-03-13
> **torgrot said:**
> Under synaptic package manager Edit-> Mark Packages by Task.  That will open a window and you can select Lamp Server.  There is a tutorial in this forum, but I haven't had much luck using it.

torgrot

When I tried the Synaptic Package Manager's "Edit" -> "Mark packages by task" feature on a fresh install of Ubuntu Desktop Edition, only "Ubuntu Desktop" and "Print Server" are listed; there is no "LAMP Server" option.

To be able to access the "LAMP Server" option in this way you need to insert an Ubuntu Server Edition CD (or capture the ISO from Microsoft Virtual PC). Once that is inserted Ubuntu recognises the CD as having distribution packages on it and offers to launch Synaptic Package Manager. If you let it run then you will now be able to see "LAMP Server" if you select "Edit" -> "Mark Packages by task".

Hope this helps any other noobs.
John

---

### Post by vpsville on 2008-03-13
Did not know you could view the server repositories so easily in the desktop edtion.  Great information.

---

### Post by wjustice on 2008-03-13
Honestly, you're better off installing a LAMP stack from [Bitnami's]("http://bitnami.org") graphical installer. It unpacks to your home dir, so there's the added bonus of not having to dick around with permissions under /var/www.

---

