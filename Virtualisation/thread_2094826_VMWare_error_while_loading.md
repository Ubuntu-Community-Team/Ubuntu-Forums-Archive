---
title: "VMWare error while loading"
date: 2012-12-14
forum: Virtualisation
---

### Post by johnnyw on 2012-12-14
I tried to make use full use of my 4 gigs of Ram and installed something called PAE if my memory serves me right. Now I have this as a result.
Thanks in advance

[IMG]http://i.imgur.com/RjXsJ.png[/IMG]
[IMG]http://i.imgur.com/DRY6n.png[/IMG]


Linux johnnyw-laptop 3.2.0-34-generic #53-Ubuntu SMP Thu Nov 15 10:49:02 UTC 2012 i686 i686 i386 GNU/Linux

Prior to upgrading to 12.04 ( from 10.04 ) I had some headers issues

---

### Post by dcstar on 2012-12-17
> **johnnyw said:**
> I tried to make use full use of my 4 gigs of Ram and installed something called PAE if my memory serves me right. Now I have this as a result.

Download the current version of VMware Player/Workstation and install that.

If you want to use all of your RAM install 64-bit Ubuntu and VMware.

---

### Post by johnnyw on 2012-12-17
Thanks for your prompt reply!
Ain't there another choice to avoid formatting?

---

### Post by Cheesemill on 2012-12-17
You're probably just missing the headers for the new kernel you installed. Try running:
```
sudo apt-get install linux-headers-`uname -r`
```
to install them and then VMWare should be able to build it's modules.

---

### Post by johnnyw on 2012-12-17
sudo apt-get install linux-headers- 'uname-r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'linux-headers' can't be removed
E: Unable to locate package uname-r

I'd been told I'm missing a .h by a colleague also

---

### Post by Cheesemill on 2012-12-17
You've made some typos.

```
sudo apt-get install linux-headers-`uname -r`
```

The only space is between uname and -r.
Also they are backticks ` not apostrophes ' (above the TAB key on a UK keyboard).

Try just copy and pasting the command.

---

### Post by johnnyw on 2012-12-17
Thanks guys. It says it will take > 2hours  ( 224 B/s)

I'm using my phone :P

---

### Post by Cheesemill on 2012-12-17
Ouch :)

---

