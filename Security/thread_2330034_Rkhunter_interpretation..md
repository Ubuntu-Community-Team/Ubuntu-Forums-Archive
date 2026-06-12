---
title: "Rkhunter interpretation."
date: 2016-07-07
forum: Security
---

### Post by juan53 on 2016-07-07
Hi ladies and gentlemen

Today I've running rkhunter. At first sight, there is no reason why should be worried about, no infection signs. But the output has made me cold. What do you think?
(In order not to be nasty, I only paste the sections I consider, "worring")

```
[09:13:23] Info: Starting test name 'properties'
[09:13:23] Performing file properties checks
[09:13:33]   /usr/bin/lwp-request                            [ Warning ]
[09:13:33] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: a /usr/bin/perl -w script, ASCII text executable

Checking /dev for suspicious file types         [ Warning ]
[09:15:26] Warning: Suspicious file types found in /dev:
[09:15:26]          /dev/shm/pulse-shm-3962536165: data
[09:15:26]          /dev/shm/pulse-shm-1118256300: data
[09:15:26]          /dev/shm/pulse-shm-3224080157: data
[09:15:26]          /dev/shm/pulse-shm-1678443143: AmigaOS bitmap font
[09:15:26]          /dev/shm/pulse-shm-3853350153: data
[09:15:26]          /dev/shm/pulse-shm-1796757104: data
[09:15:26]          /dev/shm/pulse-shm-574886: data
[09:15:26]          /dev/shm/pulse-shm-4018859456: data

[09:15:52] System checks summary
[09:15:52] =====================
[09:15:52]
[09:15:52] File properties checks...
[09:15:52] Files checked: 149
[09:15:52] Suspect files: 1
[09:15:52]
[09:15:52] Rootkit checks...
[09:15:52] Rootkits checked : 365
[09:15:52] Possible rootkits: 0
[09:15:52]
[09:15:52] Applications checks...
[09:15:52] All checks skipped
[09:15:52]
[09:15:52] The system checks took: 2 minutes and 31 seconds
[09:15:52]
[09:15:52] Info: End date is jue jul  7 09:15:52 CEST 2016
```

I have to say that nmap does not dettect anything (all ports are closed)

And command netstat -plnt shows just the usual port 53 opened.

I have to say that the current version I am running is Ubuntu 16.04, with TLP mounted and the guess account deactivated as it follows:

[http://ubuntuhandbook.org/index.php/2016/04/remove-guest-session-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/04/remove-guest-session-ubuntu-16-04/)

What do you think?

Thanks a lot.

---

### Post by QDR06VV9 on 2016-07-07
I do not think you have anything to worry over see this:[https://sourceforge.net/p/rkhunter/mailman/message/31460254/](https://sourceforge.net/p/rkhunter/mailman/message/31460254/)

---

### Post by juan53 on 2016-07-07
Thanks a lot. :)

---

### Post by QDR06VV9 on 2016-07-07
Your very welcome.:)

---

### Post by Habitual on 2016-07-07
Here's what I would do:
Look in /var/log/rkhunter.log...examine it.

After that, then here are my thoughts:
```
sudo vi + /etc/rkhunter.conf
``` and add *something like*: (examples are in the file)
```
ALLOWDEVFILE=/dev/shm/pulse* # Not sure, worth a try
SCRIPTWHITELIST=/usr/bin/lwp-request
APP_WHITELIST="openssl:1.0.1f sshd:6.6p1 php:5.5.9"
```

To get the correct values for APP_WHITELIST (openssl, sshd, gpg, and php) we use in terminal:

```
sudo dpkg -l openssl openssh-server gpg* php5
```

to get the correct values for these exceptions. The above APP_WHITELIST is on 14.04.4
but you have to examine /var/log/rkhunter.log to know what exactly to "ALLOW" and ask is 
it safe to do so? I too have /dev/shm/pulse-shm* files and it looks to me from 
```
sudo lsof +D /dev/shm
``` that programs that use "pulseaudio in shared memory" is my best guess.

After editing the /etc/rkhunter.conf file, you can check the correctness of your edits with
```
rkhunter --check-config
```

[COLOR=#ff0000]**NOTES**[/COLOR]: This next command will update the rkhunter database and you tell the system “all is accounted for”.
```
rkhunter --proupd
```
It's the "All Clear" button, use discretion. However, you must use this every time you run
[LIST]
[*] apt-get update 
[*]apt-get upgrade 
[*]apt-get dist-upgrade 
[*]any time apt* installs, updates, or removes software you must run
```
rkhunter --proupd
``` 
[/LIST]
 

rkhunter is now up to 1.4.3 and here's the recipe to "get current" on rkhunter, 
It requires you to remove the repo version,
```
sudo apt-get remove -y rkhunter
```

**Get and install rkhunter 1.4.3**
Assumes elevated privs
```

cd /usr/src/
wget http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/?view=tar
mv index.html\?view\=tar rkhunter.tar.gz
tar zxf rkhunter.tar.gz
mv rkhunter rkhunter-1-4-3
cd  rkhunter-1-4-3
./installer.sh --install
rkhunter --update
```

To run a full system scan automatically interactively, 
I use
```
rkhunter -c -sk --rwo
```
It's less "noisy" and will **R**eport **W**arnings **O**nly.
If it just comes back to prompt. It's deemed clean, IMO # As 'configured'

Crontab for rkhunter updates:
```
sudo crontab -e -u root
```
and append to the file
```
00 0 * * * /usr/local/bin/rkhunter --update > /dev/null 2>&1
```

That should get you started.

---

