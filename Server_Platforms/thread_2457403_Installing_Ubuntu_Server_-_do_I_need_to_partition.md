---
title: "Installing Ubuntu Server - do I need to partition?"
date: 2021-02-01
forum: Server Platforms
---

### Post by nick+d on 2021-02-01
Hello all,

I am new to Ubuntu with a little command line experience.

Can someone tell me if I need to set the disk up as an LVM group (when installing Ubuntu Server) or if I can just use the entire disk? I'm not sure of the pros and cons of having swap/root partitions

Thanks,
Nick.

EDIT, I am looking at [this guide]("https://www.tecmint.com/install-ubuntu-20-04-server/").

OK, another EDIT: I have been reading up a little and I don't think I need LVM as my plan is just to use one 1TB disk for the server and another 500GB disk to put backups of the main disk on using Clonezilla. Maybe there is an easier way to back up than this but the upshot is that I don't think I'll need any more than 1TB of data (famous last words...!)

---

### Post by howefield on 2021-02-01
Thread moved to the "*Server Platforms*" forums.

---

### Post by nick+d on 2021-02-01
Thank you, howefield :)

---

### Post by Doug S on 2021-02-01
I can only speak for myself.
I do not use lvm, and do just use the entire hard disk as one partition.

While not the only reason, I often have a very large /boot directory, and never liked the small 
lvm version (which I know I could have made it bigger).

EDIT: I didn't look at your reference, but consider [the Ubuntu Server Guide]("https://ubuntu.com/server/docs"), newly moved to discourse as of 20.04.

---

### Post by nick+d on 2021-02-01
Hi Doug,

