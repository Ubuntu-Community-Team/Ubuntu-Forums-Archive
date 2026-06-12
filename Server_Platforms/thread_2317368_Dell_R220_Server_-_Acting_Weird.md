---
title: "Dell R220 Server - Acting Weird"
date: 2016-03-15
forum: Server Platforms
---

### Post by soamz on 2016-03-15
HI, I purchased a new Dell R220 2 months and it acts as one of our web server. 
I monitor its uptime through 2 monitoring tools. 
Since last 10 days, Im getting emails in every 5 mins at random hours, that server is down, then again in 2 mins, server is up.


Whats the command to check in terminal the health of the server and the full detailed log, so I can see whether the server is actually doing something, or whether my network cable is faulty or the switch from where its connected. 

I just need to see first, whether the server is rebooting on its own or what. 
Whats the command ?

---

### Post by nerdtron on 2016-03-16
>  Since last 10 days, Im getting emails in every 5 mins at random hours, that server is down, then again in 2 mins, server is up. 

Did the server really go down (or rebooted itself)? 

You better have monitoring in place for CPU, and RAM. You'll need to see what is happening on the server during those downtimes. 
You can also check the /var/log/messages on which you'll see system log messages. I'm guessing the web server is running out of memory and then force kills the apache process to make itself stable again.

That's just my guess since you did not specify the server specs and how much load your web server handles.

And these links may help you:
[http://www.tecmint.com/command-line-tools-to-monitor-linux-performance/](http://www.tecmint.com/command-line-tools-to-monitor-linux-performance/)
[http://linoxide.com/linux-shell-script/shell-script-check-linux-system-health/](http://linoxide.com/linux-shell-script/shell-script-check-linux-system-health/)

---

### Post by wellsilva-email on 2016-03-16
Hi soamz,

Check with the "uptime" how long the server has been running. If there was a reboot, it will be less than one day. By reading the output of the "last" command you will find the list of reboots and crashes.

If your hardware really rebooted, you can check the /var/log/syslog files to get a clue of what made the system go down. The file has timestamps, so you will see the messages before the time skips to the next initialization.

Take a look at this first, see if you it brings you to a possible cause and let us know.

Peace.

---

