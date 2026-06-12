---
title: "Lucid and OpenVZ and/or LXC ?"
date: 2010-01-16
forum: Virtualisation
---

### Post by starfry on 2010-01-16
Hi there,

I'm well into using OpenVZ on Hardy 8.04. I'm starting to think about the next LTS upgrade that will be Lucid 10.04.

I just downloaded Alpha2 and tried OpenVZ: it isn't there! So I've been searching and it would seem that LXC (Linux Containers) is going to be in Lucid. I'd never heard of LXC before today.

Does anyone know the full story? Will OpenVZ be in Lucid? Even if it is, should one plan on migrating to LXC? What will be the pain involved in that (given the investment in configured and running Hardy based OpenVZ VEs)

As a day 1 plan, I had intended a host upgrade to Lucid leaving the many Hardy based OpenVZ VEs in place and I have (naively) hoped they would just continue working.

Any thoughts/comments appreciated...

---

### Post by mkvnmtr on 2010-01-17
I saw your post and googled LXC. On a short read it looks like this is for apps on the native system. I am still reading.

---

### Post by narcisgarcia on 2010-01-17
I've talked with one Ubuntu-OpenVZ team member, and told me:

[LIST]
[*]The plan for Lucid as agreed on with Canonical at the UDS is to have LXC in Ubuntu main and use it as a replacement for OpenVZ
[*]LXC stands for Linux Containers, it's a similar technology but provided  by the vanilla kernel instead of an heavily patched kernel like OpenVZ.
[*]Kernel support is included in mainline since 2.6.26, so it has been a while. Userspace is still in development but works correctly and is integrated with libvirt.
[*]A OpenVZ container itself should work as-is with LXC, only the configuration will need to be converted.
[*]LXC doesn't need the VT (vmx) processor instruction set.
[*]You can assign memory quota for both ram and swap and due memory overcommit without any issue.
[*]Disk space isn't implemented yet, so you'd have to user regular quotas or use LVM for storage.
[/LIST]

