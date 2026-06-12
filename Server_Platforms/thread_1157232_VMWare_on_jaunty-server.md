---
title: "VMWare on jaunty-server"
date: 2009-05-12
forum: Server Platforms
---

### Post by xkaliburx on 2009-05-12
I assume it's still called jaunty as it's a brand new server 9 download!  

So with that, I want to install VMWare-server as I am playing with a few appliances, but not so sure on the how.  I think apt needs some additional repo's but can't seem to find.

Really a simple question and hate resorting to forums for this, but google reveals way to much and nothing helpful.  Most of the time the distro is too old!

So if anyone has an easy install for VMWare-server, a reply is much appreciated.

---

### Post by TwiceOver on 2009-05-12
I'm not sure what is in the Repos but VMWare Server 2 works fine on the server version.  These are the instructions I have followed in the past:

[http://www.howtoforge.com/how-to-install-vmware-server-2-on-an-ubuntu-8.04-desktop](http://www.howtoforge.com/how-to-install-vmware-server-2-on-an-ubuntu-8.04-desktop)

One slight change...  When VMWare starts asking all the questions and it gets to something like: "Administrator for this server []" Be sure to set it as your username.

Then you don't have to create a root password and you can sign in using your credentials.

---

### Post by IamWayne on 2009-05-12
Yeah, I would like to know how to put Vmware Workstation on Jaunty. If anybody knows, please provide some info. :)

---

### Post by windependence on 2009-05-12
Have you tried ESXi? You don't need a host OS for that.

-Tim

---

### Post by xkaliburx on 2009-05-13
I actually have an ESXi host running.  But the odd thing is I can't install that VM.  That link provided gives you a download to a ubuntu64.zip file, once extracted gives you a bunch of the .vmdk files, and the .vmx file.

The ESXi server has an import with 3 options;
1. Import from Marketplace:  I tried that, but it's not ALL the VM servers so that one is not listed.

2 and 3 both look for a .ovf file, which I really don't know what they are. 

I would love to put that VM on the esxi server, so if you have suggestions on that, let me know.

Thanks

---

