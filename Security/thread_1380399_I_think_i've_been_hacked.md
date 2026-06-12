---
title: "I think i've been hacked"
date: 2010-01-13
forum: Security
---

### Post by methodtwo on 2010-01-13
Hi there
A few weeks ago i was unable to log into my system. So i booted a rescue disk changed the password. I also noticed that there was an account called guest. I'm using a router which is connected to a cable modem. The router allocates I.P addresses in the 192.168.2.1-100 range.I noticed that there were log entries in the router's log that had the address 192.168.2.10.Seeing as the pool starts from 192.168.2.2 and there are only 4 machines on the internal network i thought this was a clue as to how my system became unusable.You think that's strange well i uninstalled all my services like apache2, using apt-get remove.However apache2 still appears in a process list.When i do:
```
$ps aux
```
i get:
```
/usr/sbin/apache2 -k start
```With the users root and www-data. When i try to uninstall apache2 again it just says the apache2 is not installed.These are good indications that i'm owned right?.What can i do(without reinstalling)?Why can't i remove apache2?
I ran chkrootkit and it didn't pick anything up.How do i put tripwire on a USB stick(ready for a new install)?.How the hell do i get rid of apache2 or tell if it's trojaned?What does:
```
/usr/sbin/apache2 -k start
```
mean?
Also there are no ports open on my router so how did they get through N.A.T? and the firewall???
I don't need this information in order to cause chaos i need it because i still don't understand how i was hacked/cracked
Thankyou for any help
regards methodtwo

---

### Post by cdenley on 2010-01-13
Removing the "apache2" package does not remove apache. It is basically a meta-package, and the package containing the actual server is a dependency of it.
```

sudo apt-get remove apache2.* libapache2.*

```

A guest account is created when you create a guest session. It is a temporary non-persistent account stored in memory. I believe the user should be deleted when the guest user logs off.

That process "/usr/sbin/apache2 -k start" simply means you are running a web server.

I haven't read anything which seems to suggest you were hacked unless you can confirm someone changed your password or authenticated remotely. Check /var/log/auth.log. Routers don't always assign addresses sequentially. Are you running any servers besides apache?
```

sudo netstat -tulnp

```
Did you use a strong password? Did you set a root password? Do you have a wireless network? If so, what type of encryption?

---

### Post by badSheep8 on 2010-01-14
There are some modems with known security holes. Like BBoX2 for example that permits remote users to see the user name and password you use to log on to your ISP.

Not that I know a lot about rootkits and hiding hacking trails but you may want to watch network traffic once in a while using etherape and wireshark....

---

### Post by methodtwo on 2010-01-14
I've just run:
```
sudo apt-get -s remove apache2.* libapache2.*

```
And apache is still listed in the process list when i do a ps.Even after a reboot.
No i didn't set a root password.Yes someone did lock me out of my account from remote.Since then i've reinstalled.But as mentioned this system, that i'm using now, still has signs of hacking activity i.e the signs that i've mentioned in this thread.
Also there were entries in /var/log/auth.log that i didn't understand:
```
Jan 14 04:09:01 neptune CRON[17678]: pam_unix(cron:session): session closed for user root
Jan 14 04:10:01 neptune CRON[17820]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 14 04:10:01 neptune dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.32" (uid=1000 pid=3310 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0
```
As far as i know i'm not running any cron jobs.But there were these entries in auth.log.
Any clarification would be great.Remember i couldn't remove apache2.Well, as mentioned, i ran the command to remove it but after a reboot it is still listed in the process list.
Thank you for your help
regards methodtwo

---

### Post by methodtwo on 2010-01-14
By the way the guest account was not removed and is still in there.Having said this i never even had a guest session or initiated anything that would add a guest account.

---

### Post by cdenley on 2010-01-14
> **methodtwo said:**
> I've just run:
```
sudo apt-get -s remove apache2.* libapache2.*

```
And apache is still listed in the process list when i do a ps.Even after a reboot.


