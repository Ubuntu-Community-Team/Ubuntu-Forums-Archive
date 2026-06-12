---
title: "What should I use?"
date: 2010-03-23
forum: Virtualisation
---

### Post by SuperMiguel on 2010-03-23
So i trying to study for few ms certifications, and i have a ubuntu server, that i want to run few vms on.. This machine doesnt have a monitor so what ever i install needs to be manage by a mac running osx... 

I want something like esxi, that i can manage from another system and i can create, and view a console of the system... The problem with esxi is that the client is windows only.

Also keep in mind that some of this machines wont be connected to the internet, or will be on a network by them self so i cant rdp directly to the vms...

I was thinking that i could just rdp to the ubuntu server and use virtualbox but not sure how slow it will be... What do you guys suggest?

---

### Post by SuperMiguel on 2010-03-23
bump

---

### Post by codfather on 2010-03-23
You have several options.

1) If the server has VT extensions with the processor then just use KVM. You can manage it via just an ssh session, so OSX will give you that. If you install vnc, you could also use X to manage the VM's with virt-manager

2) Use Vmware server, again you manage it via the command line from OSX, or you can manage it via the provided web interface. It's not the best but would work fine.

3) As you have mentioned Virtualbox will work in the same way as above, and again you could use the GUI tools with vnc nad ssh.

4) You could use iESX , as it also supports an ssh interface, so you don't have to use the windows GUI client if you don't want to. If you did want to use the windows GUI, then just install Virtualbox on your OSX machine, and use a virtual windows machine to manage the virtual server.

hth

Nick

---

### Post by doas777 on 2010-03-23
well, my answer may be a little differant from others, but my recomendation is to set up your "server" with a desktop distro with a monitor attached, and then install freenx. after that you can remove the monitor, and connect back to the server over nx. then just install virtualbox, and your vms

---

### Post by SuperMiguel on 2010-03-23
so this system has 16gb and a dual core e5300 no VT supported... (i can upgrade to a VT enabled cpu if needed) how important is the cpu when running vms? ill be running multiple 2003 servers, doing very basic AD, DNS, and RRAS

btw how is freenx compared with vnc?

---

### Post by codfather on 2010-03-23
If you can get easily CPU's with VT extensions , then definitely fit them as all of the main Tier1 virtualization hypervisors will use that capability , as will most of the Tier2 ones now, including Virtualbox and VMware.

Nick

---

### Post by bodhi.zazen on 2010-03-23
Personally I would use either KVM or Virtualbox and manage the guests via ssh.

VirtManager can be forwarded to your mac via ssh -X.

Both KVM and VirtualBox can be managed from the command line.

If you want a graphical interface, there are several web based interfaces, personally I like Proxmox :

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

---

### Post by doas777 on 2010-03-23
> **SuperMiguel said:**
> so this system has 16gb and a dual core e5300 no VT supported... (i can upgrade to a VT enabled cpu if needed) how important is the cpu when running vms? ill be running multiple 2003 servers, doing very basic AD, DNS, and RRAS

btw how is freenx compared with vnc?
if you have more than one VM, then the VT will probably be important.

---

### Post by SuperMiguel on 2010-03-23
> **doas777 said:**
> if you have more than one VM, then the VT will probably be important.

and dual vs quad? does it matter much for my purpuse?

---

### Post by doas777 on 2010-03-23
> **SuperMiguel said:**
> and dual vs quad? does it matter much for my purpuse?
that depends entirely on your workload and the threading model for your apps. a single threaded app will run relentlessly on a single core, never touching the other.
in an ideal world you would want as many cores as vm's so that they can each be guaranteed one core/cpu at all times.

---

### Post by SuperMiguel on 2010-03-23
> **bodhi.zazen said:**
> Personally I would use either KVM or Virtualbox and manage the guests via ssh.

VirtManager can be forwarded to your mac via ssh -X.

Both KVM and VirtualBox can be managed from the command line.

If you want a graphical interface, there are several web based interfaces, personally I like Proxmox :

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

i can run the vbox gui using ssh -x? and the virtual machine will show on my host?

---

### Post by doas777 on 2010-03-23
> **SuperMiguel said:**
> i can run the vbox gui using ssh -x? and the virtual machine will show on my host?
don't know for sure about ssh -X, but it shoudl probably work. if not, freenx will. it's ssh based so just as secure.

---

### Post by bodhi.zazen on 2010-03-23
> **SuperMiguel said:**
> i can run the vbox gui using ssh -x? and the virtual machine will show on my host?

I am not sure about VirtualBox. Worse case scenario you would VNC into the guest.

I use KVM , and you most certainly can manage your machines with ssh 

