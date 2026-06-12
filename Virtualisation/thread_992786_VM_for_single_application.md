---
title: "VM for single application?"
date: 2008-11-25
forum: Virtualisation
---

### Post by argail1980 on 2008-11-25
Hi everyone,

I'd like to know if there's a possibility to setup a virtual machine that only starts a single application. 

What I need to do is to install AutoCad on an ubunutu machine. I've searched on this topic, but it seems that only the most ancient versions of AutoCAD will run with wine. 
My idea is to get something between wine and a full virtual machine as started i.e. by VBox, because I want to save as many resources as possible for Matlab and AutoCAD.
There is VMware - ThinApp, but of course I would prefer an OpenSource solution

---

### Post by HermanAB on 2008-11-25
Yes, you can install Vmware (or Virtualbox) install Windows ExPee in that, then install seamless RDP and create a link on your Ubuntu desktop to run rdesktop and connect to the Windows instance and launch a specific application.

See this:
[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

Cheers,

Herman

---

### Post by argail1980 on 2009-05-08
Hi,

thanks for the reply, but that is not what i'm looking for. I was trying to get around having a whole windoze running in the background. I went for the dual boot solution now.

Cheers
argail

---

### Post by thomasr on 2009-05-08
Some versions of autocad will run with Wine - 
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=86](http://appdb.winehq.org/objectManager.php?sClass=application&iId=86)

---

### Post by lukeiamyourfather on 2009-05-08
Running Windows XP requires hardly any resources on modern hardware. The only real overhead for running a full virtual machine versus Wine is the quantity of memory consumed by Windows. So get some more memory and use a full on virtual machine because memory is dirty cheap (8GB DDR2 or DDR3 for less than $100), or just dual boot anyway. Cheers!

---

### Post by dcstar on 2009-05-08
> **argail1980 said:**
> Hi,

thanks for the reply, but that is not what i'm looking for. I was trying to get around having a whole windoze running in the background. I went for the dual boot solution now.


I run an XP guest in a production environment because there is an old realtime app that requires a logged in Windows session to run, and this is the most effective way of doing it (the resources used once started are trivial).

The simplicity of having another OS available in a few seconds inside a host far outweighs the hassle of rebooting - unless the app is so resource hungry that it only runs in an acceptable manner in native mode.

---

