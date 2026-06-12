---
title: "installing Ubuntu on VM"
date: 2018-04-15
forum: Virtualisation
---

### Post by marykhaleel on 2018-04-15
Hello,

I would like to install Ubuntu on virtual machine on server. The platfrom of the server is Windows and I need file in .iso format. Could you please guide me how to do it?

thanks

---

### Post by TheFu on 2018-04-16
Welcome to the forums.

Which hypervisor?  Each has different steps for installation and different best practices.

.ISO files are used to install FROM, not into.  You can run an existing image that is in an ISO file inside a VM, but since ISOs are readonly, no updates or modifications will be saved.  There are many guides for setting up and using VMs. Youtube has thousands of videos of people doing it too.

You can build an ISO, like a liveCD if you want, but you'll want to do that from an installed version. There are tools for this, but I haven't used them in a while, so don't have 1st hand knowledge that is recent.

---

