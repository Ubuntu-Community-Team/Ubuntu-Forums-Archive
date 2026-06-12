---
title: "Dual Xeon machine freezing"
date: 2005-07-01
forum: Server Platforms
---

### Post by Zinkeldonk on 2005-07-01
I read the postings related to the Poweredge machine freezing and I have a similar problem.

I run a lab with 40 machines - all thin clients. The server is a dual processor P4 Xeon 2.4GHz beastie. It has 4BG RAM, 2 x 1Gb/s network ports.

I installed the kernel 2.6.11-1-686-smp to make use of the 4Gb RAM. Problem now is that the machine kernel panics. It was running fine using Fedora Core 1, but I wanted to make a change to Ubuntu. With the original kernel that cmae with Hoary (386) it can only see 1Gb RAM, which is not sufficient for the 40 thin clients.

It also seems that as soon as I do a startx (the Ubuntu Gnome desktop) this prompts the panic. If I don't do this, it is likely to panic at ANY point.

Wondered if anyone has any pearls of wisdom for me.

Kindest.
H

---

### Post by LordHunter317 on 2005-07-01
Hrm.  Sounds like the provided Ubuntu kernels are buggy.

As a good test, if you have the skills, I would try this:[list=1][*]Download the vanilla 2.6.11 kernel sources from kernel.org or a mirror[*]Unpack them[*]Copy the Ubuntu kernel configuration to .config in the kernel source tree[*]Run make oldconfig, which should import that configuration.  This may fail as Ubuntu has lots of patches that aren't in vanilla, but I believe it should be smart enough to ignore what it doesn't understand.[*]Build a kernel and install it.  You can download the kernel-package package if you want to be able to build a debian package to make installation easy.  Or you can do it by hand.[*]Run that kernel, and see if the behavior continues.  That helps ioslate to a bug in Ubuntu's patches/build process  or a bug in the kernel source proper.[/list]FWIW, I've been running 2.6.11 on a AMD64 SMP box for sometime without issues.  Debian sources though.  However, Ubuntu's patches over and above are mostly wireless cards and some other small things.  Though, one of the many extra ACPI patches could being doing it.

---

### Post by subterrific on 2005-07-01
As a general rule of thumb, you should see if there are any BIOS updates available for the machine. I had a lot of trouble with a desktop system that would work fine with the 386 kernel, but crash with the 686-smp kernel. A BIOS update fixed the problem. I had similar issues with RAM not working in an Athlon64 system that was fixed with a BIOS update.

---

### Post by sesstreets on 2005-07-01
I dont want to sound like a complete moron...but if you can get a dual xeon beast of a machine, why dont you use redhat ce?

---

### Post by Zinkeldonk on 2005-07-02
Why not RedHat  [-X ? No reason really. Just costs too much. This is an NGO who had to fight tooth-n-nail for this machine in the first place. Not sure they will want to spend more dosh on RedHat. Anyhow, I am a Debian fan, and South African - hence Ubuntu.

Thanks for the BIOS tip. Seemed to be running fine on Fedora though, so wonder why BIOS gremlin did not show up there.

Finally. Recompile the kernel. Now that is well within my capabilities and in fact it was what I was thinking of doing if this did not sort itself out (I know you're thinking "These things don't just '*sort themselves out*'" - I think that too). My only problem with this is that I thought these kernels that are shipped via the package repository are tested and work. To find that a pre-compiled kernel does not work it a bit of a wake-up call.

Thanks for the input anyhow.

Cheers
Zd

---

### Post by LordHunter317 on 2005-07-02
FWIW, I've had all sorts of issues with Ubuntu shipped kernels I haven't had with Debian ones, specifically a rash of XFS corruption in warty that hit several people I know.

I'm not sure it's just the kernel, but the kernel in combinations with some userspace patch exercising a bug.  Because I couldn't reproduce the behaviors by using a Ubuntu kernel with a debian userspace, which I found quite odd.

I think recompiling would be a good exercise, as much as I wouldn't normally recommend it.  I just see stability issues here I don't see in Debian.  I still never found a root cause though.

---

