---
title: "A simple howto"
date: 2009-10-30
forum: Virtualisation
---

### Post by DeadlyOats on 2009-10-30
I, a simple end user, greet all of you linux gurus.  May the gods, goddesses, spirits, and other supernatural, natural, not so natural, and artificial entities that look upon and smile on linux gurus, like you all, take a liking to your good works.

Why all of that in my greetings?  It is because I will ask a question that, no doubt, has been asked countless times before, and I'm hoping my baroquely grandiose greeting grants me your sympathy - and your attention to my question.

To the point.

I searched for a simple howto, not only here, but on google, and as my search skills are lacking, I was unable to find what I was seeking.  That is, a simple howto on how to install xen hypervisor onto a lean linux distro.  All of the howto's I've found are written for linux gurus, such as yourselves, and thus, all over my head.

I downloaded:  linux-2.6.18-xen-3.4.0.tar.gz  and  xen-3.4.1.tar.gz  from the download page at xen's development website.  I extracted the contents and wound up with two folders full of stuff I don't know how to use.  I thought, at least the linux folder would have a bootable iso image that I can burn.  Not the case.

Really to the point.

What I need is a bootable linux distro iso image that is KNOWN to work well with xen hypervisor (one witha gnome desktop would be nice), and a simple howto on how to install xen hypervisor to that linux distro.  Later, I will search for a howto on how to install and configure Ubuntu Linux and WinXP Pro onto the hypervisor.

I have a laptop that has an Intel Core 2 Duo T9500 cpu.  I found that it supports hypervisors and virtualization.  So, hardware is supported.

Please give me your advice.  Thanks.

PS

Apologies all around for the wordiness.

---

### Post by gordintoronto on 2009-10-30
You asked for advice, here it is: use Virtualbox.

---

### Post by morphodone on 2009-10-30
Or Vmware

---

### Post by DeadlyOats on 2009-11-01
I don't know.....  With all of these threads posted about troubles and bugs and what-not about virtualbox and vmware, is it really something that I want to do?

I've read somewhere that xen does not work well on ubuntu.  That's why I asked about a _KNOWN_ Linux distro that *does* work well with xen.  Also, xen is a hypervisor.  My hardware can support xen.  I'm not sure that vmware or virtualbox are hypervisors.

I want as thin a layer between the bare metal and the guest OSes as possible, but I don't think virtualbox or vmware can do that - especially with all of the troubles people, here, are having with them.

What is it about xen that you don't like?

Also, if anyone can point me to the information I'm seeking in my original post, I would really appreciate that.

Thanks.

---

### Post by gordintoronto on 2009-11-02
> **DeadlyOats said:**
> I don't know.....  With all of these threads posted about troubles and bugs and what-not about virtualbox and vmware, is it really something that I want to do?

...  I'm not sure that vmware or virtualbox are hypervisors.

I want as thin a layer between the bare metal and the guest OSes as possible...

What is it about xen that you don't like?

Also, if anyone can point me to the information I'm seeking in my original post, I would really appreciate that.

Virtualbox is "easy to use," so people who would find Xen overwhelmingly complex, will tackle Virtualbox, and not be able to figure out something.  Most of the traffic I've seen is people asking "how do I..." -- and getting answers.

I'm pretty sure Virtualbox is not a hypervisor.

My only complaint about Xen: it hasn't reached the mass media, such as Full Circle Magazine.

Unless your objective is to get experience with Xen, I think you would get what you need by installing Ubuntu, install Virtualbox (not the version from the repositories, BTW), and install XP inside the box.

The only time this might not be satisfactory is if your computer has very limited memory, such as 512 MB or less.

---

### Post by DeadlyOats on 2009-11-03
Hmmmm.....

Thanks again for your input.  I will study your comments, and decide on a course of action.

Thank you, very much.

---

