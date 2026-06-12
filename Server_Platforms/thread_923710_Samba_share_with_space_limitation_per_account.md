---
title: "Samba share with space limitation per account"
date: 2008-09-18
forum: Server Platforms
---

### Post by rslrdx on 2008-09-18
Hi and TIA,

Let me start by saying that I understand this is not the samba forum, but I thought I'd give it a try anyway.

I'm trying to setup some samba shares with custom per user account sharing rights and space, and I'm failing to do it easily with some other "ready to go" tools I tried, so here I am looking for some ideas.

First to what a I have in mind. I want to have a 500GB drive hosted on a network and a single public area but also individual folders based on users account rights. The rights include read, write, browse, mapping, limited to a 5 gigabytes space quota per account, only able to see its own space/folder for security. Some sort of basic profile where new users to can be added to avoid the work of matching basic common rights. A simple way to create this accounts and folders would be greatly appreciated as non tech users will be in charge of creating this accounts. It would be nice but not a requirement to easily find out how much space was used on each account. 

With this in mind, I looked at FreeNAS, but it doesn't have the ability to work with quotas, I started to look for something else, and OpenFiler came up, but i think that using LDAP for this task is a bit of an Over Kill, it also doesn't have good info on getting the setup I'm looking for up and going easily. Last but not least, I'm currently trying Ebox, but I'm not sure it will do it either as I try to make it work with quotas and it doesn't seem simple (I could be wrong).

I do have a single samba share right now, and everyone knows the password and that should give you an idea of how secure it really is right now, but it doesn't do things exactly the way i want to. So, I like to ask everyone if they got a good idea of if maybe I've missed something, please let me know.

I'm reading up on all this stuff, I'm not here to just scream for help and hope for a solution to fall on my lap.

Any and all good ideas are welcome.

TIA, 
Rodrigo.

---

### Post by warchief_ryan on 2008-09-18
I've never tried it myself but why not create a partition thats the size limit you want and place the share on it? Just an idea.

---

### Post by rslrdx on 2008-09-19
> **warchief_ryan said:**
> I've never tried it myself but why not create a partition thats the size limit you want and place the share on it? Just an idea.

partition size is not a problem, the problem i see with your idea is that everytime i create a new user i have to make a new partion, and this is not a good idea, one mistake and everyones data is gone, besides, teaching a non tech user to create partions on the HD is way beyond an easy setup.

Thanks anyway.
Keep the ideas comming please.
Rodrigo.

---

### Post by bab1 on 2008-09-19
I believe what you want to do can be accomplished by using disk quotas and the Samba [homes] directive in the smb.conf file.

I see it as:

1. The use of linux disk quotas.  See: [**[COLOR="Blue"]http://gentoo-wiki.com/HOWTO_use_User_Quota's[/COLOR]**]("http://gentoo-wiki.com/HOWTO_use_User_Quota's")

2. The use of the samba directive **[homes]** in the smb.conf file.  Try: ```
man smb.conf
``` for information.

The first of the man pages on [homes] reveals:
```
The [homes] section
       If a section called [homes] is included in the configuration file, services connecting  clients
       to their home directories can be created on the fly by the server.

```

My homes section of the smb.conf file looks like this:```
[homes]
        comment = Samba Home Directory
        path = /smb/home/%S
        browseable = no
   ; Only logged in users allowed 
        valid users = %S +smbusers
        force group = smbusers
        writable = yes
        create mask = 770
        directory mask = 770

```

With these you can now keep the users separated and the disk quota will limit the users disk space.

---

### Post by rslrdx on 2008-09-19
Hi, Thanks for the info, i'll be looking into it, but perhaps you know if there is a GUI to use this tools with? just trying to make it easier for the non tech and for the tech having to give training to the non tech.

TIA,
Rodrigo

---

### Post by bab1 on 2008-09-19
> perhaps you know if there is a GUI to use this tools with?

I'm afraid not.  What I have suggested is really a plan more than specifics.  What you would be doing is low level.  By that i mean you are adding basic functionality to the system with **quota**.  The tools for quota are command line tools that allow you (the sys admin) to create your own scripts.  The Samba configuration is a 2 minute job with a text editor.  It only needs to be done once.

How many users and/or their frequency of turnover is an important factor.  If if there is a lot of user turnover then I would create a bash script to set user quotas.  I also noticed there are PERL tools for scripting also.

Do you have a test host that you can experiment on?  How comfortable are you with the basics of Linux?  What is your final end use for the Samba server?

---

### Post by rslrdx on 2008-09-19
> Do you have a test host that you can experiment on? How comfortable are you with the basics of Linux? What is your final end use for the Samba server?


Hi, and thanks for the help, I do have a test server, in fact i have a test server rack of sorts (about 9 boxes right  now and growing) so that wont be a problem. and quite comfortable, its the only OS i run now to do everything, and been using it on and off since 97ish... but for the last 2 years strait its been my DE facto OS. i don't play games anymore on my boxes, just on my xbox which I'm doing my best not to turn it into another Linux box :P

As for the Samba server, i need to setup about 12 users on a graphics design firm with no permanent admin (hence the need for an easy setup). This same server will have another folder shared via FTP, to the outside world, so that clients can upload their files to them, but i doubt this will have much of an impact on the samba shares, thats why i didn't bring it up until now. 

As for the need to change users all the time, its not the reality on the samba shares but it will be on the ftp, the samba side, only needs some GUI tool to make it easy (if possible) to manage users and shares. The turnover time frame hangs between 30 to 120 days and most will be permanent, I doubt it will increase to over 20 people total in a year.

---

### Post by cariboo on 2008-09-20
There is a reference in the Samba3 howto about setting quotas in smb.conf, it is available here:

[http://www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf](http://www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf)

Jim

---

### Post by bab1 on 2008-09-20
After doing a bit of reading, I believe the eBox solution is the best for your needs.  If we were to do all of the Linux OS disk quota and Samba setup of [homes] we still would not have a web (or GUI) interface.  

The eBox has all of that and more.  I see that it's based on Debian and uses PERL as the scripting language.  All presented to the eBox admin via web pages. 

Although we have not mentioned it, you must have to maintain DNS, IP addressing and user authentication for the network.  It looks like the all of this can be handled by the eBox platform.

Is there a downside?  You bet.  It's cutting edge and untested over the long run, so there could be bugs.  But I would think it is worth it for you to attempt implementing it.

---

