---
title: "Vmware Server 1 refusing to boot virtual machine"
date: 2009-04-11
forum: Virtualisation
---

### Post by afrodeity on 2009-04-11
I have just upgraded from vmware player to vmware server 1.09, and it is running with the any any patch.However, I can't seem to get any of my virtual machines to boot. They played fine with the player, and I upgraded to get some networking capability, but no go. What am I missing? I know the company would like me to purchase the workstation, but I can't afford it, and some of the virtual machines won't play in Virtual Box either,so I need a vmware solution. Any clues?

---

### Post by dcstar on 2009-04-11
> **afrodeity said:**
> I have just upgraded from vmware player to vmware server 1.09, and it is running with the any any patch.However, I can't seem to get any of my virtual machines to boot. They played fine with the player, and I upgraded to get some networking capability, but no go. What am I missing? I know the company would like me to purchase the workstation, but I can't afford it, and some of the virtual machines won't play in Virtual Box either,so I need a vmware solution. Any clues?

Since you haven't provided any actual information as to **why** they won't boot, I will have to guess.

Change the following in the .vmx files:

```
virtualHW.version = "4"
```

---

### Post by afrodeity on 2009-04-12
> **dcstar said:**
> Since you haven't provided any actual information as to **why** they won't boot, I will have to guess.

Change the following in the .vmx files:

```
virtualHW.version = "4"
```

Nothing to change.

I tried this but also nothing.

```
config.version = "4"
```

---

### Post by afrodeity on 2009-04-12
I installed virt-manager and now vmware server 1 is refusing to budge. I tried opening the console and all it does is go through the motions of trying to start and then disappears. I uninstalled virt-manager but can't see how to uninstall its dependencies which might have clashed or something, because it was running fine last night. Oh bother. Why is this so complicated?

UPDATE: Okay this is what I love about Ubuntu. I started vmware in terminal and it told me what was wrong. It needed to be reconfigured for the system. It could be that somehow the configuration file got changed when I installed virt-manager. Will try this again to see if I can reproduce the bug.

---

### Post by afrodeity on 2009-04-15
Anyone know of a local ZA mirror for Vmware converter? I am having trouble downloading the 100mb file.

---

