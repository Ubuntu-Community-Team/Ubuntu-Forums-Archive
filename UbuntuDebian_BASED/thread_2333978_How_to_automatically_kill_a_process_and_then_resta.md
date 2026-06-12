---
title: "How to automatically kill a process and then restart it in a time period?"
date: 2016-08-15
forum: Ubuntu/Debian BASED
---

### Post by jackofdiamond5 on 2016-08-15
Hello,

I have this program that is a terminal/console application. But sometimes it returns an unhandled exception, due to network connection errors, sometimes it restarts on it's own, but sometimes it doesn't. And this is no good. Is there any way to kill the process in a specific time period and then restart it (let's say kill the process on every hour, and then start it again)? Using a bash file, maybe? Or maybe a software? 

Thank you in advance!

---

### Post by SeijiSensei on 2016-08-15
Create the following script with an editor (as root with sudo).  Let's call it /usr/local/sbin/restart_app:
```

#!/bin/bash
killall -9 program_name
/path/to/program_name restart

```
Replace "program_name" with the appropriate name, and replace the second line with whatever command is used to start the program.

Next, mark the script executable
```
sudo chmod u+x /usr/local/sbin/restart_app
```

Finally, create a symbolic link to the script in /etc/cron.hourly:
```

cd /etc/cron.hourly
sudo ln -s /usr/local/sbin/restart_app

```

Now the script will be run each hour.  It kills all instances of program_name and restarts it.

"killall -9" is a bit aggressive.  Try "killall -15" first and see if that does the trick.  That tells the application to shut down cleanly.  -9 kills it off without any regrets.

If you're not sure exactly what the running application is called, use "ps ax" to list all the running processes and find it there.

---

