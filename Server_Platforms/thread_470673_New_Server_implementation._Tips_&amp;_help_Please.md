---
title: "New Server implementation. Tips &amp; help Please"
date: 2007-06-11
forum: Server Platforms
---

### Post by dsegarra on 2007-06-11
Ok, I am ready to go ahead and switch a company server, of course, to Ubuntu. Before proceeding, I wanted some quick tips. The prior server was done by some company and all I know is a Gentoo console box and it works as a file server. I want a graphical (if possible) Ubuntu server. At least I need two things and these are:

1. Backup Application
2. Firewall application

Any other software that might be of good help?. I just need names of things, I will look for the rest.


Thanks!

dan

---

### Post by Wardazo on 2007-06-11
Hi

1. Firewall. I use ipkungfu to control my iptables, but I think most people probably use firestarter which has a nice gui. ipkungfu is controlled via a very simple config file.

2. Backup. I wrote my own back up shell script. It's  was only about 25 lines of code and remarkably easy given the vast array of tools available within Ubuntu. I think ultimately your backup system will be defined by your hardware.

One other thing you say:

"I want a graphical (if possible) Ubuntu server. "

Avoid ubuntu server edition then. You do not need ubuntu server edition to run a file server in an office.  Just use the "system>shared folders"* option and you're ready to go. I use xubuntu.

Ward

---

### Post by dsegarra on 2007-06-11
Ward,
Thanks!. Ok, so the server edition besides adding some applications that will run on start, its just a console edition just to minimize processes, processor loads?.  I have been a linux user since 1998 and I really never understood the non-graphical part of linux. I mean, if its meant for a server, isnt that server supposed to have enough muscle to move a graphical interface and still provide whatever services are needed?.

Thanks for the info

Dan

---

### Post by juantao on 2007-06-11
You might consider installing the Server Edition and include the 'LAMP' option and then once it's installed (about 15 minutes) you can add the GUI part by issuing the following command <sudo apt-get install xubuntu-desktop>. You'll end up with a box having the best of both worlds.

---

### Post by dsegarra on 2007-06-11
juantao, perfect. Will try that..thanx

---

### Post by Wardazo on 2007-06-11
> **dsegarra said:**
> Ward,
Thanks!. Ok, so the server edition besides adding some applications that will run on start, its just a console edition just to minimize processes, processor loads?.  I have been a linux user since 1998 and I really never understood the non-graphical part of linux. I mean, if its meant for a server, isnt that server supposed to have enough muscle to move a graphical interface and still provide whatever services are needed?.

Thanks for the info

Dan

1. "Ok, so the server edition besides adding some applications that will run on start, its just a console edition just to minimize processes, processor loads?" Exactly! I think there's less hardware support too. The server edition didn't "just work" for me, whereas xubuntu (almost did).

2. Also the more application you run the more them more application that can be compromised. So you could argue it's less secure to run a server with a gui. On a web server I would might accept this, but in a file server on an office... well I think it's FUD provided that you upate and upgrade regularly.

3. Muscle... depends on your situation. On web server that gets thousands of hits a second well I'd get rid of that gui. On an office file server, it probably wont matter.

If you don't want ot learn the console, use ubuntu or xubuntu. Personally, I'd use xubuntu. Light, gui and easy.

Are you usina lan or wireless? WPA is very problematic on xubuntu if your not confident with the command line. 

Get back in contact if your not sure about anything

Oh and one other thing. You might consider using a hardening tool like Bastille, and a vulnerability scanner like Nessus if you're not very clear about security risks.

---

### Post by dsegarra on 2007-06-12
> Oh and one other thing. You might consider using a hardening tool like Bastille, and a vulnerability scanner like Nessus if you're not very clear about security risks.
Thanks for the insight. This will be on a Lan. Not wireless. I have worked with Xubuntu, personally I own a Xubuntu puter. So, I am pretty familiar with it. I will get back as soon as I start this new journey. I know there is some backup system they are currently using under Gentoo. Will see, will post something in the near future.

Thanks
Dan

---

### Post by Wardazo on 2007-06-12
I think xubuntu wil lbe a great choice for you. 

Also, just to give you an idea of how simple backup is...

> tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /

...backs up everything important. 

I was really shocked by this the first time I saw it. Acronis, an excellent  windows backup tool, is what a 100mb program... Linux it's one line, couple lines more for ftp, one more for email notification. 

Good luck

---

### Post by elst on 2007-06-12
WRT backups, an important deciding factor is ease of restoration. For file servers you can anticipate loads of user created files and requests for recovery, so graphical backup tools can be useful for finding the right version of the right file. 

For application servers the majority of the files will come from packages, so you only need to focus on configuration files, logs, and user-generated data (like databases). The tar script approach Wardazo talked about works really nicely there, especially if you tune it to only backup the required directories. For extra convenience I like to have one file for logs, one for /etc, one for the Web sites, and one holding database dumps - each file is then really small, and can be quickly opened by any archiver, including the desktop graphical tools.

---

### Post by dsegarra on 2007-06-13
I see..the idea for a graphical setting is that in case the person in charge of the fileserver (that would be me) can't make it to the office, then someone with some pc experience can manage to do at least certain things. Is there a graphical backup tool that makes incremental backups every two days lets say?. Also, I have done sharing under Ubuntu, are the same techniques applied for a server side?, that would mean samba (for windows workstations). How would it be the user creation under Ubuntu for Win workgroup users to automatically login to the server?. Ideally I want a system where users in the workstations would own their own remote drive. Sounds like a lot, I know. I just want to have some degree of confidence when I do the things thats why I ask..thanks people


Dan

---

### Post by elst on 2007-06-13
> **dsegarra said:**
> I see..the idea for a graphical setting is that in case the person in charge of the fileserver (that would be me) can't make it to the office, then someone with some pc experience can manage to do at least certain things.


Partly, yes - it means that retrieving from backup generally becomes a trivial task, rather than a big issue. My experience has been that users often don't know exactly when stuff had been lost/corrupted, what it was called etc., and are very ready to accept that stuff is irretrievable. Having file browsing functionality in the backup software gives you the confidence that you can quickly locate every file that might be relevant, and get it back. Or, indeed, farm the task out to a trusted person other than the (overworked) main administrator.

> 
Is there a graphical backup tool that makes incremental backups every two days lets say?. 


BackupPC is popular, and Bacula also looks excellent. My employer uses a proprietary solution that I'm not particularly fond of.

> 
Also, I have done sharing under Ubuntu, are the same techniques applied for a server side?, that would mean samba (for windows workstations). How would it be the user creation under Ubuntu for Win workgroup users to automatically login to the server?. Ideally I want a system where users in the workstations would own their own remote drive. Sounds like a lot, I know. I just want to have some degree of confidence when I do the things thats why I ask..thanks people


The Samba suite emulates most of the functionality of a Windows LAN server, and has some extra features. For example, it can create a file share for every user home directory, and run login scripts to map drives etc. when Windows clients connect. The Web site offers the text of several published books that explain how to set up Samba for different scenarios.

One thing that often confuses people - you can't use a user account with Samba until you set a Samba password for it. The Samba password for an account is independent of the main password for the account.

---

### Post by dsegarra on 2007-06-13
;)

elst,
great!..great insight. I think this should be great to start with. I had read about bacula as well. I remember the samba password option as well. Excellent.. Thanks again!!!!.. forums is why I love Ubuntu & Zenwalk. Both have forums that are just great places to share, learn and all the good stuff.


Dan

---

