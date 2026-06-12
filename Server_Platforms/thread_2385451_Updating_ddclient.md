---
title: "Updating ddclient"
date: 2018-02-20
forum: Server Platforms
---

### Post by mike-d-thats-me on 2018-02-20
Hello, linux/ubuntu noob here.  My goal is to setup a simple web server in my office behind a router to run our wordpress sites.  I have installed Ubuntu 16.04, ran updates, upgrades, configured port forwarding on router, setup account with [https://www.dnsdynamic.org](https://www.dnsdynamic.org), installed ddclient using their instructions plus cross referenced with these instructions [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS).

The end result is that it seems to be sort of working.  Some things I discovered is that the use=web... line needed to be at the top of the config file, the password needs to be in single quotes and the instructions on dnsdynamic.org are not sufficient.  Here is mine:



```
use=web, web=myip.dnsdynamic.com, web-skip='Current Address'
ssl=yes
protocol=dyndns2
daemon=301
cache=/var/cache/ddclient/ddclient.cache
syslog=yes
mail=root
mail-failure=root
pid=/var/run/ddclient.pid
server=www.dnsdynamic.org
login=myemail@something.com
password='passwordwithquotes'
subdomain.freeddnsdomain.com
```

If I enter:

```
sudo /etc/init.d/ddclient status
```

I get:


```
ddclient.service - LSB: Update dynamic domain name service entries
   Loaded: loaded (/etc/init.d/ddclient; bad; vendor preset: enabled)
   Active: active (running) since Fri 2018-02-16 12:37:13 EST; 3 days ago
     Docs: man:systemd-sysv-generator(8)
    Tasks: 1
   Memory: 11.5M
      CPU: 44.293s
   CGroup: /system.slice/ddclient.service
           &#9492;&#9472;1122 ddclient - sleeping for 171 seconds


Feb 20 10:53:43 ubuntuserver ddclient[18938]: WARNING:  file /var/cache/ddclient/ddclient.cache, line 3: Invalid Value for keyword 'ip' = ''
Feb 20 10:58:45 ubuntuserver ddclient[18966]: WARNING:  file /var/cache/ddclient/ddclient.cache, line 3: Invalid Value for keyword 'ip' = ''
Feb 20 11:03:47 ubuntuserver ddclient[19013]: WARNING:  file /var/cache/ddclient/ddclient.cache, line 3: Invalid Value for keyword 'ip' = ''
Feb 20 11:08:49 ubuntuserver ddclient[19041]: WARNING:  file /var/cache/ddclient/ddclient.cache, line 3: Invalid Value for keyword 'ip' = ''

```

I have looked up that warning message and there is not much out there to help resolve it but there were some indications that the Ubuntu version of ddclient is outdated. On this page, [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS), it says:

> if you do not get an error similar to the following you probably are good to go: 

WARNING: file /etc/ddclient.conf, line xBut it doesn't say what to do if I DO get this error.

If you can help, I would really appreciate it.  If you can, please give the full command lines I would need to fix this, im new to terminal.

---

### Post by wildmanne39 on 2018-02-20
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by LHammonds on 2018-02-20
I don't use this but I have to wonder about the following line you posted:
```
use=web, web=myip.dnsdynamic.com, web-skip='Current Address'
```
Is "Current Address" something you typed to obscure an IP address for this forum post or is that literally what you have in there?

I would assume that is expecting an actual IP address unless that is a keyword reservation but I have seen other examples using my Google-Fu showing "IP Address" instead. [Example](https://www.dynu.com/DynamicDNS/IPUpdateClient/DDClient)

LHammonds

---

### Post by mike-d-thats-me on 2018-02-20
Thanks for the quick response.  On [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS) it says to use web-skip='IP Address' Which I have tried with same results.  Other forums have suggested web-skip='Current Address' but it didnt make any difference.  Using neither gave the same results.  It seems no matter what the config is, the same warning reoccurs:
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]> [COLOR=#000000][FONT=Monaco]WARNING:  file /var/cache/ddclient/ddclient.cache, line 3: Invalid Value for keyword 'ip' = ''[/FONT][/COLOR]


---

### Post by mike-d-thats-me on 2018-02-20
If I:
> [COLOR=#000000][FONT=Monaco]sudo nano /var/cache/ddclient/ddclient.cache[/FONT][/COLOR]


Line 3 is:
> [COLOR=#000000][FONT=Monaco]atime=1519148645,backupmx=0,custom=0,host=subdomain.freeddnsdomain.com,ip=,mtime=0,mx=,script=/nic/update,static=0,status=noconnect,warned-min-error-interval=0,warned-min-interval=0,wildcard=0,wtime=0 subdomain.freeddnsdomain.com
[COLOR=#222222][FONT=Verdana][/FONT][/COLOR][/FONT][/COLOR]

---

### Post by LHammonds on 2018-02-20
What happens if you remove the web-skip part?

---

### Post by mike-d-thats-me on 2018-02-20
Same thing.  I just now took it out, saved file, rebooted server, restart ddclient and ran status to be sure, here are the results:

> [COLOR=#000000][FONT=Monaco]sudo /etc/init.d/ddclient status

[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][COLOR=#34bc26]&#9679;[/COLOR] ddclient.service - LSB: Update dynamic domain name service entries[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]   Loaded: loaded (/etc/init.d/ddclient; bad; vendor preset: enabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]   Active: [COLOR=#34bc26]active (running)[/COLOR] since Tue 2018-02-20 12:58:37 EST; 13s ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]     Docs: man:systemd-sysv-generator(8)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]  Process: 1358 ExecStop=/etc/init.d/ddclient stop (code=exited, status=0/SUCCESS)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]  Process: 1367 ExecStart=/etc/init.d/ddclient start (code=exited, status=0/SUCCESS)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]    Tasks: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]   Memory: 4.5M[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]      CPU: 247ms[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]   CGroup: /system.slice/ddclient.service[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]           &#9492;&#9472;1376 ddclient - sleeping for 290 seconds[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Feb 20 12:58:36 ubuntuserver systemd[1]: Stopped LSB: Update dynamic domain name service entries.[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Feb 20 12:58:36 ubuntuserver systemd[1]: Starting LSB: Update dynamic domain name service entries...[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Feb 20 12:58:37 ubuntuserver systemd[1]: Started LSB: Update dynamic domain name service entries.[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Feb 20 12:58:37 ubuntuserver ddclient[1382]: WARNING:  file /var/cache/ddclient/ddclient.cache, line 3: Invalid Value for keyword 'ip' = ''[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Feb 20 12:58:37 ubuntuserver ddclient[1397]: WARNING:  skipping update of subdomain.freeddnsdomain.com from <nothing> to 67.71.XX.XXX.[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Feb 20 12:58:37 ubuntuserver ddclient[1397]: WARNING:   last updated <never> but last attempt on Tue Feb 20 12:58:10 2018 failed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Feb 20 12:58:37 ubuntuserver ddclient[1397]: WARNING:   Wait at least 5 minutes between update attempts.[/FONT][/COLOR]


---

### Post by LHammonds on 2018-02-20
Make sure the cache isn't messing with you.

```
sudo service ddclient stop
sudo rm /var/cache/ddclient/ddclient.cache
sudo service ddclient start
```

---

### Post by LHammonds on 2018-02-20
Could the problem be this?  [https://askubuntu.com/questions/64219/why-is-ddclient-giving-me-an-invalid-ip-error-when-trying-to-update-dynamic-dn/212185](https://askubuntu.com/questions/64219/why-is-ddclient-giving-me-an-invalid-ip-error-when-trying-to-update-dynamic-dn/212185)

I did an "apt search ddclient" and it shows 3.8.2- is the version in the repository.  Seems like this should have included the fix for the bug mentioned above.

I wondered since line 3 was the protocol line in the config file...but the 3rd option in line 1 was the web-skip part.

---

### Post by mike-d-thats-me on 2018-02-20
> **LHammonds said:**
> Make sure the cache isn't messing with you.

```
sudo service ddclient stop
sudo rm /var/cache/ddclient/ddclient.cache
sudo service ddclient start
```

Nope, tried and results are the same.  But thank you.

> [COLOR=#000000]I did an "apt search ddclient" and it shows 3.8.2- is the version in the repository. Seems like this should have included the fix for the bug mentioned above.[/COLOR]

Yes, I am finding the same thing.

---

### Post by LHammonds on 2018-02-20
I just installed ddclient on my test server and this is what the default config file looks like (test stuff was what I typed in which is bogus)

```
# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf

protocol=dyndns2
use=web, web=checkip.dyndns.com, web-skip='IP Address'
server=members.dyndns.org
login=testid
password='testpass'
test.dyndns.org
```

EDIT: I also see the "line 3:" warning message.  I also have an invalid / made-up credentials but it says as much further down in a FAILED message for authorization.

---

### Post by LHammonds on 2018-02-20
I was reading through the [usage documentation]("https://sourceforge.net/p/ddclient/wiki/usage/") and wondered if I would get any different results if I put everything on one line that had a key=value setting.

New config:
```
# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf

protocol=dyndns2,use=web, web=checkip.dyndns.com, web-skip='IP Address',server=members.dyndns.org,login=testid,password='testpass'
test.dyndns.org
```

I then stopped the service, cleared cache, started service and ran the command to see what errors would show.

```
service ddclient stop
rm /var/cache/ddclient/ddclient.cache
service ddclient start
ddclient
FAILED:   updating test.dyndns.org: badauth: Bad authorization (username or password)

```
The only message given was the authorization message which I expected but the WARNING messages no longer appear.

**EDIT:** Nevermind, I checked syslog and I see the IP warning there:

```
egrep ddclient /var/log/syslog
Feb 20 12:40:39 srv-testturd ddclient[30621]: WARNING:  file /var/cache/ddclient/ddclient.cache, line 3: Invalid Value for keyword 'ip' = ''
Feb 20 12:40:39 srv-testturd ddclient[30621]: WARNING:  skipping update of test.dyndns.org from <nothing> to 8.8.8.8.
Feb 20 12:40:39 srv-testturd ddclient[30621]: WARNING:   last updated <never> but last attempt on Tue Feb 20 12:39:48 2018 failed.
Feb 20 12:40:39 srv-testturd ddclient[30621]: WARNING:   Wait at least 5 minutes between update attempts.
```

I'm out of ideas.  Sorry.

---

### Post by mike-d-thats-me on 2018-02-20
I tried that, first the way I had it and then your way, without the daemon ssl and pid lines.  But the result is the same either way. 

> [COLOR=#000000][FONT=Monaco]daemon=300,pid=/var/run/ddclient.pid,ssl=yes,protocol=dyndns2,use=web, web=myip.dnsdynamic.com, web-skip='IP Address',server=www.dnsdynamic.org,login=username,password='userpassword',sub.ddnsdomain.com[/FONT][/COLOR]

I use "[COLOR=#000000][FONT=Monaco]sudo ddclient -daemon=0 -debug -verbose -noquiet" to check and I still see the line 3 warning.

[/FONT][/COLOR]EDIT: > [COLOR=#000000]I'm out of ideas. Sorry.[/COLOR] No problem, I really appreciate the effort.

---

### Post by mike-d-thats-me on 2018-02-21
I think this topic has been moved to the wrong forum.  Its not about Ubuntu Server, its about the package DDCLIENT from the official repository which seems to be out of date or buggy.

---

