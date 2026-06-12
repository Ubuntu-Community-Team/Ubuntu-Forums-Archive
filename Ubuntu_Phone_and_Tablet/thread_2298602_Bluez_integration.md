---
title: "Bluez integration"
date: 2015-10-12
forum: Ubuntu Phone and Tablet
---

### Post by karre on 2015-10-12
Hi,

I am working on bluez.
Made the kernel driver as inbuilt.

when i try to run the hciconfig command from the command prompt.
which is throughing below error message.
 
Can't open HCI socket.: Address family not supported by protocol

can you help me to solve this.

when i ran 

ps -Af | grep bluetooth 

which is something like ttyS0 bluetooth and at kernel level my driver exposing as something tty**.
how can i map this to correct one and how to solve this issue.

---

