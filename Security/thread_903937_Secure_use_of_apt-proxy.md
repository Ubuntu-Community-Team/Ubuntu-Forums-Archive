---
title: "Secure use of apt-proxy"
date: 2008-08-28
forum: Security
---

### Post by ekh on 2008-08-28
I will install a server tomorrow for serving my local net, not connected to the internet. It will be installed offline.

On my portable connected to the net, I have installed but not started apt-proxy.

I want to do an import of ubuntu repositories, but without any port opened as my portable is connected to the internet.

When the repositories has been imported, I then transfer a copy of the repositories to the local server and perform an update of the server.

Then I can configure the local workstations for updating from the local server.

My question is:

Is it possible to import the repositories without opening a port to the internet ?

Any experience with this ?

---

### Post by panhandle on 2008-08-28
Do you plan to use a router?

---

### Post by ekh on 2008-08-29
My net looks like this:

phone line <--> IP ADSL modem/router <--> WRT54GL <--> WRT54GL <--> portable

and my local net never connected to the internet:

Ubuntu server with repositories <--> router <--> workstations.

The repositories has to be carried from the portable to the server with an usb media.

I have no control over the IP ADSL modem/router.

The two Linksys WRT54GL V1.1 is both reprogrammed with DD-WRT 1.24 SP1

I guess I in some way can prevent the outside from accessing the open port from apt-proxy on my portable, but I have never tried it, so more reading, A tip is very welcome as this is not the only thing I have to learn about.

---

