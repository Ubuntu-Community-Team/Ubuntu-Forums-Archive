---
title: "php5 with gd library support"
date: 2010-06-07
forum: Server Platforms
---

### Post by nusidie on 2010-06-07
Hello everybody,

This is my first post here but i'll try to make it clear what i need help with.

first of all,

i have an ubuntu 10.04 server with apache2 php5 mysql etc

i need gd library support

so i downloaded it configured it,

it gave me an error (2005)

i went to [http://www.libgd.org/FAQ_PHP](http://www.libgd.org/FAQ_PHP)

needed to do a command in the binaries of php5

wich should be in /usr/bin/php5

but it doesn't exist

googled some more found a thread wich said why php5 directory didden't exist.

and i needed to run the following command:

**sudo apt-get install php5 php5-cli php5-cgi php5-dev**

did that now all scripts that use gd library have a white screen

can anybody help me configuring php and gd library?

Thanks in advance! Nusidie

---

### Post by Bachstelze on 2010-06-07
```
sudo apt-get install php5-gd
```

:)

---

### Post by nusidie on 2010-06-07
Thanks for youre reaction,

but it says that this pack is installed already,

i'm trying to use jgraph

[http://jpgraph.net](http://jpgraph.net)

do i need anything else to fix this problem?

Thanks id advance, nusidie

---

### Post by Bachstelze on 2010-06-07
> **nusidie said:**
> Thanks for youre reaction,

but it says that this pack is installed already,

i'm trying to use jgraph

[http://jpgraph.net](http://jpgraph.net)

do i need anything else to fix this problem?

Thanks id advance, nusidie

The software is distributed in a .tar.gz archive, there's probably a readme file of sorts in there that tells you how to install it. -

---

### Post by nusidie on 2010-06-07
Well my phpinfo says:

**ps**

  PS Support enabled  PSlib Version 0.4.3  Revision $Revision: 1.37 $  GD Support enabled 
So gd library is enabled and its the script were I'm going wrong?

I'll try to find out what i did wrong with the script itselves thanks alot!

Greetz, Nusidie

---

