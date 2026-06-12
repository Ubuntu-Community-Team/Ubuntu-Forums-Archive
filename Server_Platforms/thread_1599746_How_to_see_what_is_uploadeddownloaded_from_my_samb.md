---
title: "How to see what is uploaded/downloaded from my samba/ssh server?"
date: 2010-10-18
forum: Server Platforms
---

### Post by rado3105 on 2010-10-18
Is possible to see(some log...) files that are downloaded/uplodaded from my samba/ssh server and how? Thanks

---

### Post by Ryan Dwyer on 2010-10-18
Samba stores log files per-user and per-machine in /var/log/samba/. Have a look at those.

For SSH, commands run via sudo are logged to /var/log/auth.log. For non-sudo commands, you might be able to find out what a user has run by looking in their .bash_history file in their home folder.

---

### Post by rado3105 on 2010-10-18
whichone of this in /var/log/samba:

cores          
log.nmbd.7.gz 
 log.smbd.7.gz 
        log.winbindd.5.gz
log.nmbd     
  log.smbd      
 log.wb-BUILTIN        
log.winbindd.6.gz
log.nmbd.1.gz 
 log.smbd.1.gz  
log.wb-UBUNTU-SERVER
  log.winbindd.7.gz
log.nmbd.2.gz 
 log.smbd.2.gz 
 log.winbindd         
 log.winbindd-dc-connect
log.nmbd.3.gz 
 log.smbd.3.gz  
log.winbindd.1.gz   
  log.winbindd-idmap
log.nmbd.4.gz 
 log.smbd.4.gz
  log.winbindd.2.gz  
   log.winbindd-idmap.old
log.nmbd.5.gz  
log.smbd.5.gz  
log.winbindd.3.gz
log.nmbd.6.gz 
 log.smbd.6.gz  
log.winbindd.4.gz

Is any better choice? for ssh and samba

---

### Post by Ryan Dwyer on 2010-10-18
You need to look at the log filenames and recognise which ones are usernames or computer names.

You should connect from a different machine and transfer a file so you can see what the log entries look like. It doesn't look like you've connected to samba with a username yet.

---

### Post by rado3105 on 2010-10-18
Is any way to see it in nagios or smt. like that? To look various days and see what was somebody downloading and what size....

---

