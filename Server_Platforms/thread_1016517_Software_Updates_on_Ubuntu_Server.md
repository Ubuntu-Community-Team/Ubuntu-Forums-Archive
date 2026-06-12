---
title: "Software Updates on Ubuntu Server"
date: 2008-12-20
forum: Server Platforms
---

### Post by spynappels on 2008-12-20
Hi guys,

   This may sound like a dumb question, but does Ubuntu Server Edition automatically download and install/apply updates? I did a search and could not seem to find a definitive answer to this one.

   It is just that the Desktop Edition asks you whether you want to install updates, but I've never had such a request from my server ed. If it does not do it automatically, what is the syntax I need to use to check for updates?

   Thanks for your help.
   Stefan

---

### Post by lykwydchykyn on 2008-12-20
It does not do it automatically, though you can configure it that way with the help of a package called cron-apt.

To install you can use apt-get or aptitude.  The syntax looks like this:
```

# To refresh the package list:
apt-get update 
# To download and install packages:
apt-get upgrade

```

You can also use aptitude instead of apt-get in those commands.  It has a little more sophisticated dependency resolver for some of those tricky situations.  It also has a menu-driven interface if you just type "aptitude".

---

### Post by spynappels on 2008-12-20
Great, thanks.

Stefan

---

