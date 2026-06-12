---
title: "virtual machine on ubuntu server7.04??"
date: 2007-10-30
forum: Virtualisation
---

### Post by depele on 2007-10-30
Hello, 
I am running a ubtuntu 7.04 server @ home.
mysql, apache, gnump3, .....

But for a project in school I need an Iss ans mssql server.

Is it possible to create a virtual machine, 
install vmware ???? on the server.
start the virtual machine from commandline and keep the virtual machine running even if I logout.

configure a webserver on the virtual machine and acces the virtual machine?


grtz..


Thanks for your help

---

### Post by depele on 2007-10-31
bump :(

---

### Post by trmentry on 2007-10-31
Sure is.  ;)

This is what I did.   First off, I followed this **[post](http://ubuntuforums.org/showthread.php?p=3632767#post3632767)**.

It got Vmware installed in no time.  I chose all defaults for install.  This was for 7.10 but I'm sure works for 7.04 as well.  I think 7.04 even has vmware server in the commerical repo.  

Once i had that done, I installed 2003 server and gave it a Static IP on the network.  From there you can install your IIS, etc.  

Hope that helps.

---

### Post by bodhi.zazen on 2007-10-31
I would advise something more like OpenVZ.

I hope to post a how-to on OpenVZ in the next few days, I have a 7.10 guest up and running (which I am submitting to the OpenVZ project).

---

### Post by depele on 2007-11-01
yes please.

Let me know about the openvz tutorial.



@trmentry

==> the problem is I have no virtual windows(gnome, xfce, kde).
My server doesn't even has a screen. 
I only access it using ssh.

Everyting has to be done from command line or web-interface or something.

thanks

---

### Post by depele on 2007-11-01
Ok 

Problem installing vm ware.
I upgraded my kernel to 22.9

and I think that's why I can't install vm ware.

this is the output.

> make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to make a vmmon module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config4/vmmon.o': -1 Invalid module format
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

---

### Post by bodhi.zazen on 2007-11-01
> **depele said:**
> yes please.

Let me know about the openvz tutorial.



@trmentry

==> the problem is I have no virtual windows(gnome, xfce, kde).
My server doesn't even has a screen. 
I only access it using ssh.

Everyting has to be done from command line or web-interface or something.

thanks

I will be submitting an ubuntu-7.10 virtual machine to OpenVZ later today (the Last Ubuntu machine was 6.06 and there are problems with upstart so this is, IMO, a much needed update).

Hope to get to a how-to over the next day or so ...

---

### Post by azelter on 2007-11-01
> **bodhi.zazen said:**
> I will be submitting an ubuntu-7.10 virtual machine to OpenVZ later today (the Last Ubuntu machine was 6.06 and there are problems with upstart so this is, IMO, a much needed update).

Hope to get to a how-to over the next day or so ...

Excellent. I look forward to reading it. I would really like to get openVZ working on my gutsy system.

---

### Post by depele on 2007-11-02
I am looking to it to......    ;-) 

since vmware isn't easy to get running

---

