---
title: "Ubuntu server on Esxi6 memory requirement"
date: 2016-10-13
forum: Server Platforms
---

### Post by ispoon on 2016-10-13
Hi, I have install ubuntu server before on Hp microserver 16GB ram running samba and plex. however I would like to move it to ESXi 6 now.

Would like to know how much disk space should I assign to ubuntu server (non gui) and how much ram for it, samba will be serving 2-5 max users, plex will at most 2 users.

Also wants to find out if its possible to create a virtual disk space from Esxi datastore and use it as samba share folder in Ubuntu. i.e.: create the virtual disk and mount to Ubuntu and use it as samba path. I try google but no result on this so please advise if its possible.

Thanks in advance

---

### Post by mastablasta on 2016-10-13
5-8 GB for OS, as much ram as you can spare. i would say min 512 MB. not sure on plex requirements though. does it "eat ram"?

---

### Post by ispoon on 2016-10-13
plex require 2gb ram for typical use according to website.

my microserver only have 16GB ram and plan to run ESXi hosting Ubuntu server (non GUI) and windows server 2012 (GUI), my total disk space is 3TB x 4 and will be using raid 5, a 2.5" SSD as cache and SD card with ESXi on it, share between ubuntu and windows server.

---

### Post by mastablasta on 2016-10-14
will this be Ubuntu running inside Windows server on some virtual platform?

to clarify - i am not sure why you are using two operating systems. 

othewise re:your system - i think you are good to go. unless if you plan to run some ZFS as well, then you might need more ram (again more depending on the plex server requirements).

---

### Post by ispoon on 2016-10-14
Both ubuntu and windows server on VMware ESXI 6

for windows its for testing some application
for ubuntu is for samba and plex

I am thinking of 6gb for ubuntu, 6gb for windows server and remaining 4 for ESXi host.

would that be good?

---

### Post by Vegan on 2016-10-14
> **ispoon said:**
> Hi, I have install ubuntu server before on Hp microserver 16GB ram running samba and plex. however I would like to move it to ESXi 6 now.

Would like to know how much disk space should I assign to ubuntu server (non gui) and how much ram for it, samba will be serving 2-5 max users, plex will at most 2 users.

Also wants to find out if its possible to create a virtual disk space from Esxi datastore and use it as samba share folder in Ubuntu. i.e.: create the virtual disk and mount to Ubuntu and use it as samba path. I try google but no result on this so please advise if its possible.

Thanks in advance


16 GB is not going to get very far with plex. Especially with some other workloads besides it. I recommend doubling the RAM to 32GB or even more to allow each VM enough memory to breath.

---

### Post by darkod on 2016-10-15
I have plex and samba running on HP Microserver with 4GB RAM, and it works just nice.... There should be no need to invest money in HW upgrades because your 16GB should be enough.

Your VMs should run just fine on 16GB. The 4GB you assign to vmware is even too much, the basic hypervisor works with much less I think. So you should be able to easily run ubuntu with 6GB virtual memory and the windows with 8GB.

As for your virtual HDD question, you can assign as many of them as you want to any of your VMs. The OS sees them as local disks. In ubuntu it is easy to use them on a specific mount point, for samba, or anything else...

---

### Post by ispoon on 2016-10-16
> **darkod said:**
> I have plex and samba running on HP Microserver with 4GB RAM, and it works just nice.... There should be no need to invest money in HW upgrades because your 16GB should be enough.

Your VMs should run just fine on 16GB. The 4GB you assign to vmware is even too much, the basic hypervisor works with much less I think. So you should be able to easily run ubuntu with 6GB virtual memory and the windows with 8GB.

As for your virtual HDD question, you can assign as many of them as you want to any of your VMs. The OS sees them as local disks. In ubuntu it is easy to use them on a specific mount point, for samba, or anything else...

Ok will try this. Will be upgrading the microserver processor to a Xeon one. So hope the performance will be better after I receive the processor

---

### Post by ispoon on 2016-10-16
> **Vegan said:**
> 16 GB is not going to get very far with plex. Especially with some other workloads besides it. I recommend doubling the RAM to 32GB or even more to allow each VM enough memory to breath.

