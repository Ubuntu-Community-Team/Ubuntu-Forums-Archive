---
title: "Unaccessible after Virtual Shutdown"
date: 2011-10-10
forum: Virtualisation
---

### Post by Haneef Mubarak on 2011-10-10
When I first found out about Ubuntu, approx. June 2011 (after looking at the downloads section for EvolutionRTS), I decided to run it  (Ubuntu) in a VM on my iMac. So therefore, utilizing VMWare Fusion, I made a VM of Ubuntu. However, after a while it froze and I killed VMWare's process for the iMac Terminal. Then when I restarted it, it would not function. After four months of being unable to access it (after trying nearly everything), I am willing to do nearly anything, because I have (non-sensitive) data on there that I don't want to lose. 

Since four months ago, I converted one of my computers into a server (*.haneefmubarak.com), running Ubuntu, of course. It's gone well, but now I need to retrieve my data from the VM and get it running again.

If necessary, I can make the VMWare Disk Image (.vmdk) file (~5GB) available for download from the Internet and give the passwords for my [virtual] system.

All help appreciated.

---

### Post by An Sanct on 2011-10-11
What do the VM logs say?

Where there any .lck or .vmem files left behind after the crash?

In my case, I had problems with VirtualBox (I guess your case is different), it messed up a simple configuration script after a small update. I got it fixed back by hand and it worked.

First check the logs for errors like "unable to find (filename)" etc.

PS. Before applying any suggestions me or anyone else will provide here, make sure to do a complete copy of all files and store them in a safe place, for safety :) sparing 5 to 7Gb should be no problem these days ;)

---

### Post by CharlesA on 2011-10-11
+1 to logs. Also what error is it giving you when you try to start the VM up?

---

### Post by An Sanct on 2011-10-11
> **CharlesA said:**
> +1 to logs. Also what error is it giving you when you try to start the VM up?

Note: try to start the VM up from a terminal (I guess, iMacs should have something like that too, since they are *nix)

---

### Post by Haneef Mubarak on 2011-10-11
#1 - No Logs. It does say no OS installed when I start it though.; I have backed it up on my server already. Did that first, actually.

#2 - The Virtual PXE BIOS say no OS installed. I already tried using the LiveCD image to get a session and reinstall GRUB, but no luck.

#3 - Been there, done that. It really doesn't make a difference though.

---

### Post by An Sanct on 2011-10-12
Please explain what #1 - #3 are supposed to represent.

We cannot help you if we have no info...

---

### Post by CharlesA on 2011-10-12
Why not just boot off a livecd and pull the data off the vhd?

---

### Post by Haneef Mubarak on 2011-10-13
Tried the LiveCD boot. Didn't work. IDK why.

1-3 represent the posts that replied to my message.

---

### Post by An Sanct on 2011-10-14
(1-3 ... I understand now ;))

How about creating another virtual machine and mounting the VHD to it as the second drive? This way, you will have access to it, as if it would be just another HDD in the machine (VM)

PS. Use a copy of the VHD ... of course!

---

### Post by CharlesA on 2011-10-14
> **An Sanct said:**
> (1-3 ... I understand now ;))

How about creating another virtual machine and mounting the VHD to it as the second drive? This way, you will have access to it, as if it would be just another HDD in the machine (VM)

PS. Use a copy of the VHD ... of course!
+1. This would probably be the best way to get the data off.

---

