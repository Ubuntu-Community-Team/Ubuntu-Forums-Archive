---
title: "Snapshot Snafu"
date: 2009-04-02
forum: Virtualisation
---

### Post by itendo on 2009-04-02
Client: VirtualBox PUEL 2.1
Host: Ubuntu Intrepid Ibex 8.1 | Guest: Windows XP SP3

I am running into an issue that is not uncommon with users of vb, but i am having an issue finding an explanation of the reason. >> i got my guest up and running, took snapshot 1. >>got some programs installed, took snapshot 2. switched monitors, tweaked UI, enabled <guest additions>* and powered down before saving snapshot 3. (*probably where the problem occurred)

received the following error when trying to boot the machine:
> Unable to restore the virtual machine's saved state from '/home/[USERNAME]/.VirtualBox/Machines/[VMNAME]/Snapshots/{227a3841-1ffc-4a67-85e0-a02481db0922}.sav'. It may be damaged or from an older version of VirtualBox. Please discard the saved state before starting the virtual machine (VERR_SSM_LOAD_CONFIG_MISMATCH).
*[NAME]=truncated

I have seen a few possible fixes, and havent had a chance to try them out. (the first seems to be to change network card type to "PCNet-Fast III" based on [this post at vbox]("http://vbox.innotek.de/pipermail/vbox-trac/2008-September/011119.html").)

however, i am trying to find the underlying cause behind this problem. this is my virst VM and use of VB, and i am becoming concerned about updates and how they proceed and before i do a ton of tweaking, i want to make sure i have my nuts and bolts on tight before a the new kernel comes along and i end up with virtual shrapnel.

---

