---
title: "Apache Daemon"
date: 2008-06-18
forum: Server Platforms
---

### Post by Mosaab on 2008-06-18
I installed Apache 2.2, now as I can see from running ps command that the process name is apache2 and not httpd. is that normal?

when ever I try to stop or start or restart the process by:
apache2 restart 
it gives me the info page of apache.

when I run:
apache -k restart (for example) I get:
apache2: bad user name ${APACHE_RUN_USER}

What is this ? how can I restart the daemon?

and when I want to run the sample page in apache from localhost or anywhere else from firefox is says "timeout"!?

what can I do?

thanks..

---

### Post by Mosaab on 2008-06-18
just to let you know, when I type [http://localhost](http://localhost)  it works ... but it doesnt work with the loopback IP ?!

---

### Post by Mosaab on 2008-06-18
I read in some website that I have to run the following (I Dont know why!):
apache2ctl restart.

but even this gives me this message:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd not running, trying to start

and the apache2 daemon is running, is httpd also supposed to be running?

---

### Post by unixbills on 2008-06-18
Check /etc/apache2 and /etc/apache2/conf.d conf files for "Allow".  You probably have something like "Allow from localhost".  Make it "Allow from All" for testing.  So for example I am running nagios on apache2 so I have "Allow from All" in /etc/apaches2/conf.d/nagios.conf.

---

### Post by Mosaab on 2008-06-18
I cant ping 172.0.0.1
but I can with ping localhost !!!

---

### Post by unixbills on 2008-06-18
127.0.0.1 not 172.

---

### Post by Poleh on 2008-06-19
sudo /etc/init.d/apache start|stop|restart|reload is what you're looking for

---

### Post by Mosaab on 2008-06-19
> **unixbills said:**
> 127.0.0.1 not 172.

OOOPS :( it works now.. Thanks lol

but still I cant start apache with $etc/init.d/apache start

there is a file called apache2 ... and I tried to the same $etc/init.d/apache2 start  but it gave me this:


Usage: apache2 [-D name] [-d directory] [-f file]
               [-C "directive"] [-c "directive"]
               [-k start|restart|graceful|graceful-stop|stop]
               [-v] [-V] [-h] [-l] [-L] [-t] [-S] [-X]
Options:
  -D name            : define a name for use in <IfDefine name> directives
  -d directory       : specify an alternate initial ServerRoot
  -f file            : specify an alternate ServerConfigFile
  -C "directive"     : process directive before reading config files
  -c "directive"     : process directive after reading config files
  -e level           : show startup errors of level (see LogLevel)
  -E file            : log startup errors to file
  -v                 : show version number
  -V                 : show compile settings
  -h                 : list available command line options (this page)
  -l                 : list compiled in modules
  -L                 : list available configuration directives
  -t -D DUMP_VHOSTS  : show parsed settings (currently only vhost settings)
  -S                 : a synonym for -t -D DUMP_VHOSTS
  -t -D DUMP_MODULES : show all loaded modules 
  -M                 : a synonym for -t -D DUMP_MODULES
  -t                 : run syntax check for config files
  -X                 : debug mode (only one worker, do not detach)

---

### Post by Mosaab on 2008-06-19
When I type: &apache2 -k restart

it gives me:

apache2: bad user name ${APACHE_RUN_USER}

---

### Post by gtdaqua on 2008-06-19
```

sudo /etc/init.d/apache2 force-reload

```

---

### Post by BattMatt on 2010-09-01
I am having the same problems.  Apache, for whatever reason, will not start on reboot.  Nothing in the system, access, daemon, or apache2 logs indicates a problem.

When I try to run:

apache2 --restart

...it gives the following error, much like you encountered:

apache2: bad user name ${APACHE_RUN_USER}

I found that for whatever reason, the apache2 daemon isn't seeing the /etc/apache2/envvars file before starting up.  So here's what I have to do to get it started:

from /etc/apache2, sudo su
source envvars
apache2 --restart

...then it starts fine and stays up until the next reboot.

So the missing piece of the puzzle is, why doesn't it start on its own anymore, and how can we get it to do that again?

---

### Post by BattMatt on 2010-09-01
Without any errors being thrown up, this was tricky to diagnose, but it looks like a combination of two things solved it.  Why and how, I don't know, but maybe you'll get the same results.

I was running VirtualBox (Sun edition) and using pppoeconf to get pppoe on my internet connection (again, why these things relate, I have no idea):

1.  I found I had to keep recompiling vboxsvr on every reboot.  There was a solution that said to add vboxsvr to the end of the /etc/modules file.  Solved the recompile issue and was part of the apache2 not starting solution.

2.  pppoeconf changed my /etc/network/interfaces file unnecessarily.  Particularly, after commenting out the line it added: "provider dsl-provider", combined with step 1 above, my apache starts reliably after every reboot (so far).

Again, I have no idea how these things are related, but by breaking BOTH /etc/modules and /etc/network/interfaces, I was able to reproduce the apache problem.  By fixing BOTH (and only BOTH) of them, I was able to fix the apache problem.  Some crazy Voodoo magic going on...

---

