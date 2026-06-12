---
title: "noob vmware question - accessing guest OS"
date: 2009-05-15
forum: Virtualisation
---

### Post by maflynn on 2009-05-15
Sorry for the noob question but can I log into the guest OS via RDP instead of the console.  I start up the instance and I can click on the console tab and fire one up, but I was wondering if its possible with RDP.

I've tried using the IP address and name of the guest OS but in both cases nothing happens, I also tried using the -0 parameter to force it to use the console port.

I have yet to install vnc in the the guest os but I was hoping to use RDP - is this possible or should I just stick with the console interface?

---

### Post by dcstar on 2009-05-16
> **maflynn said:**
> Sorry for the noob question but can I log into the guest OS via RDP instead of the console.  I start up the instance and I can click on the console tab and fire one up, but I was wondering if its possible with RDP.

I've tried using the IP address and name of the guest OS but in both cases nothing happens, I also tried using the -0 parameter to force it to use the console port.

I have yet to install vnc in the the guest os but I was hoping to use RDP - is this possible or should I just stick with the console interface?

What guest?, what OS is it?

---

### Post by maflynn on 2009-05-16
Sorry for the omission.

I'm running kubuntu 9.04, loaded vmware server version 2, created a windows xp professional VM, made sure that terminal services were running within XP.  When I start KDE's RDP client and attempt to access the environment (after its up and running) I only get a blue screen in the RDP client window. No logon or password prompt, nothing. I tried expanding it to see if the logon/password prompt was hidden nada

---

### Post by HermanAB on 2009-05-16
RDP is the 'standard' way to use a Windows VM.  RDP runs on port 3389/TCP, but you can change a registry entry to make it listen on a different port - handy if you have multiple VMs.

The best tool to connect to RDP is 'rdesktop'.  I use it every day on multiple machines.

---

