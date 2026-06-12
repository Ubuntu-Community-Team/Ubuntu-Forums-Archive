---
title: "ifconfig deprecated?"
date: 2018-12-02
forum: Security
---

### Post by cam17 on 2018-12-02
Somewhere on this forum I received a response that ifconfig was deprecated and the command was missing from 18.04 but now the command exists. Can anyone explain as I noticed several entires on security issues I beleive this could be an operating system corruption.

---

### Post by The Cog on 2018-12-02
I think this says it all. 
[https://askubuntu.com/questions/1031640/ifconfig-missing-after-ubuntu-18-04-install](https://askubuntu.com/questions/1031640/ifconfig-missing-after-ubuntu-18-04-install)
If the command exists then I guess you have installed net-tools at some stage.
I don't think I would regard the existence of ifconfig as evidence of system corruption though.

---

### Post by ajgreeny on 2018-12-02
ifconfig is still in the full install (of Xubuntu at least) and perhaps is missing only if you choose minimal install.

---

### Post by corradoventu on 2018-12-18
I don't see ifconfig in my Ubuntu Disco standard install with third-party software ```
corrado@corrado-p13-dd-1107-x:~$ apt policy ifconfig
N: Unable to locate package ifconfig
corrado@corrado-p13-dd-1107-x:~$ inxi -SC
System:
  Host: corrado-p13-dd-1107-x Kernel: 4.20.0-042000rc7-generic x86_64 
  bits: 64 Desktop: Gnome 3.30.1 Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:
  Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  L2 cache: 3072 KiB 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
corrado@corrado-p13-dd-1107-x:~$ 
```

---

### Post by ajgreeny on 2018-12-18
Don't forget **Disco Dingo** has another four months to go before it's released so presence or absence of packages at this point inn development really means nothing.

---

### Post by HermanAB on 2018-12-23
Ifconfig works perfectly fine and is maintained and improved on the BSDs.  It seems to suffer from 'Not Invented Here' syndrome on Linux.

---

