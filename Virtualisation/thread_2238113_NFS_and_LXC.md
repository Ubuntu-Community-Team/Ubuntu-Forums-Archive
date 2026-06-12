---
title: "NFS and LXC"
date: 2014-08-06
forum: Virtualisation
---

### Post by schmitzzy on 2014-08-06
So maybe I am going at this the wrong way but as of now I have a shared file system on my data server being shared over NFS. On my virt/container host I have it mounted to /var/lib/lxc to therefore put all of my containers there. and when I iperf the connection i get my expected gigabit speeds(800-900 Mb/s) and if I copy from /dev/zero to this file system i get my expected gigabit speeds(40MB/s) but when i then do an lxc-create my transfer speeds go to 4 MB/second measured at the file system on my data server(ZFS) and when I do lxc-create to a local dir it runs at blazing fast speeds. 

So I am not sure what is causing this issue but it is providing to be very frustrating. Is there any other way you can see to manage this. My hosts do not have much storage, hence the data storage server. So how i can i keep the data storage on my data server and run them across the gigabit link to actually run on my hosts? this is all using LXC for clarification. 

If you need more explanation let me know. It can be confusing.

--Jezzirolk

---

### Post by TheFu on 2014-08-07
NFS is a higher level file sharing solution. Perhaps if you used block-level network storage, things would be better?  iSCSI or AoE?

I'm just guessing here.  I don't use LXC, but I do use NFS and find it to work well for storage - never attempted to use it for VMs. I like my customers too much, I guess. ;)

---

### Post by sedawk on 2014-08-08
I haven't used LXC so far, so only some general comments:
NFS can be much slower than a local disk if many files are being created, then you will see bad performance compared to a local disk.
I can propose two workarounds for your situation:
* can you run lxc-create on the NFS server itself (e.g. via ssh) and only run lxc-execute (?) on the server. (This might speed up the create phase,
   but you still might have trouble with performance fo lxc-execute.)
* A common trick ( I use with virtual machines ) is to store big files in NFS and to use these big files as disk images on the host system.
  The file operations in that fake local disk operate much faster than doing it via the NFS protocol.

---

### Post by Chayak on 2014-08-14
> **schmitzzy said:**
> So maybe I am going at this the wrong way but as of now I have a shared file system on my data server being shared over NFS. On my virt/container host I have it mounted to /var/lib/lxc to therefore put all of my containers there. and when I iperf the connection i get my expected gigabit speeds(800-900 Mb/s) and if I copy from /dev/zero to this file system i get my expected gigabit speeds(40MB/s) but when i then do an lxc-create my transfer speeds go to 4 MB/second measured at the file system on my data server(ZFS) and when I do lxc-create to a local dir it runs at blazing fast speeds. 

So I am not sure what is causing this issue but it is providing to be very frustrating. Is there any other way you can see to manage this. My hosts do not have much storage, hence the data storage server. So how i can i keep the data storage on my data server and run them across the gigabit link to actually run on my hosts? this is all using LXC for clarification. 

If you need more explanation let me know. It can be confusing.

--Jezzirolk

NFS is not optimized for that type of usage.  It's good at moving data in one direction quickly.  If you're doing reads and writes like to a virtual disk or similar it will bog down.  You should really be using a block level protocol like iSCSI.  There's a very good reason iSCSI is the standard for running systems over networks.  The only way you're going to get more performance is to go to 10gbps iSCSI or Fiber Channel.

---

### Post by santosh6 on 2014-09-10
Hi sedwak

On the second point if you are trying to use big files as images you might be mounting them as loop devices ? If so how can I make it as dynamically growing. Any idea?

I am in the similar situation as schmitzzy that creating containers on a host where /var/lib/lxc is actually NFS mount. To keep the speed intact I've used lxc-create with backingstore loop option but the default size is only 1 GB. I want the root partition of the container to be dynamically expanding without creating any trouble in the future.

---

### Post by TheFu on 2014-09-10
> **santosh6 said:**
> I want the root partition of the container to be dynamically expanding without creating any trouble in the future.

Do you think this is a realistic expectation?

---

### Post by santosh6 on 2014-09-24
I am not sure whether we can achieve something like that but if someone with the same requirement has done this before seeking help through this forum.
One of the posts I found on internet  [http://unix.stackexchange.com/questions/104790/how-to-setup-a-growable-loopback-device](http://unix.stackexchange.com/questions/104790/how-to-setup-a-growable-loopback-device) but obviously in different scenario.

---

