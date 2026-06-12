---
title: "Server/Raid/Samba/Media Streaming - Design and build"
date: 2010-09-23
forum: Server Platforms
---

### Post by Oaknut on 2010-09-23
Hi There,
 
Difficult to know where to paste this but I've gone for here and hopefully the right people will see it :P
 
The goal:
 
1. A box on the home network (wired or wireless) that I can back up machines to (the wife's Win7 laptop, my Win7/Ubuntu desktop and Ubuntu Mint Laptop) so build raid array with seperate medium for OS.
 
2. If this is going to be the backup of all these machines it seems only reasonable that it is able to stream videos/music to the PS3 etc.
 
These are the issues I have raised so far -
 
1. So i have spent the past couple of weeks trawling the Internet and the first stumbling block is Raid - Given that hardware raid card is going to be too expensive, software raid is the way to go - OK, no problem, plenty of processing power with CPU.
 
Install Operating system on a compact Flash card (or USB) and then create copy of CF card gives me resilient OS install - If I then create a raid 5 array with physical harddisks, BUT ..... where would one mount them for use by presumably Samba for the file sharing operation etc ? and would this impact any recovery proceedure if the CF card failed and had to be replaced? or even worse re-installed?
 
2. Media Streaming application - any "out of the box" Ubuntu solutions ? MediaTomb ?
 
3. A Server install ?- without a gui front end - not sure my CLI skills are leet enough :( .....So, Alternative install of the Desktop version and then use VNC to remote control the box ??? (It wont have keyboard and monitor)
 
Of course all things going well may build other services (email, dynamic DNS etc ) on top but I'll "jump off" that bridge when this is all working first!
 
All input gratefully received - many thanks in advance

---

### Post by memilanuk on 2010-09-23
I'm kind of heading the same direction, but I'm putzing about with some smaller projects first as kind 'proof of concept' before going after the serious hardware that I wish I had... ;)

>  
3. A Server install ?- without a gui front end - not sure my CLI skills are leet enough :( .....So, Alternative install of the Desktop version and then use VNC to remote control the box ??? (It wont have keyboard and monitor)


One option might be [webmin]("http://www.webmin.com")... check out the [tutorial]("http://woodel.com/") here for some info.

---

### Post by Groodles on 2010-09-23
Here's a HOWTO for Software Raid 1, but I followed it for a RAID6 array that I setup just the same.

[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)

---

### Post by memilanuk on 2010-09-23
FWIW, there are [newer versions]("http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub-configuration-debian-lenny") of that tutorial out there - for Lenny (not *quite* as ancient as Etch... ;) ) as well as some other ones specifically for Ubuntu... that site has a lot of very good info, even if they are a bit fixated on ISPConfig at times ;)

---

### Post by Oaknut on 2010-09-23
Thanks for this - I'll check them out - Before looking at the Raid Howto though. What I have no idea about is not creating the raid array as such but where I mount it so that it is used most efficiently by the system obviously bearing in mind that Samba etc. is going to be installed and should be using it.

Cheers

---

### Post by kgatan on 2010-09-24
Regarding gui,
It wont help you very much to have a gui. In the end you will find your self using the terminal in the gui anyway since alot of the configuration for these kinds of services has to be made by configs.

The gui configs that are avalible are often web based so you can config from remote, such as webmin.

CF Card
Ive also seen people not recommending cf cards for ubuntu since it uses a journaling file system which means alot of writing to os disk. CF as far as i know can only handle so many writes untill it fails.

Backup,
For windows machines id suggest using windows internal backup to a shared folder on the ubuntu.

---

### Post by cruizer8 on 2010-09-24
As far as media streaming goes, I would use MediaTomb.  It is what I am currently using to stream to my PS3 and Xbox and works really well.  There is a nice and easy to use web interface for it as well.  It was a bit of a pain to setup initially for me however.

---

