---
title: "Laggy terminal - VirtualBox install"
date: 2022-03-15
forum: Virtualisation
---

### Post by fichte-fox on 2022-03-15
Host system: Core i5 12600KF, 32GB GDDR4 RAM, GTX 1070, 1TB NVMe SSD, Windows 11
Guest system: 4,096MB RAM, 4 Cores, 128MB video memory (max)

I installed Ubuntu, and noticed that the terminal was laggy. I wanted to try some different flavours anyway, so I tried Lubuntu and Xubuntu. Lubuntu's terminal was less laggy than Ubuntu or Xubuntu, but it was still a little laggy and I prefer everything else about Xubuntu. So, now I'm on Xubuntu, which still has the same laggy terminal issue as the Ubuntu Guest I installed originally.

Pretty much everything else runs smoothly in the environment. But the Terminal begins to lag the more I type. For instance, the first couple of words typed into the terminal are fine, but after then there's a slight delay between my keystroke and the letter appearing in the terminal window. This delay gets worse the more I've typed into the Terminal, even after a 'clear'. And it begins after only typing a few words or a couple of commands. It happens also when I type code into Vim. On the other hand, when I use Sublime to write code, there is no lag at all. There's no lag typing in Firefox or LibreWolf browsers, either.

What could be causing this Terminal lag and how can I fix it?

---

### Post by TheFu on 2022-03-15
Use a lite terminal, like a pure xterm, rather than a bloated gnome-terminal.
Also, if you just want a terminal into any Unix system, use the built-in ssh client from Windows to ssh into the system. 1000x better than running a full GUI.  I've never seen Win8+, but back in the Win7 days, we'd use putty.

BTW, there's little need to give a VM 4 cores unless you are doing geospacial work.  For a typical desktop or even software development, 1 vCPU is plenty.

If you want the system to be faster, you can also ensure that virtio storage and network controllers are used, not some emulated hardware. This applies to all virtual machines, BTW.

---

### Post by fichte-fox on 2022-03-15
> **TheFu said:**
> Use a lite terminal, like a pure xterm, rather than a bloated gnome-terminal.
Also, if you just want a terminal into any Unix system, use the built-in ssh client from Windows to ssh into the system. 1000x better than running a full GUI.  I've never seen Win8+, but back in the Win7 days, we'd use putty.

BTW, there's little need to give a VM 4 cores unless you are doing geospacial work.  For a typical desktop or even software development, 1 vCPU is plenty.

If you want the system to be faster, you can also ensure that virtio storage and network controllers are used, not some emulated hardware. This applies to all virtual machines, BTW.

Thanks for this! After some Googling I've set xterm to launch with Super+T (and enabled MetaSendEscape) and it's much better!

I'm starting to learn networking, and sites/courses seem to recommend installing linux virtual machines for that, so that's what I'm doing - I might also install it properly on another laptop or something, though, once I get used to it. The videos have also recommended I stick to using NAT so that the virtual machine's in a 'separate' network while I'm messing about/learning, so that the VM is completely sealed from the host. Would using Virtio storage and network controllers compromise that? If not, I'll definitely look into it.

My 12600K has 10 physical cores and 16 threads. On VBox it says I've given it "4/20" cores, so I'm assuming I've only given it two actual cores (i.e. 4 threads).

Thing is, Intel 12-series is using the new P-Core and E-Core mixed-core architecture, so I have no idea how the VM and linux are handling that. There should only be 16 threads (P-Cores are double-threaded, E-Cores are single-threaded), but it seems like it's recognising two threads for each E-Core, too. I wonder whether it's given it two E-Cores, two P-Cores, or some combination. Who knows? Haha

---

### Post by guiverc on 2022-03-15
Providing release details is always helpful.

You mention Ubuntu (*but not desktop or server*); then Xubuntu/Lubuntu but not release details.  When you're specific we can make assumptions as to what software stack you're actually using (eg. Ubuntu uses `gnome-terminal` for GUI/desktop, Xubuntu uses `xfce4-terminal`, and *modern *Lubuntu uses `qterminal`). Ubuntu releases are *year.month* in format so age of stack in use is pretty easy where release is known.

