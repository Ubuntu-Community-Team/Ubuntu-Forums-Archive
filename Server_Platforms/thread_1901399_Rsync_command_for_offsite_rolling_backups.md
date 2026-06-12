---
title: "Rsync command for offsite rolling backups"
date: 2011-12-28
forum: Server Platforms
---

### Post by Jags_FL on 2011-12-28
I've read alot of articles and tried to come up my self but couldn't, so need help with Rsync command for offsite rolling backups please.

I have installed cwRsync(in VMs as a test run for now) on two Windows servers and would like to setup rolling backups of a folder(which contains many folders within) from server# 1 to #2 and vice versa. 

I would like to push full backups twice a week(8:00PM Monday & Thursday) and like to delete first backup when third is completed, and so on. (attached schedule as a PNG)

So far I've transferred folder/files by running following in a .cmd file:

```
REM Set HOMEPATH values
SET HOMEDRIVE=%CD:~0,2%
SET HOMEPATH=%CD:~3%
SET CWRSYNCHOME=%CD%
SET CWOLDPATH=%PATH%
SET PATH=%CWRSYNCHOME%\BIN;%PATH%
SET HOME=%HOMEDRIVE%\%HOMEPATH%

rsync -avrz -ssh "/cygdrive/C/Test-Folder1" "RSBService@192.168.1.190:/cygdrive/c/Test-Folder2"

SET PATH=%CWOLDPATH%
```

Any help is greatly appreciated.

---

### Post by collisionystm on 2011-12-28
Question for you. 

I backup windows servers with rsync. I can def help you.

BUT

What exactly are you backing up? Just folders, such as a share? Or are you trying to grab any SQL data?

I mention SQL because you should NEVER try to grab SQL data while sql is running. You will F your S*** up! lol

Anyways, here is my setup and it works just fine.

My 'backup' server is ubuntu 10.04 server on an old dell desktop with an attached raid storage. 2TB worth.
It runs rsnapshot

I have my 2 windows servers mounted in its /etc/fstab so they are accessible.
Rsnapshot copies from the mounted windows drive to its backup destination on the raid every night. Rsnapshot stores 2 weeks worth of backups for me so I can easily go back in time. The beauty of it is you only do 1 full back up, and then afterwards rsnapshot only grabs the bits of changed data.

Is this what you are trying to do?

---

### Post by Jags_FL on 2011-12-29
@ collisionystm

Many thanks for the reply. The data I want to back up, belongs to QuickBooks & Lacerte(both intuit products). 

The main problem I'm having is that there's no Linux-server in my setup, although I can run one in virtual environment, I'm trying find Windows based solution and hence I was trying to go cwRsync route.

---

### Post by CharlesA on 2011-12-29
> **collisionystm said:**
> 
I mention SQL because you should NEVER try to grab SQL data while sql is running. You will F your S*** up! lol

Sort of offtopic, but.. I use mysqldump, and haven't run into any problems. Of course it's just a forum database, and not one that is being used constantly, so I don't know if that would be a issue or not.

---

### Post by collisionystm on 2011-12-29
> **Jags_FL said:**
> @ collisionystm

Many thanks for the reply. The data I want to back up, belongs to QuickBooks & Lacerte(both intuit products). 

The main problem I'm having is that there's no Linux-server in my setup, although I can run one in virtual environment, I'm trying find Windows based solution and hence I was trying to go cwRsync route.

Use robocopy

its the windows version of rsync.

---

### Post by collisionystm on 2011-12-29
> **CharlesA said:**
> Sort of offtopic, but.. I use mysqldump, and haven't run into any problems. Of course it's just a forum database, and not one that is being used constantly, so I don't know if that would be a issue or not.

The server I have is running Sql Express 2005 and Microsoft Dynamics is feeding from it.

I fat fingered a cron and it grabbed data from the wrong drive ( holding the sql database ) and it corrupted it something awful :(

---

### Post by CharlesA on 2011-12-29
> **collisionystm said:**
> The server I have is running Sql Express 2005 and Microsoft Dynamics is feeding from it.

I fat fingered a cron and it grabbed data from the wrong drive ( holding the sql database ) and it corrupted it something awful :(
Oh crap.

That sounds nasty.

---

### Post by collisionystm on 2011-12-29
> **CharlesA said:**
> Oh crap.

That sounds nasty.


yeahh... not fun. lol.

I need to do 2 things.

1. create new sql server
2. write myself a nice script to do nightly backups of the entire sql config and database


.... back to topic....

---

