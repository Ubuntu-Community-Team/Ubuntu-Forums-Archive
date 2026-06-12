---
title: "Managing a Windows lab with *nix"
date: 2008-09-11
forum: Windows
---

### Post by Tipo on 2008-09-11
Hey all,

I work for the IT department at my University and we don't have a Windows Server... Unfortunately, we can't manage upgrading all of the campus windows machines with the Apple Xserve, and in order to manage all of the upgrades and maintenance type stuff on the Windows machines, our techs need to go around to every individual machine to apply updates.

So, any of the *nix gurus out there know anything about running a *nix update/management server for a Windows lab? Can it be done? We basically need something that (hopefully like Apple Remote Desktop :P  ) will be able to push updates and install them to many machines. Being able to add/remove/edit printers and a few other basic preferences would be a huge plus as well.

We would get a Windows server with Windows remote desktop, but the university won't put one in our budget...

---

### Post by cmat on 2008-09-11
I'm not really sure but possibly putting Cygwin on the PCs and using SSH could possibly give you the control you need. I actually made software to do this a few years ago. It shutdown, reset and did a whole bunch of other tasks over TCP/IP form a central terminal. It controls Windows clients but the server app was cross platform. I wish I kept the source code :(

---

