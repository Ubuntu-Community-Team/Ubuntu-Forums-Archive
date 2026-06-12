---
title: "Installtion of PHP 4.4.7"
date: 2007-10-01
forum: Server Platforms
---

### Post by s.s.swapnil on 2007-10-01
Hi,

I'm trying to install PHP 4.4.7 (very specific to the versioin) on my ubuntu 6.0.6 server. Because of the some reasons I do not want to use PHP 5. I've already installed Apatche & MySQL successfully & are in running state. I'm not been able to install & configure PHP on the same box. I tried following command  
[COLOR="Magenta"]# ./configure --with-mysql --with-apache=../apache_2.0.0[/COLOR]

I got the following output & installation aborted 

loading cache ./config.cache
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.


Please help. I'm new to Ubuntu.

Thanks in advance for any sincere efforts :)

---

### Post by conjur3r on 2007-10-01
Looks like a permission problem.  Try prefixing it with sudo.

---

### Post by az on 2007-10-01
> **s.s.swapnil said:**
> 
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.


sudo apt-get install build-essential

You do not have a compiler installed be default.

---

