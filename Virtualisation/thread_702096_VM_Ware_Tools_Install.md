---
title: "VM Ware Tools Install"
date: 2008-02-19
forum: Virtualisation
---

### Post by RealG187 on 2008-02-19
When I go into VMware and tell it to install VMWare tools it mounts the CD for the install. I have the OS set to Ubuntu. However it appears it uses the same image for every Linux. I have a tar.gz and an RPM.

I know minimal about tar.gz and lots about DEB. I converted the RPM to a DEB and installed the DEB. However it says VMWare tools is **not** installed.

I see it made folders but I don’t know how to run the program.

So will this happen if I do the tar.gz method?

I don’t know how to do tar.gz when I asked once they said to tell them what I was trying to insrtall (before it was just Ace of Penguins which I got a DEB for, I still had trouble running the games, they didn’t appear in the menu, I figured I would have to run the command "ace_pegged" or something like that or make a shortcut.) But now I am saying I want to install this.

---

### Post by optimizer on 2008-02-20
Tools install instructions
[http://kb.vmware.com/selfservice/dynamickc.do?externalId=340&sliceId=2&command=show&forward=nonthreadedKC&kcId=340](http://kb.vmware.com/selfservice/dynamickc.do?externalId=340&sliceId=2&command=show&forward=nonthreadedKC&kcId=340)

---

### Post by RealG187 on 2008-03-18
Well I could find Ubuntu there, but I found this page:

[http://ubuntu-tutorials.com/2007/10/02/how-to-install-vmware-tools-on-ubuntu-guests/](http://ubuntu-tutorials.com/2007/10/02/how-to-install-vmware-tools-on-ubuntu-guests/)

Basically type:
```

    sudo aptitude update

    sudo aptitude install build-essential linux-headers-$(uname -r)

    cp -a /media/cdrom/VMwareTools* /tmp/

    cd /tmp/

    tar -vxzf VMwareTools*.gz

    cd vmware-tools-distrib/

    sudo ./vmware-install.pl
```

I modified it a bit, after it said cd /tmp/ and then cd vmware-tools-distrib it said directory not found, so I just extracted the tar.zg to the desktop and modified the cd command to /home/[MPG]("http://bestwikiever.wikidot.com/MPG")/Desktop instead of /tmp/

I can drag files into the VM and it captures the mouse.

I cannot drag out cuz it says the host doesnt support symbolic links, so I guess that's a Vista problem.

The screen rel does not resize like in Windows when I got from Windows to full screen, but I dont think the Linux tools does that!

UPDATE: About the symbolic links thing, I tried again a second and third time and it worked, so that only happened the first time, the second time it said the file existed (as I copied the file from my desktop into the VM, so copying the same file out to the same place will do that), the third time I renamed the file in the VM and dragged it out!

---

