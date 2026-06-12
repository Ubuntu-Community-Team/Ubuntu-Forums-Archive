---
title: "SHMMAX limit on EC2"
date: 2010-07-05
forum: Server Platforms
---

### Post by john4 on 2010-07-05
I've brought up a "Large" EC2 instance of 10.04 which has 7.5GB of memory, but SHMMAX is set too low to use all that memory.

When I do "sudo cat /proc/sys/kernel/shmmax" it says that the limit is set to 33554432.

How do I increase this limit to use the full 7.5GB?

Thank you,

John

---

### Post by sjinks on 2010-07-05
echo "value" | sudo tee /proc/sys/kernel/shmmax

---

