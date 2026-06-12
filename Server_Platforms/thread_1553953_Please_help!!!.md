---
title: "Please help!!!"
date: 2010-08-15
forum: Server Platforms
---

### Post by =ChAoS= on 2010-08-15
Hi, I had my remote ubuntu 10.04 server configured with ispconfig and had my forum set up and running fine. I also had a teamspeak and shoutcast server running and all was well. 
 
then i followed [COLOR=red][This Tutorial]("http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html")[/COLOR] to install deluge. After i did the last command "sudo reboot -h now" my server rebooted but nothing started. 
 
I have no shoutcast or teamspek servers and most of all i have no apache web server. I also had freenx working but thats stopped and all i can do is log in with putty. I really hope someone here knows what i should do to try and recover them all. I'm still a bit of a noob where ubuntu is concerned so please explain carefully if i can save my server. If i can't i don't think i can be bothered to install everything again so will probably give it all up as a bad experiment. :(
 
Thanks =ChAoS=

---

### Post by Yarui on 2010-08-15
They don't start automatically when you boot, but does it all work right if you start the services manually?

---

### Post by =ChAoS= on 2010-08-15
Thanks for the reply.
 
I tried apache but it failed now i'll try the others and report back.
 
=ChAos=

---

### Post by wojox on 2010-08-15
Have you rebooted before this incident without a problem? When I reboot my headless server from ssh, I use one of two options:

```
shutdown -r now
```

```
sudo reboot
```

---

### Post by =ChAoS= on 2010-08-15
Tis is what i get when i try to start apache ...
 
 
* Starting web server apache2 (30)Read-only file system: apache2: could not open error log file /var/log/apache2/error.log.
Unable to open logs
 
This is when i try to start shoutcast that is always a manual restart ...
 
sudo: ./sc_serv: command not found
 
Teamspeak as a built in script to start and always started in the past.
 
Any more ideas please?
 
and yes previous reboots have been fine ... I can also sftp into the server but not ftp into my forum account.
 
 
=ChAoS=

---

### Post by =ChAoS= on 2010-08-15
I just sftp'd into the www folder where my website was and the folder is empty? Also all the home folders appear to be gone only a swap folder that was chmodded to 777 can be seen? 
 
Is there anyway to do a system restore like in windows and would this help?
 
Thanks =ChAoS=

---

### Post by wojox on 2010-08-15
> **=ChAoS= said:**
> 
 
Is there anyway to do a system restore like in windows and would this help?
 
Thanks =ChAoS=

Not that I'm aware. You could try scalpel [How To Recover Deleted Files/Data In Ubuntu Linux]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/")

---

### Post by =ChAoS= on 2010-08-15
Thanks for the reply. This is a remote ubuntu server not a desktop im trying to save all the owrk i put in there is no files, jpg, avi, mp3 etc i want to recover.
 
Does this software rebuild your file system so it was like it was previously? What i mean is will it return my server to its original state before the reboot or just try to recover lost files?
 
Thanks =ChAoS=

---

### Post by koenn on 2010-08-16
> **=ChAoS= said:**
> Hi, I had my remote ubuntu 10.04 server configured with ispconfig and had my forum set up and running fine. I also had a teamspeak and shoutcast server running and all was well. 
 
then i followed [COLOR=red][ ...  so please explain carefully if i can save my server. If i can't i don't think i can be bothered to install everything again so will probably give it all up as a bad experiment. 
If you consider this an acceptable solution to your problem, by all means go ahead.


> **=ChAoS= said:**
> Tis is what i get when i try to start apache ...
* Starting web server apache2 (30)Read-only file system: apache2: could not open error log file /var/log/apache2/error.log.
Unable to open logs

Your filesystem is read-only. It shouldn't be. This is probably the cause of most of your problems. 
Find out why the filesystem gets mounted read-only and fix that first.

---

### Post by =ChAoS= on 2010-08-18
Well i still have no idea what happened but i completely re-installed. Setting up my forum was the most time consuming but now i have back ups should it happen again.

---

### Post by arrrghhh on 2010-08-18
> **=ChAoS= said:**
> Well i still have no idea what happened but i completely re-installed. Setting up my forum was the most time consuming but now i have back ups should it happen again.

Ouch.  We really needed to sort out why the machine was mounting / as read-only... Too late for that.

Glad to hear that you've got backups now.  FYI, in the future please be more descriptive in the title of your threads.  "Please help!!!" doesn't really let us know much of anything, just that you need help ;)

---

