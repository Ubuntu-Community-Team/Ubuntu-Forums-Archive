---
title: "Running Ubuntu Server LTS adding users and setting up backup solutions"
date: 2021-11-16
forum: Server Platforms
---

### Post by rrsaldana963 on 2021-11-16
I have a home server that I assembled and installed Ubuntu Server LTS 20.04. I have been studying linux for a little while now and am trying to setup users and permissions and feel like I am doing it adequately but wanting to make sure I am doing it properly and also have a few areas that I need some assistance with clarifications.
I made several test users and created a group that they are all added too; (users1,2,3,4> group1) and changed the group of the directory on the server to that group1 that they are all added too. I changed the permissions to allow the group to read/write/execute for testing purposes. The clarification I need is when creating a user with useradd, how do I create the user without a home and not have any access to the server besides the samba share? I have found the useradd -M option for the home but I am not sure about the no-login option. I have seen that there is an -r option to make a system user but I am not 100% sure on that exactly. Are there any drawbacks on making a user with the r option for simple samba access. 

Samba is working but I am having a slight problem with a specific situation. I have a laptop that I am running Manjaro linux and it has a randomusername account but I can access the samba share using one of the accounts that I created using smbpasswd. However, I am not able to write to the directory in the share for some reason. Does the user on the machine have to be the same as the samba user or should the samba user credentials be enough to read/write to the share drive. I am using ZFS and created a Zpool with a raidz6 setup and would like to figure out what backup solutions to implement to allow for my family to backup an image of their pc's and also access data and files, some only for them (besides me having admin privileges) and have each user have a directory where they can access and write to their own directory and others have the same but not able to see or write to the other users directories. 

Thanks for your time and feedback. 
Been working hard to understand this stuff and just trying to keep learning Linux because I find it useful and beneficiary.

---

### Post by naxal on 2021-11-17
Hello,

I am no expert here, so please wait for other expert users to give you an on topic reply.

Little off topic, but I was wondering, why didn't you consider specialized backup solutions like NextCloud? Looking at your usage, NextCloud (or ownCloud) can make all these user management and access issues real easy to short out. Added benefit, NextCloud can be taken online allowing users to access the data from anywhere in the internet

Thanks.

---

### Post by MAFoElffen on 2021-11-17
Study, research and learn how to edit the options in these two files:
```

/etc/defaults/useradd
/etc/login.defs

```

The utility 'useradd' uses the option settings in these two files when it creates users...

In /etc/defaults/useradd, you can change the option for "Home=/home" to point it to a network share, where it will be easier to manage and backup.

In /etc/login.defs, confirm/change or add a line that defaults to automatically create a user's Home directory to "CREATE_HOME yes".

Either that, or you could do it manually via
```

sudo useradd -m -d /path_to/username username

```

*** EDIT ***
You want to keep data security, the administration and management of simple... Compartmentalize it by location and group (access & permissions). That just makes sense. You do not need to keep sensitive data on local machines, where that would fragment all that. 

It is not an issue of what you use to backup, as much as a methodology. Make a plan that makes sense, that streamlines your admin & time to complete, but covers what the risk is that you can accept. Keep to it simple, and consistent by automation. Test it to make sure that works... It doesn't help to have a plan, if you find out later, that it couldn't get you back to where you thought it would.

There are over 25 threads here on Backup Strategies, solutions for... And recommendations. I have my own feelings on that, but vary depending on what the infrastructure is, the business needs and what the customer accepts as risk... (What level they want to recover at any point in time, for what kinds of data.) If you are talking about financials, there is more risk that just talking about emails or funny cat videos...

---

### Post by rrsaldana963 on 2021-11-18
Thanks for the replies. I have been studying some of this material and  have read some textbooks and plenty of tutorials but I want to hopefully  get to the level of network administrator someday so am trying to make  my homelab as realistic as possible and as affordable as possible. In  the future, it would be great to have a small server rack where I can  have an epyc server with 128 gb of memory and a SAN and several other  devices but in the mean time I just have a used server I put together  with a zfs raidz storage array and 16gb of memory. It is mainly a NAS  and I have been learning how to setup samba, zfs, users/groups, and  other tasks. Still have a lot more to go but was a little frustrated  with some of the information I have read. 
The confusion I have been  having is with users, groups and samba. My family has a few windows  machines and a mac but I mainly use linux and a windows machine (for  gaming but hardly have the time and am planning on transitioning to  linux gaming on manjaro or something) and I think I have setup the basic  NAS server adequately so far but am not 100% sure on the user and  permissions setup. From my understanding, I should have a share that is  accessible by a group with all the users I want to share. I read that  samba 4 doesn't require a local user but I don't have a problem making a  useradd -M user and then giving them a smbpasswd -a and -e to add and  enable the user but do I need to give them a local password with passwd  or is just making the user without a home directory and giving them a  samba account all that is required for them to access the share that I  want with the group permission. I thought I read somewhere that if you  don't provide a local password the user is inactive or does that just  mean they can't access the server through ssh (which would be ideal)? 

