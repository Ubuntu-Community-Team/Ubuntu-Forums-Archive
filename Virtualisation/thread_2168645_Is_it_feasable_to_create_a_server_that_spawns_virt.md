---
title: "Is it feasable to create a server that spawns virtual machines"
date: 2013-08-18
forum: Virtualisation
---

### Post by JTwigg on 2013-08-18
I have a spare machine at home and i was wondering how much effort it would be to setup a ubuntu server that you can spawn an instance of a server in a few minutes for testing stuff, similiar to digital ocean droplets.

I've suppose we would need to install xen or openvz, then perhaps some web interface (or ssh in and use a command) that we can use to spawn an image of ubuntu server already setup and on a brigided connection. 

basically my question is: is this feasable to setup as a weekend project? has anyone tried his?

---

### Post by Habitual on 2013-08-18
> **JTwigg said:**
> I have a spare machine at home and i was wondering how much effort it would be to setup a ubuntu server that you can spawn an instance of a server in a few minutes for testing stuff, similiar to digital ocean droplets.

I've suppose we would need to install xen or openvz, then perhaps some web interface (or ssh in and use a command) that we can use to spawn an image of ubuntu server already setup and on a brigided connection. 

basically my question is: is this feasable to setup as a weekend project? has anyone tried his?

I have my doubts about it being a "weekend project", but tell us more about this spare machine's resources...

---

### Post by JTwigg on 2013-08-18
thanks for your reply
the machine is just an old desktop. some generic micro atx board, AMD phenom quadcore, 8 gigs of ram.
i still might try this sometime, if not as a proof of concept.

---

