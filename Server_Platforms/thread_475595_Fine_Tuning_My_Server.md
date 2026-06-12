---
title: "Fine Tuning My Server"
date: 2007-06-16
forum: Server Platforms
---

### Post by Gruelius on 2007-06-16
Well i figured id make one large thread for all the little things i need to do instead of making multiple things.

I first need to setup Security Related things for my box. At the moment it runs a php website and has a FTP. I dont have a software firewall installed or any anti DOS programs (i dont know what the right term is, when people spam the **** out of your ssh to crash it). It also runs ssh. Im installing clamav for samba so that i dont get windows viruses going around (not really an issue since 4/5 pc's are linux ;) )

I also need to setup power management options as the server is allways running and doing nothing. I was thinking of getting the hdd's to spin down after a certain time, and using cool + quiet ( i have a AM2 X2) to slow down the cpu and fan. I might actually set it up to go into standby if it is robust, i.e. it WILL come on when needed for printing or accessing or FTP or web access (im guessing the latter will need it to allways be on).

Also for backups the data is a 800gb array full of data that doesnt get changed once its on there. I have a dvd drive and a 600cd case and two 500gb usb drives at my disposal. What should i do backup wise? i was thinking of having all the sets of files (Divided logically) on dvd and also backup the whole array onto the hdd's every now and then. I might just go for dvd only and use the hdd's for something else (they were bought because my father thought they were cheap -.-).

Thats it for now, probably going to have more inspirations (and questions) tomorrow :)

Thanks 
Julius

---

### Post by dreadlord_chris on 2007-06-16
> **Gruelius said:**
> Well i figured id make one large thread for all the little things i need to do instead of making multiple things.

I first need to setup Security Related things for my box. At the moment it runs a php website and has a FTP. I dont have a software firewall installed or any anti DOS programs (i dont know what the right term is, when people spam the **** out of your ssh to crash it). It also runs ssh. Im installing clamav for samba so that i dont get windows viruses going around (not really an issue since 4/5 pc's are linux ;) )

I also need to setup power management options as the server is allways running and doing nothing. I was thinking of getting the hdd's to spin down after a certain time, and using cool + quiet ( i have a AM2 X2) to slow down the cpu and fan. I might actually set it up to go into standby if it is robust, i.e. it WILL come on when needed for printing or accessing or FTP or web access (im guessing the latter will need it to allways be on).

Also for backups the data is a 800gb array full of data that doesnt get changed once its on there. I have a dvd drive and a 600cd case and two 500gb usb drives at my disposal. What should i do backup wise? i was thinking of having all the sets of files (Divided logically) on dvd and also backup the whole array onto the hdd's every now and then. I might just go for dvd only and use the hdd's for something else (they were bought because my father thought they were cheap -.-).

Thats it for now, probably going to have more inspirations (and questions) tomorrow :)

Thanks 
Julius

Can't help with everything - but a few things come to mind....

First off - you do have a *software* firewall installed - it's called **iptables**, it's part of the Linux kernel, and it's running by default. There are some nice GUI front-ends to help configure iptables for you available in the repositories. The most basic and easiest to use would probably be Firestarter. Guarddog is another that offers much finer grain controls. One thing that tends to trip up new users - iptables is always running (unless you shut it down for some reason), even when the front-end (firestarter/guarddog/etc) isn't. Just remember - iptables is the 'firewall', the GUI is mearly a convenience for confiuration.

Second - As for *active security* for you Internet serving apps (HTTP/SSH/FTP/etc) - consider [fail2ban]("http://sourceforge.net/projects/fail2ban/"). It's in the repositories also.

Third - the RAID5 array - nice! As long as you have spare drives to swap in case of failure, and it's never more then 1 drive failing at a time - RAID5 is pretty robust at recovering from data loss. Just make sure that your spare drives are (preferably) the same make & model, and definately the same size - or you're gonna run into problems. This isn't to say you shouldn't have a regular backup plan in place - just that you are a little more secure from data loss then the average user.

That 600cd case - is that an online CD feeder (like a jukebox) to a writer?

---

