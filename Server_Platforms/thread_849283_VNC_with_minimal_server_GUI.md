---
title: "VNC with minimal server GUI"
date: 2008-07-04
forum: Server Platforms
---

### Post by robgolding63 on 2008-07-04
Hi,

I have an Ubuntu 8.04 Server, and wish to VNC to it - but I only have xorg, gnome-core ubuntu-artwork installed (I just type startx if I need a GUI when logged into the command line).

This is for VMware Server Console - I'd like to access it from a computer without the console installed - so a GUI and some sort of remote control software (VNC) is required.

The reason I am having trouble I think is because I am not using GDM. Is there a howto or some tips I could use?

Thanks,

Rob

---

### Post by robgolding63 on 2008-07-04
I have managed to get Xvnc going through xinetd, but when I connect I just get the grey X-server screen with an X cursor. No terminal so I can't type startx.

What do I need to do next to get this working?

Thanks,

Rob

---

### Post by windependence on 2008-07-04
> **robgolding63 said:**
> Hi,

I have an Ubuntu 8.04 Server, and wish to VNC to it - but I only have xorg, gnome-core ubuntu-artwork installed (I just type startx if I need a GUI when logged into the command line).

This is for VMware Server Console - I'd like to access it from a computer without the console installed - so a GUI and some sort of remote control software (VNC) is required.

The reason I am having trouble I think is because I am not using GDM. Is there a howto or some tips I could use?

Thanks,

Rob

You don't need to do this. You have a few options. Install the VMware MUI first and then you can access the web interface at https:\\yourseveraddress:8333 OR just load the VMware Console software for windows on a windoze box and access it from there by IP address. You do not need a GUI on the VMware host at all. Also, you can start and stop and check status of your VMs from the command line as well.


-Tim

---

