---
title: "Are My Server Objective Plausible?"
date: 2015-05-06
forum: Server Platforms
---

### Post by Todd_Danko on 2015-05-06
Hello,

I'm new to both Forums and Ubuntu.

I've installed Ubuntu Desktop 14.04 and have been loving it. I also am looking to take my home network to the next level.

I have a dedicated box that I would like to use to run a Ubuntu Server.  Specs Are Core i5 CPU, 16gb Ram 256GB SSD, 2 x WD Red 3TB HD (For NAS). I have purchased the book "[The Official Ubuntu Server Book]("https://www.amazon.com/gp/product/0133017532/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1")" to help learn and understand the basic concept of setting up my Server, but I would like to see if my objectives are plausible. 

Here is what I would like to accomplish with this server.

-Set up a domain that approximately 10 devices can log into anywhere they have internet and have access to the NAS. Hopefully directly from the login screen. I do not have a dedicated IP but my Dlink Router supports DDNS. 
-Set up NAS In Raid 0 on the server. 
-Connect Android, Windows, And Ubuntu devices (approximately 6)

These are my main objectives. Is this plausible? Will I need t purchase more equipment to do this? Are there other books or tutorials that you could recommend. 

Any suggestions would be greatly accepted.

---

### Post by papibe on 2015-05-06
Hi Todd_Danko. Welcome to the forum ):P

Overall, all possible.

