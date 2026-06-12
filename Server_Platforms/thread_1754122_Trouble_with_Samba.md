---
title: "Trouble with Samba"
date: 2011-05-09
forum: Server Platforms
---

### Post by Maythe on 2011-05-09
Hello everyone,

I feel terrible abusing people as a resource, so I try to avoid asking for guidance as much as possible, but this time I've landed myself in a dire predicament.

--SILLY BACKGROUND STORY THAT YOU NEED NOT READ--

I work for an accounting firm which has been employing a horrid backup method (involving the rotation of 8 external harddrives among 4 computers, each running a different Windows OS) so I offered to devise a better method for backing up and consolidating.

Well I was hoping for some time to research before I began, but my boss is rather gung-ho and purchased a server machine the next day.  Without a choice, I dove in and hit a wall. Well... several walls.

--END OF STORY--


Now for the technical stuff.  The server is running Ubuntu SE 11.04, with Samba and SWAT running.  The computer I need to back up is running WindowsXP.  

On the Server's network, I have forwarded the following ports: 
22 for SSH
137-139 for Samba
445 for Samba
901 for SWAT

I can SSH into the server from the windows XP computer, so that much is working.  However, I attempted methods for backing up via both Samba and rsync.  Rsync does not show any error messages, but does not transfer any file.  And Samba... well I can't figure out how to connect the Windows computer to it.  I'm trying to set this up over the internet, rather than a local network, so that makes things more difficult.

I've raked the internet over and over for tutorials that I could follow, but alas they were far too sporadic and lacking.  If anyone with experience in the matter could troubleshoot with me until we find a fix, I would be most grateful!

Thank you,
Maythe

---

### Post by jamesjenner on 2011-05-09
G'day mate,

I used to try using the default GUI tool to configure SAMBA in 10.10 but gave up because it always screwed things up for me. I ended up just using a shell and editing the configuration file manually, was far more successful.

The first problem your going to have is with windows. Windows plays funny buggers if your not all using the same workgroup, so I suggest make sure all windows boxes are using the same workgroup. This workgroup needs to be defined under linux for SAMBA as well.

The next biggest problem I found was that it's not just setting SAMBA to share the directory but also setting the file permissions under linux so that guest accounts can access the share. Without that you will get nowhere. 

Maybe the first step is to try and see the computer and shared files and then see if you can read. That's far easier. Once you get there it's just a matter of setting up permissions for the file system and samba and you should be right.

I haven't got acess to my linux box at the moment so I cannot give you an example of how my system works, but one thing is to make sure you allow guests access to your shares (well if that is what you wish, otherwise you have to create accounts on linux for the systems that will be connecting to it, I haven't experimented with that sorry). 

Cheers,

James.

---

### Post by Maythe on 2011-05-11
Thanks James!  I will try your advice and post back later with any progress.

Now, as far as actually connecting the Windows computer to Samba, am I supposed to add a new network place and then input the linux server IP?  The server won't show up in the local workgroup automatically because it is over the internet.

---

### Post by jamesjenner on 2011-05-11
ahh, i obviously screwed up and didn't read your original post in that I didn't realise your going over the internet. The workgroup issue is a problem for within a subnet when windows is trying to browse over the the local LAN for windows shares.

I'm not aware of any mechanism for a windows box to see a remote system over the internet without third party software, unfortunately it's not really an area I've played with. I cannot see why you cannot do it but for windows 'Network discovery' to work I would imagine you would have to be virtually a part of the network, such that windows thinks your all part of the same network. I've not played with VPN's under linux, only commercial products under windows. So I'm not going to be much help sorry.

Over the internet I don't believe windows would be able to see a share. I'm pretty sure that shares are restricted to a subnet.

I just looked at rsync (as I'm not that familiar with it) and while the doco isn't 100% clear it does appear some clients support hostname:port. It appears that generally rsync implementations use directories, which makes it understandable why your looking at the samba path. What I suspect you need is to run the appropriate daemon on your server, expose the appropriate ports to the world via a static ip and then use a tool like DeltaCopy to copy from the windows system to the remote server. I don't believe you need to setup anything other than that. 

If you wish to go the shared directory path then I think you will need VPN. Other options include secure FTP (which I believe DeltaCopy utilises). 

Cheers,

James.

---

### Post by Maythe on 2011-05-13
Alright, I got it working (mostly)!

Thanks for all your help James,

Maythe

---