[http://virt-manager.et.redhat.com/page/RemoteSSH](http://virt-manager.et.redhat.com/page/RemoteSSH)

> The quick and easy way to manage virtual machines remotely is to  leverage SSH. In essence the libvirt management connection will be  securely tunnelled over an SSH connection. All the authentication is  done using SSH keys and passwords/passphrases are gathered by your local  SSH agent. **In addition the VNC console for each guest virtual machine  will be tunnelled over SSH**. 

Emphasis added by myself, but we are talking Virt-manager here, a graphical front end to kvm ...

[http://virt-manager.et.redhat.com/screenshots.html](http://virt-manager.et.redhat.com/screenshots.html)

Virt-manager is in the Ubuntu repositories.

And proxmox . Proxmox gives you a web based graphical application to manage your guests, including VNC if you wish.

---

### Post by SuperMiguel on 2010-03-23
> **bodhi.zazen said:**
> I am not sure about VirtualBox. Worse case scenario you would VNC into the guest.

I use KVM , and you most certainly can manage your machines with ssh 

[http://virt-manager.et.redhat.com/page/RemoteSSH](http://virt-manager.et.redhat.com/page/RemoteSSH)



Emphasis added by myself, but we are talking Virt-manager here, a graphical front end to kvm ...

[http://virt-manager.et.redhat.com/screenshots.html](http://virt-manager.et.redhat.com/screenshots.html)

Virt-manager is in the Ubuntu repositories.

And proxmox . Proxmox gives you a web based graphical application to manage your guests, including VNC if you wish.

and to use KVM i need a VT enabled cpu right?

---

### Post by bodhi.zazen on 2010-03-23
> **SuperMiguel said:**
> and to use KVM i need a VT enabled cpu right?

For KVM yes. Are you sure your CPU is not capable ?

I would use Virtualbox before buying a new CPU.

And honestly it does not matter, use bridged networking, then ssh or VNC into the guest.

---

### Post by SuperMiguel on 2010-03-23
bodhi on your you use debian or ubuntu?

---

### Post by bodhi.zazen on 2010-03-23
> **SuperMiguel said:**
> bodhi on your you use debian or ubuntu?

Debian (Proxmox) and Fedora.

---

### Post by SuperMiguel on 2010-03-23
will try using vbox and see how it goes...

---

### Post by SuperMiguel on 2010-03-23
got it working.. kinda slow while running vnc and gnome :( tried running using fluxbox and slowish too.. any idea on what else i should try?

---

### Post by bodhi.zazen on 2010-03-24
ssh -X and forward only the applications you need rather then the entire desktop.

---

### Post by SuperMiguel on 2010-03-24
> **bodhi.zazen said:**
> ssh -X and forward only the applications you need rather then the entire desktop.

do i need to install ssh -X? when i type ssh -X says not valid

---

### Post by bodhi.zazen on 2010-03-24
> **SuperMiguel said:**
> do i need to install ssh -X? when i type ssh -X says not valid

[http://www.sfsu.edu/~helpdesk/ssh/ssh_osx/ssh_osx.htm](http://www.sfsu.edu/~helpdesk/ssh/ssh_osx/ssh_osx.htm)

---

### Post by SuperMiguel on 2010-03-24
i know how to ssh, i just dont know how the ssh -x works... after i ssh into my server how do i open a x windows?

---

### Post by SuperMiguel on 2010-03-24
i did this: [http://www.ssh.com/support/documentation/online/ssh/adminguide/32/X11_Forwarding.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/32/X11_Forwarding.html)

but when i type something like clock & i get Error: Can't open display:


Solution: in apple instead of ssh -x is ssh -y :)

ssh x11 seems to works good :) video is kinda slow sometimes.. :(

---

### Post by bodhi.zazen on 2010-03-24
it is ssh -X with a BIG X and not ssh -x with a small x

in your ssh session you simply start an application and the output is forwarded to your desktop.

You may need to edit /etc/ssh/sshd_config to allow X forwarding.

[http://www.techotopia.com/index.php/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29](http://www.techotopia.com/index.php/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29)

---

### Post by SuperMiguel on 2010-03-24
> **bodhi.zazen said:**
> it is ssh -X with a BIG X and not ssh -x with a small x

in your ssh session you simply start an application and the output is forwarded to your desktop.

You may need to edit /etc/ssh/sshd_config to allow X forwarding.

[http://www.techotopia.com/index.php/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29](http://www.techotopia.com/index.php/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29)

i got it to work.. but is kinda slow :(

one runs fie but for example when i run 3 at the same time i think my cpu suffers :(
[IMG]http://img651.imageshack.us/img651/1460/screenshot20100324at306.png[/IMG]

---

### Post by TheFu on 2010-03-24
I can't believe I'm gonna say this ... especially in this forum.

1) Swap that CPU for one with VT-x support ASAP. Do it. Do it now. 4 Cores is better than 2 when it comes to running multiple VMS. A Core i5-750 would be my cheap desktop choice, but that would probably mean swapping a motherboard too. A C2Q would be my next level down if you need to stay with a 775 board. [http://www.cpubenchmark.net/cpu_list.php](http://www.cpubenchmark.net/cpu_list.php) may be helpful.

2) Run ESXi as your hypervisor. In my experience with Xen, KVM, VirtualBox and ESX/ESXi, it is the fastest, easiest to get up and running for Microsoft-based OSes. It also works for other OSes, like Ubuntu Desktop and/or Ubuntu Server. I've run Windows Servers 2003/2008, WindowsXP, Windows7, Ubuntu Server x64, OpenSolaris, FreeBSD, and perhaps a few other VMs under ESX/ESXi.

3) VMware GUI to manage ESXi only runs officially on WinXP. On your Max, load Parallels or VirtualBox and build a WinXP VM.

Again, I think this is the best answer for your situation. If you weren't dealing with Microsoft server and certifications, I'd recommend Ubuntu Server with KVM, but you'd need the VT-x supported CPU for that too.

The other options outlined here aren't bad, just I don't think you'll be happy with the performance. I could be wrong. The performance of an i5 CPU over a C2Q is significant when you have multiple virtualized servers.

---

