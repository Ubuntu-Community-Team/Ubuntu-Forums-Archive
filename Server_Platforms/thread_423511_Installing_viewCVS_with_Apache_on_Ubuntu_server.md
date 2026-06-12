---
title: "Installing viewCVS with Apache on Ubuntu server"
date: 2007-04-25
forum: Server Platforms
---

### Post by sfo_sc on 2007-04-25
Hi,
I use apt-get install viewcvs on my Ubuntu server and when I browse the myhost.com/cgi-bin/viewcgi.bin  I see the following information

File 	Rev. 	Age 	Author 	Last log entry
Example 	This entry is unreadable
GameLibrary 	This entry is unreadable
Server 	This entry is unreadable
Testing 	This entry is unreadable
NOTE: One or more files were unreadable. The files in the CVS repository should be readable by the web server process. Please report this condition to the administrator of this CVS repository.

It seems to be installed correctly, but I cannot enter the module and read the contents inside.  I have a feeling that I am missing some setup link to the apache.  Any one can give me some advice?  I try to google viewCVS with ubuntu installation it has very limited result.  The way ubuntu install viewCVS is in some weird directory also.  I have no clue what I am missing and what I should do.  Can any one please help?  Thanks.

---

### Post by SneakyWho_am_i on 2008-06-11
I can't remember how I got here but... If anone else passes here in the future, this person's problem I think was the permissions of the fiels INSIDE the cvs repository (nothing to do with ViewCVS and technically not a problem with Apache)...

I might be wrong!!

The solution?
- What group does CVS run as?
- What group owns the files in the repository?
Step One: Make sure that CVS's group has access to the repository and everything in it. Use chmod and/or chown IFF you have to.
- What is the httpd process's user name?
Step Two: Ensure that Apache is a member of CVS's group


Quick and dirty:
Probably cvs runs in the group *cvsd* and probably all the files in the repository are run by the same. If so (assuming your apache user is www-data) then simply issue this at the console:
```
sudo adduser www-data cvsd
```

If I'm wrong then maybe it is something in viewcvs or whatever after all, but I really doubt it.
Also, for this to take effect, you may have to, like, restart apache or even the machine, I'm not sure. If it doesn't work straight away, this MIGHT solve the problem (assuming you're running apache2)
```
sudo /etc/init.d/apache2 restart
```

Corrections are welcome, may as well try to answer the question though because surely people have problems like this all the time, even today.

---

