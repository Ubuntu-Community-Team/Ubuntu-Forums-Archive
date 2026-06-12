---
title: "CRON doesn't execute .sh script, which works from when executed from terminal"
date: 2016-01-04
forum: Server Platforms
---

### Post by toni12 on 2016-01-04
So I have a .sh script that executes .py script

```

#!/bin/bash
# Run main.py program


python /main.py > /bulkcat.log

```

And my crontab -e looks like this:

```

*/5 * * * * /runpyscript.sh

```

Both main.py and runpyscript.sh are located in / directory

When I run "runpyscript.sh" from terminal, it works. But CRON doesnt seem to execute that script.

I made both files executable with "chmod +x main.py" and "chmod +x runpyscript.sh"

So what might be a problem here?

---

### Post by ian-weisser on 2016-01-04
Use full paths. Example: ''/usr/bin/python" instead of "python"

If your main.py requires any enviroment variables, you must explicitly declare them.
Cron has permission to your use your files, but does not run in your environment. It doesn't know your ~/ or DISPLAY: or PATH or CWD.

Check /var/log/syslog for cron errors.
If they exist, redirect the error output to a file:    */5 * * * * /runpyscript.sh > /tmp/cron.debug.output 2>&1

Did you really put runpyscript, main.py, and bulkcatlog in / (root)? That's unusual.
Or did you perhaps put them in your /home (~/)? If /home, use the full path. Cron doesn't know where ~ is.

---

### Post by toni12 on 2016-01-04
Ive modified crontab file and now it looks like this:

I got the PATH from "env" command

```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
SHELL=/bin/bash


*/5 * * * * cd /; ./runpyscript.sh.> /tmp/output.log 2>&1

```

And here is the error from CRON.

```

/bin/bash: ./runpyscript.sh.: No such file or directory

```

---

### Post by darkod on 2016-01-04
You have a trailing dot after the .sh that is in effect making it look for a file named .sh.

---

### Post by toni12 on 2016-01-04
Okay, now my crontab looks like this:

```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
SHELL=/bin/bash


*/5 * * * * /runpyscript.sh > /tmp/output.log 2>&1

```

And this is again the same error

```

/bin/bash: /runpyscript.sh: No such file or directory

```

---

### Post by matt_symes on 2016-01-04
Hi

Is runpyscript.sh in your root directory ? It doesn't look like it as cron cannot find the file there.

What does this return ?

```
file /runpyscript.sh
```

Use the full paths to the script everywhere.

Kind regards

---

### Post by darkod on 2016-01-04
Where is the script? Is it like it says, immediately in /? Because if it's in the root user default home folder it would be /root for example.

Make sure the script is there. And there is little need to put scripts in / and lots of confusion. Make a /scripts folder for example, or something like that. Then the script to run would be /scripts/runpyscript.sh

Also if using home folder or relative paths, make sure you get it right in which user home the script is, and which user crontab are you using... You probably know that:
```
crontab -e
```

opens up your crontab, but
```
sudo crontab -e
```

open up the root user crontab. If only root has access to the folder/script, you need to put it in its crontab, not in yours. Also if the script does actions that need sudo rights, you need to use the root crontab because only then it will run as root.

---

### Post by The Cog on 2016-01-04
I don't think you should try setting path variables on the crontab file. It is not a script, it's a configuration file. 

Any further setting up should be done in the runpyscript.sh file, e.g.
```
/usr/bin/python /main.py > /bulkcat.log
```
Or if you want to make it more long-winded:
```
#!/bin/sh
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
export SHELL=/bin/bash
/main.py > /bulkcat.log
```

---

### Post by lukeiamyourfather on 2016-01-04
Files run by cron can't have an extension. For example runpyscript.sh should just be runpyscript with no extension. Don't ask why because I don't know. I'm sure someone did this for a reason but it sure is annoying.

---

### Post by darkod on 2016-01-04
> **lukeiamyourfather said:**
> Files run by cron can't have an extension. For example runpyscript.sh should just be runpyscript with no extension. Don't ask why because I don't know. I'm sure someone did this for a reason but it sure is annoying.

Not true. The file/script you are running can be called what ever you like... I have .sh in root crontab and it's working perfectly.

---

### Post by lukeiamyourfather on 2016-01-04
I'm glad it's working for you but for world plus dog the file names with extensions seem to be a problem for cron. From what I can gather under the hood cron is using run-parts which has this in the manual. Note periods are not valid characters (and thus extensions are not valid).

> If neither the --lsbsysinit option nor the --regex option is given then the names must consist entirely of ASCII upper- and lower-case letters, ASCII digits, ASCII underscores, and ASCII minus-hyphens.

If you search around there are many people discussing this for both Ubuntu and Debian. Here's the manual that the quote above came from.

[http://manpages.ubuntu.com/manpages/vivid/man8/run-parts.8.html](http://manpages.ubuntu.com/manpages/vivid/man8/run-parts.8.html)

Next time I'm at a Linux machine I'll give it a shot. Maybe things have changed.

---

### Post by darkod on 2016-01-04
Just as an example, the below works perfectly. So, I don't know about your quote, I haven't even looked for naming limitations to be honest... I just selected the name and it works. And it's not the only .sh script I have crontabbed...

```
0 23 * * * /root/scripts/daily-rsync-web.sh
```

---

### Post by steeldriver on 2016-01-04
Is there maybe some confusion here between **files **in /etc/cron.d and the /etc/cron.{hourly,daily,weekly} and commands (which may be script **files**) in root's or users' **crontabs **

It's the former that must conform to the run-parts naming conventions, I think

---

### Post by matt_symes on 2016-01-04
Hi

> **steeldriver said:**
> Is there maybe some confusion here between **files **in /etc/cron.d and the /etc/cron.{hourly,daily,weekly} and commands (which may be script **files**) in root's or users' **crontabs **

It's the former that must conform to the run-parts naming conventions, I think

This is bang on the money.

Kind regards

---

### Post by 1clue on 2016-01-04
FWIW cron will never have access to your DISPLAY.  The only exception I can think of is if you set up your own server just for the cron job in order to handle apps that require a gui, like xvfb. 

Making a cron job depend on a logged-in session is bad voodoo, don't do it.

---

### Post by lukeiamyourfather on 2016-01-05
> **steeldriver said:**
> Is there maybe some confusion here between **files **in /etc/cron.d and the /etc/cron.{hourly,daily,weekly} and commands (which may be script **files**) in root's or users' **crontabs **

It's the former that must conform to the run-parts naming conventions, I think

Yes, indeed. My bad on that one.

---

### Post by The Cog on 2016-01-05
> **1clue said:**
> FWIW cron will never have access to your DISPLAY.  The only exception I can think of is if you set up your own server just for the cron job in order to handle apps that require a gui, like xvfb. 

Making a cron job depend on a logged-in session is bad voodoo, don't do it.

It is bad voodoo, but the display is accessible if you are logged on. This works and is mildly annoying:
```
* * * * * /usr/bin/pgrep xeyes || DISPLAY=:0.0 /usr/bin/xeyes
```

---

