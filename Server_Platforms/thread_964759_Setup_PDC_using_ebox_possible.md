---
title: "Setup PDC using ebox possible?"
date: 2008-10-31
forum: Server Platforms
---

### Post by tankduck on 2008-10-31
Hey guys, 
wanted to post this on here before I post it on ebox as I imagine there are plenty of ebox users on here using ubuntu and if not plenty of people that know how to setup PDC's on ubuntu.

Ok, so as my post suggests I want to setup a pdc on my ubuntu server, this seems like the right way to go as a few of us use more than one machine ie laptops, pdas...etc. I have been playing with ubuntu server 8.04 lts for about a week now and ebox for nearly as long and for the past few days have been trying to setup a pdc, but to know luck whatsoever.
The modules that I see in ebox that i would use are the file sharing one and the DNS one (correct me on the latter, I just assumed that domain name server had something to do with the setup) 
Eitherway, the file sharing general settings gives me the option of pdc or file sharing so I selected pdc obviously, and added the domain name and such, then added users under file sharing.
Then I tried to connect using a vista machine with no luck, am I totally doing this wrong? I've been reading articles about using samba as a pdc but they don't include ebox so I didn't know if ebox manages all the config files or not?

Now for a stupid question, a few of our machines are high end rendering machines, is adding them to a domain going to slow anything down? At the moment everything for the computers is on their own hdd, with work being saved to nas drives, I didn't know whether pdc's located all the user files on the server making the fast hdd's and raid etc pointless.

Sorry if these are stupid questions:(

---

### Post by tankduck on 2008-11-01
right, i have managed to get my test pc to log on to the server fine, but before I go ahead and start making changes to all the other workstations I just wanted to know what the general idea with user files is when connecting to domains, more importantly with windows vista. The user files seem to still be located on the local hard disk, I assumed that the whole idea of the domain server method of doing things was that I could use any workstation I wanted and everything would be how it is on another machine? Up until now the workstations have had a hdd for windows/applications, and then a drive for user data folders such as documents/pictures/favourites...etc. Is this still the way to do things when using domains, ie create a "user" folder on the second hdd and manually move all the folders into this whenever a new domain user account is added to a machine? Or is there a smoother way to do things. As I mentionned earlier I don't want everything to slow down because files are being located remotely but it would be nice to maybe work on the local user files on the 2nd hdd which are synced somewhere on the server.

Cheers again guys!!

---

### Post by bab1 on 2008-11-01
I'm interested in your eBox experience.

It might help if you think of the DC part of ebox as a centralized method of controlling access to the network.  The eBox DC (PDC is a windows NT thing) does not have to be a filesever (but it sure can be).  If you have a high load when serving files you can add a second machine to act as file server only.

Where data files are stored is a matter of system design.  The fat client does all the processing of the data.  Data storage in a centralized place makes it easy to control user access and to backup.  You can use a distributed file system to achieve this  The user does not even need to know about it.  You could have all home directories mounted to the file server, thus making the data available and synchronized  to the user on whatever host they log into. 

The 2 basic ways that I know of are DFS (Windows) and NFS (UNIX/Linux).  There may be more, but I am not familiar with them.  

Samba is a suite of services.  The file sharing aspect is not really a distributed file system.  More like a method of accessing files on a SMB system (Windows). You can add shares at the file server and each device that is used to login to the has access to the shares but it is not automatic and synchronized, nor is transparent.

Hope this helps.

---

### Post by tankduck on 2008-11-01
cheers bab, that gives me alot to think about. So basically the user folders when using a domain are no different at all than the user folders when using a workgroup? Basically so you understand the actual goal of what I'm doing, there isn't one user our system that has one machine, everyone has a desktop and a laptop and some have pda's and bla bla bla. The actual work side of things has almost nothing to do with this problem, as we all map samba shares of the folders that we use so nothing is actually saved locally. However, as everyone takes their laptops and pdas home with them, they have music, photos and personal work/files and we wanted a way that these would magically be exactly the same when you use your desktop. So far I've just installed the tech preview of live mesh, which seems to work a treat, but I just assumed there would be an easier way. We have plenty of hard disk space on the server plus additional space is pretty cheap at the moment so I wanted to give everyone enough space (100gb each?) to sync/backup their stuff in the background.

---

### Post by bab1 on 2008-11-01
> So basically the user folders when using a domain are no different at all than the user folders when using a workgroup?   Yes.  Domains are for access administration.  Workgroups are a Windows contrivance to allow browsing of "shares".

> I just assumed there would be an easier way.   Easier for who? :)  The technology is available to do what ever you want.  It may be hard to install and configure and easy to use or easy to install and convoluted and clumsy to use.

---

### Post by tankduck on 2008-11-01
What would you suggest as the best solution given what I want to achieve? I guess as there are not a huge number of machines I could just create a share for everyone that wants to do this that is private to them and then use the sync center thing in vista (no idea how good this is, or not) to sync their local data with the server version. I guess this is a bit of a bodge approach though...hmmmm

