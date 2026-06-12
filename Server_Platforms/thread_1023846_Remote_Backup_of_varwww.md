---
title: "Remote Backup of /var/www"
date: 2008-12-28
forum: Server Platforms
---

### Post by spynappels on 2008-12-28
Hi Guys,

   Here is a question for you:

   Let us assume that I have a web server running on an Ubuntu Server. This web server serves a web based application to local and remote (usually Windows) computers. There is a MySQL database aspect to the application.

   What I am trying to do is take a copy of the /var/www directory and all its subdirectories and copy it to an USB hard drive connected to a client machine, as a means of backing up the entire system. I also need this to be a one-click type operation which can be carried out by people with only basic computer knowledge.

   Is this possible? Does it involve setting up a Samba share of the /var/www directory and accessing it from a local machine by means of some scripts, or is there a better solution?

   Thanks for thinking about this for me, I have considered it and I am coming up against my lack of Linux experience and a distinct ignorance of scripting as roadblocks.

---

### Post by HermanAB on 2008-12-28
Rsync is your friend.

Use Rsync over SSH for secure backups.  A nightly/weekly/monthly cron job can be used to automate it.  A little Googling will get you going, or read this: [http://aeronetworks.ca/rsync-ssh-howto.html](http://aeronetworks.ca/rsync-ssh-howto.html)

Cheers,

Herman

---

