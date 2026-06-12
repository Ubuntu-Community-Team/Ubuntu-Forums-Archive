---
title: "unable to access web pages from Virtuaul machie"
date: 2016-01-13
forum: Virtualisation
---

### Post by Bello_Dalhatu on 2016-01-13
I have successfully installed Ubuntu server 14.04 LTS as a guest on window 10 host. Every thing works well as I can  brows the Internet from the quest machine , access the the ubuntu start page and access phpmyadmin which i installed .My problem  is that I can not access my other web pages which I copied in my home directory. I brows for help and various suggestions were given as to how to access the pages from the guest machine. These include editing the the file /etc/apache2.conf,  /etc/apche2/sites-available/ and others. I have tried some of these but there is still no positive results. Can some one assist please?.

---

### Post by SeijiSensei on 2016-01-13
By design a virtual machine cannot see the host it runs on.  You don't mention what type of virtualization software you are using.  If it is VirtualBox, make sure you have the Extension Pack installed, then use the "shared folders" option to make the directory with the web pages on the Windows side accessible to Ubuntu.  Otherwise you can enable Windows file sharing, then connect to the host from Linux using the host's virtual IP address.

---