---

### Post by bab1 on 2008-11-01
> What would you suggest as the best solution given what I want to achieve?  Well, that *is* the question, isn't it?  There are political as well as technological questions.  Right?  This is a work environment; do you own the business or have the owners blessing?  I'm old school and tend to want to control the networks I maintain.  Peer to peer is not in my vocabulary.  That being said, why do you want to have individual "shares"?

I have Samba running at home with a large public share.  The folders all have the sticky bit set.  This allows all users to view and copy files, but only the owner can delete them.  You can add ACL's for even finer control.  Such as read permission for specific users only.

I try to think of routine that is the most natural from the users point of view and implement a technology solution to facilitate that.  In other words "easy for the user" is how I see it.

I'm not familiar with "live mesh" so I have no opinion of it.    It looks like you have to install agents on it to sync the folders.  Pretty convoluted.  I would rather have a centralized file structure for the data.

---

### Post by tankduck on 2008-11-01
basically we're a small architectural practice, run by me and my dad, with 3 other employees in the office, and the studio for the practice is on our land so we basically run the business internet connection into the house rather than use another internet connection granted its used at totally different hours to the business. I felt it would be really beneficial to be able to log onto the work server from computers in the house for business files and be able to have my personal music, pictures ...etc on my work machines in the office when I'm working lates. Like yourself, I'd much rather have everything centralized rather than rely on third party apps running in the background. And also, like you said I want to be in total control of the network, and I know usually having personal data on the business server would seem odd but its a friendly environment and one of the other guys asked if we could do the same thing for him already so we'll see how that works out.

I think the main reason I want to do this though is I hate having totally different content on my machines, I don't know if thats a weird thing to say but I want the same environment whichever machine I'm using.

---

### Post by bab1 on 2008-11-01
> **tankduck said:**
> basically we're a small architectural practice, run by me and my dad, with 3 other employees in the office...  Well that solves the problem of asking the boss "can I do this?"

> I felt it would be really beneficial to be able to log onto the work server from computers in the house for business files and be able to have my personal music, pictures ...etc on my work machines in the office when I'm working late.

I agree.  The DC and file structure just needs to accommodate you and the security of your business interests.  Some thoughts to consider: Disk quotas for users, ACL's for file security.  Good engineering would dictate placing all of the "personal music, pictures ...etc" on a separate partition.  You can set disk quotas only on a partition, not folders.  As the sys admin you must protect the stability of your network.  Sometimes unintended stpidity breaks out. Just imagine how big the entire Stanley Kubrick film collection would be.  You know, the one your not so enlightened employee decided he would store on you system. 

> I know usually having personal data on the business server would seem odd but its a friendly environment and one of the other guys asked if we could do the same thing for him already so we'll see how that works out.

See above thoughts.  :-(

> I think the main reason I want to do this though is I hate having totally different content on my machines, I don't know if thats a weird thing to say but I want the same environment whichever machine I'm using.

This is not unreasonable, but it comes with responsibility and possibly unintended consequences.  Also see above.

Unfortunately, as the sys admin, you also have to be the "network parent".  You have to look into the future and see danger.  yes, it can make you paranoid.  :D
 
I have a /smb partition on my server for just the above reasons.  I can restrict users to a set total amount of data on the partition and restrict access on a per file/per user basis.

I like the orderliness.  The /smb partition can be on a separate hard drive or raid controller.  I can easily add storage capacity when I need to.

---

### Post by tankduck on 2008-11-02
I think I'm onto a solution that isn't as flimsy as the idea of a sync tool, even though it still kind of uses one. Basically most of the machines on the network are vista, actually they are all vista, except one ubuntu laptop. Anywho, by using folder redirection in vista as documented here [http://technet.microsoft.com/en-us/library/cc766489.aspx]("http://technet.microsoft.com/en-us/library/cc766489.aspx") I can actually move the user folder that I've been mentionning to a private user location on the server, then you can choose to make the user folders available offline to the chosen location on the local hdd so it basically syncs everything from the server rather than the other way around. 
Any opinions on this method? 
Now I just need to either do this manually on every machine that wants to do this or create a login script (which I have no idea about :( )

---

### Post by bab1 on 2008-11-03
Sorry for the late post.  > so it basically syncs everything from the server rather than the other way around.  Exactly!  For this kind of stuff you want to think one (server) to many (clients). > I can actually move the user folder that I've been mentionning to a private user location on the server, then you can choose to make the user folders available offline to the chosen location on the local hdd Very good insight.  This is how you can do snapshots of anything in a client server world.  Think of where else you could benefit at work.

---

### Post by beartham on 2009-01-23
Hi,

I'm new to Ubuntu (refugee from Fedora and Suse). I am in the process of setting up a Hardy VPS, and following the Ubuntu documentation on Remote Admin, I installed ebox. But I see it is only a few modules. I also see in this thread that others have been having trouble installing additional modules. I'm considering installing Webmin, since I used to use it a lot on Suse. 

Does anybody have a better idea?:confused:

---

