---
title: "Is this overkill for a terminal/file server, do you agree?"
date: 2010-02-01
forum: Server Platforms
---

### Post by Julian David Pitt on 2010-02-01
Hi All
I have been asked to look at the hardware required to move a business into a new building. Currently the users work from home using a broadband connection to access a remote terminal server that runs Office 2007 for a calendar and email. The business has been quoted by a company to install an IBM System x3200 M2 Server at nearly £2000, the spec of which is as follows:
Single Intel Quad-core Xeon X3320 2.5GHz Processor 
 2GB Installed RAM 
 3x 73GB 15K-rpm SAS Hard Drives Configured to RAID-5 
 (Estimated Hard Drive Storage Space 150GB’s) 
 Integrated 1000MB Network Card 
 They have also been quoted for the following:
APC 1000VA Smart-UPS  £ 265.00 
1x Linksys 16-Port 1000MB Managed Network Switch £ 119.00 
1x Vigor 2820 WiFi ADSL Router / Hardware Firewall  £ 155.00 
1x  Microsoft SBS 2008 Standard Server License £ 754.00 
Including 10x client access licenses 
1x Symantec Backup Exec for Microsoft SBS £ 195.00 Backup management software  
1x Symantec End-Point for Microsoft SBS £ 550.00 per year

I personally think this is way over the top for what would be needed to support 4 on site workers and three who need remote access to the diary and files stored on the server. Can anyone tell me if the server LTSP installation would suit this requirement and how easy is it to set up. Many thanks in advance.

---

### Post by tlsarles on 2010-02-01
I would get rid of the SAS drives, and use regular SATA. A lot more space for less money, I don't think they will require the performance of SAS. Then I would bump the RAM up to like 8gig, since it's cheap.

Other than that, I don't think it's a bad setup. You could probably go cheaper on the CPU, but it will probably delay a future upgrade, so I say keep it.

---

