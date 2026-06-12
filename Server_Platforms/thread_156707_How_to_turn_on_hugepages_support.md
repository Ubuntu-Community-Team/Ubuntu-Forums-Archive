---
title: "How to turn on hugepages support?"
date: 2006-04-07
forum: Server Platforms
---

### Post by ivangotoy on 2006-04-07
For optimal use of cpu and ram i would simply like to turn on hugetlbfs support on 

my ubuntu 5.10 amd64.

i was given a good solution info how to operate them but i cannot make them 

because i have to : To enable hugetlbpages, first you need 2.6 kernel, and then you 

need to recompile it with the following config options enabled:

CONFIG_HUGETLB_PAGE=y
CONFIG_HUGETLBFS=y

i run ubuntu since 5 days and i am using linux as a whole since 20 days. i admit i 

do not have any idea how i should compile whatever and how to turn on these 2 options.

---

### Post by Velvet Elvis on 2006-04-08
You don't want to recompile a kernel on Ubuntu unless you absolutely have to, particularly if you don't understand exactly what it is that you are doing and why.  It's just as likely that you'll kill it as it is that you'll do what you're trying to do.  It would be like trying to do open heart surgery when all you know is basic first aid.

---

### Post by LordHunter317 on 2006-04-08
I'm pretty sure the optimized kernels have them turned on, but I wasn't aware huge TLB pages was an option on AMD64 kernels.

I could be mistaken, though; I have no easy way to check at the moment.

---