### Post by Gruelius on 2007-06-16
Ive got a robotic cd disk burning station with a broken burner (planning to put a dvd drive in there. By 600cd case i mean just a box with sleeves :P

I found out one vulnerability that was pretty dumb on my half. Because i decided to get ftp to use users from my /etc/passwd i had to make two new users, and they both have ssh access. I ended up adding DenyUsers * then AllowUsers *myuser*, I was also wondering how i can restrict all global ip's except for a certain few from using ssh.

ill have a look at fail2ban tonight.

For FTP should i have set it up using mysql for the passwords?

For servers is software raid that bad? im not looking for groundbreaking performance, just the ability to add extra disks (which i know i can do easily).

Anyway i gotta bounce :) Thanks for the pointers so far.

---

### Post by dreadlord_chris on 2007-06-16
> **Gruelius said:**
> Ive got a robotic cd disk burning station with a broken burner (planning to put a dvd drive in there. By 600cd case i mean just a box with sleeves :P

I found out one vulnerability that was pretty dumb on my half. Because i decided to get ftp to use users from my /etc/passwd i had to make two new users, and they both have ssh access. I ended up adding DenyUsers * then AllowUsers *myuser*, I was also wondering how i can restrict all global ip's except for a certain few from using ssh.

ill have a look at fail2ban tonight.

For FTP should i have set it up using mysql for the passwords?

For servers is software raid that bad? im not looking for groundbreaking performance, just the ability to add extra disks (which i know i can do easily).

Anyway i gotta bounce :) Thanks for the pointers so far.

The sshd_config AllowUsers directive will also allow you to restrict to specific hosts/networks:
i.e.: 
```

AllowUsers *@192.168.1.? *@192.168.1.?? *@192.168.1.???

```
This would restrict logons to the IP range 192.168.1.1 - 192.168.1.254

Also, consider moving your SSH server to a different, non-standard, port. I run mine on port 6969 and I rarely see unauthorized login attempts.

As for using MySQL for your userbase backend - that really depends on how many users you think you'll end up having. Unless you think you're gonna have alot - I'd say it's unnecessary overhead.

Software RAID - it's better then no RAID at all. And really, other then slightly less robust fault-tolerence and slower performance - it's a damn site cheaper then a hardware solution.

---

### Post by Gruelius on 2007-06-17
When i tried DenyUsers * AllowUsers <name> that didnt work. My main worry is the two ftp accounts that will be distributed gaining SSH access so i decided to block those two accounts.

Im going to whack that line in next aswell and change the port. Does the internal linux firewall cope ok with ports being changed?

Also when i tried to add clamav to samba i have buggered many things up. Now for some reason when i try to access smb://rosch/ (the workgroup) i get error messages. If i try smb://192.168.0.3 i can access the server but the performance is quite poor. Ive removed my changes and its still like this!

hostname says tuxserver so i have a feeling its to do with samba.

Im going to make a post in proftp thread about limiting speeds as i dont want people slowing my web too much.

Again thanks so much for the help so far :D

**Edit**

Ok tuxserver is now showing up in the workgroup. So now i just need to know about getting clamav to work.

**edit**
here is my fail2ban conf file, i only added SSH cause i found an example on the web. How would i write one for ftp and http? i dont find the syntax too easy to read.
```
[Definition]

# Option:  loglevel
# Notes.:  Set the log level output.
#          1 = ERROR
#          2 = WARN
#          3 = INFO
#          4 = DEBUG
# Values:  NUM  Default:  3
#
loglevel = 3

# Option:  logtarget
# Notes.:  Set the log target. This could be a file, SYSLOG, STDERR or STDOUT.
#          Only one log target can be specified.
# Values:  STDOUT STDERR SYSLOG file  Default:  /var/log/fail2ban.log
#
logtarget = /var/log/fail2ban.log

# Option: socket
# Notes.: Set the socket file. This is used to communicate with the daemon. Do
#         not remove this file when Fail2ban runs. It will not be possible to
#         communicate with the server afterwards.
# Values: FILE  Default:  /tmp/fail2ban.sock
#
socket = /tmp/fail2ban.sock

maxfailures = 10
bantime = 600
ignoreip = 192.168.0.3

[SSH]
enabled = true
logfile = /var/log/auth.log
port = ssh
timeregex = S{3}s{1,2}d{1,2} d{2}:d{2}:d{2}
timepattern = %%b %%d %%H:%%M:%%S
failregex = : (?:(?:Authentication failure|Failed [-/w+]+) for(?: [iI](?:llegal|nvalid) user)?|[Ii](?:llegal|nvalid) user|ROOT LOGIN REFUSED) .*(?: from|FROM) (?:::f{4,6}:)?(?PS*)

```

