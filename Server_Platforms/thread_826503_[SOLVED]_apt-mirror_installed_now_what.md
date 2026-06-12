---
title: "[SOLVED] apt-mirror installed now what?"
date: 2008-06-11
forum: Server Platforms
---

### Post by doogy2004 on 2008-06-11
I installed apt-mirror using the instructions at [http://ubuntu-tutorials.com/2008/06/10/how-to-create-an-ubuntu-repository-mirror-on-ubuntu-804/](http://ubuntu-tutorials.com/2008/06/10/how-to-create-an-ubuntu-repository-mirror-on-ubuntu-804/)

I changed my download directory to /home/apt-mirror, because my raid array is mounted on /home, and ran the following to get apt-mirror to work with out failing and stating that it can't find skel
```
sudo cp -R /var/spool/apt-mirror/* /home/apt-mirror
```

What is the next step that I need to take to use the mirror with my other computers?

I'm running 8.04 Server, with LAMP, Samba, and Bind.

Thanks in advance.

---

### Post by molotov00 on 2008-06-12
[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)

Add the repo to your list of sources seems like the logical step. That's another tutorial that should help.

---

### Post by doogy2004 on 2008-06-12
> **molotov00 said:**
> [http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)

Add the repo to your list of sources seems like the logical step. That's another tutorial that should help.

Thanks, that is a much more complete how-to.  Using this tutorial, I can figure out how to use my local LAMP to serve up the repos to my other computers.  Either using Apache or Samba.

Thanks for the info.

---

### Post by doogy2004 on 2008-06-18
When I run ```
sudo apt-mirror
``` manually it works fine but when the cron job is supposed to run all I get this in the log:
```
Downloading 121 index files using 2 threads...
```
and the process is dead.

Here is the cron file:
```
#
# Regular cron jobs for the apt-mirror package
#
0 4     * * *   apt-mirror      /usr/bin/apt-mirror > /var/spool/apt-mirror/var/cron.log
```

any suggestions? Thanks in advance

---

### Post by doogy2004 on 2008-06-18
The problem is a permissions issue.  When I run ```
sudo apt-mirror
```It changes the permissions of the new files that apt-mirror uses to being owned by root.  This creates a problem when the cron job runs as the user apt-mirror, because the user apt-mirror can not alter the files owned by root.

To fix my problem I ran ```
sudo chown -R apt-mirror:apt-mirror /home/apt-mirror
```to change all the files back to apt-mirror.

When I want to manually run apt-mirror I have to use ```
sudo -u apt-mirror apt-mirror
```so that all of the changed/new files are owned by the proper user.

---

### Post by gaZooGA on 2008-11-19
I have had similar troubles, it drove me mad all last night. From your post I think I have finally solved it. 

I removed /etc/cron.d/apt-mirror

and added the code below into my crontab via:
```

crontab -e
```

Crontab now contains:

```
0 3   * * * sudo -u apt-mirror /usr/bin/apt-mirror >> /media/FileShare/apt-mirror/var/cron.log
0 9   * * * killall -v apt-mirror >> /media/FileShare/apt-mirror/var/cron.log
0 9   * * * killall -v wget >> /media/FileShare/apt-mirror/var/cron.log
```

Can anyone tell me if there is a security risk in me doing this? Or is there a better way? I basically wanted apt-mirror to start at 3 am and die at 9 am if it hadn't already finished.

---

### Post by doogy2004 on 2008-11-19
if you leave the cron as the default.  you can add the ip or domain name of your server to the beginning of each line of your sources.list file.  this will point apt to your mirror instead of the ubuntu mirrors.

---

