---
title: "cant connect to guest console"
date: 2009-04-15
forum: Virtualisation
---

### Post by uopjohnson on 2009-04-15
I hosed up the network on one of my kvm guests so I can no longer connect to it via ssh.  Both the host and the guest are headless.  
ssh to the host and do:
```
virsh console guestname 
unable to open tty /dev/pts/2: No such file or directory
```
doesn't work.  
I tried hooking up a monitor to the host and running the same command it just sits forever, doesn't display anything.  

what do I do now?

---

### Post by uopjohnson on 2009-04-16
I feel like I tried everything to get this running until finally I started tryign things again and this time virt-viewer worked.  I don't know what I was doing wrong the first time.  Here is the command if anyone is looking.
```
virt-viewer -c qemu+ssh://host:sshport/system guest
```

---

