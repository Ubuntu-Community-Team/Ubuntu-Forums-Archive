---
title: "virtualbox in ubuntu"
date: 2014-03-21
forum: Virtualisation
---

### Post by newbie75 on 2014-03-21
Hello
I want to install Ubuntu on my laptop as the host and then use virtualbox for using two virtual machine, one using centos 4.7 as guest and one using windows 8 as guest. Which Ubuntu is the best for me? 12.04 or 13.10? Can I use Virtualbox for this purpose?
Tnx.

---

### Post by andrew.46 on 2014-03-21
VirtualBox would be fine for this on either flavour of Ubuntu. Two issue to look at though:

[LIST=1]
[*]Make sure you have sufficient resources on your computer to allocate to each VM
[*]Decide whether you want the repository version of VirtualBox or you wish to download [from the Oracle site]("https://www.virtualbox.org/wiki/Downloads").
[*]
[/LIST]

---

### Post by SeijiSensei on 2014-03-22
You do know that the current version of CentOS is 6.5, right?  And that all the 4.x versions have [reached end-of-life]("http://wiki.centos.org/Download")?

---

### Post by andrew.46 on 2014-03-22
For my part I confess that CentOS is a totally unknown distro :(

---

### Post by slooksterpsv on 2014-03-22
12.04 if you want long-term Ubuntu; 13.10 you'll have 3 months left of support after April.

I personally think 13.10 would be better if your system is newer - the kernel enhancements make it worthwhile in my opinion; and I also recommend the DEB from virtualbox.org over the repo (repo version is out-dated quite a bit).

What specs are your system?

---

### Post by SeijiSensei on 2014-03-24
> **andrew.46 said:**
> For my part I confess that CentOS is a totally unknown distro :(

I was replying to the OP, Andrew.  Sorry if that was unclear!

---

### Post by holycow131415 on 2014-03-24
Perhaps wait a week for the newest LTS to arrive?

---

