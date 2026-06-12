---
title: "Total Breakdown of Ubuntu CE"
date: 2010-05-23
forum: Ubuntu Christian Edition
---

### Post by Jerriy on 2010-05-23
I recently upgraded to Lucid Lynx and that caused trouble for my ubuntu CE. Don't exactly know what the problem was but in any case it is now impossible to install Ubuntu CE.

So then I tried to do it another way and uninstall the installed one separately and start a fresh install but that was a fail as well: apparently there are some Ubuntu CE files (ubuntu sound) that couldn't be removed! And this bug completely interrupts a fresh install of anything that is related to Ubuntu CD (for example even a separate Dansguardian can't be installed cause of the Ubuntu sound error

---

### Post by Jerriy on 2010-05-23
Here it is:

---

### Post by Rasa1111 on 2010-05-23
[IMG]http://ubuntuce.com/screenshots/v5.0/access_denied.png[/IMG]

lol, sorry. 

didn't know there was such thing.
had to look it up... that was among other .... screenshots.

---

### Post by david_kt on 2010-05-23
> **Jerriy said:**
> Here it is:

Try this:
```
 sudo rm /var/lib/dpkg/info/ubuntu-ce-sounds.postrm 

```

After that:

```
sudo apt-get remove ubuntu-ce-sounds
```

But that might leave some line in the /etc/gdm/PostSession/Default.
Could you give me:

```
cat /etc/gdm/PostSession/Default
```

DK

---

### Post by david_kt on 2010-05-23
> **Rasa1111 said:**
> [IMG]http://ubuntuce.com/screenshots/v5.0/access_denied.png[/IMG]

lol, sorry. 

didn't know there was such thing.
had to look it up... that was among other .... screenshots.

That is because dansguardian is active, blocking porn sites

DK

---

### Post by Rasa1111 on 2010-05-23
yeah that's cool.
i just dont go to porn sites to begin with though. lol

---

### Post by Jerriy on 2010-05-23
> **david_kt said:**
> Try this:
```
 sudo rm /var/lib/dpkg/info/ubuntu-ce-sounds.postrm 

```

After that:

```
sudo apt-get remove ubuntu-ce-sounds
```

But that might leave some line in the /etc/gdm/PostSession/Default.
Could you give me:

```
cat /etc/gdm/PostSession/Default
```

DKHi there, I did all that and here is the result of that last command:```
#!/bin/sh

exit 0

```What does that mean now?

---

### Post by david_kt on 2010-05-23
> **Jerriy said:**
> Hi there, I did all that and here is the result of that last command:```
#!/bin/sh

exit 0

```What does that mean now?

The problem should be solved already.

DK

---

### Post by Jerriy on 2010-05-24
```
xxx:~$ **sudo apt-get update && sudo apt-get safe-upgrade**
Hit http://ubuntu.mirror.cambrium.nl lucid Release.gpg
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid/main Translation-en_US
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid/multiverse Translation-en_US
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid/universe Translation-en_US
Hit http://ubuntu.mirror.cambrium.nl lucid-security Release.gpg
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid-security/main Translation-en_US
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid-security/universe Translation-en_US
Hit http://archive.canonical.com lucid Release
Hit http://ubuntu.mirror.cambrium.nl lucid-updates Release.gpg
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid-updates/main Translation-en_US
Hit http://archive.canonical.com lucid/partner Packages
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid-updates/multiverse Translation-en_US
Reading package lists... Done
E: Invalid operation safe-upgrade

``````
xxx:~$ **sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  dansguardian-gui
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161820 files and directories currently installed.)
Removing dansguardian-gui ...
update-rc.d: /etc/init.d/ubuntu_ce_firewall exists during rc.d purge (use -f to force)
dpkg: error processing dansguardian-gui (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 dansguardian-gui
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by david_kt on 2010-05-24
> **Jerriy said:**
> 
[/CODE]```
xxx:~$ **sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  dansguardian-gui
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161820 files and directories currently installed.)
Removing dansguardian-gui ...
update-rc.d: /etc/init.d/ubuntu_ce_firewall exists during rc.d purge (use -f to force)
dpkg: error processing dansguardian-gui (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 dansguardian-gui
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Try below:
```
sudo rm /etc/init.d/ubuntu_ce_firewall
sudo apt-get remove dansguardian-gui
```

After that, try again:

```
sudo apt-get dist-upgrade
```

DK

---

