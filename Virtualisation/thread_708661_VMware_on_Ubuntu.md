---
title: "VMware on Ubuntu"
date: 2008-02-26
forum: Virtualisation
---

### Post by jboby32 on 2008-02-26
I have recently installed Ubuntu 7.10 destop. Previously I was using windows XP. I had planed to install Ubuntu and then install XP as a virtual machine, but i am having problems installing VMware workstaion 5.5.4-44386. I have viewed many help sites but none of them helped. They were all for different versions of Ubuntu. So I need some help on installing VMware on my computer, When i select the vmware-install.pl it asks if I want to run in terminal, display, close, or run. I select run and nothing happens. Then I tried run in terminal and the terminal open but then closed immediately. So then I started searching for help and supposedly I'm supposed to run some other stuff in the terminal first, but of all of the things I have read have not helped at all so here I am asking for help. So can someone please help me?

---

### Post by fjgaude on 2008-02-26
Are you doing the selecting in Nautilus?

If so, I don't think this is the way to success.

In a terminal, cd to where you have the vmware package to be installed. Then

```
sudo ./vmware-install.pl
```

Hit Enter and then answer the questions, one at a time. I would use default for them all.

Let us know how things go.

---

### Post by SonicSteve on 2008-02-26
are you aware of virtual box? 
[www.virtualbox.org](www.virtualbox.org)
It works very well.

Just make sure you don't download the OSE edition it can't handle USB.
I believe the download from the site is the full version.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) 
This download is a deb file which in Ubuntu means double click and install. Sorry if you already know this, I noticed you are new around here.

---

### Post by fjgaude on 2008-02-26
Can we compare VirtualBox to VMware Workstation?

---

### Post by SonicSteve on 2008-02-26
Let's not hijack this thread with a battle over vmware vs. virtualbox. 

They are designed to do the same thing and if you don't want to shell out $$ money for vmware, virtualbox is a great alternative. 

Vmware only gives you a 30 day evaluation license. Virtualbox is free.

---

### Post by fjgaude on 2008-02-26
Actually, VWware Server is free, no expiration, period... no money required. Workstation is not.

---

