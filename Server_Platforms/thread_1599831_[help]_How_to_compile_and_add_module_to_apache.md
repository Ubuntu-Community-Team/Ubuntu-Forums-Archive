---
title: "[help] How to compile and add module to apache?"
date: 2010-10-18
forum: Server Platforms
---

### Post by MMAMail on 2010-10-18
What are the steps to adding a new module to apache 2.2 when not using the package manager? i.e. building from source.

Any links to tutorials/blogs would be greatly appreciated.

---

### Post by James78 on 2010-10-18
Well, it's hard to give you specialized steps if I don't know what you're trying to compile and add to Apache. But generally...
```
./configure
make
sudo make install
sudo a2enmod module_name
sudo service apache2 restart
```

---

### Post by MMAMail on 2010-10-19
I am trying to add the mod_proxy and any other module needed to integrate apache with tomcat.

Do modules come with the apache source or do I have to download them separately?

---

### Post by James78 on 2010-10-19
Apache comes with a set of default modules, mod_proxy being one of them. If it's not already enabled, you could just do something like "sudo a2enmod mod_proxy"

Remember: An incorrectly setup proxy using mod_proxy will leave your server vulnerable to attacks from the web. Make sure it's secure.

As for ones that don't come packaged with Apache, just do a Google search for the module, which will bring you to the homepage of whoever's developing it, download the source, read the INSTALL if they have one, or some other instructions, which will generally conform completely or close to the steps I gave you earlier. Or, you could just try to find an already built binary version; check the repositories for that, it's generally a good idea to check for that first, plus it's easier anyways.

---

### Post by MMAMail on 2010-10-19
thanks

---

