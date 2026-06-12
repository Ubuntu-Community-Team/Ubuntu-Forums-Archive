---
title: "VMWare error message"
date: 2008-03-18
forum: Virtualisation
---

### Post by ant2ne on 2008-03-18
I have VMWare server running XP-Pro virtualized in my Ubuntu local install. (Works great with 4CPUS and 8 Gigs of RAM. *BRAG BRAG*) 

Error message pops up... seemingly randomly...

> Cannot open file "/home/ant2ne/.vmware/preferences": Permission denied.
Unable to read user preferences. I haven't noticed any performance or data loss. Is this something I should be worried about?

---

### Post by fjgaude on 2008-03-19
The read/write permissions on that file are not right. You can change them to permit your login name to be the user.

You would see better performance if you used only one core while running VMware. The new version in beta uses up to two. Four is a no-go, because of I/O wait states.

---

### Post by ant2ne on 2008-03-19
> ant2ne@2ne-buntu:~$ ls -l /home/ant2ne/.vmware/preferences
-rw------- 1 root root 1502 2008-03-19 18:40 /home/ant2ne/.vmware/preferences
ant2ne@2ne-buntu:~$ 

you are suggesting chmod 770 on that file?

I am content with one core on my XP VM. I plan to run a few different VMs at a time and want a core or two left over. ;-)

---

### Post by fjgaude on 2008-03-19
Yes, 777 or 775 or 644...

Also make sure it's you:
```

sudo chown -R <login>:<login> /that file
```

Let us know how things go.

---

