---
title: "Server appears to be rebooting"
date: 2011-04-06
forum: Server Platforms
---

### Post by fizgig on 2011-04-06
I have 10.04 server running offsite where I can still ssh into it.  It's plugged into a UPS just in case there's any power outage which I understand has not happened.

I also have one thing autostarting on startup - a ruby script which is the sole reason for the server's existence.  I want to run it in a screen instance so my /etc/rc.local looks like:

```
#!/bin/sh -e
sudo -u administrator /home/administrator/ruby_script.sh
exit 0
```

the contents of ruby_script.sh are:

> #!/bin/bash
cd /home/administrator/ruby_script
screen -d -m -S ruby_script ./the_script.rb


All seems ok since the ruby script is running after I turn the computer on.  What's odd is that a couple of times now I have logged into the computer to see that the script is no longer running and, further, the server appears to be rebooted since "uptime" indicates only 5 or so hours of uptime but the server was turned on a few weeks ago.

I guess I have two questions:
1.  Why is the server rebooting in the first place?  How can I find out?
2.  If it is rebooting, why isn't the script restarted?

Thanks for any help.

---

### Post by matt_symes on 2011-04-06
Hi

What do your logs say ? 

The first place i would look is at the files in /var/log/ to try to identify if it actually is a reboot. 

If it's rebooting, maybe it's rebooting because of a hardware issue ? Can you leave an ssh connection open to it, keep it alive and check for connection resets ?

You can use ksplice to install kernel updates without rebooting. It's in the repositories.

I could well be totally off the mark here that is why the first place i would check is the logs especially as it's not restarting your script.

Kind regards

---

### Post by fizgig on 2011-04-06
There are a ton of logs in /var/log

Any place I should look?

---

### Post by fizgig on 2011-04-06
Using the uptime command, it looks like the server rebooted at 1:32am this morning.

When I look in /var/log/messages, I do indeed see a bunch of startup-looking stuff starting at 1:32:40.

Trouble is, the first line before the startup stuff at 1:32:40 is at time 6:35:58 of the previous day - about 19 hours before the reboot occurred.

There are no error messages or any indication as to why the reboot happened at 1:32:40 this morning that I can tell.

---

### Post by matt_symes on 2011-04-06
Hi

In the first instance the ones i would check are

```
/var/log/messages
/var/log/syslog
```

and maybe

```
/var/log/kern.log
```

Both the current and older versions.

Kind regards

---

