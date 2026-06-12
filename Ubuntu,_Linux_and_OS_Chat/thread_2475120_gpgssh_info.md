---
title: "gpg/ssh info"
date: 2022-05-17
forum: Ubuntu, Linux and OS Chat
---

### Post by coley9225 on 2022-05-17
Hello again friends and neighbors. Hope everyone is doing well today. I come to, again ask for your tips, advise and references to further reading.

I recently read a tutorial from  linuxbabe on gpg. I made a key pair, uploaded to default keyserver, and tested it. I seem to have done all that correctly.
I'm also looking to explore ssh. I've read some stuff, and I *think *I understand the absolute basics, but still have more questions. References to additional reading would be very helpful with that.

Besides just having ssh knowledge in the back of my head, my reasons are twofold.  First, My daughter(granddaughter actually) was given a desktop computer. All I know about it so far is it is running win 7. I want to learn how to ssh into her machine, and help her with things, as she knows pretty much nothing about computers. I'm trying to talk her into dualbooting with lubuntu, before she gets the windows ways tatooed to her brain, but that is a work in progress.

My second reason, I would love to buy a new computer, then use my laptop as a server for media file, files to share with others in my home, etc. Because I do not have access to a second computer, how can I practice what I learn, to gain some "hands on" experience with ssh. Possibly 2 VMs, 1 windows and 1 linux, and ssh into those??
I know little about VMs, do they have their own ip address? More questions than knowledge at this point, but rest assured, with your help, and more reading, that will soon change.

Again, I'm not asking you folks for all the answers. I'm primarily looking for references to further info, and any tips, advice,etc that you can give.

Any help would be, as always, much appreciated.  Thanks. Now, back to the man pages.

---

### Post by TheFu on 2022-05-17
A) Please don't post a wall of text.  Use paragraphs for different ideas/issues.  Please make is easy for people to read and follow posts.

B) Win7 doesn't support sshd - at least not a secure version.  I recall trying to setup sshd on Win7 about a decade ago and the available solution had some major security warnings that convinced me to stop.  Of course, using ssh as a client FROM win7 was as secure as for any other platform. PuTTY was the common solution.

Win10 includes ssh (finally) which works as close to the same as any other ssh client on Unix/Linux, just with the limitations of MS-Windows and their terrible command prompt and lack of select/paste and an excellent shell.  To fix the shell issue, there's WSLv2 which I think provides bash.

