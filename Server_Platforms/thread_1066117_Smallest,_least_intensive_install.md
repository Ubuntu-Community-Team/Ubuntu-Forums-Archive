---
title: "Smallest, least intensive install?"
date: 2009-02-10
forum: Server Platforms
---

### Post by Jamina1 on 2009-02-10
I'm looking to install a few virtual machines on a server, and I was wondering what the least memory intensive / space-hoggy install is that I can go for?

I don't need gnome as it will be doing command line stuff only.

The box in question has 2 gigs of ram and a dual-core 2ghz processor. I'm only looking to run 2 - 3 VMs on it, and 256mb for each is very reasonable. I guess I should also be asking what I should run as the base OS as well.

Should I install ubuntu server or is there a smaller option I should go for?

I prefer ubuntu or one of its variants as I am most familiar with its command line (and I know that I can install everything I need right off the bat without having to worry about source lists, yum, rpm or all that crap).

---

### Post by hictio on 2009-02-10
Perhaps a Server install with nothing on? Meaning that you skip the LAMP portion during the install.
But, what will those servers do? What will they serve? (webserver? file server? DNS?)

---

### Post by mansonthomas on 2009-02-10
I don't think there's smaller memory footprint in the ubuntu flavor.

I'm currently running a fresh ubuntu server in vmware (borne 1h ago), i've setup mysql server and bacula for test purpose and ssh server, I've allocated 512Mb of ram and it's currently using 235Mb.

So you can give more memory to each that 256.

If someone has to swap, I think it's better that the host system swap than the ubuntu swap inside inside a virtual drive...

Tip: you can copy and paste your first installed VM to create the two others...

Thomas.

---

### Post by jimv on 2009-02-10
EDIT

Correction, my server only takes up 90 mb right now with a default install and SSH, Apache2, Samba, and CUPS running.

---

### Post by shunthemask on 2009-02-11
Howdy,

you should consider installing [Ubuntu JeOS]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos"):

> Just enough OS for your virtual appliance

Ubuntu Server Edition JeOS (pronounced "Juice") is an efficient variant of our server operating system, configured specifically for virtual appliances. Currently available as a CD-Rom ISO for download, JeOS is a specialised installation of Ubuntu Server Edition with a tuned kernel that only contains the base elements needed to run within a virtualized environment.

According to the page referenced above, Ubuntu JeOS should be part of the standard 8.10 Server ISO.

---

### Post by Jamina1 on 2009-02-11
So.. wow, that's a really cool option I didn't know I had! Very very complicated and a teensy tiny bit over my head.. I'll try to work through it though.

So do I just install Ubuntu Server and run JeOS on top of it or can I run JeOS as the base OS as well? I don't need anything but SSH running the host OS, and the guests will be running various sorts of things.

---

### Post by gtdaqua on 2009-02-12
> **Jamina1 said:**
> So.. wow, that's a really cool option I didn't know I had! Very very complicated and a teensy tiny bit over my head.. I'll try to work through it though.

So do I just install Ubuntu Server and run JeOS on top of it or can I run JeOS as the base OS as well? I don't need anything but SSH running the host OS, and the guests will be running various sorts of things.

JeOS can't be the host. It's meant to be a VM so OEMS could add their product and make it a app specific OS. 

Virtualization needs several tools to be installed on the host. That itself defeats the purpose of JeOS. 

Ubuntu Server has a small foot print. Debian has an even smaller foot print and much more compact than Ubuntu. Also, no frequent updates on Debian which is one more advantage over Ubuntu.

---

