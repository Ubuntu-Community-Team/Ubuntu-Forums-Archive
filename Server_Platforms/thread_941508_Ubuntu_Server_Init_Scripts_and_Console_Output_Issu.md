---
title: "Ubuntu Server Init Scripts and Console Output Issue"
date: 2008-10-08
forum: Server Platforms
---

### Post by JGillTech on 2008-10-08
My NetWorker (backup software) daemon stops the mysql daemon before backup and starts upon completion.  When the mysql init script is called the output is directed to the active console session.  This is quite annoying when you are using the system and a backup kicks off.  It looks something like this: 

root@limes:/nsr/res# * Stopping MySQL database server mysqld .... done 

The prompt disappears and you have to hit enter to get a prompt again.  This does not occur of my Ubuntu 6.06 server.  I traced the difference to the script and the use of ./lib/lsb/init-functions.  Not sure what this library is for.. but the log_daemon_msg is called to display the text to the console rather than echo in other scripts.  How can this behavior be modified?

My mysql init script on my Ubuntu 6.06 server uses echo -n and the Ubuntu Server 8.? uses a combination of log_daemon_msg and log_end msg 0.  What are these and how are they used.  I am new to Ubuntu and Linux in general... perhaps I am way off.  Why doesn't the echo -n command in on my Ubuntu 6.06 server output at the console when my backup process kicks off?

---

