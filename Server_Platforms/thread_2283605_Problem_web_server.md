---
title: "Problem web server"
date: 2015-06-23
forum: Server Platforms
---

### Post by Sapph1r3 on 2015-06-23
I set up websites on a web server and lately the websites will become unavailable.
I usually access the server using webmin and when I check that, it loads but as soon as I try to log in it says it is unavailable.
Shares on the server are accessible, however no websites are.
On occasion I am able to access it via putty, but am not well versed in this to locate the problem (and frankly am terrified that something will go terribly wrong)
I cannot check at the moment, but believe we are using Ubuntu 14.04 LTS
Any help will be greatly appreciated as I needed to reboot a few days in a row.

---

### Post by darkod on 2015-06-23
So let me see if I understand this right. The webmin page loads but when you enter the login details it can't login?
Also with ssh (putty) you can access all the time or only sometimes?

If ssh access is not working too, check network connectivity first. Is this a hosted machine? Ask the provider to check network connectivity is working.
If ping is not blocked, test ping few times and watch if there are timeouts or lost packets.

Once you are sure you have stable connectivity you can continue troubleshooting. By the way, using webmin is not such a good idea. You should try administering linux servers by ssh.

---

### Post by Sapph1r3 on 2015-06-23
Thanks for the quick response.
Webmin loads up with the login screen and as soon as I enter my details it looks like it will log in, but instead gives me the webpage is unavailable.
This is the same for other websites.
I am always able to get a ping response from the server.
I don't completely trust ssh because I tried a restart via that and nothing happened (asked tech at centre where server is housed)
I had to request a reboot as I wasn't able to access it remotely at all.
Webmin is really the only way I know my way around this server.
I get lost with command line interfaces.

---

### Post by Lars Noodén on 2015-06-23
> **Sapph1r3 said:**
> Webmin is really the only way I know my way around this server.
I get lost with command line interfaces.

The big down side to webmin is that when the web server or something it depends on is down, you have no access and someone has to have access to the shell anyway to fix it.  If you have helpers, they can use webmin but the person with the ultimate responsibility is going to need to use the shell from time to time.  But since the shell is so flexible and powerful why not start with it early on?  That's some of the rationale I went through a long time ago myself.  The shell quickly becomes easy to use in addition to being powerful and flexible.  And there are many people here that can help you at just about any task at any stage of the learning curve.  It's worth the small investment of time since you can do so much with it and we can help you with it if you are interested.

---

### Post by mastablasta on 2015-06-23
it could be some network overload. hard to say without much data. 

in SSH you can reboot by 

sudo reboot

or sudo shutdown -r now

in command line you basically need only a few basic commands to do the repair and some minor work. or at least to troubleshoot the problem.

---

### Post by SeijiSensei on 2015-06-23
Webmin runs its own web server and doesn't use Apache or nginx at all.

Are you sure apache is running?  After you fix the problem so you can log in with SSH, type the command "sudo service apache2 restart" and enter your own login password when prompted.

Having SSH access to a remote server is pretty much a necessity for any sort of maintenance.

---

### Post by darkod on 2015-06-23
Set aside that you have more trust in webmin than ssh (which should be the other way around really), now webmin is not working and the only troubleshooting you can do is using ssh, right?

I guess you could start looking at logs first, like the general syslog and the apche error log. They should be:
```
sudo nano /var/log/syslog
sudo nano /var/log/apache2/error.log
```

Few basics about the nano editor:
Inside you move page up/down with Ctrl Y / Ctrl V.
Without making changes you exit with Ctrl X.

You can also check logs with tail -f /path/filename, but usually that shows only the few last entries (which in some cases is enough). nano will open the whole file and you can check varios data going up/down.

I'm not sure if this could be a result of denial of service attack. Do you have a firewall protecting the machine? Either from the provider or iptables on the server.

---

### Post by Lars Noodén on 2015-06-24
> **SeijiSensei said:**
> Webmin runs its own web server and doesn't use Apache or nginx at all.

Thanks.  It's been much longer than I thought since I last looked at it.  I see from the project page that it has improved a lot and perhaps that is one of the improvements or  I just plain remembered wrong that it used to use Apache.  

> **darkod said:**
> Set aside that you have more trust in webmin than ssh (which should be the other way around really), now webmin is not working and the only troubleshooting you can do is using ssh, right?

I guess you could start looking at logs first, like the general syslog and the apche error log. They should be:
```
[s]sudo nano /var/log/syslog
sudo nano /var/log/apache2/error.log[/s]

```


Using nano risks changing or deleting all or part of the logs because it is an editor.

Actually, @Sapph1r3 if you are in the group **adm**, the tool [less](http://manpages.ubuntu.com/manpages/trusty/en/man1/less.1.html) could be used instead.  The **adm** group has read-only access to the Apache2, and other, logs and  [less](http://manpages.ubuntu.com/manpages/trusty/en/man1/less.1.html) is read-only itself.  
```

less /var/log/syslog
less /var/log/apache2/error.log
```

---

### Post by Sapph1r3 on 2015-06-24
Yes, there is a firewall between the machine and the outside world.
It is actually a physical device and a very good one at that.
The other servers behind it are experiencing no issues, granted they are Windows servers.
I had a look at the Apache error log and noted this line:
exit signal Segmentation fault (11), possible coredump in /etc/apache2
Which I am trying to decipher.
I have just been told that when I was off sick a similar incident occurred where first Apache stopped (was restarted), then MySQL (was restarted), then the box fell over (figuratively)

---

### Post by TheFu on 2015-06-24
Cannot help with this problem, but I can recommend a book to remove the webmin dependence:
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Webmin is like a drug - at first it feels better, but over time you become a junky. Kick the habit sooner to avoid having those deep socket eyes that all junkies get. ;)

Also - that single error isn't helping much. We'd need to see a few lines around it and any errors/warnings from other system logs too.

---

### Post by Sapph1r3 on 2015-06-30
Thanks for that link, I will have a look at it.
I went down to the server and tried working on it physically.
I had a problem doing updates, so I tried via webmin (only to see if I get errors, which I did)
I have downloaded a few log files to try to make sense of it.
The error during updates was Segmentaion fault (core dumped).
I have been doing searches, but have yet not found any help close to what I have experienced.

---

### Post by TheFu on 2015-06-30
If the web server process is dependent on the DB being available, then restart order is very important.  Start the DB first, wait 5-10 sec, then start apache.

If apache is crashing, using core dump analysis tools to see WHY the process is crashing would be my next step - well - after I've gone through all the monitoring, alarming and log files.

---

