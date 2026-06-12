---
title: "Oracle Virtual Box 4.1.4 Freazing Ubuntu 11.10"
date: 2011-10-14
forum: Virtualisation
---

### Post by apt-get install help on 2011-10-14
Hi all

This is my first post on the forums. I have been using Ubuntu since version 10.10.

A few weeks ago when I has running 11.04 I started to have problems running Oracle Virtual Box 4.1.4, when running Windows 7 as a guest OS.

When I run Windows and start using iTunes or utorrent to download media after about 30-45 minutes of running the VM it suddenly freezes, but Ubuntu still runs as normal.

When I go to kill the VM in system monitor the processes tab displays this information about the Windows VM.

Process Name     Status           %CPU            Waiting Channel                      
VBoxSVC           Sleeping         0                  poll schedule timeout

VBoxXPCOMPIPCD Sleeping      0                  futex wait queue me

VirtualBox           Sleeping       100               futex wait queue me

I have tried to increase the RAM for the VM to the maximum that I can assign to the system, but that didn't solve the problem. I am running the latest version of Virtual Box with all the current extensions installed.

My PC System Spec

Memory 4 GiB
Processor Pentium(R) Dual-Core CPU E5300 @ 2.60GHz × 2 
OS Type Ubuntu 11.10 32Bit

Thanks :)

---

### Post by apt-get install help on 2011-10-17
> **apt-get install help said:**
> Hi all

This is my first post on the forums. I have been using Ubuntu since version 10.10.

A few weeks ago when I has running 11.04 I started to have problems running Oracle Virtual Box 4.1.4, when running Windows 7 as a guest OS.

When I run Windows and start using iTunes or utorrent to download media after about 30-45 minutes of running the VM it suddenly freezes, but Ubuntu still runs as normal.

When I go to kill the VM in system monitor the processes tab displays this information about the Windows VM.

Process Name     Status           %CPU            Waiting Channel                      
VBoxSVC           Sleeping         0                  poll schedule timeout

VBoxXPCOMPIPCD Sleeping      0                  futex wait queue me

VirtualBox           Sleeping       100               futex wait queue me

I have tried to increase the RAM for the VM to the maximum that I can assign to the system, but that didn't solve the problem. I am running the latest version of Virtual Box with all the current extensions installed.

My PC System Spec

Memory 4 GiB
Processor Pentium(R) Dual-Core CPU E5300 @ 2.60GHz × 2 
OS Type Ubuntu 11.10 32Bit

Thanks :)


Has anyone got any ideas about my freezing problem?

---

### Post by Dark Slipstream on 2011-11-17
I am having this problem now as well, same Host and Guest OS, only happens when running iTunes.

---

### Post by apt-get install help on 2012-02-09
> **Dark Slipstream said:**
> I am having this problem now as well, same Host and Guest OS, only happens when running iTunes.

It did a fresh Ubuntu install and it been working fine.

---

