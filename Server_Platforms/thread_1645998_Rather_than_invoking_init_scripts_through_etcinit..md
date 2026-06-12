---
title: "Rather than invoking init scripts through /etc/init.d, use the service"
date: 2010-12-15
forum: Server Platforms
---

### Post by helix_r on 2010-12-15
I am trying to set up mysql on a stock 64bit ubuntu AMI (micro instance, ami-548c783d). I was following the [server guide mysql section]("https://help.ubuntu.com/10.10/serverguide/C/mysql.html").

So, I spin up a fresh instance, install glassfish successfully, and do the following using directions from the server guide:

1) [FONT="Courier New"]sudo apt-get install mysql-server[/FONT] [COLOR="Red"](no problem)[/COLOR]
2) [FONT="Courier New"]sudo netstat -tap | grep mysql[/FONT] [COLOR="Red"](yep, works.)[/COLOR]
3) edit the my.cnf to the correct bind-address [COLOR="Red"](no problem)[/COLOR]
4) [FONT="Courier New"]sudo /etc/init.d/mysql restart[/FONT] 

Upon #4, the restart, the command line _HANGS_ after the following response...

"[FONT="Courier New"]Rather than invoking init scripts through /etc/init.d, use the service utility, e.g. service mysql restart

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the restart utility, e.g. restart mysql[/FONT]"


Questions:

* It is not clear by the message whether or not mysql is actually being restarted or not. Is it just a suggestion?

* What is "service" and "upstart"? Isn't init.d good enough? Why the change?

* Why is this command hanging? Anyone else see this? 

Many Thanks for any help!

---

### Post by surfer on 2010-12-15
in order to stop/start a service since upstart (which uses the /etc/init.d/ scripts), run:
```
$ sudo service mysql-server start
```

---

### Post by CharlesA on 2010-12-15
It's been converted to an upstart job.

Use this to start/stop/restart:

```
sudo service mysql start|stop|restart
```

Ninja'd. :)

---

### Post by helix_r on 2010-12-15
Thanks, 

I terminated the failed init.d command and then tried "sudo restart mysql-server", it responded with "mysql start/running", no errors.

But when I use netstat to verify if mysql is running properly, I get nothing. I had set the bind-address to be my allocated elastic-ip address. Even after a reboot, still mysql isn't listening on ports. Although it is present in the ps -ax (as mysqld).

Does invoking init.d scripts while upstart is installed mess things up?

---

### Post by helix_r on 2010-12-15
Oops, I think it has something to do with the setting bind-address to my elastic-ip and my interpretation of what netstat is supposed to show. 

When switch bind-address back to 127.0.0.1, and "sudo restart mysql", I can see mysql in netstat.

---

