---
title: "Missing proxy settings can cause E: Unable to locate package ..."
date: 2010-11-03
forum: Virtualisation
---

### Post by GregoryJWolfe on 2010-11-03
I'm using Ubunto 10.10 inside of VirtualBox running on Windows XP behind my company's firewall. None of my web searches really helped resolve this issue, so I thought it was worth posting the solution.
 
In trying to install packages, **sudo apt-get install ...** failed consistently with **E: Unable to locate package xxx** with no other illuminating information. The problem was resolved by entering the required network proxy settings using **System->Administration->Synaptic Package Manager**, then **Settings->Preferences->Network**. I copied my proxy settings from **Internet Explorer->Tools->Internet Options->Connections->LAN Settings**; but you may need to get them from the equivalent dialogs in Firefox or from your system administrator.
 
Remember, Ubuntu inside VirtualBox has no knowledge of any proxy settings you may have set up in Windows.
 
While you're at it, you should also enter the proxy settings for Ubuntu Firefox.

---

### Post by dcstar on 2010-11-05
> **GregoryJWolfe said:**
> 
...........
Remember, Ubuntu inside VirtualBox has no knowledge of any proxy settings you may have set up in Windows.


VMs use the hardware of a host via the virtual interface manager, they do not use the configuration settings of the host.

You have to treat VMs as separate stand-alone systems because that is how they operate.

---

