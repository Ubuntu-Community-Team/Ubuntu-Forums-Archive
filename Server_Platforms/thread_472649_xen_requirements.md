---
title: "xen requirements?"
date: 2007-06-13
forum: Server Platforms
---

### Post by blmartin777 on 2007-06-13
I was was thinking about playing around with xen on an extra computer I have but wasn't sure what the requirements are for xen.

I have a athlonxp 2400+ and 1.256 gb ram.

Would xen run on that?

---

### Post by blmartin777 on 2007-06-13
Bump

---

### Post by gombadi on 2007-06-14
xen will run on that fine.

As with all computers the more you have the better. More RAM means you can run more virtual machines and more disk space means each VM can have bigger disks.

What size disks do you have?

With that much RAM you could install about four VM's each with 256 MB RAM. Give each at least 10GB disk space and you have a good xen system.

All that of course depends on what you are running in the VM's - web sites, databases or loading it down with java and sedi/folding@home etc. CPU speed should be fine for most loads you want to run.

---

### Post by blmartin777 on 2007-06-14
I have a 500 gb disk. Most likely a web server, print server, a mail server, and a seperate vm to back everything up to possibly. I haven't worked it all out yet. Just playing with some things. If you run all those in seperate vm's can you run one webmin to control all or does each one have to have it's own webmin. Or is there something else I should be looking at.

---

### Post by gombadi on 2007-06-14
Each VM has to be treated as a seperate machine (with its own ip address disk space etc) so you will need a webmin per vm.

With 500 GB of disk you will run out of memory before disk space. It will allow you to have many VM's setup but only some running at a time.

Using disk partitions with lvm will be the best for this. In my opinion :)

---