Another thoughts:
> **Todd_Danko said:**
> Specs Are Core i5 CPU, 16gb Ram 256GB SSD, 2 x WD Red 3TB HD (For NAS).
Hardware seems more than ehough.
> **Todd_Danko said:**
> -Set up a domain that approximately 10 devices can log into anywhere they have internet and have access to the NAS. Hopefully directly from the login screen. I do not have a dedicated IP but my Dlink Router supports DDNS.
[Here]("http://ubuntuforums.org/showthread.php?t=2257106&p=13188842#post13188842") are some tips for that.
> **Todd_Danko said:**
> -Set up NAS In Raid 0 on the server.
I'd recommend keeping the OS on the SSD, and creating a raid for the other disks. Here's a useful tutorial: [Software RAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID").
> **Todd_Danko said:**
> -Connect Android, Windows, And Ubuntu devices (approximately 6)
It depends what you want to do, but sharing files using samba may be worth looking at: [Samba tutorials]("https://help.ubuntu.com/community/Samba").
> **Todd_Danko said:**
> Are there other books or tutorials that you could recommend. 
Things move/change pretty fast so I'd recommend visiting these sites often for latest tips:
[LIST]
[*][https://help.ubuntu.com/](https://help.ubuntu.com/)
[*][http://ubuntuforums.org/](http://ubuntuforums.org/)
[*][http://askubuntu.com/](http://askubuntu.com/)
[/LIST]
Lastly, here are other 'cool' and 'entertaining' ideas for a home server (see posts #3 and #4): [A Server for What?]("http://ubuntuforums.org/showthread.php?t=2181417")

Hope it helps. Let us know if you have more questions.
Come here often and have fun.
Regards.

---

### Post by Todd_Danko on 2015-05-07
Thanks Papibe!! The hdds and books should be here on Friday and I intend to start the project this weekend. I'm sure I will have questions and difficulties but I look forward to the challenge. &#55357;&#56832;

---

### Post by mastablasta on 2015-05-07
> **Todd_Danko said:**
> 
-Set up NAS In Raid 0 on the server. 
.

why raid 0? one disk goes and you lose everything?!? what is the point of RAID then?

usually raid 0 is used if you had let's say 1TB disk and wanted to add say a 500 GB disk you found to it to make look like you have it 1.5 TB disk to clients.

also SSD for -> make sure you place swap on your HDD or reduce/remove swapiness.

your server specs are indeed kind of an overkill, but I guess you have the money for it, so why not treat yourself then :)

---

### Post by TheFu on 2015-05-07
sftp is for remote file access. You get it for free with ssh.  ssh is amazing and can do/support many things that most people without a Unix background do not consider possible. [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)  There are sftp clients for every network OS. Be certain to use ssh-keys, not passwords.

Don't use samba for external file access - ever. That is a good way to be hacked.

That box is tremendous overkill for a simple file sharing server.  I hope you plan to do much, much, much, much more with it.  It can easily do the file sharing and run 10+ virtual machines doing all sorts of interesting things - VoIP, blogs, local calendaring, email, DLNA servers, vpn, video transcoding .... just off the top of my head. There are hundreds, thousands of other things it can do - especially if you get into scripting.

For a home environment, RAID-anything is generally overkill.  RAID0 is a great way to loose data. RAID is for HA, not for backups. It brings all sorts of complexities. Just search these forums for people looking for help to get their RAID data back.  Backups are still required - hopefully, versioned backups.  Either use HW-RAID from a reputable vendor - expect to spend $300+ for this or use Linux Software RAID. Avoid Fake-RAID that comes with many motherboards. It has the same issues that HW RAID provides, but not the performance or flexibility that SW RAID provides.  It would be better NOT to use RAID at all.  If you want to span a file system across multiple disks, there are about 10 better ways than RAID0.

I only reason I know for RAID0 is to get performance improvements while working on temporary files. Think video editing for extremely large files, since most video editors switched to SSDs years ago.  A few SSDs in RAID0 would be great - provided the daily work was pushed elsewhere and backed up.  I've been burned (i.e. data lost) by RAID0 and using LVM to span storage across multiple partitions and multiple drives. That was before I got backup religion.

The idea of a "domain" is from Windows. Linux systems use the subnet as "a domain."  For sharing storage inside a Linux/Unix subnet, NFS is the best method by far. It is faster than other alternatives and if you use Kerberos, highly secure.  If you want to have shared account information across linux systems, use ldap and kerberos. Getting this working is non-trivial. 
In the old days, I'd setup NIS to have centralized host, group, userid management. Sadly it had many security flaws and has not been replaced effectively on Ubuntu/Debian systems.  Solaris has NIS+ and RHEL has FreeIPA. There are clients for Ubuntu, but no servers. ;(  There was a thread here for setting up LDAP+Kerberos where someone took careful notes. Haven't tried it - we use a central LDAP server here already.

I can't say anything about that book - but directed learning from the beginning is smart. Googling for answers can be highly dangerous for noobs. Becoming a system administrator before becoming a power user might not be the best idea, I hope you can make it work.  [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) is my best ideas for learning Linux beyond the point-n-click user, in order.

Be certain to learn file and directory permissions - this is the core of Unix system security.

This will be hard and fun!

---

### Post by MAFoElffen on 2015-05-07
Raid is not a substitue for a backup... but that being said... If system of on one segment and the data he is sharing is in RAIDX, then if the SAystem volume goes down, you just restore the system and mount the data. No loss of data (different volume container). If one of the mirror data volumes goes down, then one of the mirrors is still there...

The bug in the ointment to that is that if one side of the mirror only "partially" goes down, then the errors are mirrored to both sides. (Reiterating the need to keep up on your backups.)

So the comment on if the system volume goes down... The priority/importance to the user is the data-- the collection of media files. A/The system volume can always be recreated and/or restored. A collection of data is harder to recreate from scratch. Can you follow where that logic goes?

Ideal would be mirrored system and an extendable volume (especially for a collection that may grow in time), with backups and a fall-back plan... but when you have a budget, you have to figure out where your priorities lie. His priority is not on uptime, but protecting the accessible data collection...

My recommendation would be to look to the future and decide if a collection would ever need to be extended for growth.

On another noted... I understand the 'buzz' from time-to-time on this is the latest buzzword for what this concept really is. Problem is I'm feeling old. So someone enlighten me over what I agree with another comment made-- NAS vs. the basic concepts of file sharing. What does a "NAS" levered service give over SMB or NFS services? Isn't it just another layer providing hooks to those file sharing services?

---

### Post by mastablasta on 2015-05-08
NAS is meant as storage on network with no monitor or something like that attached to it. think of it as your own personal cloud, dropbox. while SMB is mostly used to share among desktop PC's. I think protocols, security and such is differently set up and that might be the main difference.

---

