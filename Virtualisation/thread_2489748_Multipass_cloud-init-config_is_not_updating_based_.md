---
title: "Multipass cloud-init-config is not updating based on multipassd-vm-instances.json"
date: 2023-08-09
forum: Virtualisation
---

### Post by DarthPedro on 2023-08-09
Hi,

I'm a new user of multipass. I use it on Windows 11 home with Virtualbox(7.0.10-158379), multipass 1.12-2-win.
I created an instance as in the manual without any options except the name.
multipass launch jammy --name test1
I realized later, the instance doesn't receive IP address from my local network. It cannot be reached, just by multipass shell command.
I found this post for a possible solution.
[Add ability to add --networks to existing instances #2476]("https://github.com/canonical/multipass/issues/2476")
I added this below to the multipassd-vm-instances.json
        "extra_interfaces": [
            {
                "auto_mode": false,
                "id": "en0",
                "mac_address": "52:54:00:ab:c3:0d"
            }
        ],
Actually it did not matter what was the id name, auto_mode or mac_address. I tried all of them with different values.
It didn't work. Later I found out, the multipass is not updating the cloud-init-config file. It doesn't have the network-config file.
I created another instance with --network name="Ethernet 2" mode=auto
"Ethernet 2" the network interface name on this Windows

multipass launch jammy --name test3  --network name="Ethernet 2" mode=auto

This instance receives IP address from the local network and cloud-init-config file has the proper network-config file.

Question: What I did wrong? How can I add/modify the network interfaces to existing instances?

---

### Post by DuckHook on 2023-08-09
I cannot help you with Multipass on Windows, but it seems to me that you would need to create the network interface using Windows tools first. I imagine that Windows has security safeguards against VMs just joining the LAN after the fact (malware could exploit such poor security to compromise any system) and that these would have to be set up manually to allow access.

I can't help you with Windows. I've forgotten everything I ever knew about it for years now.

My meta&#8209;question is: why are you using Multipass? Unless you are an enterprise user looking to clone/cluster VMs across multiple servers, this seems to me to be just adding an unnecessary layer. Simply install VirtualBox and do all of your tweaking within that platform. I haven't used VBox for some years now too, but if memory serves, it is easy to set up and knock down all sorts of NICs within VBox. It is—or, at least, it was—a simple, elegant interface.

---

### Post by DarthPedro on 2023-08-10
Thank you very much for your reply.
Ii is not related to Windows itself.
I didn't create anything with any Windows tools for the 2nd instance. 2nd instance receives ip address from the local network, the 1st isn't. The different is how I created the two instances. 1st was created without additional network interface, the 2nd was created with it. I tried to find the way how can I add an extra interface to the existing instance. The method what I found isn't working, because the multipass doesn't update the cloud-init-config.iso
I thing it is not related to the Windows.
For test, I changed the cpu number of the 1st instance as it supported by multipass
multipass set local.test.cpus=2
It changed the multipassd-vm-instances.json with adding
"num_cores": 2,
It was showed up in test.vbox file also
<CPU count="2">
but the cloud-init-config.iso wasn't changed.
Now my question is how uses the multipass the multipassd-vm-instances.json?
I made an another test. I changed the cpu numbers from 2 to 3 by directly modifying the multipassd-vm-instances.json file. Multipassd was stopped.
I restarted it and multipass get local.test.cpus gave back 3. 
test.vbox wasn't changed, it has still 2.
I started the instance and it had only 2 cpu core.
I changed the memory size of the 1st instance with 
multipass set local.test.memory=2G
It changed in both files multipassd-vm-instances.json and test.vbox but the cpu number wasn't updated to 3.
It looks like the multipass and multipassd don't check the multipassd-vm-instances.json for any changes.
How can I force multipass to update the virtualbox config file based on multipassd-vm-instances.json?

I know it's more easy just to create another instance, but I like to try to figure out the problems and solve it if I can and a workaround is only the last option for me.

about your meta-question: At the end I will use directly Virtualbox. I just so multipass when I was on ubuntu website and it sounds interested to me. So I gave a try what is it and how it's work.

---

### Post by TheFu on 2023-08-10
You are the first person I've ever heard of actually using Multipass.  I tried a few years ago, but at the time (and still today) the snap constraints wouldn't allow the system where I wanted to test it out to use any snap packages.

There are a multitude of well-known, often used, hypervisors for Windows.  If you want to tread down the road not travels, thank you for your service.  Please start opening bugs against the multipass subsystem.
OTOH, if you need a practical solution, the virtualbox is the least bad of the options for home users. In a corporate environment, using VMware Workstation is probably the best answer.

> about your meta-question: At the end I will use directly Virtualbox. I just so multipass when I was on ubuntu website and it sounds interested to me. So I gave a try what is it and how it's work. 
That roped me into trying it too.  When it didn't work, I stopped beating my head against the wall and felt better going back to KVM/QEMU + libvirt + virt-manager to deal with VMs on my Linux systems. Alas, with MS-Windows as the host system, that software stack isn't available. It is what nearly every VPS uses in the world, unless they are trying to sell their own dogfood, like MSFT w/ Azure does.  Azure has some strange aspects.  OTOT, Amazon EC2, Linuode, Vultr, DigitalOcean, and thousands of other VPS providers all use KVM/QEMU.

But only you can choose which makes the most sense for your needs.

---

