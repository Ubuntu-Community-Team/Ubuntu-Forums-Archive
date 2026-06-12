---
title: "ubuntu vm builder"
date: 2011-06-22
forum: Virtualisation
---

### Post by bigmonmulgrew on 2011-06-22
Hi guys
I've been experimenting with ubuntu vm builder.
I cant find via google andswers to the following. I'm probably searching for the wrong thing but here goes.

Can you set the VPC image files location?
I've stumbled accross (and admitedly not gone through thoroughly) some info on how to move the image file but not how to predefine its location.

Also is there a way to easily install a LAMP server when doing this.
I'm thinking something along the lines of
addpkg LAMP

I'm sure its simple enough to do this with individual addpkg commands for everything. Not that this is strictly necessary.

---

### Post by falko on 2011-06-22
> **bigmonmulgrew said:**
> 
Can you set the VPC image files location?
I've stumbled accross (and admitedly not gone through thoroughly) some info on how to move the image file but not how to predefine its location.
Take a look at the -d switch: ```
man vmbuilder
```

---

### Post by bigmonmulgrew on 2011-06-22
so am I right in thinking all I need to do is add this to my vmbuilder scipt
--dest /virtualmachines/myvm
and it will put the new servers image file in /virtualmachines/myvm
I'll try it when I get a moment

As regards to the LAMP. I've tried adding all the packages that are included in a lamp one by one with addpkg apache2 etc
Now this works for the most part.

However some packages require input at install time.
eg mysql and phpmyadmin
Including these packages with vmbuilder skips the setup stage.

I did manage to manually run through the setups of both of these, after installing, but is there any way to do this with vmbuilder.

---

