---
title: "VIrtualbox images on separate drive"
date: 2009-12-21
forum: Virtualisation
---

### Post by joker535 on 2009-12-21
I am in the process of building a dual quad xeon machine to run ubuntu server 64bit that has enough resources to run the host OS plus 6 virtual machines concurrently.

I have been researching some options and it was suggested to me that the I/O to the machines hard drive(s) would be very intensive and would slow the host considerably. I was thinking about using a small SSD for the host OS and storing all the Vbox images on a second drive or array. This would separate the host OS I/O and the guest I/O between different drives on different channels.

Is there any reason not to do this?

Is this difficult to do?

Thanks

Bob

---

### Post by bluelamp999 on 2009-12-21
Absolutely no reason not to do so IMO, it's always recommended to run your VMs on a separate spindle if possible.

It's very easy to do, I run all my VMs on an external drive.

Good luck!

---

### Post by sanemanmad on 2009-12-21
All i did was make a user (virtadmin) and made that users home directory (/mnt/otherdisk) example. then just su - virtadmin, then when you create the vm it should be created and ran from the otherdisk. Of course i am not running a GUI so this is all command line

---

