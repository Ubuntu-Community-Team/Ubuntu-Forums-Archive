---
title: "move vdi file from one user to another"
date: 2011-09-20
forum: Virtualisation
---

### Post by rollinsmoke on 2011-09-20
hi there 
im running virtualbox ose through ubuntu 11.something or another and was wondering how to use the vdi files from one user to the next also how to reuse the snapshots. my main user crashed and still haven't had any luck restoring it so im just going to dump it and start over i suppose thanks for looking

---

### Post by Shazaam on 2011-09-20
Can you access the .vdi file?
If you can, move it (the whole folder would be preferable) over to your home folder. Start up Vbox and make a "New" virtual machine as close to the old one as you can. When it comes time to set up a new hard drive for the vm choose "existing" and point Vbox to the saved vdi. Before you start the new vm open the Settings menu and configure it as close to the old vm as possible. Don't forget to add youself to "vboxusers" in Users and Groups.
If you have authentication errors with the .vdi file change it's permissions to your username.

---

### Post by rollinsmoke on 2011-09-20
oh that was simple enough i dont know why that didnt click to even try that thanks man

---

