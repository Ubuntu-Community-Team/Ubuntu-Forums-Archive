---
title: "Manage AD domain"
date: 2007-10-17
forum: Server Platforms
---

### Post by svalding on 2007-10-17
I hate Windows. Unfortunately, my place of employment enjoys the chaos of running 50 Windows servers. 

That being said, I would like to manage said servers from my ubuntu machine. (I dual boot at the moment to use Windows Admin tools on Active Directory).

If I could find a nice AD manager that is open source and can run on linux, and manage AD, I could move to Ubuntu permanently, and the world would be a wonderful place for me. 

Does anyone know of anything like that?

---

### Post by rickyjones on 2007-10-17
> **svalding said:**
> I hate Windows. Unfortunately, my place of employment enjoys the chaos of running 50 Windows servers. 

That being said, I would like to manage said servers from my ubuntu machine. (I dual boot at the moment to use Windows Admin tools on Active Directory).

If I could find a nice AD manager that is open source and can run on linux, and manage AD, I could move to Ubuntu permanently, and the world would be a wonderful place for me. 

Does anyone know of anything like that?

As far as I know there are none. I see two options (and I do both at my place of employment):

1) Remote Desktop: use terminal services on one of the Windows servers and use that server to administer AD.
2) Use VMWare or VirtualBox and install Windows there. Join it to the domain and use that to administer the AD.

Hope this helps!

-Richard

---

### Post by svalding on 2007-10-17
Yes, those are both viable options, but as some point I have to "touch" the windows machine. I want some sort of GUI or something that I can install into ubuntu and configure to work like active directory does. 

I know it's possible. My university has a web front end they wrote in java so regional campuses can manage their computers in the AD, which is housed at the main campus.

---

### Post by rickyjones on 2007-10-17
If there is then I'm not sure of what it is. Good luck in your quest!

For the sake of asking though, why does it seem like touching a Windows system is so deplorable to you?

Thanks,

-Richard

---

### Post by svalding on 2007-10-17
Eh, it's not deplorable. I just like Linux way more than Windows. And if I don't have to have a virtual machine running, all the better. Just cuts down on nonsense, and is purely preference!

---

### Post by Mavtech on 2007-10-17
I use Ubuntu on my work computer and manage quite a few servers and also the AD console.  I use the Linux version of Citrix to connect to a Metaframe server to access the AD Console.  So, if you have Metaframe, use that.  Otherwise, I think your only other option is to use RDP (Terminal Services on Ubuntu).  This is what I use to manage all the print servers.

---

### Post by rickyjones on 2007-10-17
> **svalding said:**
> Eh, it's not deplorable. I just like Linux way more than Windows. And if I don't have to have a virtual machine running, all the better. Just cuts down on nonsense, and is purely preference!

Fair enough :). It'd be nice if Microsoft released something similar to the MMC for Linux... ah, to dream!

-Richard

---

### Post by netlogic on 2007-10-17
> **rickyjones said:**
> If there is then I'm not sure of what it is. Good luck in your quest!

For the sake of asking though, why does it seem like touching a Windows system is so deplorable to you?

Thanks,

-Richard

The simple answers are security, reboots, working on a slimmer and simpler OS, and registry. People have gave MS 12 years to fix these problems. I think people are sick of waiting. Another thing, MS doesn't listen to their customers. They dictate what customers should use. Smaller guys are desperate for an attention, so they will listen.

---

### Post by HermanAB on 2007-10-17
One word: rdesktop

Remember to make frequent backups.

---

