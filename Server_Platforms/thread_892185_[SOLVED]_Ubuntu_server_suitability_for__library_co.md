---
title: "[SOLVED] Ubuntu server suitability for  library computers"
date: 2008-08-16
forum: Server Platforms
---

### Post by rtrdom on 2008-08-16
The library permits library card holders to use many of its computers as
the card holders wish, with some exceptions such as limiting some sites to
protect youth. The library also has its internal operations on the same
server but is trying to find a way to separate the two systems. All computers in use at the library are Windows XP Pro operating system. They are thinking about using at
least one computer to control operations of the public computers and another one to control their internal operations.   I would like to recommend Ubuntu
but know very little of its server capabilities, even after reading lots of
information at: Ubuntu server Edition. Can
Ubuntu server work with all the public machines (mostly searching the
internet, retrieving mail, etc), and keep the internal operations separate
and secure from the "public" machines?

---

### Post by tamoneya on 2008-08-16
it can definitely do all of the above.  You may however want to consider just going with the desktop version.  It is just as secure as the server edition and the only big difference between desktop and server is that the desktop edition has a graphical user interface as opposed to the server which is all command line.  If you want to do internet and stuff you may be better off with desktop.  You could install a GUI on the server edition but it is just simpler to use the desktop version.

---

### Post by rtrdom on 2008-08-16
Thank you Tamoneya for the response. I will forward the information to them
and see what they want to do.  At present, a "Network Installer" is in the
process of figuring out what to do and what costs will be but he has delayed responding for 4 days so far and they are getting anxious a bit.

Should they decide to try Ubuntu desktop as a server, What is the security
of transferring the files of all their "for loan" books, financial, and personel files to the new machines?

---

### Post by tamoneya on 2008-08-16
security wise there are no differences between server and desktop.  Personally I would setup openssh and transfer though ssh tunnels.  It will be fully encrypted.  Also ubuntu allows you to encrypt the entire OS when you install.  Im not sure how that appeals to you but it is available in both server and desktop.

---

### Post by rtrdom on 2008-08-17
Thanks for the help.  I'll consider this thread closed(solved) until I find out
what they want to do.

---

### Post by windependence on 2008-08-19
> **tamoneya said:**
> it can definitely do all of the above.  You may however want to consider just going with the desktop version.  It is just as secure as the server edition and the only big difference between desktop and server is that the desktop edition has a graphical user interface as opposed to the server which is all command line.  If you want to do internet and stuff you may be better off with desktop.  You could install a GUI on the server edition but it is just simpler to use the desktop version.

I'm sorry but this is just not accurate. The server version has many features the desktop version does not. Here's some BIG ones:

> Here is a list of the server-specific kernel optimisations that we include:

    *

      The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.
    *

      Pre-emption is turned off in the Server Edition.
    *

      The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.
    *

      The Server Edition is optimised for i686 processors while the Desktop Edition is optimised for both the i586 and i686.
    *

      Virtualization is better supported in the Server Edition through the enabling of IPC namespaces.
    *

      Multiple routing tables for the IPv6 protocol are also supported in the Server Edition.
    *

      For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB.
    *

      When running a 64-bit version of Ubuntu on 64-bit processors you are not limited by memory addressing space.




[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

That's just in the kernel alone. There is more:

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

You can read all about the differences here:

[http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition)

To answer the OP's questions, he should probably run two machines, or at least run two virtual machines on one box. I would run something like untangle ([www.untangle.com](www.untangle.com)) to filter the net traffic, and run the other box for the internal applications, or a file server, etc. The server edition is perfect for this.

You may want to note that a GUI is not essential for a good admin.

-Tim

---

### Post by cracker on 2008-08-19
It should also be noted that running a GUI (X-windows) is a potential security hole without a properly configured firewall.

---

### Post by windependence on 2008-08-19
Hey, I didn't want to push too much on that. We have many people here who can't seem to learn the CLI. If this was the desktop forum, I might be less pushy about it, but a server is meant to be admined with the CLI.

-Tim

---

