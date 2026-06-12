---
title: "I have reason to believe debian/ubuntu messes with postgresql server"
date: 2008-04-19
forum: Server Platforms
---

### Post by Mateo on 2008-04-19
i've been told by people in the know that debian makes changes to postgres.  My problem is that no matter what you do to the log settings, you can not have the server record ALL statements sent to the database.  my settings in postgresql.conf:

log_min_messages = notice
log_statement = 'all'
log_destination = 'stderr'
redirect_stderr = on	
log_directory = '/var/log/postgresql'		# Directory where log files are 
log_filename = 'postgresql-%Y-%m-%d_%H%M%S.log' 


-----------------

even turning off redirection has no effect.  i'm not getting the messages sent to the log files.  therefore, i'm unable to figure out what the problem is with my code.  No logging = no debugging.  i'm at a brick wall here and need to know a way around this problem..

---

### Post by Mateo on 2008-04-20
bump.

---

### Post by ikonia on 2008-04-20
go and ask debian support resources what they do and why.

---

