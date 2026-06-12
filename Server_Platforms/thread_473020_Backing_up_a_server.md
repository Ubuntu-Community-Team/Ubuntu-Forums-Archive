---
title: "Backing up a server"
date: 2007-06-13
forum: Server Platforms
---

### Post by Dynotrick on 2007-06-13
I'm trying to figure out the best way to backup my webserver.  I was thinking to backup the whole filesystem to a .tar.gz file and sending it out to a remote FTP server.  This way I can take back files as needed or restore the whole system.  
I'm primarily running a forum on this server, so would this also backup the mySQL databases in a usable way?  What is the best way to set up and automate such a backup?  
Is this the best way to accomplish what I'm after?  
Would restore be a relatively simple process?
I'm a bit of a newbie when it comes to Linux so don't assume I know something already ^^

---

### Post by pkarjala on 2007-06-13
What forum software are you using?  Some forums have a native export utility that will export the entire forum's database to a single file, which you can then use to restore later on if something bad occurs.

Otherwise, it's likely good to backup your /var/www/ directory to a .tar.gz so that it's kept intact.

---

### Post by Dynotrick on 2007-06-14
I'm using SMF and it does have the option to backup the database, so i'll be using that. 

But I was thinking more along the lines of how can I do a full system backup on an automated schedule.  I have some other services running, like FTP and webmin and ssh-server.  In the event of a huge failure I'd like to be able to restore the whole system, either by parts or all at once.

---

### Post by elst on 2007-06-14
> **Dynotrick said:**
> But I was thinking more along the lines of how can I do a full system backup on an automated schedule.  I have some other services running, like FTP and webmin and ssh-server.  In the event of a huge failure I'd like to be able to restore the whole system, either by parts or all at once.

Remember that the majority of files come from packages, so you can quickly restore those with apt-get. The user-created/generated bits are concentrated in specific directories (/etc, /var/www, and so on). You can create an almost identical system from a master by creating an answer file (preseed or Kickstart), giving it to the OS installer, and then just copying any files that are required from backups to the resulting system, and that is often a good enough contingency plan.

FWIW, I use a generic script that accepts options, and backs up particular directories to zip files depending on which option is used. It also has an option to run mysqldump and zip the file generated, and a final option to make a zip containing a package list etc. so that I can make a duplicate system if I need to. The cron scheduler on different machines runs the script with the options required.

---

