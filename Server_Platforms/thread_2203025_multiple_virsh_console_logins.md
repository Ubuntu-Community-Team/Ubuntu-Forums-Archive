---
title: "multiple virsh console logins"
date: 2014-02-01
forum: Server Platforms
---

### Post by nerdtron on 2014-02-01
I get a weird behavior when I use use virsh console to access a virtual machine.
Say I have a virtual machine.
```

nerdtron@kvmhost:~$ virsh list
 Id Name                 State
----------------------------------
 31 template             running

```
So I go ahead and access its console since it doesn't have any network interfaces configured yet, I won't be able to use ssh.
```
nerdtron@kvmhost:~$ virsh console template
Connected to domain template
Escape character is ^]
[    0.189353] serial82
Ubuntu 12.04.2 LTS ubuntu12042 ttyS0

ubuntu12042 login: user
password:


```

Looks good so far.
The problem occurs when another user also tries to login using virsh console on the same virtual machine. I thought we would have two different console sessions on the virtual machine but it doesn't appear to be the case. Anything he types on the second virsh console window appears on my virsh console windows. Even key press like the enter key will make my console enter to the new line.
Virsh console with multiple sessions doesn't work or is this really by design? Any help would be much appreciated.

---

### Post by Doug S on 2014-02-01
If you do not specify an alternate console in the command line then the primary will be opened (see "man virsh"). What the alternate names are or how to create them, I don't know. Myself, I have never been able to make console connections work at all.

---

### Post by nerdtron on 2014-02-01
```
virsh console template *_[device]_* 
```

I forgot to say I also tried that after reading the man virsh. I tried almost everything like /dev/ttyS1, /dev/pts/3, etc and it always returns to an error that it can't read the device.

I'm not sure if my syntax is wrong for the device? Any way to make it work?

---

### Post by nerdtron on 2014-02-10
I'm going to bump this.

Anyone has a solution or is mutiple virsh console login working properly on your end?

---

