---
title: "Server 12.01 misc setup questions"
date: 2012-12-16
forum: Server Platforms
---

### Post by rudestar on 2012-12-16
Hi Folks
     
     
     We are a small non-profit and we are getting kicked off the     building's network in two days. We have a duo core Dell with 4GB  ram.     It has two internal drives (160GB) that I'd like to RAID 1 for the     system, then an external box with two 1T drives. The caddy will RAID  1 the drives (via a switch) and the box connects via USB until I can  find a eSATA PCI card that works with Linux. I've downloaded Ubuntu  Server 12 and will install VNC and some Gnome elements

We want to go with Linux because it seems like the long term solution,  and I have been reading reading reading (what's with 'foo'?) and though  I've used Gnome, I've never used Linux to this depth.

All this machine will do is serve files to about 6 users, three Macs,  one Win XP and one Win 7 from the external drive. And it will back  itself up to another machine we have lying around (will also be set up  with Linux)

Here's what I am up against as far as fuzzy items:

Partition: The drives are large for just a system, I know but it's all  we have. Once set up, I'd like to save how Linux is configured, so I  think I want /home to be on it's own partition, if I am correct that if I  wipe and re-install the partition with / and I think I'll be back up  and running. Yes? It will read all the configurations from /home?
So I -think- 3 primary partitions, root, home, swap, then the rest  extended to be partitioned for future who knows what. Though it's no  clear, why not 1 primary for root, the the rest and extended partition  divided into logical partitions. Lost on that  one.

Format external drive: I'm getting mixed messages on this, one setup  says I -have- to format with FAT if I want Win users to connect, another  setup says use ext4. And use, er, Gpart?

Users- sharing files... I finally figured out that I'm not sharing with  users with local logins, but I think I DO give them logins, then install  Samba and generate Samba users from the list of local users. Even  though an admin user will be the only person who actually logs in to  work on this machine. 

And since different people will have access to different folders, I think I -don't- want to use the force user=

Sharing: Webmin to set up Samba, or use NFS? I'm open to suggestions. We  don't need speed just needs to be -super- easy for the users to  connect. 

Permissions: there will be three top folders. Shared (accessed by all  six but by password), Operations (two people have access)  Finance (two  people have access, one of them is a person who has access to  operations. Okay I am pretty sure when you add someone to a group, you  don't move them from the group they are in. I guess I am asking, a  person can belong to multiple groups, right? Also, can a group be an  owner? Also do I only set permissions for the top folder? or do I need  to CHOWN sub-folders. I understand I need a mask for files created by  users inside those folders to be accessible to others.

Took a basic Linux class years ago, fairly comfortable with line  command, familiar with Macs and some terminal. Small things with  something called dos.

     A lot, I know. Any thoughts you can throw my way will likely be put to use.  Thanks!

-Rudy

---

### Post by chadk5utc on 2012-12-16
One of the forums admins will likely move this to the Server sub forum where it will get more attention. 
 
 Theres a wealth of information here and Ill try to point you in the right direction to at least get you started. Links to a couple good guides
This one will also help with VPN and SSH
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)  
This one for User/Group management 
[https://help.ubuntu.com/8.04/serverguide/user-management.html](https://help.ubuntu.com/8.04/serverguide/user-management.html)
And a good server guide
[https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

---

### Post by rudestar on 2012-12-16
Thanks Chad, I wasn't sure. I'll check the links in the morning.  Should I delete and repost in Server?-R

---

### Post by Cheesemill on 2012-12-16
Hi rudestar, welcome to the forums.

First of all did you mean Ubuntu Server 12.10? There's no such thing is 12.01.

If you did then my first piece of advice would be don't use it. As 12.10 is a normal Ubuntu release it is only supported for 18 months meaning that you would have to upgrade to the next version before April 2014 (it seems a long way away now but believe me, it will be here before you know it). Instead I would recommend using 12.04 as it is an LTS (**L**ong **T**erm **S**upport) release. This means it gets 5 years of support so you won't have to upgrade your server until April 2017.

Usually on a server there isn't a graphical interface at all, instead you configure the system by editing text files. If you aren't very confident using the command line to do all of your administration then you should take a look at using something like [Zentyal]("http://www.zentyal.org/"). This is basically Ubuntu Server 12.04 but with a web interface so you can log on to the server from a browser and just point and click your way through administrating the system. Zentyal provides a huge range of features (far more than you will ever need) but you can choose to just install the file-sharing modules if you wish.

If your server is only going to be used for file-sharing and nothing else then I might be tempted to go for an even easier option. This would be to skip Ubuntu Server altogether and instead use [NAS4Free]("http://www.nas4free.org/") (used to be called FreeNAS). This is an OS that has been designed from the ground-up for one purpose only, file-sharing. The advantage of this approach is that NAS4Free can be installed in minutes, usually on a USB stick, leaving your hard drives just for storing data. It also uses the ZFS filesystem which is the most robust and reliable filesystem going.

I would highly recomend giving NAS4Free a look first, as it is by far the quickest and easiest option to set up and administrate.

---

### Post by Sef on 2012-12-16
Moved to Server Platforms.

---

### Post by rudestar on 2012-12-16
Cheesemill it's a lame as this, I couldn't find the 32 bit version for download. Thank you so much for the brilliant suggestion, I'm going to take that route. That at least will give me some breathing room and it just might turn out to be our long term solution.

-R

---

### Post by Cheesemill on 2012-12-16
All of the Ubuntu releases can be found for download here:

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

