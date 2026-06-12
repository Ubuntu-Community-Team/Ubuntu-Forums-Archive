---
title: "How do I debug an Upstart job?"
date: 2012-03-26
forum: Server Platforms
---

### Post by Deecie on 2012-03-26
Hello,

I'm administrating a small elastic cluster of servers and I'm trying to set a service to run automatically.

It's a twisted app which should be run with the twistd command-line app, which automatically forks to background.

I've created a question on SuperUser about this issue but I didn't get any responses: [http://superuser.com/questions/403847/how-do-i-debug-an-upstart-job](http://superuser.com/questions/403847/how-do-i-debug-an-upstart-job)

As mentioned there, when I run 'sudo start jobname' and then run 'initctl list', I see this for my job:

```
jobname start/killed, process 616
```There's nothing about it in /var/log/syslog. I even just replaced my upstart script with a call to a bash script that just cats a line to a file and it didn't work. The upstart script is very simple:

```

start on runlevel [2345]
stop on runlevel [!2345] 
expect daemon 
exec /usr/bin/twistd -y /path/to/my/tac/file

```Can someone point me in the right direction here?

---

### Post by iiz on 2012-03-26
Well. If all you are after is getting it to exec then you could use an upstart job, which you've chosen to do.

For upstart you need to please your JOBNAME.conf file into:

```
/etc/init/
```

I'm not sure if upstart searches for files recursively in the init directory. You could try without it being in the collector folder.

It could be possible your twistd daemon is misconfigured and dying on you prematurely, have you tried running that command directly from console? Maybe you don't have a main loop in the code so when the file is executed it exits with a status of 1 since it didn't encounter errors? I'm no expert on twistd, nor have i ever heard of it.

If the app runs normally when you call it from command line then I would say try out rc.d, the old school way.

Dump a shell script to execute the twistd app into /etc/init.d/ and then run:

```
update-rd.d scriptname defaults
```

That should apply the proper symbolic links to the different run level dirs in /etc/

I maybe have misunderstood your question entirely, if so I'm sorry. Just be patient I'm an old fart, but i know my stuff :)

P.S. Just found this nice little guide on Upstart if you're interested: [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

