---
title: "Help with partitioning 64 bit Ubuntu Server 12.04 hard drive?"
date: 2012-08-08
forum: Server Platforms
---

### Post by SunBeam on 2012-08-08
Hello,
Although I am very familiar with partitioning regular desktop installations, using separate partitions for swap, root, and home... plus multi-boot machines where some partitions need to be extended partitions, I have never partitioned a hard drive for a server.

I want to give this my best shot up front, as it's something worth doing right up front... I am in no mood to go through the hassles of making a mistake that I notice in 3 months!

So... for a small home business server with a 2TB hard drive, I want my end result to function as:

[LIST=1]
[*]Print server
[*]File server
[*]Multi-media server
[*]Potential cloud features down the line
[*]Remote access down the road
[/LIST]
I am not sure how to partition the hard drive for:

[LIST]
[*]Handling these chores today and expansion in the future
[*]Safety (separate directories for tmp, others?)
[*]Reasonable learning curve for a moderately experienced builder.
[/LIST]
I want to use Ubuntu 64 bit server 12.04. Long term service requires wise planning! :)

But am not sure of a partitioning scheme  that I am capable of achieving today, but flexible to grow into tomorrow, while providing safety throughout.

Any AND all help / advice is greatly appreciated!

Thank you,
Clinton

---

### Post by LHammonds on 2012-08-09
You're in luck.  I was in the same boat as you when I first started messing with Linux.  I am well-versed in handling Windows servers/desktops but needed re-education when it came to Linux.

The 2 biggest reasons to "separate" the various folders are for security and removing the threat of the root volume filling up (that is a BAD thing to happen on any server) but easily avoided if you push things off of the root partition into their own.

Take a look at my sig below for a link to how I setup my Ubuntu servers.

LHammonds

---

### Post by SunBeam on 2012-08-15
> **LHammonds said:**
> You're in luck.  I was in the same boat as you when I first started messing with Linux.  I am well-versed in handling Windows servers/desktops but needed re-education when it came to Linux.

The 2 biggest reasons to "separate" the various folders are for security and removing the threat of the root volume filling up (that is a BAD thing to happen on any server) but easily avoided if you push things off of the root partition into their own.

Take a look at my sig below for a link to how I setup my Ubuntu servers. LHammonds
Thank you very much for the quick response AND the link. I posted this then got swamped with some unexpected issues and also had out of the area family visiting. Now I can and will give this the attention it deserves.

I appreciate the incredible detail provided.  It does seems to be on the complex side of setups... and I'm wondering:

[LIST]
[*] Is the time/effort to create this many partitions and this type of setup a wise choice when starting out?
[*] Would a simpler setup (less partitions) significantly reduce the learning and time curves?
[*] Or is the marginal time increase and skills required very low to set up a server with this level of detail?
[/LIST]
   Maybe I am just a bit intimidated by the number of lines of instructions... but would appreciate your thoughts. 

I mean... if the amount of learning is the same for a 5 partition set up as it is for the full-blown version... and the primary difference is repetition, then it would make sense to *not* try to cut this method back.

Your thoughts/opinions please!

I *do* appreciate it LHammonds!

Thanks again,
Clinton

---

### Post by SunBeam on 2012-08-16
> **LHammonds said:**
> You're in luck...  Take a look at my sig below for a link to how I setup my Ubuntu servers. LHammonds
So how do I register for your LHammonds site so I may ask questions directly?

I do not see a place to register.

Thank you.
Clinton

---

### Post by LHammonds on 2012-08-16
My forum is not open to the public...mainly because of spam ** insert explicative **

It "looks" complex but it is really simple.  It is only long because I documented it click-for-click.

Regardless if you have everything in one partition, two or ten, you will want to be very familiar with the procedure to add space.  This is another point in the way I documented it.  Later on when I need to increase space and forgot everything, I know it is documented (tested/verified) in my thread.

When I create a new server, I typically just write down the partitions and their sizes since it is easy to reference a few lines rather than trying to keep position in the install thread.  It is repetitive and once done a few times, you won't need to look at the install steps very closely.

But through trial and error, this is the partition layout I use on all servers regardless of what is installed.  It makes for a very flexible setup.

