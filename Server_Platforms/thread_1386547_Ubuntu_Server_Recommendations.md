---
title: "Ubuntu Server Recommendations"
date: 2010-01-20
forum: Server Platforms
---

### Post by natravis on 2010-01-20
Hi all!

I'm wanting to put together my own server primarily for FTP file serving, backup, and media storage. I do not have an old box around, but was looking at something like [ur]http://www.newegg.com/Product/ComboBundleDetails.aspx?ItemList=Combo.311352[/url] as the system. I already have all the hard drives I need and I'll shift a CD drive around temporarily to install. I plan on using Ubuntu Server.

I've been toying with VSFTPD, but it seems more complex than I need or I may be missing something obvious. A perfect world solution would be something similar to Filezilla Server (which worked great but I don't want to keep my gaming rig running 24/7. I liked the ability to specify certain folders to share to certain groups, etc.

[IMG]http://wiki.filezilla-project.org/wiki/images/f/f5/FZS_aliases.png[/IMG]

The image illustrates the folder adding ability, rather than having to move folders into the ftp home folder. It also shows the user list (right side) where you can define different folder access per user or group (friends access different folders than family, for example). (as a side question, can you just create symlinks to the home folder while having the actual files mounted elsewhere?). Also, if there is a way to have a user database of people allowed to connect, rather than having users with their own local drives, that would be awesome.

So, to make a nice list of features for recommendations:
[LIST]
[*]GUI would be nice for initial testing so I can see the changes in the commandline config (testing on my laptop, eventually plan on CLI server environment) (if someone recommends a gui powered one, it would be worth installing x stuff and forwarding it to my laptop:D)
[*]easily update-able user list that does not require an actual local user account (a list of users that can access certain folders on the system)
[*]ability to share folders in their current location rather than having to migrate them into a specific folder 
[/LIST]

I'll be monitoring for any questions for me and will be happy to provide further information and thanks a million for your help.

---

