---
title: "SSH through PHP"
date: 2010-11-02
forum: Server Platforms
---

### Post by Strega on 2010-11-02
Hello,

I'm trying to run ssh commands though PHP on my website. I found this tutorial for it: [http://kevin.vanzonneveld.net/techblog/article/make_ssh_connections_with_php/](http://kevin.vanzonneveld.net/techblog/article/make_ssh_connections_with_php/)
I've got a few problems here, when I do "apt-get install openssl-dev" I get this output:```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package openssl-dev
```
So I skipped this step and tried to do the next ones, but the "pecl install -f ssh2" command failed as well. Perhaps because of the previous failure. This was the output:```
WARNING: failed to download pecl.php.net/ssh2 within preferred state "stable", will instead download version 0.11.0, stability "beta"
downloading ssh2-0.11.0.tgz ...
Starting to download ssh2-0.11.0.tgz (22,884 bytes)
........done: 22,884 bytes
5 source files, building
running: phpize
sh: phpize: not found
ERROR: `phpize' failed
```
Do you have a solution for this problem(s)?

Regards,
Strega

---

### Post by BobVila on 2010-11-02
I'm guessing that the tutorial is old. It's likely been replaced with libssl-dev

---

### Post by Strega on 2010-11-02
> **BobVila said:**
> I'm guessing that the tutorial is old. It's likely been replaced with libssl-dev
I was able to install the libssl-dev, but still the "pecl install -f ssh2" doesn't work.
Do you know how to solve this :p ?

---

### Post by BobVila on 2010-11-02
try sudo apt-get install php5-dev and then give it another go

---

### Post by Ryan Dwyer on 2010-11-02
I would ignore everything so far and try installing libssh2-php from the repo.

---

### Post by Strega on 2010-11-02
> **Ryan Dwyer said:**
> I would ignore everything so far and try installing libssh2-php from the repo.That's a little too late :p I now ran the command "pecl install -f ssh2". It's prompting me with the question "libssh2 prefix? [/usr]". What do I do now?

---

### Post by Strega on 2010-11-02
> **Ryan Dwyer said:**
> I would ignore everything so far and try installing libssh2-php from the repo.I checked the installation of libssh2-php, and it is already installed on my system.

---

### Post by waustin on 2010-11-07
[phpseclib, a pure PHP SSH implementation](http://phpseclib.sourceforge.net/) is generally considered easier to use than libssh2-php.

I mean, even if you do manage to get libssh2-php installed, you'll still run into issues like ssh2_exec() returning prematurely, as described here:

[http://www.frostjedi.com/phpbb/viewtopic.php?f=46&t=13223](http://www.frostjedi.com/phpbb/viewtopic.php?f=46&t=13223)
[https://bugs.launchpad.net/ubuntu/+source/php-ssh2/+bug/501959](https://bugs.launchpad.net/ubuntu/+source/php-ssh2/+bug/501959)

libssh2-php is also no longer actively maintained and, in fact, doesn't even work on PHP 5.3, unless you modify the source code:

[http://core.trac.wordpress.org/ticket/10348#comment:10](http://core.trac.wordpress.org/ticket/10348#comment:10)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569119](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569119)
[http://pecl.php.net/bugs/bug.php?id=16727](http://pecl.php.net/bugs/bug.php?id=16727)


On top of that the phpseclib is just plain faster:


[http://kevin.vanzonneveld.net/techblog/article/make_ssh_connections_with_php/#comment_3759](http://kevin.vanzonneveld.net/techblog/article/make_ssh_connections_with_php/#comment_3759)

---

