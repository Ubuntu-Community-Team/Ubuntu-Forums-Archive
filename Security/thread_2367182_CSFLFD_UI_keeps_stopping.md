---
title: "CSF/LFD UI keeps stopping"
date: 2017-07-26
forum: Security
---

### Post by slightly on 2017-07-26
I recently installed (3/4 days ago) CSF on Ununtu 16.04 via QuickBox.


At first, I am able to log into the UI. However it will randomly stop responding. The web page comes up as not responding and I have to restart lfd I order to be able to log in again. As far as I can tell the services are running it’s just the UI not working.


Before I log in successfully the process lfd UI is running. Once the webpage stops working the lfd UI process is no longer listed. The process displays like:
```
root 14448 0.0 0.2 97784 44368 ? S 06:00 0:00 lfd UI
```


An example of a change I tried was to add a test port 12345. I clicked Change and restarted csf/lfd via the UI button. I then logged back in and removed the port. This time when I pressed Change the web page stopped responding.
Sometimes I can make a couple of changes before the page stops responding. Other times I can’t make a single change.


I’m new to both CSF/LFD and Linux but am good at copying and pasting :)

---

### Post by Habitual on 2017-07-27
Never heard of any lfd "UI" but I suppose it had to happen. ;)
Actually, I have, in cPanel/WHM, but that's another "adventure".

Any hoos, [What do the logs say?]("https://wiki.debian.org/TroubleShooting#What_Does_The_Log_Say.3F") 
Look for and if present, at /var/log/lfd.log or possibly /var/log/lfd/lfd.log mebbe?

See anything like an error log? 
```
sudo find /var/log/ -iname '*lfd*.log' -type f
``` 
should show you something. Show us the output, if any and it doesn't have to be all of it, if it is lengthy use:
```
sudo find /var/log/ -iname '*lfd*.log' -type f | pastebin
```
or what ever. :) Pastebins are ubiquitous, no?

Let us know.

---

### Post by slightly on 2017-07-27
Unfortunately the lfd.log file is pretty sparse. It seems to start fine. I then make a change and when I click Change I get the page cannot be displayed.

```

[COLOR=#000000][FONT=Verdana]Jul 28 05:51:51 server lfd[1168]: daemon stopped
Jul 28 05:51:51 server lfd[1620]: daemon started on server - csf v10.16 (generic)
Jul 28 05:51:51 server lfd[1620]: Restricting syslog/rsyslog socket acccess to group [mysyslog]...
Jul 28 05:51:51 server lfd[1620]: CSF Tracking...
Jul 28 05:51:51 server lfd[1620]: IPv6 Enabled...
Jul 28 05:51:51 server lfd[1620]: LOAD Tracking...
Jul 28 05:51:51 server lfd[1620]: csf Integrated UI running up on port xxxx...
Jul 28 05:51:51 server lfd[1620]: Blocklist Tracking...
Jul 28 05:51:51 server lfd[1620]: Country Code Lookups...
Jul 28 05:51:51 server lfd[1620]: System Integrity Tracking...
Jul 28 05:51:51 server lfd[1620]: Exploit Tracking...
Jul 28 05:51:51 server lfd[1620]: Directory Watching...
Jul 28 05:51:51 server lfd[1620]: Temp to Perm Block Tracking...
Jul 28 05:51:51 server lfd[1620]: Process Tracking...
Jul 28 05:51:51 server lfd[1620]: Account Tracking...
Jul 28 05:51:51 server lfd[1620]: Webmin Tracking...
Jul 28 05:51:51 server lfd[1620]: Console Tracking...
Jul 28 05:51:51 server lfd[1620]: Watching /var/log/mail.log...
Jul 28 05:51:51 server lfd[1620]: Watching /var/log/secure...
Jul 28 05:51:51 server lfd[1620]: Watching /var/log/customlog...
Jul 28 05:51:51 server lfd[1620]: Watching /var/log/apache2/error.log...
Jul 28 05:51:51 server lfd[1620]: Watching /var/log/syslog...
Jul 28 05:51:51 server lfd[1620]: Watching /var/log/auth.log...
Jul 28 05:52:22 server lfd[1626]: Unable to retrieve blocklist BDE - Unable to download: read timeout

```

I made the change at approx 05:53:01 in the above log. You'll see there's not record at that time, this is the end of the log file. (That message about the blocklist comes up after each restart)

[/FONT][/COLOR]

---

### Post by Habitual on 2017-07-27
I don't know, sorry. 
Casual search of the interwebs suggests [csf.blocklists]("https://serverfault.com/questions/807405/lfd-is-unable-to-download-blocklist-rbn-cannot-remove-it-from-config") file, but I don't know where that is, 
Should be around /etc/lfd/ or /etc/csf/ something or other.

I'd find it without guessing by issuing
```
find /etc -name csf.blocklists -type f
```

And not sure this is related to the "UI" crashing, as this indication is much closer to the firewall. Theirs (the BDE) or yours, or both.
I suspect an improperly named, or formed entry in the csf.blocklists, but that's just a guess.

---

### Post by slightly on 2017-07-27
Thanks very much. I've commented out the BDE blocklist in csf.blocklists and restarted the service. I'll see if that makes a difference.

Edit: Sadly it happened again. At least that blocklist message doesn't come up any more.

---

### Post by slightly on 2017-07-28
One of the CSF staff on their forums advised an upcoming version would have some more verbose logging around the UI so that may help when it's released.

---

### Post by Habitual on 2017-07-29
Until you find and examine the csf "error log", I will just have to take your word for it. :)

---

