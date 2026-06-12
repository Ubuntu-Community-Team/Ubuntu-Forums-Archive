---
title: "Running a VBOX inside a VBOX"
date: 2008-05-20
forum: Virtualisation
---

### Post by mcai8rw2 on 2008-05-20
Hello!

I've tried many different Virtualisation packages and innotek's (now 'sun') Virtualbox is by far my favourite tool.

I;ve got an XP host, running an UBUNTU guest os.

Now then... i've just installed Virtualbox on my Ubuntu Guest; to see if i can get a Virtual machine running INSIDE a virtual machine!

I wonder if anyone else has tried this... if so, what o/s (s) did you use.  And were they successful?

My troubles so far are that the second virtual box hangs on the "inode-cache hash table" part of the startup. I'm trying different distros to see if any of these solve the issue.. but so far 'nicht'.

So.. has anyone else had success in virutalisation of a virtual environment. I wonder how far one could concievably go!

thanks

---

### Post by stefangr1 on 2008-05-20
> **mcai8rw2 said:**
> Hello!

I've tried many different Virtualisation packages and innotek's (now 'sun') Virtualbox is by far my favourite tool.

I;ve got an XP host, running an UBUNTU guest os.

Now then... i've just installed Virtualbox on my Ubuntu Guest; to see if i can get a Virtual machine running INSIDE a virtual machine!

I wonder if anyone else has tried this... if so, what o/s (s) did you use.  And were they successful?

My troubles so far are that the second virtual box hangs on the "inode-cache hash table" part of the startup. I'm trying different distros to see if any of these solve the issue.. but so far 'nicht'.

So.. has anyone else had success in virutalisation of a virtual environment. I wonder how far one could concievably go!

thanks

If you do try this in vmware it just sais you can't run a virtual machine on a virtual host :)

---

### Post by mcai8rw2 on 2008-05-20
> **stefangr1 said:**
> If you do try this in vmware it just sais you can't run a virtual machine on a virtual host :)

i see... with Virtualbox, the 'livecd' mode actually starts to load successfully. (admittedly it breaks down after that)

But the fact that it STARTS kind of indicates to me that there is a way of making it FINISH too.

---

### Post by Skeet on 2008-05-20
I don't really see the point in it to be honest. If you want another virtual pc, just make another one in the Windows host. :confused:

---

### Post by -Rick- on 2008-05-20
I remember reading something about Qemu being able to do guest in guest virtualization.

---

