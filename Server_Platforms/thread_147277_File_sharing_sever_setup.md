---
title: "File sharing sever setup"
date: 2006-03-19
forum: Server Platforms
---

### Post by Tarmon.Gaidon on 2006-03-19
I was wondering if anyone could help me set up a file sharing server that me and and a few of my friends would be able to access and share files. So they could upload files and download and such. Any help on setting this up would be great. Sorry if this sounds kind of stupid I have never set anything up like this.

Any help would be welcome, thank you!

---

### Post by cilynx on 2006-03-19
Are you looking for an in-house server or an Internet wide data-store?  Do you want to mount the storage space on the client machines or are you looking for more of an FTP like solution?  Basically, what are you trying to accomplish?  We can help more with more info.

---

### Post by oly on 2006-03-20
basically its a network for a school which i am setting up, i have it all set up as a single server but the load will be to great for one server so want to seperate the tasks to different machines.

so i would like to store student home areas on one server teachers on another server shared areas on a third server, and possible put printing on to one of the three servers as i do not think a 4th is nessecary.

i am just unsure how to go about configuring samba for this, so yes its internal and not suited to ftp because the areas should be mounted on login.

---

### Post by derelict on 2006-03-20
[QUOTE=oly]
so i would like to store student home areas on one server teachers on another server shared areas on a third server, and possible put printing on to one of the three servers as i do not think a 4th is nessecary.[/quote]
If you really feel that you need that much hardware I'd set up the shared space and printers together.

> i am just unsure how to go about configuring samba for this (...) the areas should be mounted on login.
If you're going to keep user accounts on the Samba server (i.e. each student needs and account on the student server and each teacher needs one on the teacher server) the configuration is rather simple:
The user's space:
[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mode = 0700

The shared space can be something like:
[shared]
   comment = Shared area
   path = /shared
   read only = no
   public = yes

You'll probably need to fine tune these settings to match your context

---

### Post by oly on 2006-03-21
ooops i actually replyed in the wrong thread mine was a bit further down :( 

what i am confused about is how they interact, i want all account info on one computer but have the home areas on differnet servers.

in windows i can referance another server using //server/path so would i add something like that into the main samba share, or do i configure another instance of samba on the second server and have it referance the first for permissions some how. ?? 

this is for a school with aroun 300 computer with pretty much all of them being accessed at the same time when people log on at the start of the lesson so a fair amount of horse power is needed,

---

### Post by derelict on 2006-03-21
[QUOTE=oly]
what i am confused about is how they interact, i want all account info on one computer but have the home areas on differnet servers.[/quote]
Then you'll have to setup the Samba servers with the home areas to authenticate to another machine, like a Windows Active Directory domain controller or some other Samba server that holds the user accounts.

> 
in windows i can referance another server using //server/path so would i add something like that into the main samba share
You can also reference a Samba server and shares like that.

---

