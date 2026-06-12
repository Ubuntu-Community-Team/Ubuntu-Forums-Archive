---
title: "clarification"
date: 2009-05-20
forum: Server Platforms
---

### Post by salim.madni on 2009-05-20
hello

can someone advise how to check if so and so package are installed or not. further to this, advise how to install if not there

    *  Linux OS, kernel 2.6
    * glibc version 2.3 or later
    * libstdc++ version 3.4 or later
regards
salim

---

### Post by 73ckn797 on 2009-05-20
> **salim.madni said:**
> hello

can someone advise how to check if so and so package are installed or not. further to this, advise how to install if not there

    *  Linux OS, kernel 2.6
    * glibc version 2.3 or later
    * libstdc++ version 3.4 or later
regards
salim

In Synaptic you should be able to list only installed packages using the status option at the lower left side of the window. Alternately you can enter the file name(s) in the search window and it will list all/the match(es).

---

### Post by salim.madni on 2009-05-20
dear sir

it is ubuntu server there is no gui, guide on bash,command line how to check the packages

i hope you get what i ask for

regards

---

### Post by ephmanjmm on 2009-05-20
uname -r will give you the kernel release

sudo updatedb 
then
locate libstdc++

might help

---

### Post by cdenley on 2009-05-20
```

man dpkg
man apt-get
man apt-cache

```
In ubuntu, and basically every Linux distro, you use the version of software that has been released and supported for the version of the distro you are using. There are a few exceptions (libstdc++ is one) where multiple versions are available in the repo as different packages. I think the packages provided in the repo for all recent releases would satisfy your requirements, though. They should be installed with this command, if they aren't already:
```

sudo apt-get install build-essential

```

---

### Post by volkswagner on 2009-05-20
You should get information in the man page.

```
apt man
```

Look for apt-cache.

You can try:
```
sudo apt-cache -i package-you-are-looking-for
```

---

### Post by 73ckn797 on 2009-05-20
> **salim.madni said:**
> dear sir

it is ubuntu server there is no gui, guide on bash,command line how to check the packages

i hope you get what i ask for

regards

Nevermind!

---

