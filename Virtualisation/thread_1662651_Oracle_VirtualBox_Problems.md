---
title: "Oracle VirtualBox Problems"
date: 2011-01-08
forum: Virtualisation
---

### Post by throese on 2011-01-08
I have the Ubuntu Desktop CD in my CD-Drive, but when I hit "Start" in VB I get this (View Attachment):

How can I fix it?

It only started happening today, after I used the update manager to update my laptop earlier this morning.

---

### Post by karthick87 on 2011-01-08
Run the following in ur terminal,

```
sudo aptitude install virtualbox-ose-modules-generic
```

---

### Post by dino99 on 2011-01-08
is DKMS installed ?

note: if you previously had an oldish virtualbox installed, you need to remove/purge it first with synaptic

---

### Post by dino99 on 2011-01-08
> **karthick87 said:**
> Run the following in ur terminal,

```
sudo aptitude install virtualbox-ose-modules-generic
```

virtualbox-ose is not an ORACLE built, dont insert confusion if you dont know.

---

### Post by CharlesA on 2011-01-08
Is that VirtualBox 4?

Have you run the command it suggested?

---

### Post by throese on 2011-01-08
I've tried and all it gives me are different options like:

start, stop, restart, etc etc, but idk what option to pick. Why did it start having this problem?

Update: I uninstalled Oracle Vbox 4.0, put OSE on, then removed OSE and put Oracle 4.0 back on. When I did that, I didn't have the /etc/init.d/vboxdrv, but I did have an /etc/init.d/vboxdrv.dpkg-bak, I ran it in the Terminal and now Oracle Vb 4.0 works again.

One last question: How do I get USB devices to work on Oracle VB 4.0 on Linux? I know how to make it work on Windows, but not Linux.

---

### Post by CharlesA on 2011-01-08
If it's the same as VBox 3.2, you need to have yourself added to the vboxusers group.

---

### Post by throese on 2011-01-09
Thanks everyone, it works like it's supposed to now! =D

---

