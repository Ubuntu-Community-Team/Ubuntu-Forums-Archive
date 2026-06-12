---
title: "Reset your Windows password, edit the Windows Registry from Ubuntu"
date: 2010-07-10
forum: Tutorials
---

### Post by melnichuk on 2010-07-10
THE MAIN GOAL OF THIS TOPIC IS TO **SHOW AN ABILITY OF WINDOWS REGISTRY EDITING** BUT NOT PASSWORD RESETTING ONLY. IT WAS CREATED AFTER READING OF THE FOLLOWING AT THE FORUM, WHERE THE QUESTIONS STILL WITHOUT ANSWERS INFACT:

[http://ubuntuforums.org/showthread.php?t=1046931]("http://ubuntuforums.org/showthread.php?t=1046931")
[http://ubuntuforums.org/showthread.php?t=624943]("http://ubuntuforums.org/showthread.php?t=624943")
[http://ubuntuforums.org/showthread.php?t=955950]("http://ubuntuforums.org/showthread.php?t=955950")
[http://ubuntuforums.org/showthread.php?t=678747]("http://ubuntuforums.org/showthread.php?t=678747")

In connection with the Windows viruses and impossibility to start **regedit** or Windows in whole, sometimes Windows users need to edit the registry from outside. I've found, so far, the only utility in Linux **chntpw**, which was originally designed to reset passwords, and then acquired the registry editing ability. 

**Editing the registry:** 

1. Boot from a LiveCD or install a second system Ubuntu.

2. Install **chntpw** utility:

```
sudo apt-get install chntpw 
```

3. Mount Windows partition: 

Find the Windows partition: 

```
$ sudo fdisk -l
```

Assume it is on /dev/sda2. Next step is mounting of the partiotion:
 
```
$ sudo mkdir /media/windows 
$ sudo mount /dev/sda2 /media/windows
```

4. Registry editing

```
$ chntpw -l /media/windows/Windows/system32/config/software
```

Move to registry branch you need, for example: 

```
$ cd Microsoft\Windows NT\CurrentVersion\Winlogon
```

and edit a key, for example:
 
```
$ ed Shell 
```

**Password resetting: **

1. See 1-3 of the previous section 

4. Find the user whose password will be changed 

```
$ chntpw -l /media/windows/Windows/system32/config/SAM
```

5. Password resetting 

```
$ chntpw /media/windows/Windows/system32/config/SAM -u Administrator
``` 

Just cite the places in the registry where they can hide a record of running viruses: 

HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Notify
HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Userinit
HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Shell
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
HKLM\SOFTWARE\Microsoft\Active Setup\Installed Components
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\SharedTaskScheduler
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\ShellServiceObjectDelayLoad
HKCU\Software\Microsoft\Windows\CurrentVersion\Run

The default values in Regedit: 
[HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon] 
"Shell" = "Explorer.exe" 
"Userinit" = "C:\WINDOWS\system32\userinit.exe" 

Check Explorer.exe file for double presence ... the right place for the file is Windows\ but not Windows\System32\ ... 

This post was written to open the theme to combat viruses and sms-extortionists.

---

### Post by Shala on 2010-08-20
I use Windows Password Key 8.0 to reset the lost password before,i think it is also OK.

---

### Post by easterbunny on 2011-02-22
update:
to edit registry, use -e key:
[HTML]$ chntpw -e /media/windows/Windows/system32/config/software[/HTML]

chntpw for x64 in Ubuntu repositories doesn't work. Use version from Debian reps:[ http://packages.debian.org/sid/amd64/chntpw/download]("http://packages.debian.org/sid/amd64/chntpw/download")

---

### Post by crucafix18 on 2011-08-16
lovlely but win7 password is not clearing.it detects and says OK but when i log on windows it again says to give a password

---

### Post by Ibuntufixmypc on 2012-01-02
Hmmm... there's no software folder in my config folder. 

So on the step where you type chntpw -l /media/windows/Windows/system32/config/software, it says: 

owner@Owner:~$ chntpw -l /media/windows/Windows/system32/config/software
chntpw version 0.99.6 080526 (sixtyfour), (c) Petter N Hagen
openHive(/media/windows/Windows/system32/config/software) failed: No such file or directory, trying read-only
openHive(/media/windows/Windows/system32/config/software) in fallback RO-mode failed: No such file or directory
closing hive /media/windows/Windows/system32/config/software
Unable to open/read a hive, exiting..

Am I doing something wrong? I'm using this to attempt to edit the Windows registry to delete specific registry keys to remove a virus. I would stick with Ubuntu and just use it but the problem is Windows CD's don't work on Linux. :( :/

By "assume it's on sda2" on the mounting step, do you mean it is usually on sda2 by default? Because I checked the system monitor and it led me to believe that my Windows partition is on sda3....

---

### Post by MG&amp;TL on 2012-01-02
> **Ibuntufixmypc said:**
> Hmmm... there's no software folder in my config folder. 

So on the step where you type chntpw -l /media/windows/Windows/system32/config/software, it says: 

owner@Owner:~$ chntpw -l /media/windows/Windows/system32/config/software
chntpw version 0.99.6 080526 (sixtyfour), (c) Petter N Hagen
openHive(/media/windows/Windows/system32/config/software) failed: No such file or directory, trying read-only
openHive(/media/windows/Windows/system32/config/software) in fallback RO-mode failed: No such file or directory
closing hive /media/windows/Windows/system32/config/software
Unable to open/read a hive, exiting..

Am I doing something wrong? I'm using this to attempt to edit the Windows registry to delete specific registry keys to remove a virus. I would stick with Ubuntu and just use it but the problem is Windows CD's don't work on Linux. :( :/

By "assume it's on sda2" on the mounting step, do you mean it is usually on sda2 by default? Because I checked the system monitor and it led me to believe that my Windows partition is on sda3....


I have no clue about the piece of software you're using, but I think if Windows is on /dev/sda3, then use /dev/sda3. I think the OP meant /dev/sda2 is normal.

---

### Post by gato_negro87 on 2012-01-04
> **Ibuntufixmypc said:**
> Hmmm... there's no software folder in my config folder. 

So on the step where you type chntpw -l /media/windows/Windows/system32/config/software, it says: 

owner@Owner:~$ chntpw -l /media/windows/Windows/system32/config/software
chntpw version 0.99.6 080526 (sixtyfour), (c) Petter N Hagen
openHive(/media/windows/Windows/system32/config/software) failed: No such file or directory, trying read-only
openHive(/media/windows/Windows/system32/config/software) in fallback RO-mode failed: No such file or directory
closing hive /media/windows/Windows/system32/config/software
Unable to open/read a hive, exiting..

Am I doing something wrong? I'm using this to attempt to edit the  Windows registry to delete specific registry keys to remove a virus. I  would stick with Ubuntu and just use it but the problem is Windows CD's  don't work on Linux. :sad: :/

By "assume it's on sda2" on the mounting step, do you mean it is usually  on sda2 by default? Because I checked the system monitor and it led me  to believe that my Windows partition is on sda3....


be careful to use capital or lowercase letters in windows 7 folder is media/windows/Windows/System32/config/SOFTWARE

---

### Post by Loan_Refi on 2012-01-11
Re: Password Resetting

Hi, My Dell Desktop is not allowing me to boot from CD Rom or USB so I removed the Hard Drive and plugged it into my laptop.

Now, here is my question;

Can I erase/clear Wind0z XP password using this method meaning my hard drive being external?

I have Ubuntu 11.10 installed on my laptop and I've tried resetting the password but when I plug in the Hard Drive back on the Dell Desktop it doesn't work.

I've tried resetting/erasing the password using chntpw -u <username> SAM but its not working.

---

### Post by gagankapula on 2012-12-03
thanks man.....

---

