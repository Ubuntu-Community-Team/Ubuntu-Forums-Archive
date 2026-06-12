---
title: "Unknown permission status for class system"
date: 2020-11-10
forum: Server Platforms
---

### Post by msalazar77 on 2020-11-10
good morning, I have the following problem: I think it was after some kernel update, or some update; But I'm not sure.

ubuntuserver kernel: [187539.669409] audit: type=1107 audit(1605024901.496:6676): pid=1 uid=0 auid=4294967295 ses=4294967295 subj=system_u:system_r:kernel_t:s0 msg='Unknown permission status for class system exe="/lib/systemd/systemd" sauid=0 hostname=? addr=? terminal=?'

this error repeats 2 times every minute.

When I enter the ssh with root it tells me that I do not give permissions when I edit a configuration file of a service x

As much as I search on the internet I can't find any solution, the closest thing to this is the same in fedora and they request a version update, I'm not sure if this will be possible.

---

### Post by LHammonds on 2020-11-10
I will assume you are talking about the current version of Ubuntu Server which is 20.04.1 LTS which is running kernel version 5.4.0-52

On my server, here are the permission settings for each of those folders to the target file:

/lib (Directory which is symlinked to /usr/lib)
```
drwxr-xr-x  86 root root  4096 Oct 21 03:00 lib
```

/lib/systemd (Directory)
```
drwxr-xr-x 18 root root   12288 Nov  4 03:00 systemd
```

/var/systemd/systemd (File)
```
-rwxr-xr-x  1 root root 1620224 Oct  8 15:14 systemd
```

LHammonds

---

### Post by msalazar77 on 2020-11-10
thanks for your answer, however I am talking about the Ubuntu Linux 16.04.1 version. Also check the permissions of those folders and I tell you:  symlinked to / usr / lib - there is no reference to that directory/ lib / systemd - has the same permissions as your server/ var / systemd / systemd - no file exists

---

### Post by msalazar77 on 2020-11-10
sorry, the var directory is in the lib path : /var/lib/systemd with drwxr-xr-x.

the content is like this:


drwxr-xr-x.  2 root             root             4096 oct 14 16:49 catalog
-rw-r--r--.  1 systemd-timesync systemd-timesync    0 nov 10 12:50 clock
drwxr-xr-x.  2 root             root             4096 ago 17  2016 coredump
drwxr-xr-x. 11 root             root             4096 nov 10 08:33 deb-systemd-helper-enabled
drwxr-xr-x.  2 root             root             4096 dic  2  2016 deb-systemd-helper-masked
-rw-------.  1 root             root              512 nov 10 12:08 random-seed
drwxr-xr-x.  2 root             root             4096 oct 22  2019 timers

---

### Post by ajgreeny on 2020-11-10
Be very careful how you type as the pathways you show above will always be a problem; they do not and can not exist as you have spaces shown in them:-

/ lib / systemd
/ var / systemd / systemd
/ usr / lib

---

### Post by LHammonds on 2020-11-10
Well, your error message says:

```
'Unknown permission status for class system exe="/lib/systemd/systemd"
```

Ubuntu 16.04 was the 1st LTS version to use systemd so it "should" be there.

It is possible it got deleted by something.

Check if it is installed:

```
dpkg -l systemd
```

