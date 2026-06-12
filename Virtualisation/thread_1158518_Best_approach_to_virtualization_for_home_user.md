---
title: "Best approach to virtualization for home user?"
date: 2009-05-13
forum: Virtualisation
---

### Post by theRick on 2009-05-13
I am a home user who wants to do all of my computing off of virtual machines (Windows 7 RC, XP for gaming, Ubuntu Desktop and Server...). Because of this, obviously I want to have as many resources as possible available to the virtual machines.

What is the best way to install the lightest host system possible? Is there any option that doesn't even require a graphic host system?

Is there any option that lets me use things that are important to me such as dual monitors within my virtual machines?

I've used Paralells and VMware inside Windows before - but I love the flexibility of saving and cloning virtual machines and really want to start learning more.

Thanks in advance.

---

### Post by pro003 on 2009-05-13
in linux i.e ubuntu I've tried lots of times Virtual Box (from Sun) and it proved to be OK.

Im not sure is there a package in repo but do a search in synaptic or in terminal type

# aptitude search virtual*

---

### Post by whoop on 2009-05-13
I wouldn't expect a good gaming experience inside a vm if I where you.
There are various virtualization packages that you can install on a server. You get better performance if you use processors that support virtualization (and don't be shy with RAM either). Keep your server install as light as possible (don't install a window manager, unnecessary servives etc.) and install virtualization software on the server. Then you can connect with a client (using a different physical machine). You can actually run numerous guests at the same time (if your hardware can handle it) and use them on different client machines.
Examples of virtualization software that run on (ubuntu) server are kvm and vmware server.

I'm not sure how far you want to go with this, but I'm just showing you what's possible.

---

### Post by theRick on 2009-05-13
Thank you for the reply whoop

So based on what I want to do (a lot of flexibility playing with different operating systems) it sounds like my best bet is to install a minimal ubuntu server with kvm or wmware and then access that server with my desktop pc and just do my gaming off of the desktop pc. Would you (or others) agree?

As far as kvm and wmware are concerned - is one better than the other considering I'll be installing different flavors of both linux and windows?

Can they I access guest OS remotely on both?

Thanks again

---

### Post by bodhi.zazen on 2009-05-13
If you are new to virtualization I suggest VirtualBox as I think it is the easiest to set up and learn.

Spending an hour or so reading some of the sections in the virtualbox manual is also time well spent.

[http://download.virtualbox.org/virtualbox/2.2.2/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.2.2/UserManual.pdf)

Personally I prefer KVM and OpenVZ , but IMO best learn the basics with VBox first.

---

### Post by theRick on 2009-05-15
> **bodhi.zazen said:**
> Personally I prefer KVM and OpenVZ , but IMO best learn the basics with VBox first.

Just wanted to come back and say thanks for that recommendation.

I was able to get virtualbox installed on my ubuntu server this evening and following the virtualbox manual i then got an instance of windows xp running on it with VBoxHeadless and remote desktop connection.

That is exactly what I was looking for. Thanks again!

---

### Post by bodhi.zazen on 2009-05-15
I am glad you had a good experience with Virtualbox :)

---

### Post by maflynn on 2009-05-15
I tried virtualbox and while it did work w/o any problems I was dissatisfied with the performance and it seemed to lack the polish of vmware that I've grown accustomed too (using vmware fusion).  I have since uninstalled virtualbox and installed vmware server. It seems overkill for my needs and probably most home users but its free and the performance of the guest OS was much better then virtualbox.  The other option is to use vmware server or workstation (the trial), create the vm, then use the free version of vmware player.  This seems like a lot of work, but it will get you a vm at no cost.

I've downloaded (but not installed) the trial version of vmware workstation. I'll probably play with that myself but it seems kind of pricey (almost 200 bucks) for my needs and while it is over-kill vmware server does work and it is free.
[/ramble]

---

