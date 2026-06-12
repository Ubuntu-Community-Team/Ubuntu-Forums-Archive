---
title: "vboxusers group doesn't exist?"
date: 2010-09-27
forum: Virtualisation
---

### Post by memilanuk on 2010-09-27
Hello all,

Seems like one of the common things that people have problems with is not adding themselves to the vboxusers group so they can use USB, etc.  My problem is slightly different... running 10.04.1 LTS server, have virtualbox-ose installed (the default version available from the Ubuntu repositories)... and I can access/control the various commands like vboxmanage and vboxheadless and I am *not* in the vboxusers group... mainly cuz it doesn't exist, near as I can tell.

```
monte@vbox-server:~$ sudo adduser monte vboxusers
[sudo] password for monte:
adduser: The group `vboxusers' does not exist.
monte@vbox-server:~$

```

I ran into the same issue yesterday with the same machine, but with a Debian Lenny 5.06 install on it, using virtualbox-3.2.4 OSE from backports.  So I don't know if this comes from 'upstream', or what?

So... if there is no vboxusers group, what keeps any tom, **** or harry user from accessing/controlling/deleting the VMs?

TIA,

Monte

---

### Post by CharlesA on 2010-09-27
You would need shell access to delete/run the VMs. Unless you have a very lax security policy, you'll be fine.

I haven't added anyone to the vboxusers group either, since I have no idea why it's even created, or what it's purpose is. :|

Granted, I don't use USB in my VMs but I'm kinda curious why it is there.

Using the non free version btw, not OSE.

---

### Post by memilanuk on 2010-09-28
I was under the impression the vboxusers group was primarily to facilitate access to the USB devices since they would have to be mounted/unmounted, which normally takes elevated privileges.  For some reason I also thought it was used as a means of access control for who had the ability to start VMs and consume large amount of system resources...

---

### Post by CharlesA on 2010-09-28
> **memilanuk said:**
> I was under the impression the vboxusers group was primarily to facilitate access to the USB devices since they would have to be mounted/unmounted, which normally takes elevated privileges.  For some reason I also thought it was used as a means of access control for who had the ability to start VMs and consume large amount of system resources...

I just tried adding myself to the vboxusers group and seeing if a USB device (external hdd) would work. It didn't. I was testing with Ubuntu Desktop 10.04.1 with guest additions installed and the device didn't even show inside the VM.

If I moused over the USB icon at the bottom of the screen it said no USB devices were active. *shrugs*

Maybe there is something funky with my setup.

---

### Post by Matti L on 2010-09-30
Don't have vbox user group either but haven't had any problems. USB is not available in OSE version but is in PUEL (or something) as far as I know.

---

### Post by jabz on 2010-10-18
I am about to set up my Virtual Box right now. I was reading this thread for preparation purposes. :)

However, a few minutes before reading this thread I found a resource stating that "**the OSE version in ubuntu software center dones't have USB settings...**". This might be the reason why there is not vboxusers group. (I can't find it either).

Resource - VirtualBox USB fix for Ubuntu 10.04: [http://www.clearevo.com/blog/howto/2010/05/25/virtualbox_usb_fix_for_ubuntu_1004.html](http://www.clearevo.com/blog/howto/2010/05/25/virtualbox_usb_fix_for_ubuntu_1004.html)

Cheers.

---

### Post by jonobe on 2010-10-19
I have the same issue - no vboxusers group.

I am trying to make it possible for another user to access the guest OS I have on Vbox.  When they start up vbox, they don't have the guest OS I have as a choice on mine.

I presumed this was because they weren't a vboxuser, so off I went to Groups to add their name.  But no, no vboxusers group in sight.

Does anyone have any ideas how the other user can have access to the guest OS?:confused:

---

