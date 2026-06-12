---
title: "Mount vmdk for both read and write access"
date: 2010-07-02
forum: Virtualisation
---

### Post by LuckyNeo on 2010-07-02
I installed VMware Workstation 7.1 on my Ubuntu 10.04 and I want to access guest OS virtual drive (vmdk). Is it possible to mount it?

---

### Post by LuckyNeo on 2010-07-02
Shame on me. There is vmware-mount command.

---

### Post by sgomez11 on 2013-05-01
Hey did you get this working? I used the vmware-mount command to mount a particular partition of my VMDK file and I was able to see/read the files. After some permissions changes, I was able to write to the files and add new files. 

However, the changes did not persist after unmounting. I didn't see any errors or anything when I did 'vmware-mount -d <mount point>', but when I remount the same VMDK I don't see the changes that I made.

---

### Post by wildmanne39 on 2013-05-03
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

