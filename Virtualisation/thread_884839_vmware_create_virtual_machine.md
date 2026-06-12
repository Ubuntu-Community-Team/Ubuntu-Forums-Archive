---
title: "vmware create virtual machine"
date: 2008-08-09
forum: Virtualisation
---

### Post by Mr_Whippy on 2008-08-09
Hi all,

could do with some help here, I have installed vmware server on our server however i can not figure out how to create a machine and then access it to install the software on it. 

can anyone help please.

---

### Post by tamoneya on 2008-08-09
which version exactly of vmware server do you have.  Some of them do not allow you to make machines.

---

### Post by fjgaude on 2008-08-09
I take it you have no GUI menu from which to make a VM machine?

Looking at the man pages for vmware it would seem you can't make a VM from the command line... I could be wrong.

I think I am... try this simple command... from there you can see how to create a VM machine:

```
vmware help
```

Just like that, no dashes or anything else. Hope this solves your problem.

But do let us know how you are doing.

---

### Post by sndnichols on 2008-08-10
If you installed VM server on a server box that has no gui, you need to go to another machine and download vmware server console. Next you go to localhost:902. Tht should connect you to the server. VM ware server console alows you to build the VM's using many different confgurations. HTH

---

### Post by Mr_Whippy on 2008-08-11
Cheers all,

i will have a look tonight and get back to you all with how i get on, thanks very much.

---

### Post by Mr_Whippy on 2008-08-15
This problem is now fixed i reinstalled everything and got it to work 

thanks for your help

---