Would  I create a ZFS filesystem for backups and add user directories in that  filesystem and chown each directory to be owned by the user and give 700  permissions so that they are not accessible by other users be good  enough? 
I know there are a lot of apps like nextcloud (or the other  one, forgot which one is recommended), docker, VMs, plex, and several  others that are useful and I plan on setting them up for backups and  automatic stuff like syncing phones when entering the home but I am  still learning a lot of things so I am unfortunately not able to do all  of this with the available time. 
I actually want to learn how to  setup a VM for potential solutions at work. I work in a chemistry  laboratory and analyze samples but some of the instruments and computers  are fairly old. Some run on XP and one even runs on W2000. I was hoping  I could figure out a solution where I can clone and virtualize the OS  and software and figure out how to passthrough the physical connection  with some adapters or something. The problem is the OS and software are  fairly old and use foreign connections like HPIB/GPIB, coaxial and  analog connections. 

Sorry for my rant but I find linux and  computers extremely interesting; even though I studied chemistry in  college because I was hoping to go into materials or something but eh  lol. Thank you again for your suggestions and comments and will try my  best to figure some of this stuff out.

---

### Post by naxal on 2021-11-19
Hello,

My two cents,

You have multiple requirements and you are tying to achieve too many things at once. Although I am no expert here, so you should always wait for experts to reply, but personally I would suggest to first make a clean flow chart as what exactly you wish to achieve. Leave the technical aspects aside, but as from user point a view, dot down the list of work you wish to achieve.

Once you have the list of tasks that you need to do as from user point a view, then you can start exploring the available solutions and pick the right one for you exact specific need.

For example,

1. Virtual PC need,

> I actually want to learn how to setup a VM for potential solutions at work. I work in a chemistry laboratory and analyze samples but some of the instruments and computers are fairly old. Some run on XP and one even runs on W2000. I was hoping I could figure out a solution where I can clone and virtualize the OS and software and figure out how to passthrough the physical connection with some adapters or something. The problem is the OS and software are fairly old and use foreign connections like HPIB/GPIB, coaxial and analog connections.

Here, base / host OS doesn't matter that much, rather your hypervisor selection is important for allowing these legacy device/connection pass through. VMWare / Virtual Box and such hypervisor are cross platform compatible so you can execute VM from any Windows / Linux Host OS. All of them supports converting your existing Physical OS Drive to their respective VM Disk format. You may need to do bit or trial n error to figure out which one of it is working with your different legacy setups and proceed accordingly.


> I know there are a lot of apps like nextcloud (or the other one, forgot which one is recommended), docker, VMs, plex, and several others that are useful and I plan on setting them up for backups and automatic stuff like syncing phones when entering the home but I am still learning a lot of things so I am unfortunately not able to do all of this with the available time.

I have done my internet enabled personal backup server with NextCloud and it was very easy with snap setup. Just few commands and it should be up and running. Web based control panel is offered for simple and easy to use user management. Everything else is taken care by NextCloud (permissions and such back end stuff).

Just sharing my setup process,

1. Clean installation of Ubuntu Server 20 LTS Min Setup. (On an Acer Laptop)
2. Configured Static IP (NAT IP Range of Home Router) while installing
3. Simple Default partition scheme of the installer, just increased the LVM to allocate max possible disc size (I am using 2TB 2.5 inch HDD)
4. updated the installation to latest (apt update and upgrade)
5. Installation of snap nextcloud -> sudo snap install nextcloud -> sudo nextcloud.manual-install username password (replace username without your desired username and then same with password) -> sudo nextcloud.occ config:system:set trusted_domains 1 --value=192.168.1.xx (Replace this IP with the static ip of your installation) -> sudo nextcloud.enable-https self-signed -> sudo reboot

Done.. Your nextcloud setup is running and you can access it from any PC / phone in your home network via that static IP address via any browser. Just log in and create users.

You can do a trial run in a VM too, to test it out.

Thanks.

---

### Post by MAFoElffen on 2021-11-19
As I was reading your post #5, I was thinking some of the same things that naxal mentioned in his past #6... Years ago, I had a large server rack at home with 14 Servers, 7 workstations, and 2 Laptops. Most of that hardware is in storage now.

