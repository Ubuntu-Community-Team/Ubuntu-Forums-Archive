---
title: "turning off kernel updates"
date: 2006-03-10
forum: Server Platforms
---

### Post by dcherryholmes on 2006-03-10
I've got some compiled stuff on a server that is sensitive to a particular kernel.  I'd like to script apt-get update && apt-get upgrade, but I'm worried I'll accidently shlurp down another kernel and break stuff.  Does anyone know how to tell apt to ignore kernel upgrades?  It was doable in Suse with YAST, so I'd expect it's doable with apt.

---

### Post by Xian on 2006-03-10
You can use wajig to hold packages:

$ sudo apt-get install wajig
$ sudo wajig hold <package_name>
$ sudo wajig unhold <package_name>

---

### Post by dcherryholmes on 2006-03-11
Thanks a lot for the solution!  I'm in the middle of dist-upgrading to Dapper Flight 5 atm, but I'll install wajig and try it out.

---

### Post by az on 2006-03-11
You can also use apt or synaptic (if you're running X) to pin packages.

---

