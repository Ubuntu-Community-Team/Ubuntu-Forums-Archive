---
title: "Virtual Box + DVD recognition."
date: 2010-10-05
forum: Virtualisation
---

### Post by Pengwyn44 on 2010-10-05
Virtual Box. Ubuntu 10.4 + Latest download from V. Box website.
All works well but for one problem. My DVD drive is correctly recognised by V.Box but is not attached to the Guest O.S. (Windows XP)
V.Box recognises the virtual hard drive and reports it as 'attached'. It recognises the DVD but reports it as "not attached'. My problem is, how do I attach it? I've read all the V. Box instructions,but I cannot find a reference to a difficulty.
Any help gratefully acknowledged.

---

### Post by scrooge_74 on 2010-10-05
You want to mount a disk right? On the top bar of the VBox window where your Guest OS is running you have some options including mounting the cd. 

Did you installed Guess additions?

---

### Post by Pengwyn44 on 2010-10-06
Thank you for showing me a menu that I had not noticed before.It shows the DVD drive as mounted. Yet in the VBox window it shows the virtual hard drive as "attached to XP" and the  DVD as "not attached". XP does recognise the dvd and will load some MS programs. However with some CD's Ubuntu grabs them first! I just assumed that the "not attached" was the problem.
No I have not the Guest Additions.

---

### Post by scrooge_74 on 2010-10-06
In the same menu it gives you the options to install the Guest Addition. That helps XP integrate better as a VM

---

### Post by Pengwyn44 on 2010-10-06
Many thanks for all your help. I will add the guest additions.

---

### Post by Pengwyn44 on 2010-10-13
Now sorry that I added the desk additions, they made things worse!
Currently Vbox does not support playing audio disks, so that may be the underlying problem.

---

### Post by scrooge_74 on 2010-10-13
> **Pengwyn44 said:**
> Now sorry that I added the desk additions, they made things worse!
Currently Vbox does not support playing audio disks, so that may be the underlying problem.

Check that your audio is enable under the VM and that nothing is using the audio in the Host OS

---