If she is under 10 yrs old, then you could help her to learn computers like this guy did: 
[https://lifehacker.com/i-raised-my-kids-on-the-command-line-and-they-love-it-5974087](https://lifehacker.com/i-raised-my-kids-on-the-command-line-and-they-love-it-5974087)  It keeps them interested AND teaches them how computers really work.

But if she is 12+, the fight is probably lost already.

I couldn't read any farther. wall-of-text made it too hard.

---

### Post by DuckHook on 2022-05-17
Hmm…

To my mind, the first order of business is Win 7. This is a dumpster fire waiting to happen. W7 has been out of support for some time and, given that it is Windows, it is thoroughly compromised by now. The only way to run it safely is in a VM with all network access disabled, which means that you can't ssh into it to help her. At a minimum, she should be on W8, but there's little point in that. Just go straight to 10 or 11.

I'm not sure that getting her started in Linux is the right strategy. The reality is that it's a Windows world out there, especially for young people focused on what their peers are doing. The Linux world is awesome, but it may have to come later and of her own accord. You could plant the seeds now by installing a VM with Linux on it, or having her over more often to play on your machine, but starting her out on Linux is kind of limiting given typical young people desires.

As for your own needs, running a stack of VMs, then practising your networking skills on this virtual network, is a great learning strategy. It's exactly how I learned much of my networking basics. There will be some things that you can't do because VMs are significantly different from real infrastructure, but those differences are pretty plain and obvious.

There's a link in my sig: Resources for Newcomers

It contains a wealth of further links to really good learning resources. What you are looking for would be under the section: Free books for advanced GNU/Linux system administrators

Don't be intimidated by the "advanced" part—the concepts are not that hard to grasp if you already have a basic understanding of Linux and are not allergic to the command line.

Last but not least: I've tried using old laptops as servers in the past. While they work nicely for some sorts of servers, when it comes to file servers, they are brittle. This is because they must rely on USB HDDs for storage and USB is notoriously unreliable. You cannot even do proper HDD diagnostics over USB. Since purchasing proper machines for my file servers, I haven't had to wrestle with those alligators anymore.

It needn't be expensive: two of my file servers are obsolete Western Digital MyBook Live boxes where I've replaced the original firmware with OpenWRT (a highly versatile Linux&#8209;based appliance OS). I bought them for US$40 on ebay. I bought two so that I could mirror them for redundancy. Mirroring is done every night with a dead simple rsync script and cron. The biggest expenditure was a high capacity HDD, but you would be buying one for the laptop anyway, so that's a wash.

If rehabilitating old appliances is not your thing, then a cheap and cheerful dedicated file server box is not *that* expensive. I recently purchased one from Amazon for $300, in my case, for use as a router, but it could easily have been used for a file server. It has room for only one HDD and is passively cooled. If used as a file server, you would be running a cli environment and won't need much RAM—possibly as little as 4GB. This would keep the cost down too.

---

### Post by coley9225 on 2022-05-17
Thanks for the responses. First, my apologies for the 'wall of text'. I see your point about readability, I try to make things a little better from here on out.

TheFu, my granddaughter is 9, and loves to get on my computer when she's here. I do not have windows, nor plans to reinstall windows, but she is fascinated with the scripts I wrote, and seems a little interested in learning to do the same. It's a start. My daughter wants me to upgrade their computer to win10, but we haven't worked out the scheduling yet.

DuckHook, As mentioned, working on upgrading their box, and would love to set up dual boot, that way she can begin to get the basics for now.

I wasn't sure if VMs had a separate ip address so I could use ssh or not. I'll go that route for the time being. 

I was thinking of laptop as a server as a short term thing, just to experiment. It wouldn't have anything on there that can't be replaced. I have a 1TB ssd in it now, and could buy a caddy to convert the optical drive to a second hdd, so would have plenty of storage. I'll look into a use computer to use instead, and keep the laptop synced with a desktop for use when I'm away from home.

I'l definitely check out your links, sounds as if I find good info there.

Thanks again for the info guys

---

### Post by DuckHook on 2022-05-17
Ah. I see. A budding IT genius. In that case, Linux might be just the ticket. I shouldn't have jumped to conclusions. It's just that, in my experience, youngsters are more interested in games and social media. Linux is not strong in either category.

If you are okay with 1TB for storage, then in fact there is nothing wrong with using a laptop for a file server. Again, faulty assumptions on my part. I thought that you wanted multi TB storage that would only be available on an external drive. If it's internal, then a laptop that sips a small fraction of a desktop's power is actually a good solution. And especially if it's just for experimenting, then there's nothing wrong with your plan.

A further site that I've found useful is: [https://linuxjourney.com/](https://linuxjourney.com/)

I'm serious about Win 7 though. Do not allow that OS on the Internet. Nothing but really bad trouble can come of it.

---

### Post by TheFu on 2022-05-17
> **coley9225 said:**
> Thanks for the responses. First, my apologies for the 'wall of text'. I see your point about readability, I try to make things a little better from here on out.


You'll likely get more responses if you edit the first post and break up the wall-of-text a bit.  You can edit any post you've made if the thread hasn't been CLOSED by forum staff.

---

### Post by coley9225 on 2022-05-17
I have edited my OP, hope it's a little easier to read now.

DuckHook, great links you have there. I've had the cl book for quite some time now, and have bookmarked the resources link, as well as the new one you posted.(I may go through that one myself!) 

I was looking at your tutorial on lxd containers. Do you think that would be a better option for me than VMs? I will have to figure out the process either way, and if lxd containers are the better option, I'll just go that route, I've not really had a good experience with VMs anyway. I have aprox 500 GB of unallocated space on my internal ssd, and multiple hdd and an enclosure to had them, so space isn't an issue.

Again, I can't you guys enough for the help.

---

### Post by TheFu on 2022-05-17
LXD only runs Linux, not Windows, not BSD, not any other OSes.  They share the same kernel as the host.

VMs provide fake hardware that looks like hardware that the guest VM sees.  There are some drivers specifically created to be more efficient that are just for VMs. Those should be used.

Which is better, lxd or VMs?  The answer is it depends.  Don't forget that there are 20 other Linux Container methods and that LXD really isn't very popular.

With VMs, you can treat the VM like a physical machine. That's what I do.
I also use LXD for some specific needs. There are things I like and things I dislike.  LXD is about halfway between the protection that a full hypervisor like KVM-QEMU provides and what Docker Containers provide.  The great thing about Docker is there are many thousands of pre-built tools/servers for it.  The terrible thing about docker is that most of those pre-built containers shouldn't be trusted. It is easy to forget where a container was from and inappropriately trust it, especially if you are really busy.

For media files, an external USB3 or faster storage should be fine. Be certain you have a place for backups. 

VMs are about 10x heavier than lxd.  But if you want to run Windows under Linux, then you don't have any choice.  I use lxd containers for my LAN DNS, pi-hole, email gateway, and for a wallabag web-app server.  I have plans to move my nextcloud setup from a full VM to a container. I'll keep all the storage outside the container to avoid issues. The best practice for containers is for them to be used for CPU and providing services, not for storage heavy needs.  VMs should be used for things that are a little more risky and where the separation of the OS from the host hypervisor OS is really important.

I do have concerns that an IdeaPad would have a fast enough CPU for anything other than small, webapps and only if a container is used.

BTW, DuckHook has plenty of LXD experience. Far more than I and my uses are for pure servers, no GUI things.  I've been running VMs since the late 1990s at work.  Over the decades, I've used about 10 different VM hypervisors. In 2011, I started migrating off virtualbox, Xen, VMware ESXi and onto KVM-QEMU with libvirt and virt-manager.

As for networking, virtual machines usually have 4 different ways for the network to be setup under the VM.  On Linux, the networking is separately configured from the VM.  Most people would choose a "bridge". To have a bridge on Linux, that needs to be manually configured outside any virtualization.   Oh ... and you'll want your VM host to use static IPs, not DHCP. While it is technically possible to use DHCP, if your network skills aren't pretty good, you'll just have problems. Any server needs a static IP.  Just take that as the rule. Your life will be 10x easier that way.  Of course, if you have static IPs, that also means you'll likely want to have an internal DNS and otherwise run a well-managed IP network.

I don't really provide links, since google is how I find this information, when I need it.  I try to stick with reputable websites, typically with Ubuntu in the domain name, for the best quality information.  help.ubuntu.com is where the official Canonical stuff is.   I've followed LinuxBabe too, but she sometimes misses important security considerations, IMHO.  Her guides generally work and to my eye, they are the shortest and usually complete. She's been responsive to feedback too, which is pretty impressive, unlike some more famous, larger, tech sites behind larger 200+ people companies.

---

### Post by DuckHook on 2022-05-17
> **coley9225 said:**
> …I was looking at your tutorial on lxd containers. Do you think that would be a better option for me than VMs? I will have to figure out the process either way, and if lxd containers are the better option, I'll just go that route, I've not really had a good experience with VMs anyway. I have aprox 500 GB of unallocated space on my internal ssd, and multiple hdd and an enclosure to had them, so space isn't an issue.
I have to be honest: although LXD is a wonder once it is mastered and up and running, it is a royal pain getting it set up properly. There are no man pages, documentation is Spartan, there are few online resources and it is saddled with an unreasonable level of arcanery and obscurity.

It is really meant for power users with hides tougher than those of rhinoceroses who don't mind spending hours sifting through web searches for the few nuggets of useful hints, explanations and workarounds. It also helps to have a magic wand lying around.

Though I have a link in my sig pointing to a LXD tutorial, I would recommend this platform only for someone who is entirely at home with the command line and is a geek/tinkerer at heart. For those who just want something to work with the minimum of effort, it requires too much time investment and wailing and gnashing of teeth.

Using my own experience for measure, on a ten point scale, I would compare respective difficulties as follows:

[LIST]
[*]Learning, installing and using VirtualBox — 3
[*]KVM/QEM — 5
[*]LXD — 9
[/LIST]
To be fair, I would apply the same numbers to each of these three platforms' usefulness too, so it's another example of the reward being commensurate to the investment.

TheFu is spot on that LXD is not very popular (else it would have better documentation). And he is also right that your only choice for Windows is a VM. Windows will not run in a container (although it is possible to install a streamlined VM within LXD, then Windows within that, but let's not even go there).

All in all, I would recommend that you get comfortable with VMs first. If you then want to explore LXD, you can do so at leisure and without feeling that you have to rely on it for anything.

---

### Post by coley9225 on 2022-05-18
Thanks so much for the input guys. I looks like I'm about to get more familiar with VMs. I'll continue to look into LXD, but for now just leave it as a back burner project.

---

### Post by TheFu on 2022-05-18
> I have to be honest: although LXD is a wonder once it is mastered and up and running, it is a royal pain getting it set up properly. 
Very true.  Most of the issues I had getting it setup came down to 3 issues.

* The LXD team **really** likes ZFS.  Using any other back-end storage is counterproductive. I don't use ZFS due to some circumstances here, but I ended up creating a file-based block device to place ZFS on, just for LXD needs.  I would have rather used LVM, which I'm more familiar with and have been using 20 yrs. Alas, I was unable to figure out how to convince LXD to use LVM.

* Networking.  This wasn't really much of an issue for me, but I have network bridges setup on most of my physical machines for use by VMs.  LXD can be hooked into any of those bridges, but most new users wouldn't know what a bridge is or how to set them up.  I think by default, LXD sets up a new NAT subnet for containers.  I don't recall today.  It is a common solution for VM desktops and makes sense.  But for "servers" - say a container running a small internal-only website - having bridged network is more sensible.  In Linux, networking isn't part of the container or VM tools.  It is separate, so if the admin setting things up (this applies to all hypervisors too), they need to setup at least 1 bridge too.

* Snap package.  LXD is only available as a snap package with all the great and terrible things about that constrained package format and running in that environment.  The other issues, above, would be there regardless of the snap or no snap.  I have to setup different userids to run snaps, since my normal user cannot due to some decisions by the snap package team around where home directories must be located and which storage can be used.  They have valid reasons for this, but other, similar, package tools allow local overrides. Snaps to not.  Also, I'd like more control over where VMs are stored.  Due to snap constraints, access to storage locations they haven't 'blessed' and actually hard coded, we cannot.

I'll probably never use LXD for anything with lots of data. It will only be used for 1-off, small, internal, services where most of the data isn't tied to the snap.

Though documentation is a little odd for lxd, it is there.  They just split up the documents for 1 command into 10 other manpages, which have lots of details, but lack the caveats and 'why' certain options should be used or not.  LXD is the name of the system and daemon, but lxc (this can be confusing) is the main program used post-install of the LXD system.  There are manpages for .... well .... here are some of them.
```
lxc                                lxc.image.alias                    lxc.profile.edit
lxc.alias                          lxc.image.alias.create             lxc.profile.get
lxc.alias.add                      lxc.image.alias.delete             lxc.profile.list
lxc.alias.list                     lxc.image.alias.list               lxc.profile.remove
lxc.alias.remove                   lxc.image.alias.rename             lxc.profile.rename
lxc.alias.rename                   lxc.image.copy                     lxc.profile.set
lxc.cluster                        lxc.image.delete                   lxc.profile.show
lxc.cluster.enable                 lxc.image.edit                     lxc.profile.unset
lxc.cluster.list                   lxc.image.export                   lxc.publish
lxc.cluster.remove                 lxc.image.import                   lxc.remote
lxc.cluster.rename                 lxc.image.info                     lxc.remote.add
lxc.cluster.show                   lxc.image.list                     lxc.remote.get-default
lxc.config                         lxc.image.refresh                  lxc.remote.list
lxc.config.device                  lxc.image.show                     lxc.remote.remove
lxc.config.device.add              lxc.info                           lxc.remote.rename
lxc.config.device.get              lxc.launch                         lxc.remote.set-default
lxc.config.device.list             lxc.list                           lxc.remote.set-url
lxc.config.device.override         lxc.move                           lxc.rename
lxc.config.device.remove           lxc.network                        lxc.restart
lxc.config.device.set              lxc.network.attach                 lxc.restore
lxc.config.device.show             lxc.network.attach-profile         lxc.snapshot
lxc.config.device.unset            lxc.network.create                 lxc.start
lxc.config.edit                    lxc.network.delete                 lxc.stop
lxc.config.get                     lxc.network.detach                 lxc.storage
lxc.config.metadata                lxc.network.detach-profile         lxc.storage.create
lxc.config.metadata.edit           lxc.network.edit                   lxc.storage.delete
lxc.config.metadata.show           lxc.network.get                    lxc.storage.edit
lxc.delete                         lxc.profile.delete                 lxc.storage.volume.get
lxc.exec                           lxc.profile.device                 lxc.storage.volume.list
lxc.file                           lxc.profile.device.add             lxc.storage.volume.move
lxc.file.delete                    lxc.profile.device.get             lxc.storage.volume.rename
lxc.file.edit                      lxc.profile.device.list            lxc.storage.volume.set
lxc.file.pull                      lxc.profile.device.remove          lxc.storage.volume.show
lxc.file.push                      lxc.profile.device.set             lxc.storage.volume.unset
lxcfs                              lxc.profile.device.show            lxc.version
lxc.image                          lxc.profile.device.unset           

```
More documentation than anyone would read.

Most of us would find a walk-thru guide and follow that, trusting it does "the right thing." Once the networking, storage, and minimal understand for LXD are solved, getting from idea to having a new server is, perhaps 5 minutes.  LXD containers are treated very much like VMs, which no other linux containers can be done that way.  

lxc - is a terrible choice for the LXD client program. This is because the first set of scripts to create Linux Containers 15 yrs ago was named "lxc" and this was used by everyone else with their on containers, including Docker, for years.  lxc (lxd's version) is not that lxc.  None of those manpages listed above are either. 

Confusion.

Canonical has and end-user KVM VM tool called **MultiPass**.  I've never gotten it to work, but that's more about their choice to make it a constrained snap package. Besides lxd, I've struggled to get most snaps working. Snaps are not flexible and THAT is a huge issue for Linux systems.

---

### Post by coley9225 on 2022-05-18
OK..status update.
It took me better part of the day, but I now have kvm/qemu installed, and working lubuntu 21.10 on it. Static ip set. I was able to ssh into the VM. I edited my ssh_config so all I have to type is
```
ssh coley
```

and I am ssh'ed into lubuntu VM. So far so good...HOWEVER...
I noticed that the VM is located in my / partition. Is there a way to make it go to my /home partition, or even a seperate partition. I have a large amount of room on my ssd, but unsure how to resize or move /home, and the resize /.
I have limited space left in my / partition, and don't want to fill it up, so moving to /home or a separate partition would be tremendous help. Ideas?
I can post returns of any commands you may need to help me with this.
Thanks

---

### Post by TheFu on 2022-05-18
lubuntu 21.10 support ends in less than 2 months. Should have started with 22.04 or 20.04, which are LTS releases with 3yrs support.  20.04 Lubuntu support will end next April, but you'll have many months to consider the migration.

KVM is an enterprise virtual machine tool. If you use libvirt to manage VMs (and I wouldn't do it any other way), it expects VMs to be something that isn't per user, but managed by a team.
Don't put shared things under your HOME, especially not VMs.  Put them somewhere else or mount some extra storage specifically for VMs where libvirt expects.

There are multiple solutions to adding storage where it is needed.  

[LIST]
[*]If you used LVM with your OS at installation time, you can tell libvirt about that and have new VMs use LVM-LVs. This assumes that the VG has unallocated storage, which is an LVM best practice. These are all LVM-LVs, each assigned to a virtual machine:
```
$ sudo lvs
  LV             VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-blog44-1804 hadar-vg -wi-ao----  16.20g                                                    
  lv-regulus     hadar-vg -wi-ao----  30.00g                                                    
  lv-regulus-2   hadar-vg -wi-ao----  10.00g                                                    
  lv-tp-lxd      hadar-vg twi-a-tz--  32.23g             0.00   10.06                           
  lv-vpn09-2004  hadar-vg -wi-ao----   7.50g                                                    
  lv-xen41-1804  hadar-vg -wi-ao----  12.50g                                                    
  lv-zcs45-1804  hadar-vg -wi-ao----  25.00g                             

```
[*]Mount a separate partition or LVM-LV directly to the libvirt area, sized as needed.
```
$ sudo lvs
  LV             VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  libvirt-lv     hadar-vg -wi-ao---- **175.00g**                                                    

$ df -Th /var/lib/libvirt
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-libvirt--lv ext4  **173G**  132G   33G  81% /var/lib/libvirt

```
[*]Tell libvirt about a different storage area.  Either **virt-manager** or **virsh** can be used for this. The virsh manpage has a section called "_STORAGE POOL COMMANDS_" which goes into how to do this.  In virt-manager, there is a Details for the KVM server, then Storage is a tag. The left-hand columns are the major storage groups. At the bottom of the current list, there is a "+" to add more storage groups. I have 6 different storage groups, but almost always, I choose the LVM-VG. It is crazy convenient to use and since the storage isn't mounted to the file system, there is a bit of safety from people accidentally deleting it.  Also, no /etc/fstab issues, since they aren't in the fstab. Creating and deleting LVM-LVs through this interface are nearly instant. You can add either a "Filesystem Directory" location or point it a an "LVM Volume Group" or  ... well, there are 12 different back-end storage options, like Sheepdog, Gluster, NFS, direct disks, SCSI, iSCSI, and others.  I'd warn against using any storage under /home/ or any storage on USB connected storage.
[/LIST]

Those are the options.

---

### Post by coley9225 on 2022-05-21
I want to again thank you guys for the help.
I pretty much got what I was looking for here. Great references, some tips, and some advise. Some I have already started using, and some(LXD, LVM) I will look into further.

I handled my storage issue, for now, by creating a 300GB partition, made a mount point, /home/charles/KVM_pool, and added an fstab entry for that. That is working great. The 'guts' of the app remains at the default location, and the images get place on the seperate partition.
I have run into a new issue though. However, since I have worked this thread for what I needed, and the new issue(s) are a support type of thing, I will start a new thread in the networking sub-forum to address those.

You guys(community in general) don't get thanked nearly enough. I want to emphasize that you are not unnoticed, or unappreciated. Please, continue the great things you do for us new guys.

I will continue to monitor this thread in case someone has more ideas or references for me to consider.

---

### Post by TheFu on 2022-05-21
Thanks for the kind words.

I would caution against using this location for VMs. /home/charles/KVM_pool.  Placing mounts under a user's HOME is a bad idea. There are a number of issues that we have seen with doing this.  I'd rather see you mount that partition to /var/lib/libvirt where libvirt expects the default storage pool to be.

But it is your system.  You've been warned.

---

### Post by coley9225 on 2022-05-21
TheFu, thanks for the tip. I mounted in /home/charles because  I thought it would be safer, as it isn't touched during a release upgrade. I think I know how to do this, but I want to make sure.

First, unmount the partition;
```
sudo umount /home/charles/KVM_pool
```

Second, edit fstab;
```
## current entry for KVM_pool
UUID=c23e8deb-98eb-437a-834f-7a9287937dc0  [COLOR=#ff0000]/home/charles/KVM_pool[/COLOR] ext4 auto,rw,async,user 0 0
## edit to read
UUID=c23e8deb-98eb-437a-834f-7a9287937dc0 [COLOR=#ff0000] /var/lib/libvirt/images [/COLOR]ext4 auto,rw,async,user >
```

Third, edit default pool as follows;
```
## existing entry
    <path>/home/charles/KVM_pool/images</path>
## edit to
<path>/var/lib/libvirt/images</path>
```

Finally, remount the partition;
```
sudo mount /var/lib/libvirt/images
```

If this is not correct, please let me know. I will hold back on making the changes stated above until I'm sure this is correct.

---

### Post by TheFu on 2022-05-21
Just be certain that you stop all VMs and KVM and get any directories/files in /var/lib/libvirt/images/ moved to the new storage first.

The fstab above isn't complete.  Looks like the copy/paste missed the last 2 fields which are critical.
I wouldn't use those options.  This is my exact fstab line:
```
/dev/hadar-vg/libvirt-lv  /var/lib/libvirt    ext4     noatime,errors=remount-ro 0 2
```
I use LVM, so the first field points to the LVM-LV.  You'd use the UUID= method.

---

### Post by coley9225 on 2022-05-21
Thanks. I only have the images stored on the separate partition, all config files, binaries, etc. are store at default locations. I'm not moving the storage itself, just changing the mount point. I have all VMs stopped, and closed virt-manager. I'll double check to see if anything else is running and stop those. God willing and the creeks don't rise, this should go smoothly. If not, I'll be back looking for more help.

---

### Post by TheFu on 2022-05-21
> **coley9225 said:**
> Thanks. I only have the images stored on the separate partition, all config files, binaries, etc. are store at default locations. I'm not moving the storage itself, just changing the mount point. I have all VMs stopped, and closed virt-manager. I'll double check to see if anything else is running and stop those. God willing and the creeks don't rise, this should go smoothly. If not, I'll be back looking for more help.

I think it should work.  When I did it, I hadn't migrated any VMs to the new machine yet, so I really don't know if that is sufficient.  The kvm+libvirt subsystem may have open files even when they aren't used.  A reboot after changing it in the main install should be sufficient. Worst case, boot into a Try Ubuntu environment from flash media and move the mount.  Always have a flash drive with the same version of Ubuntu (flavor doesn't matter) available to fix still stuff like this.

---

### Post by coley9225 on 2022-05-21
It worked, with a little work. Kept changing paths, and still couldn't get 'virsh pool-start default' to work. also couldn't start any VM. I finally solved that. I had to edit each VM xml file to the new path, after that, it's working fine. I was just using ssh to update and upgrade each of them.
By the way, you were curious as to why I installed lubuntu 21.10 when support ends soon. I wanted to see if I could do a release upgrade via ssh. That went very well, it is now a full 22.04 OS. It also let me 'test run' the process so I could be sure I understood it, so I can reduce any chance of surprises when I do the release upgrade on my bare metal install. That was a new install with almost no added apps whereas I have added a great deal to my computer, but now I know what to expect.

Again, many thanks.

ps.. I have 2 bootable usb drives with the installers, of multiple distros. All I need to do is get more familiar with chroot, but enough knowledge to get the most common issues handled.
Plus, there's alway the forums to help.

---

### Post by TheFu on 2022-05-21
The reason to avoid creating VMs BEFORE doing a planned system upgrade to a new distro, is because the qemu-virtual-machine used will be for the older release.  For Linux distros, changing the motherboard model to a newer one isn't an issue that I've had, but for some commercial OSes, like that "other OS", you'll be stuck with the old fake motherboard, perhaps for decades, since changing the motherboard will invalidate the license. For example:
```
Win7Ult.xml:    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
WinXPPro.xml:    <type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
```

If I change those, bad things happen, like license reactivation is mandated.

So, when USB5 becomes available and your OS was installed with USB2/3 as the only known options, then the newer hardware won't support the faster connectivity.

Just something to consider.

---

### Post by kevdog on 2022-05-22
Is lxd an Ubuntu thing or is this taken from Debian (as I'm aware Proxmox can run this type of containerization). Can I use this type of virtualization on Fedora?

---

### Post by TheFu on 2022-05-23
> **kevdog said:**
> Is lxd an Ubuntu thing or is this taken from Debian (as I'm aware Proxmox can run this type of containerization). Can I use this type of virtualization on Fedora?

Don't confuse LXC and LXD.  LXD is a Canonical management system, deployed as a snap package on any Linux platform.  

LXC was the original name of Linux Containers from 2013 times. [https://en.wikipedia.org/wiki/LXC](https://en.wikipedia.org/wiki/LXC) Basically, from 2.6.24 and later, the ability to have cgroups and namespaces has been part of the Linux kernel.  It really wasn't until the 3.8 kernels that it took off (to my recollection). Early versions used the host root user and it was possible for the container to modify things on the host.  Non-root containers weren't easily available for many years. Docker created "privileged containers" for many years, which any security conscious person would consider a non-starter for that technology and choose full VMs.  I think 3.11 finally allowed unprivileged containers, with some support packages.  

Canonical seems to be backing the lxc project now and the core developers for lxc and lxd overlap.

Clear as mud?

[https://discourse.ubuntu.com/t/lxd-4-0-quick-recipe-lxc-and-kvm-coexisting/15222](https://discourse.ubuntu.com/t/lxd-4-0-quick-recipe-lxc-and-kvm-coexisting/15222) can help understand how libvirt, lxd, kvm can be used together. There are many, many, many, things I like about lxd and a few things that are Canonical choices which I disagree concerning.  That link has actual commands to setup an lxd system and create a few lxd containers and kvm VMs. Importation of existing VMs might be possible. I've never looked into that.

Think of lxd as a replacement for libvirt and virsh.

---

### Post by DuckHook on 2022-05-24
> **kevdog said:**
> Is lxd an Ubuntu thing or is this taken from Debian (as I'm aware Proxmox can run this type of containerization). Can I use this type of virtualization on Fedora?
To my very, very limited knowledge, Proxmox indeed runs LXD and so does Fedora. I'm talking about LXD in the sense that TheFu is: the management platform on top of which all of that namespace magic happens. In the case of Proxmox, they've chosen to piggyback much of their functionality on LXD. So they have made a deep commitment to the LXD platform and have tied their fortunes to it.

In the case of Fedora, it's just another container option. They are supporting it as an alternative to Docker.

The results are the same but the motivation is quite different. I have confidence that Proxmox will continue to support LXD; less so about Fedora.

---

### Post by kevdog on 2022-05-27
Thanks @DuckHook and @TheFu.  Still looking into exploring lxd/lxc.  I just don't want to be stuck with a container or virtualization system that unfortunately is only applicable to Ubuntu.

---

### Post by TheFu on 2022-05-27
> **kevdog said:**
> Thanks @DuckHook and @TheFu.  Still looking into exploring lxd/lxc.  I just don't want to be stuck with a container or virtualization system that unfortunately is only applicable to Ubuntu.

It will work on any Linux that supports snaps and has the appropriate CPU architecture.  LXD will work places that KVM does not, providing you can meet the snap requirements (which many of my systems cannot).

---

### Post by kevdog on 2022-05-28
@TheFu

Honestly hate the direction Ubuntu is going with the snap requirements.  Not trying to beat a dead horse here but it seems like they are treading uphill alone on the snap implementation on this one.  I like virtualization solutions however I don't like one that locks me into specific linux distributions.

---

### Post by TheFu on 2022-05-28
Sorry if it isn't clear, but snaps are NOT specific to any Linux distro, therefore lxd isn't specific to any Linux distro.

Sure, I'd much prefer that lxd and the included lxc be normally packaged, without snaps. Then it would work on more of my systems, but for most home users, with reasonable CPU, RAM, and storage, snaps are probably a good thing.

Canonical decided that allowing too many controls for most people just makes them anxious.  That doesn't make grandma prefer Ubuntu, which I fear is Canonical's target user.  Well, grandmas and IoT device makers.

For me and my use, snaps are an abomination. I put up with a few and purge most systems of any snap stuff.  I'll probably be switching desktops from Ubuntu in my next upgrade to avoid snaps. Have about a year before that is forced.  Servers are a harder choice for me.

---

### Post by #&amp;thj^% on 2022-05-28
> **TheFu said:**
> 
 but for most home users, with reasonable CPU, RAM, and storage, [B]snaps are probably a good thing.
[/B]

For me the jury is still out on that point. ;)

---

### Post by DuckHook on 2022-05-29
> **1fallen said:**
> For me the jury is still out on that point. ;)
I feel snaps to be a mixed bag with the potential to get better (which gives me hope). However, in their current incarnation, I am forced to find workarounds, but only for *some* apps, so I can't condemn the entire platform.

I am in soft agreement with TheFu that they are probably a good thing for general home users with sufficient HW requirements. I applaud the idea of automatic default sandboxing. While this gives rise to certain complaints, we forum members need to guard against confirmation bias—in this case, negative confirmation bias. We hear only of the problems, but none of the successes, since people who are happy with their install rarely come on the forums to tell us how delighted they are. Likewise, the problems that sandboxing prevents (like stopping malware) aren't going to get mentioned either. How does one even recognize, much less report, the *absence* of a problem?

My only criticism of snaps is that there are not enough options to fine tune such sandboxing (including bypassing it altogether). I'm optimistic that this will get better with time.

In fact, the devs do recognize some of the issues arising from snaps and are slowly working on them. This just in: [https://www.omgubuntu.co.uk/2022/05/ubuntu-making-firefox-snap-app-faster](https://www.omgubuntu.co.uk/2022/05/ubuntu-making-firefox-snap-app-faster)

---

