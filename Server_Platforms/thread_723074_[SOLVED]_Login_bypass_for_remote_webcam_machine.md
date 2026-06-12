---
title: "[SOLVED] Login bypass for remote webcam machine"
date: 2008-03-13
forum: Server Platforms
---

### Post by talkeetnaweb on 2008-03-13
I'm making a webcam machine and would have to drive 30 miles to enter a password if the power failed and then came back on. Is there a way to make the machine start up, bypass the login, and run the webcam program? Maybe /etc/rc.local is the answer to running the program but I still need to login in absentia.

Thanx

---

### Post by MJN on 2008-03-13
Anything run as a system service, including those called by rc.local, will run without you logging in.

Mathew

---

### Post by talkeetnaweb on 2008-03-14
Thanks for that bit of insight into the system. That will solve my problem and in a more elegant way than starting without a login prompt.

---