For Lubuntu the various releases have different *swap* defaults so is yours appropriate? (*I don't know what you're using as you've not said; but I often find changing swap is beneficial & ~mandatory for some releases*).  Being specific allows us to better respond.

---

### Post by ajgreeny on 2022-03-15
My hardware, an i5 3750K using the CPU graphics used to run Xubuntu each time a new LTS version appeared just for me to check its progress from one LTS to the next.

I usually gave the VMs 2 of the 4 cores available and 4G of my 8G ram and with thoe settings I never ever saw any terminal lag, not lag in any other application.
To be perfectly honest it was very difficult to see any difference in system speed between host and guest VM.

I'm sure I have read somewhere that there are some incompatibilities or problems with Linux and such new Intel-12 series CPUs but can't find anything now, but I wonder if your hardware is too new and recent for Linux, or perhaps for VBox itself, though why it should be just the terminal that lags in a VM is beyond me, and there is no way to test this now as I gave up using VBox about 18 months ago and now am using KVM/QEMU which is much smoother and faster in my experience.

---

### Post by fichte-fox on 2022-03-15
> **guiverc said:**
> Providing release details is always helpful.

You mention Ubuntu (*but not desktop or server*); then Xubuntu/Lubuntu but not release details.  When you're specific we can make assumptions as to what software stack you're actually using (eg. Ubuntu uses `gnome-terminal` for GUI/desktop, Xubuntu uses `xfce4-terminal`, and *modern *Lubuntu uses `qterminal`). Ubuntu releases are *year.month* in format so age of stack in use is pretty easy where release is known.

For Lubuntu the various releases have different *swap* defaults so is yours appropriate? (*I don't know what you're using as you've not said; but I often find changing swap is beneficial & ~mandatory for some releases*).  Being specific allows us to better respond.
Apologies, I should have included the release. The Ubuntu version is 20.04.4, and both Xubuntu and Lubuntu versions are 21.10. I chose the latest stable release for the latter two, and I can't remember whether I chose stable or LTS for Ubuntu. All GUIs etc are their defaults for those releases - I haven't changed anything, and I have apt updated/upgraded.

> **ajgreeny said:**
> My hardware, an i5 3750K using the CPU graphics used to run Xubuntu each time a new LTS version appeared just for me to check its progress from one LTS to the next.

I usually gave the VMs 2 of the 4 cores available and 4G of my 8G ram and with thoe settings I never ever saw any terminal lag, not lag in any other application.
To be perfectly honest it was very difficult to see any difference in system speed between host and guest VM.

I'm sure I have read somewhere that there are some incompatibilities or problems with Linux and such new Intel-12 series CPUs but can't find anything now, but I wonder if your hardware is too new and recent for Linux, or perhaps for VBox itself, though why it should be just the terminal that lags in a VM is beyond me, and there is no way to test this now as I gave up using VBox about 18 months ago and now am using KVM/QEMU which is much smoother and faster in my experience.

This is the only thing I could think of, too, that maybe it's either 12th Gen Intel, or Windows 11 (I realise most people are still using Win10) + VirtualBox shenanigans. I should say that there is slight lag in the desktop environment itself, too, e.g. dragging a selection box on the desktop has a little delay, and with pure Ubuntu the application animation (when they float up from the bottom left corner to show you the app grid) occasionally stuttered and faltered. But by-and-large other apps were completely okay - though I only tested FireFox, LibreWolf, Sublime, and the default notepad-esque text editor(s), whatever they are.

---

### Post by TheFu on 2022-03-15
> **fichte-fox said:**
> ..., so I'm assuming I've only given it two actual cores (i.e. 4 threads).
Virtualization CPU allocation doesn't actually work that way by default.  I've only seen specific CPUs pinned to a specific VM in extremely low-latency, real-time, VM deployments.  I have doubts that a toy hypervisor supports it.

> **fichte-fox said:**
> Thing is, Intel 12-series is using the new P-Core and E-Core mixed-core architecture, so I have no idea how the VM and linux are handling that. There should only be 16 threads (P-Cores are double-threaded, E-Cores are single-threaded), but it seems like it's recognising two threads for each E-Core, too. I wonder whether it's given it two E-Cores, two P-Cores, or some combination. Who knows? Haha

Don't assume that virtualbox knows anything about the CPUs, beyond which instructions they all support.

virtio is a device layer. It has nothing to do with network architecture. You can read more about how and what virtualbox supports in the online manual, chapter 6.  This comes up so often here, that I've memorized the chapter, though I stopped using virtualbox about a decade ago for an native linux enterprise hypervisor.

I suspect the real issue with the slow terminal is more about font handling between X11 and Windows, but I don't really know.  Running a full VM with a GUI just to have a terminal seems noobish.  If all you need is a terminal, run a server installation and ssh in. People have been remotely managing systems over this type of connection for 25 yrs around the world.  I've used it from 5 continents myself.  GUIs slow everything down and should be avoided if performance is your need.

One more idea. Run the VM full screen at the native resolution. I'd be surprised if the GUI performance didn't drastically improve.

> now am using KVM/QEMU which is much smoother and faster in my experience. 
I switched to KVM/qemu with libvirt initially around 2010, but the migration off Xen and virtualbox took about 18 months for all my VMs. Alas, if the host is Windows, there aren't many good choices for a hypervisor that are free.  Of the free choices, vbox is probably the best.  If you have $200, VMware Workstation is very nice, but beware that it delays support for the latest hardware and OS releases for months. During those delays, either odd behavior or it doesn't work are the usual outcomes.

For my 20 VMs, all under kvm these days, I default for Linux servers to 512MB of RAM and 1 vCPU.  A really heavy VM used 2 vCPUs and 4G of RAM.

For my desktop (20.04 server with fvwm as the window-manager) which also runs inside a KVM VM, I provide 1 vCPU and 4G of RAM. I find this the right mix of light, usable, and lacking of most bloat that all the DEs bring.  I'd never recommend fvwm to someone with less than a year Linux experience and probably only someone either using it on other Unix platforms or who has been running Linux at least 5 yrs would be interested.  LXQt and XFCE and the Mate DEs are each lighter than KDE or Gnome by a sufficient margin to be noticeable.

To see what any Linux system get for RAM+swap, use **free -hm** in a terminal.  To learn about the CPU(s), the **lscpu** command.
For example:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           3.9G        3.0G        359M        828K        485M        603M
Swap:          979M        152M        827M

$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             2
NUMA node(s):          1
Vendor ID:             AuthenticAMD
...
```
There are other tools/command that can capture lots of hardware and driver information. **inxi** is one. **lshw** is another. Neither of these are pre-installed, so I always install both packages on my systems BEFORE they are needed for troubleshooting any issues.  For example, the network summary:
```
$ inxi -N
Network:
  Device-1: Intel 82371AB/EB/MB PIIX4 ACPI type: network bridge 
  driver: piix4_smbus 
  Device-2: Red Hat Virtio network driver: [COLOR="#FF0000"]virtio-pci[/COLOR] 

```
See the virtio device and driver?

There are built-in commands to get information, but getting exactly what you'd like to see is less intuitive.  An example command with output:
```
$ lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
03:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
        Subsystem: ASUSTeK Computer Inc. I211 Gigabit Network Connection
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Memory at fc800000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at d000 [size=32]
        Memory at fc820000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: igb
        Kernel modules: igb

07:00.0 Ethernet controller: Intel Corporation 82575GB Gigabit Network Connection (rev 02)
        Subsystem: Intel Corporation Gigabit VT Quad Port Server Adapter
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at fc620000 (32-bit, non-prefetchable) [size=128K]
        Memory at fc400000 (32-bit, non-prefetchable) [size=2M]
        I/O ports at c020 [size=32]
        Memory at fc644000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: igb
        Kernel modules: igb
...

``` There are 3 more NICs in that box, so the output continues.
Hope that seeing a few commands helps a little. Of course, what is useful depends on your goals.  Admins need to know different things than developers, though there is some overlap.

---

### Post by slickymaster on 2022-03-16
Thread moved to **Virtualisation** for a better fit

---

### Post by ActionParsnip on 2022-03-16
Did you install the virtualbox guest additions?

---

### Post by TheFu on 2022-03-16
> **ActionParsnip said:**
> Did you install the virtualbox guest additions?

Excellent point!  That will make the graphics integration better.  Not all hypervisors have guest additions, BTW. Virtualbox, VMware desktop hypervisors do.

---