This hp microserver support max ram of 16gb only :(

---

### Post by mastablasta on 2016-10-18
if they say plex requires 2 Gb for typical use then even 4 GB should be an overkill. so your plan to use 6 should be more than enough.

4GB just for wm ware is indeed too much.

---

### Post by TheFu on 2016-10-19
Samba and Plex are not memory hogs.  

Checking my plex server (tons and tons of content), Plex is using under about 700MB of RAM while streaming.  There is another plex process using about the same amount - think this is the library management - 1.5G RAM total.  My Calibre server which runs on the same system is using more RAM than all of Plex.

4G of RAM is overkill for almost any Linux server running in a home environment. My only concern is if your plex will need to transcode. Transcoding is CPU intensive and direct access to the CPU is handy for that workload.  My plex server isn't all that powerful, just a Pentium G3258. It handles many tasks and only has 8G of RAM total.  Much of that RAM is used as disk buffers.

There are geospatial DBs which need lots and lots of RAM 32GB+, but if you aren't running one of those, it is normal for a VM server to need 1G or less of RAM.  Save the RAM for Windows.

Any chance I can talk you out of ESX and push KVM instead?  I've run both of those, Xen, virtualbox, and a few others.  KVM is the fastest, most flexible, least picky about HW, and most stable out of all of them, IME.  Of course, if you want to learn ESX/ESXi for work reasons, this is a good way too, but without vSphere which every company uses, not sure you can get the same learning.  For GUI client VMs, spice is really great now too.

---

### Post by ispoon on 2016-10-22
> **TheFu said:**
> Samba and Plex are not memory hogs.  

Checking my plex server (tons and tons of content), Plex is using under about 700MB of RAM while streaming.  There is another plex process using about the same amount - think this is the library management - 1.5G RAM total.  My Calibre server which runs on the same system is using more RAM than all of Plex.

4G of RAM is overkill for almost any Linux server running in a home environment. My only concern is if your plex will need to transcode. Transcoding is CPU intensive and direct access to the CPU is handy for that workload.  My plex server isn't all that powerful, just a Pentium G3258. It handles many tasks and only has 8G of RAM total.  Much of that RAM is used as disk buffers.

There are geospatial DBs which need lots and lots of RAM 32GB+, but if you aren't running one of those, it is normal for a VM server to need 1G or less of RAM.  Save the RAM for Windows.

Any chance I can talk you out of ESX and push KVM instead?  I've run both of those, Xen, virtualbox, and a few others.  KVM is the fastest, most flexible, least picky about HW, and most stable out of all of them, IME.  Of course, if you want to learn ESX/ESXi for work reasons, this is a good way too, but without vSphere which every company uses, not sure you can get the same learning.  For GUI client VMs, spice is really great now too.

No not running any DB so don't need so much ram, just samba and plex, maybe openvpn as well, current using the Asus router's openvpn, might move it to ubuntu to host it. 

not much transcode on plex I believe, as I view the media on iPad only mostly 720p.

For ESXi am learning coz just change job (AIX system engineer previously) and doing more to esxi server installations now. Using vsphere client on my desktop to access the esxi server and cli command, too bad only have 1 microserver else can try out vmotion etc.

---

### Post by TheFu on 2016-10-22
> **ispoon said:**
> No not running any DB so don't need so much ram, just samba and plex, maybe openvpn as well, current using the Asus router's openvpn, might move it to ubuntu to host it. 

not much transcode on plex I believe, as I view the media on iPad only mostly 720p.

For ESXi am learning coz just change job (AIX system engineer previously) and doing more to esxi server installations now. Using vsphere client on my desktop to access the esxi server and cli command, too bad only have 1 microserver else can try out vmotion etc.

No need to quote everything. 

Plex is mainly a DB app, but it transcodes any media on-the-fly based on the player requirements.  Apple has specific formats they support, so I would be surprised if transcoding didn't happen all the time.  Only my Kodi machines running on x86 or R-pi don't need transcoding most of my content.  The tablet, website and chromecast all need transcoded content.  That's because my default format is h.264 + AC3/ogg audio and the chromecast doesn't have a clue how to select different audio tracks.  For my recorded TV, the audio always needs transcoding.

I worked on AIX for decades. ESXi is nowhere near as good as LPARS where a decade ago, IMHO.  vmotion isn't something special.  KVM does it too. It is only the desktop VM stuff that doesn't.  Plus ESXi is really picky about hardware.  Of my 6 physical systems, only 1 worked with ESXi. Ended up giving that box away and moving everything from ESXi and Xen to KVM in 2010 and 2011. Never regret that, since KVM is what runs openstack used by pretty much every cloud provider except Amazon and Microsoft.  But if your goal is to earn a living, then going where the money is really is the smart way.  VMware has screwed their customers a few times over the years.  One of my clients was so pissed at a price increase that we pulled all their ESX systems and replace them with KVM in just a few months. We'd just deployed ESX for them the prior year (they weren't doing any virtualization before that).

I stopped using consumer routers a few years ago. Couldn't figure out how to keep them patched for the lifetime of the HW. Even DD-WRT hasn't been maintained for my old hardware which is still working.  Switched to an x86 specific box running a BSD router distro which has a long history of updates over a decade. Keep wifi separate from the router, since those standards change all the time and the location of the router isn't ideal for wifi coverage. Using $144 router HW, GigE capable, that I expect to last 10 yrs, minimally, as an edge/WAN router.  Moved all the other routers to internal subnets so I don't have to trust them nearly as much.

Anyways, if you don't run ZFS with dedup enabled, 2G of RAM is fine for Plex even if it needs to transcode. Transcoding really hits the CPU. My prior Plex system was an AMD E-350 system which couldn't handle any transcoding of HiDef stuff.  Sometimes it is nice to watch content from home when on the road. A $150 system solved that and I just use an ssh tunnel for connectivity - to avoid the plex-account thing.  Not really interested in having another unneeded online account if it can be trivially avoided.

Sorry for babbling.

---

### Post by ispoon on 2016-10-23
Yep AIX VIO and LPARS is far better than esxi, but since after jobless for a few months and move to esxi server I have no choice but to learn more at home for now, I have free static ip from isp so I always remote back home when I outside for plex or my file share. will try out kvm soon once have explore enough of esxi at home.

my microserver is using xeon processor so should work flawlessly for plex.

---

