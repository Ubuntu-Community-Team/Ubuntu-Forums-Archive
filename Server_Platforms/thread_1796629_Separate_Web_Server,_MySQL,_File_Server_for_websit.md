---
title: "Separate Web Server, MySQL, File Server for website"
date: 2011-07-04
forum: Server Platforms
---

### Post by swiggyswag on 2011-07-04
Hello everyone,
I've tried searching for answer to my question but came up empty probably due to me not know exactly what to search for.  I have a lamp server set-up on one server.  What I want to do now is set-up another server to run just the MySQL database and then other servers/NAS to host the files that will be on my website.  The way the site is there will be lots of user uploaded content, so I will end up needing to add more and more space to it.  My question is what is the best way to achieve this?  I will have all the machines set-up on a gigabit network through a switch so that part is figured out.  My LAMP server (Ubuntu Server 10.04) has webmin running.  My website works perfect fine just running on the one machine doing everything.  I'm just not sure how to go about setting up a server that does the mysql and what not and then the file serving.  Would I set-up another LAMP server just running MySQL and point my database host to that IP then it would take care of those calls?  Then setup each other file server with LAMP and point the webserver to the file locations to save?

Also, what is the best way to account for a website that say the videos folder will need to keep growing?  I need to set the hdds up in RAID so they will the files up, but that space needs to keep growing.  Can you say have individual hdds in one server raided.  For example hdd 1 is set-up raid 1 with hdd 2 and hdd 3 is set-up raid 1 with hdd 4?  

I know its a a lot of questions.  I have a pretty good understanding of what I'm doing but I'm in the process of coding in 3 different languages right now on a time limit and need this done and my brain is going crazy trying to find time to figure this out lol. 

Thank you guys very much for the help or yelling or anything you want to type back to me :).

Tom

---

### Post by SeijiSensei on 2011-07-04
For MySQL, you can install it on another machine and access it over the network.  I don't know what language you're using to develop web applications, but if it's PHP, you just enter the name or IP of the remote host in [mysql_connect()]("http://php.net/manual/en/function.mysql-connect.php").  You'll need to edit the configuration files so that mysqld listens on the network interface; by default it's limited to localhost for security reasons.

As for file services, the best solution for Linux-to-Linux sharing remains NFS.

If you want to build a RAID filesystem that can be easily expanded by adding additional drives, you need to use RAID5 or RAID6.  If you're building these machines yourself, use hot-swappable drives if possible.  Even better is to use hot-swappable drives with a hardware RAID controller.

---

### Post by rudelgurke on 2011-07-04
Well - to avoid some confusion - there's no RAID filesystem - either you format a partition on a RAID array with a filesystem or you use a Cluster Filesystem (like OCFS2).

For building your environment - what you exactly want to reach ? If you've 3 machines and only 1 serving content for the public, best use 2 NIC's in the public machine.
One for serving content, the other NIC listens local for DB / NAS etc.

Then install the DB machine, if you want to use a dedicated DB server - setup MySQL to listen on the network interface and create the users granting them the right to connect from remote (dbuser@192.168.0.102). Also don't forget /etc/hosts.allow to restrict access a bit further.
If there're other machines in this internal network, maybe setup an underlying encryption (SSH tunnel, VLAN with IPsec etc.)

Then the fileserver - here it depends on what you want to use. Just serving files from this server or "splitting" them - clustering.
If you decide to cluster - OCFS2 and DRBD are good choices.

If you just want to store your webroot on the fileserver - maybe not much advantage doing so because you can put the HDD's in your webserver and have less network traffic and maybe less failures - in case your fileserver is down.

Though - why not cluster anything ? 3 machines and then do load balancing gives maybe some better fault tolerance than having single servers to do 1 task and in case one of your machines fail the other 2 ones can't do anything.

---

