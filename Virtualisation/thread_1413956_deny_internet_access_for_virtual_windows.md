---
title: "deny internet access for virtual windows"
date: 2010-02-23
forum: Virtualisation
---

### Post by Bear number one on 2010-02-23
Dual boot system Ubuntu and Vista.
I have installed virtualbox on Ubuntu and am running xp as the guest o/s.
I don't intend to allow xp to have internet access and am only using it to run a couple of programs that don't work too well under Wine.
I have created a shared folder to allow editing of text created in one of the programs.
What is the best way to ensure that xp does not have internet access and is it still necessary to run a firewall and antivirus on the guest o/s when internet access is denied?

---

### Post by byStanderone on 2010-02-23
...viruses and programs for xp will still execute although virtually and your xp programs can be compromised...you can disable windows networking also in its control panel, but the safest way of course is to disconnect your ubuntu network access. 

if you have an ubuntu firewall, i'd guess it would be redundant to have one in xp, but you can have one it you wanted to.

---

### Post by Bear number one on 2010-02-23
> **byStanderone said:**
> ...viruses and programs for xp will still execute although virtually and your xp programs can be compromised...you can disable windows networking also in its control panel, but the safest way of course is to disconnect your ubuntu network access. 

if you have an ubuntu firewall, i'd guess it would be redundant to have one in xp, but you can have one it you wanted to.

  Not sure that I fully understand your reply. My intention is to completely deny internet access for xp and keep only the two programs that I will be using. No other programs will be added. Could a virus be passed onto the virtual xp via Ubuntu? I have currently configured virtualbox to the option 'host only adapter', would I still need to disable windows networking.........

---

### Post by Bachstelze on 2010-02-23
If your XP virtual machine has its network configured as Host-Only, it does not have Internet access. That's what Host-Only means: the virtual machine can only communicate with the host, not with the outside world.

---

### Post by mkvnmtr on 2010-02-23
In Virtual Box when you look under network you can disable the nat connection. I am sure on the other virtual programs there is a similar feature.

---

### Post by Bear number one on 2010-02-23
> **Bachstelze said:**
> If your XP virtual machine has its network configured as Host-Only, it does not have Internet access. That's what Host-Only means: the virtual machine can only communicate with the host, not with the outside world.

 Thanks, now I know I've got that bit right, I had tested internet access with the browser but wasn't totally convinced. So the final question is do I need any windows security to run the virtual xp in this way bearing in mind that I will not be adding further programs to the install, could a virus still find it's way via Ubuntu?

---

