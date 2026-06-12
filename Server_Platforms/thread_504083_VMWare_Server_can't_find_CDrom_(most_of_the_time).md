---
title: "VMWare Server can't find CDrom (most of the time)"
date: 2007-07-18
forum: Server Platforms
---

### Post by twistedtwig on 2007-07-18
Hi all,

I have just installed VMWare Server onto Feisty from this [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")

link.

but when ever I try and boot it up I ever get a message NTLDR is missing or it will start to boot then say it can not contact the CDROM.  I have set the CDrom as the first boot but can not figure out what is going wrong.

can anyone help me please?

Thanks

---

### Post by twistedtwig on 2007-07-19
I can not get anything but NTLDR (NT boot loader fingy) now... I have tried all the config settings I can think of :(

---

### Post by crush304 on 2007-07-19
is the cd mounted on the host, I don't know if it is a problem or not but you might try to make sure it is unmounted before booting the guest

what happens if you use an iso image instead of the physical drive?

---

### Post by twistedtwig on 2007-07-20
I uninstalled it all and started again and it all worked this time :)

but thank you

---