Sorry, I forgot to take out the "-s", which means simulate but don't actually do anything. I like to test commands before I post them, but didn't actually want to remove my web server.
> **methodtwo said:**
> 
No i didn't set a root password.Yes someone did lock me out of my account from remote.Since then i've reinstalled.But as mentioned this system, that i'm using now, still has signs of hacking activity i.e the signs that i've mentioned in this thread.
Also there were entries in /var/log/auth.log that i didn't understand:
```
Jan 14 04:09:01 neptune CRON[17678]: pam_unix(cron:session): session closed for user root
Jan 14 04:10:01 neptune CRON[17820]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 14 04:10:01 neptune dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.32" (uid=1000 pid=3310 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0
```
As far as i know i'm not running any cron jobs.But there were these entries in auth.log.
Any clarification would be great.Remember i couldn't remove apache2.Well, as mentioned, i ran the command to remove it but after a reboot it is still listed in the process list.
Thank you for your help
regards methodtwo

I'm not familiar with neptune. Is it an application you installed? From where? Also, you never posted the output from the netstat command I suggested. Simply not being able to login doesn't convince me someone actually changed your password remotely. I've seen too many people doing things like forgetting their password or forgetting num/caps lock.

---

### Post by methodtwo on 2010-01-14
I must have another package installed that depends on apache2 because i can't remove it, right?.I followed the thread on intrusion detection on these, ubuntu, forums.I realised that it was a bad trade off to have services running just to monitor traffic.I thought i would be better off without snort and apache2 running than i would be with snort and apache2 running, right?.So what is the command to remove apache2 now is it??:
```
apt-get remove build-essential libpcap0.8-dev libmysqlclient15-dev mysql-client-5.0 mysql-server-5.0 bison flex apache2 libapache2-mod-php5 php5-gd php5-mysql libphp-adodb php-pear libc6-dev g++ gcc pcregrep libpcre3-dev
```
Is this what i need to issue in order to get rid of apache2?
Thank you for your time
Regards methodtwo

---

### Post by cdenley on 2010-01-14
I already gave you the command to remove apache!
```

sudo apt-get remove apache2.* libapache2.*

```

As I explained, I accidentally left the "-s" switch in there previously, but without it, it removes any package starting with apache2 or libapache2, which should include the worker and prefork server, common files, binary files, and any modules you may have installed. In other words, that command removes apache, not simply the meta package containing 2 files.

Your command removes the meta package and a few modules, not apache2.2-bin, apache2.2-common, apache2-mpm-worker, or apache2-mpm-prefork.

---

### Post by cariboo on 2010-01-14
@methodtwo

Make sure you stop apache, before trying to remove it. Open a terminal and type:

```
sudo /etc/init.d/apache2 stop
```

Then instead of using the remove command, as doesn't remove the configuration files, use the purge command.

```
sudo apt-get purge apache2
```

This command will completely remove apache, including configuration files and mods.

---

### Post by cdenley on 2010-01-15
> **cariboo907 said:**
> 
This command will completely remove apache, including configuration files and mods.

I don't think so. That would purge the apache2 package, which is next to nothing. If you want to purge apache, replace "remove" with "purge" in the command I posted previously.

---

### Post by cariboo on 2010-01-15
From man apt-get:

> remove
           remove is identical to install except that packages are removed
           instead of installed. Note the removing a package leaves its
           configuration files in system. If a plus sign is appended to the
           package name (with no intervening space), the identified package
           will be installed instead of removed.

> purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).

---

### Post by d3v1150m471c on 2010-01-15
Make certain you've removed anything someone may have dropped onto your system. Also, look into getting firestarter, learning how to port stealth, and check out packages like snort, psad, tripwire, and the like. This won't make you hack proof but it does make it a hell of a lot harder for people to get into your system. Especially without you knowing about it. You can open firestarter and watch your active connections. I'd recommend doing this a few times while you're on your system to make sure a trojan or some crap someone may have uploaded is not trafficking outbound without your permission. In the event something malicious is going outbound, log the ip, the software that's making unauthorized connections, block it and/or delete it, and report this to your local authorities. You can get a more detailed network traffic report using etherape as well. All these tools can be installed with synaptic and have a plethora of tutorials on google.

---

### Post by methodtwo on 2010-01-16
Apache2 only was removed when i removed all the packages that i installed after following the intrusion detection thread on this forum:
```
sudo apt-get remove libpcap0.8-dev libmysqlclient15-dev mysql-client-5.0 mysql-server-5.0 bison flex apache2.* libapache2-mod-php5 php5-gd php5-mysql libphp-adodb php-pear pcregrep libpcre3-dev

```
When i ran this code apache2 was successfully removed
regards methodtwo

---

