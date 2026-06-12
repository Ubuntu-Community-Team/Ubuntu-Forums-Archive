---
title: "Inheriting permissions"
date: 2007-10-15
forum: Server Platforms
---

### Post by ginjabunny on 2007-10-15
I have been dabbling at home with Linux for many years now and have never worried much about permissions until recently. When Feisty appeared I converted my server from FC6. I used to just use Samba but now I am running Linux desktop aswell I decided to try NFS for them, so I now have both.
I have a second disk in my Ubuntu server which I share as Public on NFS and Samba, so when I set it up I just chown root and chmod 777,  but now depending how and who creates the files and folders they get different owners and hence different permissions, I want to treat it as totally public so everyone has complete access.

So is there a way to set the permission at the top level and anything new created by anyone always gets that permission, i.e. it is inherited and not just taken from the uid that created it?

I have been hunting around for pointers and can't figure out how I would do this, if at all, any ideas? :confused:

Any help would be much appreciated :)
_!!_

---

### Post by netlogic on 2007-10-15
First, you want to change all the permissions of the group from the parent directory level and apply the Recursive function

**chmod -R 750 director**y

After that you want to set setgid to the folder by 
[B]chmod +s name.of.the.group directory
[/B]
[http://en.wikipedia.org/wiki/Chmod#Special_modes](http://en.wikipedia.org/wiki/Chmod#Special_modes)

---

### Post by ginjabunny on 2007-10-15
Thanks Netlogic for the help

But I think I am must be missing something, when you say 

chmod +s **name.of.the.group** directory

is there a particular group I should use that encompasses everyone or nobody or just a "user" or do I use root? this is confusing me :confused:

---

### Post by netlogic on 2007-10-15
If you are sharing files with few people. You should create a group for that folder. Let's say the folder contains open office docs. Create a group called, **oodocs** and put all the users who need to write to that group. The users might be Jane, Bob, and John.  Set folder to 770 on oodoc folder.

chmod 770 oodoc

If you already have stuff in that folder,

chmod -R 770 oodoc

-R is recursive

After that set your setgid by typing

chmod g+s oodoc

It will inherited the group permission now on.
Also, read the wiki. It will be more clear.

---

### Post by ginjabunny on 2007-10-15
Thanks, this is roughly what I thought, I though maybe there was a user or group that would cover everyone.

So I now have the problem that I run TorrentFlux on Apache and that writes data with user "www-data", I can't really change the group that Apache is in can I? This is why I wanted a catchall everyone group.

Maybe if we approach it from another angle, like a Company setup type scenario, if I had 10 users in 2 groups, say Accounts and Sales, they both have their own group folders, then how do I setup the Public folder so both groups can read and write to the Public folder?

---

### Post by netlogic on 2007-10-15
Why don't you just create a new group that contains all those users? Unix permission doesn't work like ACL.

If you want everyone to read 775 on your folder
7-owner rwx
7-group rwx
5-everyone rx

---

### Post by ginjabunny on 2007-10-15
that's probably why I could never figure it out, I was using NT4 server long before I discovered Linux, obviously I was expecting too much, so there is no way I can set it up as I would like?

---

### Post by netlogic on 2007-10-15
You can't make UNIX work exactly like Windows and you can't make NT work like UNIX.  It is better to create groups for folder and file usages in UNIX and functionality usage with NT.

---

### Post by netlogic on 2007-10-15
Unix is simpler on the group permission. Windows have local groups, global groups, and universal groups. You can't freely use them like most people like. Windows groups are made based around the AD structure.

---

### Post by Brazen on 2007-10-15
You have to enable ACLs in order to do what you want.  ACLs act pretty much just like Windows permissions.  ACLs are a whole 'nother can of worms though and pretty hard to really tell you how to use them in a little forum post.  google for something like 'linux acl' and you should find several very helpful guides.  I particularly remember cutting my teeth on an ACL guide specific to Fedora, but the only difference with Ubuntu is you'll use apt-get to install the ACL support instead of yum.

Personally, I would just ditch nfs and have your linux clients connect through Samba if you already have the samba connections working the way you want.

---

### Post by ginjabunny on 2007-10-16
Thanks for all your help, I understand now why I can't do what I want but will have to revert to just using Samba.

Unless there is some way to do this I can never see native Linux with NFS being used in an office environment, shared files between groups is a basic need.

 I hate to say this but it seems that Linux is inflexible in it's functionality when it comes to permissions and this is crucial if it is to compete with Windows, 

If anyone knows differently then please let me know.

---

### Post by netlogic on 2007-10-16
You have to weight the pros and cons of your needs. Linux will not be better at everything. Certain things, Windows are better.  For me, security, uptime and trust from the vendors are very important than flexible configurations and easier usage.  Also, having the software giant determine the IT budget can get annoying.

---

### Post by ginjabunny on 2007-10-16
Thanks for your time netlogic, I think I will look into ACLs as Brazen suggested.

I have always wondered how you would setup a typical business using only Linux with NFS network shares in the usual model of Home, Group and Public because I couldn't figure out how the permissions would fit (because they are not inherited). This is effectively what I have tried to do at home, maybe there is a way of doing it? If someone knows of a detailed case study in which it works it may illuminate things for me.

---

### Post by codmate on 2007-10-16
> **ginjabunny said:**
> Thanks for your time netlogic, I think I will look into ACLs as Brazen suggested.

I have always wondered how you would setup a typical business using only Linux with NFS network shares in the usual model of Home, Group and Public because I couldn't figure out how the permissions would fit (because they are not inherited). This is effectively what I have tried to do at home, maybe there is a way of doing it? If someone knows of a detailed case study in which it works it may illuminate things for me.

Wel - you can either set up a user on the Linux box for each user in the Windows world (and rely on *nix permissions - which can do what you need using stickybits etc.), or you can use ADS security in Samba to authenticate samba shares via AD.

I've been taking the latter route recently, and with a few caveats, it works well. The setfacl command will be your friend if you choose this strategy.

---

