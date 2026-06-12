---
title: "virsh console problem"
date: 2011-06-21
forum: Virtualisation
---

### Post by kostasps on 2011-06-21
Hi all! 
absolute beginner in the forum.
I'm trying to use kvm-qemu in ubuntu 11.04.
I managed to create a VM using ubuntu-vm-builder and list it in virsh dump its xml 
and most importantly gat a console of it through virtual manager.

what i didn't manage to do (and is actually my problem) is get its console through 
'virsh console' command.
the line ii get is

error: internal error cannot find character device (null)

if anyone needs more info please post the command and i'll respond with the output

thanks in advance

---

### Post by diepes on 2011-07-01
I have the same problem.
$ virsh console jabber
Connected to domain jabber
Escape character is ^]
error: internal error cannot find character device (null)

---

### Post by chaolinyu@gmail.com on 2011-12-15
exactly the same problem....

---

### Post by rockballad on 2012-03-07
I have the same problem.
```

$ virsh -c 'qemu:///system' console control-test

Connected to domain control-test
Escape character is ^]
error: internal error cannot find character device (null)
```

Please help us.

Thanks so much.

---