This is good to know since I have just finished installing it without LVM (I'm impatient). Many thanks for the guide and I will be going through that tonight.

No doubt I'll be back with further questions but thanks for your help here.

All the best,
Nick.

---

### Post by ameinild on 2021-02-03
I've also installed with the "default" disk setting, alas using an entire 500GB disk for everything. 
Just keep an eye on your logfiles, that they're not suddenly exploding in size. 
I've been running a number of docker services for a year, and no problems whatsoever.
My system is still using 20GB out of 470GB on disk (5%).

---

### Post by nick+d on 2021-02-03
Thanks, ameinild!

I'm sure that this will be fine for me and suit my purposes. All I want to do with the server is to host Piwigo on it and a Wordpress site for developing websites. Those two things said, do you guys (or anybody else reading this) have any guides for installing these things as I am new to this? I did try installing Piwigo but I keep running into the same problem with it.

Thank you,
Nick.

---

### Post by ameinild on 2021-02-03
I really like using docker to host application containers, since it keeps the main system clean, and the containers "just work". It requires a little more setup, and that you do some research about how to use docker.

For a crash course in docker, I'd highly recommend this video series: 
[https://www.youtube.com/playlist?list=PLT98CRl2KxKECHltRib03tG8pyKEzwf9t](https://www.youtube.com/playlist?list=PLT98CRl2KxKECHltRib03tG8pyKEzwf9t)

For high quality docker images, I'd recommend Linuxserver.io:
[URL="https://fleet.linuxserver.io/"]https://fleet.linuxserver.io/
[/URL] (they have a piwigo image as well)
[https://hub.docker.com/r/linuxserver/piwigo](https://hub.docker.com/r/linuxserver/piwigo)

And for Wordpress/Nginx, this seems like a good bet:
[https://hub.docker.com/r/bitnami/wordpress-nginx](https://hub.docker.com/r/bitnami/wordpress-nginx)

Also, for a nice overview and web management tool, I prefer Portainer:
[https://hub.docker.com/r/portainer/portainer-ce](https://hub.docker.com/r/portainer/portainer-ce)

---

### Post by nick+d on 2021-02-03
Thanks, ameinild,

Yes, I was running Piwigo on Docker using Open Media Vault but the container for Piwigo kept changing its IP address and giving me other connection issues. I got fed up of reinstalling and tagging loads of photos only for it to fail again. I have to say that Docker was a bit over my head so I will watch your videos and maybe I'll give it another shot.

Thanks for all the links there, I will let you know how I get on!

Nick.

---

### Post by ameinild on 2021-02-03
Sure - check it out and see if it works for you. However, it sounds like one thing that didn't work out on OMV was persistent volumes. If you set up the Piwigo container on docker correctly with a volume mapping, all the data (for instance photo tagging) would be saved outside the container, and thus could be transferred if the container was restored or updated. No persistent data should ever be saved inside the container.

If you need a bit of assistance about container management in general or for a particular container configuration (Piwigo for instance), just get back here and I'll see if I can help. I've not had any problems with docker containers on Ubuntu so far (except for a few very specific problems on specific containers).

---

### Post by nick+d on 2021-02-03
Hi ameinild,

Thanks for your continued support. I got a bit distracted and had a go at installing LAMP and it's worked well. This is all a big learning journey so I am happy to just go with the flow. That said, I will definitely look at the videos you have linked to and the other information as I am sure that Docker is the way to go for the future. I have also set up vsftpd and I'm just figuring out how to give the user rights to the apache public directory and with rights to upload and alter stuff in there.

Sorry, I don't mean to look like I have ignored all of your help but I just feel that it might be running before I can walk. I feel a bit more comfortable with a boring old web server set up and phpMyAdmin, which is something else I need to set up. I think that with a good grasp of setting something up this basic, I'll be better equipped to understand Docker. I will be referring back to all your links then.

You have been realluy helpful, so many thanks. I will update here as the journey continues!

Thanks again!
Nick.

---

### Post by ameinild on 2021-02-03
Of course, you just do whatever you feel like to get a grasp of the possibilities of what you can do with your Ubuntu server. But I do think that once you get around to using docker, you'll find that is has some advantages, at least for what I would call "stand-alone applications".

---

### Post by nick+d on 2021-02-03
OK, that's great - I just don't like to look like one of those people that put people like you to all the effort of explaining things and then do something else. All the stuff you mentioned is much appreciated, and there are so many people using Docker now, that this just has to be the future, I am sure. phpMyAdmin now installed! Very much enjoying learning things by doing - the best way I learn things!

Thanks again,
Nick.

---

### Post by nick+d on 2021-02-04
> **ameinild said:**
> If you need a bit of assistance about container management in general or for a particular container configuration (Piwigo for instance), just get back here and I'll see if I can help. I've not had any problems with docker containers on Ubuntu so far (except for a few very specific problems on specific containers).
Hello ameinild, its me again.

Ok so I tried all day yesterday to understand the best/safest way to install Piwigo and I even got LAMP, phpMyAdmin and sftp working nicely on the server but its just too much for me to learn at the moment. I did get PIwigo working but finished up at 0200 and didn't sleep until 0400 as I couldn't stop turning it all over in my mind! Since I have had success with running Docker and Portainer on OMV, I'm going back to that and I wondered if you'd be willing to help me with setting it up so that it doesn't lose the IP address, and anything else that you recommend?

I'll be using [this guide]("https://forum.openmediavault.org/index.php?thread/34497-piwigo-on-omv5-via-portainer-quick-install/"), with a few changes to the stack that I can post for you - these have been recommended changes by the good people over at the OMV forum.

Thanks,
Nick.

---

### Post by ameinild on 2021-02-04
Hi. I'm willing to give it a shot, but I would like to use the links I provided as reference, instead of the OMV forum.
I'll get back to you when I have the time. For starters, make sure you have docker and docker-compose installed.

---

### Post by nick+d on 2021-02-04
OK, will do and I just linked to the OMV how-to for your reference. I will look at using your links.

Thanks, this is kind of you.

EDIT: Do you mind if I use Portainer instead of docker-compose as I am more familiar with that?

---

### Post by ameinild on 2021-02-04
Actually I think the OMV link is pretty usable as it is. Also, I don't believe the IP address should be an issue if the container is running. Would you mind posting your stack config as you've edited it for reference, maybe I might spot some issues before you deploy.

---

### Post by nick+d on 2021-02-04
Yes, that's great - let me go and look for it as I need to install Portainer again but I know I backed it up somewhere.

Thanks for this :)

---

### Post by nick+d on 2021-02-04
OK, so here is my effort - its can't be that bad because it did actually work!

All that needs changing are the uuid's as I have formatted the drives and recreated the filesystems. Good luck ;)
```
version: 2.1
services:
  piwigo:
    image: linuxserver/piwigo
    container_name: piwigo
    environment:
      - PUID=1000
      - PGID=100
      - TZ=Europe/London
    volumes:
      - /srv/dev-disk-by-uuid-a02e5633-efc0-42a0-8098-3d413a5bc0b0/piwigo:/config
    ports:
      - 8125:80
    restart: unless-stopped
  mariadb:
    image: linuxserver/mariadb
    container_name: piwidb
    environment:
      - PUID=1000
      - PGID=100
      - MYSQL_ROOT_PASSWORD=MYPASSWORD
      - TZ=Europe/London
      - MYSQL_DATABASE=piwigo
      - MYSQL_USER=piwigo
      - MYSQL_PASSWORD=piwigo
    volumes:
      - /srv/dev-disk-by-uuid-a02e5633-efc0-42a0-8098-3d413a5bc0b0/mariadb-photo:/config
    ports:
      - 3306:3306
    restart: unless-stopped
```

---

### Post by ameinild on 2021-02-04
Ok a couple of observations:

Is your PGID really 100? Normally both your PUID and PGID is 1000 - just checking.

Also, I don't think the reference [FONT=courier new]/srv/dev-disk-by-uuid-a02e5633-efc0-42a0-8098-3d413a5bc0b0/piwigo[/FONT] works on Ubuntu.

I would instead "just" use the mount points. Let's say you've mounted the disk in [FONT=courier new]/mnt[/FONT], then you could refer to [FONT=courier new]/mnt/piwigo[/FONT] and [FONT=courier new]/mnt/mariadb-photo[/FONT] instead.

It's really important that your volume identifiers work, and point to a known place on your system, since all important data is there, and will stay there even if the container goes down.

So I would suggest the following config (provided your PGID is 1000 and your data is in [FONT=courier new]/mnt[/FONT]):

```

version: 2.1
services:
  piwigo:
    image: linuxserver/piwigo
    container_name: piwigo
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/London
    volumes:
      - /mnt/piwigo:/config
    ports:
      - 8125:80
    restart: unless-stopped
  mariadb:
    image: linuxserver/mariadb
    container_name: piwidb
    environment:
      - PUID=1000
      - PGID=1000
      - MYSQL_ROOT_PASSWORD=MYPASSWORD
      - TZ=Europe/London
      - MYSQL_DATABASE=piwigo
      - MYSQL_USER=piwigo
      - MYSQL_PASSWORD=piwigo
    volumes:
      - /mnt/mariadb-photo:/config
    ports:
      - 3306:3306
    restart: unless-stopped



```

---

### Post by nick+d on 2021-02-04
Well, as you by now know ,it doesn't take much to lose me, but here I go.

The PUID and GUID came from [this post]("https://www.networkshinobi.com/docker-containers-puid-and-pgid/"). That said, I departed from that post and then went on to set things up using the how-to I linked to earlier from the OMV forum.

Since the OMV how-to doesn't mention a user, I don't know which user to find the PUID and GUID from.

Regarding the uuid string, I am not sure how docker would find the directory if it didn't know the absolute path? Which is what I think it needs it for.

This is where drives are listed:

```
root@omvpeR210lo:/# cd srv
root@omvpeR210lo:/srv# ls
dev-disk-by-uuid-95ac1cb3-9588-41ec-a22d-d4f049397005  ftp     salt
dev-disk-by-uuid-c2a977a3-533c-4f40-a677-069261ea1301  pillar
```

Thanks,
Nick.

EDIT, okay, so I have re-read things and I get it now. The user isn't really important, its just there to provide a PUID and a GUID, so as to stop root from owning the files and them being inaccessible. So I will just create a user 'mrdocker', and then find out his PUID/GUID, and assign those to the stack.

So, I get this now:

```
root@omvpeR210lo:/srv# id mrdocker
uid=1001(mrdocker) gid=100(users) groups=100(users)
root@omvpeR210lo:/srv# 

```

In that case I will use PUID=1001; GUID+100.

---

### Post by ameinild on 2021-02-04
I'm a little confused - are those code snippets from Ubuntu or OpenMediaVault? On my Ubuntu server I have nothing in the dir /srv.
However, use the drive mappings and user ID's that work for you, and let us know how it goes.

---

### Post by nick+d on 2021-02-04
Yes, they are from OMV - like I said, I am moving back to that as Ubuntu server is just too complicated for me.

---

### Post by ameinild on 2021-02-04
Ah ok - good luck! ;)

---

### Post by LHammonds on 2021-02-04
I know people like the the atomic partitioning (all space allocated to one partition) because it is simple but I really would recommend using LVM in conjunction with separating partitions so any runaway data (logs or uploads) do not fill up your entire system.  When the root partition becomes full, things tend to break and fail.  So I slice off my data and apps onto separate partitions so that the root partition never grows over time or at least never becomes full causing stability issues.

I cover this in the partition section of my "[how to install Ubuntu](https://hammondslegacy.com/forum/viewtopic.php?p=811#p811)" guide which is rather involved but detailed to allow someone to setup a server which is expected to live a long time with little manual intervention.

---

