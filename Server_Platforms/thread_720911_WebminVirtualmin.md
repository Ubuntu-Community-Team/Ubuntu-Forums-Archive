---
title: "Webmin/Virtualmin"
date: 2008-03-10
forum: Server Platforms
---

### Post by neverett on 2008-03-10
Is there a difference between Virtualmin and Webmin?  If so, what is the difference?  Thanks in advance!!!

---

### Post by e_labranche on 2008-04-03
Hi neverett,

actually, they go both hand in hand depending on your needs. Webmin is a web interface that allows you to administer your server via a web interface. So, for example, if you wanted to make changes to postfix(you mail server) config file, you would use webmin and have a nice gui in which you would make your changes. Before webmin, you had to edit the files using the shell or via a text editor.

virtualmin comes in if you want to host your own domain names. Virtualmin is a module that you install via webmin and has its own set of parametters that you can tweak. The beauty with virtualmin is that fact that once all is configured correctly on your server (mail server, apache etc), virtualmin will do all the configurations for you in one click of a button when you create new domains that you will host.

Hope this sheds some light on both of them.

---

