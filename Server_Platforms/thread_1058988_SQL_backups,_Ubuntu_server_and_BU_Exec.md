---
title: "SQL backups, Ubuntu server and BU Exec"
date: 2009-02-03
forum: Server Platforms
---

### Post by awsutter on 2009-02-03
Hi everyone,

I've just put up an Ubuntu server our otherwise all-Windows shop. The Ubuntu box is a LAMP and hosts our internal helpdesk system. 

I don't need technical help so much as I'd like some input on keeping the backup scheme as efficient as possible. 

I need db backups from the Ubuntu box to be picked up by our Backup Exec 11 server. Currently I've got a cron job running a nightly mysqldump to the local disk.

Perhaps someone with more experience can help here: am I best off attempting to install the BUExec remote agent (is it possible?) on the Ubuntu box, or am I better off with a series of convoluted scp/wget/ftp/whatever scripts to and from a Windows box already running the agent?

The SQL dumps already generated are more than adequate, and I don't anticipate any further backup needs from the Ubuntu machine.

Thanks!
Drew

---

### Post by Coreigh on 2009-02-03
I should be doing this but I have not yet. My plan was to utilize a native Linux backup application to create a backup-to-file on the Ubuntu server then dump the backup file in a folder on the Windows server to be backed up. This was the easiest solution I could find but the down side, in my case, was that the Ubuntu backup would be one day behind. In other words I would have a current backup of my Ubuntu server (on the Windows file server) but it would not get archived to tape until the next days Windows backup cycle.

---

### Post by awsutter on 2009-02-03
Thanks, Coreigh. 

For now, I've just scheduled a nightly batch job on the Windows box to scp (pscp actually) the contents of my sqldump directory to a local folder on the Windows box. Seemed to be the simplest means of getting that done.

May investigate installing the BUExec agent in the future, if a real SQL agent should become useful.

Drew

---

