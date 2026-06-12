---
title: "How do I send the three-finger salute to winXP using kvm?"
date: 2009-07-17
forum: Virtualisation
---

### Post by Tomy on 2009-07-17
I am running kvm from the cli not virt-manager. I like it -- it works great -- I even have bridged networking. Thanks bodhi ):P

When I ctrl-alt-delete from my winXP guest I get the ubuntu shut-down-the-computer message box. How do I get the traditional micro$oft ctrl-alt-delete so I can kill the app that's already died?

Thanks

---

### Post by bodhi.zazen on 2009-07-17
Awesome :twisted:

hit ctrl-alt-2

This is a terminal that gives you access to the kvm hypervisor

type 
help
help sendkey

```
sendkey ctrl-alt-delete
```then hit ctl-alt-1 to return to your normal kvm interface.

---

### Post by Li1t on 2009-07-18
I'm running vmware on Win, so I'm not sure if the command will be exactly the same, but it offers a direct key-combo alternative to Ctrl-Alt-Del: **Ctrl-Alt-Backspace**

---

### Post by Deathshrimp316 on 2009-07-18
All ctrl-alt-backspace will do under Ubuntu is reset X, so it would be advisable to NOT try that key combination, because it will be Ubuntu you are giving the three finger salute to!

---

### Post by bodhi.zazen on 2009-07-18
> **Deathshrimp316 said:**
> All ctrl-alt-backspace will do under Ubuntu is reset X, so it would be advisable to NOT try that key combination, because it will be Ubuntu you are giving the three finger salute to!

Just FYI in many distros, Ubuntu included, that key combination has been disabled.

---

### Post by Tomy on 2009-07-18
Thanks bodhi, that works.

---

