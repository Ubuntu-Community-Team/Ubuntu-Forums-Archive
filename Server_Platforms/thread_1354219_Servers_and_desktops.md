---
title: "Servers and desktops"
date: 2009-12-13
forum: Server Platforms
---

### Post by Marvin666 on 2009-12-13
What exactly are the differences between ubuntu server, and the desktop version?
I know the win server versions are faster, lighter, and more stable than their desktop equivalents, but does this apply to ubuntu as well?

---

### Post by Cheesemill on 2009-12-13
The main difference is that Ubuntu Server doesn't come with a GUI, it's command line only by default, a graphical interface would use up unnecessary resources and provides a bigger attack surface for anyone trying to hack your machine.

Also the server kernel is optimized for server rather than desktop processes.

[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

---

### Post by Marvin666 on 2009-12-13
So would a server kernel give me any speed increase on a normal computer (with a gui installed) or would it actually slow down?

---

### Post by Queue29 on 2009-12-13
> **Marvin666 said:**
> So would a server kernel give me any speed increase on a normal computer (with a gui installed) or would it actually slow down?

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

It does not make sense to run your desktop on the server optimized kernel. The server optimized kernel is optimized to run server type processes. 

Don't you think if using the server optimized kernel on the desktop was faster, that Ubuntu would be using that kernel on the desktop? Believe it or not, some of the developers know what they are doing.

---

### Post by Marvin666 on 2009-12-13
I just assumed the server kernel ran faster than the desktop like on win, but I guess on linux the kernels are already fully stream-lined.

---

### Post by tgalati4 on 2009-12-13
I run a dapper desktop with several server daemons running.  I find the desktop uses ~10% of cpu cycles when not in use.  So you would effectively gain a 10% increase in performance without xorg installed.

Also, the server version doesn't have hooks into the ACPI to put the machine to sleep or to wake.  So your machine is on 24/7 with the server version.

The server kernel is slower to respond to mouse and keyboard interrupts as it is optimized for handling large number of processes, not user input.

---

### Post by HighCommander540 on 2009-12-14
> **Marvin666 said:**
> I just assumed the server kernel ran faster than the desktop like on win, but I guess on linux the kernels are already fully stream-lined.

The Win server runs fast, because the server is not running all of the ******** that your desktop is running. Not because it is faster or better, but because it is literally just not running as much.

The same is mostly true on Ubuntu (with a few exceptions. The point is if you want a desktop run the desktop software. They are named what they are for a reason. It would actually run slower if you used the server as your desktop, because it would be best built to run stuff you are asking it to.

---

