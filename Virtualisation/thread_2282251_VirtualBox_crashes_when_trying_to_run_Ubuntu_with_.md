---
title: "VirtualBox crashes when trying to run Ubuntu with 3d acceleration"
date: 2015-06-12
forum: Virtualisation
---

### Post by stupidquestion on 2015-06-12
When trying to log in, I get:

VirtualBox.exe - Application Error
The instruction at 0xfb8ead4e referenced memory at 0x00000000. The memory could not be read.
Click on OK to terminate the program.

And VirtualBox would close. 
The only way around this is to start without 3D acceleration. 

Any idea on how to fix this?

I even reinstalled a new Ubuntu instance from scratch, and it still crashed the same way when trying to login for the first time after installing Guest Additions.

---

### Post by TheFu on 2015-06-17
That is a null pointer reference. It is bad.
Looks like you are running under Windows - might be best to ask on a Windows vbox forum?

To get mire help here, we need lots more data - OSes, guest and host. RAM, CPUs, any other details that aren't normal.

---

