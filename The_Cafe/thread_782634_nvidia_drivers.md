---
title: "nvidia drivers"
date: 2008-05-05
forum: The Cafe
---

### Post by cb951303 on 2008-05-05
I remember using nvidia's installer some time ago. The installer was unable to find an appropriate module for my system and tried to recompile it from scratch. Does that mean the source code is encoded/encrypted in the *.run file provided by nvidia? or am I just being silly and misinterpreted what I have seen :)?

---

### Post by Joeb454 on 2008-05-05
You could try and open the .run file in a text editor and see what's there.

I would assume that it's protected somehow, as the normal nvidia drivers are proprietary

---

### Post by SupaSonic on 2008-05-05
I had seen .run files which were in essence tar archives. Maybe try to untar it?

---

### Post by Tuna-Fish on 2008-05-05
> **cb951303 said:**
> I remember using nvidia's installer some time ago. The installer was unable to find an appropriate module for my system and tried to recompile it from scratch. Does that mean the source code is encoded/encrypted in the *.run file provided by nvidia? or am I just being silly and misinterpreted what I have seen :)?

Yes, the source is there in some form. Only for the kernel module though, not the actual drivers.

I think the easiest way to see the source is just to temporarily replace /usr/bin/gcc with a program that writes all it's input to a file.

---

### Post by cb951303 on 2008-05-05
what do you mean not the actual source. isn't the module's source is the actual source?

---

### Post by Tuna-Fish on 2008-05-05
No. The drivers have 2 parts, the actual driver and the kernel interface. The driver is a binary blob in the package, while the interface is in source.

---

### Post by DoktorSeven on 2008-05-05
You can definitely extract the NVidia .run file (there's a commandline switch!) and view the code for the kernel module.  As others stated, though, that's not the main nvidia "driver", all the good parts are in the binary blobs installed on your system which the kernel module calls on.

---