Each server ended up costing me about $10 each a month in power. I found that I could do the same by downsizing and consolidating my resources to VM Hosts. First I had downsized to 4 VM Hosts, then 2, now 1. I can run different systems via multi-boots, and/or running nested hypervisors as guests.

I now do no have additional costs for cabling and KVM switches. The space savings alone... LOL

Some things I still run on hardware/metal. Things that require VFIO and/or IOMMU.

---

### Post by rrsaldana963 on 2021-11-19
Thanks for the feedback. I have been trying to write and organize what I  want to do and that has been helping without setting out an outline.  You were right about the permissions with the group and writing so I was  able to get that fixed. I hopefully will be able to setup the virtual  machine and some of the other stuff like docker and what not on a test  computer I have. I don't really have to worry too much about cost of  power at the moment as it is included with rent but I also generally try  to be conscientious of power usage in general. I might be able to get a  supermicro M11-SDV 8C (not sure about the 16T) and 32 GB of memory as a  VM home lab setup for testing and learning things but it is pricey for  my current budget but worth it I think if I can find an entry level job.

---

### Post by MAFoElffen on 2021-11-20
I like SuperMicro Boards. That just happens to be what I have for my VM Host/Gaming PC. 

I've spent most my life as an IT Consultant. At this point in time... Look for something that is adaptable and upgradable, that is going to grow with what you want to do. I would say, something that is going to be between 32TB to 128GB memory. Something that can host a few things. That doesn't mean you have to start out with a lot. That means you can start out with 16GN of Ram, but have the option to grow to something higher. 

On storage, SATA III and USB3.x. But maybe also some options for NVMe. My VM Host has 6 6Gib/S SATA ports and USB 3 connected to USB 3.x Dock Bays (Hotswap). Even before those USB drive bays, I can store a lot of VM's on 4x4TB drives, and my 2TB system Drive. My 6th is a BlueRay Drive which I rip Blureay's and DVD's for my media server. But it is 12 years old. Is in a large tower. Which that server board, is noisy when it starts and slow to boot (because of all the server hardware management checks).

My VM Host of choice is KVM. I have supported many VM Hosts- KVM, RHEL, iVirt, Hyper-V, XenServer/Citrix, VMware vSphere/ESXi, and others. I can now do anything I want with a KVM Host, and nest VM Hosts from there. Anything I want to do in virtual networking, I can do within that system. Honestly, I do still beta test vSphere, which I do from my USB3.1 drive dock, and boot from it when I do.

I am in the process of replacing that VM Host with something else now. Based on lessons learned and redefining what works and what I really need. This new VM Host is in a Micro AT case. 128GB Max Ram. Can start out with 'any' 10th Gen Intel processor. Has two NVme slots and 6x6GB/s Sata III, with one eSATA... and 8 USB3.1's... and 4 USB2.0 ports. A whole lot less space. Uses less power, a lot less quieter, and is expandable.

---

### Post by rrsaldana963 on 2021-11-20
Thanks for the feedback. I built my NAS with a used supermicro board  with an xeon processor (X9SCM-F, Xeon E3-1220 V2) and 16 GB of memory  and I have it in a fractal node 804 and 6x 4TB hard drives. It was what I  could afford at the time and it is doing a great job at that. I have  saved up some money and was considering getting a Supermicro MBD-M11-SDV  8C (not sure about the 16 thread one as it cost another 150 more) and  2x 32GB sticks of ECC memory. This would be for learning and seeing what  cool stuff I could do with it. I like the mini ITX form factor as it is  doable with my current budget but would like to get a small server rack  that would be able to house stuff as I got better at it. If there are  better options than what was listed for around the same price point or  less ($800 would be max) I would be very interesting. I am enjoying  learning linux and server stuff and I don't mind spending the money on  this as I feel like I use this stuff more than my gaming machine lol. 

Thanks for the feedback everyone, very appreciated.

---

### Post by MAFoElffen on 2021-11-21
Then maybe you should Private Message me... 

I volunteer for a non-profit Computer Recycler. I think he still has an HP HPC Blade server with at least 6 Xeon Blades in it (so is not full yet) that you might be interested in. I get nothing from it... But you might be interested in it. It seems to possibly be a fit and good investment for you. Fairly recent hardware, that I know works well with anything.

I think it is about 4U or 5U, but is about 3 hundred pounds with the blades that are in it. So would need a hydraulic table to get it into a sever rack. Would be more than you would need for anything. Depending on your location, it would be the shipping costs that might be a stickler to that. I could put you two in contact and introduce you to the owner. Always like to see good hardware go to good use.

---

