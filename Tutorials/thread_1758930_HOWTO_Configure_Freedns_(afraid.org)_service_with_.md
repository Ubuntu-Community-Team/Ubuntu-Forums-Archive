---
title: "HOWTO Configure Freedns (afraid.org) service with Inadyn (Lucid)"
date: 2011-05-15
forum: Tutorials
---

### Post by dentaku65 on 2011-05-15
As soon as you need that your PC will be reachable with the public IP address, you can setup a free dns service in order to reach your machine with a unique hostname upon the changes of the IP address from the ADSL connection.

I'm reporting that [http://freedns.afraid.org/](http://freedns.afraid.org/) still offer the service for free (seems that the popular ones like No-IP or DynDNS don't provide their service for free anymore); here the steps to configure it automatically with inadyn, partially based on Ubuntu documentation [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS) and [https://help.ubuntu.com/community/DynamicDNS#inadyn](https://help.ubuntu.com/community/DynamicDNS#inadyn)

First of all register your account on Freedns:
[http://freedns.afraid.org/menu/](http://freedns.afraid.org/menu/)
Freedns offer a bunch of domain names, from my taste the best ones (or the ones easy to remember) are:
[INDENT]mooo.com
ignorelist.com[/INDENT]
Assume that you register: <your_host>.ignorelist.com

Install inadyn:
```
sudo apt-get install inadyn curl
```

Open the url:
[INDENT][http://freedns.afraid.org/dynamic/](http://freedns.afraid.org/dynamic/)
Login with your account
Select the link **Direct URL** beside <your_host>.ignorelist.com
Copy everything from the right of the ? in the address bar ([COLOR="Red"]**alphanumeric string**[/COLOR])[/INDENT]

Create configuration file of inadyn:
```
sudo gedit /etc/inadyn.conf
```

And save this content:
```
--username <your_username>
--password <your_password>
--update_period 60000
--forced_update_period 320000
--alias <your_host>.ignorelist.com,[COLOR="Red"]**[B]alphanumeric string**[/B][/COLOR]
--background
--dyndns_system default@freedns.afraid.org
--syslog
```

Add inadyn to crontab:
```
export EDITOR=gedit && sudo crontab -e
```
Edit the file to add the following line:
```
@reboot /usr/sbin/inadyn
```

Reboot your PC

Wait 3 minutes

Check if inadyn is running:
```
ps -A | grep inadyn
```

Check inadyn behaviour:
```
more /var/log/messages |grep INADYN
```

Check if your host is up:
```
ping <your_host>.ignorelist.com
```

Done!

---

### Post by dewsworld on 2012-04-04
Many Many thanks for the post. It works great for me!:guitar:

---

### Post by TommiHommi on 2012-05-20
yeah it works! now ill try it on my minimal ubuntu with only java and mono installed (i'm setting up a minecraft server)

---

### Post by Fatman_UK on 2012-06-18
Thanks dentaku! It works! :D 

(but ... reboot your PC instead of just running the program? Seriously? :P )

---

### Post by TopherMan on 2012-07-03
Hello all,

I am setting up my first server, and I followed these directions for setting up inadyn. I'm still having an issue, and I'm trying to pinpoint it, and the only thing that didn't work is the second to last line of code, starting with "more". It just returns "no such file or directory," and since I'm not totally sure what I'm doing, I don't know if that's a problem or not. However, ps shows that it's running, and the ping seems to work fine, so should I be concerned, or is this not an issue?

Thanks!

PS. For reference, I'm using 12.04 on an old machine, and my attempts to ssh through the afraid.org address are failing. If this isn't the problem, I'm going to start a new thread asking questions about opening ports.

---

### Post by Fatman_UK on 2012-07-25
Despite my chirpy post above I had some trouble too. Here's the config I ended up with:

```
fatman@nikko:~$ cat /etc/inadyn.conf
--username notmyusername
--password notmypassword
--update_period_sec 7200
--forced_update_period 21600
--alias notmysubdomain.strangled.net,bm90bXliYXNlNjRjb2Rlbm9yZWFsbHlub3RteWJhc2U2NGNvZGU=
--background
--dyndns_system default@freedns.afraid.org
--syslog

```

Try replacing '--syslog' with '--verbose 5' and remove '--background'. That might give you some idea what's wrong.

I seem to recall my problem was the hash after '--alias', double check you've got that right.

---

### Post by strat1219 on 2012-07-26
> **Fatman_UK said:**
> Despite my chirpy post above I had some trouble too. Here's the config I ended up with:
 
```
fatman@nikko:~$ cat /etc/inadyn.conf
--username notmyusername
--password notmypassword
--update_period_sec 7200
--forced_update_period 21600
--alias notmysubdomain.strangled.net,bm90bXliYXNlNjRjb2Rlbm9yZWFsbHlub3RteWJhc2U2NGNvZGU=
--background
--dyndns_system default@freedns.afraid.org
--syslog

```
 
Try replacing '--syslog' with '--verbose 5' and remove '--background'. That might give you some idea what's wrong.
 
I seem to recall my problem was the hash after '--alias', double check you've got that right.
 
I am having a similar issue as above, no log file, but process is running.  Is the "alias" line supposed to look like...
 
--alias [www.somedomain.com,bm90bXliYXNlNjRjb2Rlbm9yZWFsbHlub3RteWJhc2U2NGNvZGU]("http://www.somedomain.com,bm90bXliYXNlNjRjb2Rlbm9yZWFsbHlub3RteWJhc2U2NGNvZGU")=  ?
 
Or is it supposed to have the ".ignorelist.com" in there?
 
Thanks!

---

### Post by scudzilla on 2012-08-11
```
INADYN: Started 'INADYN version 1.96.2' - dynamic DNS updater.
INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 0)
I:INADYN: IP address for alias 'xxx.xxx.com' needs update to 'x.x.x.x'
I:INADYN: Alias 'xxx.xxx.com' to IP 'x.x.x.x' updated successful.
```That's my log. Yes, x.x.x.x is what my router's current ip is. It says ip update successful, but when pinging, my subdomain still points to my router's old ip address. I had to log in to afraid.org to change the ip address. Any ideas?

---

### Post by pedm on 2012-08-31
> **TopherMan said:**
> Hello all,

I am setting up my first server, and I followed these directions for setting up inadyn. I'm still having an issue, and I'm trying to pinpoint it, and the only thing that didn't work is the second to last line of code, starting with "more". It just returns "no such file or directory," and since I'm not totally sure what I'm doing, I don't know if that's a problem or not. However, ps shows that it's running, and the ping seems to work fine, so should I be concerned, or is this not an issue?

Thanks!

PS. For reference, I'm using 12.04 on an old machine, and my attempts to ssh through the afraid.org address are failing. If this isn't the problem, I'm going to start a new thread asking questions about opening ports.

Thanks for this great tutorial! It works like a charm for freedns.afraid.org

Try:

```
more /var/log/syslog |grep INADYN 
```instead of:
```

more /var/log/messages |grep INADYN
```

If gedit does not work use nano:
```
sudo nano /etc/inadyn.conf

```
```
 export EDITOR=nano && sudo crontab -e 
```

---

### Post by pedm on 2012-08-31
To run inadyn every 5 minutes:
```

export EDITOR=nano && sudo crontab -e

```Add bellow @reboot   /usr/sbin/inadyn :

```

# m h  dom mon dow   command
@reboot /usr/sbin/inadyn
*/5 * * * * /usr/sbin/inadyn

```

---

### Post by mpgarate on 2012-12-15
It appears to be working correctly, except that I'm unable to ping at the end. Here's my output:

```
mike@mike-1001PXD:~$ more /var/log/syslog |grep INADYN
Dec 15 23:22:11 mike-1001PXD INADYN[2243]: INADYN: Started 'INADYN version 1.96.2' - dynamic DNS updater.
Dec 15 23:22:11 mike-1001PXD INADYN[2243]: I:INADYN: IP address for alias 'mooo.ignorelist.com' needs update to 'xxx.xxx.xx.74'
Dec 15 23:22:12 mike-1001PXD INADYN[2243]: I:INADYN: Alias 'mooo.ignorelist.com' to IP 'xxx.xxx.xx.74' updated successful.
Dec 15 23:22:43 mike-1001PXD INADYN[2243]: I:INADYN: IP address for alias 'mooo.ignorelist.com' needs update to 'xxx.xxx.xx.78'
Dec 15 23:22:43 mike-1001PXD INADYN[2243]: I:INADYN: Alias 'mooo.ignorelist.com' to IP 'xxx.xxx.xx.78' updated successful.
Dec 15 23:23:01 mike-1001PXD INADYN[2254]: INADYN: Started 'INADYN version 1.96.2' - dynamic DNS updater.
Dec 15 23:23:01 mike-1001PXD INADYN[2254]: I:INADYN: IP address for alias 'mooo.ignorelist.com' needs update to 'xxx.xxx.xxx.79'
Dec 15 23:23:02 mike-1001PXD INADYN[2254]: I:INADYN: Alias 'mooo.ignorelist.com' to IP 'xxx.xxx.xx.79' updated successful.
Dec 15 23:23:14 mike-1001PXD INADYN[2243]: I:INADYN: IP address for alias 'mooo.ignorelist.com' needs update to 'xxx.xxx.xx.79'
Dec 15 23:23:14 mike-1001PXD INADYN[2243]: I:INADYN: Alias 'mooo.ignorelist.com' to IP 'xxx.xxx.xx.79' updated successful.
Dec 15 23:23:33 mike-1001PXD INADYN[2254]: I:INADYN: IP address for alias 'mooo.ignorelist.com' needs update to 'xxx.xxx.xx.72'
Dec 15 23:23:34 mike-1001PXD INADYN[2254]: I:INADYN: Alias 'mooo.ignorelist.com' to IP 'xxx.xxx.xx.72' updated successful.
Dec 15 23:23:46 mike-1001PXD INADYN[2243]: I:INADYN: IP address for alias 'mooo.ignorelist.com' needs update to 'xxx.xxx.xx.73'
Dec 15 23:23:46 mike-1001PXD INADYN[2243]: I:INADYN: Alias 'mooo.ignorelist.com' to IP 'xxx.xxx.xx.73' updated successful.
Dec 15 23:24:05 mike-1001PXD INADYN[2254]: I:INADYN: IP address for alias 'mooo.ignorelist.com' needs update to 'xxx.xxx.xx.74'
Dec 15 23:24:05 mike-1001PXD INADYN[2254]: I:INADYN: Alias 'mooo.ignorelist.com' to IP 'xxx.xxx.xx.74' updated successful.
Dec 15 23:24:17 mike-1001PXD INADYN[2243]: I:INADYN: IP address for alias 'mooo.ignorelist.com' needs update to 'xxx.xxx.xx.74'
Dec 15 23:24:17 mike-1001PXD INADYN[2243]: I:INADYN: Alias 'mooo.ignorelist.com' to IP 'xxx.xxx.xx.74' updated successful.

```

If I go to freedns.afraid.org/subdomain/ I can see the dns refresh when it's updated (every few seconds on my network). I am unable to ping my alias, however.

---

### Post by dentaku65 on 2013-01-04
> **mpgarate said:**
> It appears to be working correctly, except that I'm unable to ping at the end. Here's my output:


If I go to freedns.afraid.org/subdomain/ I can see the dns refresh when it's updated (every few seconds on my network). I am unable to ping my alias, however.

Are u able to ping your current public IP address? If not maybe should be firewall setting of your box.

---

### Post by tehjolly81 on 2013-03-25
> **pedm said:**
> To run inadyn every 5 minutes:
```

export EDITOR=nano && sudo crontab -e

```Add bellow @reboot   /usr/sbin/inadyn :

```

# m h  dom mon dow   command
@reboot /usr/sbin/inadyn
*/5 * * * * /usr/sbin/inadyn

```

Thanks to all who have contributed to this thread for helping me get up and running with inadyn and freedns.afraid.org. A couple of things I noticed as I read through this thread that tripped me up:

-Scheduling inadyn to start at reboot using cron is a good idea, however scheduling it to run every 5 minutes as previously suggested might be a bad idea. The reason for this is that every 5 minutes, cron starts a new instance of inadyn while the old instance is still running.. so after an hour, you'd have 12 instances, after a day, 288 instances, etc.

-I couldn't get forced update checking to work - inadyn was updating the IP when cron started it right after a reboot, but it wasn't updating every 5 minutes as it was supposed to after that, even though the daemon was still running. I was starting to think I was going to have to kill the daemon after every update and then have cron run it every 5 minutes as previously discussed... until I realized that the --forced_update_period argument is in SECONDS, not MS. Updating the inadyn.conf file to show:

--forced_update_period 300

fixed the problem for me and allowed inadyn to update my IP every 5 minutes as intended. It is a bit confusing that update_period uses MS and forced_update_period uses SECONDS.

The OP's post shows a forced_update_period of 320000. This results in a forced update every 88 hours. Not sure if this was intended or not, but if you are wanting to force an update more frequently like I did, make sure you are calculating this value in SECONDS.

---

### Post by pedm on 2013-04-05
> --forced_update_period 300
Thanks a lot! 

Sorry, adding this to the contab:
> */5 * * * * /usr/sbin/inadyn
was not a good idea

---

