---
title: "more problems with tor"
date: 2009-10-22
forum: Security
---

### Post by jinwald12 on 2009-10-22
i tried compiling tor from source, that didn't work so then some people on this forum suggested using a source package. That let it run but it cant connect to the tor network and that the torrec file wasn't there what did i do wrong? I'm running jaunty if that makes a difference.

---

### Post by cdenley on 2009-10-22
Why compile from source?
[https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)

---

### Post by jinwald12 on 2009-10-22
> **jinwald12 said:**
> i tried compiling tor from source, that didn't work so then some people on this forum suggested using a source package****. That let it run but it cant connect to the tor network and that the torrec file wasn't there what did i do wrong? I'm running jaunty if that makes a difference.

i then tried following the tor web site's instructions but it won't create a torrec file

---

### Post by cdenley on 2009-10-22
> **jinwald12 said:**
> i then tried following the tor web site's instructions but it won't create a torrec file

You mean "torrc"?
```

cdenley@ubuntu:~$ dpkg-query -S torrc
tor: /usr/share/man/man5/torrc.5.gz
tor: /etc/tor/torrc

```

---

### Post by jinwald12 on 2009-10-22
i tried that it still can't find it it says it was extracted but it wont recognize  its there

---

### Post by cdenley on 2009-10-22
```

cdenley@ubuntu:~$ dpkg -l tor
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  tor                               0.2.1.19-1~jaunty+1               anonymizing overlay network for TCP
cdenley@ubuntu:~$ ls -l /etc/tor/torrc
-rw-r--r-- 1 root root 7045 2009-07-29 06:09 /etc/tor/torrc

```

What "wont recognize its there"?

---

### Post by jinwald12 on 2009-10-23
```
[CODE]NAME:~$ dpkg -l tor
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  tor            0.2.1.19-1~jau anonymizing overlay network for TCP
NAME:~$ ls -l /etc/tor/torrc
ls: cannot access /etc/tor/torrc: No such file or directory
jethro@jethro-laptop:~$ -rw-r--r-- 1 root root 7045 2009-07-29 06:09 /etc/tor/torrc
bash: -rw-r--r--: command not found

```[/CODE]

---

### Post by cdenley on 2009-10-23
You can try purging it then reinstalling it.
```

sudo dpkg -P tor
sudo apt-get install tor

```
If files from packages you're installing end up disappearing, then you have bigger problems than getting tor to work.

---

