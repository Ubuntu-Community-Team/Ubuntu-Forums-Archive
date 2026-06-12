---
title: "kernel driver not accessible in Virtualbox"
date: 2008-04-03
forum: Virtualisation
---

### Post by bcasanov on 2008-04-03
I am getting an error when trying to start a virtual machine of Kubuntu Hardy in Virtualbox: The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

What can I do about this?

---

### Post by bcasanov on 2008-04-03
I actually found out how to do this.  All I had to do was to add myself to the group vboxusers, and then it finally worked!!

---

### Post by zorkerz on 2008-05-19
Hmm this is not working for me. I have gone to system -> administration -> users and groups. Then the manage groups button and the vboxusers group is my bottom group. I checked both root and my user but im still getting the above error. 

I thought this worked more me in the past. Is there anything else i can try?

it works fine when i open in a terminal with sudo but i don't want to to that in the long run.

*** Update: After adding yourself to the vboxusers group as described above it is necessary to log out and the back in again.

---

### Post by pro003 on 2008-06-24
I'm gettin' this error msg too... I've added vboxuser group to the user and still same error pops up...

is there any workaround here about this... why is this topic / thraad abandoned?

---

### Post by joseelsegundo on 2008-06-26
Looks like a new kernel blew it up.  I ran VirtualBox as root and it gave me an error message in the terminal window saying that that there was not a kernel module available for the current kernel.  Then it said to re-compile the kernel module using:
```
sudo /etc/init.d/vboxdrv setup
```

That fixed things for me.  You may need to have build-essentials installed to do the compile.  I already had it so I'm not sure if it's necessary or not.

---

### Post by RobsterUK on 2008-07-15
I am also having the problem stated in the original post with virtualbox-ose

I checked I was in the vboxusers group, logged off and on again, even tried rebooting. Then re-installed virtualbox-ose and logged off and on again, still the same.

Any ideas?

---

### Post by greg0x01 on 2009-12-08
I had the same problem when changing to the OSE version.  In my case, the user was already in the vboxusers group, but the /dev/vboxdrv and /dev/vboxnetctl nodes had "root" as the group, not "vboxusers".  Once I changed the group for those nodes to "vboxusers" it worked fine.

---

