---
title: "Linux and virtualisation: why are some distro's not working?"
date: 2016-01-28
forum: Virtualisation
---

### Post by Domie on 2016-01-28
I like Gnome 3. Many people left Gnome after 3 came out (Mate, Cinnamon, Unity,...) but I think it's fine working. I also like Ubuntu.It's community, the software center, the set-up,... So I certainly wanted UbuntuGnome as a distro.

I also have to use Windows for my work. I use specific software in which there is no valable Linux alternative and due to the very limited and underdeveloped target public there never will be. So I run VirtualBox and have some virtual machines running GNU/Linux. Gives me the chance to check out other distro's too, I even gave Gentoo and Linux from scratch a shot but I'm not that technically developped. :(

OK, UbuntuGnome works fine, but is enormously resource hungry after a while: it goes slow slow slow with over 2 GB of RAM consumed (3GB dedicated of 8G physically present) and 85% of processor capacity (AMD A10-6700). The only programs open are LibreOffice Calc, Firefox, a gnome-calculator and Terminator.

Other distro's are giving problems too. CentOS won't even install. Fedora did, but failed in the first attempt: I had to install KDE in stead of Gnome to make it work. Edubuntu: mouse did not respond. Debian: won't install.

There's only one distribution that works like a charm: Linux Mint, both Cinnamon and Mate. Cinnamon works very fast, although it's based on G3, so I assume my VM is "strong" enough to run Gnome 3.

When I let it boot from USB, UbuntuGnome is really fast and enjoyable. But I really need Windows and I need it very often, so dual boot is not an option, it has to be virtualisation. But I think it's very strange some distro's are not working properly or won't even install in VB, where others will. Especially LM Cinnamon and UbuntuGnome, who should share a lot of code, they react very different.

If someone had an explanation of this phenomenon: I'm very interested. Because although I like UbuntuGnome, I'm using Linux Mint now because it's not acceptable...

---

### Post by MAFoElffen on 2016-01-28
I guess a basic understand of hypervisors might explain what is happening. Since a detailed explanation could filled pages, I'll try to keep this just short enough to explain the whys.

A hypervisor (vitualisation hosting software) creates a virtual machine environment that simulates the hardware that a virtulised system will install onto and run on. Diiferent types of hyperviosrs do this in diffrent ways, dependining on their types, but basically, they use software and/or hardware hooks to simulate the hardware and BIOS of a basic system... but shields from the host system. The purpose of this is so if a guest system crashes, that it doesn't bring the host system down with it.

Two basic types of hypervisors. Type II creates te virtual environment, mostly through software virtualised devices.Soemthing running inside it see the virtual device, which is a simulated by software.This can take a lot of memory. Each time it tries to access a different device, the more resources it uses to keep up the illusion. 

Some modern type II hypervisors (VirtialBox, VMPlayer) take advantage of a CPU's vt-m (and equivalent) to use some of that to help with virtualisation.This makes things faster. But for that to be able to happen, the Host's CPU have that capability. Without that, you are limited to using 32bit guests.

Then enter type I hypervisors, like vSphere and KVM. For all intensive purposes, Hyper-V (which is really a hybrid). Think of them as bare-metal-like virtualisation. They are closer to running guests on iron. They use of lot of hardware virtualisation to support guests running on them. Doing it that way, they can better manage the resources they use, and better share the hosts resources. You can only do this with a CPU with virtual hardware capabilities (vt-m or equivalent).

On type I hypervisors, there is more flexibility on how you can configure the environment for the intended guest. I prefer KVM (on Ubuntu) but also have vSphere (on Ubuntu) and Hyper-V on Windows). I don't have problems installing most OS'es. Sometimes I have to tweak the environment, or the deives they say they have... but most are possible.

Under Windows, if you were using the Pro Version or higher of... then you are limited to hyper-v as a type I hypervisor. Cutting through the BS, there are some drwbacks. Liek MS'es other stragies, they assume that Windows and windows products are the only products that someone would use or need. If you install Hyper-V, it configures deep roots into the host environment. All type II hypervisors installed on the system will be affected, thnking that the system is now "without CPU virtualisation support." The performance on them after that will "suck."

There are things that you can do to help (tuning and other tweaks) with a type II hypervisor, but basically there is a limit to what you can do, just because of the framework that you are running the gust within. If you tried out running guests on a type I hyperviser, you would wonder what is wrong with other types... (I get spoiled). VirtualBox itself uses guest additions and the extension pack to try to help extend the capabilities and devices available to the guest environment.

So to answer the other question of why some do not work... following what was said above, the environment it sees (including devices) is not suitable for it to work. For instance, the Gnome3 desktop depends on 3D graphics capabilities in a GPU... But I can run it in type I hypervisors... with no tweaks.

I tried to be brief, but that is the short summarized version. Doe that explanation help?

---

