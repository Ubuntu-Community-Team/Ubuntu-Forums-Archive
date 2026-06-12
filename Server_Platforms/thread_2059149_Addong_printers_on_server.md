---
title: "Addong printers on server"
date: 2012-09-17
forum: Server Platforms
---

### Post by bouzzi on 2012-09-17
I'm looking for a way to add printers to my server using command line methode.

to be able to script printer installation

So far I have find this instruction:

lpadmin -p b0542 -E -v lpd://10.1.205.81/b0542

What should I add to this line to set the driver : Generic text-only printer ?

What should I add to this line to set the location of the printer?

Thank you !

bouzzi

---

### Post by Jorel on 2012-09-22
Hi,

Have you tried installing CUPS? in my experience it is much easier to add printers with it.

# sudo apt-get install cups

---

