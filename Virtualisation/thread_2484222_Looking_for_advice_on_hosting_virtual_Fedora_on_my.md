---
title: "Looking for advice on hosting virtual Fedora on my Xubuntu system"
date: 2023-02-20
forum: Virtualisation
---

### Post by kogorman-pacbell on 2023-02-20
I have a busy [beowulf cluster]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwjdnJnLyKT9AhUUK0QIHXlgAZkQFnoECAsQAQ&url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FBeowulf_cluster&usg=AOvVaw1fBT7qi4wsN1s4r5LevlRx") of Xubuntu machines, one of which I sometimes reboot into Fedora just for one app I don't know how else to run: Fedora's [six]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwjz3_37yKT9AhW2LEQIHVOoCjsQFnoECBcQAQ&url=https%3A%2F%2Fpackages.fedoraproject.org%2Fpkgs%2Fsix%2Fsix%2F&usg=AOvVaw2gLjTvR8NLSpbfzz702hX-"), which is useful because my project concerns strategy games.  But I would prefer to stop rebooting in favor of running everything on Xubuntu..

I have two or three ideas, with several sub-plots, and I have not really explored them all.  I could spend a lot of time on this, or ask if there's an expert here who can guide me.  What I'm thinking so far:
[LIST]
[*]Recompile six on Xubuntu.  The main hurdles here are that six depends on very old versions of Qt and KDE, which Fedora still supports but Ubuntu does not.  I don't know if just finding libraries and rebuilding on modern Xubuntu is workable.  If it is, it would be the ideal solution. 
[*]Run Fedora in a virtual machine.  I gather there are multiple ;choices for that.  It could be simpler in some ways, but is likely more resource-intensive.  But for starters, I'm not sure how to pick a VM
[LIST=1]
[*]VirtualBox -- I gather it's an Oracle product. 
[*]Docker 
[*]LXD 
[*]Any others worth considering? 
[/LIST]
  
[*]Should I consider containerization instead? 
[/LIST]

---

### Post by ajgreeny on 2023-02-20
I suggest you have a look at KVM/QEMU and virt-manager, the Linux kernel-virtual macine system, along with all its dependencies and then install your Fedora version in that.  
It runs faster, smoother and more reliably than VBox in my experience, and I can say that as I used to use VBox until about 2 years ago when I tried KVM/QEMU and have stayed with it ever since.

