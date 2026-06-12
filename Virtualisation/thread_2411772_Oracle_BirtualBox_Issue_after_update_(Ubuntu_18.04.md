---
title: "Oracle BirtualBox Issue after update (Ubuntu 18.04)"
date: 2019-02-03
forum: Virtualisation
---

### Post by rayfrommo on 2019-02-03
All,

Have run into an issue with Oracle VirtualBox that is new for me. Currently my OS is Ubuntu 18.04 and this started yesterday after allowing automated updates.

In the past, whenver there have been kernel updates, I had to reintiate machine owner keys to allow for UEFI working properly with VirtualBox. I followed the process that I have been doing in that for more than a year, but still could not initiate a virtual Windows session (or any other).

I was running VirtualBox 5.2 and also upgraded to 6.0 (after being unsuccessful at opening virtual OS's). No change in results and no error/abend messages to assist me here (will attempt to add debugging information if I am able to produce later today/tomoorow).

Symptoms are:

Oracle VirtualBox session manager starts
Attempting to start a virtual OS session initiates a new open window session, but stops at that point (window contents are all blank).
Unable to close either the new open window or VirtualBox Session manager
If a normal shutodwn of the machine is initiated (selecting power off graphically for Ubuntu), machine performs exit from the graphical environment, then displays kernel error messages and hangs.
Only option here is to manually power off with physical power key.

Will attempt to augment this post as I am able to tonight/tomorrow as I have other obligations that will consume my time for most/all of the rest of the day.

I know this also needs to be reported to launchpad and will do so after attempting to glean as much debug information as possible.

---

### Post by ajgreeny on 2019-02-03
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

Have you updated the Extension pack to the same version as you VBox install by downloading from [https://download.virtualbox.org/virtualbox/6.0.4/Oracle_VM_VirtualBox_Extension_Pack-6.0.4.vbox-extpack](https://download.virtualbox.org/virtualbox/6.0.4/Oracle_VM_VirtualBox_Extension_Pack-6.0.4.vbox-extpack)

You must do that for successful use of VBox.

---

