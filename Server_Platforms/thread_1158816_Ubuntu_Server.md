---
title: "Ubuntu Server"
date: 2009-05-14
forum: Server Platforms
---

### Post by kjangas on 2009-05-14
Hi everyone,
 
I will like to ask a Question! 
 
I want to setup a Ubuntu server as a domain controller, to control Windows XP or vista client. Isit ok or got any problem??
 
Like that isit i can set the user right, print, and file on Ubuntu server. Isit same like Windows server 2003??  
 
Thank for reply me.
Have a good day..

---

### Post by mitanc on 2009-05-14
I have set exactly this up in my company.  For the most part users can log in, a script can set their directories / printers, and you can have a Domain using OpenLDAP.  

I didn't need all of the features of Windows Server 2003, so basically with Ubuntu the setup enables me to have ldap entries for users and groups and those users and groups can have their permissions set in the Samba share.  This allows you to do whatever permissions you want, and its pretty stable.  Some useful tips:

1.  Use ubuntu 8.04 LTS Server.  There are good HOW TOs on Sourceforge and the Ubuntuforums on how to set exactly what you want up.  I used the latest Ubuntu version and while you can get it working, its not as good as my experience with 8.04.

2.  I would recommend getting a dummy windows machine as a print server, CUPS is okay but I find it slower than using Win XP on an old box dedicated to my 2 laser printers.  Also CUPS drivers are hit or miss, if your printer is supported without some hacking then it may be good to go.  YMMV.

3.  I switched from Windows SBS 2003 to Ubuntu.  While administration wise I LOVE it, the users do say its a bit sluggish at times.  NOTE: We mainly use excel here so sometimes saving files is a bit slow (slower than SBS 2003) but livable for me.  

Other things to consider:
1.  ClamAV scans my shared folders on the server nightly.  Emails me a report and I can delete any virus's found.

2.  I have nightly backups.  All important client images are rsync'd to a server over the internet and all data is in a seperate harddrive using rsnapshot.  (I get full backups of one week of data + a month)

3.  Hamachi enables me to access my server from anywhere.  I can access my files, SSH, do whatever I need to do.

Anyways, hope this helps!

---

### Post by kjangas on 2009-05-14
Hi mitanc,
 
Thank for reply. And you are solve my worry. Many thank
 
You mean the print server better host by windows system??

---

### Post by ghen on 2009-05-19
considering any windows machine 2000 or higher will act as a print server that isn't really a priority. The main crux is removing Windows Server from the mix IMO. If you truly need a real print server just set up a dummy XP machine. You'll have an easier time with drivers that way with windows clients.

---

