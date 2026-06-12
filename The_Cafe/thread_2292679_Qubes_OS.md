---
title: "Qubes OS"
date: 2015-08-30
forum: The Cafe
---

### Post by Welly Wu on 2015-08-30
1. [https://www.qubes-os.org/](https://www.qubes-os.org/)

So, I decided to download and install Qubes OS 3.0 rc2 using VMWare Workstation 12 Pro and it installed successfully. I have my own serious doubts about this software project. Information Assurance is about protecting the confidentiality, integrity, and availability of the data itself. There are three methods:

1. Security through obscurity: use less common hardware and software to achieve security
2. Security through correctness: use perfect software code and do regular and rigorous software code audits to discover and patch flaws if necessary
3. Security through isolation: use hardware and software that is separate from production systems so if an attacker or attack vector penetrates and compromises only virtualized, compartmentalized, containers, sandboxes, etc. to minimize damage to the desktop operating system, user accounts, and data

The reason why Qubes OS is incomplete in terms of providing strong security is that it currently occupies the first principle because it is relatively unknown and obscure software code and it prioritizes the third principle while de-emphasizing the second principle. Look, this is a software project that is slowly developing and iterating because the Invisible Things Labs is a very small company with a very small staff with an unknown budget that is also probably much smaller than Apple, Google, and Microsoft. There have been regular patches and updates to the software code over time and there will continue to be more in the future. You can not achieve robust security by emphasizing the third principle and reducing the importance of the first two principles. The other major gripe that I have with Qubes OS 3.0 rc2 is that it is glaciar slow in terms of its active software development cycle, but I can't fault ITL because they are such a small company with very limited resources. It tries to be mostly compliant with POSIX and mostly compatible with the Linux kernel, but it succeed in being neither here or there. What ITL is creating is its own Xen distribution that will be a mess to manage in the long term future if they decide to switch to an Ubuntu GNU/Linux based distribution. Oh, did they mention that they are targeting Microsoft Windows 7 to be compatible in disposable VMs? Microsoft Corporation ended mainstream consumer support for that so yeah. This software project has had numerous delays and setbacks in the past that it makes Steam early access PC games look like all of them are on time and under budget all of the time.

Right now, it's coin toss as to whether a traditional GNU/Linux distribution or Qubes OS is supposedly more "secure" or whatever that term connotes. It has the feel of a perpetual startup company as its endgame strategy. I don't mean to sound critical or harsh, but you would be a fool to trust Qubes OS at its current stage of development with your most secret private user data without first educating yourself about information assurance.

Give it a try if you feel that you must scratch an itch. When you want your Preparation H, don't come yelling at me.

Remember, the Linux kernel is not invincible. It is not perfect and free of all forms of defects currently available in this world. Neither is Xen Type 1 hypervisor. That's the Achilles' heel of free, libre, open source software. Once you publish it to the world, anyone can read your source code and find bugs, vulnerabilities, active exploits, and attack vectors while you run around like a dog chasing its own tail trying to fix the damage done during a Nation State sponsored attack on your systems.

I still trust Green Hills Software Integrity 178B or DO-178B.

---

### Post by Welly Wu on 2015-08-30
Out of all of the different desktop operating systems that I tried this week, Qubes OS is the most severe in terms of its basic PC hardware requirements. First, I could not meet all of them. I use VMWare Workstation 12 Pro 64 bit GNU/Linux version when Qubes OS specifically warns against using it inside a Type 2 hosted virtual machine manager and it should be installed bare metal directly on the desktop or notebook PC. Second, I don't have enough available disk space on either of my Crucial solid state disks to test it out so I installed it on my Western Digital Black desktop hard disk drive.

Another thing that should be noted is that creating multiple disposable virtual machines is rather resource consuming. You have to read the user manual to understand what specific type of disposable VM you want to create for an intended purpose and getting it confused can lead to a security breach across different active VMs. The methodology of copying, cutting, and pasting information and data among active VMs is a bit cumbersome and automatically mounting internal and external disk drives requires opening the terminal and typing in the mount command for the dom-0. Joanna and her team are working on automatic or manual mounting of disk drives in the latest release candidate, but it is not as functional as expected with most modern GNU/Linux distributions. The other problem is that very little work has been accomplished toward the capability of creating Microsoft Windows 7 disposable VMs that are fully functional. At this time, Windows 7 is quite dated, but it is still supported with an extended service contract through Microsoft Corporation. It's sad to see that Windows 8.1 and 10 are not yet supported and no plans to support them are coming soon. By the way, this is a proprietary feature that is separate from Qubes-OS and ITL may charge money for this capability. UEFI and Secure Boot are not yet supported which is a real bummer considering that most modern desktop and notebook PCs support these features. Finally, no word has been announced about switching from Red Hat Fedora to Ubuntu in the near future yet. This is the major reason why I don't like Qubes OS. I prefer Ubuntu over Fedora. I know how to use Debian, Ubuntu, and Red Hat very well, but my personal preference is for Debian or Ubuntu.

The other thing to note is that iteration is slow and very minor. Each alpha, beta, and release candidate only tests small changes in the source code to identify and quash specific bugs with no major features announced until the next major release version. This is disappointing as well as I think it amounts to lost opportunities.

---

