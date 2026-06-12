---
title: "Domino 8.5 Unable to bind to port Port = 6400 errno = 98 &quot;Address already in use&quot;"
date: 2008-11-24
forum: Server Platforms
---

### Post by felixdzerzhinsky on 2008-11-24
I have been able to install Lotus Domino 8.5 on Ubuntu Intrepid. When starting the server I get the following messages. How do I fix?

Update: I found this link. In the case of SUSE it is because SuSe Linux employs the Postfix Mail System to run an SMTP daemon that binds to port 25. What is it for Ubuntu?:

[http://tinyurl.com/67z7z3](http://tinyurl.com/67z7z3)

```

felixdz@gUn:~$ su domino 
Password: 
domino@gUn:/home/felixdz$ cd /local/notesdata/
domino@gUn:/local/notesdata$ DISPLAY=:0.0
domino@gUn:/local/notesdata$ export DISPLAY
domino@gUn:/local/notesdata$ /opt/ibm/lotus/bin/server

Lotus Domino (r) Server, Build V85_M2_08202008, August 20, 2008
Copyright (c) IBM Corporation 1987, 2008. All Rights Reserved.

11/25/2008 07:21:55 AM  Event Monitor started
11/25/2008 07:21:55 AM  Warning: All Domino Domain Monitoring probes are disabled resulting in the loss of valuable diagnostic information. Please configure DDM probes in events4.nsf. Assess DDM reports in ddm.nsf.
11/25/2008 07:21:57 AM  Server started on physical node gUn
11/25/2008 07:21:57 AM  Informational, mailbox /local/notesdata/mail.box not cached, either downlevel ODS (minimum ODS level supported for mailbox caching 51, found 43) or not transactionally logged
11/25/2008 07:21:57 AM  Informational, mailbox /local/notesdata/mail.box not cached, either downlevel ODS (minimum ODS level supported for mailbox caching 51, found 43) or not transactionally logged
11/25/2008 07:21:57 AM  The Console file is /local/notesdata/IBM_TECHNICAL_SUPPORT/console.log 
11/25/2008 07:21:57 AM  Console Logging is ENABLED 
11/25/2008 07:21:58 AM  Index update process started
11/25/2008 07:21:58 AM  Database Replicator started
11/25/2008 07:21:58 AM  Replicator is set to Ignore Database Quotas
11/25/2008 07:21:58 AM  Rooms and Resources Manager started
11/25/2008 07:21:58 AM  Schedule Manager started
11/25/2008 07:21:58 AM  DAOSMGR: DAOS Manager started
11/25/2008 07:21:58 AM  DAOSMGR: DAOS is not enabled, nothing to do.
11/25/2008 07:21:58 AM  DAOSMGR: DAOS Manager terminating
11/25/2008 07:21:58 AM  DAOSMGR: DAOS Manager shutdown complete
11/25/2008 07:21:58 AM  Calendar Connector started
11/25/2008 07:21:58 AM  Admin Process: RAD1/Felix Dzerzhinsky Workers Defence Collective is the Administration Server of the Domino Directory.
11/25/2008 07:21:59 AM  Database Server started
> 11/25/2008 07:22:09 AM  AMgr: Executive '1' started. Process id '30709'
Unable to bind to port Port = 6400 errno = 98 "Address already in use"
11/25/2008 07:22:09 AM  SchedMgr: Informational: Schedule Manager is responsible for the busytime database on this server.
11/25/2008 07:22:10 AM  RnRMgr: Informational: Schedule Manager is responsible for the busytime database on this server.
11/25/2008 07:22:10 AM  Agent Manager started
11/25/2008 07:22:10 AM  Schedule Manager: Informational: Detailed schedule information collection is not enabled via the domain-wide Server Configuration document.
11/25/2008 07:22:10 AM  SchedMgr: Validating schedule database
11/25/2008 07:22:10 AM  POP3 Server: Starting...
11/25/2008 07:22:10 AM  IMAP Server: Starting...
11/25/2008 07:22:10 AM  SMTP Server: Starting...
11/25/2008 07:22:10 AM  Rooms and Resources Manager: Informational: Detailed schedule information collection is not enabled via the domain-wide Server Configuration document.
11/25/2008 07:22:10 AM  RnRMgr: Validating schedule database
11/25/2008 07:22:10 AM  LDAP Server: Starting...
11/25/2008 07:22:10 AM  SMTP Server: Started
11/25/2008 07:22:10 AM  Router: Unable to obtain Internet host and domain names
11/25/2008 07:22:10 AM  POP3 Server: Started
11/25/2008 07:22:10 AM  IMAP Server: Started
11/25/2008 07:22:10 AM  ERROR: bindsock' helper application is missing, not executable, not setuid root, or no sticky bit set
11/25/2008 07:22:10 AM  SMTP Server: Listener failure: 'bindsock' is missing, not executable, not owned by root, not setuid root or user needs net_privaddr privilege.
11/25/2008 07:22:10 AM  Suspending listen task for 20 seconds due to network errors
11/25/2008 07:22:10 AM  LDAP Server: Serving directory names.nsf in the  Internet domain
11/25/2008 07:22:10 AM  LDAP Schema: Started loading...
11/25/2008 07:22:10 AM  Administration Process started
11/25/2008 07:22:10 AM  RnRMgr: Done validating schedule database
11/25/2008 07:22:11 AM  SchedMgr: Done validating schedule database
11/25/2008 07:22:11 AM  HTTP Server: Using Web Configuration View
11/25/2008 07:22:19 AM  Router: Mail Router started for domain RAD1
11/25/2008 07:22:19 AM  Router: Internet SMTP host gUn in domain 
11/25/2008 07:22:19 AM  LDAP Schema: Finished loading
11/25/2008 07:22:19 AM  LDAP Server: Started
11/25/2008 07:22:21 AM  JVM: Java Virtual Machine initialized.
11/25/2008 07:22:21 AM  HTTP Server: Java Virtual Machine loaded
11/25/2008 07:22:21 AM  HTTP Server: DSAPI Domino Off-Line Services HTTP extension Loaded successfully
11/25/2008 07:22:24 AM  XSP Command Manager initialized
11/25/2008 07:22:25 AM  HTTP Server: Started
Unable to bind to port Port = 6400 errno = 98 "Address already in use"
11/25/2008 07:22:29 AM  ERROR: bindsock' helper application is missing, not executable, not setuid root, or no sticky bit set
11/25/2008 07:22:29 AM  SMTP Server: Listener failure: 'bindsock' is missing, not executable, not owned by root, not setuid root or user needs net_privaddr privilege.
11/25/2008 07:22:29 AM  Suspending listen task for 20 seconds due to network errors
Unable to bind to port Port = 6400 errno = 98 "Address already in use"

```

---

### Post by cariboo on 2008-11-25
What else is using port 6400, at the prompt type:

```
netstat lpad
```

to see what is listening on port 6400.

Jim

---