The results of this command on my Ubuntu Server 20.04.1 LTS:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version          Architecture Description
+++-==============-================-============-==============================>
ii  systemd        245.4-4ubuntu3.3 amd64        system and service manager
```

When I type this:
```
which systemd
```
It says this:
```
/usr/bin/systemd
```

Now, when I look at this file using **ls -l /usr/bin/systemd**, I get this:
```
lrwxrwxrwx 1 root root 20 Oct  8 15:14 /usr/bin/systemd -> /lib/systemd/systemd
```
Which is a symlink to the same systemd file in your error log...so the path should not have changed from 16.04 to 20.04.

LHammonds

---

### Post by msalazar77 on 2020-11-10
Result: 
ii  systemd                                   229-4ubuntu21.29          amd64                     system and service manager


ls -l /bin/systemd
lrwxrwxrwx. 1 root root 20 sep  4 03:31 /bin/systemd -> /lib/systemd/systemd




the directories exist, just in another path

---

### Post by LHammonds on 2020-11-10
Let's see if systemd is responding and doing its job.  Check the status of various systems that should be "active"

```
systemctl status cron
```

```
systemctl status unattended-upgrades
```

It has been a long time since I ran 16.04 servers but I think those two are there.  You can see what services you have by typing the following command:

```
ls /lib/systemd/system/*.service
```

LHammonds

---

### Post by msalazar77 on 2020-11-10
Regarding the list of services, I must indicate that it has a very large list, so I do not think it will help you to solve the problem, so if I can tell you that there are more than 100. I give you the  status of the commands you indicate.

cron.service - Regular background program processing daemon
   Loaded: loaded (/lib/systemd/system/cron.service; enabled; vendor preset: enabled)
   Active: active (running) since mar 2020-11-10 12:08:26 CST; 2h 34min ago
     Docs: man:cron(8)
 Main PID: 980 (cron)
    Tasks: 1
   Memory: 22.5M
      CPU: 3min 169ms
   CGroup: /system.slice/cron.service
           &#9492;&#9472;980 /usr/sbin/cron -f






 systemctl status unattended-upgrades
&#9679; unattended-upgrades.service - Unattended Upgrades Shutdown
   Loaded: loaded (/lib/systemd/system/unattended-upgrades.service; enabled; vendor preset: enabled)
   Active: active (running) since mar 2020-11-10 12:08:29 CST; 2h 37min ago
     Docs: man:unattended-upgrade(8)
 Main PID: 1173 (unattended-upgr)
    Tasks: 2
   Memory: 13.4M
      CPU: 113ms
   CGroup: /system.slice/unattended-upgrades.service
           &#9492;&#9472;1173 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal

---

### Post by LHammonds on 2020-11-10
Yes, there are a lot of .service files.  That is expected.  I was just giving you a place to look if the two I mentioned did not exist.  However, they do and it seems they are actively running....which means systemd is running...which is great.

You mentioned that this might have happened  after a kernel update.  You can see when kernel packages were  downloaded/installed on the system by typing this command and looking at  the dates:

```
ls -l /boot/vm*
```

Example:
```
lrwxrwxrwx 1 root root       24 Oct 20 03:00 /boot/vmlinuz -> vmlinuz-5.4.0-52-generic
-rw------- 1 root root 11678464 [COLOR=#ff0000]**Oct  5**[/COLOR] 08:54 /boot/vmlinuz-**[COLOR=#ff0000]5.4.0-51[/COLOR]**-generic
-rw------- 1 root root 11678464 **[COLOR=#ff0000]Oct 15[/COLOR]** 05:33 /boot/vmlinuz-**[COLOR=#ff0000]5.4.0-52[/COLOR]**-generic
lrwxrwxrwx 1 root root       24 Oct 20 03:00 /boot/vmlinuz.old -> vmlinuz-5.4.0-51-generic
```

From the above example, you can see that the last kernel installed was 5.4.0-52 on Oct 15th and 5.4.0-51 on Oct 5th.

I can tell which kernel I am using right now by typing:

```
uname -r
5.4.0-52-generic
```

I just did some google searching and they are  all related to systemd (Fedora/CentOS) but seem to be related to a bug  but nobody has fixed it due to End-of-Life support ending before being  resolved.  You are on 16.04.1, is it an option to upgrade to at least  16.04.5 which was the last point release for 16.04?  But of course, do  not make any system changes until you have a good backup.

LHammonds

---

### Post by msalazar77 on 2020-11-10
Yes, it was precisely the same thing that I found, at least in fedora there was a post indicating that it had to be updated, but for Ubuntu there is nothing. I already thought about starting with the older kernel to see if the problem stops. And well of course, update the server to 18 and then to 20.I really appreciate your help, I think that at the moment I do not have a critical effect on my server, unless of course you tell me otherwise.Of course, that has to do with the error, and not with the Linux version, that represents some kind of risk.

---

### Post by msalazar77 on 2020-11-10
Yes, it was precisely the same thing that I found, at least in fedora there was a post indicating that it had to be updated, but for Ubuntu there is nothing. I already thought about starting with the older kernel to see if the problem stops. And well of course, update the server to 18 and then to 20.I really appreciate your help, I think that at the moment I do not have a critical effect on my server, unless of course you tell me otherwise.Of course, that has to do with the error, and not with the Linux version, that represents some kind of risk.

---

### Post by LHammonds on 2020-11-10
As you said, there just isn't any reference material in Ubuntu about that specific error.  SystemD seems to be working despite the error.  You mentioned there is a message when editing root-level configuration files but I do not think you clarified if you are able to successfully edit those files or if it prevents you from making changes.

Your OS is long in the tooth (old) so I would not put off upgrading it if there is nothing preventing it.  I would recommend against trying to upgrade-in-place from 16 to 18 and then to 20.  Even if you did not have any applications installed, it is still a risky business doing in-place upgrades and just crossing your fingers that it will work.

If at all possible, install a 20.04 server somewhere and see if you can get your software installed and configured like your existing server.  Then copy over the data and see if you can get a fully-working copy running.  If you can do this, then you will know how to make it work and not be under the panic/rush to fix and figure out things on the fly.

If you only have a single server, see if you can get it working on your PC inside a virtual environment or temporarily rent a server for the migration.  Once you get it running on the temp server, you can then re-format the 16.04 server and install 20.04 from scratch (assuming there are no hardware issues).  Then going from the 20.04 temp server to your main server which is also 20.04 should be very easy.

No matter what path you go down, make sure you have a backup and can restore if needed.

**EDIT:** Oops, noticed all my signature links were outdated.  Fixed.

LHammonds

---

### Post by msalazar77 on 2020-11-10
excellent recommendation, thank you very much.

---