### Post by Kevin_Arnold on 2013-08-18
You can create a KVM VM straight from the command line: [http://agix.com.au/blog/?p=2730](http://agix.com.au/blog/?p=2730)

With that being true, all you would need to do is wire up some scripts to run the commands based on input from a web form. Digital Ocean has a lot more stuff to manage, so they obviously have a much more complicated system, but I think you could do something simple pretty easily.

I am assuming you're just doing this for fun, btw. I wouldn't suggest such a simple answer if you're doing it for profit.

---

### Post by 1clue on 2013-08-18
Not an expert on this, but I believe the kvm command line thing is pretty much assuming you would host the VM on that box too.  Which means that system should have some muscle to it.  Which rules out what most home users would refer to as a 'spare machine'.

I know you CAN move the files over to some other system, but then IMO you would run that command on the other system.  It would be much faster, and much easier.

---

### Post by JTwigg on 2013-08-18
thanks for the link.
yeah this is entirely for fun and will be on my home network. 
I think i will try setting up kvm then i could probably setup some php scripts and shell_exec the commands for spawning, listing removing virtual machines.
i will play with this next weekend and report back in case anyone is interested.

---

### Post by JTwigg on 2013-08-18
also, if i can actually get it working, I may invest in some dedicated hardware next pay day :P

---

### Post by 1clue on 2013-08-18
OK with regards to buying dedicated hardware, it's well worth the effort to go look for recommended hardware that you know works.

I tried this for the first time a few years back, wound up with a motherboard that had bugs in the virtualization firmware and to this day it's still not fixed.

If I were doing it again, I'd look for examples in my price range with the features I like, go build the box from it and install it right away.

Also as what I would call a hobbyist KVM administrator who uses VMs for my job, I would mention that while you CAN do all this from the command line, using virt-manager is super easy.

---

### Post by 1clue on 2013-08-18
Duplicate post.  Not sure why.

---

### Post by mark_spieth2 on 2013-08-19
> **JTwigg said:**
> I have a spare machine at home and i was wondering how much effort it would be to setup a ubuntu server that you can spawn an instance of a server in a few minutes for testing stuff, similiar to digital ocean droplets.

I've suppose we would need to install xen or openvz, then perhaps some web interface (or ssh in and use a command) that we can use to spawn an image of ubuntu server already setup and on a brigided connection. 

basically my question is: is this feasable to setup as a weekend project? has anyone tried his?


Absolutely you can. I use Openvz for this, under Redhat, however you should be able to do it under ubuntu as well. Using [ansible]("http://www.ansibleworks.com/") and the [openvz]("https://github.com/rivik/ansible-openvz/blob/master/openvz") module you can create VM's easily with one command:

ansible VM1 -i hosts/create-mu -m openvz -a "command=create hostname=host.host.com ctid=100 ipadd=10.200.50.10 create_magic=no"

You can then further customize the VM with ansible if needed, or create openvz templates, and use ansible to startup new VM's. It should also work with KVM, although since I don't use KVM all that often I don't know what modules are available to do so, but you can always use ansible to run the KVM creation script. Also look into ubuntu's vmbuilder.

---

### Post by TheFu on 2013-08-20
> **mark_spieth2 said:**
> Absolutely you can. I use Openvz for this, under Redhat, however you should be able to do it under ubuntu as well. Using [ansible]("http://www.ansibleworks.com/") and the [openvz]("https://github.com/rivik/ansible-openvz/blob/master/openvz") module you can create VM's easily with one command:

ansible VM1 -i hosts/create-mu -m openvz -a "command=create hostname=host.host.com ctid=100 ipadd=10.200.50.10 create_magic=no"

You can then further customize the VM with ansible if needed, or create openvz templates, and use ansible to startup new VM's. It should also work with KVM, although since I don't use KVM all that often I don't know what modules are available to do so, but you can always use ansible to run the KVM creation script. Also look into ubuntu's vmbuilder.

The virtualization tech doesn't really matter that much. Use whatever you like, but "container-based" VMs will be much, much quicker to start. Xen, KVM, virtualbox, qemu, openvz, lxc ... doesn't matter for a simple Linux guest.  If you want to screw around with more advanced network stuff, avoid the containers and setup dedicated bridges for each clientOS under an HVM setup.

+1 on ansible. It is a competitor to Puppet with almost zero client-side requirements. You can be controlling remote systems in 15 minutes. Of course, it will take a week or so to understand the real power of managing systems with ansible.  Ansible is a competitor to Rexify, SaltStack, Puppet, Chef, CFengine and old school bash/perl/python scripts.

+1 on virt-manager. It makes using and managing KVM like using virtualbox or vmware-player's GUIs. With libvirt, you can use the CLI interface at any point to manage systems - virsh works locally or on remote VMs.  Use virt-manage to setup different, new systems and use virsh to clone and spawn them easily ... other you can use virt-manager for everything in a tiny shop.

I didn't lookup the capabilities for your current machine, but you should be able to run 7+ VMs on that concurrently.  I'm running 6 production VMs on a Core2Duo Xtreme with 8G now.  Blogs, desktops, Zimbra, Alfresco, and an email gateway are examples. It is fast enough. All KVM.

BTW, I previously used Xen, ESXi, VirtualBox ... each had "issues" of a different sort.  ESXi was very picky about hardware. 1/4 of my systems couldn't install ESXi - disk controller was incompatible.  VirtualBox would crash after an hour of running a client VM ... without doing anything inside it.  Xen would refuse to boot the hostOS about 4 times a year after kernel updates. Client OSes would refuse to boot about 12 times a year, which forced us to fallback to 1 or 2 prior kernel versions to get a booting system.  

Been running KVM about 18 months now. I can't think of any issues. No crashes. No funny business at all. It just works.  Have 1 Windows VM running inside KVM here - it records TV shows. All the other VMs are Linux ... 10.04, 12.04 .... stay with LTS releases if you want stability.

---

### Post by CharlesA on 2013-08-21
I've been using [Proxmox]("http://proxmox.com/") for my virtualization solution for a few months now and I love it. It makes managing KVM and OpenVZ dead simple.

I was using VirtualBox previously with no issues - but the web frontend I was using was no longer under development, so I decided it was time to move on.

---

### Post by JTwigg on 2013-08-26
thanks for your replies, I'm going to try the kvm way first

---

