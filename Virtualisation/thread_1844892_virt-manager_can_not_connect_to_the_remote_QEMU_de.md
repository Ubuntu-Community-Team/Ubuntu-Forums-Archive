---
title: "virt-manager can not connect to the remote QEMU demon"
date: 2011-09-15
forum: Virtualisation
---

### Post by xueliangfei on 2011-09-15
i can connect to the remote CentOS host which install the kvm+qemu  
**[SIZE=4]in the Ubuntu command line[/SIZE]** use the code
 
```
virsh -c qemu+ssh://*.*.*.*/system
```
 
(i have omit the IP)
 
**[SIZE=4]But in the virt-manager[/SIZE]**, i can not open the connection. and the error show as below:
[IMG]http://fmn.rrimg.com/fmn062/20110916/1015/p_large_6oKI_7c6f00009ad91210.jpg[/IMG]
 
i am sure i have done the described thing in the error.
what i can try to solve it?
any help is welcomed.........
thanks in advance......

---

### Post by xueliangfei on 2011-09-18
can anyone help me ?
Up  
Thanks in advance

---

### Post by Dangertux on 2011-09-18
If you have verified that libvrt-bin is installed, and your user's group membership is correct.

Did you edit the domain configuration manually? If you did you will have to force reload the domain. First stop the domain by doing this

```

virsh shutdown domain

```

then run the following.

```

virsh define /etc/libvirt/qemu/domain.xml

```

and restart the domain

```

virsh start domain

```

If that isn't the issue I highly recommend you double check your permissions and that you have all the necessary libraries installed.

---

### Post by xueliangfei on 2011-09-19
> **Dangertux said:**
> If you have verified that libvrt-bin is installed, and your user's group membership is correct.
 
Did you edit the domain configuration manually? If you did you will have to force reload the domain. First stop the domain by doing this
 
```

virsh shutdown domain

```
 
then run the following.
 
```

virsh define /etc/libvirt/qemu/domain.xml

```
 
and restart the domain
 
```

virsh start domain

```
 
If that isn't the issue I highly recommend you double check your permissions and that you have all the necessary libraries installed.
 
 
First  thank you very much
second i will introduce my situation
1   i have installed the libvirt-bin
2   i am sure the user is in the group of libvirtd
3   and i try your method above, but the situation is the same !
 
So , i do not know what i can do now.
why i can connect throw the command line but i can not by the virt-manager?
any help?
Thanks!

---

### Post by w4rren on 2011-09-19
I think this is the same problem as this user was having:
[http://ubuntuforums.org/showthread.php?t=1709702](http://ubuntuforums.org/showthread.php?t=1709702)

You could try some of the recommendations there but it doesn't seem like a complete solution was found to the problem, I'm afraid.

Hope you find a way around it.

---

### Post by xueliangfei on 2011-09-19
> **w4rren said:**
> I think this is the same problem as this user was having:
[http://ubuntuforums.org/showthread.php?t=1709702](http://ubuntuforums.org/showthread.php?t=1709702)
 
You could try some of the recommendations there but it doesn't seem like a complete solution was found to the problem, I'm afraid.
 
Hope you find a way around it.
 
 
i try it but the situation is still there  .
 
i do not know why the problem happens when using virt-manager but it s ok by command line

---

