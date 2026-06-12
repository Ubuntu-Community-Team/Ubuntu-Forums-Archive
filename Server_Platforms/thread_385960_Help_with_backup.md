---
title: "Help with backup"
date: 2007-03-16
forum: Server Platforms
---

### Post by fernando_lopes_jr on 2007-03-16
I need same help with a backup job I want to do with my system. I want to do a weekly backup every sunday of my files I was thinking of compressing my files to save space. I did this: 
> sudo vi /etc/crontab

and added this line

00 04 * * 0 root tar cvpjf /backup/backup.tar.bz2 /home/cda/cda-server/Jr/Books /home/cda/cda-server/Jr/Documents /home/cda/cda-server/Jr/Enta /home/cda/cda-server/Jr/Music /home/cda/cda-server/Pictures /home/cda/cda-server/Jr/System*

Just wanted to check everything was ok :)

---

### Post by fernando_lopes_jr on 2007-03-18
Please can sameone give me a hand

---

### Post by fluffymikey on 2007-03-18
You might make some small adjustments like;

> 
0 4 * * 0 tar -cjf /backup/backup.tar.bz2 /home/cda/cda-server/Jr/Books /home/cda/cda-server/Jr/Documents /home/cda/cda-server/Jr/Enta /home/cda/cda-server/Jr/Music /home/cda/cda-server/Pictures /home/cda/cda-server/Jr/System*


Unless what you have isn't working, you can probably take off the unecessary commands like -v since it's a cronjob.  If you're doing this as root then you won't likely need the -p.  You also don't need to have 'root' in front of the tar command, unles that is some kind of aliased command for getting root access.

I have a similar cronjob on one of my servers.  I do it by creating a shell script to do the tar command, then then having a cronjob run that script.  The only reason I do it that way is because the crontab looks like a mess when there's a lot of commands in there like that.  I can also run the same command at different schedules easily.

Hope that helps some.

---

### Post by nix4me on 2007-03-18
i make a script also.  Then just save the script into the /etc/cron.weekly folder and restart cron.

nix4me

---

### Post by fernando_lopes_jr on 2007-03-19
Could you show me how I could run a script? Like a Howto with the steps.

---

### Post by fluffymikey on 2007-03-19
> **fernando_lopes_jr said:**
> Could you show me how I could run a script? Like a Howto with the steps.

A script is just a text file with console commands in it.  For instance;

```

#!/bin/bash
#backupscript.sh

tar -cjf /backup/backup.tar.bz2 /home/fnord/stufftobackup/;

```

Then to run it, you would need to make it executable with 'chmod u+x backupscript.sh'

```

# chmod u+x backupscript.sh
# ./backupscript.sh

```

Or if you wanted to run it in cron, you would need to use the absolute path.

---

### Post by fernando_lopes_jr on 2007-03-19
So let me just recap to make sure I've got this all rigth:

> # vi backupjob1.sh

Paste

#!/bin/bash
#backupjob1.sh

tar -cjf /backup/Books.Documents.Enta.tar.bz2 /home/cda/cda-server/Jr/Books/; /home/cda/cda-server/Jr/Documents/; /home/cda/cda-server/Jr/Enta/; 

# chmod u+x backupjob1.sh
# sudo vi /etc/crontab

Paste 

30 1   8 * *    root    /home/cda/cda-server/Jr/Backup/./backupjob2.sh  - this will do backup at 1:30 am every 8th of each month
30 1   * * 0    root    /home/cda/cda-server/Jr/Backup/./backupjob3.sh  - this will do backup at 1:30 am every Sunday 



Thanks alot for all the help :)

---

