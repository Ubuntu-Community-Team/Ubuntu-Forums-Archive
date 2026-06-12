---
title: "Problem with virtualization in virtual box (windows 8)"
date: 2014-09-05
forum: Virtualisation
---

### Post by silveringking on 2014-09-05
Hi I'm having the following problem:

I was following this guide [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox) to install ubuntu in my virtual box (Oracle VM Virtualbox Manager).

I set up it just like it says but when I start it in order to install this error appears:

```
Failed to open a session for the virtual machine **Ubuntu**.

The virtual machine **'Ubuntu'** has terminated unexpectedly during startup with exit code 1.
[TABLE="width: 100%"]
[TR]
[TD]Result Code: [/TD]
[TD]E_FAIL (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component: [/TD]
[TD]Machine[/TD]
[/TR]
[TR]
[TD]Interface: [/TD]
[TD]IMachine {480cf695-2d8d-4256-9c7c-cce4184fa048}[/TD]
[/TR]
[/TABLE]

```

And here is a print screen.

[IMG]http://i.imgur.com/rnIsQ7Q.png?1[/IMG]

Can you guys help me? Thank you so much in advance.

---

### Post by bashiergui on 2014-09-06
See if this helps, not sure if it will be true for Win 8:
[https://forums.virtualbox.org/viewtopic.php?f=6&t=33196](https://forums.virtualbox.org/viewtopic.php?f=6&t=33196)

It says: > I went into the folder "C:\Users\COMPUTER_NAME\.VirtualBox\Machines\VM_NAME\" and saw two xml files but for some reason they both had suffixes. 1. VM_NAME.xml-prev
2. VM_NAME.xml-tmp
So it simply just couldn't find "VM_NAME.xml" because it technically didn't exist.
I made a copy of the "VM_NAME.xml-prev" file and renamed the copy to "VM_NAME.xml"
Restarted VirtualBox and it worked just fine.By the way the virtualbox forum has been the best way for me to find solutions.

---

