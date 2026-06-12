---
title: "Memory allocation for virtual machines"
date: 2009-08-01
forum: Server Platforms
---

### Post by DaveAK on 2009-08-01
Can you over allocate memory from the host?  And how much memory do you need to leave for the host itself?

I have a Dell workstation with 1GB of memmory that I'm throwing on some different servers under VMWare as a learning experience.  I've got a mail server up and running which I gave 256MB to. I'd like to add a web server, dns server and dhcp server.  I'm thinking 256MB for the web server and 128MB a piece for the other two.  That would leave 256MB for the host, if that's the way it works.  Does that all sound reasonable?

What if I allocated 256MB to each guest, how would the host react?  What if I allocated more than the 1GB, assuming that they all wouldn't be at peak usage at the same time?  Can you even do that?

---

### Post by Nburnes on 2009-08-01
Man running Virtualizations on 1GB RAM is really hard.

---

### Post by DaveAK on 2009-08-01
> **Nburnes said:**
> Man running Virtualizations on 1GB RAM is really hard.
These are not heavy use or production servers, (home environment), and the mail server that is running right now is doing just fine.  I'm just curious as to how hard I can actually push this.  I don't see any problem with DNS/DHCP, but adding in a web server might get interesting. :)

---

### Post by jamesrfla on 2009-08-01
You should be able to run all of your server services on one operating system. The mail server, web server, DNS server, and DHCP server can run all on one OS. I run a web server, mail server, file server, ssh server, mysql, and a terminal server all on one operating system. Ubuntu Server edition with just apache2 running took up 32MB of RAM on my one computer. Linux doesn't take up much RAM with server services. Windows server uses a lot of RAM.

---

### Post by lykwydchykyn on 2009-08-02
is the point to learn those services or learn virtualization?  Like the previous poster said, all those will run happily on the same machine.  And IME running multiple VM's on workstation hardware (especially if it's a single core processor like a P4) is painfully slow.

I don't know about vmware, but I know virtualbox will throw an error if you try to allocate more than half your RAM to VM's.  You can override the error, but it's there for a reason...

---

### Post by DaveAK on 2009-08-02
I know I could easily run everything I need off of one server, but this is all part of a learning exercise for me.  Take the Mail Server for instance, I took a couple of goes to get it set up the way I wanted.  If I then tackle a DNS server, and screw it up and want to start again, I'd also have to redo the Mail Server if I wanted a clean install, or at the very least disrupt my mail service while I sorted out the DNS. Having the servers virtualized protects the good ones from being screwed up by my efforts on the bad ones.

Right now it is just a P4 with 1GB RAM, running a host and one guest, (a mail server).  The performace is just fine for this, and I don't think it will suffer with DNS and DHCP.  Web server might be a different story, but I might just use separate hardware for a web server, or just not do one at all.  (I have a dedicated hosted web server, so don't really need one at home.)

---

