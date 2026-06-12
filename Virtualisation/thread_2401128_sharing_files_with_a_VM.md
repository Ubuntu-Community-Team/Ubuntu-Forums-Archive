---
title: "sharing files with a VM"
date: 2018-09-13
forum: Virtualisation
---

### Post by Skaperen on 2018-09-13
i would like to know if there is any setup which makes it easy to run Linux guested VMs with its root filesystem(s) (/etc, /bin, /usr, and so on) shared from the host system, not as a block device or loopback device.  usually this will mean _NFS_.  but i am hoping there are now things like emulation of devices sourced without NFS or small commonly usable images to bring up a guest that the uses _NFS_.  i'm just looking around for possibly new stuff in the past 8 years since i did virtualization.  otherwise i'll just spend the time to piece it together, myself.

my goal is to set up several VMs i can run in the background with no GUI except via VNC connections (when i want to be on, not required to bring a guest up).  they will be started in CLIs under _[FONT=courier new]screen[/FONT]_ (which i use for just about all my background stuff).  they will, in most cases, be there to test things under different distros and/or versions.

---

### Post by TheFu on 2018-09-15
Not sure I understand but sheepdog is a storage cluster solution for KVM.  There are others.

The goal you have mentioned is something that virsh does all the time .... though you don't need screen.  virsh uses libvirt and a client/server connection.  Not sure what having shared critical file systems has to do with this.  Most distros have slightly different needs for the files in /usr, /bin, and /etc/.  If they are identical, then only /var/ and /etc/ have to be unique, sharing of /bin and /usr is fine.  At least that's how I interpret the FHS.  /etc is tiny, so it usually isn't a big deal to have it on local storage.  But only you know the specific situation.

---

### Post by Skaperen on 2018-09-15
the reason i want to share files between host and guest is so i can readily change things when all th[FONT=arial]e VMs ar[/FONT]e down, which could very often include parts of [FONT=courier new]/etc[/FONT].  yes, that can involve some executables runnable as [FONT=courier new]root[/FONT] on both.  but i will be the only one doing that.  i do trust me, myself, and i, with [FONT=courier new]root[/FONT] powers.

---

### Post by TheFu on 2018-09-15
A few options now that I understand the real goal.

