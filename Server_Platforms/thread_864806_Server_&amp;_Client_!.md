---
title: "Server &amp; Client !"
date: 2008-07-20
forum: Server Platforms
---

### Post by krsnavan on 2008-07-20
As Linux Desktop versions allows to install all Servers such as MAil,DNS,SUID etc, WHat is the fundamental difference from Linux Server and client versions? Both use the same kernel versions?

Vanna

---

### Post by tinny on 2008-07-20
They are the same.

Except the Desktop version comes with software that makes a desktop installation more usable.

E.g. 

Gnome, office software, email client etc...

At the core they are essentially the same.

---

### Post by krsnavan on 2008-07-20
What about the other considerations as No OF CPUs supported,LOAD BALANCING Features!

Vanna

---

### Post by HermanAB on 2008-07-20
If you are working with servers that are that complicated, then you'll already know what to do...
;)

---

### Post by tinny on 2008-07-20
> **krsnavan said:**
> What about the other considerations as No OF CPUs supported,LOAD BALANCING Features!

Vanna

Those features are in addition to the "core" OS. And if you really wanted you could setup a Desktop on the multi CPU hardware you are talking about.

---

### Post by windependence on 2008-07-20
> **tinny said:**
> They are the same.

Except the Desktop version comes with software that makes a desktop installation more usable.

E.g. 

Gnome, office software, email client etc...

At the core they are essentially the same.

Not hardly.

They are NOT the same at all. The server kernel is far different than the desktop kernel.

More info:

> Here is a list of the server-specific kernel optimisations that we include:

The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.

Pre-emption is turned off in the Server Edition.

The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.

The Server Edition is optimised for i686 processors while the Desktop Edition is optimised for both the i586 and i686.

Virtualization is better supported in the Server Edition through the enabling of IPC namespaces.

Multiple routing tables for the IPv6 protocol are also supported in the Server Edition.

For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB.

When running a 64-bit version of Ubuntu on 64-bit processors you are not limited by memory addressing space.


[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)


-Tim

---

### Post by windependence on 2008-07-20
> **tinny said:**
> Those features are in addition to the "core" OS. And if you really wanted you could setup a Desktop on the multi CPU hardware you are talking about.

....And just why would you want to do something like that? Either you're running a server or you are running a desktop machine, which is it? You have to decide.

-Tim

---

### Post by krsnavan on 2008-07-20
Thanx!

---

### Post by windependence on 2008-07-20
> **krsnavan said:**
> Thanx!

Glad to help. I am curious what you meant when you asked about load balancing features. This would be done with software or maybe a hardware load balancing unit.

-Tim

---

