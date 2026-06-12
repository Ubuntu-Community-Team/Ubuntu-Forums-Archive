---
title: "Measures of system inspection"
date: 2017-08-01
forum: Security
---

### Post by schnuckenack2 on 2017-08-01
Hello,

what measures of inspection are available for the purpose of monitoring what action is going on on your system regarding potential (network related, but not only) security issues, detecting suspicious activity, etc.

Like: change of important files; if something was changed: find out by what process; find out, what processes do, etc..

I only know of 

```
lsof -i
```

Thank you very much

---

### Post by Habitual on 2017-08-01
> **schnuckenack2 said:**
> Hello,

what measures of inspection are available for the purpose of monitoring what action is going on on your system regarding potential (network related, but not only) security issues, detecting suspicious activity, etc.

Like: change of important files; if something was changed: find out by what process; find out, what processes do, etc..
I use ```
sudo lsof -p <pid> | less
```on occasion.
And ```
sudo netstat -putan
```

"Security Issues"?

---

### Post by TheFu on 2017-08-01
I use full system monitoring, since the first thing that will happen when someone takes over a system is usually they will increase the system load.  Hourly, daily, weekly, monthly graphs show that stuff easily, but you have to have them from the system running normally for a few months first.

There are lots and lots of different sorts of monitoring tools.  Watching the network is important, but not enough.  Watching disk usage, CPU, RAM, even thermal values help.  When any of these things appear out of place, it is time for more detailed research.  Logwatch will help track issues and changes.  Nagios or cacti or munin or sysusage will alarm and graph things.

Daily, automatic, versioned backups are the most important security tool that I have.  If a system backup is normally 20MB a day and it becomes 500MB on a Tuesday ... huh?  I've got some research to do.  With a clone or mirrored backup, I don't know that and don't have the older files to see what actually changed.  Also, rsync doesn't capture ownership/groups/permissions as they changed over time.  There are also tools that take a metadata snapshot of all files at a specific point - I don't use them, so don't remember their names. Sorry.

Most of these things require manual configuration to be of any use after install.  

lsof is a great command.
fuser is another if you want to see which process is using a resource (port, file).

If you use SE Linux or apparmor more than the default settings, you can get a pretty good idea of what is happening on your system - for the cost of larger logs and a little overhead.  If you have a process that you believe is actively being used by hackers, then you can attach to the running process with strace (this is like the truss cmd on Solaris).

A fun little article about what happens when a Linux server is placed on the internet with bad security - on purpose: [https://sysdig.com/blog/fishing-for-hackers/](https://sysdig.com/blog/fishing-for-hackers/)

There are similar stories like these out there for all the different webapps, if you care to look.  Lots and lots of php webapps, but some ruby, python, perl, java, and cgi stuff too.

And don't forget the sticky threads at the top of the Ubuntu Security subForum here. Lots of stuff there about IDS/IPS systems, if you want to protect a network and not just 1 system.

---

### Post by deadflowr on 2017-08-01
And moved to the *Security* sub-forum

---

### Post by schnuckenack2 on 2017-08-03
Wow, thank you for your great responses so far. :)

And sorry @deadflowr

---

