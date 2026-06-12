---
title: "Mixing both Hardy and Lucid repositories"
date: 2011-01-24
forum: Server Platforms
---

### Post by mellowcat on 2011-01-24
Hi All,

I'm a fairly new Ubuntu user but am very comfortable with Linux administration.

I have Ubuntu Server 8.04 (LTS) installed and running well, but there a few packages that I'd like to upgrade, without upgrading the entire system (e.g, apache2). Is it possible to include both the Hardy (8.04) and Lucid (10.04) distributions in sources.list? Is that even safe? By the same token, can I  add a Maverick repo to my list? I'm using "apache2" as an example, but this is more of a general question.

How should situations like this usually be handled, when only a select few packages would profit from an upgrade that resides in a different Ubuntu release?

On a similar note, is it possible to install two different versions of the same package using the APT tools? Let's say I want two different versions of php5 -- how would I go about doing that?

I'd appreciate any feedback (including books or online resources), success / failure stories, etc. Thanks!

---

### Post by cmileto on 2011-02-06
If it were me I would download a source tarball of the program you want and then compile it and set it up yourself if its the only thing you really need upgraded.

---

### Post by Thirtysixway on 2011-02-06
Simple answer is: you can't mix repos.

While some packages may install just fine, others that depend on newer versions of libraries may not work at all. You would most likely have to compile yourself. 

Check out [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
for some info, since I think that's what you're looking for. Not every package has been backported, but some have.

---

