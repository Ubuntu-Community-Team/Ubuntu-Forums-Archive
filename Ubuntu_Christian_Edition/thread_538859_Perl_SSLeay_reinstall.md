---
title: "Perl SSLeay reinstall"
date: 2007-08-30
forum: Ubuntu Christian Edition
---

### Post by dstockham on 2007-08-30
While installing SSH I misspelled a word and the perl ssleay lib didn't load and then I received the "The Perl SSLeay library is not installed. SSL not available."

How do I reinstall the perl ssleay lib?

Linux Noob.

---

### Post by dstockham on 2007-08-31
Couldn't figure it out so I just reinstalled the OS and double checked my spelling before hitting Enter.

---

### Post by tr333 on 2007-09-02
I'm not sure which SSLeay package you're referring to; CPAN lists Crypt::SSLeay and Net::SSLeay.

For future reference, you can use either of the following commands to install SSLeay on ubuntu.

```
cpan -i Net::SSLeay
cpan -i Crypt::SSLeay
```

```
sudo apt-get install libnet-ssleay-perl
sudo apt-get install libcrypt-ssleay-perl
```

Read "man cpan" or check [http://www.cpan.org/](http://www.cpan.org/) for more details.

---

### Post by JarodLee on 2009-05-11
thanks....I am trying....

---

