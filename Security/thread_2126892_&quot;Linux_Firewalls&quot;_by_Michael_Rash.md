---
title: "&quot;Linux Firewalls&quot; by Michael Rash"
date: 2013-03-18
forum: Security
---

### Post by Niemand000 on 2013-03-18
So, I got a hold of this book (Linux Firewalls) and I'm trying to go about installing and setting up iptables.  Before I ask the other slew of questions that I need to ask, I've noticed that this book was written for Linux Kernel 2.6, is this book out of date for me?

---

### Post by tgalati4 on 2013-03-18
It's probably 90% correct.  As you go through the examples, you will find some differences.  Make note of them, but don't panic.  After a little research, you can easily find the answers.

It's also a good idea to read some online documentation concerning iptables: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

The basics of iptables have been around a long, long time, but the configuration will differ slightly from distro to distro.

Compile the differences that you find and send them back to the author.  Who knows, you may be a co-author on the 2nd edition!

---

### Post by haqking on 2013-03-18
> **Niemand000 said:**
> So, I got a hold of this book (Linux Firewalls) and I'm trying to go about installing and setting up iptables.  Before I ask the other slew of questions that I need to ask, I've noticed that this book was written for Linux Kernel 2.6, is this book out of date for me?

It is already installed, Netfilter/IPtables is part of the Linux Kernel.

As for learning it,

```
man iptables
```

Gives you everything you need.

Peace

---

### Post by Niemand000 on 2013-03-18
> **tgalati4 said:**
> It's probably 90% correct.  As you go through the examples, you will find some differences.  Make note of them, but don't panic.  After a little research, you can easily find the answers.

It's also a good idea to read some online documentation concerning iptables: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

The basics of iptables have been around a long, long time, but the configuration will differ slightly from distro to distro.

Compile the differences that you find and send them back to the author.  Who knows, you may be a co-author on the 2nd edition!
Thanks! I'll do that, and thanks so much for the link!

---

### Post by Niemand000 on 2013-03-18
> **haqking said:**
> It is already installed, Netfilter/IPtables is part of the Linux Kernel.

As for learning it,

```
man iptables
```

Gives you everything you need.

Peace
So I don't need to worry about installing Netfilter/IPtables, but how about downloading, configuring, compiling, and installing the latest version of the kernel?

---

### Post by haqking on 2013-03-18
> **Niemand000 said:**
> So I don't need to worry about installing Netfilter/IPtables, but how about downloading, configuring, compiling, and installing the latest version of the kernel?

A new kernel is a completely different question and not related to IPTables in anyway.

To change your kernel I suggest searching to forum as that questiuon has been answered many times or wacth this for starters: [https://www.youtube.com/watch?v=traegZveTKo](https://www.youtube.com/watch?v=traegZveTKo)

Which is basd on 12.04 and 12.10, as you never said what version you were running it is an example.

YOu can read about and see the changes if any in versions of IPTables at its home page [http://www.netfilter.org/projects/iptables/](http://www.netfilter.org/projects/iptables/)

---

### Post by kevdog on 2013-03-19
Michael Rash is a very easy guy to get a hold of.  I've frequently written him regarding his fwknop program and I always get a reply usually the same day or a few days later.  If you find any errors I would suggest you write him. 

His book is good, however it's slightly advanced for the beginner.  His book focuses on security with a subfocus on snort as an intrusion detection system.  This may or may not be your thing.  If your looking for just a basic primer how to set up basic iptables to filter inbound/outbound packets, I would supplement your reading with other sources.

---

### Post by Niemand000 on 2013-03-19
> **haqking said:**
> A new kernel is a completely different question and not related to IPTables in anyway.

To change your kernel I suggest searching to forum as that questiuon has been answered many times or wacth this for starters: [https://www.youtube.com/watch?v=traegZveTKo](https://www.youtube.com/watch?v=traegZveTKo)

Which is basd on 12.04 and 12.10, as you never said what version you were running it is an example.

YOu can read about and see the changes if any in versions of IPTables at its home page [http://www.netfilter.org/projects/iptables/](http://www.netfilter.org/projects/iptables/)

While following the youtube video, he sends me here([http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/)) to download the latest kernel, but I notice there are two for 32 bit
[linux-headers-3.4.0-030400-generic-pae_3.4.0-030400.201205210521_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-precise/linux-headers-3.4.0-030400-generic-pae_3.4.0-030400.201205210521_i386.deb")
[linux-headers-3.4.0-030400-generic_3.4.0-030400.201205210521_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-precise/linux-headers-3.4.0-030400-generic_3.4.0-030400.201205210521_i386.deb")[TABLE]
[TR]
[TD][/TD]
[TD][/TD]
[TD="align: right"]Which one's for me? What difference does the .pae make? 


[/TD]
[/TR]
[/TABLE]

[On a side note, before reading your reply I went about upgrading to 3.8.3 raring which I realize now was a mistake.  My display's a bit off about an inch and a half on each side.  I'm assuming that downloading 3.4 for precise will fix that?]

---

### Post by Niemand000 on 2013-03-19
> **kevdog said:**
> His book is good, however it's slightly advanced for the beginner... I would supplement your reading with other sources.
Yeah, I definitely figured that out. I'm using [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) for now.  I figured it would be an adequate prerequisite for his book.  I guess I'll find out! haha

I'll definitely get in touch with him though, thanks for suggesting that.

---

