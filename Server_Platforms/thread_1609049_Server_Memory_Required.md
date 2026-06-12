---
title: "Server Memory Required"
date: 2010-10-29
forum: Server Platforms
---

### Post by chideock on 2010-10-29
I have many documents that indicate many different min requirements for drive memory. Will someone give me an idea for the following
Ubuntu 10.10 server running SSH and Samba what would be the memory requirements, recommended as opposed to min, for partitions as follows:
/ -- root
/home -- as a separate partition
/boot -- as a separate partition (do I really need a separate boot)
swap my RAM is 768mg so 1 gig should be good

40gig is the drive size

Thanks

---

### Post by psusi on 2010-10-29
Memory is not disk space.  For disk space, you need at least 10gb for /.  You do not need a separate /boot or /home, but some people like to have a separate /home.  With only a 40 gb disk I would suggest not having a separate /home.

---

### Post by chideock on 2010-10-29
psusi

Thanks. I know the drive is small I am experimenting more than anything else. Trying to understand how all this works. Of course with a bigger drive having /home separate would be the way I would want to go.

Sorry about my syntax for memory vs drive space. You are correct in interpreting that I was talking about drive space..

---

### Post by chideock on 2010-10-29
Just found out 10gb is not enough. I'll try again.

---

### Post by psusi on 2010-10-29
What makes you say that?  I have a fair amount of stuff installed on my desktop and am only using around 6gb in /.

---

### Post by chideock on 2010-10-29
Just runnig it again with 15GB for /  -- thelast try at 10GB failed after selecting the Samba package for install during the "select and install software" phase. I made the assumption that space was the issue. Was using 10.10 Server for that install.

Yes I know what is said about assumptions.

Anyway I am trying again. Its now install Samba. Using the 10.04.1 install this time.

---

### Post by dtfinch on 2010-10-29
My 10.04 server installs are all using between 700mb and 1.3gb on /. One is a server slice where 256mb ram and 10gb hd is all it has.

In what way is the install failing?

---

### Post by lisati on 2010-10-29
Mileage can vary depending on what you're doing. I have one machine set up as a backup for my server that I can switch in if needed. It seems to be happy with a 3Gb hard drive.

---

### Post by hantechbl on 2010-10-29
LOL my system is 2gb hdd and 170mb ram and it runs, ok, kinda.... (DoN't ReStArT It!!!!!!!!!):)

---

### Post by chideock on 2010-10-29
At this point all I can say is that several failure messages came up and the system stop functioning - froze.

I switched to the 10.04.1 server CD and it is now installed and running with 15GB in the "/" partition. As I mentioned I am experimenting with this as a learning process. I am using 2 40gig drives and RAID1 with a swap, / and /home partition.

I did have it set up with the RAID0 on the 10.10 and two partitions -- swap and /. Worked fine then once I had got by the fact that there is no need to set the "bootable flag" as all the guides and how-tos say to do.

I am busy the next couple of days but I will try the 10.10 again with 15GB in /
I will also try the 10.04.1 with less memory in /

If those have problems I will take more specific notes.

Any thoughts?

So for the moment
10.04.1 ubuntu server
i386
two 40 gig drives
768 ram
RAID1
3 partitions -- swap 1GB, / 15GB, /home rest of drive
/ and /home ext4

---

### Post by CharlesA on 2010-10-29
I don't have a seperate /home on my server, since I only use the OS drive for the OS and my VMs.

---

### Post by arnavk007 on 2010-10-30
no need for seperate /home you will end up messing everything

---

### Post by chideock on 2010-11-01
CharlesA
Would you be kind enough to give me a sample partitioning for your setup?

Thanks

arnavk007
Why would a separate /home mess things up?
Thanks

---

### Post by CharlesA on 2010-11-01
> **chideock said:**
> CharlesA
Would you be kind enough to give me a sample partitioning for your setup?

Thanks

My setup is really simple, it's just the default partitioning scheme that the Ubuntu installer uses.

All I've got one on partition for / and one partition for swap.

> arnavk007
Why would a separate /home mess things up?
Thanks

I don't know why it would mess it up, the installer does all the "hard work" for you. The only iffy part is when you do reinstalls, but always do a backup before doing major changes to yer system.

---

### Post by chideock on 2010-11-01
CharlesA

Thank you. 

With that setup would one not have issues with data and the OS all one one partition. I ask because I was looking at a samba server home setup, a simple file server and storage, where users (2 of us) data would be separate from the OS. So I was trying to separate / from /home. Is that a reasonable way to go or should I not be concerned and use the setup like you?

Thanks
Tom

---

### Post by CharlesA on 2010-11-01
> **chideock said:**
> CharlesA

Thank you. 

With that setup would one not have issues with data and the OS all one one partition. I ask because I was looking at a samba server home setup, a simple file server and storage, where users (2 of us) data would be separate from the OS. So I was trying to separate / from /home. Is that a reasonable way to go or should I not be concerned and use the setup like you?

Thanks
Tom

Well on my server, I've got another drive that has all my data, which is why I don't bother to create a separate /home.

If you are serving to two people over Samba, and don't have a load of data, it should be ok just to leave /home on the same partition, as long as you do regular backups to external media.

What I would recommend is this:

Add another drive to the machine and use that drive as a dedicated data drive for Samba, that's what I do. Makes backups a lot less complicated too.

---

### Post by chideock on 2010-11-01
CharlesA

Thanks for your thoughts.

It is an interesting setup and I may try it. I don't know how to setup the 2nd HD as a separate data disk at the moment. Do you have a suggestion what to read?

I was initially looking at a server setup with 2 HDs, albeit small ones (40gigs each), set in a RAID one with partitions as swap, / and /home. I managed that late Friday but with / set at 15gigs. 

Root set at 10gigs produced an error that the system could not load the selected kernel image.

I am just experimenting at the moment to see if I can do all this.

Tom

---

### Post by CharlesA on 2010-11-01
There are a ton of tutorials about adding another drive, but most are old.

I googled it and came up with this list of [search results]("http://www.google.com/#sclient=psy&hl=en&q=mounting+second+hard+drive+linux&aq=f&aqi=g1g-o1&aql=&oq=&gs_rfai=&pbx=1&fp=2304850557947867").

Basically you need to add the drive, format it and then add it to fstab so that it's got a static mountpoint.

Adding the drive is easy, formatting can be done with gparted if need be.

As for adding it to fstab, read [here]("https://help.ubuntu.com/community/Fstab").

---

### Post by chideock on 2010-11-01
CharlesA

Thanks for the pointers. I'll do some more reading.

Tom

---

