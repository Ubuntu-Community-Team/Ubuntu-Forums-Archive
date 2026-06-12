---
title: "Ubuntu Upgrade to KVM Server"
date: 2018-09-25
forum: Virtualisation
---

### Post by way-hap on 2018-09-25
[FONT=century gothic][/FONT]Hi,

Firstly I am not an Ubuntu expert and therfore not a KVM wiz either.


I have inherited a standalone physical server that is running Ubuntu 16.10 (EOL) that runs KVM with a few Virtual machines runnin on it. I need to upgrade Ubuntu to 18.04.01 LTS and I am wondering what is the best way to do this upgrade and migrate the VMs. 


Note: I have 1 of these KVM servers at each DC and will need to upgrade both eventually. The hardware is compatible with Ubuntu 18.04LTS


The images and backups of the VMs are on NFS mounts contained on centralised storage arrays.


Has anyone done this lately. If you have a plan that you followed I would appreciate if you could share it with me. 


My question are:
If i shutdown the VMs, dismount the NFS shares and then do a clean install of Ubuntu 18.04LTS will I be able to use the old VMs/images in the new version of Ubuntu/KVM? I realise i will need to setup the network configs and local user accounts again. 


Or is it better to follow the upgrade path (16.10 --> 16.04 --> 17.10 --> 18.04) in order to re-use the VMs again. 


Any help would be much appreciated. Thanks in advance.

---

### Post by TheFu on 2018-09-25
If this is a business, you should test the new version of KVM with the existing VMs well before any upgrade attempts.
For Linux VMs, I've never had issues moving from KVM host to KVM host even with version changes.  
For Windows VMs, I've been burned a few times.  Windows doesn't like when the virtual motherboard changes and either refuses to boot or complains loudly. Had to call MSFT to get a fresh reactivation key.

I wouldn't do any upgrade. I'd load either 16.04 or 18.04, setup KVM on those and move the VMs over.  If forced to do this today, I wouldn't touch 18.04.  For my needs, it isn't ready for production use.  Just look through these forums for all the 18.04 issues.  I can't remember an LTS with so many problems.

---

