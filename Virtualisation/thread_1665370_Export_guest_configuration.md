---
title: "Export guest configuration?"
date: 2011-01-12
forum: Virtualisation
---

### Post by ronni on 2011-01-12
Hi,

I have installed a lightweight GUI only to be able to configure Virtualbox guests; hardware, network etc.

Now, I have used almost the same configuration for my 3 guests. Is it possible, using the cmd-line to export the configuration of a guest and use as a template when creating new guests from the cmd-line?

By configuration I mean the network interface (bridged, NAT etc), chipset, if there should be a floppy and so on.

---

### Post by Garthhh on 2011-01-12
> **ronni said:**
> Hi,

I have installed a lightweight GUI only to be able to configure Virtualbox guests; hardware, network etc.

Now, I have used almost the same configuration for my 3 guests. Is it possible, using the cmd-line to export the configuration of a guest and use as a template when creating new guests from the cmd-line?

By configuration I mean the network interface (bridged, NAT etc), chipset, if there should be a floppy and so on.

I don't know about a commandline solution, but all the settings are in the .virtualbox folder
whatever you have named your vm with a vdi extension I have one named XP40g.vdi when you create a new machine 
when you get to the step labeled Virtual Hard Disk find the file of the VM you want to replicate choose it

---

### Post by ronni on 2011-01-13
> **Garthhh said:**
> I don't know about a commandline solution, but all the settings are in the .virtualbox folder
whatever you have named your vm with a vdi extension I have one named XP40g.vdi when you create a new machine 
when you get to the step labeled Virtual Hard Disk find the file of the VM you want to replicate choose it

As far as I know, and have done, the way you suggests only duplicates the harddrive, not the configuration of the VM. Correct me if I'm wrong, I'm still new to VB :)

But the reason I look for a cmd-line solution is so that I can remove the GUI.

---

### Post by Garthhh on 2011-01-13
> **ronni said:**
> As far as I know, and have done, the way you suggests only duplicates the harddrive, not the configuration of the VM. Correct me if I'm wrong, I'm still new to VB :)

But the reason I look for a cmd-line solution is so that I can remove the GUI.

I'm new to VB too
maybe some other resources?

you might try these guys
[http://linux.ittoolbox.com/groups/technical-functional/linuxadmin-l/](http://linux.ittoolbox.com/groups/technical-functional/linuxadmin-l/)
or of course
[http://forums.virtualbox.org/viewforum.php?f=1](http://forums.virtualbox.org/viewforum.php?f=1)

---

### Post by CharlesA on 2011-01-13
I've been using [phpvirtualbox]("http://code.google.com/p/phpvirtualbox/") for a while and really like it.

Note: You can forward X over SSH to access the VBox GUI without running a full GUI on the server. :)

As for your other question, I don't know. I tried creating a VM from the CLI before but it was more painful then I liked.

---

