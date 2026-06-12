---
title: "Webmin bandwidth no longer being logged after upgrade to Ubuntu Server 9.10"
date: 2010-03-30
forum: Server Platforms
---

### Post by nimrodwebdesign on 2010-03-30
I just spent ages trying to find information about why my Webmin Bandwidth Monitor stopped logging after I upgraded my server install to 9.10 last week. 

I can't understand why I couldn't find any information about it anywhere, but I eventually managed to work it out. So here is what the problem was...


It seems that syslog is not longer used, it's been replaced by rsyslog. So the changes to /etc/syslog.conf that Webmin made (and remade after I turned the monitoring off and on again) were useless.

To fix this all I had to do was create the file /etc/rsyslog.d/bandwidth.conf (you can call the file anything you like as long as it ends in *.conf*, because the main *rsyslog.conf* file includes anything in the *rsyslog.d* directory ending in *.conf*) and put this in it:

```
kern.=debug		-/var/log/bandwidth
```

Note: The advantage of putting this in a new file rather than modifying an old one is that you won't lose it (or have to merge them) if a later upgrade changes an existing config file.


Then you just need to restart the rsyslog server by running the following command:

```
sudo service rsyslog restart
```


And you should be back in business.


Another Note:

This is replicating **exactly** what webmin put in the syslog.conf file, so it's doing the exact same thing.

It's not ideal though because that will log any message that is debug level (which is what the webmin iptables rules use), not just messages from iptables, it will also log all the iptables data to several other log files (syslog, kern & debug), which is just silly.

You can fix that by using the following lines instead:

```

:msg,contains,"BANDWIDTH" -/var/log/bandwidth
& ~

```

The first makes it only log lines that contain the word *BANDWITH*, which the Webmin iptables rules use as a prefix.

The second discards those lines so they won't be logged anywhere else.

One other thing to do. Instead of calling the file *bandwidth.conf* you should call it *10-bandwidth.conf* (well any prefix number below 50 would do). This will make sure our file is used before the *50-default.conf* file, which means the iptables rows are discarded before they are logged to the other log files.


Yet another Note:

It looks like rsyslog can handle some form of expressions that would allow you to *and* the debug level and contain filters together, but I couldn't get it to work with the tiny amount of rubbish documentation they provided. So if you can get that to work it will probably make things a bit faster because it won't have to parse every syslog message, only the debug level ones. Post it here if you do.


And finally, thanks to this post for the information on limiting the output rows and discarding them: [http://www.uluga.ubuntuforums.org/showthread.php?p=8969926](http://www.uluga.ubuntuforums.org/showthread.php?p=8969926)


I hope that helps someone.

Colin =)

---

