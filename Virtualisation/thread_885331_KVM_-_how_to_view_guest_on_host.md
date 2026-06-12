---
title: "KVM - how to view guest on host"
date: 2008-08-10
forum: Virtualisation
---

### Post by satimis on 2008-08-10
Hi folks,


Ubuntu 8.04 desktop amd64
KVM


On host terminal I can create guest .img and start it.  

Create guest .img```

# qemu-img create -f qcow2 guest.img 10G

# kvm -hda guest.img -cdrom /dev/scd0 -m 512 -vnc :0

```


Start guest.img```

# kvm guest.img -vnc :0

```


But I can't view/operate guest on host.  I must run vncviewer on remote machine terminal;

$ vncview 192.168.0.110:0


to view and operate the guest.  192.168.0.110 is host local IP address.



Please advise how to view and operate guest on host.  TIA


B.R.
satimis

---

### Post by ktulu73 on 2008-08-10
You can run the vm without the vnc option, the vm then run in a sdl window.

But it make not really a sense, that the vnc connection on remote host work, but not on local host.

---

### Post by satimis on 2008-08-10
> **ktulu73 said:**
> You can run the vm without the vnc option, the vm then run in a sdl window.

But it make not really a sense, that the vnc connection on remote host work, but not on local host.
Hi ktulu73,


Thanks for your advice.  I got it.


How to adjust the geometry of the sdl window making it bigger to read?


Besides I have Vista installed as guest runnig following commands;```

# qemu-img create -f qcow2 vista.img 10G
# kvm vista.img -cdrom /dev/scd0 -m 1024 -boot d -vnc :0

```
Vista starts finally.


However each starting vista I have to insert its installer on cdrom and run;
# kvm vista.img -cdrom /dev/scd0 -m 1024 -boot d 

again.  Otherwise it only starts rescue mode.


Advice would be appreciated.  TIA


Edit:

Re vncviewer:

After installing xtightvncviewer addtional to tightvnc-server and tightvnc-java run;

$ vncviewer localhost


Then the viewer starts connnecting the guest.



B.R.
satimis

---

### Post by forrestxm on 2009-08-27
I met similar problem, but my kvm is 72, and on ubuntu hardy 8.04.3. The bridge network does not work in guest system. Why?

I also searched web, no useful answers to my problem.

So could anyone ubuntu super guy answer our questions? Thanks a lot!

---

