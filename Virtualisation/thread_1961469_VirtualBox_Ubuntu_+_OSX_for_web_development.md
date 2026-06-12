---
title: "VirtualBox Ubuntu + OSX for web development"
date: 2012-04-19
forum: Virtualisation
---

### Post by AdamGerthel on 2012-04-19
I'm looking into the ability to use Ubuntu running on a VirtualBox in OSX environment as a local webserver for web development. 

Ubuntu would be handling php, apache and mysql, but I would want to handle everyday activities from within OSX.

So OSX should handle files, version control, and also be able to reach the MySQL server on Ubuntu (using SequelPro).

I've gotten pretty far in trying to accomplish this when I've tried it out, but I was having trouble with shared folder, since I want to keep all the files on OSX. It's been a while so I don't recall exactly that the problem was, but since then, the need to be able to work this way has increased. It does seem difficult to accomplish though.

Does anyone have any experience of this? Is it possible to do it?

Thanks,
Adam

---

### Post by avunda on 2012-04-19
Hi Adam,

I know this might be dumb, but have you installed the guest permissions on the virtual machine, and allowed it to connect to the rest of your HD? That seems to have been able to give me full access to most files on my Mac while running Ubuntu virtually.


I hope this helps!

---

### Post by 2F4U on 2012-04-19
The VirtualBox documentation has a very detailed section about shared folders.

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

You need to install the VirtualBox Guest Additions in Ubuntu.

---

