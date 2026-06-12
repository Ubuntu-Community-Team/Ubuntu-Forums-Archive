---
title: "Can't start host"
date: 2011-06-18
forum: Virtualisation
---

### Post by ClientAlive on 2011-06-18
Edit: I made an error in the title of this thread. It's supposed to read "can't start _guest_" Sorry, guess I'm a little tired.


I have a virtual machine which disk is on my external hdd (don't ask - it's a horror show).

I have gone into settings > usb  and made sure "Enable USB" is ticked as well as setting a filter for my usb drive that has the disk on it. However, when I try to start the vm I get the following error:

```

FATAL: Could not read from the boot medium! System halted.

```

I've also tried to start it from the host command line using VBoxManage

```

VBoxManage startvm "HostClone"

```

("HostClone" is the name of my vm). It begins to start, just like when you do it through the Virtual Box front end, but I get the same result (error message above).

I though maybe I needed to install the guest additions (grabbing at straws - I know better). Since I knew I could not start the vm I knew I looked for a way to do it through the host command line. I found this [http://www.notesofasysadmin.com/unixlinux/installing-virtualbox-guest-additions-from-a-linux-host/](http://www.notesofasysadmin.com/unixlinux/installing-virtualbox-guest-additions-from-a-linux-host/)  article. It turns out the article is a bit dated and the VBoxManage commands are no longer the same. When I attempt to run the commands given in the article VBoxManage tells me . . .

```

Syntax error: Invalid parameter [command I had tried to use from the article]

```

On top of it all, starting the machine is just a means to an end anyhow. I'm trying to compact the disk so I can move it from the USB to my local hard drive. To do this I need to start the machine so I can install zerofree in it, zero out any free space, compact it, resize it to the size I actually want (10 gig - but it's 50 now) and then move the vdi to my local hard drive.

What can I do? This whole thing is turning into a total nightmare!

---

### Post by ClientAlive on 2011-06-18
> **ClientAlive said:**
> Edit: I made an error in the title of this thread. It's supposed to read "can't start _guest_" Sorry, guess I'm a little tired.


I have a virtual machine which disk is on my external hdd (don't ask - it's a horror show).

I have gone into settings > usb  and made sure "Enable USB" is ticked as well as setting a filter for my usb drive that has the disk on it. However, when I try to start the vm I get the following error:

```

FATAL: Could not read from the boot medium! System halted.

```

I've also tried to start it from the host command line using VBoxManage

```

VBoxManage startvm "HostClone"

```

("HostClone" is the name of my vm). It begins to start, just like when you do it through the Virtual Box front end, but I get the same result (error message above).

I though maybe I needed to install the guest additions (grabbing at straws - I know better). Since I knew I could not start the vm I knew I looked for a way to do it through the host command line. I found this [http://www.notesofasysadmin.com/unixlinux/installing-virtualbox-guest-additions-from-a-linux-host/](http://www.notesofasysadmin.com/unixlinux/installing-virtualbox-guest-additions-from-a-linux-host/)  article. It turns out the article is a bit dated and the VBoxManage commands are no longer the same. When I attempt to run the commands given in the article VBoxManage tells me . . .

```

Syntax error: Invalid parameter [command I had tried to use from the article]

```

On top of it all, starting the machine is just a means to an end anyhow. I'm trying to compact the disk so I can move it from the USB to my local hard drive. To do this I need to start the machine so I can install zerofree in it, zero out any free space, compact it, resize it to the size I actually want (10 gig - but it's 50 now) and then move the vdi to my local hard drive.

What can I do? This whole thing is turning into a total nightmare!

.

---

### Post by ClientAlive on 2011-06-25
Found out that what happened was the guest's vdi disk (hard disk) was somehow separated from the vm. While the vm was saved on my local drive the vdi was on the usb; and, for whatever reason, that just didn't work for the thing.

Got it all squared away now though.

Thanks

---

