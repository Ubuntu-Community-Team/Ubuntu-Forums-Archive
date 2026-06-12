---
title: "Best Practice for Starting a Django Site at Boot"
date: 2009-06-12
forum: Server Platforms
---

### Post by vanderkerkoff on 2009-06-12
Hello everyone, I'm on Ubuntu 8.0.4 and running a number of django sites with nginx and fastcgi.

I've installed nginx and mysql with aptitude so at boot time that will start up fine, I've used the default config files.

What I need to do now is to start the django applications as a non root user at boot time.

The command to start each of the applications is very simple.

python /pathtoproject/manage.py runfcgi method=prefork minspare=1 maxspare=1 socket=/pathtosockets/projectname.sock pidfile=/pathtopidfiles/projectname.pid

I've done some reading and there seems to be numerous ways of achieving starting this process at boot time, but I was wondering what you would consider as best practice?  It has to run after nginx and mysql have started up.

Also, how do you get it to run as a different user?  

Any help, greatly appreciated.

---

### Post by vanderkerkoff on 2009-06-12
ok, I've got a working solution up and running

in my /etc/rc.local file I've got this at the end

# By default this script does nothing.
su user_name -c /pathtoproject/bootstartdjango.sh
exit 0

and pathtoproject/bootstartdjango.sh looks like this

#!/bin/sh
/pathtoproject/manage.py runfcgi method=prefork minspare=1 maxspare=1 socket=/pathtosockets/projectname.sock pidfile=/pathtopidfiles/projectname.pid

I've rebooted and it all works swimmingly, can anyone see any problems with doing it like that?  Some people were saying to put an ampersand after the call to the bash script in the /etc/rc.local file, do I need to do that if I'm calling in another script and not actually writing a script in the rc.local file?

Any help, greatly appreciated.

---

