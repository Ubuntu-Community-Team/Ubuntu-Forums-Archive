---
title: "Two Ubuntu installations with same computer name"
date: 2010-08-17
forum: Ubuntu One (CLOSED)
---

### Post by ratcheer on 2010-08-17
My Ubuntu PC has two Ubuntu installations (Lucid and Maverick) in separate partitions. I gave both installations the same computer name.

Now, I have signed up for UbuntuOne and added my computer from the Maverick installation. I would like to add the Lucid installation to the account so I can sync some files between the two. However, I am concerned that if I add the same computer name, again, it will mess up the original one (or, make a huge mess of both).

So, my question is, do I need to give a different computer name to one or the other installations to add both to UbuntuOne, cleanly?

If the answer is, Yes, is there a way to rename the computer on an already installed Ubuntu system?

Thanks,
Tim

---

### Post by CharlesA on 2010-08-17
I don't know the answer, but to rename a computer, you edit /etc/hostname and /etc/hosts to the new hostname.

If you don't edit /etc/hosts, sudo will throw up errors.

---

### Post by ratcheer on 2010-08-17
Thank you. I will try this on the Mavarick installation, since it is the more disposable of the two, currently.

Tim

---

### Post by ratcheer on 2010-08-17
Thanks again - it worked like a charm. ):P

Tim

---

### Post by DarthScape on 2010-08-18
I have multiple computers with the same name, and they all work with ubuntu one. just lists them multiple times.

---