---

### Post by dreadlord_chris on 2007-06-17
Sorry, can't help ya with clamAV - I've never used it.

When/if you change the sshd port you will have to open it in the firewall as well. Just be sure to plug the old hole. Also, you'll need to change the port line in fail2ban - just change **port = ssh** to **port = port#**

fail2ban:
[http://fail2ban.org/wiki/index.php/ProFTPd](http://fail2ban.org/wiki/index.php/ProFTPd)
from the link above, I would say the fail2ban config for proftp would be:
```

[FTP]
enabled = true
logfile = /var/log/auth.log
port = ftp
timeregex = S{3}s{1,2}d{1,2} d{2}:d{2}:d{2}
timepattern = %%b %%d %%H:%%M:%%S
failregex = USER \S+: no such user found from \S* ?\[<HOST>\] to \S+\s*$

```
Not really sure about the *logfile* line - relatively sure that proftp logs to auth.log - if not just point that line at the proper log.

And here we have the page for Apache: [http://fail2ban.org/wiki/index.php/Apache](http://fail2ban.org/wiki/index.php/Apache)
Your turn :wink:

---

### Post by Gruelius on 2007-06-18
Cool,
Yeah im not trying for a free ride i just had no clue what that line was. So is failregex what is searched for in the  log file?

Now for networking, if i want to gain a great understanding of how the logistics work (Wins sever, domain servers, Web servers, Proxies) on a more detailed level, not just what they do where should i look? freebie ebooks/websites would be great :D

---

### Post by dreadlord_chris on 2007-06-18
> **Gruelius said:**
> Cool,
Yeah im not trying for a free ride i just had no clue what that line was. So is failregex what is searched for in the  log file?

Now for networking, if i want to gain a great understanding of how the logistics work (Wins sever, domain servers, Web servers, Proxies) on a more detailed level, not just what they do where should i look? freebie ebooks/websites would be great :D

yup, failregex is the test line - there's a "rexex testing utility" included with fail2ban:
```

fail2ban-regex "line" "failregex"

```

will test a single regular expression *"failregex"* (such as given in sshd.conf) with a single *"line"* of your logfile. Don't forget the double quotes around your line and failregex definitions. 

fail2ban-regex accepts files too. Thus, it is easier to test and debug your own regular expressions:
```
 
# fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf

```

Or you can use a combination of both:
```

# fail2ban-regex /var/log/auth.log "Failed [-/\w]+ for .* from <HOST>"

```

As for networking - there are lots of rescources out there - Google is your friend :)
A couple places to start:
[The Linx Document Project]("http://www.tldp.org/")
[http://www.windowsnetworking.com](http://www.windowsnetworking.com)

---

### Post by irober02 on 2008-04-16
I've been investigating powermanagement on my new domestic server (samba, etc) based on a AMD Athlon(tm) 64 X2 Dual Core Processor 4400+.

The BIOS was factory set to do power management (Cool'N'Quiet -horrible name) but th CPU was at 2300 MHz even while idling.

Web research revealed a fair bit of information about power management -mainly focussing on laptops.

Anyway, I took a punt and installed powernowd (and lm-sensors so that I could observe the changes). 

Immediately the CPU slowed to 1000 MHz with a lower VCore. I didn't notice any performance change (samba serving and web proxying don't tax the system noticeably). 

So, I installed mencoder and kicked off some video encoding and was able to observe the CPU immediately jump to full clock speed and VCore.

I guess that means that part of power management is working well.

Is this a good approach? Any suggestions?

I would like to look into controlling the case fan -it seems to be spinning faster than it needs to. Also possibly HD spin down on-idle -some homework.

---

### Post by irober02 on 2008-04-16
Not having much time or expertise in iptables but having some workstations running firestarter, I temporarilly adjusted one of their firewalls to match my servre's requirements. I then used iptables-save > iptables.txt to create a text file of iptables rules. I made the obvious edits to rename the network device and ip address to match the server and copied it there. I ran sudo iptables-restore < iptables.txt and, hey presto, a firewall! :-)

A rudimentary init script to do the same at boot time was the final step and all seems good, suggestions welcome though. :-)

---

