---
title: "Installing VMware-Workstation-6.5.1-126130.x86_64.bundle"
date: 2009-02-12
forum: Virtualisation
---

### Post by pogoman on 2009-02-12
I'm trying to install VMware-Workstation-6.5.1-126130.x86_64.bundle. But I get the following error:
sh VMware-Workstation-6.5.1-126130.x86_64.bundle
Extracting VMware Installer...done.

(vmware-installer.py:6241): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(vmware-installer.py:6241): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Is this a bug or am i doing something wrong?

thx:confused:

---

### Post by darco on 2009-02-12
What is the command you are using to extract the .bundle?
I just installed the x64 myself recently....In my history it shows:

sudo sh VMware-Workstation-6.5.1-126130.x86_64.bundle


darco

---

### Post by pogoman on 2009-02-13
I have used the same command. I seems te be running. You can see the graff. interface. You can answer the eul etc.. But when you press the install button you get the error I described.
What I am forgetting to mention is that in the graphical interface I get the following message: You cannot install on a system with KVM enabled. So first i disabled KVM. That didn't work. Than I completely removed the directory and everything that revered to it.

---

