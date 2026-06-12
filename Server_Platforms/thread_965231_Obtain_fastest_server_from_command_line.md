---
title: "Obtain fastest server from command line"
date: 2008-10-31
forum: Server Platforms
---

### Post by leandromartinez98 on 2008-10-31
I'm trying to upgrade my Ubuntu Server, and I would like to get the files from the fastest ubuntu mirror for me. This is trivial if one has the graphical interface, of course. Is there any way to do it from the command line? I've checked the apt-spy or netselect packages, but these seem to work only for Debian repositories. Is there an alternative for Ubuntu Server? (ps. Using hardy).

---

### Post by dantrevino on 2008-12-09
I think thats mainly an experience thing.  AFAIK, netselect will show you the lowest latency, but not the fastest connection.  For instance, sitting in florida, most times the gui will show me the 'fastest' mirror being the NZ mirror, when I clearly have big pipe universities nearby.

---

### Post by koenn on 2008-12-09
> **leandromartinez98 said:**
> I'm trying to upgrade my Ubuntu Server, and I would like to get the files from the fastest ubuntu mirror for me. This is trivial if one has the graphical interface, of course. Is there any way to do it from the command line? I've checked the apt-spy or netselect packages, but these seem to work only for Debian repositories. Is there an alternative for Ubuntu Server? (ps. Using hardy).

netselect should work :

```

kn@knix:~$ sudo netselect -vv ftp.belnet.be archive.ubuntu.com.ba archive.ubuntu.com
Running netselect to choose 1 out of 6 addresses.       
...................................................................
ftp.belnet.be                           16 ms   9 hops   90% ok ( 9/10) [   34]
archive.ubuntu.com.ba                   56 ms  19 hops   85% ok ( 6/ 7) [  188]
91.189.88.31                            24 ms  12 hops   90% ok ( 9/10) [   57]
91.189.88.46                            22 ms  12 hops   90% ok ( 9/10) [   55]
91.189.88.45                            23 ms  12 hops   90% ok ( 9/10) [   55]
91.189.88.40                            25 ms  12 hops   90% ok ( 9/10) [   61]
   34 ftp.belnet.be
kn@knix:~$ 


```
man netselect for an explanation how netselect decides what is "faster"

---

