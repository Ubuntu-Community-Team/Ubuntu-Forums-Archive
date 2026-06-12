---
title: "Ubuntu MID on KVM"
date: 2008-08-06
forum: Virtualisation
---

### Post by zaarch on 2008-08-06
I wanted to give the ubuntu MID a shot, downloaded the image from the site. After extracting, I now have a file root.qcow2. 

Not quite clear on how to use a qcow2 file specially with the virt-install method of creating vms.


Any words of wisdom ??

---

### Post by zaarch on 2008-08-07
no one...*sigh

---

### Post by jurrit on 2008-08-08
Didn't it supply you with a ubuntu.kvm file? If so, you can do this:

```
sh ubuntu.kvm
```

Otherwise you might try the following:

```
kvm -soundhw all -m 256 -hda root.qcow2 "$@"
```

You probably need to do the follwing first:

```
apt-get install kvm
```

---

### Post by zaarch on 2008-08-10
thanks jurrit..yeah i saw that.. and I do have KVM ..however..after doing that ..i am still unable to boot the vm..

granted that ..i have more experience with QEMU over ssh for making and managing vms..and also with virt-install 

however none with KVM....

once i actually create the vm runnning kvm prompt in the terminal..how do i boot the machine..and see the visual output

---

### Post by zaarch on 2008-08-11
see i can create VMs using the KVM from command line..
however since ...i have KVM installed on ubuntu server ed...hence no GUI ..therefore SDL cannot start..

of course i can always view the vm from a remote machine..there in lies the problem..

how do i know the ip of the machine so that i can use vnc to view..

ideas anyone ?

---

### Post by jurrit on 2008-08-20
> **zaarch said:**
> see i can create VMs using the KVM from command line..
however since ...i have KVM installed on ubuntu server ed...hence no GUI ..therefore SDL cannot start..

of course i can always view the vm from a remote machine..there in lies the problem..


You could try to start it with the following option -vnc :0
and connect to the ipaddress of your server with the remote desktop viewer?

---

