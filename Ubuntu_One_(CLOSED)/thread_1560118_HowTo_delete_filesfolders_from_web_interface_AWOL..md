---
title: "HowTo delete files/folders from web interface AWOL."
date: 2010-08-24
forum: Ubuntu One (CLOSED)
---

### Post by casbahdk on 2010-08-24
I have installed a new system on my desktop computer, and would now like to delete files/folders from the web interface, as they no longer reflect the files and folders on my desktop PC. I use my desktop PC to sync files and folders one way to my laptops.

---

### Post by afrowildo on 2010-08-26
It doesn't seem possible to delete folders via the Ubuntu One web interface. You can however just sign in to U1 on your new system, wait for the existing folders to sync onto the hard drive, then delete as appropriate and the changes will be mirrored on the U1 server.

---

### Post by casbahdk on 2010-08-26
Thanks for the reply. I thought of that also, but file contents have been changed on my new install and I am worried that I will end up with the old versions from my previous install. A rather drastic solution could be to delete my account and then create a new account, but I imagine that I won't be able to get my same user name again.

---

### Post by afrowildo on 2010-08-26
Could you move the new files out of the way, say to a flash drive or somewhere else in your home directory, while you delete the old one (after they sync), then move the new ones back into place?

---

### Post by casbahdk on 2010-08-27
I think this is probably more complicated than it would seem. I have been using my desktop computer as the point of reference for syncing my laptops. The new desktop installation is Peppermint Ice, a Lubuntu and Linux Mint derivative, using the LXDE desktop. Installing the Ubuntu One bits from the repos allows syncing from the Ubuntu One web interface to a laptop, but I am not sure how this will work when I don't want to sync from the Ubuntu One web interface to the desktop. Particularly, as I have yet to try to sync a file or folder from the LXDE desktop to the Ubuntu One server.

---

### Post by afrowildo on 2010-08-27
I've never tried to sync Ubuntu One on an LXDE desktop, but wouldn't it just be the same experience as doing so on Ubuntu? Ubuntu One is simply an application that directs your files to the appropriate server, and should be capable of running on your computer.

I can only advise you to isolate the up to date files somewhere safe and sync the contents of your Ubuntu One server to the hard drive. Once that's done, and everything's in sync, you can simply delete the old files and put the new ones in their place.

---

### Post by casbahdk on 2010-08-27
I can move or make a copy of my new files and file structure, but I still don't understand how syncing the old files and folders, and then replacing them with the new will sort out the problem with the old out of sync files on the Ubuntu One servers.  The new files and file structure will not be registered on the U1 servers and Ubuntu One will continue to sync the old versions. The root of the problem still seems to me to be the files and folders on the U1 servers that need to be expunged.

---

### Post by afrowildo on 2010-08-27
The deleting the files from your hard drive is what will delete the copies on the server. The server simply mirrors the activity on your hard drive. If you add a file or folder to your U1 folder, it will be synced to the server. If you go ahead and remove that file from your U1 folder, that change will be mirrored on the server.

---

### Post by casbahdk on 2010-08-28
OK, I'll give it a try and report back.

---

### Post by casbahdk on 2010-08-30
> **casbahdk said:**
> OK, I'll give it a try and report back.

Everything is installed, everything is working, so far with regards to syncing _from the cloud_ to my computer. Unfortunately there seems to be no obvious way to sync from my computer _to the cloud_ with a LXDE desktop (Lubuntu/Peppermint Ice). I have installed the cli tools for U1 as well, but haven't found a guide as to how to use them for syncing folders or files to the cloud.

---

### Post by casbahdk on 2010-08-30
> **afrowildo said:**
> The deleting the files from your hard drive is what will delete the copies on the server. The server simply mirrors the activity on your hard drive. If you add a file or folder to your U1 folder, it will be synced to the server. If you go ahead and remove that file from your U1 folder, that change will be mirrored on the server.

Thanks for hanging on :) I have selected specific folders in a file path. Those folders have all been changed in connection with my system reinstall. Those are the folders that I am now deleting, to make way for the new copies that I would like to sync with the cloud. In reality, at this point, it doesn't matter if the files are new or just haven't been uploaded to the cloud - the question is how to do that with the LXDE desktop?

---