Send me a PM if you'd like to get my attention faster...I am in the middle of a massive rollout at the moment and do not visit here as often as before.

LHammonds

---

### Post by SunBeam on 2012-08-16
> **LHammonds said:**
> My forum is not open to the public...mainly because of spam ** insert explicative **
Understood. Glad you checked in here today (the Ubuntu forum!)

> **LHammonds said:**
> It "looks" complex but it is really simple.  It is only long because I documented it click-for-click. 
for which I am grateful

> **LHammonds said:**
> Regardless if you have everything in one partition, two or ten, you will want to be very familiar with the procedure to add space. 
Yep... I agree

> **LHammonds said:**
> It is repetitive and once done a few times, you won't need to look at the install steps very closely. 
haha... one of my quotes when teaching people new things is "*repetition is a good thing*" when learning... and here you made me chuckle as it's time to take some of this medicine!

> **LHammonds said:**
> this is the partition layout I use on all servers regardless of what is installed... It makes for a very flexible setup. 
Score! (as in perfect. :)

> **LHammonds said:**
> Send me a PM if you'd like to get my attention faster...I am in the middle of a massive rollout at the moment 
Understood and thank you very much for your offer.

---

### Post by SunBeam on 2012-08-24
Hello again,
Sorry for the time delay, guess was getting comfortable with other issues and things before moving on.

Two main questions now regarding partitions and using  Logical Volume Manager (LVM) to resize.

[LIST]
[*]All my file server storage data is on /srv/samba/share. How do I resize this share to make it larger?
[*]If I decide to add functionality to the server (e.g. print server, multimedia server, etc...) and I am warned there is not enough space,  how do I increase related partitions to allow expansion?
[/LIST]
Thank you... I ***really*** do appreciate getting this far and all that has been taught. It's a great feeling to learn from experienced people!

Clinton

---

### Post by LHammonds on 2012-08-24
I have those questions answered in the thread in my sig.

To give more space to the /srv partition, you must add space to the LVM if there is none in reserve.  You do this by adding another drive, config it as physical volume, add to LVM, increase size of LV (SRV) and then increase the srv file system.

All these commands are covered in the "Volume Management / Disk" section.

if you have space in the LVM, you just need to increase the srv LV and then the file system.

LHammonds

---

### Post by SunBeam on 2012-08-24
**Couple more items:**

[LIST]
[*] This server will be central file server for mainly debian/ubuntu/mint and Windows files.
[*] Have set up SAMBA to store files.
[/LIST]
 **Folder Naming Convention Questions**: 

[LIST]
[*]Does all file server data get stored in in /srv/samba/share ? or another way to describe this, will there be any instances where data will get stored **outside** of te samba share(s)?
[*]Does anybody have useful hints for naming and setting up the folder system of ./share so I avoid future headaches?
[/LIST]
I am wondering about shared folder security.

[LIST]
[*]At the moment, I am just operating within my LAN and have no outside ports open.
[*]In the future, I'd  like to have a 'guest' section that is open to anybody on my LAN, but have my private folders/contents with no read or write capacity.
[*]Down the road further, I'd like for myself to be able to tunnel through and access my LAN from outside the LAN.
[/LIST]
Specific folder permission examples:
So below are two main folder divisions on my /srv partition. The /srv/files folder was a folder created before I activated samba, just testing and messing around. It's pretty wide open for 'root'. However... this data from what I can tell should be moved to the samba share and permissions modified.
This is where I want to clarifiy. **What are ideal / reasonable permission settings for the /srv/samba/share folders?** (See below for more details/criteria)

[FONT=Courier New][I]username@servername:/srv/files$ ls -ld /srv/files
drwxrwxrwx 29 root root 4096 Aug 21 11:32 /srv/files[/I][/FONT]

[FONT=Courier New][I]username@servername:/srv/samba/share$ ls -ld /srv/samba/share
drwxr-xr-x 5 nobody nogroup 4096 Aug 20 16:20 /srv/samba/share[/I][/FONT]

I understand this will happen one item at a time, but any help is welcome.

THANK YOU! 
Clinton

---

