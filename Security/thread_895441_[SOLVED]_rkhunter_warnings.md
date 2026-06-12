---
title: "[SOLVED] rkhunter warnings"
date: 2008-08-20
forum: Security
---

### Post by Camilia on 2008-08-20
I installed rkhunter.  Running it got 2 warnings for these 2 areas:
   Checking /dev for suspicious file types                   
   Checking for hidden files and directories 
What do I do now? 

Results have been written to the logfile -
/var/log/rkhunter.log)   Where can I find this?

---

### Post by pedja_portugalac on 2008-08-20
Hello Camilia

There's lot about rkhunter on this forum. Next time you should use "search" before posting new tread.
Concerning your question, read my second post on this page:
[http://ubuntuforums.org/showthread.php?t=881404](http://ubuntuforums.org/showthread.php?t=881404)

---

### Post by Camilia on 2008-08-20
All this computer language confuses me. Can't I get a simple answer?

---

### Post by pedja_portugalac on 2008-08-20
> **Camilia said:**
> All this computer language confuses me. Can't I get a simple answer?

Open terminal: Applications > Accessories > Terminal and type

```
sudo gedit /etc/rkhunter.conf
```

Remove "#" in the beginning of lines in question: 

# Allow the specified hidden directories.
# One directory per line (use multiple ALLOWHIDDENDIR lines).
#
ALLOWHIDDENDIR=/etc/.java
ALLOWHIDDENDIR=/dev/.udev
#ALLOWHIDDENDIR=/dev/.udevdb
#ALLOWHIDDENDIR=/dev/.udev.tdb
ALLOWHIDDENDIR=/dev/.static
ALLOWHIDDENDIR=/dev/.initramfs
#ALLOWHIDDENDIR=/dev/.SRC-unix

Like I have done. Then scroll down and add the following line (ALLOWDEVFILE=/dev/shm/pulse-shm-*) to:

# Allow the specified files to be present in the /dev directory and not
# regarded as a suspicious file.  One file per line (use multiple
# ALLOWDEVFILE lines), wildcards accepted.
#
#ALLOWDEVFILE=/dev/abc
ALLOWDEVFILE=/dev/shm/pulse-shm-*

Save and close gedit (text editor).
Run in terminal:
```
sudo rkhunter --propupdate
```

And that's it. Now

sudo rkhunter --update
sudo rkhunter -c -sk 

to check again.

---

### Post by brian_p on 2008-08-20
> **Camilia said:**
> I installed rkhunter.  Running it got 2 warnings for these 2 areas:
   Checking /dev for suspicious file types                   
   Checking for hidden files and directories 
What do I do now? 

These are not warnings. The program is telling you what it is doing.

> Results have been written to the logfile -
/var/log/rkhunter.log)   Where can I find this?

In a terminal type:

```
sudo less /var/log/rkhunter.log

```

---

### Post by Camilia on 2008-08-25
> **pedja_portugalac said:**
> Open terminal: Applications > Accessories > Terminal and type

```
sudo gedit /etc/rkhunter.conf
```

Remove "#" in the beginning of lines in question: 

# Allow the specified hidden directories.
# One directory per line (use multiple ALLOWHIDDENDIR lines).
#
ALLOWHIDDENDIR=/etc/.java
ALLOWHIDDENDIR=/dev/.udev
#ALLOWHIDDENDIR=/dev/.udevdb
#ALLOWHIDDENDIR=/dev/.udev.tdb
ALLOWHIDDENDIR=/dev/.static
ALLOWHIDDENDIR=/dev/.initramfs
#ALLOWHIDDENDIR=/dev/.SRC-unix

Like I have done. Then scroll down and add the following line (ALLOWDEVFILE=/dev/shm/pulse-shm-*) to:

# Allow the specified files to be present in the /dev directory and not
# regarded as a suspicious file.  One file per line (use multiple
# ALLOWDEVFILE lines), wildcards accepted.
#
#ALLOWDEVFILE=/dev/abc
ALLOWDEVFILE=/dev/shm/pulse-shm-*

Save and close gedit (text editor).
Run in terminal:
```
sudo rkhunter --propupdate
```

And that's it. Now

sudo rkhunter --update
sudo rkhunter -c -sk 

to check again.

Don't have ALLOWDEVFILE=/dev/shm/pulse-shm-*
Got warning for hecking /dev for suspicious file types

---

### Post by Camilia on 2008-08-26
Ran another check and still have a warning
Checking /dev for suspicious file types  Warning
To feel more sure that I don't have any viruses I created a dual boot windows and downloaded superantispyware for scanning after I surf throught Ubuntu

---

### Post by Camilia on 2008-08-28
Uninstalled ubuntu to create a dual bootup. Pasted sudo gedit /etc/rkhunter.conf got a blank page. What does this mean?

---

### Post by Skorzen on 2008-08-28
> **Camilia said:**
> Uninstalled ubuntu to create a dual bootup. Pasted sudo gedit /etc/rkhunter.conf got a blank page. What does this mean?

Possibly it means that the file doesn't existed and you created one, or that the file is blank.

---

### Post by Camilia on 2008-08-29
I still don't feel comfortable without superantispyware. Thus did a dual boot and have superantispyware on windows portion.

---