There used to be a very good Ubuntu-wiki page about installing and running virtual installations using this but as far as I can see this has now become a bit out of date, and suggests you install a package ***qemu-kvm*** that no longer exists though it automatically uses and installs the alternative package, ***qemu-system-x86*** which replaced kvm-qemu fairly recently.
I think that if you run command ```
sudo apt install qemu-system-x86 libvirt-daemon-system virt-manager
``` you will get all that is needed to try using that system instead of the alternatives such as virtualbox.
See these three pages, though you'll probably find others to help you.
[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)
[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)
[https://help.ubuntu.com/community/KVM/CreateGuests](https://help.ubuntu.com/community/KVM/CreateGuests)

Open up virtual-machine-manager from the menu of your Xubuntu and then follow the instructions from these pages, and don't worry if things go wrong to start with as they did for me; you can delete any bad VMs and start again without difficulty.
Here's a glimpse of my attempts and problems when I started; now, there's no going back to VBox for me.
[https://ubuntuforums.org/showthread.php?t=2450115&highlight=kvm%2Fqemu](https://ubuntuforums.org/showthread.php?t=2450115&highlight=kvm%2Fqemu)

I'll be interested to hear your feelings about trying this and how you get on if you do give it a go.

---

### Post by ajgreeny on 2023-02-20
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit irrespective of the OS you wish to use.

---

### Post by MAFoElffen on 2023-02-20
I also recommend and use KVM...

I install using the basic KVM toolset
```

sudo apt install -y qemu-kvm libvirt-daemon-system virtinst libvirt-clients virt-manager

```
Then add yourself to the kvm and libvirt groups
```

sudo usermod -aG kvm $USER
sudo usermod -aG libvirt $USER

```
After that, you can use Virt Manager to start installing VM's...

What I do first, before installing the first VM on a fresh install, is to create a directory which I keep my ISO's into and download them to. On the install of the first VM, I then then setup (add) a pool in Virt-Manager that I can find them in, pointing to that directory That way you can get back to that same directory later in later VM Installs..

One thing beyond that might be to install a bridged network for your virtual network, so that some VM's such as that planned Fedora VM can be accessed from computers on the Host's Network...

Welcome to your new experiences. Have fun.

---

### Post by SeijiSensei on 2023-02-20
I've used this tutorial which generally follows MAFoElffen's approach with some added bells and whistles.

[https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)

---

### Post by DuckHook on 2023-02-20
I see you are open to using LXD. Though they share many similarities, you should be aware of the significant differences between a VM and a container. They are different technologies:

VMs:

[LIST]
[*]Older, proven, stable tech
[*]Easier to install and implement
[*]Best sandboxing and security
[*]Resource intensive and will never run at native HW speed
[/LIST]

Containers:

[LIST]
[*]Runs so close to native HW speed as to be indistinguishable
[*]Very efficient resource usage: disk as well as RAM, CPU & GPU
[*]Good sandboxing but not the best
[*]More difficult, convoluted install. More exotic tech. Less documentation.
[*]In the case of LXD, is only available as a snap. Is basically ZFS&#8209;dependent.
[/LIST]
I don't run dockers, so can't really advise you on that. LXD will likely install that older version of Fedora right from LXD's image store (though you haven't told us which version, so no promises). I'm sold on LXD, but I'm a minority on these forums, so take what I say with a heavy dose of salt.

There's a link in my sig to installing and using LXD

---

### Post by TheFu on 2023-02-21
> **kogorman-pacbell said:**
>   But for starters, I'm not sure how to pick a VM
[LIST=1]
[*]VirtualBox -- I gather it's an Oracle product. 
[*]Docker 
[*]LXD 
[*]Any others worth considering? 
[/LIST]
  
[*]Should I consider containerization instead? 
[/LIST]

Docker and LXD/LXC **ARE** container managers, so you've listed 2 containers and 1 hypervisor.
I've never used virtualbox with Linux as the host.  Tried, but at the time it wouldn't work. That was long ago.  I was using Xen in productions and KVM for testing and VMware ESXi for client support back then. After about a year of testing KVM and likeing what it provided for server virtualization, I migrated off Xen and ESXi completely.  I ran Virtualbox on a MS-Windows laptop for a few more years, but KVM became the "standard" used.  Almost every VPS company in the world uses KVM today, unless they are selling their own dogfood like VMware, MSFT, Oracle ... everyone else uses KVM, including Amazon, Linode, and all the other VPS people.  Around 2016, KVM became good for desktop-on-desktop needs, not just server-on-server needs, which is what I care about, mostly.

A friend runs AutoCAD under KVM on his laptop, so the desktop-on-desktop stuff is very good. Networking is best setup outside the hypervisor, though libvirt does provide a simple NAT interface.  If you want a bridged interface, you'll want to setup up the bridge using netplan YAML files.

If you don't need this software to be accessed over the internet, I'd suggest going with an LXD managed LXC container.  It will be fairly light, fast, and should use 1/10th the resources of a full VM.  Below are the list of x86-64 Fedora LXD images available:
```
$ lxc image list images:fedora |grep amd64
| fedora/36 (3 more)              | 8aed0d556af4 | yes    | Fedora 36 amd64 (20230220_20:33)        | x86_64       | CONTAINER       | 101.08MB | Feb 20, 2023 at 12:00am (UTC) |
| fedora/36 (3 more)              | a6526fe3e56e | yes    | Fedora 36 amd64 (20230220_20:33)        | x86_64       | VIRTUAL-MACHINE | 482.97MB | Feb 20, 2023 at 12:00am (UTC) |
| fedora/36/cloud (1 more)        | 8856b8b8037c | yes    | Fedora 36 amd64 (20230220_20:33)        | x86_64       | VIRTUAL-MACHINE | 499.03MB | Feb 20, 2023 at 12:00am (UTC) |
| fedora/36/cloud (1 more)        | ec9cfe819a5b | yes    | Fedora 36 amd64 (20230220_20:33)        | x86_64       | CONTAINER       | 111.20MB | Feb 20, 2023 at 12:00am (UTC) |
| fedora/37 (3 more)              | 1b04756b79b7 | yes    | Fedora 37 amd64 (20230220_20:33)        | x86_64       | VIRTUAL-MACHINE | 487.27MB | Feb 20, 2023 at 12:00am (UTC) |
| fedora/37 (3 more)              | e0c067b24a2b | yes    | Fedora 37 amd64 (20230220_20:33)        | x86_64       | CONTAINER       | 100.16MB | Feb 20, 2023 at 12:00am (UTC) |
| fedora/37/cloud (1 more)        | 0d208685efad | yes    | Fedora 37 amd64 (20230220_20:33)        | x86_64       | VIRTUAL-MACHINE | 504.87MB | Feb 20, 2023 at 12:00am (UTC) |
| fedora/37/cloud (1 more)        | b4738015e808 | yes    | Fedora 37 amd64 (20230220_20:33)        | x86_64       | CONTAINER       | 111.47MB | Feb 20, 2023 at 12:00am (UTC) |
| fedora/Rawhide (3 more)         | a55ef0dec09e | yes    | Fedora Rawhide amd64 (20230210_02:25)   | x86_64       | VIRTUAL-MACHINE | 498.44MB | Feb 10, 2023 at 12:00am (UTC) |
| fedora/Rawhide (3 more)         | f02d27b6958c | yes    | Fedora Rawhide amd64 (20230210_02:25)   | x86_64       | CONTAINER       | 101.92MB | Feb 10, 2023 at 12:00am (UTC) |
| fedora/Rawhide/cloud (1 more)   | 5fbe18152ae4 | yes    | Fedora Rawhide amd64 (20230210_00:59)   | x86_64       | VIRTUAL-MACHINE | 515.94MB | Feb 10, 2023 at 12:00am (UTC) |
| fedora/Rawhide/cloud (1 more)   | fd5c3b031257 | yes    | Fedora Rawhide amd64 (20230210_00:59)   | x86_64       | CONTAINER       | 113.59MB | Feb 10, 2023 at 12:00am (UTC) |

```

After you initialize lxd's environment, run
```
$ time sudo lxc launch images:fedora/Rawhide Fedora
Creating Fedora
Starting Fedora                             
                               
real    0m34.130s
user    0m0.039s
sys     0m0.036s
 
$ lxc list
+-----------+---------+----------------------+------+-----------+-----------+
|   NAME    |  STATE  |         IPV4         | IPV6 |   TYPE    | SNAPSHOTS |
+-----------+---------+----------------------+------+-----------+-----------+
| Fedora    | RUNNING | 172.22.22.224 (eth0) |      | CONTAINER | 0         |
+-----------+---------+----------------------+------+-----------+-----------+
```
to have a running Fedora system in about 40 seconds.
```
$ lxc exec Fedora   -- sudo --login
[root@Fedora ~]# df -Th
Filesystem            Type      Size  Used Avail Use% Mounted on
lxd/containers/Fedora zfs        48G  287M   47G   1% /

```
Under 300MB. Nice.

---

