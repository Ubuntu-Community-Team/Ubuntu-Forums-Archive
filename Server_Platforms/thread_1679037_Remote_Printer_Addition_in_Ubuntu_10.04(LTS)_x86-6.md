---
title: "Remote Printer Addition in Ubuntu 10.04(LTS) x86-64"
date: 2011-01-31
forum: Server Platforms
---

### Post by ecampbell on 2011-01-31
I'm setting up a new server that is remote from me.  I need to establish a printer on this server that is managed by a Solaris 10 print server and I'm having trouble determining what the command line command would be to add this printer to the system.  Normally I would do "lpadmin -p <printer name on this system> -s<printer server host>!<printer name on printer server>.  These options aren't available on the cups lpadmin command.  Does anyone know the packages I need to have installed to make this work and also the command  to add this printer.

Thanks for the help.
Ed

---

### Post by perspectoff on 2011-01-31
What eventually becomes easier and the most reliable is to refer to printers by an IP address, not by name. (Naturally, your firewalls must not block access to the printer port anywhere along the way. One of my network printers uses, for example, port 9100).

All the network printers I use have a static IP address (which can be on the LAN network or on the WAN). When I set up a printer using CUPS, I set it up using the IP address of the remote printer, not the name. For example, I have a network printer at

socket://10.0.1.134:9100

If the printer is on your LAN (and your firewall is temporarily turned off), CUPS can actually find and install it for you automatically. (CUPS has improved tremendously the past year.)

Using names for printers is something Windows networking did/does and caused me endless headaches with my Windows networks for years.

---

### Post by ecampbell on 2011-01-31
I know I can add the printer as a networked printer, but I need to integrate my print request with request that come from many different sources into one print queue (Hence the solaris print server).  I may be missing something very basic but my experience is mostly in Unix Sys 5, Solaris and recently Linux.  I haven't as yet needed to set up printers on Linux.  I have searched the web but most  post I find are as yours.  I haven't found a solution where the printer is managed by a single host.

---

