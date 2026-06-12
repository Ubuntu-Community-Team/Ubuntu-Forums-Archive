---
title: "Grub2 issue in vmware vsphere 4.1"
date: 2011-04-10
forum: Virtualisation
---

### Post by aink99 on 2011-04-10
Hi

I have an issue when enabling grub on vsphere 4.1 server for a Ubuntu 10.04 guest.

The screen stays dark instead of showing the usual menu for grub. After the time out of 

grub Ubuntu  boot without issue.

Any Ideas ?

---

### Post by drs305 on 2011-04-10
This combination in /etc/default/grub would produce that effect (any value for GRUB_HIDDEN_TIMEOUT):

> 
GRUB_HIDDEN_TIMEOUT="10"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="0"


To remove the hidden timeout, place a # symbol in front of the first line above. If you want a counter on a blank screen, change the second one to false. In either case, the last line will display the menu for X seconds (if not 0), either with or without a prior blank screen based on the other two entries.

That's the first thing I can think of to describe the behavior.

---