If the VMs are off, it is possible to mount the storage from the host.
[https://www.jamescoyle.net/tag/qemu-nbd](https://www.jamescoyle.net/tag/qemu-nbd) is one method for qcow2 VM storage.

Use **mount -o loop**  with raw image VM storage.  I remember having to use an offset last time I did it.

---

### Post by KillerKelvUK on 2018-09-15
Suggest you look into containers ([https://linuxcontainers.org](https://linuxcontainers.org)) rather than a traditional VMs. Low latency, images for different distros ([https://us.images.linuxcontainers.org](https://us.images.linuxcontainers.org)), all guest filestorage is file-by-file on host, different toolset options for managing via cli (ubuntu pushes LXD [https://lxd.readthedocs.io/en/latest/](https://lxd.readthedocs.io/en/latest/)).

---

### Post by Skaperen on 2018-09-16
> **KillerKelvUK said:**
> Suggest you look into containers ([https://linuxcontainers.org](https://linuxcontainers.org)) rather than a traditional VMs. Low latency, images for different distros ([https://us.images.linuxcontainers.org](https://us.images.linuxcontainers.org)), all guest filestorage is file-by-file on host, different toolset options for managing via cli (ubuntu pushes LXD [https://lxd.readthedocs.io/en/latest/](https://lxd.readthedocs.io/en/latest/)).

do i have to use a prebuilt image with containers or can i start empty and boot an ISO or USB stick image and my own install.

i need to go way back to unsupported versions of several distros.  probably to 10.04 for Ubuntu.

if filestorage is file-by-file on the host, how are these prebuilt images used?  will they be there file-by-file when i boot up the container?  can i modify those files before booting?  i do plan on keeping the changes in SVN or HG so i can just pick a revision when i need to.

---

### Post by Skaperen on 2018-09-16
> **TheFu said:**
> A few options now that I understand the real goal.

If the VMs are off, it is possible to mount the storage from the host.
[https://www.jamescoyle.net/tag/qemu-nbd](https://www.jamescoyle.net/tag/qemu-nbd) is one method for qcow2 VM storage.

Use **mount -o loop**  with raw image VM storage.  I remember having to use an offset last time I did it.

and **u**mount, too.

i've already done this with NFS and am looking to find a way forward from that.

---

### Post by KillerKelvUK on 2018-09-17
> **Skaperen said:**
> do i have to use a prebuilt image with containers or can i start empty and boot an ISO or USB stick image and my own install.

i need to go way back to unsupported versions of several distros.  probably to 10.04 for Ubuntu.

if filestorage is file-by-file on the host, how are these prebuilt images used?  will they be there file-by-file when i boot up the container?  can i modify those files before booting?  i do plan on keeping the changes in SVN or HG so i can just pick a revision when i need to.

I believe you can create your own container images although I never have.

Regards storage...the management layer i.e. LXD allows different storage solution but, for example if you choose local disk the the prebuilt images are simply cached locally and unpacked to your local disk per container you create, you can then go an modify these files offline.

---

### Post by TheFu on 2018-09-17
The best practice for using containers doesn't include treating them like complete OSes.  They only have enough OS to perform the specific task.  No ssh.  No shells.  All config management happens outside the container.  

Containers should be treated like Zombies. As soon as they don't do what you want, you shoot it in the head and build a fresh one that does do what you want.  Also, most containers shouldn't have any data.  They are service providers.  Data should be stored elsewhere.

I wouldn't compare access via NFS to access via qemu-nbd.  One is a network protocol and the other is direct access.

---

### Post by Skaperen on 2018-09-17
i'm not implying that NFS is direct access.  but it can be host access by setting up NFS export on the host and specify the host IP in the NFS boot specification for the guest.  i don't know (yet) how the direct access files show up in the guest (e.g where mounted from).  i have only used qemu for VM operation, before, and that was back before 64-bit came out.  i have used instances on the xen-based AWS EC2 cloud (made custom AMIs, some derived from existing AMIs, some built from scratch).  i have also built embedded images for multiple architectures.  my prior VM experience was on IBM mainframes before Linux existed.

---

### Post by TheFu on 2018-09-17
I use raw images and qcow2 for VMs and have since the beginning.  If the VM is shutdown, you can mount those on the VM-host. You said you wanted a way to modify the OS for a VM from the host.  I provided 2 methods.  Did I misunderstand to purpose?

I'm an old MF programmer from before switching to Unix, then Linux. Actually wrote code for modified IBM 360s doing real-time control systems.  IBM midrange LPARS are pretty slick on the P-series, but Sun/Oracle and HP had their versions for a long time.  But none of that really matters.

AWS uses KVM now.   [https://www.theregister.co.uk/2017/11/07/aws_writes_new_kvm_based_hypervisor_to_make_its_cloud_go_faster/](https://www.theregister.co.uk/2017/11/07/aws_writes_new_kvm_based_hypervisor_to_make_its_cloud_go_faster/)

I think we're at the point where you either found what seems reasonable or not. Good luck.

---

### Post by Skaperen on 2018-09-18
> **KillerKelvUK said:**
> Suggest you look into containers ([https://linuxcontainers.org](https://linuxcontainers.org)) rather than a traditional VMs. Low latency, images for different distros ([https://us.images.linuxcontainers.org](https://us.images.linuxcontainers.org)), all guest filestorage is file-by-file on host, different toolset options for managing via cli (ubuntu pushes LXD [https://lxd.readthedocs.io/en/latest/](https://lxd.readthedocs.io/en/latest/)).

i was jumping to the assumption that containers was some more sophistication/advanced virtual machine.  i did that because i was looking for just such a thing and it was what i had in mind.  i had heard of containers over the past few years but didn't have a reason at the time to look further.  and i had heard nothing to connect them to virtualization (which they are not but there is an overlap of use cases).  containers are more like BSD jail.  and, as it turns out, what i am planning to do could work in containers, or perhaps a large subset could.

a container has an isolated distinct name space where one can run a suite of user land processes apart from any other.  the catch is that everything runs under the same kernel.  so each set of user land, which has it's own separate / directory must support that kernel.  so a really old version of Ubuntu, with an older libc that doesn't understand any API changes made to the kernel, won't be able to run.

any information about which versions of user land package suites will work under which kernels would be helpful.  otherwise i will just have to try it and see.  i had looked into how dpkg can be run to target an initially empty directory and build a system, as an alternate way to go virtual.  containers would actually make this easier since it takes out the steps to setup a boot loader and kernel(s) within the VM.

and, yes, making your own custom images is very possible, it appears.  this also explains a lot of how various cloud providers are doing their pseudo-virtualization (many of them clearly mention containers as what they are doing).

this reminds me of some of the steps i had to do with the file tree back when i made a single CDR that would boott into Linux on either an Intel x86 or a Sun Sparc machine.  one was made with Slackware and another was made with Linux From Scratch (from a scripted build).

i am running Ubuntu 16.04.5 LTS.  it is running kernel 4.4.0.  do you know what other versions of Ubuntu userland can run on kernel 4.4.0?  do you think i should run a different kernel version?  which version?

---

### Post by Skaperen on 2018-09-18
i have used _nbd_ with _qemu_ to make use of a block device space i had on another host, many years ago when i was doing some VM stuff with _qemu_.  now days we also have _iSCSI_, a more sophisticated network protocol.  _iSCSI_ is also more complex compared to _nbd_.  i'd still use _nbd_ if the use case allowed it, for the simplicity.  _KISS_ works in configurations, too.

---

### Post by KillerKelvUK on 2018-09-19
> i am running Ubuntu 16.04.5 LTS. it is running kernel 4.4.0. do you know what other versions of Ubuntu userland can run on kernel 4.4.0? do you think i should run a different kernel version? which version?

So this depends on whether you are intending to use a package manager e.g. aptitude within the container or whether you intend to build from source.  As an acid test for either you can use [https://packages.ubuntu.com](https://packages.ubuntu.com) to track available packages by Ubuntu release and then use [https://people.canonical.com/~kernel/info/kernel-version-map.html](https://people.canonical.com/~kernel/info/kernel-version-map.html) to track kernel alignment to release but as aptitude will do all this automatically this would be simpler, I guess it depends how far back you need to go as to whether the repos extend that distance.  Or maybe I'm not understanding your question?

---

### Post by Skaperen on 2018-09-19
> **TheFu said:**
> I use raw images and qcow2 for VMs and have since the beginning.  If the VM is shutdown, you can mount those on the VM-host. You said you wanted a way to modify the OS for a VM from the host.  I provided 2 methods.  Did I misunderstand to purpose?

i want to have automated file changes and i want to do that without mounting anything.  what i am looking for is some means to have the files as files in the host and have the guest have a means to access them.  that's why i have used NFS.  now that i expect to run some VMs after not doing so for 5+ years, i am wondering if this problem has been solved, yet.

> **TheFu said:**
> I'm an old MF programmer from before switching to Unix, then Linux. Actually wrote code for modified IBM 360s doing real-time control systems.  IBM midrange LPARS are pretty slick on the P-series, but Sun/Oracle and HP had their versions for a long time.  But none of that really matters.

AWS uses KVM now.   [https://www.theregister.co.uk/2017/11/07/aws_writes_new_kvm_based_hypervisor_to_make_its_cloud_go_faster/](https://www.theregister.co.uk/2017/11/07/aws_writes_new_kvm_based_hypervisor_to_make_its_cloud_go_faster/)

I think we're at the point where you either found what seems reasonable or not. Good luck.

i did old MF programming, too, but not RTCS.  that's one reason i had Hercules in my VM mix a few years back.  and i may do that again.  but i basically just run Linux on them (still was able to play around with assembler even though it was in lower case), though i did dabble around with some old MF OSes i could get online (but have no real use for them today).

and AWS still has a lot of Xen still running.  i don't know, yet, what mix of things i can run here and run on AWS.

if i can't find what i want, i'll either go back to doing NFS and/or trying some things in containers (specifically running older kernels is not the objective so containers may well end up doing most of this for me in this project)

one of the elements of what i'll be doing is running a script loop every minute to look in a specific directory for something to do.  when files or directories show up, do things like compile stuff and/or run stuff and move it to another directory.  the host will be moving stuff in and the guest will be doing stuff with it to see how it behaves under various versions and architectures (so i expect to run Qemu system emulations and Hercules for MF emulation).  some other distros will be in the mix.  i may also throw in some BSDs.

---

