---
title: "Running VirtualBox Windows 10 Guest on Ubuntu 16.04 Host"
date: 2016-05-18
forum: Virtualisation
---

### Post by wanderer3 on 2016-05-18
I have installed Windows 10 in VB 5 on Xenial. I have been unable to figure out how to share Ubuntu folders with the guest system or how to get it to access USB portals or the DVD drive. I did install Samba but can't set folder permissions to share , there doesn't seem to be an option to do this - am using Cinnamon Raspberry desktop. I have spent a lot of time getting nowhere with this. 

Virtualbox extension pack and guest additions are installed. I am perhaps asking a lot here but am truly stuck.

---

### Post by ajgreeny on 2016-05-18
You don't need samba as far as I'm aware.

You should be able to set up the sharing of folders from the VBox window.  Highlight the VM in the left hand pane and click on Settings in the toolbar at the top, then go to "Shared folders", navigate to the folder you want to share, set it to automount, and that should be all that is needed.

It certainly works that way for Windows XP which I still use occasionally. However, I have no idea if your problems are related to Windows 10 which so far I have not even seen in use, so I don't know where in the Windows 10 filesystem you would find the shared files and folders.

---

### Post by Habitual on 2016-05-18
I share out my $HOME directory using this

---

### Post by ajgreeny on 2016-05-18
I am assuming you are a member of the **vboxusers** group in your host Xenial OS.
If you're not sure use command **groups** in terminal and vboxusers should be included in the output.

---

### Post by wanderer3 on 2016-05-19
Thanks for all the replies. I have made some progress. The guest  additions once installed in the Guest Windows 10 OS as well as VirtualBox (not sure how this  activated, but I installed after a pop-up box appeared), allowed for  folder sharing between Xenial and Windows. The CD/DVD drive also became  available. Still haven't managed to access USB portals but can get by  for now by copying to a shared folder.

---

