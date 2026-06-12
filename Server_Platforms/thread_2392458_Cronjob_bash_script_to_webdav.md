---
title: "Cronjob bash script to webdav"
date: 2018-05-21
forum: Server Platforms
---

### Post by ricardo35 on 2018-05-21
Hi,

I've been messing with this a few hours now and I can't figure this out. Can someone please help me or point me in the right direction?

I have in my home folder (ricardo) three subfolders:
- Scans
- Scripts
- Stack

Inside Scipts there is a bash script that moves everything from Scans to Stack.
Scans is a folder where an MFP saves its scans.
Stack is a folder which is mounted with webdav.

Basically when someone scans a document, it goes to the Scans folder (works!) and then with the bash script it's moved to the Stack folder. Works too!

Now the final piece of the puzzle is that it runs on its own without any intervention, even on reboot without anyone logging in since this is a VPS.

I thought to do:
sudo crontab -e
and put this in:

```

SHELL=/bin/bash

* * * * * /home/ricardo/Scripts/move.sh

```

In the syslog I see the following:
May 21 17:56:01 omega CRON[2578]: (root) CMD (/home/ricardo/Scripts/move.sh)May 21 17:56:01 omega CRON[2577]: (CRON) info (No MTA installed, discarding output)

So I guess the cron is running but the scan is never moved to the Stack folder.

The contents of my script:
```

#! /bin/bash
clear
mv ~/Scans/* ~/Stack/Tunnel/Scans/

```


What am I doing wrong?

---

### Post by papibe on 2018-05-21
Hi ricardo35.

A few thoughts:
I'd start by making sure your script has execute permissions:
```
chmod a+x /home/ricardo/Scripts/move.sh
```
This
```
No MTA installed, discarding output
```
usually means, the script is producing an output to a terminal, and cron tries to send you a mail with the text. Since the mail alerts are not configured by default, the script fails.

You can solve that by redirecting the output of your script to /dev/null, or better to a log file so you can debug it:
```
* * * * * /home/ricardo/Scripts/move.sh >> ~/log.log 2>&1
```
Then, you could check that file later to review the output.

There should be no space between the shebang and the shell's path:
```
#!/bin/bash
...
```

Do not use interactive shell commands in your script: remove the 'clear' command.

Since you are registering the output of your script now, be more verbose so the log is more meaningful
```
date
mv  -v ~/Scans/* ~/Stack/Tunnel/Scans/ 
echo done
echo
```
If the scanner doesn't generate unique names, very common problem in my opinion, you will be either overwriting, and thus losing files, or triggering a interactive prompt to confirm the move. To avoid that situation, you can use the --backup option:
```
mv -iv --backup=numbered ....
```

Hope that helps. Let us know how it goes.
Regards.

---

### Post by LHammonds on 2018-05-21
Here is what you are doing wrong:


[LIST=1]
[*]You do not need the "clear" command in the script when using it for scheduled automation. 
[*]As papibe said, you have a space in #!/bin/bash 
[*]Do NOT use relative paths.  Using "which mv" should reveal "/bin/mv"  Do not use ~/ but instead the full path you "expect" such as:
```
/bin/mv --backup=numbered /home/ricardo/Scans/* /home/ricardo/Stack/Tunnel/Scans/.
``` 
[*]Add logging to your script so you can look at the log and know exactly what is going on and WHEN it is going in.
```

LogFile="/var/log/move-scans.log"
echo "`date +%Y-%m-%d_%H:%M:%S` Move started..." >> ${LogFile}
/bin/mv --backup=numbered /home/ricardo/Scans/* /home/ricardo/Stack/Tunnel/Scans/.
echo "`date +%Y-%m-%d_%H:%M:%S` Move completed." >> ${LogFile}

``` 
[*]Add error-checking to the move command and log the results:
```

/bin/mv --backup=numbered /home/ricardo/Scans/* /home/ricardo/Stack/Tunnel/Scans/.
ReturnCode=$?
if [ ${ReturnCode} -ne 0 ]; then
  echo "`date +%Y-%m-%d_%H:%M:%S` ERROR: mv return code is ${ReturnCode}" >> ${LogFile}
  ## This is also a good place to insert a "sendemail" command for notifying you that something wrong happened. ##
else
  ## INFO is not necessary but an example of what can be done if command completed successfully. ##
  echo "`date +%Y-%m-%d_%H:%M:%S` INFO: mv completed." >> ${LogFile}
fi

``` 
[*]Include code at the top so that the move command is not executed if it is not needed.
```
## If no files exist, there is nothing to do.
files=$(ls -A /home/ricardo/Scans/ 2> /dev/null | wc -l)
if [ "${files}" = "0" ]; then
  exit 0
fi

``` 
[*]If you do not want to or have too many scripts to go back and insert the full path to executables, you could include the path inside the crontab schedule but that is considered less secure than including full path in your scripts:
```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
``` 
[*]When scheduling scripts, I re-direct all output and errors from the script to /dev/null since I do all my own logging inside the script.
```
*/15 * * * * /home/ricardo/Scripts/ricardo-move.sh > /dev/null 2>&1
``` 
[/LIST]

When automating commands, you should account for things not working as you would expect because when you are typing these simple commands interactively, you can see what is going on and react immediately to fix what is not working correctly.  This is not the case when doing automation, you have to assume failure at every step...such as not able to find the program you are calling (path issue) or relative paths not working as expected (being run under different IDs) or errors with the commands (such as disk space full, overwriting files with same names, etc.)

I hope this helps...and have fun with Bash automation!  It is one of the best things I love about Linux.

LHammonds

---

### Post by papibe on 2018-05-21
@LHammonds, hi

What would be the benefit of forcing an interactive prompt in the 'mv' command (option -i)?

Regards.

---

### Post by LHammonds on 2018-05-21
> **papibe said:**
> What would be the benefit of forcing an interactive prompt in the 'mv' command (option -i)?
My bad.  I liked the --backup option that you gave and copy/pasted it and didn't realize I got the -iv (which I would not use)

On my scripts, I do not need such a thing because I loop through each and every file and check to make sure the source will not overwrite a target.  If a target exists (depending on the situation), I may abort the script and send an email notification or overwrite the file.  The --backup seems like a good option if it is not known if there are going to be possible duplicates or know if it is ok to overwrite.

LHammonds

---

