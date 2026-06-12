---
title: "Virtualbox- shared folders (installed VB &amp; extensions from Oracle, in user group)"
date: 2012-01-27
forum: Virtualisation
---

### Post by Ms. Daisy on 2012-01-27
I can't get to a folder from my guest OS that I have shared on my Ubuntu host.  Here's what I've done:


[LIST=1]
[*]I had VB from the software center, so I removed it using sudo apt-get remove virtualbox.
[*]I used synaptic package manager to remove the guest additions.
[*]Downloaded Oracle VB version 4.1.8 from the website.
[*]Downloaded Oracle VB extensions version 4.1.8 from the website
[*]Installed both VB & the extensions.
[*]I opened my virtual machine, I see extensions 4.1.8 mounted on the guest desktop. For good measure I tried to "install guest additions" but nothing happened presumably because it's already installed.
[*]I added myself to the user group on the guest using sudo usermod -a -G vboxusers MsDaisy
[*]I installed samba on the host and shared the host folder. (because I was failing without it)
[*]On the host I logged off and logged back on.
[*]I went to Devices --> Shared folders in the guest OS and chose "Shared Folders", I see the  correct path to the folder that I want to share listed with full access & auto mount.
[/LIST]
That brings me to my question.  Where is the shared folder? I chose auto mount, so presumably that means it would automatically mount somewhere?  Where exactly does it mount? I cannot find it on the desktop, in the file system, or anywhere within the guest. Apparently I've configured something incorrectly. Anyone have a clue what that might be?

---

### Post by haqking on 2012-01-27
> **Ms. Daisy said:**
> I can't get to a folder from my guest OS that I have shared on my Ubuntu host.  Here's what I've done:


[LIST=1]
[*]I had VB from the software center, so I removed it using sudo apt-get remove virtualbox.
[*]I used synaptic package manager to remove the guest additions.
[*]Downloaded Oracle VB version 4.1.8 from the website.
[*]Downloaded Oracle VB extensions version 4.1.8 from the website
[*]Installed both VB & the extensions.
[*]I opened my virtual machine, I see extensions 4.1.8 mounted on the guest desktop. For good measure I tried to "install guest additions" but nothing happened presumably because it's already installed.
[*]I added myself to the user group on the host using sudo usermod -a -G vboxusers MsDaisy
[*]I installed samba on the host and shared the host folder. (because I was failing without it)
[*]On the host I logged off and logged back on.
[*]I went to Devices --> Shared folders in the guest OS and chose "Shared Folders", I see the  correct path to the folder that I want to share listed with full access & auto mount.
[/LIST]
That brings me to my question.  Where is the shared folder? I chose auto mount, so presumably that means it would automatically mount somewhere?  Where exactly does it mount? I cannot find it on the desktop, in the file system, or anywhere within the guest. Apparently I've configured something incorrectly. Anyone have a clue what that might be?

what is the guest OS ?

If it is windows then look in your network, windows explorer for a new drive letter or map a drive to it

here is a guide [http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by Ms. Daisy on 2012-01-27
Thanks. I missed the section on automatic mounting.

Just for future reference, it auto mounts the shared folder in ```
 /media/sf_myfiles
``` on linux guests.

---

