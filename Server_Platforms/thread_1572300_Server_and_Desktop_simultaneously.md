---
title: "Server and Desktop simultaneously"
date: 2010-09-10
forum: Server Platforms
---

### Post by boeing114 on 2010-09-10
I currently have a dual boot of Ubuntu Desktop Edition, and Windows Vista. (the only reason vista is around is because of iTunes). I was wondering if it is possible to add Ubuntu server to the mix, and if it is possible, could I be on Ubuntu desktop while my server is still accessible online via ispconfig.

Help would be greatly appreciated.

---

### Post by Nythain on 2010-09-10
ubuntu server is nothing more than ubuntu, without a gui, and the option to install certain server apps at install... and a very very few minor kernel tweaks that i dont even know if they're there anymore...

moral of this story is, install whatever server daemons you want, webserver, mail server, whatever server, and viola, you have ubuntu server and a desktop environment :)

---

### Post by boeing114 on 2010-09-10
> **Nythain said:**
> ubuntu server is nothing more than ubuntu, without a gui, and the option to install certain server apps at install... and a very very few minor kernel tweaks that i dont even know if they're there anymore...

moral of this story is, install whatever server daemons you want, webserver, mail server, whatever server, and viola, you have ubuntu server and a desktop environment :)

But if I hosted the domain 'somedomain.com' on the ubuntu server, if I was on my Desktop partition, would the server still work? Or would I have to be on the Server partition for it to work?

---

### Post by CharlesA on 2010-09-10
If you installed those services on Ubuntu Desktop, they would work whenever the desktop was running.

If you want a seperate desktop and server, you could always run a VM in VirtualBox.

---

### Post by boeing114 on 2010-09-10
So in order to make my server work, It has to be booted on my computer?

---

### Post by CharlesA on 2010-09-10
> **boeing114 said:**
> So in order to make my server work, It has to be booted on my computer?

Yes. Like I said, you can install server packages on the desktop version and it'll work fine, but if you really want to run a "server" you might as well use the server install.

---

### Post by HermanAB on 2010-09-11
Linux is Linux is Linux...

You can install whatever you want on your machine.  The distinction between 'Server' and 'Desktop' versions is rather meaningless and artificial.

However, from a management and maintenance point of view, it is frequently better to make a complicated server setup a separate machine (hardware of virtual), just to keep things under control more easily.

---

### Post by CharlesA on 2010-09-11
> **HermanAB said:**
> 
However, from a management and maintenance point of view, it is frequently better to make a complicated server setup a separate machine (hardware of virtual), just to keep things under control more easily.

Not to mention not putting all yer eggs in one basket, should the server be compromised.

---

