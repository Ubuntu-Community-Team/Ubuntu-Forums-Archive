---
title: "Using Screen with Logged Rsync Cron Jobs"
date: 2016-12-09
forum: Server Platforms
---

### Post by thufirhawat2 on 2016-12-09
I have a headless Ubuntu 14.04 server I manage solely over SSH. It is basically a webserver/fileserver.

I have been using rsync for quite some time to perform backups, but I have been trying to automate things a little more of late.

Basically, I have a few different rsync jobs setup in cron, and I only want to receive an e-mail if the rsync exits with an error, and I like having my rsyncs run with screen -d -m so if one of the jobs happens to be going, I can connect to the screen at will and check its progress. I have it almost completely figured out, but I am having one strange issue, so I wanted some advice on how I should go about this.

For starters, I followed this thread ([https://ubuntuforums.org/showthread.php?t=1123227](https://ubuntuforums.org/showthread.php?t=1123227)) to get the error-checking e-mails I wanted, and that works great. But when I try to run this script with the screen -d -m, it still works fine, but it leaves the screen running indefinitely (as far as I can tell) after the command completes when I run it as a standard user. When I run it as sudo, it works perfect and the screen terminates after the command is finished. Any ideas/tips? Here is an example of my test rsync script. the rsync locations are intentionally nonexistent so that the rsync will return an error code and trigger the e-mail. I tried invoking screen -d -m right before rsync instead of at the beginning, but that seems to cause the script to fail entirely. I suspect the problem is something simple.

```
#!/bin/bash
# Performs full backup of server data to external drive.
screen -d -m

rsynclog="/var/log/rsynclog"

function checkforerrors {

if [ "$?" -ne "0" ]; then
cat $rsynclog | grep error | mail -s 'RSYNC Error' root
fi

}

rsync --log-file=$rsynclog -r -t -x -v --progress --delete -s /home/user/data username@192.168.1.220:/not/real; checkforerrors
```

---

### Post by thufirhawat2 on 2016-12-09
Nevermind, I figured it out.

Instead of running screen as part of the script the way I used to, I just took that out and called screen -d -m as part of the cron job. So now my cron line looks like this: 

```
52 16 * * * screen -d -m /usr/local/bin/sudorsynctest.sh
```

And all the functionality seems to be there. Hope this helps someone in the future anyway!

---

### Post by Habitual on 2016-12-09
why is screen necessary at all?

---

### Post by thufirhawat2 on 2016-12-09
I wouldn't say it is necessary per se, but I like that if a particularly long rsync job is running, I could attach to the screen and watch it's progress if i so desired.

---

### Post by Habitual on 2016-12-12
Sorry, I meant why is screen -d -m in the script as well as cron?
cron is where I'd expect it in this instance.

---

### Post by thufirhawat2 on 2016-12-12
That is just how my script originally was before I added the logging and conditional e-mail parts and it always worked fine. My original script was basically 

```
#!/bin/bash
# Performs full backup of server data to external drive.
screen -d -m rsync -r -t -x -v --progress --delete -s /home/user/data /mnt/USBDrive
```

And it worked fine for years, so I never had a reason to put it in cron instead of just having it in the script. 

But when I recently added the logging and conditional e-mail parts as shown above, the screens that were generated never terminated, 
and after troubleshooting the script I was sort of at a loss, so I posted the question, then it occurred to me to try putting the 
screen command in cron instead and that worked without the screens hanging. 

I still think it is weird how they hung only for the user and not for sudo even though the script was doing the same thing.

---

### Post by Habitual on 2016-12-12
> **thufirhawat2 said:**
> That is just how my script originally was before I added the logging and conditional e-mail parts and it always worked fine. My original script was basically 

```
#!/bin/bash
# Performs full backup of server data to external drive.
screen -d -m rsync -r -t -x -v --progress --delete -s /home/user/data /mnt/USBDrive
```

And it worked fine for years, so I never had a reason to put it in cron instead of just having it in the script. 

But when I recently added the logging and conditional e-mail parts as shown above, the screens that were generated never terminated, 
and after troubleshooting the script I was sort of at a loss, so I posted the question, then it occurred to me to try putting the 
screen command in cron instead and that worked without the screens hanging. 

I still think it is weird how they hung only for the user and not for sudo even though the script was doing the same thing.

Good reason. I've had those, but I had to issue
```
echo
``` on a single line in one of my scripts or it "just wouldn't work".
So, it's working now?

---

### Post by thufirhawat2 on 2016-12-12
You know, I did search for more information about the echo command because I saw other people doing somewhat similar things and they all had that in there somewhere, but then I started to kind of lose confidence in my scripts' formatting; I started to think that perhaps the positioning of my various lines was what was screwing with me, and so I started looking at other stuff and then finally just came to the solution of putting the screen command in as part of cron's invocation.

It is working great now! I have tested connecting to the screen session during an automatically running job and watching it progress, and I have tested modifying the script in such a way as to guarantee rsync fails either because the backup location does not really exist, or the drive is too small, etc., and it e-mails me every time and lists the error line in the e-mail. Also, I put the logs in log rotate's configuartion so the e-mail will only have to search back for errror lines through 1 week of logs. Thanks for taking a look with me!

---

### Post by Habitual on 2016-12-12
> **thufirhawat2 said:**
> You know, I did search for more information about the echo command because I saw other people doing somewhat similar things and they all had that in there somewhere, but then I started to kind of lose confidence in my scripts' formatting; I started to think that perhaps the positioning of my various lines was what was screwing with me, and so I started looking at other stuff and then finally just came to the solution of putting the screen command in as part of cron's invocation.

It is working great now! I have tested connecting to the screen session during an automatically running job and watching it progress, and I have tested modifying the script in such a way as to guarantee rsync fails either because the backup location does not really exist, or the drive is too small, etc., and it e-mails me every time and lists the error line in the e-mail. Also, I put the logs in log rotate's configuartion so the e-mail will only have to search back for errror lines through 1 week of logs. Thanks for taking a look with me!

Glad it worked out!

---

