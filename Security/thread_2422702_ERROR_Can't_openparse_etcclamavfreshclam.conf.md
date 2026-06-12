---
title: "ERROR: Can't open/parse /etc/clamav/freshclam.conf"
date: 2019-07-11
forum: Security
---

### Post by psoderlund on 2019-07-11
I am running Ubuntu 16.04 LTS and recently attempted to install clamav. I ran the command "sudo apt-get install clamav clamav-daemon clamtk" and then edited the /etc/clamav.freshclam.conf file to add my proxy information. When I ran the command "sudo freshclam" I received the error "ERROR: Can't open/parse the config file /etc/clamav/freshclam.conf". After googling I found this stackexchange conversation on the topic [https://askubuntu.com/questions/526317/cant-run-freshclam](https://askubuntu.com/questions/526317/cant-run-freshclam) and tried to reconfigure freshclam with the command "sudo dpkg-reconfigure clamav-freshclam" which did not resolve the issue. I also tried placing the symlink as suggested in the stackexchange article. I have also tried removing the installation and reinstalling to no avail. Does anyone have any thoughts as to what I could be doing wrong?

Thank you for any help you can provide.

---

### Post by SeijiSensei on 2019-07-12
Did you actually install the clamav-freshclam package?

---

### Post by psoderlund on 2019-07-12
Yes I did.
sudo apt-get install clamav-freshclam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav-freshclam is already the newest version (0.100.3+dfsg-0ubuntu0.16.04.1).
clamav-freshclam set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 103 not upgraded.
peter@AEB809:~$ sudo freshclam
ERROR: Can't open/parse the config file /etc/clamav/freshclam.conf

---

### Post by SeijiSensei on 2019-07-13
Is there an /etc/clamav/freshclam.conf? What owner:group and permissions does it have? I don't use ClamAV on Linux workstations, just on mail servers and web proxies. Anti-virus software is largely unnecessary on Linux. I've been using this OS since the mid-90's and never had any sort of malware or infection.

---

### Post by psoderlund on 2019-07-15
I normally don't have any AV software on my workstation but my company has made it policy to have it so I am trying to be compliant. That said I do have a /etc/clamav/freshclam.conf file with these permissions 
-r--------   1 clamav adm    944 Jul 12 11:42 freshclam.conf
I have tried changing the permissions and seen where that causes ClamAV to complain about the permissions. These permissions were set when I ran 
sudo dpkg-reconfigure clamav-freshclam

---

### Post by SeijiSensei on 2019-07-15
Those are incredibly restrictive. Try making it readable to all users with "sudo chmod 444 /etc/clamav/freshclam.conf".  Any better?

---

### Post by psoderlund on 2019-07-18
Sorry for the delay. Here is the results of your suggestion:

sudo chmod 444 /etc/clamav/freshclam.conf
peter@AEB809:~$ sudo freshclam
ERROR: Incorrect argument format for option HTTPProxyPort
ERROR: Can't open/parse the config file /etc/clamav/freshclam.conf

Not sure what caused the new error.

---

### Post by SeijiSensei on 2019-07-19
Well, it can now read the file, since it generated that new error.

Unless you're using a proxy to connect to the Internet, I'd edit clamav.conf as root with sudo and disable all the proxy stuff like this:

```

# Proxy settings
# Default: disabled
#HTTPProxyServer myproxy.com
#HTTPProxyPort 1234
#HTTPProxyUsername myusername
#HTTPProxyPassword mypass

```

You can use the command-line program nano to edit this file. "sudo nano /etc/clamav/clamav.conf".  Nano uses control-key combination for its commands; there's a handy help section at the bottom of the screen.

---

### Post by psoderlund on 2019-07-19
I did as you suggested and reviewed my proxy settings and did find and error which I fixed. However, I ended up back where I started.
peter@AEB809:~$ sudo freshclam
WARNING: Insecure permissions (for HTTPProxyPassword): /etc/clamav/freshclam.conf must have no more than 0700 permissions.
peter@AEB809:~$ sudo chmod 0700 /etc/clamav/freshclam.conf
peter@AEB809:~$ ll /etc/clamav/freshclam.conf
-rwx------ 1 clamav adm 939 Jul 19 13:11 /etc/clamav/freshclam.conf*
peter@AEB809:~$ sudo freshclam
ERROR: Can't open/parse the config file /etc/clamav/freshclam.conf

---

### Post by SeijiSensei on 2019-07-20
Are you using a proxy that requires a password?  Can you avoid using the proxy?

Perhaps you should try this:

```
sudo -u clamav -g adm freshclam
```

See "man sudo" for details.

I've set up organizations to use Squid as a proxy. We never required them to log in since we could control access by IP address.

Just out of curiosity, why are you using ClamAV? It's good for identifying Windows malware, but Linux is invulnerable to that. As I said above, ClamAV on Linux machines only makes sense for mail and file servers, or perhaps to scan a Windows filesystem on another partition.

---

### Post by psoderlund on 2019-07-22
Running the command you suggested worked. Now I am a bit confused, why did that work? Should I change the owner and group of freshclam? Or is it the user and group its run as that matters? 
As for why I need it, I don't per se, its now become company policy to have AV on every system.

---

### Post by SeijiSensei on 2019-07-23
> -rwx------ 1 clamav adm 939 Jul 19 13:11 /etc/clamav/freshclam.conf*

This file is owned by clamav in group adm. Running freshclam with that user and group enables it to read the freshclam.conf file. (Actually the group ownership doesn't matter here.)

You could set up a task in /etc/crontab that would run that command nightly

```

31 4 * * * clamav /path/to/freshclam >> /var/log/freshclam.log 2>&1

```

would run the freshclam program as user clamav every morning at 4:31 am. Replace "/path/to" with the actual path. /usr/bin/freshclam perhaps? Its output will be written to /var/log/freshclam.log. The "2>&1" item directs any errors written to the SYSERR device to the log file along with the normal program output. You might need to create the freshclam.log file manually to start since it needs to be owned by user clamav.

```

cd /var/log
sudo touch freshclam.log
sudo chown clamav:adm freshclam.log

```

---

### Post by jedi123 on 2019-08-09
Have you ever tried it this way to update ? 

sudo systemctl stop clamav-freshclam
sudo freshclam
sudo systemctl start clamav-freshclam
clamscan  [B] '/what-ever- the-directory-you need-scanned'

This worked for me as an update. 
[/B]

---