Some references to use LXC:
[LIST]
[*][http://www.stgraber.org/category/lxc](http://www.stgraber.org/category/lxc)
[*][https://wiki.ubuntu.com/ContainersSpec](https://wiki.ubuntu.com/ContainersSpec)
[*][http://www.ibm.com/developerworks/linux/library/l-lxc-containers/](http://www.ibm.com/developerworks/linux/library/l-lxc-containers/)
[/LIST]

---

### Post by starfry on 2010-01-22
Thanks for the replies. So one question: If I want to continue using OpenVZ on Lucid, will I be able to ?

I'd like the choice, and the ability to migrate over in my own timeframe :)

I'm running 2.6.24-26 (Hardy) so I don't have the option of migrating in advance.

---

### Post by narcisgarcia on 2010-01-22
With any Ubuntu version (younger or older than 8.04) you can recompile the kernel to use OpenVZ:
[http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_(the_Debian_way)](http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_(the_Debian_way))

With Ubuntu GNU/Linux 8.04 we had an already compiled+patched kernel for OpenVZ, but you can do the same by yourself.

---

### Post by bodhi.zazen on 2010-01-22
> **starfry said:**
> Thanks for the replies. So one question: If I want to continue using OpenVZ on Lucid, will I be able to ?

Almost certainly not. 

I use OpenVZ and would advise you migrate to Proxmox.

The problem with OpenVZ is that it is a kernel patch, and there is no patch for more recent kernels.

The "solution" is LXC. I have just started LXC and I will tell you

1. It is not up to par with openvz yet. You will need to be willing to do a lot of reading to migrate.

2. LXC still has bugs. I was unable to boot a Fedora-12 container I built for example.

3. Much of LXC is not there yet, the containers are NOT as isolated as they should be and networking is manual, in order to get networking I had to manually add a bridge (no big deal, but still ... ), manually add an IP to the container, and manually add a route.

4. Documentation for LXC is sketchy at best, it seems scattered and incomplete, for example I can not find a document that explains the config files and options in any detail, most of the stuff I have found seems to use the minimal options.

5. Did I mention LXC containers are not completely isolated from the host ? Isolation seems better in a standard chroot then lxc. One has access to the host file system, I accessed the  host swap with no problem, and one can start a process on the host from the container, all without "cracking" anything, simply running an init or upstart script or starting a server in the container can start a process on the host.

6. I have had problems getting the user space tool set working, I need to look into this problem more.

7. Although LXC is reported to work with libvirt, I could find no documentation in my brief search and libvirt seemed to have no clue about LXC.

Now these problems may well be that I do not yet understand LXC, but IMO it is not yet up to par with OpenVZ.

Moving forward, it appears once they work out the bugs and get libvirt up w/ LXC it will almost certainly replace OpenVZ.

On the flip side, LXC are part of the main stream kernel so many more developers are working on LXC and forward compatibility will be much easier.

You can start with LXC very easily, simply

sudo apt-get install lxc

This installs the tools / scripts, lxc is already enabled in the kernel, so installing the lxc package does not affect the host as much.

I suggest playing with lcx in a VM or in a dedicated test host, and it certainly is not ready for deployment in a production environment.

You may wist to look at some of these links:

[http://openvz.org/pipermail/devel/2008-September/014314.html](http://openvz.org/pipermail/devel/2008-September/014314.html)

[http://forum.openvz.org/index.php?t=msg&goto=38118&](http://forum.openvz.org/index.php?t=msg&goto=38118&)

[http://openvz.org/pipermail/users/2010-January/003189.html](http://openvz.org/pipermail/users/2010-January/003189.html)

---

### Post by starfry on 2010-01-23
This is a real shame. I've grown to really like OpenVZ. Proxmox isn't really an option for me here because my OpenVZ VE's are running on a desktop workstation box rather than a dedicated server box. OpenVZ has given me what I need and I am mostly happy with it.

I am not afraid of recompiling kernels and I have done this many times. I've never done it on any Ubuntu box however because I wasn't sure how it would affect the ability to run other packaged software that depends on a specific kernel package.

For ease of life I may have to go LXC if the Lucid team don't see sense and include OpenVZ in the next LTS release.

I'm going to take your suggestion and evaluate LXC in a virtual machine.

---

### Post by sweetsinse on 2010-01-27
unfortunately, most of bodhi.zazen's post is simply not true.

i do not use ubuntu anymore, and havent for some time, but the platform i have created should apply to ubuntu with some minor alterations.  i work with arch linux, and within a week will be posting an extensive writeup on LXC w/BTRFS along with a git url to a full implementation of my platform.  all you need to do is download it, add 2 lines to your rc.local, and thats it.**[1]

i will try to remember to post back here after i write it, else my name on arch linux forums is extofme.

i am using LXC in conjunction with BTRFS (awesome together) in a production environment, and can say that it is more than sufficient as a replacement for any chroot/openvz implementation.  it is very flexible in the types of container it can construct, and with some conscious, secure as well. i use openvz on my other server and will be moving all my hosts to my LXC server, so i can make that server run LXC also.


> 1. It is not up to par with openvz yet. You will need to be willing to do a lot of reading to migrate.

it can do everything openvz can, along with freeze/unfreeze, and in the future checkpoint/restart.  a little reading never hurt anyone either.  openvz is deprecated, and lxc is the result of openvz devs and others sick of maintaining massive out of tree patches.  openvz is likely to fall out of most distributions, as you've seen it's not in ubuntu, and has been dropped from arch linux as well.

> 2. LXC still has bugs. I was unable to boot a Fedora-12 container I built for example.

the userspace tools are still under development, but are more than sufficient and stable for use.  kernel features were fully implemented in 2.6.29.  your fedora problem is problem due to udev not working in a container and not having the appropriate device files in /dev or something along that line.

> 3. Much of LXC is not there yet, the containers are NOT as isolated as they should be and networking is manual, in order to get networking I had to manually add a bridge (no big deal, but still ... ), manually add an IP to the container, and manually add a route.

see above about fully implemented.  when using the lxc.rootfs config option, pivot_root() syscall (vs. chroot()) is used... thats about as isolated as you can get.  containers can share the network stack with the host, or have unlimited veth pairs created, one side in the container, and the other added to a bridge on the host.  yes you have to pre create the bridges.  in my system i have dedicated DHCP bridge, and another raw bridge so containers can have direct access to the lan (external IP) if need be.  you dont have to specify an ip, the container init scripts should take care of this.

> 4. Documentation for LXC is sketchy at best, it seems scattered and incomplete, for example I can not find a document that explains the config files and options in any detail, most of the stuff I have found seems to use the minimal options.

[http://manpages.ubuntu.com/manpages/karmic/man5/lxc.conf.5.html](http://manpages.ubuntu.com/manpages/karmic/man5/lxc.conf.5.html)

thats what i use.

> 5. Did I mention LXC containers are not completely isolated from the host ? Isolation seems better in a standard chroot then lxc. One has access to the host file system, I accessed the host swap with no problem, and one can start a process on the host from the container, all without "cracking" anything, simply running an init or upstart script or starting a server in the container can start a process on the host.

see above about pivot_root().  if you dont use the lxc.rootfs config option, the rootfs is shared with the host.  anything not specified in the config is shared with the host.

> 6. I have had problems getting the user space tool set working, I need to look into this problem more.

i use the lxc-* tools in my scripts, they work for me.  i have used libvirt successfully as well, but you must mount the cgroup filesystem WITHOUT the ns option. see here for details:

[http://www.mail-archive.com/libvir-list@redhat.com/msg18689.html](http://www.mail-archive.com/libvir-list@redhat.com/msg18689.html)

havent tried since i sent that message to the list.  i moved to the lxc-* tools for the flexibility; libvirt tries to impose to much on me for my liking.

> 7. Although LXC is reported to work with libvirt, I could find no documentation in my brief search and libvirt seemed to have no clue about LXC.

it does work but you must do what i wrote above.  additionally i dont think "virsh console" works right; i only got it working after i wrote a custom /sbin/init in bash (virsh console seems to want to connect your tty to /sbin/init stdin/out/err, whereas lxc-console connects you to a pty that is linked to a tty in the container)

> Now these problems may well be that I do not yet understand LXC, but IMO it is not yet up to par with OpenVZ.

not as mature, but very capable, and using a vanilla kernel is a must for me at least (using BTRFS)

i have been working with this technology for several months and am very satisfied with my results.  when combined with BTRFS, i can create several working containers in seconds, without consuming any physical space on the hard drive.

**[1] if you have BTRFS and archlinux as the host of course, else there will be some minor changes needed.  pretty much all references to btrfs in my scripts:

btrfsctl -s ${VPS_DOM}/${dom} ${VPS_TPL}/${tpl}

could be replaced with:

cp -R ${VPS_TPL}/${tpl} ${VPS_DOM}/${dom}

it's just stupidly slower and doesn't share blocks as the FS level like btrfs does.  i intend to add this options eventually for those not using a btrfs based root filesystem.  also mkarchroot is the equivalent to debbootstrab, and would need to be changed.  i intend on add this kind of support as well by including static binaries of these kinds of bootstrap programs.

---

### Post by bodhi.zazen on 2010-01-27
I look forward to your write up then. I have been playing with LXC for the last few days and I can not for the life of me get an ubuntu lucid container (built with debootstrap) to boot properly.

Your obviously know more about LXC then I do, I have been using the defaults.

Neither lxc-debian or lxc-fedora function properly on Ubuntu 10.04.

Also no need for the "attitude". For example I do not see pivot root mentioned anywhere in the man page you referenced

[http://manpages.ubuntu.com/manpages/karmic/man5/lxc.conf.5.html](http://manpages.ubuntu.com/manpages/karmic/man5/lxc.conf.5.html)

except at the bottom as a link to the pivot_root page.

Nor is that option listed on any of these pages:

[LXC: Linux container tools]("http://www.ibm.com/developerworks/linux/library/l-lxc-containers/") 
[Linux Containers - ArchWiki]("http://wiki.archlinux.org/index.php/Linux_Containers") 
[LXC - openSUSE]("http://en.opensuse.org/LXC") 
[LXC HOWTO]("http://lxc.teegra.net/") 

Would you mind providing a link to documentation of the pivot_root option ?

So no need to talk down to us "mere mortals" just because you know a few advanced tricks to LXC. Along those lines, what I said in my post is accurate if you use the defaults for LXC. If you like I can post the exact output from my terminal.

Here are some bug reports:

[https://bugs.launchpad.net/ubuntu/+source/lxc/+bug/512200](https://bugs.launchpad.net/ubuntu/+source/lxc/+bug/512200)
[https://bugs.launchpad.net/ubuntu/+source/lxc/+bug/471615](https://bugs.launchpad.net/ubuntu/+source/lxc/+bug/471615)

Perhaps you know how to solve those ?

Using the defaults for LXC, on both fedora and ubuntu, it is trivial to break out of the container, easier then breaking out of a traditional chroot jail.

the only other document I am aware of that discusses security in any detail is here:

[http://www.ibm.com/developerworks/linux/library/l-lxc-security/index.html](http://www.ibm.com/developerworks/linux/library/l-lxc-security/index.html)

Again , if you have a better document, please share.

I agree LXC is up and coming, but the project lacks documentation.

If you would be so kind as to post documentation of your claims that would be useful to others migrating to LXC.

It would also help if you were able to post some documentation on how to create a container. Most of the how -to's simpley state use chroot, lxc-{debian,fedora}, or an openvz template, but none of these techniques allows an ubuntu 10.40 (lucid) template to boot.

---

### Post by sweetsinse on 2010-01-27
whoa there big guy, attitude?  i thought my post was fairly informative, and light of any snippiness... save maybe the first sentence and my comment about the ubuntu manpage :).  at any rate, i apologize because i see how it might be interpreted as being more hostile than i meant, as i meant none; i guess i just felt a slight tone/bias in your original post that twanged a chord with me, because i have been spending literally every day for many moons constructing the LXC based system i am using now.  so again i apologize if i seemed to have an elitist attitude or something, i didn't intend that at all, i mean only to help, inform, and share.

anyways lets get constructive.  your right about the pivot_root() thing not really being mentioned.  i believe the lxc-* tools originally used pivot root, but it was then switched to chroot temporarily for some reason, probably due to other problems.  it is however back at using pivot_root() since this commit:

[http://lxc.git.sourceforge.net/git/gitweb.cgi?p=lxc/lxc;a=commit;h=bf601689a9e0cea1ceaf17e4f7f853f5392c2827](http://lxc.git.sourceforge.net/git/gitweb.cgi?p=lxc/lxc;a=commit;h=bf601689a9e0cea1ceaf17e4f7f853f5392c2827)

but thats jan 08, a little before the release of 0.6.5, i guess i forgot to specify that i use an arch package that builds itself from git :( sorry bout that. the version in karmic/lynx probably still uses chroot().

> Here are some bug reports:

[https://bugs.launchpad.net/ubuntu/+s...xc/+bug/512200](https://bugs.launchpad.net/ubuntu/+s...xc/+bug/512200)
[https://bugs.launchpad.net/ubuntu/+s...xc/+bug/471615](https://bugs.launchpad.net/ubuntu/+s...xc/+bug/471615)

Perhaps you know how to solve those ?

the first one has to do with the fact that there is no config file being defined in lxc-create (the -f option).  because of that, the rootfs is being shared with the host, and this it is trying to use devices/init on the host, NOT in the folder that was just debootstrapped.  there was actually a patch, because its an innocently disastrous problem, disallowing using lxc-start without a valid config option for just this reason... it can crash the host.  see here:

[http://lxc.git.sourceforge.net/git/gitweb.cgi?p=lxc/lxc;a=commit;h=f2ae79a04567fb8c1181f4d3331d2b7a48889cf3](http://lxc.git.sourceforge.net/git/gitweb.cgi?p=lxc/lxc;a=commit;h=f2ae79a04567fb8c1181f4d3331d2b7a48889cf3)

there is a bug about the "Device or resource busy" part.  i have seen that happen before, but only when i had partial cgroups mounted, some for libvirt and some for lxc with different subsystems enabled (like what i said about libvirt having a problem with th "ns" mount flag... which is enabled by default). see this thread:

[http://www.mail-archive.com/devel@openvz.org/msg19729.html](http://www.mail-archive.com/devel@openvz.org/msg19729.html)

im not sure if thats been addressed or not, but it hasnt caused my problems since i moved to lxc-* tools exclusively.  also if you mount a cgroup using the lxc name, lxc-* tools will use that cgroup. like this:

mount -t cgroup lxc /cgroup

from : [http://lxc.sourceforge.net/lxc.html](http://lxc.sourceforge.net/lxc.html)
> The control group can be mounted anywhere, eg: mount -t cgroup cgroup /cgroup. If you want to dedicate a specific cgroup mount point for lxc, that is to have different cgroups mounted at different places with different options but let lxc to use one location, you can bind the mount point with the lxc name, eg: mount -t cgroup lxc /cgroup4lxc or mount -t cgroup -ons,cpuset,freezer,devices lxc /cgroup4lxc

the second one looks like it could have the same problem, as neither seem to be defining the rootfs via a config file.  however, im not really sure, it could be because there are several missing kernel features.  in my setup i have all namespaces enabled, and all cgroup features, as well as multiple devpts (this is HIGHLY recommended. without, all containers will see each others ptys including the hosts...) i even mount the hosts pty with the "newinstance" flag to force all instances of devpts to be private.  there is a CONFIG kernel option to disable the "real" kernel devpts, and force all devpts mounts to be private.  i would expect this to become the default soon, as you could use bind mount to share pty mounts instead.  see here for more details, good read and not too long:

[http://www.mjmwired.net/kernel/Documentation/filesystems/devpts.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/devpts.txt)

as for security, pivot_root() addresses the break out part, beyond that there are other things that need to be done.  inside the lxc config file you specify:

lxc.cgroup.devices.deny = a

(requires the cgroup "devices" to be enabled) which will prevent the guest from creating any device files whatsoever.  you then add things like in "marios" post here:

[http://blog.flameeyes.eu/2009/08/10/some-more-notes-about-linux-containers](http://blog.flameeyes.eu/2009/08/10/some-more-notes-about-linux-containers)

which explicitly allow certain device files to be created in the container, like random/urandom/etc.  ill admit this is the part im working on now, i.e. locking down the containers, some i'm a little lacking in knowledge there.

that also reminds me that lxc has no inherent support yet for controlling disk quota.  in my setup, i use BTRFS subvolumes as rootfs's, so it is trivial for me to place limits on how large they can grow using the BTRFS tools.  otherwise you'll probably need to use LVM or something to enforce disk quota.  i think openvz did support this.

the lxc-* tools config files can support any cgroup that exists, even those that havent been created.  so you can place quota on memory, cpu, etc. as you see fit, im still working with this also.

im pretty excited to share with everyone what i have learned and all the tools/scripts i've written; they represent a serious amount of work and they should help anyone looking to explore this technology get a jump start into how it works.  you are right about the sparseness of docs, and many tutorials are out of date (including the one @ teegra.net which i started with) i will post a link once ive written it.

---

### Post by narcisgarcia on 2010-01-28
I see that a lot of tutorials are needed, but... who works on tutorials if LXC can change? Actually it doesn't sound possible to make a stable migrator script to automate the change from OpenVZ to LXC of a container maintaining all the features.

Me and other people who decided to work with the help of Ubuntu 8.04 openvz-kernels, we feel that we are in an ambush with LXC.

Is a good news that Ubuntu supports LXC (I hope mature in april 2010), but we are orphaned since Ubuntu 8.10, 9.04 and 9.10 without openvz-kernels, and without any information about the future.

We received a sweet with OpenVZ in Ubuntu 8.04, and some developers say that the sweet is out, and we are now bound to learn a lot of internal technical details, when we need to devote to manage server systems.

**Before taking off OpenVZ easiness, we need a complete userspace utilities, high level tools and tutorials. And there is no bad to maintain OpenVZ while LXC is maturing.**

---

### Post by bodhi.zazen on 2010-01-28
> **narcisgarcia said:**
> I see that a lot of tutorials are needed, but... who works on tutorials if LXC can change? Actually it doesn't sound possible to make a stable migrator script to automate the change from OpenVZ to LXC of a container maintaining all the features.

Me and other people who decided to work with the help of Ubuntu 8.04 openvz-kernels, we feel that we are in an ambush with LXC.

Is a good news that Ubuntu supports LXC (I hope mature in april 2010), but we are orphaned since Ubuntu 8.10, 9.04 and 9.10 without openvz-kernels, and without any information about the future.

We received a sweet with OpenVZ in Ubuntu 8.04, and some developers say that the sweet is out, and we are now bound to learn a lot of internal technical details, when we need to devote to manage server systems.

**Before taking off OpenVZ easiness, we need a complete userspace utilities, high level tools and tutorials. And there is no bad to maintain OpenVZ while LXC is maturing.**

 I agree with what you say, in principle, but in practice it is not so clean.

The OpenVZ Kernel patch is maintained "upstream", by the openVZ developers.

The Ubuntu developers then take the openvz patch, from upstream, and the generic kernel, from upstream, and packaged them into the Ubuntu openvz kernel.

The OpenVZ project , the upstream source, maintains openvz as a large kernel patch and they do not have a stable patch beyond the 2.6.18 Kernel.


[http://wiki.openvz.org/Category:Kernel_download](http://wiki.openvz.org/Category:Kernel_download)

There is a 2.6.24, not stable, a few development releases,  and a RHEL kernel, which is what is used by Proxmox.

Ubuntu uses a more recent kernel.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=kernel+generic](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=kernel+generic)

Hardy - 2.6.24

Intrepid - 2.6.27

...

Lucid - 2.6.32

So what you are asking is for the Ubuntu developers to do is to take over the OpenVZ project and release a patch for the 2.6.32 kernel. 

Not going to happen.

============

The Long term "solution", as has been mentioned in this thread, is LXC.

If you read the links I gave or look at the OpenVZ mailing lists you will see the technical reasoning for this.

Basically LXC is in the mainline kernel and is easier to maintain. Many of the OpenVZ developers are contributing to the LXC project and it is very likely the OpenVZ project will either die off due to a lack of development or the developers will move to LXC, which is more likely.

============

The major problem with LXC at this moment is that it is under rapid development and as is often the case, the documentation has (and can) not keep pace.

Unless you are using a developmental kernel and the lxc tools from git, if you find a bug in LXC, you will be told to upgrade.

Once the project matures a bit, and lxc (user tools) are at version 1.0 (1.0 is the first planned stable release) documentation will lag.

============


With all of the discussion in mind, if you are already familiar with openzv, it seems rather easy to migrate to LXC.

Last night I was able to make a Fedora 12 container that now boots properly. I have made minimal effort to downsize the container, but when I package it up, as I would an openvz template, it is 150 Mb in size, which is not bad at all.

I need to look at Ubuntu Lucid, and the lxc git tools, and write it all into a few blog pages.

So you now have two people who are working on the details. If all goes will I will add a "How to LXC" thread in the Virtualization forums for the upcoming release of lucid, 10.04, similar to my openvz thread.

Now I am just learning and so likely to make mistakes, but I should at least be able to get you (and others) started.

Basically there are several things you need to understand:

1. How to configure LXC on the host node.

2. How to make a container. You either bootstrap/chroot , use an openvz template, or use lxc-debian / lxc-fedora. Each option requires some manual configuration, but many of the lxc scripts are bash scripts , so if you are interested, you could modify the scripts and submit them to the lxc project or post them on a personal blog.

---

### Post by narcisgarcia on 2010-01-28
Since 1 month ago I have a dedicated server with the Ubuntu 10.04 server, focused on play with LXC and to prepare a fast and solid migration of my OpenVZ containers on april.

What can I do?
Without any How-To now I don't know the way to begin.

---

### Post by bodhi.zazen on 2010-01-28
> **narcisgarcia said:**
> Since 1 month ago I have a dedicated server with the Ubuntu 10.04 server, focused on play with LXC and to prepare a fast and solid migration of my OpenVZ containers on april.

What can I do?
Without any How-To now I don't know the way to begin.

Depends on how much time you have. Keep playing with it, start a thread if you get stuck.

Otherwise, I am working on documentation, and hope ot work with [sweetsinse]("http://ubuntuforums.org/member.php?u=417214") and others to generate a few Ubuntu wiki pages / blogs / etc.

At the moment I just made a Fedora 12 "template", the tar.gz is 150 Mb , not bad.

If I extract it it boots and runs normally.

Next step for me is to look at my openvz templates and lucid.

Once I get it up and working, people with more LXC experience can add to it and we can get some documentation going.

Do you know how to use IRC ?

I was thinking of registering a channel for lxc, but in the mean time, if you come over to say #ubuntu-beginners I may be able to help you.

---

### Post by narcisgarcia on 2010-01-28
I don't like chat support, I prefer wikis and forums because here you can participate without being online all the time.
Chat is good when people meets at a concrete time for a concrete question.

We can work in the already existing wiki page in Ubuntu:
[https://wiki.ubuntu.com/ContainersSpec](https://wiki.ubuntu.com/ContainersSpec)

---

### Post by bodhi.zazen on 2010-01-28
Starting a few wiki pages would be a great idea. The one you linked is probably not the best to start posting a "how to LXC" on.

I suggest breaking it into a few pages

LXC - Overview. What is is ? User case examples.

LXC - Host configuration
kernel requiremetns
apt-get install lxc
install lxc from git

LXC - Container configuration / 
options/examples for congig files
chroot/debootstrap/febootstrap
migrate openvz containers
lxc-debian / lxc-fedora
lxc-console / ssh into containers

LXC - Application configuration.

---

### Post by sweetsinse on 2010-01-28
hooray!  you can grab my sources from here:
```
git clone git://devel.extof.me/vps
```
i can't guarantee that will always be up (im doing alot of work with these containers and on these scripts), or that the git repo will be a proper one (when i update it i might break history :p, for a little while at least), but i should be up most the time, and the url wont change.  that url is running in an LXC container created using the tools it's hosting.

**DISCLAIMER** as is, these tools are meant for an archlinux host and WILL NOT work for an ubuntu/debian host.  this is something i intend to change.  in addition, the scripts expect a BTRFS based root filesystem, others (ext3/4/etc) will need to replace btrfsctl commands with "cp -R" and "rm -rf" (i intend to do this in a slick/hacky way... by making a bash function with the same name as btrfsctl when its not available.  when its called it will cp/rm instead) right now i am providing these to help others understand how the lxc-* tools work, and present a setup that works for me, and may for you.  all the scripts together are less than 1000 lines of bash, so a light read :)

**FEATURES**
[LIST=1]
[*]uses btrfs to create efficient "forks" of templates into writable domains (vps)
[*]complete, drop in solution (only add two lines to rc.local)
[*]when you enter a vps from the host, the PS1 will reflect that:
```
cr@ph1 ~ $ vps-enter guest-personal-tony

Type <Ctrl+a q> to exit the console

VPS[guest-personal-tony] cr@extof /srv/git $
```
ONLY if you're entering from the host, if you enter via ssh, the VPS[XXX] part is not there (host is on a real tty, everything else is pty)
[*]by default, a dhcp bridge is created so all guests see each other, and have dns/dhcp/internet access
[*]there is more i swear...
[/LIST]

**KNOWN CAVEATS/BUGS**
[LIST=1]
[*]at least with arch guests, the dhcp never works/times out the first time a vps is booted; this could have something to do with the bridge.  fix by manually restarting network a second time  doesnt affect interfaces that are bridged directly to the LAN, i.e. no dhcp
[*]TERM=linux in a container.  "export TERM=xterm" to get stuff working nicer in vim/maybe others (home/end keys dont work without)
[*]vps-enter will only let one person in a vps at a time, even if the container is configured with more than one tty.  i will update this soon (compare config file to used sockets)
[*]i run misc/check-dev-pts.sh as a cron also.  this makes sure that /dev/ptmx never breaks in the event of a rouge udev process (this only happened once, but had i not caught it i would have been locked out of my server.  only affects those using the newinstance devpts mount flag on the actual host) i dont know how udev did this from inside a container... im not sure what happened.  i dont use udev in containers, they already have the devices they need
[*]i use special entries in the /etc/inittab of containers to handle rebooting/powerdown of containers:
```
p6::ctrlaltdel:/sbin/init 6
p0::powerfail:/sbin/init 0
```
this lets me send, from the host, a SIGINT to reboot, and a SIGPWR to "power down" (with the help of vps-monitor, more on that below).  this trick probably doesnt work with upstart
[*]i havent made an elegant way to edit the configs of an already running domain.
[*]and probably plenty of other things...
[/LIST]

**DEVELOPMENT FUTURE**
[LIST=1]
[*]support other hosts than archlinux
[*]add bash completion scripts
[*]support creating containers that are not archlinux based
[*]harden/extend all scripts by using getopts
[*]colorize everything :)
[*]other things i can't think of ATM
[/LIST]

**HOW TO USE**

place the vps folder at /vps

i create a file, /etc/profile.d/vps.sh, chmod +x it, (i think this will work for ubuntu) and put this in it:
```
# export VPS_ENV and add vps-* scripts to PATH

export EDITOR=vim
export VPS_ENV=/vps/usr/lib/common/env
export PATH="${PATH}:/vps/usr/bin"

# gen the motd
#/vps/usr/cron/motd
```
you dont need the any of it really, except the PATH part if you want to run the commands without their full path.  i included the motd script (pretty) i use on my host server if anyone is interested.

i put this in my /etc/rc.local:
```
#!/bin/bash
#
# /etc/rc.local: Local multi-user startup script.
#

export VPS_ENV=/vps/usr/lib/common/env
/vps/usr/misc/vps-init.sh
```
vps-init.sh is the bootstrap file for the whole process.  start there to understand how everything works, its really not too bad. archlinux has a rc.local.shutdown file where i place the vps-shutdown.sh script... not sure the equiv for ubuntu.

lastly, i create a way to exec this stuff as a regular user.  create a group called vps (this is hard coded for the time being), add the users to it that you want to make/control/stop/see containers, and add this to your sudoers file:
```
%vps    ALL=(root) NOPASSWD: /vps/usr/bin/vps-*
```
when you run the file as a normal user, the script does this:
```
# exec as VPS_USER if need be
if [ -n "${VPS_SUDO}" ] && [ -n "${VPS_USER#$(whoami)}" ]; then
    exec ${VPS_SUDO} ${0} $@
fi
```
this may not be the best way, and might have an infinite loop possibility.  i tried to drop privileges completely by making a vps user instead of root... but there are several things that need root in the scripts and it was too difficult for the time being.  if you dont do this step simply run as root, it will Just Work.  any suggestions welcome.

**BREAKDOWN OF FILES**

all the vps-* commands will dispay a usage when invoked with no arguments.  i eventually want to use getopts. here is the file hierarchy and what everything does:
```
vps
&#9500;&#9472;&#9472; def
&#9474;   &#9500;&#9472;&#9472; exec
&#9474;   &#9474;   &#9500;&#9472;&#9472; proc
&#9474;   &#9474;   &#9492;&#9472;&#9472; sys
&#9474;   &#9492;&#9472;&#9472; mnt
&#9500;&#9472;&#9472; dom
&#9500;&#9472;&#9472; log
&#9500;&#9472;&#9472; tpl
&#9500;&#9472;&#9472; usr
&#9474;   &#9500;&#9472;&#9472; bin
&#9474;   &#9474;   &#9500;&#9472;&#9472; vps-create
&#9474;   &#9474;   &#9500;&#9472;&#9472; vps-enter
&#9474;   &#9474;   &#9500;&#9472;&#9472; vps-ls
&#9474;   &#9474;   &#9500;&#9472;&#9472; vps-mkdom
&#9474;   &#9474;   &#9500;&#9472;&#9472; vps-mktpl
&#9474;   &#9474;   &#9500;&#9472;&#9472; vps-reboot
&#9474;   &#9474;   &#9500;&#9472;&#9472; vps-rmdom
&#9474;   &#9474;   &#9500;&#9472;&#9472; vps-rmtpl
&#9474;   &#9474;   &#9500;&#9472;&#9472; vps-start
&#9474;   &#9474;   &#9500;&#9472;&#9472; vps-stop
&#9474;   &#9474;   &#9492;&#9472;&#9472; vps-tree
&#9474;   &#9500;&#9472;&#9472; conf
&#9474;   &#9474;   &#9492;&#9472;&#9472; dnsmasq-dhcpbr0.conf
&#9474;   &#9500;&#9472;&#9472; cron
&#9474;   &#9474;   &#9492;&#9472;&#9472; motd
&#9474;   &#9500;&#9472;&#9472; doc
&#9474;   &#9474;   &#9500;&#9472;&#9472; BUGS
&#9474;   &#9474;   &#9500;&#9472;&#9472; INSTALL
&#9474;   &#9474;   &#9492;&#9472;&#9472; TODO
&#9474;   &#9500;&#9472;&#9472; lib
&#9474;   &#9474;   &#9500;&#9472;&#9472; common
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; color
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; env
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; function
&#9474;   &#9474;   &#9500;&#9472;&#9472; exec
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; vps-monitor
&#9474;   &#9474;   &#9492;&#9472;&#9472; static
&#9474;   &#9474;       &#9500;&#9472;&#9472; autologin
&#9474;   &#9474;       &#9500;&#9472;&#9472; bash.bashrc.local
&#9474;   &#9474;       &#9500;&#9472;&#9472; rc.conf
&#9474;   &#9474;       &#9500;&#9472;&#9472; rc.shutdown
&#9474;   &#9474;       &#9500;&#9472;&#9472; rc.single
&#9474;   &#9474;       &#9492;&#9472;&#9472; rc.sysinit
&#9474;   &#9492;&#9472;&#9472; misc
&#9474;       &#9500;&#9472;&#9472; check-dev-pts.sh
&#9474;       &#9500;&#9472;&#9472; start-brctl-dhcpbr0.sh
&#9474;       &#9500;&#9472;&#9472; start-dnsmasq-dhcpbr0.sh
&#9474;       &#9500;&#9472;&#9472; start-iptables-dhcpbr0.sh
&#9474;       &#9500;&#9472;&#9472; start-mount-cgroup.sh
&#9474;       &#9500;&#9472;&#9472; stop-brctl-dhcpbr0.sh
&#9474;       &#9500;&#9472;&#9472; stop-dnsmasq-dhcpbr0.sh
&#9474;       &#9500;&#9472;&#9472; stop-iptables-dhcpbr0.sh
&#9474;       &#9500;&#9472;&#9472; stop-mount-cgroup.sh
&#9474;       &#9500;&#9472;&#9472; vps-init.sh
&#9474;       &#9492;&#9472;&#9472; vps-shutdown.sh
&#9492;&#9472;&#9472; var
    &#9492;&#9472;&#9472; run
```
/vps/def/*
[INDENT]definition (conf) files for each process (proc) container, or system (sys) container.  also mount (mnt) definition files[/INDENT]
/vps/dom
[INDENT]domains.  where all your system containers will be[/INDENT]
/vps/log
[INDENT]logs.  when domains are started, output from the init process is logged here.  i will probably extend this to log events from the vps-* scripts too[/INDENT]
/vps/tpl
[INDENT]templates.  system templates that will be forked (BTRFS) or copied (others) to usable domains[/INDENT]
/vps/usr/bin
[LIST]
[*]vps-create: define a domain that has been made with vps-mkdom
[*]vps-enter: enter a running domain that has a free tty slot
[*]vps-ls: show the status of defined domains and/or templates
[*]vps-mkdom: create a dom from an existing template
[*]vps-mktpl: create a template from a list of predefined packs
[*]vps-reboot: send a SIGINT to the init process of a running domain
[*]vps-rmdom: delete a dom that isnt running
[*]vps-rmtpl: remove a template
[*]vps-start: start a dom that has been defined with vps-create, or has been stopped by vps-stop
[*]vps-stop: stop a running domain
[*]vps-tree: use the tree command to get a view of the folders (this will fail horribly without BTRFS... it uses the -x flag to avoid traversing into dom/tpl directories... useless without that)
[/LIST]
/vps/usr/conf
[INDENT]config files.  right now only for dnsmasq[/INDENT]
/vps/usr/cron
[INDENT]not really crons, used to be.  right now just the motd file i use[/INDENT]
/vps/usr/doc
[INDENT]self explanatory?[/INDENT]
/vps/usr/lib
[LIST]
[*]common: files included by other scripts (function isnt used)
[*]exec: executables from other scripts.  vps-monitor is the only one right now, its job is to monitor the utmp file in a container and determine if the container should be killed or rebooted based off the runlevel.  should still work for upstart. see here for more details: [http://www.mail-archive.com/lxc-users@lists.sourceforge.net/msg00040.html](http://www.mail-archive.com/lxc-users@lists.sourceforge.net/msg00040.html)
[*]static: files copied verbatim to containers
[/LIST]
/vps/usr/misc
[INDENT]i dont like this folder or its name.  right now it has all the bootstrap files[/INDENT]
/vps/var/cgroup
[INDENT]you dont see this in the tree view, but it will be created, and the cgroup filesystem mounted here (i dont make it because git cant track empty folders without at least a .gitignore file... but then when it's mounted git complains that the .gitignore file is no longer there AND wants to place the entire cgroup under revision control... annoying)[/INDENT]
/vps/var/run
[INDENT]has pidfiles (dnsmasq) and whatnot[/INDENT]


some of this structure is definately going to change as i break things off, esp. once i start adding support for other templates than archlinux.

as always, comments welcome.

---

### Post by narcisgarcia on 2010-01-29
sweetsinse, you are docummenting in the Ubuntu forums a solution for archlinux, that is not a solution for Ubuntu.

I suggest you post the Arch Linux information here:
[http://bbs.archlinux.org/](http://bbs.archlinux.org/)

---

### Post by narcisgarcia on 2010-01-29
Started on:
[https://help.ubuntu.com/community/LXC](https://help.ubuntu.com/community/LXC)

---

### Post by bodhi.zazen on 2010-01-29
Thank you for starting a wiki page narcisgarcia.

I got a little farther with a lucid container last night, but it still does not boot. I believe there is a problem with the init / upstart scripts , but the upstart script I wrote did not work either so I am at a loss.

I added a little to your start =)

---

### Post by sweetsinse on 2010-01-29
Really?  I know where the arch forums are, believe me... I posted that because anyone who is serious about using lxc in production will be able to glean much valuable information from those scripts.   They work.  Right now.  Did I mention it will soon work for ubuntu? I think so... It only needs a small amount of work to work with ubuntu.  Of course there is always the option of writing a solution from scratch yourself, after the pain of research that I have already endured.

They contain direction about how to get information from the cgroup filesystem, how to create a NAT bridge, lxc config file examples, the kernel configuration, devpts configuration, and many other things that you will need to understand.

unfortunately, I don't have the time to get ubuntu working flawlessly as a host or container ATM.  I put that out there as an oppurtunity for you to get a jumpstart into lxc by looking at a working implementation, that is all.

---

### Post by bodhi.zazen on 2010-01-29
> **sweetsinse said:**
> Really?  I know where the arch forums are, believe me... I posted that because anyone who is serious about using lxc in production will be able to glean much valuable information from those scripts.   They work.  Right now.  Did I mention it will soon work for ubuntu? I think so... It only needs a small amount of work to work with ubuntu.  Of course there is always the option of writing a solution from scratch yourself, after the pain of research that I have already endured.

They contain direction about how to get information from the cgroup filesystem, how to create a NAT bridge, lxc config file examples, the kernel configuration, devpts configuration, and many other things that you will need to understand.

unfortunately, I don't have the time to get ubuntu working flawlessly as a host or container ATM.  I put that out there as an oppurtunity for you to get a jumpstart into lxc by looking at a working implementation, that is all.

Thank you for sharing your scripts. I agree there is some generic information there, I also agree they are indeed sophistocated, give people time to digest the info.

Along those lines, I tried to get your scipts, but it did not work.

I entered 

```
git clone git://devel.extof.me/vps
```

And nothing happened, no error message.

Is there something about git I do not understand ?

---

### Post by sweetsinse on 2010-01-29
you should see something like this:
```
cr@extofme-m0 ~/hi $ git clone git://devel.extof.me/vps
Initialized empty Git repository in /home/cr/hi/vps/.git/
remote: Counting objects: 56, done.
remote: Compressing objects: 100% (49/49), done.
remote: Total 56 (delta 8), reused 0 (delta 0)
Receiving objects: 100% (56/56), 18.74 KiB, done.
Resolving deltas: 100% (8/8), done.
cr@extofme-m0 ~/hi $ ls -l vps/
total 0
drwxr-xr-x 1 cr cr 14 Jan 29 11:30 def
drwxr-xr-x 1 cr cr 20 Jan 29 11:30 dom
drwxr-xr-x 1 cr cr 20 Jan 29 11:30 log
drwxr-xr-x 1 cr cr 20 Jan 29 11:30 tpl
drwxr-xr-x 1 cr cr 42 Jan 29 11:30 usr
drwxr-xr-x 1 cr cr 26 Jan 29 11:30 var
cr@extofme-m0 ~/hi $
```
you have git installed right?  i think the package is called git-core (i know its not called git) in ubuntu.  also my DNS maybe hasnt fully propagated yet, try:
```
git clone git://extof.me/vps
```

---

### Post by bodhi.zazen on 2010-01-29
The repository is working now, thank you

---

### Post by narcisgarcia on 2010-01-29
Ok sweetsinse, I didn't understood the contribution.

---

### Post by sweetsinse on 2010-01-29
if i can get a static copy of debootstrap, i can work on building a lucid container under my working host.

is that what this package is:

[http://packages.debian.org/squeeze/cdebootstrap-static](http://packages.debian.org/squeeze/cdebootstrap-static)

seems like it but i haven't tried yet; perhaps one of you already knows.  my host is arch so i have to convert the package (i.e. i need to get debootstrap working in non debian), would rather not waste time if its not what i need.

EDIT: actually it looks like arch has a copy of debootstrap in the user repositories (AUR).  i'll see what i can do.

---

### Post by bodhi.zazen on 2010-01-29
[http://packages.ubuntu.com/lucid/debootstrap](http://packages.ubuntu.com/lucid/debootstrap)

The version from Arch will almost certainly pull Debian.

You can specify the repo on the command line :

[https://help.ubuntu.com/9.10/installation-guide/i386/linux-upgrade.html](https://help.ubuntu.com/9.10/installation-guide/i386/linux-upgrade.html)

---

### Post by sweetsinse on 2010-01-29
bodhi.zazen, im getting the same probs as _i think_ you mentioned before:
```
ph1 ~ # lxc-start -n guest-test-ubuntu_lucid
init: ureadahead main process (4) terminated with status 5
mountall: Could not connect to Plymouth                   
mountall: Event failed                                    
mountall: Event failed                                    
mountall: Event failed
```
after which upstart sems to do nothing.  im not as familiar with upstart... is there a way to enable more verbose output?  or what have you done so far?

this was a raw bootstrap of lucid with no alterations yet, although im going to keep hacking at it

---

### Post by bodhi.zazen on 2010-01-29
> **sweetsinse said:**
> bodhi.zazen, im getting the same probs as _i think_ you mentioned before:
```
ph1 ~ # lxc-start -n guest-test-ubuntu_lucid
init: ureadahead main process (4) terminated with status 5
mountall: Could not connect to Plymouth                   
mountall: Event failed                                    
mountall: Event failed                                    
mountall: Event failed
```after which upstart sems to do nothing.  im not as familiar with upstart... is there a way to enable more verbose output?  or what have you done so far?

this was a raw bootstrap of lucid with no alterations yet, although im going to keep hacking at it

I believe it is a problem with the upstart scripts as well, similar problems with Ubuntu openvz templates.

I tried using the same scripts as from an Ubuntu 9.10 openvz template, no joy.

Need to look at the boot scripts, but I am not overly familiar with them either, lol.

---

### Post by ibuclaw on 2010-01-29
Thanks for this thread (bodhi poked me to have a look at it after having some minor interest).

I'll have a play, and see if I can get anything working. ;)

---

### Post by sweetsinse on 2010-01-29
well i went thru all/most of the upstart event files i think.  i made a small wrapper for upstart:
```
#!/bin/bash

exec /sbin/init --debug
```
and this is what i got... trying to make sense of everything that is going on, maybe someone more familiar will see something useful:
```
ph1 ~ # lxc-start -n guest-test-ubuntu_lucid2 /upwrap.sh
Loading configuration from /etc/init.conf               
Loading configuration from /etc/init                    
conf_reload_path: Loading control-alt-delete from /etc/init/control-alt-delete.conf
conf_reload_path: Loading dmesg from /etc/init/dmesg.conf                          
conf_reload_path: Loading hostname from /etc/init/hostname.conf                    
conf_reload_path: Loading hwclock-save from /etc/init/hwclock-save.conf            
conf_reload_path: Loading hwclock from /etc/init/hwclock.conf                      
conf_reload_path: Loading module-init-tools from /etc/init/module-init-tools.conf  
conf_reload_path: Loading mountall-net from /etc/init/mountall-net.conf            
conf_reload_path: Loading mountall-reboot from /etc/init/mountall-reboot.conf      
conf_reload_path: Loading mountall-shell from /etc/init/mountall-shell.conf        
conf_reload_path: Loading mountall from /etc/init/mountall.conf                    
conf_reload_path: Loading mounted-dev from /etc/init/mounted-dev.conf              
conf_reload_path: Loading mounted-tmp from /etc/init/mounted-tmp.conf              
conf_reload_path: Loading mounted-varrun from /etc/init/mounted-varrun.conf        
conf_reload_path: Loading network-interface-security from /etc/init/network-interface-security.conf
conf_reload_path: Loading network-interface from /etc/init/network-interface.conf                  
conf_reload_path: Loading networking from /etc/init/networking.conf                                
conf_reload_path: Loading procps from /etc/init/procps.conf                                        
conf_reload_path: Loading rc-sysinit from /etc/init/rc-sysinit.conf                                
conf_reload_path: Loading rc from /etc/init/rc.conf                                                
conf_reload_path: Loading rcS from /etc/init/rcS.conf                                              
conf_reload_path: Loading rsyslog-kmsg from /etc/init/rsyslog-kmsg.conf                            
conf_reload_path: Loading rsyslog from /etc/init/rsyslog.conf                                      
conf_reload_path: Loading tty1 from /etc/init/tty1.conf                                            
conf_reload_path: Loading tty2 from /etc/init/tty2.conf                                            
conf_reload_path: Loading tty3 from /etc/init/tty3.conf                                            
conf_reload_path: Loading tty4 from /etc/init/tty4.conf                                            
conf_reload_path: Loading tty5 from /etc/init/tty5.conf                                            
conf_reload_path: Loading tty6 from /etc/init/tty6.conf                                            
conf_reload_path: Loading udev-finish from /etc/init/udev-finish.conf                              
conf_reload_path: Loading udev from /etc/init/udev.conf                                            
conf_reload_path: Loading udevmonitor from /etc/init/udevmonitor.conf                              
conf_reload_path: Loading udevtrigger from /etc/init/udevtrigger.conf                              
conf_reload_path: Loading upstart-udev-bridge from /etc/init/upstart-udev-bridge.conf              
conf_reload_path: Loading ureadahead-other from /etc/init/ureadahead-other.conf                    
conf_reload_path: Loading ureadahead from /etc/init/ureadahead.conf                                
init: event_new: Pending startup event                                                             
init: Handling startup event                                                                       
init: event_pending_handle_jobs: New instance mountall                                             
init: mountall goal changed from stop to start                                                     
init: mountall state changed from waiting to starting                                              
init: event_new: Pending starting event                                                            
init: event_pending_handle_jobs: New instance hostname                                             
init: hostname goal changed from stop to start                                                     
init: hostname state changed from waiting to starting                                              
init: event_new: Pending starting event                                                            
init: Handling starting event                                                                      
init: event_pending_handle_jobs: New instance hwclock                                              
init: hwclock goal changed from stop to start                                                      
init: hwclock state changed from waiting to starting                                               
init: event_new: Pending starting event                                                            
init: event_pending_handle_jobs: New instance ureadahead                                           
init: ureadahead goal changed from stop to start                                                   
init: ureadahead state changed from waiting to starting                                            
init: event_new: Pending starting event                                                            
init: Handling starting event                                                                      
init: event_finished: Finished starting event                                                      
init: hostname state changed from starting to pre-start                                            
init: hostname state changed from pre-start to spawned                                             
init: hostname main process (2)                                                                    
init: hostname state changed from spawned to post-start                                            
init: hostname state changed from post-start to running                                            
init: event_new: Pending started event                                                             
init: Handling starting event                                                                      
init: event_finished: Finished starting event                                                      
init: hwclock state changed from starting to pre-start                                             
init: hwclock state changed from pre-start to spawned                                              
init: hwclock main process (3)                                                                     
init: hwclock state changed from spawned to post-start                                             
init: hwclock state changed from post-start to running                                             
init: event_new: Pending started event                                                             
init: Handling starting event                                                                      
init: event_finished: Finished starting event                                                      
init: ureadahead state changed from starting to pre-start                                          
init: ureadahead state changed from pre-start to spawned                                           
init: ureadahead main process (4)                                                                  
init: Handling started event                                                                       
init: event_finished: Finished started event                                                       
init: Handling started event                                                                       
init: event_finished: Finished started event                                                       
init: job_process_handler: Ignored event 1 (0) for process 2                                       
init: hostname main process (2) exited normally                                                    
init: hostname goal changed from start to stop                                                     
init: hostname state changed from running to stopping                                              
init: event_new: Pending stopping event                                                            
init: job_process_handler: Ignored event 20 (5) for process 4                                      
init: Handling stopping event                                                                      
init: event_finished: Finished stopping event                                                      
init: hostname state changed from stopping to killed                                               
init: hostname state changed from killed to post-stop                                              
init: hostname state changed from post-stop to waiting                                             
init: event_new: Pending stopped event                                                             
init: job_change_state: Destroyed inactive instance hostname                                       
init: Handling stopped event                                                                       
init: event_finished: Finished stopped event                                                       
init: job_process_handler: Ignored event 1 (0) for process 3                                       
init: hwclock main process (3) exited normally                                                     
init: hwclock goal changed from start to stop                                                      
init: hwclock state changed from running to stopping                                               
init: event_new: Pending stopping event                                                            
init: Handling stopping event                                                                      
init: event_finished: Finished stopping event                                                      
init: hwclock state changed from stopping to killed                                                
init: hwclock state changed from killed to post-stop                                               
init: hwclock state changed from post-stop to waiting                                              
init: event_new: Pending stopped event                                                             
init: job_change_state: Destroyed inactive instance hwclock                                        
init: Handling stopped event                                                                       
init: event_finished: Finished stopped event                                                       
init: job_process_handler: Ignored event 1 (5) for process 4                                       
init: ureadahead main process (4) terminated with status 5                                         
init: ureadahead goal changed from start to stop                                                   
init: ureadahead state changed from spawned to stopping                                            
init: event_new: Pending stopping event                                                            
init: event_finished: Finished starting event                                                      
init: mountall state changed from starting to pre-start                                            
init: mountall state changed from pre-start to spawned                                             
init: mountall main process (5)                                                                    
init: event_new: Pending starting/failed event                                                     
init: Handling stopping event                                                                      
init: event_finished: Finished stopping event                                                      
init: ureadahead state changed from stopping to killed                                             
init: ureadahead state changed from killed to post-stop                                            
init: ureadahead state changed from post-stop to waiting                                           
init: event_new: Pending stopped event                                                             
init: job_change_state: Destroyed inactive instance ureadahead                                     
init: Handling starting/failed event                                                               
init: event_finished: Finished starting/failed event                                               
init: Handling stopped event                                                                       
init: event_finished: Finished stopped event                                                       
init: job_process_handler: Ignored event 20 (5) for process 5                                      
init: job_process_handler: Ignored event 40 (4) for process 5                                      
init: mountall main process (5) executable changed                                                 
init: Connection from private client                                                               
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/mountall_2dnet                   
mountall: Could not connect to Plymouth                                                            
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/rc                               
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/rsyslog                          
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/tty4                             
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/udev                             
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/upstart_2dudev_2dbridge          
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/ureadahead_2dother               
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/hwclock_2dsave                   
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/tty5                             
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/control_2dalt_2ddelete           
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/hwclock                          
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/module_2dinit_2dtools            
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/mountall                         
init: job_register: Registered instance /com/ubuntu/Upstart/jobs/mountall/_                        
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/rcS                              
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/mounted_2dvarrun                 
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/rc_2dsysinit                     
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/tty2                             
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/udevtrigger                      
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/mounted_2ddev                    
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/rsyslog_2dkmsg                   
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/tty3                             
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/udev_2dfinish                    
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/hostname                         
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/mountall_2dreboot                
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/mountall_2dshell                 
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/mounted_2dtmp                    
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/network_2dinterface              
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/tty1                             
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/udevmonitor                      
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/dmesg                            
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/network_2dinterface_2dsecurity   
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/networking                       
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/procps                           
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/tty6                             
init: job_class_register: Registered job /com/ubuntu/Upstart/jobs/ureadahead                       
init: job_process_handler: Ignored event 20 (19) for process 6                                     
init: job_process_handler: Ignored event 40 (1) for process 5                                      
init: mountall main process (5) became new process (6)                                             
init: job_process_handler: Ignored event 20 (19) for process 7                                     
init: job_process_handler: Ignored event 40 (1) for process 6                                      
init: mountall main process (6) became new process (7)                                             
init: mountall state changed from spawned to post-start                                            
init: mountall state changed from post-start to running                                            
init: event_new: Pending started event                                                             
init: job_process_handler: Ignored event 1 (0) for process 5                                       
init: Handling started event                                                                       
init: event_finished: Finished started event                                                       
init: job_process_handler: Ignored event 1 (0) for process 6                                       
init: event_new: Pending mounted event                                                             
init: Handling mounted event                                                                       
init: event_finished: Finished mounted event                                                       
init: event_new: Pending all-swaps event                                                           
init: Handling all-swaps event                                                                     
init: event_finished: Finished all-swaps event                                                     
init: event_new: Pending mounted event                                                             
init: Handling mounted event                                                                       
init: event_finished: Finished mounted event                                                       
init: event_new: Pending mounted event                                                             
init: Handling mounted event                                                                       
init: event_finished: Finished mounted event                                                       
init: event_new: Pending mounted event                                                             
init: Handling mounted event                                                                       
init: event_finished: Finished mounted event                                                       
init: event_new: Pending mounted event                                                             
init: Handling mounted event
init: event_finished: Finished mounted event
init: event_new: Pending mounted event
init: Handling mounted event
init: event_finished: Finished mounted event
init: event_new: Pending mounted event
init: Handling mounted event
init: event_finished: Finished mounted event
init: event_new: Pending mounted event
init: Handling mounted event
init: event_finished: Finished mounted event
init: event_new: Pending mounting event
init: Handling mounting event
init: event_finished: Finished mounting event
init: event_new: Pending mounted event
init: Handling mounted event
init: event_finished: Finished mounted event
init: event_new: Pending mounting event
init: Handling mounting event
init: event_finished: Finished mounting event
init: event_new: Pending mounted event
init: Handling mounted event
init: event_finished: Finished mounted event
init: event_new: Pending mounting event
init: Handling mounting event
init: event_finished: Finished mounting event
init: event_new: Pending mounted event
init: Handling mounted event
init: event_finished: Finished mounted event
init: event_new: Pending mounting event
init: Handling mounting event
init: event_finished: Finished mounting event
mountall: Event failed
mountall: Event failed
mountall: Event failed
```
but it still doesnt seem to tell me exactly whats failing.

---

### Post by sweetsinse on 2010-01-29
i modified /etc/init/mountall.conf to try and figure out why it was failing.  i changed the line:

exec mountall --daemon $force_fsck $fsck_fix

to:

exec mountall --debug --daemon $force_fsck $fsck_fix > /tmp/mountall 2>&1

480 lines of output, most looks ok, but these parts fail:
```
...
spawn: mount -a -t devtmpfs,tmpfs -o mode=0755 none /dev
mountall: Event failed
...
spawn: mount -a -t tmpfs -o nosuid,nodev none /dev/shm
mountall: Event failed
...
spawn: mount -a -t tmpfs -o mode=0755,nosuid none /var/run
mountall: Event failed
...
```

am am going to try disabling them, and adding those mounts to the lxc config, right now i have all lxc-based mounting disabled (i thought maybe that was the three failing but its not)

ill update in a few min

EDIT: hmm well you cant really mount /dev and /dev/shm from the lxc config, because once you mount dev as tmpfs, its empty and thus there is no place to mount shm.  ubuntu already had static devices in dev, and shm isnt critical, so i disabled them... and got a little further:
```
 6229 pts/1    S+     0:00 lxc-start -n guest-test-ubuntu_lucid2
 6230 ?        Ss     0:00 /sbin/init
 6264 ?        S      0:00 upstart-udev-bridge --daemon
 6268 ?        Ss     0:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
 6270 ?        S<s    0:00 udevd --daemon
 6271 ?        Sl     0:00 rsyslogd -c4
 6361 ?        S<     0:00 /sbin/udevd --daemon
 6372 ?        S<     0:00 /sbin/udevd --daemon
```
but upstart now seems to hang waiting for udev to finish (i had the same issue with arch, i removed udev from initscripts):
```
...
...
...
init: udev main process (36) became new process (40)
init: udev state changed from spawned to post-start
init: udev state changed from post-start to running
init: event_new: Pending started event
init: event_finished: Finished virtual-filesystems event
init: Handling started event
init: job_register: Registered instance /com/ubuntu/Upstart/jobs/module_2dinit_2dtools/_
init: event_pending_handle_jobs: New instance module-init-tools
init: module-init-tools goal changed from stop to start
init: module-init-tools state changed from waiting to starting
init: event_new: Pending starting event
init: job_register: Registered instance /com/ubuntu/Upstart/jobs/udevtrigger/_
init: event_pending_handle_jobs: New instance udevtrigger
init: udevtrigger goal changed from stop to start
init: udevtrigger state changed from waiting to starting
init: event_new: Pending starting event
```
going to try and kill udev completely because its really not needed

---

### Post by sweetsinse on 2010-01-30
yay, i managed to get into a raw debootstrapped lucid container.  i had to:

[LIST=1]
[*]uncomment /dev, /dev/shm, and /var/run in /lib/init/fstab
[*](re)move /etc/init/udev* and /etc/init/upstart-udev-bridge.conf
[*]remove "and started udev" condition from /etc/init/module-init-tools.conf (although this is probably moot... i'm pretty sure you cant modprobe from inside a container)
[*]remove "and stopped udevtrigger" condition from /etc/init/networking.conf
[*]remove "and net-device-up IFACE=lo" condition from /etc/init/rc-sysinit.conf
[/LIST]

i think lxc is setting up the loopback device for you, and thus the needed event is not firing to trigger rc-sysinit.  after this i was able to lxc-console into the lucid container:
```
ph1 guest-test-ubuntu_lucid2 # lxc-console -n guest-test-ubuntu_lucid2

Type <Ctrl+a q> to exit the console

Ubuntu lucid (development branch) guest-test-ubuntu_lucid2 tty1

guest-test-ubuntu_lucid2 login: root
Password:
Last login: Sat Jan 30 05:10:18 UTC 2010 on tty1
Linux guest-test-ubuntu_lucid2 2.6.32-ARCH #1 SMP PREEMPT Fri Jan 1 06:07:00 CST 2010 i686

For official documentation, please visit:
 * http://help.ubuntu.com/
root@guest-test-ubuntu_lucid2:~#
```
i dont know the default pass, i chrooted in and manually changed it with passwd beforehand.

---

### Post by bodhi.zazen on 2010-01-30
Very nice. I spent last night building a Fedora 12 container.

By default, there is no root password, ubuntu uses sudo, so you either need to make a new user with sudo access or set a root password.

---

### Post by bodhi.zazen on 2010-02-01
> **sweetsinse said:**
> yay, i managed to get into a raw debootstrapped lucid container.  i had to:

[LIST=1]
[*]uncomment /dev, /dev/shm, and /var/run in /lib/init/fstab
[*](re)move /etc/init/udev* and /etc/init/upstart-udev-bridge.conf
[*]remove "and started udev" condition from /etc/init/module-init-tools.conf (although this is probably moot... i'm pretty sure you cant modprobe from inside a container)
[*]remove "and stopped udevtrigger" condition from /etc/init/networking.conf
[*]remove "and net-device-up IFACE=lo" condition from /etc/init/rc-sysinit.conf
[/LIST]

i think lxc is setting up the loopback device for you, and thus the needed event is not firing to trigger rc-sysinit.  after this i was able to lxc-console into the lucid container:
```
ph1 guest-test-ubuntu_lucid2 # lxc-console -n guest-test-ubuntu_lucid2

Type <Ctrl+a q> to exit the console

Ubuntu lucid (development branch) guest-test-ubuntu_lucid2 tty1

guest-test-ubuntu_lucid2 login: root
Password:
Last login: Sat Jan 30 05:10:18 UTC 2010 on tty1
Linux guest-test-ubuntu_lucid2 2.6.32-ARCH #1 SMP PREEMPT Fri Jan 1 06:07:00 CST 2010 i686

For official documentation, please visit:
 * http://help.ubuntu.com/
root@guest-test-ubuntu_lucid2:~#
```i dont know the default pass, i chrooted in and manually changed it with passwd beforehand.

I tried to get an ubuntu container up yesterday and can only partially replicate your results.

I can not access the container with lxc-console, it hangs, no matter what I did.

The container will not start when using the -d option

lxc-start -d -n ubuntu 

With the -d option, ssh server does not start and the container is NOT assigned an "eth0" and ipaddress.

The container starts, at least partially. The container is assigned an eth0, an ipaddress, and I can ssh into it. When I ssh in it seems to be functioning , although I did not do extensive testing. 

lxc-console still fails to connect, it hangs with no log in prompt.

---

### Post by sweetsinse on 2010-02-01
i updated that bug with some possibilities, but basically i think the -d thing is either outdated lxc-* tools or the issue i have where DHCP networking never starts the first time a container is booting (i swear it has something to do with the bridge not forwarding packets initially but im not sure)

can you confirm a getty is running on a tty1 inside the container?  lxc-console should not hang (you should still be able to exit w/ctrl-a q) but you will not have a prompt unless the container is configured with tty's:

lxc.tty = N

(N=number of ttys to enable) AND there are processes inside the container running on those ttys.  this is the config i was using to produce the results i posted above:

lxc.rootfs = /vps/dom/guest-test-ubuntu_lucid2/rootfs
lxc.mount = /vps/def/mnt/guest-test-ubuntu_lucid2.conf
lxc.utsname = guest-test-ubuntu_lucid2
lxc.tty = 1
lxc.pts = 1024
lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = dhcpbr0
lxc.network.name = eth0
lxc.network.mtu = 1500

i have been working on completely revamping my scripts and setup to support distribution profiles, non-BTRFS filestystems, and non-Archlinux hosts, in addition to extensive internal documentation and proper option processing.  i am a few days away from being done with this, and will update when done.

---

### Post by bodhi.zazen on 2010-02-01
I have it working now =)

---

### Post by bodhi.zazen on 2010-02-05
This is how I was able to manage :

Host node configuration : [http://blog.bodhizazen.net/linux/lxc-linux-containers/](http://blog.bodhizazen.net/linux/lxc-linux-containers/)

Ubuntu (Lucid): [http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/](http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/)

Fedora 12 & Rawhide: [http://blog.bodhizazen.net/linux/lxc-configure-fedora-containers/](http://blog.bodhizazen.net/linux/lxc-configure-fedora-containers/)

---

### Post by narcisgarcia on 2010-02-06
On a today's updated Ubuntu 10.04 Server, I've tried your [specific tutorial for Ubuntu]("http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/") and just running this command:
```
debootstrap –variant=minbase lucid rootfs.ubuntu # two – - in front of “- -variant”
```
The system answer is:
> E: No such script: /usr/share/debootstrap/scripts/–variant=minbase

With your [other general tutorial]("http://blog.bodhizazen.net/linux/lxc-linux-containers/"), my steps in the same scenario were:
```

sudo mkdir /virtuals
sudo apt-get install lxc bridge-utils debootstrap
sudo mkdir /virtuals/rootfs
sudo mkdir /virtuals/cgroup
echo "none /virtuals/cgroup cgroup defaults 0 0" >>/etc/fstab
mount /virtuals/cgroup
sudo apt-get remove network-manager network-manager-gnome
cd /virtuals
wget http://download.openvz.org/template/precreated/contrib/ubuntu-9.04-i386-minimal.tar.gz
sudo mkdir /virtuals/rootfs/prova1
cd /virtuals/rootfs/prova1
sudo tar -x /virtuals/ubuntu-9.04-i386-minimal.tar.gz

```
This server has already static IP; I've added the following to /etc/network/interfaces
```

auto br0
	iface br0 inet static
	address 192.168.2.249
	netmask 255.255.255.0
	broadcast 192.168.2.255
	gateway 192.168.2.254
	bridge_ports eth0
	bridge_stp off
	bridge_maxwait 5
	post-up /usr/sbin/brctl setfd br0 0

```
```
sudo mkdir /virtuals/configs
```
Created a file /virtuals/configs/prova1.conf with the folowing:
```

lxc.utsname = prova1
lxc.tty = 4
lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = br0
lxc.network.name = eth0
lxc.network.mtu = 1500
lxc.network.ipv4 = 192.168.2.0/24
lxc.rootfs = /virtuals/rootfs/prova1
lxc.cgroup.devices.deny = a
# /dev/null and zero
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
# consoles
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
lxc.cgroup.devices.allow = c 4:0 rwm
lxc.cgroup.devices.allow = c 4:1 rwm
# /dev/{,u}random
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
# /dev/pts/* - pts namespaces are "coming soon"
lxc.cgroup.devices.allow = c 136:* rwm
lxc.cgroup.devices.allow = c 5:2 rwm
# rtc
lxc.cgroup.devices.allow = c 254:0 rwm

```
And when run this command:
```
sudo lxc-start -n prova1
```
This is the result:
> 
lxc-start: failed to attach 'vethV6UMCJ' to the bridge 'br0'
lxc-start: failed to create netdev
lxc-start: failed to create the network
lxc-start: failed to spawn '/sbin/init'
lxc-start: No such file or directory - failed to remove cgroup '/virtuals/cgroup/prova1'


---

### Post by bodhi.zazen on 2010-02-07
You are mixing apples and oranges and I can not follow what you are doing, installing lucid from debootstrap or converting a working openvz template.

With deboostrap, that error message looks nothing like what you should be running.

```
debootstrap --variant=minbase lucid rootfs.ubuntu
```As far as openz goes, other then extracting the tar , what did you do to convert the container ? As far as I understand you can not simply extract an openvz template and expect it to work. In addition, I have not been able to get a karmic (9.10) container working, I have not tried that hard as 10.04 is a LTS.

I have no way of confirming that your bridge is working or your config file is correct.

---

### Post by juancarlospaco on 2010-02-07
**bodhi.zazen would be nice Renaming and Sticking this thread*** (or merge)*.
The sticked one is pretty old.

---

### Post by bodhi.zazen on 2010-02-14
> **juancarlospaco said:**
> **bodhi.zazen would be nice Renaming and Sticking this thread*** (or merge)*.
The sticked one is pretty old.

Aye.

I plan to update the Virtulization sticky for 10/04 (LTS releases).

LXC is up and coming, no doubt, but it is a bit of a hassle at the moment so hard to encourage people to use LXC with a sticky just yet.

Hopefully LXC will receive the attention of the Ubuntu developers, at the moment is does not seem to be the case as of yet.

---

### Post by sweetsinse on 2010-02-14
i have done a major update to vps-lxc tools, and i _think_ should at least run on ubuntu.  i have not completed the template files for building debian/ubuntu containers.  bodhi.zazen, you might be interested in that, only 1 file need to be created to enable ubutnu build support; i will do it soon otherwise.

here is how you can try:
```
$ sudo git clone git://github.com/extofme/vps-lxc.git /vps
$ sudo /vps/struct
$ sudo mount -t cgroup lxc /vps/dev/vps-lxc
$ sudo ln -s /vps/etc/profile.d/vps-lxc.sh /etc/profile.d
$ sudo ln -s /vps/etc/bash_completion.d/vps-lxc /etc/bash_completion.d
[close terminal and reopen]
$ vps-lxc help
Usage: vps-lxc COMMAND [help|OPTION]...
Create, destroy, interact with, and manage LXC based Virtual Private Server
(VPS/container) domains and templates.

Creation/destruction COMMANDs:
  mktpl    create a new template from scratch or based off an existing template
  mkdom    create a new domain based off a pre-created template
  rmtpl    remove a created template
  rmdom    remove a defined/created, STOPPED domain and it's configuration
Definition/edit COMMANDs:
  define   initialize a domain after editing it's configuration (once)
  edit     edit the persistent configuration of a VPS (requires reboot)
Control/interaction COMMANDs:
  start    send a STOPPED domain a signal to start
  stop     send a RUNNING domain a signal to stop
  reboot   send a RUNNING domain a signal to reboot
  enter    enter a domain and interact via console (limited, config specific)
Query COMMANDs:
  help     what you are seeing right now
  tree     view the VPS system's directories/files in a tree
  ls       list each domain and/or template and their status
```
there is bach completion for most things, and the scripts are clean and easy to extend.  the mkdom subcommand is fully capable of generating a complete LXC config from command options only:
```
$ vps-lxc mkdom help
Usage: vps-lxc mkdom -b BASE [-p PROFILE] [-h HOSTNAME] [-t TTY] [-s DEVPTS]
       [-n type=TYPE,flags=FLAGS,link=LINK,name=NAME,hwaddr=HWADDR,ipv4=IPV4,ipv6=IPV6]...
       [-c subsys.param=VALUE]... TARGET                                                  
Generate a VPS domain using an existing template as a base.  The resultant domain         
configuration is altered according to the selected profile and any options passed         

Options:
   -b   specifies the template used as a base for this domain
   -p   the profile to use; default if not provided          
   -h   the hostname assigned to this domain; defaults to NAME
        if not provided                                       
   -t   number of ttys to allocate to this domain             
   -s   use a private devpts instance if possible, and restrict
        ptys to this number; not implemented upstream          
   -n   append a network interface to this domain in addition  
        to any defined by the profile                          
   -c   append cgroup subsystem values to this domain in
        addition to any defined by the profile
Arguments:
   BASE       name of an existing template
   PROFILE    an existing folder in include/mkdom
   HOSTNAME   a valid hostname; default TARGET
   TTY        positive integer; default 2
   DEVPTS     positive integer; default 1024
   TYPE       empty, veth, macvlan, or phys
   FLAGS      up; or do not specify
   LINK       an existing interface on the host
   NAME       the interface name assigned internally
              to the container
   HWADDR     a valid MAC address; do not specify
              for dynamic
   IPV4       a valid IPV4 address in the form
              x.y.z.t/m, eg. 192.168.1.123/24
   IPV6       a valid IPV6 address in the form x::y/m,
              eg. 2003:db8:1:0:214:1234:fe0b:3596/64
   VALUE      set VALUE to the specified cgroup subsystem
              parameter, e.g devices.deny=a; if VALUE has
              spaces, quotes are needed
Parameters:
   TARGET   the name of the domain to be created

Options not defined can/may be set by the selected profile
```
its very complete, im using it to run my containers now.  there is still a question of how sys and proc will be handled (a FUSE based proc for containers is a possibility...) i will be keeping it up to date and coding on it more.

see here:
[http://bbs.archlinux.org/viewtopic.php?pid=706970](http://bbs.archlinux.org/viewtopic.php?pid=706970)
or here:
[http://www.mail-archive.com/lxc-users@lists.sourceforge.net/msg00148.html](http://www.mail-archive.com/lxc-users@lists.sourceforge.net/msg00148.html)

for similar information

---

### Post by narcisgarcia on 2010-03-21
I've written this script, based on [bodhi.zazen's tutorial]("http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/comment-page-1/") to create a container easily:
```

#!/bin/sh
# Copyright (GNU GPL) Narcis Garcia
# Thanks to bodhi.zazen
# Version 2010.03.20

ContainersPath="/var/lxc"
Languages="en_GB.UTF-8"
LanguagePackages="language-pack-en"

if [ "$2" = "" ] ; then
	echo "CONTAINER CREATOR FOR LXC"
	echo ""
	echo "Syntax:"
	echo "	lxc-prebuild.sh name ip-net [newuser]"
	echo "Examples:"
	echo "	lxc-prebuild.sh myvirtual1 192.168.1.50/24"
	echo "	lxc-prebuild.sh myserver 192.168.1.60/24 administrator"
else
	ContainerRoot="$ContainersPath/$1/root"
	ContainerConf="$ContainersPath/$1/container.conf"
	
	HostNIC="$(ifconfig | grep -E "^eth")"
	HostNIC=$(OneWord () { echo $1; }; OneWord $HostNIC)
	HostMask="$(env LANGUAGE=en ifconfig $HostNIC | grep Mask:)"
	HostMask=$(OneWord () { echo $4; }; OneWord $HostMask)
	HostMask="$(echo "$HostMask" | tr -s ":" " ")"
	HostMask=$(OneWord () { echo $2; }; OneWord $HostMask)
	HostBroadcast="$(env LANGUAGE=en ifconfig $HostNIC | grep Bcast:)"
	HostBroadcast=$(OneWord () { echo $3; }; OneWord $HostBroadcast)
	HostBroadcast="$(echo "$HostBroadcast" | tr -s ":" " ")"
	HostBroadcast=$(OneWord () { echo $2; }; OneWord $HostBroadcast)
	HostGateway="$(netstat -rn | grep -E "^0.0.0.0" | grep "$HostNIC")"
	HostGateway=$(OneWord () { echo $2; }; OneWord $HostGateway)
	HostNet="$(netstat -rn | grep "$HostMask" | grep "$HostNIC")"
	HostNet=$(OneWord () { echo $1; }; OneWord $HostNet)
	ContainerIP="$(echo "$2" | tr -s "/" " ")"
	ContainerBitmask=$(OneWord () { echo $2; }; OneWord $ContainerIP)
	ContainerIP=$(OneWord () { echo $1; }; OneWord $ContainerIP)

	if [ "$(which debootstrap)" = "" ] ; then
		apt-get install -y debootstrap
	fi
	if [ "$(which lxc-version)" = "" ] ; then
		apt-get install -y lxc
	fi
	mkdir -p "$ContainerRoot"
	debootstrap --variant=minbase $(lsb_release -cs) "$ContainerRoot"
	cp /etc/resolv.conf "$ContainerRoot/etc/"
	
	# -------------------------------------
	# bodhi.zazen's lxc-config (2010.02.02)
	# Makes default devices needed in lxc containers
	# modified from http://lxc.teegra.net/
	
	ROOT="$ContainerRoot"
	DEV=${ROOT}/dev
	if [ $ROOT = '/' ]; then
	printf "\033[22;35m\nDO NOT RUN ON THE HOST NODE\n\n"
	tput sgr0
	exit 1
	fi
	if [ ! -d $DEV ]; then
	printf "\033[01;33m\nRun this script in rootfs\n\n"
	tput sgr0
	exit 1
	fi
	rm -rf ${DEV}
	mkdir ${DEV}
	mknod -m 666 ${DEV}/null c 1 3
	mknod -m 666 ${DEV}/zero c 1 5
	mknod -m 666 ${DEV}/random c 1 8
	mknod -m 666 ${DEV}/urandom c 1 9
	mkdir -m 755 ${DEV}/pts
	mkdir -m 1777 ${DEV}/shm
	mknod -m 666 ${DEV}/tty c 5 0
	mknod -m 666 ${DEV}/tty0 c 4 0
	mknod -m 666 ${DEV}/tty1 c 4 1
	mknod -m 666 ${DEV}/tty2 c 4 2
	mknod -m 666 ${DEV}/tty3 c 4 3
	mknod -m 666 ${DEV}/tty4 c 4 4
	mknod -m 600 ${DEV}/console c 5 1
	mknod -m 666 ${DEV}/full c 1 7
	mknod -m 600 ${DEV}/initctl p
	mknod -m 666 ${DEV}/ptmx c 5 2
	#--------------------------------
	
	# Generate a config file

	echo "# container name (lxc.utsname)" >"$ContainerConf"
	echo "# network (lxc.network.ipv4)" >>"$ContainerConf"
	echo "# rootfs (lxc.rootfs)" >>"$ContainerConf"
	echo "" >>"$ContainerConf"
	echo "lxc.utsname = $1" >>"$ContainerConf"
	echo "lxc.tty = 4" >>"$ContainerConf"
	echo "lxc.network.type = veth" >>"$ContainerConf"
	echo "lxc.network.flags = up" >>"$ContainerConf"
	echo "lxc.network.link = br0" >>"$ContainerConf"
	echo "lxc.network.name = eth0" >>"$ContainerConf"
	echo "lxc.network.mtu = 1500" >>"$ContainerConf"
	echo "lxc.network.ipv4 = $HostNet/$ContainerBitmask" >>"$ContainerConf"
	echo "lxc.rootfs = $ContainerRoot" >>"$ContainerConf"
	echo "lxc.cgroup.devices.deny = a" >>"$ContainerConf"
	echo "# /dev/null and zero" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 1:3 rwm" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 1:5 rwm" >>"$ContainerConf"
	echo "# consoles" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 5:1 rwm" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 5:0 rwm" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 4:0 rwm" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 4:1 rwm" >>"$ContainerConf"
	echo "# /dev/{,u}random" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 1:9 rwm" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 1:8 rwm" >>"$ContainerConf"
	echo "# /dev/pts/* - pts namespaces are \"coming soon\"" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 136:* rwm" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 5:2 rwm" >>"$ContainerConf"
	echo "# rtc" >>"$ContainerConf"
	echo "lxc.cgroup.devices.allow = c 254:0 rwm" >>"$ContainerConf"

	# Configure basic tools
	LocalConfig="$ContainerRoot/tmp/basics.sh"
	echo "#!/bin/sh" >"$LocalConfig"
	echo "apt-get install --force-yes -y gpgv" >>"$LocalConfig"
	echo "apt-get update" >>"$LocalConfig"
	echo "apt-get install -y $LanguagePackages" >>"$LocalConfig"
	echo "update-locale LANG=\"$Languages\" LANGUAGE=\"$Languages\" LC_ALL=\"$Languages\"" >>"$LocalConfig"
	echo "apt-get install -y adduser apt-utils iproute netbase nano openssh-blacklist openssh-blacklist-extra openssh-server console-setup sudo ping" >>"$LocalConfig"
	echo "echo \"--------------------------------------\"" >>"$LocalConfig"
	if [ "$3" = "" ] ; then
		echo "echo \"Enter a password for 'root' in $1\"" >>"$LocalConfig"
		echo "passwd" >>"$LocalConfig"
	else
		echo "echo \"Enter a password for '$3' in $1\"" >>"$LocalConfig"
		echo "adduser --gecos \"\" $3" >>"$LocalConfig"
		echo "usermod --groups dialout,cdrom,plugdev,sudo $3" >>"$LocalConfig"
	fi
	chmod +x "$LocalConfig"
	chroot "$ContainerRoot" /tmp/basics.sh
	rm "$LocalConfig"

	# Configure NIC
	echo "" >>"$ContainerRoot/etc/network/interfaces"
	echo "auto eth0" >>"$ContainerRoot/etc/network/interfaces"
	echo "iface eth0 inet static" >>"$ContainerRoot/etc/network/interfaces"
	echo "	address	$ContainerIP" >>"$ContainerRoot/etc/network/interfaces"
	echo "	netmask	$HostMask" >>"$ContainerRoot/etc/network/interfaces"
	echo "	broadcast	$HostBroadcast" >>"$ContainerRoot/etc/network/interfaces"
	echo "	gateway	$HostGateway" >>"$ContainerRoot/etc/network/interfaces"

	# Remove tty4, 5, & 6
	rm "$ContainerRoot/etc/init/tty4.conf"
	rm "$ContainerRoot/etc/init/tty5.conf"
	rm "$ContainerRoot/etc/init/tty6.conf"

	# Fix /var/run/network/ifstate
	mkdir -p "$ContainerRoot/var/run/network"
	touch "$ContainerRoot/var/run/network/ifstate"

	# Add a directory to allow ssh user privilege separation
	mkdir -p "$ContainerRoot/var/run/sshd"

	# Edit rootfs.ubuntu/lib/init/fstab
	cp "$ContainerRoot/lib/init/fstab" "$ContainerRoot/lib/init/fstab.bak"
	cat "$ContainerRoot/lib/init/fstab" | grep -vE "/proc " > "$ContainerRoot/tmp/fstab1"
	cat "$ContainerRoot/tmp/fstab1" | grep -vE "/sys " > "$ContainerRoot/tmp/fstab2"
	cat "$ContainerRoot/tmp/fstab2" | grep -vE "/dev " > "$ContainerRoot/lib/init/fstab"
	rm "$ContainerRoot/tmp/fstab1"
	rm "$ContainerRoot/tmp/fstab2"

	# Edit rootfs.ubuntu/etc/init/rc-sysinit.conf
	IFS=$(printf "\n\b") ; for OneLine in $(cat "$ContainerRoot/etc/init/rc-sysinit.conf") ; do unset IFS
		InterestingLine="$(echo $OneLine | grep "start on filesystem and net-device-up IFACE=lo")"
		if [ "$InterestingLine" != "" ] ; then
			OneLine="start on filesystem # and net-device-up IFACE=lo"
		fi
		echo "$OneLine" >>"$ContainerRoot/tmp/rc-sysinit.conf"
	done
	mv "$ContainerRoot/tmp/rc-sysinit.conf" "$ContainerRoot/etc/init/rc-sysinit.conf"

	# Add an init (upstart) script
	echo "# LXC – Fix init sequence to have LXC containers boot with upstart" >"$ContainerRoot/etc/init/lxc.conf"
	echo "" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "# description “Fix LXC container - Lucid”" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "start on startup" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "task" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "pre-start script" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "mount -t proc proc /proc" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "mount -t devpts devpts /dev/pts" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "mount -t sysfs sys /sys" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "mount -t tmpfs varrun /var/run" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "mount -t tmpfs varlock /var/lock" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "mkdir -p /var/run/network" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "touch /var/run/utmp" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "chmod 664 /var/run/utmp" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "chown root.utmp /var/run/utmp" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "if [ \"\$(find /etc/network/ -name upstart -type f)\" ]; then" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "chmod -x /etc/network/*/upstart || true" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "fi" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "end script" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "script" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "start networking" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "initctl emit filesystem --no-wait" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "initctl emit local-filesystems --no-wait" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "initctl emit virtual-filesystems --no-wait" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "init 2" >>"$ContainerRoot/etc/init/lxc.conf"
	echo "end script" >>"$ContainerRoot/etc/init/lxc.conf"

	echo ""
	echo "------------------------"
	lxc-create -f "$ContainerConf" -n $1
	Result=$?
	if [ "$Result" = "0" ] ; then
		echo "You can start the new container with this command:"
		echo "lxc-start -n $1"
	fi
fi

```

I've run it in a Ubuntu 10.04 server (alpha 2010.03.17 fresh installed):
```

sudo lxc-prebuild.sh server1 192.168.1.71/24 administrator

```
...but after all the process , when I run "lxc-start -n server1" this is the result:
> 
lxc-start: failed to attach 'vethkcT2cj' to the bridge 'br0'
lxc-start: failed to create netdev
lxc-start: failed to create the network
lxc-start: failed to spawn '/sbin/init'
lxc-start: cgroup is not mounted


---

### Post by Dorowan on 2010-03-24
> **starfry said:**
> Thanks for the replies. So one question: If I want to continue using OpenVZ on Lucid, will I be able to?

Sinc OpenVZ [just]("http://git.openvz.org/?p=linux-2.6.32-openvz;a=log;h=2.6.32-afanasyev") released a [2.6.32 Kernel with OpenVZ patches]("http://wiki.openvz.org/Download/kernel/2.6.32/2.6.32-afanasyev.1") you have a good chance though I do not think the kernel will make it into the official Lucid Lynx release. Maybe you will be able to get it from the OpenVZ repository or from launchpad. At the moment there are only rpms and source.

---

### Post by narcisgarcia on 2010-03-24
As commented by Dorowan OpenVZ released a 2.6.32 Kernel with OpenVZ support. At the moment the only prebuild packages are for rpm-based distros, but server administrators need a reliable way to upgrade our LTS host servers, and LXC sowftare+docummentation is not ready for OpenVZ migration.

---

### Post by bodhi.zazen on 2010-03-24
> **Dorowan said:**
> Sinc OpenVZ [just]("http://git.openvz.org/?p=linux-2.6.32-openvz;a=log;h=2.6.32-afanasyev") released a [2.6.32 Kernel with OpenVZ patches]("http://wiki.openvz.org/Download/kernel/2.6.32/2.6.32-afanasyev.1") you have a good chance though I do not think the kernel will make it into the official Lucid Lynx release. Maybe you will be able to get it from the OpenVZ repository or from launchpad. At the moment there are only rpms and source.

If you wish to try that kernel, IMO, I would start with the patch. If that fails you could take a look at converting the .rpm with alien, which is what I believe Proxmox does.

It does not appear either openvz or LXC are priorities for the Ubuntu Developers and if you wish to use OpenVZ I highly suggest Debian, Proxmox, or Centos.

---

### Post by ribo on 2010-03-27
Fresh install of lucid server, did everything exactly as bodhi.zazen has written instructions for; and I get this every time:

```

:0.root.ubuntu- lxc-start -n lxc01
init: lxc pre-start process (2) terminated with status 32
mountall: Could not connect to Plymouth
init: console-setup main process (34) terminated with status 1
^Z
zsh: suspended  lxc-start -n lxc01
:20.root.ubuntu- bg
[1]  + continued  lxc-start -n lxc01
:0.root.ubuntu- lxc-stop -n lxc01
[1]  + exit 137   lxc-start -n lxc01
:0.root.ubuntu-


```

Any ideas?

---

### Post by cdufour on 2010-03-27
LXC is definitely not ready for production. The lack of proper documentation is one proof of it, among others. Dropping support of a stable, efficient, well-documented virtualization solution for a new unreliable, unproven, poorly documented one, in a LTS release, without providing a path for a smooth migration (like having the two solutions co-exist for a time), is a poor choice of strategy. That not being said against LXC, which holds great promises for when it will be mature.

---

### Post by ribo on 2010-03-27
So, I got into my containers finally, made two of them.

But now, I get this network interleaving problem if I ssh to two containers at the same time, where one starts to time out when I type in the other one.  Obviously something with my bridge config, but I don't know what.

---

### Post by narcisgarcia on 2010-03-28
Ribo, can you rewrite bodhi.zazen's tutorial to show how to get more success?

[https://help.ubuntu.com/community/LXC](https://help.ubuntu.com/community/LXC)

Thanks

---

### Post by narcisgarcia on 2010-03-28
Which steps are needed to do, to use today OpenVZ in a fresh Lucid server installation?

---

### Post by bodhi.zazen on 2010-03-28
> **narcisgarcia said:**
> Which steps are needed to do, to use today OpenVZ in a fresh Lucid server installation?

You would first of all need to build a custom kernel. The poenvx project just released a new patch, I have not tried it yet.

If you want to use OpenVZ I highly suggest you use Ubuntu 8.04, Centos, or Proxmox / Debian.

For a 10.04 guest there are reports that the guest templates work with a custom Upstart script, but as 10.04 is still in development I have not tried it.

I suggest you post questions about 10.04 either in the development section or better on launchpad.

---

### Post by narcisgarcia on 2010-03-28
Expressed here:

[http://ubuntuforums.org/showthread.php?t=1441265](http://ubuntuforums.org/showthread.php?t=1441265)

---

### Post by cdufour on 2010-03-28
See [http://community.livejournal.com/openvz/30998.html](http://community.livejournal.com/openvz/30998.html) . A pity there has not been just a few more weeks. Maybe OpenVZ could have made it into Lucid :-(

---

### Post by narcisgarcia on 2010-03-29
May be better to discuss Lucid's OpenVZ question there

[http://ubuntuforums.org/showthread.php?t=1441265](http://ubuntuforums.org/showthread.php?t=1441265)

---

### Post by narcisgarcia on 2010-03-29
I've found this guide to use a wizard:

[http://publib.boulder.ibm.com/infocenter/lnxinfo/v3r0m0/topic/liaai/container/liaaicontainernewenviron.htm](http://publib.boulder.ibm.com/infocenter/lnxinfo/v3r0m0/topic/liaai/container/liaaicontainernewenviron.htm)

This seems to be useful to create config files.

( WBEM-SMT with [http://sblim.sourceforge.net/](http://sblim.sourceforge.net/) )

---

### Post by JedMeister on 2010-03-30
> **cdufour said:**
> See [http://community.livejournal.com/openvz/30998.html](http://community.livejournal.com/openvz/30998.html) . A pity there has not been just a few more weeks. Maybe OpenVZ could have made it into Lucid :-(

Yes you are right. It is a shame.

That thread you linked to is very interesting, thanks for that. 

k001 (Kir Kolyshkin - OpenVZ dev) suggests that whilst LXC is built on proven foundations, it's feature set is less, it is new and yet to mature, it is less resource efficient than OpenVZ and it has unproven stability. 

From what I've read on this thread there are some who would disagree with that. Regardless, I think I'll stick with OpenVZ; so it'll be 8.04 until Debian Squeeze (with native OpenVZ support on a 2.6.32 kernel).

---

### Post by bodhi.zazen on 2010-03-30
I have tried the latest openvz kernel , 2.6.32, installed via alien on an up to date lucid server.

[http://wiki.openvz.org/Install_kernel_from_rpm_on_debian](http://wiki.openvz.org/Install_kernel_from_rpm_on_debian)

The kernel installs, and boots, with a few error messages ...

Removed apparmor, rebooted ...

BUT openvz guests hang , the command

```
vzctrl create 777 --os-template ubuntu-8.04
```

Hangs the entire system.

I am in process of 

1. Building a custom kernel (the build takes a while, lol).

2. Trying it on Debian squeeze.

---

### Post by bodhi.zazen on 2010-03-30
Update : The openvz 2.6.32-afanasyev.1 kernel works on Debian Squeeze.

[http://wiki.openvz.org/Install_kernel_from_rpm_on_debian](http://wiki.openvz.org/Install_kernel_from_rpm_on_debian)

---

### Post by narcisgarcia on 2010-03-30
Now we need to make a tutorial to build Ubuntu's server kernel (in 10.04) for OpenVZ. This will be usefull also for kernel updates.

[https://help.ubuntu.com/community/OpenVZ](https://help.ubuntu.com/community/OpenVZ)
[https://wiki.ubuntu.com/OpenVZ](https://wiki.ubuntu.com/OpenVZ)

---

### Post by bodhi.zazen on 2010-03-30
> **narcisgarcia said:**
> Now we need to make a tutorial to build Ubuntu's server kernel (in 10.04) for OpenVZ. This will be usefull also for kernel updates.

[https://help.ubuntu.com/community/OpenVZ](https://help.ubuntu.com/community/OpenVZ)
[https://wiki.ubuntu.com/OpenVZ](https://wiki.ubuntu.com/OpenVZ)

I am working on building a kernel for Ubuntu. If it works I will post the tutorial, it takes a long time to build (compile) the kernel, will update you on my progress.

---

### Post by bodhi.zazen on 2010-03-31
I built a kernel from the vanilla 2.6.32 , it boots, but openvz did not work in Ubuntu, not sure why.

I tried patching the ubuntu kernel source, the openvz patch fails.

So I can not get the 2.6.32 openvz kernel running on lucid.

---

### Post by narcisgarcia on 2010-03-31
We may need now some support from OpenVZ project for compiling successfully:
[http://forum.openvz.org/](http://forum.openvz.org/)

bodhi.zazen, could you update this guide with your experience ?:
[http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_%28the_Debian_way%29](http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_%28the_Debian_way%29)

---

### Post by bodhi.zazen on 2010-04-02
> **narcisgarcia said:**
> We may need now some support from OpenVZ project for compiling successfully:
[http://forum.openvz.org/](http://forum.openvz.org/)

bodhi.zazen, could you update this guide with your experience ?:
[http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_%28the_Debian_way%29]("http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_%28the_Debian_way%29")

You basically have four options with Debian :

1. Use alien to convert the openvz 2.6.32 rpm to a deb

[http://wiki.openvz.org/Install_kerne..._rpm_on_debian]("http://wiki.openvz.org/Install_kernel_from_rpm_on_debian")

2. Enable the unstable (sid) repository :

[http://packages.debian.org/unstable/kernel/linux-image-2.6.32-4-openvz-686](http://packages.debian.org/unstable/kernel/linux-image-2.6.32-4-openvz-686)
[http://packages.debian.org/unstable/kernel/linux-image-2.6.32-4-openvz-amd64](http://packages.debian.org/unstable/kernel/linux-image-2.6.32-4-openvz-amd64)

3. For Ubuntu, you could try downloading those .deb and they may well run on Ubuntu (I do not know).

4. You can apply the patch as directed on the openvz wiki :

[http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_%28the_Debian_way%29](http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_%28the_Debian_way%29)

The only changes you might need to make are to download the proper kernel and openvz patch.

Note: The patch here : [http://wiki.openvz.org/Download/kernel/2.6.32/2.6.32-afanasyev.1](http://wiki.openvz.org/Download/kernel/2.6.32/2.6.32-afanasyev.1)

does not work on either Debian or Ubuntu. The kernel builds, and boots, but when starting an openvz guest the kernel locks up.

As a side note: 

1. With all due respect, we do not always agree with the decisions of the Ubuntu developers, but it is fairly clear to me that support for Xen, openvz, vserver, and LXC are poor in Ubuntu.

It seems VPS is NOT a priority for Canonical / MOTU and / or they choose to support KVM and LXC. LXC has issues at the moment and I would not advise anyone use it on a production server for a variety of reasons from a lack of documentation to potential security issues. Although there are those who may feel LXC is ready for "prime time" those users are in the minority (IMO). 

Ubuntu has minimal documentation for LXC, and the Ubuntu developers does not yet have published any Ubuntu specific LXC user scripts.

If you wish to use these tools (XEN, vserver, openvz) you should use a supported distro such as Centos for Debian.

2. I think you will fine the best, most up to date information on the openvz mailing list.

---

### Post by ibuclaw on 2010-04-03
> **bodhi.zazen said:**
> I built a kernel from the vanilla 2.6.32 , it boots, but openvz did not work in Ubuntu, not sure why.

I tried patching the ubuntu kernel source, the openvz patch fails.

So I can not get the 2.6.32 openvz kernel running on lucid.

In the cases where a patch fails, you need to check the source tree for .rej files.

```
find . -name "*.rej"
```
Then apply each of the rejects manually - if at all possible.

Once finished, remove all .rej and .orig files (using the same find command, except have '-exec rm {} \;' appended on the end). Then extract the original source into a new directory, and create a new patch.
ie:
```
diff -ur ubuntu-kernel.orig ubuntu-kernel > ubuntu-openvz.patch
```

Regards

---

### Post by ibuclaw on 2010-04-05
Ugh, actually having a look, the openvz patch [(the one here)]("http://wiki.openvz.org/Download/kernel/2.6.32/2.6.32-afanasyev.1") - it is not openvz as an addon. It is openvz + .32 updates.

It won't apply to Ubuntu/Debian because they have their own .32 kernels with same, similar, or more recent updates to the one in the patch.

Could start bisecting the patch later this week, and test it then.

Attached is a start - this is the main openvz code, but none of the glue. So while it will patch against the ubuntu kernel source, it will not show in the Make menu.

Watch here for more updates.

Regards

Update:
Bisected some of the glue, but not all of it. (somewhere about a 1/3 done).

---

### Post by cdufour on 2010-04-10
> **bodhi.zazen said:**
> You basically have four options with Debian :
It seems VPS is NOT a priority for Canonical / MOTU and / or they choose to support KVM and LXC. LXC has issues at the moment and I would not advise anyone use it on a production server for a variety of reasons from a lack of documentation to potential security issues. Although there are those who may feel LXC is ready for "prime time" those users are in the minority (IMO). 


Sadly, I entirely agree with you. I just "upgraded" my server from Ubuntu Hardy to Debian Lenny - which provides a rock solid OpenVZ foundation as far as I've been able to judge - and will stick to Debian for servers and virtualization. And I'm afraid even Debian Squeeze won't provide a mature LXC foundation yet (one reason being the lack of sVirt integration - IIRC - which I feel is a MUST as far as security is concerned for production servers)

---

### Post by narcisgarcia on 2010-04-10
[http://en.wiktionary.org/wiki/IIRC](http://en.wiktionary.org/wiki/IIRC)
[http://en.wiktionary.org/wiki/must](http://en.wiktionary.org/wiki/must)

---

### Post by narcisgarcia on 2010-04-10
I see that the last released Ubuntu with OpenVZ kernel is the version 8.04.4 with the kernel Linux 2.6.24

And the last released Debian with OpenVZ kernel is the version 5.04 with the kernel Linux 2.6.26

Superior versions I suppose are not good choices for production environments, because not yet considered stable.

---

### Post by david_lynch on 2010-04-14
I've been running ubuntu server for a couple of years now, and was looking forward to running openvz on 10.04 - but I'm quite disappointed to see that ubuntu is leaving the openvz users in the lurch. Sorry, but LXC just isn't there yet. end of story. If they wanted to introduce it, they should have at least retained the option of choosing openvz, for the less adventurous.

FWIW Debian squeeze will ship with openvz on a 2.6.32 kernel. You could try the debian 2.6.32 openvz kernel on ubuntu 10.04 server, as suggested by Kir of openvz.

Ultimately, in light of ubuntu's apparent lack of concern for the wishes of its users, it may be necessary to move your ubuntu based openvz servers to debian in order to keep things running.

---

### Post by narcisgarcia on 2010-04-15
"for what it's worth"

---

### Post by bodhi.zazen on 2010-04-15
> **david_lynch said:**
> I've been running ubuntu server for a couple of years now, and was looking forward to running openvz on 10.04 - but I'm quite disappointed to see that ubuntu is leaving the openvz users in the lurch. Sorry, but LXC just isn't there yet. end of story. If they wanted to introduce it, they should have at least retained the option of choosing openvz, for the less adventurous.

FWIW Debian squeeze will ship with openvz on a 2.6.32 kernel. You could try the debian 2.6.32 openvz kernel on ubuntu 10.04 server, as suggested by Kir of openvz.

Ultimately, in light of ubuntu's apparent lack of concern for the wishes of its users, it may be necessary to move your ubuntu based openvz servers to debian in order to keep things running.

There is an openvz 2.6.32 kernel in Debian unstable, it was not working yet last time I checked (see the openvz mailing list).

The openvz kernel works on Debian squeeze if you import it via alien (see the openvz 2.6.32 page or my earlier posts).

Manually applying the openvz patch to a vanella kernel does not work in either Debian or Ubuntu.

Importing the openvz kernel from either the .rpm (alien) or the Debian kernel ( .deb) does not work on Ubuntu.

If you want to run openvz I suggest either Centos or Proxmox.

---

### Post by narcisgarcia on 2010-04-15
Ubuntu 8.04 LTS server has support until 2013, and Debian Lenny (stable) I believe more.

Then at his moment I see more secure to use stable and long-supported versions that come with openvz in repositories: Ubuntu Hardy and Debian Lenny.

---

### Post by bodhi.zazen on 2010-04-15
> **narcisgarcia said:**
> Ubuntu 8.04 LTS server has support until 2013, and Debian Lenny (stable) I believe more.

Then at his moment I see more secure to use stable and long-supported versions that come with openvz in repositories: Ubuntu Hardy and Debian Lenny.

Proxmox == Debian Lenny

Openvz is much better supported, as you can see from the 2.6.32 kernel, on Centos.

---

### Post by narcisgarcia on 2010-04-16
Oh, I see that the [CentOS]("http://www.centos.org/") project gives 7 years of updates support for each version, and has the same age as Ubuntu.

For the moment, I still prefer Debian based distributions, and I'm now reflecting about the real needing of 2.6.32 before Debian 6 release.

---

### Post by JedMeister on 2010-04-16
> **bodhi.zazen said:**
> 
...If you want to run openvz I suggest either Centos or Proxmox.

I really like Proxmox VE. I think its a great hypervisor solution as not only does it include OpenVZ, but also KVM so its useful for hosting non-Linux OSs too. The web based admin is very handy too, allowing you to have access to all your VMs remotely (via web based VNC window). Also being Debian based the transition from Ubuntu is pretty easy.

---

### Post by narcisgarcia on 2010-04-17
I've seen the videotutorials about Proxmox and looks a good thing.
Proxmox is really a distribution? Based on...?

I've tried to add its repository on an Ubuntu 9.10 but seems malformed:
```
wget -O- "http://download.proxmox.com/debian/key.asc" | apt-key add -
echo "deb http://download.proxmox.com/debian lenny pve" >>/etc/apt/sources.list
apt-get update
```

> W: Failed to fetch [http://download.proxmox.com/debian/dists/lenny/Release](http://download.proxmox.com/debian/dists/lenny/Release)  Unable to find expected entry  pve/binary-i386/Packages in Meta-index file (malformed Release file?)

---

### Post by bodhi.zazen on 2010-04-17
> **narcisgarcia said:**
> I've seen the videotutorials about Proxmox and looks a good thing.
Proxmox is really a distribution? Based on...?

I've tried to add its repository on an Ubuntu 9.10 but seems malformed:
```
wget -O- "http://download.proxmox.com/debian/key.asc" | apt-key add -
echo "deb http://download.proxmox.com/debian lenny pve" >>/etc/apt/sources.list
apt-get update
```

No offense, but I have already given you many links and much information on Proxmox.

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

If you look at my posts you will see I told you it is based on Debian Lenny + an openvz kernel imported from a rpm.

I would not advise you add the repository and using apt-get unless you know what you are doing as the repository is likely to have issues and you would need to do things such as pinning.

I advise you install proxmox.

---

### Post by narcisgarcia on 2010-04-17
Ok, thanks.
I was vague lackadaisical.

---

### Post by JedMeister on 2010-04-19
> **bodhi.zazen said:**
> 
I would not advise you add the repository and using apt-get unless you know what you are doing as the repository is likely to have issues and you would need to do things such as pinning.

I advise you install proxmox.
I 110% agree. It can be installed on x84_64 Debian Lenny but is unsupported. Mucking around (just for kicks) I tried to install to Ubuntu and it was an abysmal failure! 
OTOH installing from ISO worked a treat. As you may well already realise (if you followed the link) ProxmoxVE is 64 bit only and to get the full benifits install to hardware that supports virtual extentions (AMD-V/Intel VT). Its a winner!

---

### Post by ribo on 2010-04-19
For those using LXC: be warned that the latest version installed in Lucid (0.6.5) has a bug when /var is mounted on the host as a separate volume.  I've had to downgrade to 0.6.3 to fix the issue.  The LXC folks are aware of it, and the patch should make it to the next minor rev.

---

### Post by ribo on 2010-04-19
Did a bit of a writeup on LXC network config with bonded interfaces if anyone else needs such a config. [http://system42.net]("http://system42.net")

---

### Post by narcisgarcia on 2010-04-24
There are some people working on OpenVZ for Ubuntu 10.04

[https://bugs.launchpad.net/vzorchestra/+bug/545850](https://bugs.launchpad.net/vzorchestra/+bug/545850)

---

### Post by bodhi.zazen on 2010-05-05
First I moved this thread to Virtualization as, IMO, this is an ongoing issue.

Second, Proxmox released a 2.6.32 kernel that , in theory, should work on Debian or Ubuntu - YEA !!!

[http://pve.proxmox.com/wiki/Downloads](http://pve.proxmox.com/wiki/Downloads)

[http://download.proxmox.com/debian/dists/lenny/pve/binary-amd64/](http://download.proxmox.com/debian/dists/lenny/pve/binary-amd64/)

Update - Read the release notes, the 2.6.32 kernel has KVM support ONLY (No openvz).

In addition I posted Ubuntu 10.04 Templates

[http://blog.bodhizazen.net/linux/ubuntu-10-04-openvz-templates/](http://blog.bodhizazen.net/linux/ubuntu-10-04-openvz-templates/)

[http://blog.bodhizazen.net/linux/download-ubuntu-10-04-openvz-templates/](http://blog.bodhizazen.net/linux/download-ubuntu-10-04-openvz-templates/)

---

### Post by BoneKracker on 2010-05-12
I'm not using LXC on Ubuntu, but I thought I'd pass this on.

Read-only bind mounts don't work as advertised in LXC (as of 0.6.5).  For example, this won't work:
```
lxc.mount.entry = /etc /srv/vps3/etc none ro,bind 0 0
```

Instead of getting mounted read-only, it gets mounted read-write (not good).

This is sure to be fixed in some future version, but this capability is critical to some use-cases (e.g., you want to reuse parts or most of the host system's root filesystem by want it protected from writes).

Obviously, you can write your own script to take care of the mounts, but this simple patch fixes the problem.

---

### Post by bodhi.zazen on 2010-05-15
As an update to all following this thread, I was able to get LXC up an running and it works well.

Part of the problem with using LXC is coming to an understanding of the configuration files and mor eimportant, eliminate as many init scripts as possible.

I updated my blog:

[http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/](http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/)

Assuming people find this information helpful, the next step is to update the Ubuntu LXC wiki page.

---

### Post by BoneKracker on 2010-05-15
> **bodhi.zazen said:**
> As an update to all following this thread, I was able to get LXC up an running and it works well.

Part of the problem with using LXC is coming to an understanding of the configuration files and mor eimportant, eliminate as many init scripts as possible.

I updated my blog:

[http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/](http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/)

Assuming people find this information helpful, the next step is to update the Ubuntu LXC wiki page.

Congratulations, and nice work documenting it (something badly needed).  :)

Here's an experiment I tried (it works) -- making a container by reusing the existing host system's files as read-only bind mounts (something that requires the bugfix patch I posted earlier or that you wait for a version beyond 0.6.5 where that works like it's supposed to).  The point here is that you don't have to configure and maintain a separate "system" or "image", but it's as compartmentalized as if you did.  Also, it requires essentially no additional disk space (this is the lowest-overhead vps you could possibly make, I would think).

This container is currently an ftp server (with ssh also, for administrative access.  I am making another like this that will be a webdav server.

As you can see from the config file below, it reuses (read-only) /bin /etc /lib /sbin and /usr from the host system. (Don't pay too much attention to the cgroup stuff, since I'm still dabbling where that's concerned.)  This is on a gentoo box, but I think all this transfers.

```
# /etc/lxc/alpha/config

# hostname for virtual private server
lxc.utsname = beta

# network configuration
lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = br0
lxc.network.hwaddr = b6:67:82:92:ca:a0
lxc.network.ipv4 = 0.0.0.0

# pseudo-filesystems to be created and isolated in the container
lxc.mount.entry = none /srv/lxc/beta/proc proc defaults 0 0
#lxc.mount.entry = none /srv/lxc/beta/sys sysfs defaults 0 0
lxc.mount.entry = none /srv/lxc/beta/dev/pts devpts defaults 0 0
lxc.mount.entry = none /srv/lxc/beta/dev/shm tmpfs defaults 0 0
lxc.mount.entry = none /srv/lxc/beta/var/run tmpfs defaults 0 0

# files to be reused from host system (read-only bind mounts)
lxc.mount.entry = /bin /srv/lxc/beta/bin none ro,bind 0 0
lxc.mount.entry = /etc /srv/lxc/beta/etc none ro,bind 0 0
lxc.mount.entry = /lib /srv/lxc/beta/lib none ro,bind 0 0
lxc.mount.entry = /sbin /srv/lxc/beta/sbin none ro,bind 0 0
lxc.mount.entry = /usr /srv/lxc/beta/usr none ro,bind 0 0

# files unique to container, overlayed on the bind-mounts from host (some ro, some rw)
lxc.mount.entry = /etc/lxc/beta/sbin/init /srv/lxc/beta/sbin/init none ro,bind 0 0
lxc.mount.entry = /etc/lxc/beta/etc/ssh /srv/lxc/beta/etc/ssh none ro,bind 0 0
lxc.mount.entry = /etc/lxc/beta/etc/vsftpd /srv/lxc/beta/etc/vsftpd none ro,bind 0 0
lxc.mount.entry = /etc/lxc/beta/etc/resolv.conf /srv/lxc/beta/etc/resolv.conf none bind 0 0
lxc.mount.entry = /etc/lxc/beta/etc/mtab /srv/lxc/beta/etc/mtab none bind 0 0


lxc.rootfs = /srv/lxc/beta

lxc.pts = 128

lxc.cgroup.cpu.shares = 512

lxc.cgroup.devices.deny = a
lxc.cgroup.devices.allow = c 1:3 rw
lxc.cgroup.devices.allow = c 1:9 rw
lxc.cgroup.devices.allow = c 5:2 rw
lxc.cgroup.devices.allow = c 136:* rw
```

As a reminder, the "ro,bind" stuff above won't work without the patch I mentioned, as of version 0.6.5 (although it's supposed to), but I'm sure that will be fixed in a later version.

---

### Post by bodhi.zazen on 2010-05-15
> **BoneKracker said:**
> Congratulations, and nice work documenting it (something badly needed).  :)

Indeed, that is one of the biggest downsides of LXC, There are many undocumented features and without documentation LXC is not ready for a "Production" Environment.

> As a reminder, the "ro,bind" stuff above won't work without the patch I mentioned, as of version 0.6.5 (although it's supposed to), but I'm sure that will be fixed in a later version.

Very nice configuration. 

I believe btrfs would work well with LXC as well.

I was going to point out , the ro option does not work without the patch.

LXC, IMO, needs a better set of scripts, to set up / configure cgroups , config files on the host, "Live migration" of containers / guests, etc, etc. Right now we have a number of talented individuals working on personal scripts (they have posted here and on the LXC mailing list), but we need to encourage those people to become more directly involved with LXC development so that we have a consistent and reliable set of scripts.

---

### Post by BoneKracker on 2010-05-15
I agree.  To me, it very much has the feeling of a decentralized "work in progress".

---

### Post by Runner85sx on 2010-06-07
Hello together.

I'am using openvz with ubuntu lucid. I compiled the kernel and the applications from source. It is working very well here and there are no problems.

If you like to know how i did it, let me know and i will share my experience with it.

Greets from germany.

---

### Post by narcisgarcia on 2010-06-07
What's your plan for kernel updates; compile again?

Could you share your experience as a tutorial in the wiki as a new chapter?
[https://help.ubuntu.com/community/OpenVZ](https://help.ubuntu.com/community/OpenVZ)

---

### Post by Runner85sx on 2010-06-08
Yes of cause.
If there is a new kernel, i will rebuild it.
I have a big root-server with intel core i 7. So rebuilding a kernel won't take much time.
Maybe i can provide patched kernelsources or the kernelimage.

Sorry for my poor english. :p


Edit: Howto for building and installing openvz on ubuntu lucid is ready.

Please visit: [https://help.ubuntu.com/community/OpenVZ#Building%20OpenVZ%20on%20Ubuntu%2010.04%20Lucid](https://help.ubuntu.com/community/OpenVZ#Building%20OpenVZ%20on%20Ubuntu%2010.04%20Lucid)

---

### Post by narcisgarcia on 2010-06-08
Oh, thanks.
How can be obtained the number of CPU cores?

---

### Post by Runner85sx on 2010-06-08
do a: sudo apt-get install htop && sudo htop

if you have a dualcore-cpu than the vaule for the level is 3.

---

### Post by narcisgarcia on 2010-06-08
Ok, I've been searching and developed a direct and compatible formula to obtain the number of CPU cores:
```
echo $(ArgumentsNumber () { echo $#; }; ArgumentsNumber $(grep "processor" /proc/cpuinfo | cut -f2 -d":"))
```

Then I suppose that the CONCURRENCY line can be replaced by:
```
CoresNumber=$(ArgumentsNumber () { echo $#; }; ArgumentsNumber $(grep "processor" /proc/cpuinfo | cut -f2 -d":"))
sudo echo "CONCURRENCY_LEVEL := $CoresNumber" >> /etc/kernel-pkg.conf
```

---

### Post by narcisgarcia on 2010-06-08
Also the PC architecture autodetection can be implemented:

```
Architecture="i686"
if [ $(free -m) -gt 3072 ]; then Architecture="i686-PAE" ; fi
if [ $(uname -m) = "x86_64" ]; then Architecture="x86_64" ; fi
sudo wget http://download.openvz.org/kernel/branches/2.6.32/2.6.32-belyayev.1/configs/kernel-2.6.32-$Architecture.config.ovz

```

What about finding the last kernel's version available?

---

### Post by Runner85sx on 2010-06-08
Maybe you like to visit: [http://git.openvz.org/](http://git.openvz.org/)

---

### Post by bodhi.zazen on 2010-06-09
You may also install openvz using alien :

[http://wiki.openvz.org/Install_kernel_from_rpm_on_debian](http://wiki.openvz.org/Install_kernel_from_rpm_on_debian)

This is the method used by Proxmox and may or may not be easier.

The openvz tools are in the Ubuntu repositories if you do not want to install from git.

```
sudo apt-get install vzctl vzdump
```

[http://wiki.openvz.org/Download/kernel/2.6.32/2.6.32-belyayev.1](http://wiki.openvz.org/Download/kernel/2.6.32/2.6.32-belyayev.1)

Again, the best and most up to date information on openvz is either the openvz mailing list or the openvz site. It is nice to see new life in openvz development.

---

### Post by Runner85sx on 2010-06-12
Yesterday i noticed that there is some trouble with panels like "ovz-web".
I try to figure out what is the problem.

Greets from Germany.

---

### Post by starfry on 2010-08-15
> **Runner85sx said:**
> 
Edit: Howto for building and installing openvz on ubuntu lucid is ready.

Please visit: [https://help.ubuntu.com/community/OpenVZ#Building%20OpenVZ%20on%20Ubuntu%2010.04%20Lucid](https://help.ubuntu.com/community/OpenVZ#Building%20OpenVZ%20on%20Ubuntu%2010.04%20Lucid)

I have just tried about ten times to build the kernel using these instructions. I get the kernel built, but it won't boot. Here's what happens:

mounting none on /dev failed : no such device
ureadahead main process 416 terminated on signal 5

It then goes to the splash screen which immediately gets garbled and then the machine hangs.

Any ideas?

To do this build, I used a brand new install of 10.04 desktop 64 bit. The only thing ever done on that install was the kernel build.

Help! I am very frustrated!!!

---

### Post by bodhi.zazen on 2010-08-15
> **starfry said:**
> I have just tried about ten times to build the kernel using these instructions. I get the kernel built, but it won't boot. Here's what happens:

mounting none on /dev failed : no such device
ureadahead main process 416 terminated on signal 5

It then goes to the splash screen which immediately gets garbled and then the machine hangs.

Any ideas?

To do this build, I used a brand new install of 10.04 desktop 64 bit. The only thing ever done on that install was the kernel build.

Help! I am very frustrated!!!

I could not get the openvz kernel to build on Ubuntu either.

There is a .deb in the Debian repositories (sid), but I could not get that one working on either Debian or Ubuntu (I have not tried recently).

If you want to use OpenVZ, use either Proxmox or Centos.

---

### Post by starfry on 2010-08-22
Ok, I am going to evaluate LXC making use of the info here and over on the Arch forums. I am going to evaluate under Ubuntu and Arch. OpenVZ was good but it's obviously time to move on...

Has anyone here had any luck getting X running in a container using the host's hardware? 

I believe I need /dev/mem in the container to do this but I can not get it to work. If I include a cgroup allow for it the container doesn't start:

```
lxc.cgroup.devices.allow = c 1:1   rwm # dev/mem
```

If I can get this to work it will be a big win for me...

---

### Post by bodhi.zazen on 2010-08-22
> **starfry said:**
> Ok, I am going to evaluate LXC making use of the info here and over on the Arch forums. I am going to evaluate under Ubuntu and Arch. OpenVZ was good but it's obviously time to move on...

Has anyone here had any luck getting X running in a container using the host's hardware? 

I believe I need /dev/mem in the container to do this but I can not get it to work. If I include a cgroup allow for it the container doesn't start:

```
lxc.cgroup.devices.allow = c 1:1   rwm # dev/mem
```

If I can get this to work it will be a big win for me...

Some words of caution :

1. LXC is not exactly openvz , and depending on what functions you are wanting they may or may not be available in LXC.

2. LXC is is fairly rapid development. There is what I think of as the "core" - LXC the userspace tools and then there are a number of other projects.

The LXC tools, IMO, should be used from git rather then your package managers. If you are using an old version, as with all things, you will almost certainly be advised to upgrade to the git version.

The "other projects" are a bunch of scripts, varying in complexity, to manage LXC containers. Some of these are more feature rich then others, others seem so obtuse that by time you figure them out, you could have written them yourself.

3. Ubuntu does not run well as a guest.

---

### Post by narcisgarcia on 2010-10-13
I've started a new thread here to solve a test-installation with LXC:
[http://ubuntuforums.org/showthread.php?p=9967793](http://ubuntuforums.org/showthread.php?p=9967793)

---

### Post by JedMeister on 2010-10-13
FYI for anyone interested in using OpenVZ under a 2.6.32 kernel:
Proxmox have released v1.6 of their VE (Virtual Environment) see [here]("http://pve.proxmox.com/wiki/Roadmap#Proxmox_VE_1.6_-_ISO_Installer_with_2.6.32_Kernel_with_OpenVZ_including_KVM_0.12.5") (was actually released month and a half ago but I only just realised and thought I'd share). As has already been discussed in this thread ProxmoxVE is a Debian Lenny based hypervisor OS which includes KVM and OpenVZ support with a nifty WebUI. The 2.6.32 kernel is AFAIK a custom PVE kernel based on the 2.6.32 Debian Squeeze OVZ kernel, with KVM support too. PVE have had a 2.6.32 kernel for some time but up until v1.6 it has only had KVM support. IMO PVE is the best option by far if you want trouble free OVZ support.

---

### Post by bodhi.zazen on 2010-10-13
> **JedMeister said:**
> FYI for anyone interested in using OpenVZ under a 2.6.32 kernel:
Proxmox have released v1.6 of their VE (Virtual Environment) see [here]("http://pve.proxmox.com/wiki/Roadmap#Proxmox_VE_1.6_-_ISO_Installer_with_2.6.32_Kernel_with_OpenVZ_including_KVM_0.12.5") (was actually released month and a half ago but I only just realised and thought I'd share). As has already been discussed in this thread ProxmoxVE is a Debian Lenny based hypervisor OS which includes KVM and OpenVZ support with a nifty WebUI. The 2.6.32 kernel is AFAIK a custom PVE kernel based on the 2.6.32 Debian Squeeze OVZ kernel, with KVM support too. PVE have had a 2.6.32 kernel for some time but up until v1.6 it has only had KVM support. IMO PVE is the best option by far if you want trouble free OVZ support.

Proxmox is the best .deb baised solution is is well done.

However, Centos is the other option. The openvz project tends to develop on RPM systems first, Centos is also rock solid stable, and the 2.6.32 kernel was available as a rpm before a .deb (the source did not build on a debian system and has had to be modified into the current debian kernel .deb).

While the Proxmox web interface is very nice, there are other web interfaces.

As far as a guest, I advise a Debian guest. squeeze runs fine as an openvz container with minimal modifications.

I have been playing with Ubuntu 10.10, but I can not build a container with debootstrap on Proxmox. I built a 64 bit container on Ubuntu 10.10 and will try it out on Proxmox in the next few days.

---

### Post by narcisgarcia on 2010-10-15
Hello, I've followed Runner85sx guide docummented on [https://help.ubuntu.com/community/OpenVZ](https://help.ubuntu.com/community/OpenVZ) and I was successful using Ubuntu's kernel 2.6.32-24-generic-pae, but I have 2 questions about packages used to compile:

- I see that using 2.6.32-24 results in 2.6.32-22-ovz. Is convenient to build dependencies for 2.6.32-22 version or can be patched any 2.6.32-x update?

- Since Ubuntu 10.04 there is no "-server" specific kernel in Ubuntu repositories. Is convenient to build dependencies specifying "-server" termination or it can be used system's current?

---

### Post by Runner85sx on 2010-10-16
Hello together.
I will update the guide today or tomorrow.


Greets Runner

---

### Post by narcisgarcia on 2010-10-16
Thanks, I'm at the middle of an installation and this matters to me.

Ah, one question: Why is needed the package exim4?

---

### Post by Runner85sx on 2010-10-17
I cant really update the guide today because g++ (>= 4:4.3.1) is broken in apt/aptitude today.

---

### Post by narcisgarcia on 2010-10-17
I installed an updated g++ (4:4.4.3-1ubuntu1) 12 hours ago, and I hadn't any problem.

I see that the current kernel for Lucid is 2.6.32-25 , which is not published in [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)
And from ubuntu I only see a basic "2.6.32.orig" source package.

---

### Post by Runner85sx on 2010-10-17
I installed Ubuntu Lucid again before 12 minuties and g++ is broken for me.

---

### Post by narcisgarcia on 2010-10-18
It could be interesting to know if
exactly the same process is useful to later compile and install a new kernel version (example 2.6.32-26)

---

### Post by narcisgarcia on 2010-10-28
Well I answer me: There is only a version to compile for 2.6.32 ; the -24 -25 -26 are only recompilations from the same Linux version.

---

### Post by narcisgarcia on 2010-10-29
Successfully installing OpenVZ... not 100% clean but better.

[The guide in community help]("https://help.ubuntu.com/community/OpenVZ#10.04%20LTS%20%28Lucid%29") works for me and I've tested it in 3 computers with Ubuntu 10.04.1
In every computer these messages are shown in a clean install without touching kernel and nothing about OpenVZ:
> 
init: *ssh* main process (*608*) terminated with status *255*
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
2 of the computers, after installing OpenVZ in all-compiling way (kernel + vzctl + vzquota + vzpkg), reproduce the following additional boot messages (in bold):
> 
**vzctl set 0 --cpuunits 1000 failed: /usr/local/sbin/vzctl: error while loading shared libraries: libvzctl-0.0.3.so: cannot open shared object file: No such file or directory..failed**
**/etc/rc2.d/S20vz: 477: vzlist: not found**
**mount: mounting none on /dev failed: No such device**
init: *ureadahead* main process (*226*) terminated with status *5*
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
Note that *vzpkg* package is marked as obsolete in OpenVZ, and few documented. Instead of compiling the utilities, I've tried to install Ubuntu repository's packages (vzctl vzquota vzdump) and then don't appear any error about "vzlist" or "libvzctl-0.0.3.so".
Only remains the "**none on /dev**" issue.

---

### Post by narcisgarcia on 2010-10-29
People sees server faults when formats container's filesystem (often the same as root) in Ext4, because of space quota feature.
OpenVZ patch isn't complete (stable) for kernel 2.6.32 version, as it can be seen in [the downloads directory]("http://download.openvz.org/kernel/") and [the wiki status]("http://wiki.openvz.org/Download/kernel/2.6.32").

There are 2 solutions:
[LIST]
[*]Format the partition where containers are stored in Ext3
[*]Disable disk space quotas feature, by setting the 'DISK_QUOTA=no' in the /etc/vz/vz.conf file
[/LIST]

---

### Post by narcisgarcia on 2010-10-30
I've completely revised [the guide in community help]("https://help.ubuntu.com/community/OpenVZ#10.04%20LTS%20%28Lucid%29"), and now almost all systems can work with OpenVZ on Ubuntu 10.04

I needed some complete days of docummentation searching and testing on several scenarios.
We may have now OpenVZ working for all the 10.04 LTS cycle. I hope that in 2015 LXC will be stable + decent + mature.

---

### Post by narcisgarcia on 2010-11-03
Does somebody know how to apply the file [kernel-ovz.spec]("http://download.openvz.org/kernel/branches/2.6.32/current/"), and if it couls have any advantage?

---

### Post by JimGvo on 2010-11-04
> **narcisgarcia said:**
> I've completely revised [the guide in community help]("https://help.ubuntu.com/community/OpenVZ#10.04%20LTS%20%28Lucid%29"), and now almost all systems can work with OpenVZ on Ubuntu 10.04

I needed some complete days of docummentation searching and testing on several scenarios.
We may have now OpenVZ working for all the 10.04 LTS cycle. I hope that in 2015 LXC will be stable + decent + mature.

As requested I'm commenting on our conversation from the OpenVZ wiki.  I apparently built my kernel a couple of days before you modified it.  That's why I was using an old kernel.  I have successfully built (maybe) a kernel based on 2.6.32-25.  I say maybe because it didn't boot.  I'm away from home and was doing it remotely but the server didn't come back up.  I don't have access to the console from 300 miles from home, so will have to see why it didn't boot  the next time I'm home.

The patching and compiling went along without a hitch.

Jim.

---

### Post by bodhi.zazen on 2010-11-04
> **JimGvo said:**
> I'm away from home and was doing it remotely but the server didn't come back up.

I learned this lesson as well, I do my testing on a VM. Testing is not 100 % on a VM , but at least when the VM fails it is not 300 miles away.

---

### Post by JimGvo on 2010-11-04
> **bodhi.zazen said:**
> I learned this lesson as well, I do my testing on a VM. Testing is not 100 % on a VM , but at least when the VM fails it is not 300 miles away.

For many things I do the same, howerver when compiling and testing an Open
VZ kernel I can't do it.  I suppose I could run virtualbox and then OpenVZ from within, but that's not my environment.  

It's not a big problem since the server is primarily my backup server and since I'm not doing any development, current backups aren't very important.

Jim.

---

### Post by JimGvo on 2010-11-09
> **JimGvo said:**
> As requested I'm commenting on our conversation from the OpenVZ wiki.  I apparently built my kernel a couple of days before you modified it.  That's why I was using an old kernel.  I have successfully built (maybe) a kernel based on 2.6.32-25.  I say maybe because it didn't boot.  I'm away from home and was doing it remotely but the server didn't come back up.  I don't have access to the console from 300 miles from home, so will have to see why it didn't boot  the next time I'm home.

The patching and compiling went along without a hitch.

Jim.

I found out why it wasn't working.  The -25 generic kernel wasn't working either, so the openvz version didn't have a chance.

See [http://ubuntuforums.org/showthread.php?p=10093281#post10093281](http://ubuntuforums.org/showthread.php?p=10093281#post10093281) for details.

Jim.

---

### Post by narcisgarcia on 2010-11-09
JimGvo, try the tutorial replacing this URL:
[http://download.openvz.org/kernel/branches/2.6.32/current/patches/patch-dzhanibekov.1-combined.gz](http://download.openvz.org/kernel/branches/2.6.32/current/patches/patch-dzhanibekov.1-combined.gz)
For this other one:
[http://download.openvz.org/kernel/branches/2.6.32/2.6.32-dyomin.1/patches/patch-dyomin.1-combined.gz](http://download.openvz.org/kernel/branches/2.6.32/2.6.32-dyomin.1/patches/patch-dyomin.1-combined.gz)

You will get a package for OpenVZ kernel Linux 2.6.32.22 , and worked fine for me.

---

### Post by JimGvo on 2010-11-09
> **narcisgarcia said:**
> JimGvo, try the tutorial replacing this URL:
[http://download.openvz.org/kernel/branches/2.6.32/current/patches/patch-dzhanibekov.1-combined.gz](http://download.openvz.org/kernel/branches/2.6.32/current/patches/patch-dzhanibekov.1-combined.gz)
For this other one:
[http://download.openvz.org/kernel/branches/2.6.32/2.6.32-dyomin.1/patches/patch-dyomin.1-combined.gz](http://download.openvz.org/kernel/branches/2.6.32/2.6.32-dyomin.1/patches/patch-dyomin.1-combined.gz)

You will get a package for OpenVZ kernel Linux 2.6.32.22 , and worked fine for me.


I did get a 2.6.32.22 kernel, but it didn't work.  It fails with the splash screen showing The disk drive for / is not ready yet or not present.
Continue to wait: or Press S to skip mounting or M for manual recovery.

If I press M I get:

some messages, of little importance and in the dmesg I see

ext4-fs sda5 mounted fs with ordered data
vfs mounted root (ext4 fs mode 3 ro on dev 8:5)

Not much else of interest.  If I wait, it never continues, if I press S I get a list of some modules loaded and then:

init: plymouth main process killed by segv signal

it then waits for a long time.  If I press C-A-D it will reboot so it isn't hung, just pausing.  An enter doesn't do anything.

I'd really hate to have to run RHEL on this system.  I'm quite pissed at Ubuntu for abandoning OpenVZ before a viable alternative is stable.

Jim.

---

### Post by narcisgarcia on 2010-11-10
- Have you read notes about ext4 and OpenVZ (ext3 or disable quotas)?
- Are you using GRUB1 or GRUB2?

---

### Post by JimGvo on 2010-11-11
> **narcisgarcia said:**
> - Have you read notes about ext4 and OpenVZ (ext3 or disable quotas)?
- Are you using GRUB1 or GRUB2?
No I don't know about ext4.  I don't use quotas.

I believe the default is GRUB2. And I think that's what's be used.

Jim.

---

### Post by realloc on 2011-02-21
> **ribo said:**
> So, I got into my containers finally, made two of them.

How did you get past this error?

```
init: lxc pre-start process (2) terminated with status 32
```

I am getting the same thing (trying to set up a new LXC container).

---

### Post by bodhi.zazen on 2011-02-21
FYI: There is an openvz kernel available in the Debian repositories.

See : [http://www.howtoforge.com/installing-and-using-openvz-on-debian-squeeze-amd64](http://www.howtoforge.com/installing-and-using-openvz-on-debian-squeeze-amd64)

I have not tried this kernel, but you could look at the sources and / or compile your own kernel if you so desire.

---

### Post by JedMeister on 2011-02-21
I have not tried the Debain Squeeze kernel either but I know someone who has (under Debian) and it seems to be working fine for them.

---