### Post by Julian David Pitt on 2010-02-01
Hi tlsarles
Thanks for responding my friend. I agree that SATA is a much better option capacity wise at least. I am contemplating the Karmic alternative LTSP install or perhaps using the FreeNX server and thin client mentioned on this website [COLOR="Blue"][http://www.howtoforge.com/how-to-set-up-a-terminal-server-in-linux-using-ubuntu-9.10-and-freenx]("http://www.howtoforge.com/how-to-set-up-a-terminal-server-in-linux-using-ubuntu-9.10-and-freenx")[/COLOR] Does anyone have any experience of this please?

---

### Post by BkkBonanza on 2010-02-01
You just have to consider money vs. performance. For a few local users serving files and assuming it's not for video or something else needing crazy performance I'd say this is plenty of system. Judging by the little info given you could do with a lot less. Cheaper drives is a big money saver, and even an old P4 can saturate a regular LAN connection. A Quad Core Xeon is way overkill but sure would be nice if money isn't an issue. Sounds like it is though.

Your few remote users aren't going to impact anything and certainly don't need high speed drives as they won't even notice unless they're on gigabit links (!).

I used to sell hardware and there is always a tendency to up-sell as much as the client will accept. You can't really go wrong by overselling. If the client doesn't notice the price tag they will notice the great performance. You just need to be clearer about your budget.

Regarding LTSP, that is suitable if you want to run workstations that are thin-client. ie. have no disks in them. If you're already using regular capable PCs then you don't really need to get into that. They can just use shares from the server. And they can be running Windows or Linux, or whatever, they can all access the server.

Edit - 754 quid for Windows Server! ROFL...

---

### Post by tlsarles on 2010-02-01
As far as OS, yes, you probably can run Office 07 with WINE using that NX software you we're looking at. And if your on an extreme budget, maybe you give it a shot. If a paying customer was asking me for a solution however, I would probably tell them to use a win box to host a win application like that... but I might be tempted to talk them into OpenOffice/Thunderbird or something

---

### Post by Julian David Pitt on 2010-02-01
Hi Bkkbonaza and tslarles
Thanks for the advice once again. I should point out perhaps this is for a medical business that only employs about 10 people in total, the present quote runs to over £12,000 quid at present. The other info you may appreciate Bkkbonaza, is that all the current workstations run Windows OS's which is why I thought the FreeNX windows client would be ideal. > Regarding LTSP, that is suitable if you want to run workstations that are thin-client. ie. have no disks in them. If you're already using regular capable PCs then you don't really need to get into that. They can just use shares from the server. And they can be running Windows or Linux, or whatever, they can all access the server. Forgive my ignorance but how would using just shares on the server enable access to an Office 2007 calendar and email? If you have any ideas please let me know and thanks again for the help.

---

### Post by SlugSlug on 2010-02-01
How many users is it for? 2GB is low for server RAM and 1CPU seems strange.

---

### Post by lykwydchykyn on 2010-02-01
> **Julian David Pitt said:**
> Hi Bkkbonaza and tslarles
Thanks for the advice once again. I should point out perhaps this is for a medical business that only employs about 10 people in total, the present quote runs to over £12,000 quid at present. The other info you may appreciate Bkkbonaza, is that all the current workstations run Windows OS's which is why I thought the FreeNX windows client would be ideal.  Forgive my ignorance but how would using just shares on the server enable access to an Office 2007 calendar and email? If you have any ideas please let me know and thanks again for the help.

 - Regarding the hardware:  It's not about power as much as it is redundancy and quality.  You don't want cheapo server hardware if you can avoid it.  I agree about bumping up the RAM as well.

 - Regarding LTSP: people confuse this with Windows terminal services all the time (understandably), but it's not analogous at all.  FreeNX is more comparable.  It's a little tricky to set up, but once you get it going it's worth it.  Very fast even over the internet or WAN.

 - If they WANT to use Office 2007 specifically, they are pretty much stuck with Windows -- specifically Windows server, since standard windows doesn't allow multiple concurrent logins via terminal services.  It also requires purchasing the CALs, though if you only have four users hitting this thing they're overselling you on CALs.

That's where the rubber meets the road, as we say in Tennessee.  In the end you can't just swap out Ubuntu for Windows and keep rolling, it's going to be a whole different experience from there on up.  

If they're balking at the price and are open to other options, you should prototype something using Ubuntu and some kind of [FOSS groupware](http://www.linuxlinks.com/article/20090921133533625/Groupware.html).  Let them compare the user experience and the price.

I wouldn't run Office in wine, but that's just me.  For me a solution involving WINE does not fly for mission-critical applications.

Another approach is to look at browser-based desktops, like eyeOS or Ulteo.

---

### Post by BkkBonanza on 2010-02-01
> **Julian David Pitt said:**
> Forgive my ignorance but how would using just shares on the server enable access to an Office 2007 calendar and email? If you have any ideas please let me know and thanks again for the help.

I'm not actually a user of Office calender/email. Or at least I haven't been for years. I had just assumed that with those programs the needed data files could be stored on a disk location that would be pulled from the shared resource. I don't have specific experience with this. Usually MS-Office apps keep their data in the (linux equivalent to) user home (Application Data) directory so you would have to map that location to be mounted from the server. I know Windows usually mounts shares as drive letters but they do now have some tools for symbolic links that work for Samba as well. Alternately maybe the Office products can be configured to find user data on specific drives via the registry. But just a guess on that.

---

### Post by Julian David Pitt on 2010-02-01
> **SlugSlug said:**
> How many users is it for? 2GB is low for server RAM and 1CPU seems strange.

It is for at the most 10 users. I was thinking of maybe 8gb RAM but I think a quad core processor would suffice?

---

### Post by munky99999 on 2010-02-01
sounds like massive overkill for stated uses. It also wouldnt run so well as a top server.

> Hi All
I have been asked to look at the hardware required to move a business into a new building. Currently the users work from home using a broadband connection to access a remote terminal server that runs Office 2007 for a calendar and email.
You can most likely run those apps on pretty much anything.

> Single Intel Quad-core Xeon X3320 2.5GHz Processor 
If you're jumping up to a xeon. You really should expect heavy load on the cpu. The jump from a typical say intel i7 to xeon really only gains it's performance when it's running 95% cpu or more for a year. In which case, you're better off you go dual quad xeon as the increase in cost is justified in the room to grow.
> 
2GB Installed RAM 
very low for any server at this rate. You should be looking at more like 12-64 gigs ram in any server hosting a xeon.

> 3x 73GB 15K-rpm SAS Hard Drives Configured to RAID-5 
3 drives in raid 5 is a big waste. especially at the prices of SAS. I would put SAS being worth it only when you really know you do. Database type stuff for example.

> 1x Vigor 2820 WiFi ADSL Router / Hardware Firewall £ 155.00 
That looks really expensive to me. Unnecessarily so. You could get a wireless n router for probably 30 and then dsl modem for just as cheap. No reason to combine them.
> 
1x Microsoft SBS 2008 Standard Server License £ 754.00 
You are posting on an ubuntu forum. Why not use ubuntu?
> 1x Symantec Backup Exec for Microsoft SBS £ 195.00 Backup management software
1x Symantec End-Point for Microsoft SBS £ 550.00 per year
dont need that neither with ubuntu.

---

### Post by Julian David Pitt on 2010-02-02
> **munky99999 said:**
> 
You are posting on an ubuntu forum. Why not use ubuntu?

Thanks Munky99999
I was posting to see the viability of running an Ubuntu system, in particular if a terminal server could run office 2007/2003 as that is what they currently use. A friend has suggested why use a terminal server at all, could I not just use an Exchange server for the email and calendar requirement. I agree completely about the hardware as well as the back up software. Presumably Rsync would do the job just as well?

---

### Post by lykwydchykyn on 2010-02-02
> **Julian David Pitt said:**
> Thanks Munky99999
I was posting to see the viability of running an Ubuntu system, in particular if a terminal server could run office 2007/2003 as that is what they currently use. A friend has suggested why use a terminal server at all, could I not just use an Exchange server for the email and calendar requirement. I agree completely about the hardware as well as the back up software. Presumably Rsync would do the job just as well?

rsync would work, though there are tons of backup solutions for Linux, both free and commercial.  Do you have an existing backup solution that you would need to integrate it into?

If nobody's married to exchange yet, you might want to look into an alternative like zimbra or openXchange.  Choice of an email server is the kind of decision that you get stuck with for years to come, might as well choose something free that gives you platform options.

---

### Post by Julian David Pitt on 2010-02-02
Hi lykwydchykyn
Nobody is married to exchange yet so if I can get them to go down the open source route then that would be great. It's the unfamiliarity with software that is not Microsoft that I have to contend with more than anything else really. Thanks for your opinion.

---

### Post by tlsarles on 2010-02-02
If you want to pitch exchange, I might recommend google apps for free.

google.com/a

You can host your own domain at google and get gmail/gcal. I don't see a reason to setup a mail server for 10 users. Or find hosted exchange if they really like outlook. We use app river.

---

### Post by Julian David Pitt on 2010-02-03
I will take a look at google apps as that would seem to suffice for what is needed. Does each user of the google calendar need their own google account do you know? I will also take a look at App River as well, thanks again.

---

