---
title: "Backup Script trouble"
date: 2012-10-12
forum: Server Platforms
---

### Post by X1R1 on 2012-10-12
Hi all,

I wrote a very small and simple script to stop a service, backup a folder, copy it to a remote location via scp and then start the service again.

Everything works except for one thing, the service does not want to start for some reason, I have to manually ssh into the server and execute the comand to start it.

Here is the script, like I said, nothing fancy:

```
#!/bin/bash
FILE=openbravo$(date +"%d-%m-%y").tar.gz
/etc/init.d/openbravo stop
cd /opt
tar cvzf $FILE OpenbravoERP-3.0
scp $FILE 123.123.123.123:/REMOTE/LOCATION
/etc/init.d/openbravo start
```

If I input the last command on the command line it works no problem, its only when the scheduled job runs that I run into this issue.

I have also tried putting the scp command at the end to see if it made any difference, but same problem.

How can I debug this?

thanks a lot for the help!

ps: I checked the scp command above and its completing succesfully (I can see the file on the remote location).

---

### Post by koenn on 2012-10-12
does the entire script works when you run it manually ?
if not, what does it say ?

Dou you suppress output from cron ? It usually logs or sends mail if a cron job produces output, such as an error msg. You want to see those.

---

### Post by koenn on 2012-10-12
wild guess:

the '/etc/init.d/openbravo start' is not executed because your script hangs on the preceding command; 

therefore : assume the script fails on 'scp $FILE ... ... ' fails, possibly  because cron runs as root and root can not logon to the target server.

---

### Post by LHammonds on 2012-10-12
What user are you scheduling this script to run as?

Can the service only be shutdown using root privileges?

** EDIT #1:** Also, when using scripts, be sure to include the FULL path to everything...never assume a current working directory.

e.g. Full path for the archive file in your FILE variable.

It would also be wise to checked the return code of any command you run so you can handle the exceptional case of when it doesn't work.  Did the tar command work?  Did the copy command work?  Did the service actually stop...did it actually start?  These are all things you really need to know when automating such tasks.  I would include a bit of code to include sending email notifications whenever (not if) it fails.

**EDIT #2:** I include a path in my crontab schedule to help avoid these problems...but I still specify full paths whenever I can.  [LOOK HERE]("http://www.hammondslegacy.com/forum/viewtopic.php?p=261#p261")

LHammonds

---

### Post by steeldriver on 2012-10-12
I agree it's likely a environment (PATH) thing - you may need to give a path to start/stop as well  (which are also commands - in /sbin) not just the 'service' command (in /usr/sbin) - see this post

[http://ubuntuforums.org/showpost.php?p=12093594&postcount=4](http://ubuntuforums.org/showpost.php?p=12093594&postcount=4)

---

### Post by HermanAB on 2012-10-14
Howdy,

Check the paths in the /etc/init.d/openbravo script and expand them all.  Cron runs with a very limited environment setup.

---

### Post by X1R1 on 2012-10-15
Thanks for all the tips!

Im going to try an answer every post, here I go:

@koen 1. Yes it works when I run it manually (every part of the script does)
2. No I haven't suppressed any output from cron. The only part where I found cron output was in syslog, but nothing relevant, only stuff like this:

```
Oct 15 12:17:01 openbravo CRON[18181]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 12:25:01 openbravo CRON[18361]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 15 12:35:01 openbravo CRON[18544]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 15 12:45:01 openbravo CRON[18728]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 15 12:55:01 openbravo CRON[18947]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 15 13:05:01 openbravo CRON[19132]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 15 13:15:01 openbravo CRON[19316]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 15 13:17:01 openbravo CRON[19326]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

No idea what any of that means.

Also, regarding your wild guess, I also tought about that and switched the commands order, but same result, the file in fact gets copied succesfully.

@LHammonds

1. Script is scheduled to run as root and I always stop the service using sudo (if im not root at that time) so no problems there. I will also try and improve the script to check the return codes and make the script a little more professional.

regarding your EDIT#1 part, I just implemented this, lets see if it makes any difference.

[B]I also added a PATH to the crontab file as suggested by you and @steeldriver (I included the PATH on your webpage)

I have a question regarding this...am I opening a security hole while adding non-default paths to a root crontab?[/B]

@HermanAB the openbravo script in fact shutdowns a couple processes:

```
start() {
        service openbravo-postgresql start
        service openbravo-tomcat start
        service apache2 status >/dev/null 2>&1 || service apache2 start
}

stop() {
        service openbravo-tomcat stop
        service openbravo-postgresql stop

```

thanks all! hopefully this changes will make it work

---

### Post by LHammonds on 2012-10-16
> **X1R1 said:**
> 
[B]I also added a PATH to the crontab file as suggested by you and @steeldriver (I included the PATH on your webpage)

I have a question regarding this...am I opening a security hole while adding non-default paths to a root crontab?[/B]

I don't think anything there is non-standard.  All I did was "echo $PATH" while logged in as root and copied the same path into the crontab...thus ensuring that whatever I type at the console will work in crontab.  It is not absolutely necessary but if adding the path to crontab and the script starts to work, then it is obvious that the problem is in the script...no using full paths (e.g. relative paths).

If the path variable allows it to work, I recommend modifying your script so that it will work without the presence of the path variable in crontab.

Regarding security, it could be an issue if somebody places a man-in-the-middle program with the same name in your path (before it finds the real program) or it can be a version/name issue where your script is expecting a certain program but because it was not called with the full path, could get a completely different program that is found in the path with the same name.

Use relative paths can help your script be a bit more portable but always try to use the full path whenever you can.  The full path can include variables to help keep it portable such as ${TMP}/tempfile.txt or ${HOME}/myfile.txt

But regardless of any proposed solutions, you need to find out exactly why the script is failing and fix that particular problem (and not leave a bunch of failed test solutions in place when finished).

For examples on checking return codes and handing errors, you can look at the same link I gave earlier.  I have several scripts there that have all kinds of helpful code to handle all kinds of scenarios.  Just pick-n-choose what you need for your scenario.  Many of my scripts are VERY simple at its core...maybe a handful of commands but the bulk of the scripts are there to handle errors and logging.

LHammonds

---

### Post by Alekz_ on 2012-10-16
Best way to discover what's going on is to put some output for commands on your startup script..

About your profile environment.. If you have a .bashrc or .bash_profile for root you can load it on you backup script..

Just put something like this:

> ./root/.PROFILE_SCRIPT

Assuming that /root is your root's $HOME and that it's scheduled into root's cron

---

