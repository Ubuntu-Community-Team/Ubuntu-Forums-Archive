---
title: "getting undefined reference to errors"
date: 2012-06-18
forum: Server Platforms
---

### Post by said76 on 2012-06-18
Hi,

I am getting undefined reference errors when trying to install postfix-2.9.3 from Source Code on my Ubuntu Server 12.04 LTS.

The errors are as follows
dict_nis.c: error: undefined reference to yp_match
dict_nic.c: error: undefined reference to yp_get_default_domain
collect2: ld returned 1 exit status

I wonder if anyone might have encountered the similar issues before and would be kind to share some info with me.

Thank you in advance

---

### Post by SeijiSensei on 2012-06-19
Did you run 

```
sudo apt-get build-dep postfix
```

before compiling?  Those yp_ files have to do with something called "NIS," or the "yellow pages" service, which is a method of authenticating users over a network.  You apparently don't have the NIS header files installed that the source code expects.

Unless you use NIS, which is doubtful, you could  probably disable it in postfix by modifying the list of switches sent to /configure. I'd try the build-dep approach above first, though.  That command tells APT to download all source-code dependencies that were used to compile the Ubuntu version of postfix.  That list of dependencies probably includes the needed NIS headers.  If you still get errors after running build-dep, you'll need to modify how you run ./configure to avoid any missing source dependencies.  Usually "./configure --help" will display the list of configuration options.

---

